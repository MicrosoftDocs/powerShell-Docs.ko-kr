---
title: PowerShell 모듈 어셈블리 종속성 충돌 해결
description: C#에서 이진 PowerShell 모듈을 작성하는 경우 다른 패키지나 라이브러리에 대한 종속성을 사용하여 기능을 제공하는 것이 자연스럽습니다.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 536bcfd1ced536faccde0d6c5bc483cdaf31ce68
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87775179"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a><span data-ttu-id="fa520-103">PowerShell 모듈 어셈블리 종속성 충돌 해결</span><span class="sxs-lookup"><span data-stu-id="fa520-103">Resolving PowerShell module assembly dependency conflicts</span></span>

<span data-ttu-id="fa520-104">C#에서 이진 PowerShell 모듈을 작성하는 경우 다른 패키지나 라이브러리에 대한 종속성을 사용하여 기능을 제공하는 것이 자연스럽습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-104">When writing a binary PowerShell module in C#, it's natural to take dependencies on other packages or libraries to provide functionality.</span></span> <span data-ttu-id="fa520-105">코드를 재사용을 위해 다른 라이브러리에 대한 종속성을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-105">Taking dependencies on other libraries is desirable for code reuse.</span></span> <span data-ttu-id="fa520-106">PowerShell은 항상 어셈블리를 동일한 컨텍스트에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-106">PowerShell always loads assemblies into the same context.</span></span> <span data-ttu-id="fa520-107">이로 인해 모듈의 종속성이 이미 로드된 DLL과 충돌할 때 문제가 발생하며 동일한 PowerShell 세션에서 두 가지 관련이 없는 모듈을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-107">This presents issues when a module's dependencies conflict with already-loaded DLLs and may prevent using two otherwise unrelated modules in the same PowerShell session.</span></span>

<span data-ttu-id="fa520-108">해당 문제가 발생하면 다음과 같은 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-108">If you've had this problem, you've seen an error message like this:</span></span>

![어셈블리 로드 충돌 오류 메시지](./media/resolving-dependency-conflicts/moduleconflict.png)

<span data-ttu-id="fa520-110">이 문서에서는 PowerShell에서 종속성 충돌이 발생하는 방법 및 종속성 충돌 문제를 완화하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-110">This article looks at some of the ways dependency conflicts occur in PowerShell and ways to mitigate dependency conflict issues.</span></span> <span data-ttu-id="fa520-111">여기에는 모듈 작성자가 아니더라도 사용하는 모듈에서 발생하는 종속성 충돌에 도움이 될 수 있는 몇 가지 요령이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-111">Even if you're not a module author, there are some tricks in here that might help you with dependency conflicts occurring in modules that you use.</span></span>

## <a name="why-do-dependency-conflicts-occur"></a><span data-ttu-id="fa520-112">종속성 충돌이 발생하는 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="fa520-112">Why do dependency conflicts occur?</span></span>

