---
ms.date: 01/10/2020
keywords: powershell,cmdlet
title: 이식 가능한 모듈 작성
ms.openlocfilehash: 124e6efadfd07b8c5214a5c0446b1589f7142388
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809619"
---
# <a name="portable-modules"></a><span data-ttu-id="1798c-103">이식 가능한 모듈</span><span class="sxs-lookup"><span data-stu-id="1798c-103">Portable Modules</span></span>

<span data-ttu-id="1798c-104">Windows PowerShell은 [.NET Framework][]용으로 작성되지만 PowerShell Core는 [.NET Core][]용으로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="1798c-105">이식 가능한 모듈은 Windows PowerShell 및 PowerShell Core에서 모두 작동하는 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="1798c-106">.NET Framework 및 .NET Core는 호환성이 높지만 사용 가능한 API에는 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="1798c-107">Windows PowerShell 및 PowerShell Core에서 사용할 수 있는 API에도 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="1798c-108">두 환경에서 모두 사용할 수 있는 모듈이 이 차이를 인식해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="1798c-109">기존 모듈 이식</span><span class="sxs-lookup"><span data-stu-id="1798c-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="1798c-110">PSSnapIn 이식</span><span class="sxs-lookup"><span data-stu-id="1798c-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="1798c-111">PowerShell [스냅인](/powershell/scripting/developer/cmdlet/modules-and-snap-ins)은 PowerShell Core에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-111">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="1798c-112">그러나 PSSnapIn을 PowerShell 모듈로 변환하는 것은 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="1798c-113">일반적으로 PSSnapIn 등록 코드는 [PSSnapIn][]에서 파생되는 클래스의 단일 원본 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span>
<span data-ttu-id="1798c-114">빌드에서 이 원본 파일을 제거하세요. 이 파일은 더 이상 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="1798c-115">[New-ModuleManifest][]를 사용하여 PSSnapIn 등록 코드를 사용할 필요가 없는 새 모듈 매니페스트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="1798c-116">**PSSnapIn**의 일부 값(예: **Description**)은 모듈 매니페스트 내에서 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-116">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span></span>

<span data-ttu-id="1798c-117">모듈 매니페스트의 **RootModule** 속성은 cmdlet을 구현하는 어셈블리(dll)의 이름으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-117">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="1798c-118">.NET 이식성 분석기(APIPort)</span><span class="sxs-lookup"><span data-stu-id="1798c-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="1798c-119">Windows PowerShell용으로 작성된 모듈을 PowerShell Core에서 작동하도록 이식하려면 [.NET 이식성 분석기][]로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="1798c-120">컴파일된 어셈블리에서 이 도구를 실행하여 모듈에서 사용되는 .NET API가 .NET Framework, .NET Core 및 기타 .NET 런타임과 호환되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="1798c-121">대체 API가 있는 경우, 이 도구에서는 대체 API를 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="1798c-122">제안이 없는 경우 [런타임 검사][]를 추가하고 특정 런타임에서 사용할 수 없는 기능을 제한해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="1798c-123">새 모듈 만들기</span><span class="sxs-lookup"><span data-stu-id="1798c-123">Creating a New Module</span></span>

<span data-ttu-id="1798c-124">새 모듈을 만드는 경우 [.NET CLI][]를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="1798c-125">PowerShell Standard 모듈 템플릿 설치</span><span class="sxs-lookup"><span data-stu-id="1798c-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="1798c-126">.NET CLI가 설치된 후 템플릿 라이브러리를 설치하여 간단한 PowerShell 모듈을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="1798c-127">이 모듈은 Windows PowerShell, PowerShell Core, Windows, Linux 및 macOS와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="1798c-128">다음 예제에서는 템플릿 설치 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-128">The following example shows how to install the template:</span></span>

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

### <a name="creating-a-new-module-project"></a><span data-ttu-id="1798c-129">새 모듈 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="1798c-129">Creating a New Module Project</span></span>

<span data-ttu-id="1798c-130">템플릿이 설치된 후 템플릿을 사용하여 새 PowerShell 모듈 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="1798c-131">이 예제에서 샘플 모듈을 'myModule'이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-131">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="1798c-132">모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="1798c-132">Building the Module</span></span>

<span data-ttu-id="1798c-133">표준 .NET CLI 명령을 사용하여 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-133">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="1798c-134">모듈 테스트</span><span class="sxs-lookup"><span data-stu-id="1798c-134">Testing the Module</span></span>

