---
ms.date: 12/14/2018
keywords: powershell,cmdlet
title: 이식 가능한 모듈 작성
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682553"
---
# <a name="portable-modules"></a><span data-ttu-id="200c0-103">이식 가능한 모듈</span><span class="sxs-lookup"><span data-stu-id="200c0-103">Portable Modules</span></span>

<span data-ttu-id="200c0-104">Windows PowerShell 기록 됩니다 [.NET Framework][] PowerShell Core는 작성 하는 동안 [.NET Core][]합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="200c0-105">이식 가능한 모듈은 Windows PowerShell과 PowerShell Core에서 작동 하는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="200c0-106">.NET Framework 및.NET Core는 호환성이, 둘 사이의 차이점은 사용 가능한 api가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="200c0-107">차이점도 있습니다 Api에서 Windows PowerShell 및 PowerShell Core에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="200c0-108">두 환경 모두에서 사용할 모듈의 이러한 차이점을 알도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="200c0-109">기존 모듈 이식</span><span class="sxs-lookup"><span data-stu-id="200c0-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="200c0-110">PSSnapIn 이식</span><span class="sxs-lookup"><span data-stu-id="200c0-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="200c0-111">PowerShell 스냅인 (PSSnapIn)는 PowerShell Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="200c0-112">그러나 PowerShell 모듈에 PSSnapIn을 변환 하는 것이 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="200c0-113">파생 된 클래스의 단일 소스 파일로 PSSnapIn 등록 코드는 일반적으로 [PSSnapIn][]합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="200c0-114">빌드에서;이 소스 파일을 제거 합니다. 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="200c0-115">사용 하 여 [New-modulemanifest][] PSSnapIn 등록 코드를 대체 하는 새 모듈 매니페스트를 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="200c0-116">모듈 매니페스트 내에서 (예: 설명) PSSnapIn 값 중 일부를 재사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="200c0-117">`RootModule` 모듈 매니페스트에 속성 cmdlet을 구현 하는 어셈블리 (dll)의 이름으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="200c0-118">.NET Portability Analyzer (APIPort 라고도 함)</span><span class="sxs-lookup"><span data-stu-id="200c0-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="200c0-119">PowerShell Core를 사용 하 여 작업을 시작 하려면 Windows PowerShell 용으로 작성 하는 포트 모듈에는 [.NET 이식성 분석기][]합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="200c0-120">모듈에 사용 되는.NET Api를.NET Framework,.NET Core 및 다른.NET 런타임을 사용 하 여 호환 되는 경우를 확인 하 여 컴파일된 어셈블리에 대해이 도구를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="200c0-121">있는 경우 대체 Api를 제안 하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="200c0-122">추가 해야 하는 고, 그렇지 [런타임 검사][] 특정 런타임에서 사용할 수 없는 기능을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="200c0-123">새 모듈을 만드는 중</span><span class="sxs-lookup"><span data-stu-id="200c0-123">Creating a New Module</span></span>

<span data-ttu-id="200c0-124">새 모듈을 만드는 경우 사용 하는 것이 좋습니다 합니다 [.NET CLI][]합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="200c0-125">표준 PowerShell 모듈 템플릿 설치</span><span class="sxs-lookup"><span data-stu-id="200c0-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="200c0-126">.NET CLI가 설치 되 면 간단한 PowerShell 모듈을 생성 하는 템플릿 라이브러리를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="200c0-127">모듈은 Windows PowerShell, PowerShell Core, Windows, Linux 및 macOS와 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="200c0-128">다음 예제에서는 서식 파일을 설치 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-128">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="200c0-129">새 모듈 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="200c0-129">Creating a New Module Project</span></span>

<span data-ttu-id="200c0-130">템플릿이 설치 된 후 해당 템플릿을 사용 하 여 새 PowerShell 모듈 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="200c0-131">이 예제에서는 샘플 모듈 'myModule' 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-131">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="200c0-132">모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="200c0-132">Building the Module</span></span>

<span data-ttu-id="200c0-133">표준.NET CLI 명령을 사용 하 여 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-133">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="200c0-134">테스트 모듈</span><span class="sxs-lookup"><span data-stu-id="200c0-134">Testing the Module</span></span>

<span data-ttu-id="200c0-135">모듈을 빌드한 후 가져올 수 있으며 샘플 cmdlet을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="200c0-136">다음 섹션에서는이 템플릿에서 사용 되는 기술 중 일부에 대해 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="200c0-137">.NET 표준 라이브러리</span><span class="sxs-lookup"><span data-stu-id="200c0-137">.NET Standard Library</span></span>

<span data-ttu-id="200c0-138">[.NET standard][] 는 모든.NET 구현에서 사용할 수 있는.NET Api의 공식 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="200c0-139">.NET Standard 호환 해당 버전의.NET Standard를 사용 하 여 호환 되는.NET Framework 및.NET Core 버전을 대상으로 하는 코드를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="200c0-140">.NET standard API 있을 수 있지만.NET core에서 API 구현 throw 될 수 있습니다는 `PlatformNotSupportedException` 런타임에 하므로 Windows PowerShell 및 PowerShell Core를 사용 하 여 호환성을 확인 하려면 것이 좋습니다 두 환경 내에서 모듈에 대 한 테스트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="200c0-141">모듈 간 플랫폼을 사용할 경우 Linux 및 macOS에서 테스트를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="200c0-142">.NET 표준을 대상으로 하는 모듈 진화 함에 따라 호환 되지 않는 Api 없는 실수로 도입 되어 모듈로 확인 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="200c0-143">런타임 대신 컴파일 타임에 비 호환성 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="200c0-144">그러나 필요는 없습니다.NET 표준을 대상 모듈에 대 한 Windows PowerShell과 PowerShell Core를 사용 하려면 호환 되는 Api를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="200c0-145">IL (Intermediate Language)는 두 런타임 간 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="200c0-146">.NET Standard 2.0 호환 되는.NET Framework 4.6.1을 대상 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="200c0-147">.NET Standard 2.0 외부 Api를 사용 하지 않는 경우 다음 모듈 작동 PowerShell Core 6을 사용 하 여 다시 컴파일하지 않고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="200c0-148">PowerShell 표준 라이브러리</span><span class="sxs-lookup"><span data-stu-id="200c0-148">PowerShell Standard Library</span></span>