<span data-ttu-id="fa520-113">.NET에서는 동일한 어셈블리의 두 버전이 동일한 _어셈블리 로드 컨텍스트_에 로드될 때 종속성 충돌이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-113">In .NET, dependency conflicts occur when two versions of the same assembly are loaded into the same _Assembly Load Context_.</span></span> <span data-ttu-id="fa520-114">해당 용어는 여러 .NET 플랫폼에서 조금씩 다른 의미로 사용되며 관련 내용은 [뒤에서](#powershell-and-net) 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-114">This term means slightly different things on different .NET platforms, which is covered [later](#powershell-and-net).</span></span> <span data-ttu-id="fa520-115">해당 충돌은 버전이 지정된 종속성이 사용되는 모든 소프트웨어에서 발생하는 일반적인 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-115">This conflict is a common problem that occurs in any software where versioned dependencies are used.</span></span> <span data-ttu-id="fa520-116">간단한 솔루션은 없고 많은 종속성 해결 프레임워크가 다양한 방법으로 문제를 해결하려고 시도하기 때문에 해당 상황을 “종속성 결함”이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-116">Because there are no simple solutions, and because many dependency-resolution frameworks try to solve the problem in different ways, this situation is often called "dependency hell".</span></span>

<span data-ttu-id="fa520-117">충돌 문제는 프로젝트가 의도적이든 직접적이든 동일한 종속성의 두 가지 버전에 종속되지 않는다는 사실로 인해 심각해집니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-117">Conflict issues are compounded by the fact that a project almost never deliberately or directly depends on two versions of the same dependency.</span></span> <span data-ttu-id="fa520-118">대신, 프로젝트는 동일한 종속성의 각기 다른 버전이 필요한 두 개 이상의 종속성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-118">Instead, the project has two or more dependencies that each require a different version of the same dependency.</span></span>

<span data-ttu-id="fa520-119">예를 들어 .NET 애플리케이션인 `DuckBuilder`가 해당 기능의 일부를 수행하는 두 가지 종속성을 제공하며 다음과 같이 표시된다고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-119">For example, say your .NET application, `DuckBuilder`, brings in two dependencies, to perform parts of its functionality and looks like this:</span></span>

![DuckBuilder의 두 종속성은 Newtonsoft.json의 서로 다른 버전을 사용합니다.](./media/resolving-dependency-conflicts/dep-conflict.jpg)

<span data-ttu-id="fa520-121">`Contoso.ZipTools` 및 `Fabrikam.FileHelpers`는 서로 다른 버전의 `Newtonsoft.Json`을 사용하므로 각 종속성이 로드되는 방식에 따라 종속성 충돌이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-121">Because `Contoso.ZipTools` and `Fabrikam.FileHelpers` both depend on different versions of `Newtonsoft.Json`, there may be a dependency conflict depending on how each dependency is loaded.</span></span>

### <a name="conflicting-with-powershells-dependencies"></a><span data-ttu-id="fa520-122">PowerShell 종속성과 충돌</span><span class="sxs-lookup"><span data-stu-id="fa520-122">Conflicting with PowerShell's dependencies</span></span>

<span data-ttu-id="fa520-123">PowerShell 모듈 및 PowerShell 자체 종속성이 동일한 공유 컨텍스트에 로드되므로 PowerShell에서 종속성 충돌 문제가 커집니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-123">In PowerShell, the dependency conflict issue is magnified because PowerShell modules and PowerShell's own dependencies are loaded into the same shared context.</span></span> <span data-ttu-id="fa520-124">즉, PowerShell 엔진과 로드된 모든 PowerShell 모듈에는 충돌하는 종속성이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-124">This means the PowerShell engine and all loaded PowerShell modules must not have conflicting dependencies.</span></span> <span data-ttu-id="fa520-125">이에 관한 기존 예는 `Newtonsoft.Json`입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-125">A classic example of this is `Newtonsoft.Json`:</span></span>

![FictionalTools 모듈은 PowerShell보다 최신 버전의 Newtonsoft.json을 사용합니다.](./media/resolving-dependency-conflicts/engine-conflict.jpg)

<span data-ttu-id="fa520-127">이 예제에서 모듈 `FictionalTools`는 예제 PowerShell에 제공되는 `11.0.2`보다 최신 `Newtonsoft.Json` 버전인 `Newtonsoft.Json` 버전 `12.0.3`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-127">In this example, the module `FictionalTools` depends on `Newtonsoft.Json` version `12.0.3`, which is a newer version of `Newtonsoft.Json` than `11.0.2` that ships in the example PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="fa520-128">이는 예제이며 PowerShell 7에는 현재 `Newtonsoft.Json 12.0.3`이 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-128">This is an example and PowerShell 7 currently ships with `Newtonsoft.Json 12.0.3`.</span></span>

<span data-ttu-id="fa520-129">모듈은 최신 버전의 어셈블리를 사용하므로 PowerShell이 이미 로드한 버전을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-129">Because the module depends on a newer version of the assembly, it won't accept the version that PowerShell already has loaded.</span></span> <span data-ttu-id="fa520-130">그러나 PowerShell이 이미 특정 버전의 어셈블리를 로드했으므로 모듈은 기존 로드 메커니즘을 사용하여 자체 버전을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-130">But because PowerShell has already loaded a version of the assembly, the module can't load its own version using the conventional load mechanism.</span></span>

### <a name="conflicting-with-another-modules-dependencies"></a><span data-ttu-id="fa520-131">또 다른 모듈의 종속성과 충돌</span><span class="sxs-lookup"><span data-stu-id="fa520-131">Conflicting with another module's dependencies</span></span>

<span data-ttu-id="fa520-132">PowerShell의 또 다른 일반적인 시나리오는 한 버전의 어셈블리를 사용하는 모듈이 로드된 다음, 다른 버전의 해당 어셈블리를 사용하는 또 다른 모듈이 나중에 로드되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-132">Another common scenario in PowerShell is that a module is loaded that depends on one version of an assembly, and then another module is loaded later that depends on a different version of that assembly.</span></span>

<span data-ttu-id="fa520-133">해당 시나리오는 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-133">This often looks like the following:</span></span>

![두 PowerShell 모듈에는 서로 다른 버전의 Microsoft.Extensions.Logging 종속성이 필요합니다.](./media/resolving-dependency-conflicts/mod-conflict.jpg)

<span data-ttu-id="fa520-135">이 경우 `FictionalTools` 모듈에는 `FilesystemManager` 모듈보다 최신 버전의 `Microsoft.Extensions.Logging`이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-135">In this case, the `FictionalTools` module requires a newer version of `Microsoft.Extensions.Logging` than the `FilesystemManager` module.</span></span>

<span data-ttu-id="fa520-136">해당 모듈이 종속성 어셈블리를 루트 모듈 어셈블리와 동일한 디렉터리에 배치하여 종속성을 로드한다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-136">Imagine these modules load their dependencies by placing the dependency assemblies in the same directory as the root module assembly.</span></span> <span data-ttu-id="fa520-137">이렇게 하면 .NET은 종속성을 이름으로 암시적으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-137">This allows .NET to implicitly load them by name.</span></span> <span data-ttu-id="fa520-138">PowerShell 7(.NET Core 3.1 기반)을 실행하는 경우 `FictionalTools`를 로드하고 실행한 다음, 문제 없이 `FilesystemManager`를 로드하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-138">If we're running PowerShell 7 (on top of .NET Core 3.1), we can load and run `FictionalTools`, then load and run `FilesystemManager` without issue.</span></span> <span data-ttu-id="fa520-139">그러나 새 세션에서 `FilesystemManager`를 로드하고 실행한 다음, `FictionalTools`를 로드하면 로드된 것보다 최신 버전의 `Microsoft.Extensions.Logging`이 필요하므로 `FictionalTools` 명령에서 `FileLoadException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-139">However, in a new session, if we load and run `FilesystemManager`, then load `FictionalTools`, we get a `FileLoadException` from the `FictionalTools` command because it requires a newer version of `Microsoft.Extensions.Logging` than the one loaded.</span></span>
<span data-ttu-id="fa520-140">이름이 같은 어셈블리가 이미 로드되었으므로 `FictionalTools`는 필요한 버전을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-140">`FictionalTools` can't load the version needed because an assembly of the same name has already been loaded.</span></span>

## <a name="powershell-and-net"></a><span data-ttu-id="fa520-141">PowerShell 및 .NET</span><span class="sxs-lookup"><span data-stu-id="fa520-141">PowerShell and .NET</span></span>

<span data-ttu-id="fa520-142">PowerShell은 .NET 플랫폼에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-142">PowerShell runs on the .NET platform.</span></span> <span data-ttu-id="fa520-143">NET은 기본적으로 어셈블리 종속성 확인 및 로드를 담당하므로 종속성 충돌을 이해하려면 여기에서 .NET이 작동하는 방식을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-143">NET is ultimately responsible for resolving and loading assembly dependencies, so we must understand how .NET operates here to understand dependency conflicts.</span></span>

<span data-ttu-id="fa520-144">또한 여러 가지 버전의 PowerShell이 여러 가지 .NET 구현에서 실행된다는 사실도 인식해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-144">We must also confront the fact that different versions of PowerShell run on different .NET implementations.</span></span> <span data-ttu-id="fa520-145">일반적으로 PowerShell 5.1 이하는 .NET Framework에서 실행되지만 PowerShell 6 이상은 .NET Core에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-145">In general, PowerShell 5.1 and below run on .NET Framework, while PowerShell 6 and above run on .NET Core.</span></span> <span data-ttu-id="fa520-146">.NET의 해당하는 두 가지 구현은 어셈블리를 서로 다르게 로드하고 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-146">These two implementations of .NET load and handle assemblies differently.</span></span>
<span data-ttu-id="fa520-147">즉, 종속성 충돌 해결은 기본 .NET 플랫폼에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-147">This means that resolving dependency conflicts can vary depending on the underlying .NET platform.</span></span>

### <a name="assembly-load-contexts"></a><span data-ttu-id="fa520-148">어셈블리 로드 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="fa520-148">Assembly Load Contexts</span></span>

<span data-ttu-id="fa520-149">.NET에서 어셈블리가 로드되는 런타임 네임스페이스인 ALC(‘어셈블리 로드 컨텍스트’) 입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-149">In .NET, an _Assembly Load Context_ (ALC) that is a runtime namespace into which assemblies are loaded.</span></span> <span data-ttu-id="fa520-150">어셈블리 이름은 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-150">The assemblies' names must be unique.</span></span> <span data-ttu-id="fa520-151">해당 개념을 사용하면 각 ALC에서 이름으로 어셈블리를 고유하게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-151">This concept allows assemblies to be uniquely resolved by name in each ALC.</span></span>

### <a name="assembly-reference-loading-in-net"></a><span data-ttu-id="fa520-152">.NET의 어셈블리 참조 로딩</span><span class="sxs-lookup"><span data-stu-id="fa520-152">Assembly reference loading in .NET</span></span>

<span data-ttu-id="fa520-153">어셈블리 로딩의 의미 체계는 .NET 구현(.NET Core 대비 .NET Framework) 및 특정 어셈블리를 로드하는 데 사용되는 .NET API에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-153">The semantics of assembly loading depend on both the .NET implementation (.NET Core vs .NET Framework) and the .NET API used to load a particular assembly.</span></span> <span data-ttu-id="fa520-154">여기서 자세히 설명하지 않지만 각 .NET 구현에서 .NET 어셈블리 로딩이 작동하는 방식을 자세히 살펴볼 수 있는 링크가 [추가 정보](#further-reading) 섹션에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-154">Rather than go into detail here, there are links in the [Further reading](#further-reading) section that go into great detail on how .NET assembly loading works in each .NET implementation.</span></span>

<span data-ttu-id="fa520-155">이 문서에서는 다음 메커니즘을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-155">In this article we'll refer to the following mechanisms:</span></span>

- <span data-ttu-id="fa520-156">암시적 어셈블리 로드(실제로 `Assembly.Load(AssemblyName)`) - .NET이 .NET 코드의 정적 어셈블리 참조에서 이름으로 어셈블리를 암시적으로 로드하려고 시도하는 경우.</span><span class="sxs-lookup"><span data-stu-id="fa520-156">Implicit assembly loading (effectively `Assembly.Load(AssemblyName)`), when .NET implicitly tries to load an assembly by name from a static assembly reference in .NET code.</span></span>
- <span data-ttu-id="fa520-157">`Assembly.LoadFrom()` - 로드된 DLL의 종속성을 확인하기 위한 처리기를 추가하는 플러그인 기반 로딩 API입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-157">`Assembly.LoadFrom()`, a plugin-oriented loading API that adds handlers to resolve dependencies of the loaded DLL.</span></span> <span data-ttu-id="fa520-158">해당 메서드는 원하는 방식으로 종속성을 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-158">This method may not resolve dependencies the way we want.</span></span>
- <span data-ttu-id="fa520-159">`Assembly.LoadFile()` - 요청된 어셈블리만 로드하고 종속성을 처리하지 않는 기본 로딩 API.</span><span class="sxs-lookup"><span data-stu-id="fa520-159">`Assembly.LoadFile()`, a basic loading API intended to load only the assembly asked for and does not handle any dependencies.</span></span>

### <a name="differences-in-net-framework-vs-net-core"></a><span data-ttu-id="fa520-160">.NET Framework 및 .NET Core의 차이점</span><span class="sxs-lookup"><span data-stu-id="fa520-160">Differences in .NET Framework vs .NET Core</span></span>

<span data-ttu-id="fa520-161">해당 API가 작동하는 방식은 .NET Core와 .NET Framework 간에 약간 변경되었으므로 포함된 [링크](#further-reading)를 참조하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-161">The way these APIs work has changed in subtle ways between .NET Core and .NET Framework, so it's worth reading through the included [links](#further-reading).</span></span> <span data-ttu-id="fa520-162">중요한 점은, .NET Framework와 .NET Core 간에 어셈블리 로드 컨텍스트 및 기타 어셈블리 확인 메커니즘이 변경되었다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-162">Importantly, Assembly Load Contexts and other assembly resolution mechanisms have changed between .NET Framework and .NET Core.</span></span>

<span data-ttu-id="fa520-163">특히 .NET Framework에는 다음 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-163">In particular, .NET Framework has the following features:</span></span>

- <span data-ttu-id="fa520-164">머신 전체의 어셈블리 확인을 위한 전역 어셈블리 캐시</span><span class="sxs-lookup"><span data-stu-id="fa520-164">The Global Assembly Cache, for machine-wide assembly resolution</span></span>
- <span data-ttu-id="fa520-165">어셈블리 격리를 위해 In Process 샌드박스에서 작동하며 경합할 serialization 계층을 제공하는 애플리케이션 도메인</span><span class="sxs-lookup"><span data-stu-id="fa520-165">Application Domains, which work like in-process sandboxes for assembly isolation, but also present a serialization layer to contend with</span></span>
- <span data-ttu-id="fa520-166">각각 자체 동작을 포함하는 고정된 어셈블리 로드 컨텍스트 세트가 있는 제한된 어셈블리 로드 컨텍스트 모델([여기](/dotnet/framework/deployment/best-practices-for-assembly-loading)에서 자세히 설명함):</span><span class="sxs-lookup"><span data-stu-id="fa520-166">A limited assembly load context model, explained in depth [here](/dotnet/framework/deployment/best-practices-for-assembly-loading), that has a fixed set of assembly load contexts, each with their own behavior:</span></span>
  - <span data-ttu-id="fa520-167">기본적으로 어셈블리가 로드되는 기본 로드 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="fa520-167">The default load context, where assemblies are loaded by default</span></span>
  - <span data-ttu-id="fa520-168">런타임에 어셈블리를 수동으로 로드하기 위한 로드 시작 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="fa520-168">The load-from context, for loading assemblies manually at runtime</span></span>
  - <span data-ttu-id="fa520-169">어셈블리를 실행하지 않고 메타데이터를 읽도록 어셈블리를 안전하게 로드하기 위한 리플렉션 전용 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="fa520-169">The reflection-only context, for safely loading assemblies to read their metadata without running them</span></span>
  - <span data-ttu-id="fa520-170">`Assembly.LoadFile(string path)` 및 `Assembly.Load(byte[] asmBytes)`로 로드된 어셈블리가 있는 이해하기 힘든 void</span><span class="sxs-lookup"><span data-stu-id="fa520-170">The mysterious void that assemblies loaded with `Assembly.LoadFile(string path)` and `Assembly.Load(byte[] asmBytes)` live in</span></span>

<span data-ttu-id="fa520-171">.NET Core(및 .NET 5 이상)에서는 해당 복잡성이 보다 간단한 모델로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-171">.NET Core (and .NET 5+) has replaced this complexity with a simpler model:</span></span>

- <span data-ttu-id="fa520-172">전역 어셈블리 캐시 없음</span><span class="sxs-lookup"><span data-stu-id="fa520-172">No Global Assembly Cache.</span></span> <span data-ttu-id="fa520-173">애플리케이션이 모든 자체 종속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-173">Applications bring all their own dependencies.</span></span> <span data-ttu-id="fa520-174">이에 따라 애플리케이션에서 종속성 확인을 위한 외부 요소가 제거되어 종속성 확인의 재현 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-174">This removes an external factor for dependency resolution in applications, making dependency resolution more reproducible.</span></span>
  <span data-ttu-id="fa520-175">플러그인 호스트로서 PowerShell은 모듈에서 해당 상황을 약간 복잡하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-175">PowerShell, as the plugin host, complicates this slightly for modules.</span></span> <span data-ttu-id="fa520-176">`$PSHOME`에서 해당 종속성은 모든 모듈과 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-176">Its dependencies in `$PSHOME` are shared with all modules.</span></span>
- <span data-ttu-id="fa520-177">애플리케이션 도메인이 하나만 있고 새 항목을 만들 수 없음</span><span class="sxs-lookup"><span data-stu-id="fa520-177">Only one Application Domain, and no ability to create new ones.</span></span> <span data-ttu-id="fa520-178">애플리케이션 도메인 개념은 .NET Core에서 .NET 프로세스의 전역 상태로만 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-178">The Application Domain concept is maintained in .NET Core purely to be the global state of the .NET process.</span></span>
- <span data-ttu-id="fa520-179">확장 가능한 새 어셈블리 로드 컨텍스트 모델.</span><span class="sxs-lookup"><span data-stu-id="fa520-179">A new, extensible Assembly Load Context model.</span></span> <span data-ttu-id="fa520-180">어셈블리 확인은 새 ALC에 배치하여 네임스페이스로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-180">Assembly resolution can be namespaced by putting it in a new ALC.</span></span> <span data-ttu-id="fa520-181">.NET Core 프로세스는 모든 어셈블리가 로드되는 단일 기본 ALC로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-181">.NET Core processes begin with a single default ALC into which all assemblies are loaded.</span></span> <span data-ttu-id="fa520-182">(`Assembly.LoadFile(string)` 및 `Assembly.Load(byte[])`를 사용하여 로드된 어셈블리 제외) 그러나 프로세스는 자체 로딩 논리를 사용하여 자체 사용자 지정 ALC를 만들고 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-182">(except for those loaded with `Assembly.LoadFile(string)` and `Assembly.Load(byte[])`) But the process can create and define its own custom ALCs with its own loading logic.</span></span> <span data-ttu-id="fa520-183">어셈블리가 로드되면 해당 어셈블리가 로드되는 첫 번째 ALC는 해당 종속성을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-183">When an assembly is loaded, the first ALC it is loaded into is responsible for resolving its dependencies.</span></span> <span data-ttu-id="fa520-184">이렇게 하면 강력한 .NET 플러그인 로딩 메커니즘을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-184">This creates opportunities to implement powerful .NET plugin loading mechanisms.</span></span>

<span data-ttu-id="fa520-185">두 가지 구현에서 모두 어셈블리는 지연 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-185">In both implementations, assemblies are loaded lazily.</span></span> <span data-ttu-id="fa520-186">즉, 해당 형식이 필요한 메서드가 처음으로 실행될 때 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-186">This means that they are loaded when a method requiring their type is run for the first time.</span></span>

<span data-ttu-id="fa520-187">예를 들어 서로 다른 시간에 종속성을 로드하는 동일한 코드의 두 가지 버전은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-187">For example, here are two versions of the same code that load a dependency at different times.</span></span>

<span data-ttu-id="fa520-188">첫 번째 코드는 종속성 참조가 메서드 내에 어휘로 존재하기 때문에 항상 `Program.GetRange()`가 호출될 때 해당 종속성을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-188">The first always loads its dependency when `Program.GetRange()` is called, because the dependency reference is lexically present within the method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

<span data-ttu-id="fa520-189">두 번째는 메서드를 통한 내부 간접 참조이므로 `limit` 매개 변수가 20개 이상인 경우에만 해당 종속성을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-189">The second will load its dependency only if the `limit` parameter is 20 or more, because of the internal indirection through a method:</span></span>

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

<span data-ttu-id="fa520-190">이는 메모리와 파일 시스템 I/O를 최소화하고 리소스를 보다 효율적으로 사용하기 때문에 좋은 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-190">This is a good practice since it minimizes the memory and filesystem I/O and uses the resources more efficiently.</span></span> <span data-ttu-id="fa520-191">이로 인한 안타까운 부작용은 어셈블리를 로드하려고 하는 코드 경로에 도달할 때까지 어셈블리가 로드에 실패하는지 알 수 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-191">The unfortunate a side effect of this is that we won't know that the assembly fails to load until we reach the code path that tries to load the assembly.</span></span>

<span data-ttu-id="fa520-192">어셈블리 로드 충돌의 타이밍 조건을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-192">It can also create a timing condition for assembly load conflicts.</span></span> <span data-ttu-id="fa520-193">동일한 프로그램의 두 부분이 동일한 어셈블리의 서로 다른 버전을 로드하려고 시도하면 로드되는 버전은 먼저 실행되는 코드 경로에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-193">If two parts of the same program try to load different versions of the same assembly, the version loaded depends on which code path is run first.</span></span>

<span data-ttu-id="fa520-194">PowerShell의 경우 이는 다음 요소가 어셈블리 로드 충돌에 영향을 줄 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-194">For PowerShell, this means that the following factors can affect an assembly load conflict:</span></span>

- <span data-ttu-id="fa520-195">먼저 로드된 모듈은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="fa520-195">Which module was loaded first?</span></span>
- <span data-ttu-id="fa520-196">종속성 라이브러리를 사용하는 코드 경로가 실행되었나요?</span><span class="sxs-lookup"><span data-stu-id="fa520-196">Was the code path that uses the dependency library run?</span></span>
- <span data-ttu-id="fa520-197">PowerShell이 시작 시 또는 특정 코드 경로에서만 충돌 종속성을 로드하나요?</span><span class="sxs-lookup"><span data-stu-id="fa520-197">Does PowerShell load a conflicting dependency at startup or only under certain code paths?</span></span>

## <a name="quick-fixes-and-their-limitations"></a><span data-ttu-id="fa520-198">빠른 수정 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="fa520-198">Quick fixes and their limitations</span></span>

<span data-ttu-id="fa520-199">일부 경우에는 모듈을 약간 조정하고 최소한의 작업으로 항목을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-199">In some cases, it's possible to make small adjustments to your module and fix things with minimal effort.</span></span> <span data-ttu-id="fa520-200">그러나 해당 솔루션은 신중하게 제공되는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-200">But these solutions tend to come with caveats.</span></span> <span data-ttu-id="fa520-201">모듈에 적용될 수 있지만 모든 모듈에서 작동하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-201">While they may apply to your module, they won't work for every module.</span></span>

### <a name="change-your-dependency-version"></a><span data-ttu-id="fa520-202">종속성 버전 변경</span><span class="sxs-lookup"><span data-stu-id="fa520-202">Change your dependency version</span></span>

<span data-ttu-id="fa520-203">종속성 충돌을 방지하는 가장 간단한 방법은 종속성에 동의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-203">The simplest way to avoid dependency conflicts is to agree on a dependency.</span></span> <span data-ttu-id="fa520-204">해당 방법은 다음 경우에 가능할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-204">This may be possible when:</span></span>

- <span data-ttu-id="fa520-205">충돌이 모듈의 직접 종속성에서 발생하며 버전을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-205">Your conflict is with a direct dependency of your module and you control the version.</span></span>
- <span data-ttu-id="fa520-206">충돌이 간접 종속성에서 발생하지만 작업 가능한 간접 종속성 버전을 사용하도록 직접 종속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-206">Your conflict is with an indirect dependency, but you can configure your direct dependencies to use a workable indirect dependency version.</span></span>
- <span data-ttu-id="fa520-207">충돌 버전을 알고 있으며 변경하지 않고 해당 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-207">You know the conflicting version and can rely on it not changing.</span></span>

<span data-ttu-id="fa520-208">`Newtonsoft.Json` 패키지는 마지막 시나리오의 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-208">The `Newtonsoft.Json` package is a good example of this last scenario.</span></span> <span data-ttu-id="fa520-209">해당 패키지는 PowerShell 6 이상의 종속성이며 Windows PowerShell에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-209">This is a dependency of PowerShell 6 and above, and isn't used in Windows PowerShell.</span></span> <span data-ttu-id="fa520-210">즉, 버전 지정 충돌을 해결하는 간단한 방법은 대상으로 지정하려는 PowerShell 버전에서 `Newtonsoft.Json`의 가장 낮은 버전을 대상으로 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-210">Meaning a simple way to resolve versioning conflicts is to target the lowest version of `Newtonsoft.Json` across the PowerShell versions you wish to target.</span></span>

<span data-ttu-id="fa520-211">예를 들어 PowerShell 6.2.6 및 PowerShell 7.0.2는 둘 다 현재 `Newtonsoft.Json` 버전 12.0.3을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-211">For example, PowerShell 6.2.6 and PowerShell 7.0.2 both currently use `Newtonsoft.Json` version 12.0.3.</span></span> <span data-ttu-id="fa520-212">따라서 Windows PowerShell, PowerShell 6 및 PowerShell 7을 대상으로 하는 모듈을 만들려면 종속성으로 `Newtonsoft.Json 12.0.3`을 대상으로 지정하고 빌드된 모듈에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-212">So, to create a module targeting Windows PowerShell, PowerShell 6, and PowerShell 7, you would target `Newtonsoft.Json 12.0.3` as a dependency and include it in your built module.</span></span> <span data-ttu-id="fa520-213">모듈이 PowerShell 6 또는 7에 로드되면 PowerShell의 자체 `Newtonsoft.Json` 어셈블리가 이미 로드된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-213">When the module is loaded in PowerShell 6 or 7, PowerShell's own `Newtonsoft.Json` assembly is already loaded.</span></span> <span data-ttu-id="fa520-214">또한 모듈에 필요한 최소한의 버전이므로 확인이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-214">Also, it is at least the version required for your module, so resolution succeeds.</span></span> <span data-ttu-id="fa520-215">Windows PowerShell에서 어셈블리는 아직 PowerShell에 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-215">In Windows PowerShell, the assembly isn't already present in PowerShell.</span></span> <span data-ttu-id="fa520-216">대신, 모듈 폴더에서 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-216">So, it's loaded from your module folder instead.</span></span>

<span data-ttu-id="fa520-217">일반적으로 `Microsoft.PowerShell.Sdk` 또는 `System.Management.Automation` 같은 구체적인 PowerShell 패키지를 대상으로 지정하는 경우 NuGet은 필요한 적합한 종속성 버전을 확인할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-217">Generally, when targeting a concrete PowerShell package, like `Microsoft.PowerShell.Sdk` or `System.Management.Automation`, NuGet should be able to resolve the right dependency versions required.</span></span> <span data-ttu-id="fa520-218">대상으로 여러 프레임워크 또는 `PowerShellStandard.Library`를 지정하도록 선택해야 하므로 Windows PowerShell 및 PowerShell 6 이상을 둘 다 대상으로 지정하는 것이 더 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-218">Targeting both Windows PowerShell and PowerShell 6+ becomes more difficult because you must choose between targeting multiple frameworks or `PowerShellStandard.Library`.</span></span>

<span data-ttu-id="fa520-219">일반 종속성 버전으로 고정할 수 없는 경우는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-219">Circumstances where pinning to a common dependency version won't work include:</span></span>

- <span data-ttu-id="fa520-220">충돌이 간접 종속성에서 발생하며 일반 버전을 사용하도록 구성할 수 있는 종속성이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="fa520-220">The conflict is with an indirect dependency, and none of your dependencies can be configured to use a common version.</span></span>
- <span data-ttu-id="fa520-221">다른 종속성 버전이 자주 변경될 수 있으므로 일반 버전의 정착이 단기 고정일 뿐인 경우</span><span class="sxs-lookup"><span data-stu-id="fa520-221">The other dependency version is likely to change often, so settling on a common version is only a short-term fix.</span></span>

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a><span data-ttu-id="fa520-222">AssemblyResolve 이벤트 처리기를 추가하여 동적 바인딩 리디렉션 만들기</span><span class="sxs-lookup"><span data-stu-id="fa520-222">Add an AssemblyResolve event handler to create a dynamic binding redirect</span></span>

<span data-ttu-id="fa520-223">경우에 따라 자체 종속성 버전을 변경하는 것이 불가능하거나 너무 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-223">Sometimes changing your own dependency version isn't possible or is too difficult.</span></span> <span data-ttu-id="fa520-224">또 다른 옵션은 `AssemblyResolve` 이벤트의 이벤트 처리기를 등록하여 동적 바인딩 리디렉션을 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-224">Another option is to set up a dynamic binding redirect by registering an event handler for the `AssemblyResolve` event.</span></span>

<span data-ttu-id="fa520-225">정적 바인딩 리디렉션과 마찬가지로 요점은 종속성의 모든 소비자가 동일한 실제 어셈블리를 사용하도록 강제하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-225">As with a static binding redirect, the point is to force all consumers of a dependency to use the same actual assembly.</span></span> <span data-ttu-id="fa520-226">종속성을 로드하는 호출을 가로채고 항상 원하는 버전으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-226">You intercept calls to load the dependency and always redirect them to the version you want.</span></span>

<span data-ttu-id="fa520-227">다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-227">This looks something like this:</span></span>

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

<span data-ttu-id="fa520-228">기술적으로 PowerShell 내에 스크립트 블록을 등록하여 `AssemblyResolve` 이벤트를 처리할 수 있지만 다음과 같은 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-228">You can technically register a scriptblock within PowerShell to handle an `AssemblyResolve` event, but:</span></span>

- <span data-ttu-id="fa520-229">PowerShell이 처리할 수 없는 모든 스레드에서 `AssemblyResolve` 이벤트가 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-229">An `AssemblyResolve` event may be triggered on any thread, something that PowerShell will be unable to handle.</span></span>
- <span data-ttu-id="fa520-230">이벤트가 적합한 스레드에서 처리되는 경우에도 PowerShell의 범위 지정 개념에 따라 외부에서 정의되는 변수를 사용하지 않도록 이벤트 처리기 스크립트 블록을 신중하게 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-230">Even when events are handled on the right thread, PowerShell's scoping concepts mean that the event handler scriptblock must be written carefully to not depend on variables defined outside it.</span></span>

<span data-ttu-id="fa520-231">일반 버전으로 리디렉션이 작동하지 않는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-231">There are situations where redirecting to a common version won't work:</span></span>

- <span data-ttu-id="fa520-232">버전 간에 종속성에 관련된 호환성이 손상되는 변경이 있는 경우 또는 종속 코드가 리디렉션되는 버전에서 사용할 수 없는 기능을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="fa520-232">When the dependency has made breaking changes between versions, or when dependent code relies on a functionality otherwise not available in the version you redirect to.</span></span>
- <span data-ttu-id="fa520-233">모듈이 충돌 종속성 전에 로드되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="fa520-233">When your module isn't loaded before the conflicting dependency.</span></span> <span data-ttu-id="fa520-234">종속성이 로드된 후 `AssemblyResolve` 이벤트 처리기를 등록하면 처리기가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-234">If you register an `AssemblyResolve` event handler after the dependency has been loaded, it will never be fired.</span></span> <span data-ttu-id="fa520-235">또 다른 모듈과 종속성 충돌을 방지하려는 경우 다른 모듈이 먼저 로드될 수 있으므로 해당 상황에 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-235">If you're trying to prevent dependency conflicts with another module, this may be an issue, since the other module may be loaded first.</span></span>

### <a name="use-the-dependency-out-of-process"></a><span data-ttu-id="fa520-236">out of process 종속성 사용</span><span class="sxs-lookup"><span data-stu-id="fa520-236">Use the dependency out of process</span></span>

<span data-ttu-id="fa520-237">이 솔루션은 모듈 작성자보다 모듈 사용자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-237">This solution is more for module users than module authors.</span></span> <span data-ttu-id="fa520-238">기존 종속성 충돌로 인해 작동하지 않는 모듈이 나타나는 경우 사용할 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-238">This is a solution to use when confronted with a module that won't work due to an existing dependency conflict.</span></span>

<span data-ttu-id="fa520-239">동일한 어셈블리의 두 버전이 동일한 .NET 프로세스로 로드되기 때문에 종속성 충돌이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-239">Dependency conflicts occur because two versions of the same assembly are loaded into the same .NET process.</span></span> <span data-ttu-id="fa520-240">간단한 솔루션은, 양쪽에서 해당 기능을 사용할 수 있다면 두 버전을 서로 다른 프로세스로 로드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-240">A simple solution is to load them into different processes, as long as you can still use the functionality from both together.</span></span>

<span data-ttu-id="fa520-241">PowerShell에서 해당 작업을 수행하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-241">In PowerShell, there are several ways to achieve this:</span></span>

- <span data-ttu-id="fa520-242">PowerShell을 하위 프로세스로 호출</span><span class="sxs-lookup"><span data-stu-id="fa520-242">Invoke PowerShell as a subprocess</span></span>

  <span data-ttu-id="fa520-243">현재 프로세스에서 PowerShell 명령을 실행하는 간단한 방법은 명령 호출을 통해 직접 새 PowerShell 프로세스를 시작하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-243">A simple way to run a PowerShell command out of the current process is to just start a new PowerShell process directly with the command call:</span></span>

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  <span data-ttu-id="fa520-244">여기서 주요 제한 사항은 결과를 재구성하는 것이 다른 옵션보다 더 까다롭고 오류가 발생하기 쉽다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-244">The main limitation here is that restructuring the result can be trickier or more error prone than other options.</span></span>

- <span data-ttu-id="fa520-245">PowerShell 작업 시스템</span><span class="sxs-lookup"><span data-stu-id="fa520-245">The PowerShell job system</span></span>

  <span data-ttu-id="fa520-246">PowerShell 작업 시스템은 새 PowerShell 프로세스에 명령을 전송하고 결과를 반환함으로써 명령을 out of process로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-246">The PowerShell job system also runs commands out of process, by sending commands to a new PowerShell process and returning the results:</span></span>

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  <span data-ttu-id="fa520-247">이 경우 변수와 상태가 제대로 전달되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-247">In this case, you just need to be sure that any variables and state are passed in correctly.</span></span>

  <span data-ttu-id="fa520-248">작은 명령을 실행하는 경우 작업 시스템이 약간 복잡할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-248">The job system can also be slightly cumbersome when running small commands.</span></span>

- <span data-ttu-id="fa520-249">PowerShell 원격 기능</span><span class="sxs-lookup"><span data-stu-id="fa520-249">PowerShell remoting</span></span>

  <span data-ttu-id="fa520-250">사용할 수 있는 경우 PowerShell 원격은 명령을 out of process로 실행하는 유용한 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-250">When it's available, PowerShell remoting can be a useful way to run commands out of process.</span></span> <span data-ttu-id="fa520-251">원격을 사용하여 새 프로세스에서 새 **PSSession**을 만들고, PowerShell 원격을 통해 해당 명령을 호출한 다음, 충돌 종속성을 포함하는 다른 모듈에서 로컬로 결과를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-251">With remoting, you can create a fresh **PSSession** in a new process, call its commands over PowerShell remoting, then use the results locally with the other modules containing the conflicting dependencies.</span></span>

  <span data-ttu-id="fa520-252">예제는 다음과 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-252">An example might look like this:</span></span>

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- <span data-ttu-id="fa520-253">Windows PowerShell에 대한 암시적 원격</span><span class="sxs-lookup"><span data-stu-id="fa520-253">Implicit remoting to Windows PowerShell</span></span>

  <span data-ttu-id="fa520-254">PowerShell 7의 또 다른 옵션은 `Import-Module`에서 `-UseWindowsPowerShell` 플래그를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-254">Another option in PowerShell 7 is to use the `-UseWindowsPowerShell` flag on `Import-Module`.</span></span> <span data-ttu-id="fa520-255">이 방법으로 로컬 원격 세션을 통해 모듈을 Windows PowerShell로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-255">This will import the module through a local remoting session into Windows PowerShell:</span></span>

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  <span data-ttu-id="fa520-256">모듈이 작동하지 않거나 Windows PowerShell과 다르게 작동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-256">Be aware that modules may not work with, or work differently with Windows PowerShell.</span></span>

#### <a name="when-out-of-process-invocation-should-not-be-used"></a><span data-ttu-id="fa520-257">Out of Procss 호출을 사용하지 않아야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="fa520-257">When out-of-process invocation should not be used</span></span>

<span data-ttu-id="fa520-258">모듈 작성자로서 out of process 명령 호출은 모듈에 반영되기 어려우며 문제를 일으키는 에지 사례를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-258">As a module author, out-of-process command invocation is difficult to bake into a module and may have edge cases that cause issues.</span></span> <span data-ttu-id="fa520-259">특히 원격 및 작업은 모듈이 작동해야 하는 일부 환경에서 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-259">In particular, remoting and jobs may not be available in all environments where your module needs to work.</span></span> <span data-ttu-id="fa520-260">그러나 구현을 out of process로 이동하고 PowerShell 모듈이 더 씬한 클라이언트가 되도록 허용하는 일반적인 원칙이 계속 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-260">However, the general principle of moving the implementation out of process and allowing the PowerShell module to be a thinner client, may still be applicable.</span></span>

<span data-ttu-id="fa520-261">모듈 사용자로서는 out of process 호출이 작동하지 않는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-261">As a module user, there are cases where out-of-process invocation won't work:</span></span>

- <span data-ttu-id="fa520-262">사용할 권한이 없거나 사용하도록 설정되지 않아 PowerShell 원격을 사용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="fa520-262">When PowerShell remoting is unavailable because you don't have privileges to use it or it is not enabled.</span></span>
- <span data-ttu-id="fa520-263">특정 .NET 형식이 출력에서 메서드 또는 다른 명령에 대한 입력으로 필요한 경우.</span><span class="sxs-lookup"><span data-stu-id="fa520-263">When a particular .NET type is needed from output as input to a method or another command.</span></span>
  <span data-ttu-id="fa520-264">PowerShell 원격을 통해 실행되는 명령은 강력한 형식의 .NET 개체가 아닌 역직렬화된 개체를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-264">Commands running over PowerShell remoting emit deserialized objects rather than strongly-typed .NET objects.</span></span> <span data-ttu-id="fa520-265">즉, 메서드 호출 및 강력한 형식의 API는 원격을 통해 가져온 명령의 출력에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-265">This means that method calls and strongly typed APIs do not work with the output of commands imported over remoting.</span></span>

## <a name="more-robust-solutions"></a><span data-ttu-id="fa520-266">더 강력한 솔루션</span><span class="sxs-lookup"><span data-stu-id="fa520-266">More robust solutions</span></span>

<span data-ttu-id="fa520-267">이전 솔루션에는 모두 작동하지 않는 시나리오 및 모듈이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-267">The previous solutions all had scenarios and modules that don't work.</span></span> <span data-ttu-id="fa520-268">그러나 비교적 간단하게 제대로 구현할 수 있다는 장점도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-268">However, they also have the virtue of being relatively simple to implement correctly.</span></span> <span data-ttu-id="fa520-269">다음 솔루션은 더 강력하지만, 제대로 구현하려면 더 많은 작업이 필요하며, 신중하게 작성되지 않을 경우 사소한 버그가 도입될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-269">The following solutions are more robust, but require more effort to implement correctly and can introduce subtle bugs if not written carefully.</span></span>

### <a name="loading-through-net-core-assembly-load-contexts"></a><span data-ttu-id="fa520-270">.NET Core 어셈블리 로드 컨텍스트를 통해 로드</span><span class="sxs-lookup"><span data-stu-id="fa520-270">Loading through .NET Core Assembly Load Contexts</span></span>

<span data-ttu-id="fa520-271">특히 동일한 어셈블리의 여러 버전을 동일한 런타임으로 로드해야 하는 필요성을 해결하기 위해 구현 가능한 API로서 ALC([어셈블리 로드 컨텍스트](/dotnet/api/system.runtime.loader.assemblyloadcontext))가 .NET Core 1.0에 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-271">[Assembly Load Contexts](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) as an implementable API were introduced in .NET Core 1.0 to specifically address the need to load multiple versions of the same assembly into the same runtime.</span></span>

<span data-ttu-id="fa520-272">.NET Core 및 .NET 5 내에서 ALC는 어셈블리의 충돌 버전을 로드하는 문제에 대한 가장 강력한 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-272">Within .NET Core and .NET 5, they offer the most robust solution to the problem of loading conflicting versions of an assembly.</span></span> <span data-ttu-id="fa520-273">그러나 사용자 지정 ALC는 .NET Framework에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-273">However, custom ALCs are not available in .NET Framework.</span></span> <span data-ttu-id="fa520-274">즉, 해당 솔루션은 PowerShell 6 이상에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-274">This means that this solution only works in PowerShell 6 and above.</span></span>

<span data-ttu-id="fa520-275">현재 PowerShell에서 종속성 격리를 위해 ALC를 사용하는 가장 좋은 예는 PowerShell Editor Services, Visual Studio Code용 PowerShell 확장의 언어 서버에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-275">Currently, the best example of using an ALC for dependency isolation in PowerShell is in PowerShell Editor Services, the language server for the PowerShell extension for Visual Studio Code.</span></span> <span data-ttu-id="fa520-276">[ALC를 사용](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs)하여 PowerShell Editor Services의 자체 종속성이 PowerShell 모듈의 종속성과 충돌하지 않도록 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-276">An [ALC is used](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) to prevent PowerShell Editor Services' own dependencies from clashing with those in PowerShell modules.</span></span>

<span data-ttu-id="fa520-277">ALC를 사용하여 모듈 종속성 격리를 구현하는 것은 개념적으로 어렵지만 최소한의 예제를 통해 작업할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-277">Implementing module dependency isolation with an ALC is conceptually difficult, but we will work through a minimal example.</span></span> <span data-ttu-id="fa520-278">PowerShell 7에서만 작동하도록 고안된 간단한 모듈이 있다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-278">Imagine we have a simple module that is only intended to work in PowerShell 7.</span></span>
<span data-ttu-id="fa520-279">원본 코드는 다음과 같이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-279">The source code is organized as follows:</span></span>

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

<span data-ttu-id="fa520-280">cmdlet 구현은 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-280">The cmdlet implementation looks like this:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="fa520-281">(매우 단순화된) 매니페스트는 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-281">The (heavily simplified) manifest, looks like this:</span></span>

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

<span data-ttu-id="fa520-282">또한 `csproj`는 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-282">And the `csproj` looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="fa520-283">해당 모듈을 빌드할 때 생성된 출력의 레이아웃은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-283">When we build this module, the generated output has the following layout:</span></span>

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

<span data-ttu-id="fa520-284">이 예제에서 문제는 가상 충돌 종속성인 `Shared.Dependency.dll` 어셈블리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-284">In this example, our problem is in the `Shared.Dependency.dll` assembly, which is our imaginary conflicting dependency.</span></span> <span data-ttu-id="fa520-285">이는 모듈 특정 버전을 사용할 수 있도록 ALC 뒤에 배치해야 하는 종속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-285">This is the dependency that we need to put behind an ALC so that we can use the module-specific version.</span></span>

<span data-ttu-id="fa520-286">다음과 같이 모듈을 다시 엔지니어링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-286">We need to re-engineer the module so that:</span></span>

- <span data-ttu-id="fa520-287">모듈 종속성은 PowerShell의 ALC가 아닌 사용자 지정 ALC에만 로드되므로 충돌이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-287">Module dependencies are only loaded into our custom ALC, and not into PowerShell's ALC, so there can be no conflict.</span></span> <span data-ttu-id="fa520-288">또한 프로젝트에 더 많은 종속성을 추가하면서 로딩이 계속 작동하도록 더 많은 코드를 지속적으로 추가하지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-288">Moreover, as we add more dependencies to our project, we don't want to continuously add more code to keep loading working.</span></span> <span data-ttu-id="fa520-289">대신, 재사용 가능한 제네릭 종속성 확인 논리를 원합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-289">Instead, we want reusable, generic dependency resolution logic.</span></span>
- <span data-ttu-id="fa520-290">모듈 로드는 PowerShell에서 계속 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-290">Loading the module still works as normal in PowerShell.</span></span> <span data-ttu-id="fa520-291">PowerShell 모듈 시스템에 필요한 cmdlet 및 기타 형식은 PowerShell 자체 ALC 내에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-291">Cmdlets and other types that the PowerShell module system needs are defined within PowerShell's own ALC.</span></span>

<span data-ttu-id="fa520-292">두 가지 요구 사항을 중재하려면 모듈을 다음과 같은 두 어셈블리로 분할해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-292">To mediate these two requirements, we must break up our module into two assemblies:</span></span>

- <span data-ttu-id="fa520-293">PowerShell의 모듈 시스템에서 모듈을 제대로 로드하는 데 필요한 모든 형식의 정의를 포함하는 cmdlet 어셈블리 `AlcModule.Cmdlets.dll`.</span><span class="sxs-lookup"><span data-stu-id="fa520-293">A cmdlets assembly, `AlcModule.Cmdlets.dll`, that contains definitions of all the types that PowerShell's module system needs to load our module correctly.</span></span> <span data-ttu-id="fa520-294">즉, `Cmdlet` 기본 클래스의 구현과 사용자 지정 ALC를 통해 `AlcModule.Engine.dll`을 적절히 로드하도록 `AssemblyLoadContext.Default.Resolving`의 이벤트 처리기를 설정하는 `IModuleAssemblyInitializer`를 구현하는 클래스의 구현을 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-294">Namely, any implementations of the `Cmdlet` base class and the class that implements `IModuleAssemblyInitializer`, which sets up the event handler for `AssemblyLoadContext.Default.Resolving` to properly load `AlcModule.Engine.dll` through our custom ALC.</span></span> <span data-ttu-id="fa520-295">PowerShell 7은 다른 ALC에 로드된 어셈블리에 정의된 형식을 의도적으로 숨기므로 PowerShell에 공개적으로 공개되어야 하는 모든 형식도 여기에서 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-295">Since PowerShell 7 deliberately hides types defined in assemblies loaded in other ALCs, any types that are meant to be publicly exposed to PowerShell must also be defined here.</span></span> <span data-ttu-id="fa520-296">마지막으로, 사용자 지정 ALC 정의를 해당 어셈블리에서 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-296">Finally, our custom ALC definition needs to be defined in this assembly.</span></span> <span data-ttu-id="fa520-297">그 외에도 해당 어셈블리에는 최대한 적은 코드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-297">Beyond that, as little code as possible should live in this assembly.</span></span>
- <span data-ttu-id="fa520-298">모듈의 실제 구현을 처리하는 엔진 어셈블리 `AlcModule.Engine.dll`.</span><span class="sxs-lookup"><span data-stu-id="fa520-298">An engine assembly, `AlcModule.Engine.dll`, that handles the actual implementation of the module.</span></span>
  <span data-ttu-id="fa520-299">해당 어셈블리의 형식은 PowerShell ALC에서 사용할 수 있지만 처음에는 사용자 지정 ALC를 통해 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-299">Types from this are available in the PowerShell ALC, but it will initially be loaded through our custom ALC.</span></span> <span data-ttu-id="fa520-300">해당 종속성은 사용자 지정 ALC에만 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-300">Its dependencies are only loaded into the custom ALC.</span></span> <span data-ttu-id="fa520-301">실제로 해당 종속성은 두 ALC 간에 ‘브리지’가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-301">Effectively, this becomes a _bridge_ between the two ALCs.</span></span>

<span data-ttu-id="fa520-302">브리지 개념을 사용하는 새로운 어셈블리 상황은 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-302">Using this bridge concept, our new assembly situation looks like this:</span></span>

![두 ALC를 연결하는 AlcModule.Engine.dll을 나타내는 다이어그램](./media/resolving-dependency-conflicts/alc-diagram.jpg)

<span data-ttu-id="fa520-304">기본 ALC의 종속성 검색 논리가 사용자 지정 ALC로 로드되는 종속성을 확인하지 않도록 하려면 모듈의 해당하는 두 부분을 서로 다른 디렉터리로 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-304">To make sure the default ALC's dependency probing logic does not resolve the dependencies to be loaded into the custom ALC, we need to separate these two parts of the module in different directories.</span></span> <span data-ttu-id="fa520-305">새 모듈 레이아웃의 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-305">The new module layout has the following structure:</span></span>

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

<span data-ttu-id="fa520-306">구현이 어떻게 변경되는지 확인하기 위해 `AlcModule.Engine.dll` 구현부터 시작하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-306">To see how the implementation changes, we'll start with the implementation of `AlcModule.Engine.dll`:</span></span>

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

<span data-ttu-id="fa520-307">이는 종속성 `Shared.Dependency.dll`의 간단한 컨테이너이지만, 다른 어셈블리의 cmdlet이 PowerShell용으로 래핑하는 기능의 .NET API로 간주해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-307">This is a simple container for the dependency, `Shared.Dependency.dll`, but you should think of it as the .NET API for your functionality that the cmdlets in the other assembly wrap for PowerShell.</span></span>

<span data-ttu-id="fa520-308">`AlcModule.Cmdlets.dll`의 cmdlet은 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-308">The cmdlet in `AlcModule.Cmdlets.dll` looks like this:</span></span>

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

<span data-ttu-id="fa520-309">이때 **AlcModule**을 로드하고 `Test-AlcModule`을 실행하는 경우 기본 ALC가 `Alc.Engine.dll`을 로드하여 `EndProcessing()`을 실행하려고 시도하면 `FileNotFoundException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-309">At this point, if we were to load **AlcModule** and run `Test-AlcModule`, we get a `FileNotFoundException` when the default ALC tries to load `Alc.Engine.dll` to run `EndProcessing()`.</span></span> <span data-ttu-id="fa520-310">해당 예외는 기본 ALC가 숨기려는 종속성을 찾을 수 없음을 의미하므로 정상입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-310">This is good, since it means the default ALC can't find the dependencies we want to hide.</span></span>

<span data-ttu-id="fa520-311">이제 `AlcModule.Engine.dll`을 확인하는 방법을 알 수 있도록 `AlcModule.Cmdlets.dll`에 코드를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-311">Now we need to add code to `AlcModule.Cmdlets.dll` so that it knows how to resolve `AlcModule.Engine.dll`.</span></span> <span data-ttu-id="fa520-312">먼저 모듈의 `Dependencies` 디렉터리에서 어셈블리를 확인할 사용자 지정 ALC를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-312">First we must define our custom ALC that will resolve assemblies from our module's `Dependencies` directory:</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _depdendencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                s_dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

<span data-ttu-id="fa520-313">그런 다음, 사용자 지정 ALC를 기본 ALC의 `Resolving` 이벤트에 연결해야 합니다. 해당 이벤트는 애플리케이션 도메인에서 `AssemblyResolve` 이벤트의 ALC 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-313">Then we need to hook up our custom ALC to the default ALC's `Resolving` event, which is the ALC version of the `AssemblyResolve` event on Application Domains.</span></span> <span data-ttu-id="fa520-314">해당 이벤트는 `EndProcessing()`이 호출될 때 `AlcModule.Engine.dll`을 찾기 위해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-314">This event is fired to find `AlcModule.Engine.dll` when `EndProcessing()` is called.</span></span>

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

<span data-ttu-id="fa520-315">새 구현에서는 모듈이 로드되고 `Test-AlcModule`이 실행될 때 발생하는 호출의 시퀀스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-315">With the new implementation, take a look at the sequence of calls that occurs when the module is loaded and `Test-AlcModule` is run:</span></span>

![사용자 지정 ALC를 사용하여 종속성을 로드하는 호출의 시퀀스 다이어그램](./media/resolving-dependency-conflicts/alc-sequence.png)

<span data-ttu-id="fa520-317">몇 가지 관심 지점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-317">Some points of interest are:</span></span>

- <span data-ttu-id="fa520-318">`IModuleAssemblyInitializer` 모듈은 `Resolving` 이벤트를 로드 및 설정할 때 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-318">The `IModuleAssemblyInitializer` is run first when the module loads and sets the `Resolving` event.</span></span>
- <span data-ttu-id="fa520-319">`Test-AlcModule`이 실행되고 해당 `EndProcessing()` 메서드가 호출될 때까지 종속성을 로드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-319">We don't load the dependencies until `Test-AlcModule` is run and its `EndProcessing()` method is called.</span></span>
- <span data-ttu-id="fa520-320">`EndProcessing()`이 호출되면 기본 ALC는 `AlcModule.Engine.dll`을 찾지 못하고 `Resolving` 이벤트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-320">When `EndProcessing()` is called, the default ALC fails to find `AlcModule.Engine.dll` and fires the `Resolving` event.</span></span>
- <span data-ttu-id="fa520-321">이벤트 처리기는 사용자 지정 ALC를 기본 ALC에 연결하고 `AlcModule.Engine.dll`만 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-321">Our event handler hooks up the custom ALC to the default ALC and loads `AlcModule.Engine.dll` only.</span></span>
- <span data-ttu-id="fa520-322">`AlcModule.Engine.dll` 내에서 `AlcEngine.Use()`가 호출되면 사용자 지정 ALC는 다시 `Shared.Dependency.dll`을 확인하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-322">When `AlcEngine.Use()` is called within `AlcModule.Engine.dll`, the custom ALC again kicks in to resolve `Shared.Dependency.dll`.</span></span> <span data-ttu-id="fa520-323">특히 기본 ALC의 구성 요소와 충돌하지 않으므로 항상 ‘우리의’ `Shared.Dependency.dll`을 로드하며 `Dependencies` 디렉터리에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-323">Specifically, it always loads _our_ `Shared.Dependency.dll` since it never conflicts with anything in the default ALC and only looks in our `Dependencies` directory.</span></span>

<span data-ttu-id="fa520-324">구현을 어셈블하면 새 원본 코드 레이아웃이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-324">Assembling the implementation, our new source code layout looks like this:</span></span>

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

<span data-ttu-id="fa520-325">AlcModule.Cmdlets.csproj는 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-325">AlcModule.Cmdlets.csproj looks like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="fa520-326">AlcModule.Engine.csproj는 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-326">AlcModule.Engine.csproj looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="fa520-327">따라서 모듈을 빌드할 때 전략은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-327">So, when we build the module, our strategy is:</span></span>

- <span data-ttu-id="fa520-328">`AlcModule.Engine` 빌드</span><span class="sxs-lookup"><span data-stu-id="fa520-328">Build `AlcModule.Engine`</span></span>
- <span data-ttu-id="fa520-329">`AlcModule.Cmdlets` 빌드</span><span class="sxs-lookup"><span data-stu-id="fa520-329">Build `AlcModule.Cmdlets`</span></span>
- <span data-ttu-id="fa520-330">`AlcModule.Engine`의 모든 항목을 `Dependencies` 디렉터리로 복사하고 복사한 항목 기억</span><span class="sxs-lookup"><span data-stu-id="fa520-330">Copy everything from `AlcModule.Engine` into the `Dependencies` directory, and remember what we copied</span></span>
- <span data-ttu-id="fa520-331">`AlcModule.Engine`에 없는 `AlcModule.Cmdlets`의 모든 항목을 기본 모듈 디렉터리에 복사</span><span class="sxs-lookup"><span data-stu-id="fa520-331">Copy everything from `AlcModule.Cmdlets` that wasn't in `AlcModule.Engine` into the base module directory</span></span>

<span data-ttu-id="fa520-332">여기서 모듈 레이아웃은 종속성 분리에 매우 중요하므로 원본 루트에서 사용할 빌드 스크립트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-332">Since the module layout here is so crucial to dependency separation, here's a build script to use from the source root:</span></span>

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

<span data-ttu-id="fa520-333">마지막으로, 어셈블리 로드 컨텍스트를 사용하여 더 많은 종속성이 추가되면서 시간이 지남에 따라 강력하게 유지되는 모듈의 종속성을 격리하는 일반적인 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-333">Finally, we have a general way to use an Assembly Load Context to isolate our module's dependencies that remains robust over time as more dependencies are added.</span></span>

<span data-ttu-id="fa520-334">자세한 예제는 관련 [GitHub 리포지토리](https://github.com/rjmholt/ModuleDependencyIsolationExample)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa520-334">For a more detailed example, go to this [GitHub repository](https://github.com/rjmholt/ModuleDependencyIsolationExample).</span></span> <span data-ttu-id="fa520-335">이 예제에서는 모듈을 마이그레이션하여 ALC를 사용하면서 .NET Framework에서 해당 모듈이 계속 작동하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-335">This example demonstrates how to migrate a module to use an ALC, while keeping that module working in .NET Framework.</span></span> <span data-ttu-id="fa520-336">또한 .NET Standard 및 PowerShell Standard를 사용하여 핵심 구현을 간소화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-336">It also show how to use .NET Standard and PowerShell Standard to simplify the core implementation.</span></span>

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a><span data-ttu-id="fa520-337">`Assembly.LoadFile()`을 사용하여 나란히 로드를 위한 어셈블리 확인 처리기</span><span class="sxs-lookup"><span data-stu-id="fa520-337">Assembly resolve handler for side-by-side loading with `Assembly.LoadFile()`</span></span>

<span data-ttu-id="fa520-338">나란히 어셈블리 로딩을 수행하는 더 간단할 수 있는 또 다른 방법은 `Assembly.LoadFile()`에 `AssemblyResolve` 이벤트를 연결하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-338">Another, possibly simpler, way to achieve side-by-side assembly loading is to hook up an `AssemblyResolve` event to `Assembly.LoadFile()`.</span></span> <span data-ttu-id="fa520-339">`Assembly.LoadFile()` 사용은 .NET Core 및 .NET Framework를 둘 다 구현하고 사용할 수 있는 가장 간단한 솔루션이라는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-339">Using `Assembly.LoadFile()` has the advantage of being the simplest solution to implement and works with both .NET Core and .NET Framework.</span></span>

<span data-ttu-id="fa520-340">이를 제시하기 위해 동적 바인딩 리디렉션 예제 및 위 어셈블리 로드 컨텍스트 예제의 아이디어를 결합하는 구현의 간단한 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-340">To show this, let's take a look at a quick example of an implementation that combines ideas from our dynamic binding redirect example, and the Assembly Load Context example above.</span></span>

<span data-ttu-id="fa520-341">Trivial 명령 `Test-LoadFile [-Path] <path>`를 포함하는 **LoadFileModule** 모듈을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-341">We'll call this module **LoadFileModule**, which has a trivial command `Test-LoadFile [-Path] <path>`.</span></span> <span data-ttu-id="fa520-342">해당 모듈은 `CsvHelper` 어셈블리(버전 15.0.5)에 대한 종속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-342">This module takes a dependency on the `CsvHelper` assembly (version 15.0.5).</span></span>

<span data-ttu-id="fa520-343">ALC 모듈과 마찬가지로 먼저 모듈을 두 부분으로 분할해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-343">As with the ALC module, we must first split up the module into two pieces.</span></span>

<span data-ttu-id="fa520-344">첫 번째 부분은 실제 구현인 `LoadFileModule.Engine`을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-344">The first part does the actual implementation, `LoadFileModule.Engine`:</span></span>

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

<span data-ttu-id="fa520-345">두 번째 부분은 PowerShell이 직접 로드하는 항목인 `LoadFileModule.Cmdlets`입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-345">The second part is what PowerShell loads directly, `LoadFileModule.Cmdlets`.</span></span> <span data-ttu-id="fa520-346">종속성을 별도 디렉터리에 격리하는 ALC 모듈과 유사한 전략을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-346">We use a strategy similar to the ALC module, where we isolate dependencies in a separate directory.</span></span> <span data-ttu-id="fa520-347">그러나 이번에는 `LoadFileModule.Engine.dll`만이 아니라 확인 이벤트를 사용하여 모든 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-347">But this time, we load all assemblies in with a resolve event rather than just `LoadFileModule.Engine.dll`.</span></span>

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

<span data-ttu-id="fa520-348">마지막으로, 모듈의 레이아웃도 ALC 모듈과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-348">Finally, the layout of the module is also similar to the ALC module:</span></span>

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

<span data-ttu-id="fa520-349">해당 구조가 준비되면 **LoadFileModule**은 이제 **CsvHelper**에 대한 종속성을 사용하여 다른 모듈과 함께 로드될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-349">With this structure in place, **LoadFileModule** now supports being loaded alongside other modules with a dependency on **CsvHelper**.</span></span>

<span data-ttu-id="fa520-350">해당 처리기는 애플리케이션 도메인 전체에서 **모든** `AssemblyResolve` 이벤트에 적용되므로 다음과 같은 몇 가지 특정 디자인 항목을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-350">Because our handler applies to **all** `AssemblyResolve` events across the Application Domain, we need to make some specific design choices here:</span></span>

- <span data-ttu-id="fa520-351">이벤트가 다른 로딩을 방해할 수 있는 창을 좁히려면 `LoadFileModule.Engine.dll`이 로드된 후에만 일반 종속성 로딩 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-351">To narrow the window in which our event may interfere with other loading, we only start handling general dependency loading after `LoadFileModule.Engine.dll` has been loaded.</span></span>
- <span data-ttu-id="fa520-352">`LoadFileModule.Engine.dll`을 종속성 디렉터리에 푸시하면 PowerShell이 아닌 `LoadFile()` 호출을 통해 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-352">We push `LoadFileModule.Engine.dll` out into the Dependencies directory, so that it's loaded by a `LoadFile()` call rather than by PowerShell.</span></span> <span data-ttu-id="fa520-353">즉, 예를 들어 다른 `CsvHelper.dll`이 PowerShell에 로드된 경우에도 자체 종속성 로드는 항상 `AssemblyResolve` 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-353">This means its own dependency loads always raise an `AssemblyResolve` event, even if another `CsvHelper.dll` (for example) is loaded in PowerShell.</span></span>
  <span data-ttu-id="fa520-354">이렇게 하면 올바른 종속성을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-354">This gives us the opportunity to find the correct dependency.</span></span>
- <span data-ttu-id="fa520-355">모듈의 특정 종속성만 해결 확인해야 하므로 종속성 이름 및 버전의 사전을 처리기로 코딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-355">Since we must only resolve the specific dependencies for our module, we're forced to code a dictionary of dependency names and versions into our handler.</span></span> <span data-ttu-id="fa520-356">이 경우 `ResolveEventArgs.RequestingAssembly` 속성을 사용하여 `CsvHelper`가 모듈에서 요청되고 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-356">In our particular case, it would be possible to use the `ResolveEventArgs.RequestingAssembly` property to work out whether `CsvHelper` is being requested by our module.</span></span> <span data-ttu-id="fa520-357">그러나 해당 내용은 `CsvHelper` 자체가 `AssemblyResolve` 이벤트를 발생시키는 경우와 같은 종속성의 종속성에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-357">But this doesn't work for dependencies of dependencies; for example, if `CsvHelper` itself raised an `AssemblyResolve` event.</span></span> <span data-ttu-id="fa520-358">`Dependencies` 디렉터리에 있는 어셈블리의 메타데이터에 요청된 어셈블리를 비교하는 등의 더 어려운 다른 방법으로 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-358">There are other, harder ways to do this, such as comparing requested assemblies to the metadata of assemblies in the `Dependencies` directory.</span></span> <span data-ttu-id="fa520-359">그러나 이 예제에서는 문제를 강조할 뿐 아니라 예제를 간소화하기 위해 해당 검사를 더 명시적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-359">But, in this example, we've made this checking more explicit to both highlight the issue and simplify the example.</span></span>

<span data-ttu-id="fa520-360">이는 `LoadFile()` 전략과 ALC 전략 간 주요 차이점입니다. `AssemblyResolve` 이벤트는 애플리케이션 도메인에서 모든 로드를 처리해야 하므로 종속성 확인이 다른 모듈에 관련되지 않도록 하는 것이 훨씬 더 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-360">This is the key difference between the `LoadFile()` strategy and the ALC strategy: the `AssemblyResolve` event must service all loads in the Application Domain, making it much harder to keep our dependency resolution from being tangled with other modules.</span></span> <span data-ttu-id="fa520-361">그러나 .NET Framework에 ALC가 없으면 해당 옵션을 이해하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-361">However, the lack of ALCs in .NET Framework makes this option worth understanding.</span></span>

### <a name="custom-application-domains"></a><span data-ttu-id="fa520-362">사용자 지정 애플리케이션 도메인</span><span class="sxs-lookup"><span data-stu-id="fa520-362">Custom Application Domains</span></span>

<span data-ttu-id="fa520-363">어셈블리 격리의 가장 극단적인 최종 옵션은 사용자 지정 애플리케이션 도메인을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-363">The final and most extreme option for assembly isolation is to use custom Application Domains.</span></span>
<span data-ttu-id="fa520-364">애플리케이션 도메인은 .NET Framework에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-364">Application Domains (used in the plural) are only available in .NET Framework.</span></span> <span data-ttu-id="fa520-365">.NET 애플리케이션의 부분 간에 In Process 격리를 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-365">They are used to provide in-process isolation between parts of a .NET application.</span></span> <span data-ttu-id="fa520-366">용도 중 하나는 동일한 프로세스 내에서 어셈블리 로드를 서로 격리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-366">One of the uses is to isolate assembly loads from each other within the same process.</span></span>

<span data-ttu-id="fa520-367">그러나 애플리케이션 도메인은 serialization 경계입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-367">However, Application Domains are serialization boundaries.</span></span> <span data-ttu-id="fa520-368">한 애플리케이션 도메인의 개체는 다른 애플리케이션 도메인의 개체에서 직접 참조하고 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-368">Objects in one Application Domain can't be referenced and used directly by objects in another Application Domain.</span></span> <span data-ttu-id="fa520-369">`MarshalByRefObject`를 구현하여 해당 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-369">You can work around this by implementing `MarshalByRefObject`.</span></span> <span data-ttu-id="fa520-370">하지만 형식을 제어하지 않는 경우 일반적으로 종속성을 사용하는 경우처럼 여기에는 구현을 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-370">But when you don't control the types, as is often the case with dependencies, it's not possible to force an implementation here.</span></span> <span data-ttu-id="fa520-371">유일한 솔루션은 아키텍처를 크게 변경하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-371">The only solution is to make large architectural changes.</span></span> <span data-ttu-id="fa520-372">Serialization 경계는 성능에도 심각한 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-372">The serialization boundary also has serious performance implications.</span></span>

<span data-ttu-id="fa520-373">애플리케이션 도메인에는 이런 심각한 제한 사항이 있고, 구현하기에 복잡하고, .NET Framework에서만 작동하기 때문에 여기서는 사용하는 방법의 예제는 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-373">Because Application Domains have this serious limitation, are complicated to implement, and only work in .NET Framework, we won't give an example of how you might use them here.</span></span> <span data-ttu-id="fa520-374">가능성으로 언급할 가치가 있지만 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-374">While they're worth mentioning as a possibility, they're not recommended.</span></span>

<span data-ttu-id="fa520-375">사용자 지정 애플리케이션 도메인을 사용하려는 경우 다음 링크가 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-375">If you're interested in trying to use a custom Application Domain, the following links might help:</span></span>

- [<span data-ttu-id="fa520-376">애플리케이션 도메인에 관한 개념 설명서</span><span class="sxs-lookup"><span data-stu-id="fa520-376">Conceptual documentation on Application Domains</span></span>](/dotnet/framework/app-domains/application-domains)
- [<span data-ttu-id="fa520-377">애플리케이션 도메인 사용 예제</span><span class="sxs-lookup"><span data-stu-id="fa520-377">Examples for using Application Domains</span></span>](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a><span data-ttu-id="fa520-378">PowerShell에서 작동하지 않는 종속성 충돌의 솔루션</span><span class="sxs-lookup"><span data-stu-id="fa520-378">Solutions for dependency conflicts that don't work for PowerShell</span></span>

<span data-ttu-id="fa520-379">마지막으로, 유망해 보일 수 있지만 일반적으로 PowerShell에서 작동하지 않는 .NET 종속성 충돌을 .NET에서 조사할 때 나타나는 몇 가지 가능성을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-379">Finally, we'll address some possibilities that come up when researching .NET dependency conflicts in .NET that can look promising, but generally won't work for PowerShell.</span></span>

<span data-ttu-id="fa520-380">해당 솔루션에는 애플리케이션 및 가능한 경우 전체 머신을 제어하는 환경에 관한 배포 구성의 변경 내용이라는 일반적인 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-380">These solutions have the common theme that they are changes to deployment configurations for an environment where you control the application and possibly the entire machine.</span></span> <span data-ttu-id="fa520-381">해당 솔루션은 웹 서버 및 서버 환경에 배포된 기타 애플리케이션과 같은 시나리오를 기반으로 합니다. 이 경우 환경은 애플리케이션을 호스트하는 데 사용되며 배포하는 사용자가 자유롭게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-381">These solutions are oriented toward scenarios like web servers and other applications deployed to server environments, where the environment is intended to host the application and is free to be configured by the deploying user.</span></span> <span data-ttu-id="fa520-382">또한 대부분 .NET Framework를 기반으로 하는 경향이 있으므로 PowerShell 6 이상에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-382">They also tend to be very much .NET Framework oriented, meaning they do not work with PowerShell 6 or above.</span></span>

<span data-ttu-id="fa520-383">모듈이 전체 제어 권한이 있는 Windows PowerShell 5.1 환경에서만 사용되는 것을 알고 있으면 해당 솔루션 중 일부가 옵션일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-383">If you know that your module is only used in Windows PowerShell 5.1 environments that you have total control over, some of these may be options.</span></span> <span data-ttu-id="fa520-384">그러나 일반적으로 **모듈은 이처럼 전역 머신 상태를 수정하면 안 됩니다**.</span><span class="sxs-lookup"><span data-stu-id="fa520-384">In general however, **modules should not modify global machine state like this**.</span></span> <span data-ttu-id="fa520-385">수정하는 경우 `powershell.exe`에서 문제를 일으키는 구성이 중단되거나 예기치 않게 모듈 실패를 일으키는 기타 종속 애플리케이션이 중단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-385">It can break configurations that cause problems in `powershell.exe`, other modules, or other dependent applications that cause your module to fail in unexpected ways.</span></span>

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a><span data-ttu-id="fa520-386">동일한 종속성 버전을 강제로 사용하기 위한 app.config를 통한 정적 바인딩 리디렉션</span><span class="sxs-lookup"><span data-stu-id="fa520-386">Static binding redirect with app.config to force using the same dependency version</span></span>

<span data-ttu-id="fa520-387">.NET Framework 애플리케이션은 `app.config` 파일을 활용하여 일부 애플리케이션 동작을 선언적으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-387">.NET Framework applications can take advantage of an `app.config` file to configure some of the application's behaviors declaratively.</span></span> <span data-ttu-id="fa520-388">어셈블리 로딩을 특정 버전으로 리디렉션하도록 어셈블리 바인딩을 구성하는 `app.config` 항목을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-388">It's possible to write an `app.config` entry that configures assembly binding to redirect assembly loading to a particular version.</span></span>

<span data-ttu-id="fa520-389">PowerShell에서 해당 솔루션과 관련된 두 가지 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-389">Two issues with this for PowerShell are:</span></span>

- <span data-ttu-id="fa520-390">.NET Core는 `app.config`를 지원하지 않으므로 해당 솔루션은 `powershell.exe`에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-390">.NET Core does not support `app.config`, so this solution only applies to `powershell.exe`.</span></span>
- <span data-ttu-id="fa520-391">`powershell.exe`는 `System32` 디렉터리에 있는 공유 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-391">`powershell.exe` is a shared application that lives in the `System32` directory.</span></span> <span data-ttu-id="fa520-392">해당 모듈은 대부분의 시스템에서 관련 콘텐츠를 수정할 수 없을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-392">It's likely that your module won't be able to modify its contents on many systems.</span></span> <span data-ttu-id="fa520-393">수정할 수 있더라도 `app.config`를 수정하면 기존 구성이 중단되거나 다른 모듈의 로딩에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-393">Even if it can, modifying the `app.config` could break an existing configuration or affect the loading of other modules.</span></span>

### <a name="setting-codebase-with-appconfig"></a><span data-ttu-id="fa520-394">app.config를 사용하여 `codebase` 설정</span><span class="sxs-lookup"><span data-stu-id="fa520-394">Setting `codebase` with app.config</span></span>

<span data-ttu-id="fa520-395">동일한 이유로 `app.config`에서 `codebase` 설정을 구성하려고 하면 PowerShell 모듈에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-395">For the same reasons, trying to configure the `codebase` setting in `app.config` is not going to work in PowerShell modules.</span></span>

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a><span data-ttu-id="fa520-396">GAC(전역 어셈블리 캐시)에 종속성 설치</span><span class="sxs-lookup"><span data-stu-id="fa520-396">Installing dependencies to the Global Assembly Cache (GAC)</span></span>

<span data-ttu-id="fa520-397">.NET Framework에서 종속성 버전 충돌을 해결하는 또 다른 방법은 GAC에서 다양한 버전을 나란히 로드할 수 있도록 GAC에 종속성을 설치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-397">Another way to resolve dependency version conflicts in .NET Framework is to install dependencies to the GAC, so that different versions can be loaded side-by-side from the GAC.</span></span>

<span data-ttu-id="fa520-398">PowerShell 모듈의 경우 주요 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-398">Again, for PowerShell modules, the chief issues here are:</span></span>

- <span data-ttu-id="fa520-399">GAC는 .NET Framework에만 적용되므로 PowerShell 6 이상에서는 해당 방법이 도움이 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-399">The GAC only applies to .NET Framework, so this does not help in PowerShell 6 and above.</span></span>
- <span data-ttu-id="fa520-400">GAC에 어셈블리를 설치하는 것은 전역 머신 상태를 수정하는 것이며 다른 애플리케이션 또는 다른 모듈에서 부작용을 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-400">Installing assemblies to the GAC is a modification of global machine state and may cause side-effects in other applications or to other modules.</span></span> <span data-ttu-id="fa520-401">또한 모듈에 필요한 액세스 권한이 있는 경우에도 작업을 제대로 수행하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-401">It may also be difficult to do correctly, even when your module has the required access privileges.</span></span> <span data-ttu-id="fa520-402">작업이 잘못되면 다른 .NET 애플리케이션에서 머신 전체의 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-402">Getting it wrong could cause serious, machine-wide issues in other .NET applications.</span></span>

## <a name="further-reading"></a><span data-ttu-id="fa520-403">추가 정보</span><span class="sxs-lookup"><span data-stu-id="fa520-403">Further reading</span></span>

<span data-ttu-id="fa520-404">.NET 어셈블리 버전 종속성 충돌에 관한 많은 자료를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-404">There's plenty more to read on .NET assembly version dependency conflicts.</span></span> <span data-ttu-id="fa520-405">몇 가지 좋은 출발점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa520-405">Here are some nice jumping off points:</span></span>

- [<span data-ttu-id="fa520-406">.NET: .NET의 어셈블리</span><span class="sxs-lookup"><span data-stu-id="fa520-406">.NET: Assemblies in .NET</span></span>](/dotnet/standard/assembly/)
- [<span data-ttu-id="fa520-407">.NET Core: 관리형 어셈블리 로딩 알고리즘</span><span class="sxs-lookup"><span data-stu-id="fa520-407">.NET Core: The managed assembly loading algorithm</span></span>](/dotnet/core/dependency-loading/loading-managed)
- [<span data-ttu-id="fa520-408">.NET Core: System.Runtime.Loader.AssemblyLoadContext 이해</span><span class="sxs-lookup"><span data-stu-id="fa520-408">.NET Core: Understanding System.Runtime.Loader.AssemblyLoadContext</span></span>](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [<span data-ttu-id="fa520-409">.NET Core: 나란히 어셈블리 로딩 솔루션에 관한 설명</span><span class="sxs-lookup"><span data-stu-id="fa520-409">.NET Core: Discussion about side-by-side assembly loading solutions</span></span>](https://github.com/dotnet/runtime/issues/13471)
- [<span data-ttu-id="fa520-410">.NET Framework: 어셈블리 버전 리디렉션</span><span class="sxs-lookup"><span data-stu-id="fa520-410">.NET Framework: Redirecting assembly versions</span></span>](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [<span data-ttu-id="fa520-411">.NET Framework: 어셈블리 로딩 모범 사례</span><span class="sxs-lookup"><span data-stu-id="fa520-411">.NET Framework: Best practices for assembly loading</span></span>](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [<span data-ttu-id="fa520-412">.NET Framework: 런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="fa520-412">.NET Framework: How the runtime locates assemblies</span></span>](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [<span data-ttu-id="fa520-413">.NET Framework: 어셈블리 로드 확인</span><span class="sxs-lookup"><span data-stu-id="fa520-413">.NET Framework: Resolve assembly loads</span></span>](/dotnet/standard/assembly/resolve-loads)
- [<span data-ttu-id="fa520-414">StackOverflow: 어셈블리 바인딩 리디렉션, 방법 및 이유</span><span class="sxs-lookup"><span data-stu-id="fa520-414">StackOverflow: Assembly binding redirect, how and why?</span></span>](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)
- [<span data-ttu-id="fa520-415">PowerShell: AssemblyLoadContexts 구현에 관한 설명</span><span class="sxs-lookup"><span data-stu-id="fa520-415">PowerShell: Discussion about implementing AssemblyLoadContexts</span></span>](https://github.com/PowerShell/PowerShell/issues/11571)
- [<span data-ttu-id="fa520-416">PowerShell: `Assembly.LoadFile()`이 기본 AssemblyLoadContext에 로드되지 않음</span><span class="sxs-lookup"><span data-stu-id="fa520-416">PowerShell: `Assembly.LoadFile()` doesn't load into default AssemblyLoadContext</span></span>](https://github.com/PowerShell/PowerShell/issues/12052)
- [<span data-ttu-id="fa520-417">Rick Strahl: .NET 어셈블리 종속성이 로드되는 시기는 언제인가요?</span><span class="sxs-lookup"><span data-stu-id="fa520-417">Rick Strahl: When does a .NET assembly dependency get loaded?</span></span>](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)
- [<span data-ttu-id="fa520-418">Jon Skeet: .NET의 버전 지정 요약</span><span class="sxs-lookup"><span data-stu-id="fa520-418">Jon Skeet: Summary of versioning in .NET</span></span>](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- [<span data-ttu-id="fa520-419">Nate McMaster: .NET Core 기본 형식에 관해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="fa520-419">Nate McMaster: Deep dive into .NET Core primitives</span></span>](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)