<span data-ttu-id="1798c-135">모듈을 빌드한 후 모듈을 가져오고 샘플 cmdlet을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

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

<span data-ttu-id="1798c-136">다음 섹션에서는 이 템플릿에서 사용되는 일부 기술을 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="1798c-137">.NET Standard 라이브러리</span><span class="sxs-lookup"><span data-stu-id="1798c-137">.NET Standard Library</span></span>

<span data-ttu-id="1798c-138">[.NET Standard][]는 모든 .NET 구현에서 사용할 수 있는 .NET API의 공식 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="1798c-139">.NET Standard를 대상으로 하는 관리 코드는 .NET Standard의 해당 버전과 호환되는 .NET Framework 및 .NET Core 버전에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="1798c-140">.NET Standard에 API가 있을 수 있지만 .NET Core의 API 구현에서 런타임에 `PlatformNotSupportedException`이 throw될 수 있으므로, Windows PowerShell 및 PowerShell Core와 호환되는지 확인하려면 두 환경에서 모두 모듈 테스트를 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="1798c-141">모듈을 플랫폼 간에 사용해야 하는 경우 Linux 및 macOS에서도 테스트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="1798c-142">.NET Standard를 대상으로 지정하면 모듈이 발전됨에 따라 호환되지 않은 API가 실수로 모듈에 도입되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="1798c-143">비호환성은 런타임이 아니라 컴파일 시간에 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="1798c-144">그러나 호환되는 API를 사용한다면 모듈을 Windows PowerShell 및 PowerShell Core에서 모두 작동하기 위해 .NET Standard를 대상으로 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="1798c-145">IL(중간 언어)은 두 런타임 간에 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="1798c-146">.NET Standard 2.0과 호환되는 .NET Framework 4.6.1을 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="1798c-147">.NET Standard 2.0 외부에서 API를 사용하지 않는 경우에는 다시 컴파일하지 않고도 모듈이 PowerShell Core 6에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="1798c-148">PowerShell Standard Library</span><span class="sxs-lookup"><span data-stu-id="1798c-148">PowerShell Standard Library</span></span>

<span data-ttu-id="1798c-149">[PowerShell Standard][] 라이브러리는 해당 표준 버전 이상의 모든 PowerShell 버전에서 사용할 수 있는 PowerShell API의 공식 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="1798c-150">예를 들어 [PowerShell Standard 5.1][]은 Windows PowerShell 5.1 및 PowerShell Core 6.0 이상과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="1798c-151">PowerShell Standard Library를 사용하여 모듈을 컴파일하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="1798c-152">라이브러리를 사용하면 API가 Windows PowerShell 및 PowerShell Core 6에서 모두 사용 가능하고 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="1798c-153">PowerShell Standard는 항상 상위 버전과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="1798c-154">PowerShell Standard Library 5.1을 사용하여 구축된 모듈은 항상 PowerShell의 상위 버전과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="1798c-155">모듈 매니페스트</span><span class="sxs-lookup"><span data-stu-id="1798c-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="1798c-156">Windows PowerShell 및 PowerShell Core와의 호환성 표시</span><span class="sxs-lookup"><span data-stu-id="1798c-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="1798c-157">모듈이 Windows PowerShell 및 PowerShell Core에서 모두 작동하는지 유효성을 검사한 후 모듈 매니페스트에서 [CompatiblePSEditions][] 속성을 사용하여 호환성을 명시적으로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="1798c-158">`Desktop` 값은 모듈이 Windows PowerShell과 호환됨을 의미하지만, `Core` 값은 모듈이 PowerShell Core와 호환됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="1798c-159">`Desktop` 및 `Core`를 둘 다 포함하면 모듈이 Windows PowerShell 및 PowerShell Core와 모두 호환됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="1798c-160">`Core`는 자동으로 모듈이 Windows, Linux 및 macOS아 호환됨을 의미하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="1798c-161">**CompatiblePSEditions** 속성은 PowerShell v5에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="1798c-162">**CompatiblePSEditions** 속성을 사용하는 모듈 매니페스트는 PowerShell v5 이전 버전에 로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="1798c-163">OS 호환성 표시</span><span class="sxs-lookup"><span data-stu-id="1798c-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="1798c-164">먼저 모듈이 Linux 및 macOS에서 작동하는지 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="1798c-165">다음으로, 모듈 매니페스트에서 해당 운영 체제와의 호환성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="1798c-166">이렇게 하면 모듈이 [PowerShell 갤러리][]에 게시되는 경우 사용자가 사용 중인 운영 체제용 모듈을 더 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="1798c-167">모듈 매니페스트 내에서 `PrivateData` 속성에는 `PSData` 하위 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="1798c-168">`PSData`의 선택적 `Tags` 속성은 PowerShell 갤러리에 표시되는 값 배열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="1798c-169">PowerShell 갤러리는 다음 호환성 값을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="1798c-170">태그</span><span class="sxs-lookup"><span data-stu-id="1798c-170">Tag</span></span>               | <span data-ttu-id="1798c-171">Description</span><span class="sxs-lookup"><span data-stu-id="1798c-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="1798c-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="1798c-172">PSEdition_Core</span></span>    | <span data-ttu-id="1798c-173">PowerShell Core 6과 호환 가능</span><span class="sxs-lookup"><span data-stu-id="1798c-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="1798c-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="1798c-174">PSEdition_Desktop</span></span> | <span data-ttu-id="1798c-175">Windows PowerShell과 호환 가능</span><span class="sxs-lookup"><span data-stu-id="1798c-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="1798c-176">Windows</span><span class="sxs-lookup"><span data-stu-id="1798c-176">Windows</span></span>           | <span data-ttu-id="1798c-177">Windows와 호환 가능</span><span class="sxs-lookup"><span data-stu-id="1798c-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="1798c-178">Linux</span><span class="sxs-lookup"><span data-stu-id="1798c-178">Linux</span></span>             | <span data-ttu-id="1798c-179">Linux와 호환 가능(특정 배포판 없음)</span><span class="sxs-lookup"><span data-stu-id="1798c-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="1798c-180">macOS</span><span class="sxs-lookup"><span data-stu-id="1798c-180">macOS</span></span>             | <span data-ttu-id="1798c-181">macOS와 호환 가능</span><span class="sxs-lookup"><span data-stu-id="1798c-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="1798c-182">예제:</span><span class="sxs-lookup"><span data-stu-id="1798c-182">Example:</span></span>

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