<span data-ttu-id="200c0-149">합니다 [PowerShell 표준][] 라이브러리는 해당 표준의 버전 보다 크거나 같은 경우 모든 PowerShell 버전에서 사용할 수 있는 PowerShell Api의 공식 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="200c0-150">예를 들어 [PowerShell 5.1 표준][] 이상 Windows PowerShell 5.1 및 PowerShell Core 6.0 모두와 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="200c0-151">PowerShell 표준 라이브러리를 사용 하 여 모듈을 컴파일하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="200c0-152">라이브러리를 사용 하면 Api를 사용 가능 하 고 Windows PowerShell 및 PowerShell Core 6에서 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="200c0-153">PowerShell 표준 반드시 전달 호환이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="200c0-154">표준 라이브러리 5.1 PowerShell을 사용 하 여 빌드된 모듈은 항상 PowerShell의 이후 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="200c0-155">모듈 매니페스트</span><span class="sxs-lookup"><span data-stu-id="200c0-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="200c0-156">Windows PowerShell 및 PowerShell Core를 사용 하 여 호환성을 나타내는</span><span class="sxs-lookup"><span data-stu-id="200c0-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="200c0-157">Windows PowerShell과 PowerShell Core를 사용 하 여 모듈 작동 하는지 유효성을 검사 한 후 모듈 매니페스트의 명시적으로 나타내야 호환성을 사용 하 여 합니다 [CompatiblePSEditions][] 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="200c0-158">값이 `Desktop` 모듈의 값 하는 동안 Windows PowerShell을 사용 하 여 호환 임을 의미 `Core` 모듈이 PowerShell Core와 호환 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="200c0-159">둘 다를 포함 하 여 `Desktop` 고 `Core` 모듈은 Windows PowerShell과 PowerShell Core와 호환 되는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="200c0-160">`Core` 자동으로 의미가 아니라 모듈은 Windows, Linux 및 macOS를 사용 하 여 호환 되는 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="200c0-161">합니다 **CompatiblePSEditions** 속성 PowerShell v5에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="200c0-162">모듈 매니페스트를 사용 하는 합니다 **CompatiblePSEditions** 속성 PowerShell v5 이전 버전에서 로드 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="200c0-163">OS 호환성을 나타내는</span><span class="sxs-lookup"><span data-stu-id="200c0-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="200c0-164">먼저 모듈 Linux 및 macOS에서 작동 하는지 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="200c0-165">그런 다음 모듈 매니페스트에서 이러한 운영 체제와의 호환성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="200c0-166">이렇게 하면 쉽게 게시 하는 경우 해당 운영 체제에 대 한 모듈을 찾을 수 있습니다 합니다 [PowerShell 갤러리][]합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="200c0-167">모듈 매니페스트 내 합니다 `PrivateData` 속성에는 `PSData` 하위 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="200c0-168">선택적 `Tags` 속성의 `PSData` PowerShell 갤러리에 표시 되는 값 배열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="200c0-169">PowerShell 갤러리에는 다음 호환성 값을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="200c0-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="200c0-170">태그</span><span class="sxs-lookup"><span data-stu-id="200c0-170">Tag</span></span>               | <span data-ttu-id="200c0-171">설명</span><span class="sxs-lookup"><span data-stu-id="200c0-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="200c0-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="200c0-172">PSEdition_Core</span></span>    | <span data-ttu-id="200c0-173">PowerShell Core 6와 호환</span><span class="sxs-lookup"><span data-stu-id="200c0-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="200c0-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="200c0-174">PSEdition_Desktop</span></span> | <span data-ttu-id="200c0-175">Windows PowerShell을 사용 하 여 호환</span><span class="sxs-lookup"><span data-stu-id="200c0-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="200c0-176">Windows</span><span class="sxs-lookup"><span data-stu-id="200c0-176">Windows</span></span>           | <span data-ttu-id="200c0-177">Windows 호환</span><span class="sxs-lookup"><span data-stu-id="200c0-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="200c0-178">Linux</span><span class="sxs-lookup"><span data-stu-id="200c0-178">Linux</span></span>             | <span data-ttu-id="200c0-179">Linux (특정 배포판 없음)와 호환</span><span class="sxs-lookup"><span data-stu-id="200c0-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="200c0-180">macOS</span><span class="sxs-lookup"><span data-stu-id="200c0-180">macOS</span></span>             | <span data-ttu-id="200c0-181">호환 되는 macOS 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="200c0-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="200c0-182">예:</span><span class="sxs-lookup"><span data-stu-id="200c0-182">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[런타임 검사]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell 표준]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell 5.1 표준]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 갤러리]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET 이식성 분석기]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