## <a name="dependency-on-native-libraries"></a><span data-ttu-id="1798c-183">네이티브 라이브러리에 대한 종속성</span><span class="sxs-lookup"><span data-stu-id="1798c-183">Dependency on Native Libraries</span></span>

<span data-ttu-id="1798c-184">여러 운영 체제 또는 프로세서 아키텍처에서 사용하기 위한 모듈은 자체적으로 일부 네이티브 라이브러리에 종속된 관리되는 라이브러리에 종속될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-184">Modules intended for use across different operating systems or processor architectures may depend on a managed library that itself depends on some native libraries.</span></span>

<span data-ttu-id="1798c-185">PowerShell 7 이전 버전에서는 관리되는 라이브러리가 제대로 찾을 수 있도록 적절한 네이티브 dll을 로드하는 사용자 지정 코드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-185">Prior to PowerShell 7, one would have to have custom code to load the appropriate native dll so that the managed library can find it correctly.</span></span>

<span data-ttu-id="1798c-186">PowerShell 7에서는 [.NET RID 카탈로그][] 표기법의 하위 집합에 따라 로드할 네이티브 이진 파일을 관리되는 라이브러리의 위치에 있는 하위 폴더에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1798c-186">With PowerShell 7, native binaries to load are searched in sub-folders within the managed library's location following a subset of the [.NET RID Catalog][] notation.</span></span>

```
managed.dll folder
                |
                |--- 'win-x64' folder
                |       |--- native.dll
                |
                |--- 'win-x86' folder
                |       |--- native.dll
                |
                |--- 'win-arm' folder
                |       |--- native.dll
                |
                |--- 'win-arm64' folder
                |       |--- native.dll
                |
                |--- 'linux-x64' folder
                |       |--- native.so
                |
                |--- 'linux-x86' folder
                |       |--- native.so
                |
                |--- 'linux-arm' folder
                |       |--- native.so
                |
                |--- 'linux-arm64' folder
                |       |--- native.so
                |
                |--- 'osx-x64' folder
                |       |--- native.dylib
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
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 갤러리]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET 이식성 분석기]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET RID 카탈로그]: https://docs.microsoft.com/dotnet/core/rid-catalog
[.NET RID Catalog]: https://docs.microsoft.com/dotnet/core/rid-catalog
