---
title: 표준 라이브러리 이진 모듈을 만드는 방법
description: PowerShell Standard Library를 사용하면 PowerShell Core와 Windows PowerShell 5.1 모두에서 작동하는 플랫폼 간 모듈을 만들 수 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 51734fd9232e7c33b11c6c5a6abddbcc1f28413c
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149416"
---
# <a name="how-to-create-a-standard-library-binary-module"></a><span data-ttu-id="58523-103">표준 라이브러리 이진 모듈을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="58523-103">How to create a Standard Library binary module</span></span>

<span data-ttu-id="58523-104">얼마 전 이진 모듈로 구현하고 싶은 모듈이 떠올랐습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-104">I recently had an idea for module that I wanted to implement as a binary module.</span></span> <span data-ttu-id="58523-105">[PowerShell Standard Library][]를 사용하여 만든 적이 없기 때문에 좋은 기회라고 생각했습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-105">I have yet to create one using the [PowerShell Standard Library][] so this felt like a good opportunity.</span></span> <span data-ttu-id="58523-106">[플랫폼 간 이진 모듈 만들기][] 가이드를 사용하여 어떤 장애물도 없이 이 모듈을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-106">I used the [Creating a cross-platform binary module][] guide to create this module without any roadblocks.</span></span>
<span data-ttu-id="58523-107">같은 프로세스를 진행하면서 약간의 추가 해설을 해드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-107">We're going to walk that same process and I'll add a little extra commentary along the way.</span></span>

> [!NOTE]
> <span data-ttu-id="58523-108">이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="58523-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="58523-109">PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="58523-110">[PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="58523-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-the-powershell-standard-library"></a><span data-ttu-id="58523-111">PowerShell Standard Library란 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="58523-111">What is the PowerShell Standard Library?</span></span>

<span data-ttu-id="58523-112">PowerShell Standard Library를 사용하면 PowerShell Core와 Windows PowerShell 5.1 (또는 3.0) 모두에서 작동하는 플랫폼 간 모듈을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-112">The PowerShell Standard Library allows us to create cross platform modules that work in both PowerShell Core and with Windows PowerShell 5.1 (or 3.0).</span></span>

## <a name="planning-our-module"></a><span data-ttu-id="58523-113">Microsoft 모듈 계획</span><span class="sxs-lookup"><span data-stu-id="58523-113">Planning our module</span></span>

<span data-ttu-id="58523-114">이 모듈의 목표는 C# 코드용 `src` 폴더를 만들고 나머지 요소는 스크립트 모듈처럼 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-114">The plan for this module is to create a `src` folder for the C# code and structure the rest like I would for a script module.</span></span> <span data-ttu-id="58523-115">여기에는 빌드 스크립트를 사용하여 모든 요소를 `output` 폴더에 컴파일하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-115">This includes using a build script to compile everything into an `output` folder.</span></span> <span data-ttu-id="58523-116">폴더 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-116">The folder structure looks like this:</span></span>

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a><span data-ttu-id="58523-117">시작하기</span><span class="sxs-lookup"><span data-stu-id="58523-117">Getting Started</span></span>

<span data-ttu-id="58523-118">보통 Plaster 템플릿을 사용하지만 현재 템플릿은 아직 이진 모듈을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-118">I normally use a Plaster template but my current template doesn't have any binary module support yet.</span></span> <span data-ttu-id="58523-119">큰 문제는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="58523-119">Not a big deal.</span></span> <span data-ttu-id="58523-120">이번에는 직접 만들어보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-120">I'll create this one by hand this time.</span></span>

<span data-ttu-id="58523-121">먼저 폴더를 만들고 git 리포지토리를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-121">First I need to create the folder and create the git repo.</span></span> <span data-ttu-id="58523-122">모듈 이름의 자리 표시자로 `$module`를 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-122">I'm using `$module` as a placeholder for the module name.</span></span> <span data-ttu-id="58523-123">이렇게 하면 필요할 때 이러한 예제를 쉽게 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-123">This should make it easier for you to reuse these examples if needed.</span></span>

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

<span data-ttu-id="58523-124">그런 다음 루트 수준 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="58523-124">Then create the root level folders.</span></span>

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a><span data-ttu-id="58523-125">이진 모듈 설정</span><span class="sxs-lookup"><span data-stu-id="58523-125">Binary module setup</span></span>

<span data-ttu-id="58523-126">이 문서의 주제는 이진 모듈이므로 이진 모듈부터 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-126">This article os focused on the binary module so that is where we'll start.</span></span> <span data-ttu-id="58523-127">이 섹션에서는 [플랫폼 간 이진 모듈 만들기][] 가이드의 예제를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-127">This section pulls examples from the [Creating a cross-platform binary module][] guide.</span></span> <span data-ttu-id="58523-128">자세한 내용을 알고 싶거나 문제가 있다면 이 가이드를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="58523-128">Review that guide if you need more details or have any issues.</span></span>

<span data-ttu-id="58523-129">가장 먼저 할 일은 설치한 [dotnet core SDK][]의 버전을 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-129">First thing we want to do is check the version of the [dotnet core SDK][] that we installed.</span></span> <span data-ttu-id="58523-130">2\.1.4를 사용하지만 2.0.0 이상이라면 작업을 계속 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-130">I'm using 2.1.4, but you should have 2.0.0 or newer before continuing.</span></span>

```powershell
PS> dotnet --version
2.1.4
```

<span data-ttu-id="58523-131">이 섹션에서는 `src` 폴더에서 작업을 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-131">I'm working out of the `src` folder for this section.</span></span>

```powershell
Set-Location 'src'
```

<span data-ttu-id="58523-132">dotnet 명령을 사용하여 새 클래스 라이브러리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="58523-132">Using the dotnet command, create a new class library.</span></span>

```powershell
dotnet new classlib --name $module
```

<span data-ttu-id="58523-133">하위 폴더에 라이브러리 폴더가 생성되지만 추가 중첩 수준은 원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-133">This created the library project in a subfolder but I don't want that extra level of nesting.</span></span> <span data-ttu-id="58523-134">이 파일들의 수준을 한 단계 올리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-134">I'm going to move those files up a level.</span></span>

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

<span data-ttu-id="58523-135">프로젝트의 .NET core SDK 버전을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-135">Set the .NET core SDK version for the project.</span></span> <span data-ttu-id="58523-136">2\.1 SDK를 이용하니 2.1.0을 지정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-136">I have the 2.1 SDK so I'm going to specify 2.1.0.</span></span>
<span data-ttu-id="58523-137">2\.0 SDK를 사용한다면 2.0.0를 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-137">Use 2.0.0 if you're using the 2.0 SDK.</span></span>

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

<span data-ttu-id="58523-138">PowerShell Standard Library [NuGet 패키지][]를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-138">Add the PowerShell Standard Library [NuGet package][] to the project.</span></span> <span data-ttu-id="58523-139">필요한 호환성 수준에 맞는 최신 버전을 사용하는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="58523-139">Make sure you use the most recent version available for the level of compatibility that you need.</span></span> <span data-ttu-id="58523-140">기본적으로 최신 버전을 사용하지만 이 모듈에서는 PowerShell 3.0 이상에서 제공하는 기능은 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-140">I would default to the latest version but I don't think this module leverages any features newer than PowerShell 3.0.</span></span>

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

<span data-ttu-id="58523-141">다음과 같은 src 폴더가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-141">We should have a src folder that looks like this:</span></span>

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

<span data-ttu-id="58523-142">이제 자체 코드를 프로젝트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-142">Now we're ready to add our own code to the project.</span></span>

### <a name="building-a-binary-cmdlet"></a><span data-ttu-id="58523-143">이진 cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="58523-143">Building a binary cmdlet</span></span>

<span data-ttu-id="58523-144">이 시작 cmdlet을 포함하도록 `src\Class1.cs`를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-144">We need to update the `src\Class1.cs` to contain this starter cmdlet:</span></span>

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

<span data-ttu-id="58523-145">클래스 이름과 일치하도록 파일 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="58523-145">Rename the file to match the class name.</span></span>

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

<span data-ttu-id="58523-146">그래야 모듈을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-146">Then we can build our module.</span></span>

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

<span data-ttu-id="58523-147">새 dll에서 `Import-Module`을 호출하면 새 CMDlet을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-147">We can call `Import-Module` on the new dll to load our new CMDlet.</span></span>

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

<span data-ttu-id="58523-148">시스템에서 가져오기에 실패한다면 .NET을 4.7.1 이상으로 업데이트하세요.</span><span class="sxs-lookup"><span data-stu-id="58523-148">If the import fails on your system, try updating .NET to 4.7.1 or newer.</span></span> <span data-ttu-id="58523-149">[플랫폼 간 이진 모듈 만들기][] 가이드에서 .NET 기존 버전에 대한 지원과 호환성 관련 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-149">The [Creating a cross-platform binary module][] guide goes into more details on .NET support and compatibility for older versions of .NET.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="58523-150">모듈 매니페스트</span><span class="sxs-lookup"><span data-stu-id="58523-150">Module manifest</span></span>

<span data-ttu-id="58523-151">다행히 우리는 dll을 가져오고 작업 모듈을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-151">It's cool that we can import the dll and have a working module.</span></span> <span data-ttu-id="58523-152">작업 모듈을 계속 이용해 모듈 매니페스트를 만들어보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-152">I like to keep going with it and create a module manifest.</span></span> <span data-ttu-id="58523-153">나중에 PSGallery에 게시하려면 매니페스트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-153">We need the manifest if we want to publish to the PSGallery later.</span></span>

<span data-ttu-id="58523-154">프로젝트의 루트에서 이 명령을 실행하면 필요한 모듈 매니페스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-154">From the root of our project, we can run this command to create the module manifest that we need.</span></span>

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

<span data-ttu-id="58523-155">이후 PowerShell 함수를 위한 빈 루트 모듈도 만들겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-155">I'm also going to create an empty root module for future PowerShell functions.</span></span>

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

<span data-ttu-id="58523-156">이렇게 하면 동일한 프로젝트에서 일반 PowerShell 함수와 이진 Cmdlet을 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-156">This allows me to mix both normal PowerShell functions and binary Cmdlets in the same project.</span></span>

### <a name="building-the-full-module"></a><span data-ttu-id="58523-157">전체 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="58523-157">Building the full module</span></span>

<span data-ttu-id="58523-158">모든 요소를 출력 폴더로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-158">I compile everything together into an output folder.</span></span> <span data-ttu-id="58523-159">이 작업을 수행하려면 빌드 스크립트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-159">We need to create a build script to do that.</span></span> <span data-ttu-id="58523-160">보통은 `Invoke-Build` 스크립트에 추가하지만 이번 예제에서는 간단하게 진행하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-160">I would normally add this to an `Invoke-Build` script, but we can keep it simple for this example.</span></span> <span data-ttu-id="58523-161">이 스크립트를 프로젝트 루트에 있는 `build.ps1`에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-161">Add this to a `build.ps1` at the root of the project.</span></span>

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

<span data-ttu-id="58523-162">이러한 명령은 DLL을 빌드하고 `output\$module\bin` 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-162">These commands build our DLL and place it into our `output\$module\bin` folder.</span></span> <span data-ttu-id="58523-163">그러면 다른 모듈 파일을 현재 위치로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-163">It then copies the other module files into place.</span></span>

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

<span data-ttu-id="58523-164">이 시점에서 psd1 파일을 사용하여 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-164">At this point, we can import our module with the psd1 file.</span></span>

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

<span data-ttu-id="58523-165">여기서 `.\Output\$module` 폴더를 `$env:PSModulePath` 디렉터리에 드롭하면 필요할 때마다 명령을 자동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-165">From here, we can drop the `.\Output\$module` folder into our `$env:PSModulePath` directory and it autoloads our command whenever we need it.</span></span>

### <a name="update-dotnet-new-psmodule"></a><span data-ttu-id="58523-166">업데이트: dotnet 신규 PSModule</span><span class="sxs-lookup"><span data-stu-id="58523-166">Update: dotnet new PSModule</span></span>

<span data-ttu-id="58523-167">`dotnet` 도구에 `PSModule` 템플릿이 있음을 알게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-167">I learned that the `dotnet` tool has a `PSModule` template.</span></span>

<span data-ttu-id="58523-168">위에서 설명한 모든 단계는 여전히 유효하지만 이 템플릿은 여러 단계를 생략합니다. 아직도 지속적으로 개선되고 있는 신규 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-168">All the steps that I outlined above are still valid, but this template cuts many pf them out. It's still a fairly new template that is still getting some polish placed on it.</span></span> <span data-ttu-id="58523-169">여기서도 계속 개선될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-169">Expect it to keep getting better from here.</span></span>

<span data-ttu-id="58523-170">PSModule 템플릿은 이런 식으로 설치하고 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-170">This is how you use install and use the PSModule template.</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

<span data-ttu-id="58523-171">최소 실행 가능 템플릿은 .NET SDK와 PowerShell Standard Library 추가를 처리하고 프로젝트에 예제 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="58523-171">This minimally-viable template takes care of adding the .NET SDK, PowerShell Standard Library, and creates an example class in the project.</span></span> <span data-ttu-id="58523-172">이 템플릿은 바로 빌드하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-172">You can build it and run it right away.</span></span>

## <a name="important-details"></a><span data-ttu-id="58523-173">중요 세부 정보</span><span class="sxs-lookup"><span data-stu-id="58523-173">Important details</span></span>

<span data-ttu-id="58523-174">이 문서를 끝내기 전에 다음과 같은 몇 가지 다른 세부 정보를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-174">Before we end this article, here are a few other details worth mentioning.</span></span>

### <a name="unloading-dlls"></a><span data-ttu-id="58523-175">DLL 언로드</span><span class="sxs-lookup"><span data-stu-id="58523-175">Unloading DLLs</span></span>

<span data-ttu-id="58523-176">이진 모듈이 로드되면 언로드할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-176">Once a binary module is loaded, you can't really unload it.</span></span> <span data-ttu-id="58523-177">DLL 파일은 사용자가 언로드할 때까지 잠금 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-177">The DLL file is locked until you unload it.</span></span> <span data-ttu-id="58523-178">변경 작업을 수행하고 빌드할 때마다 파일이 자주 잠기기 때문에 개발에 지장을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-178">This can be annoying when developing because every time you make a change and want to build it, the file is often locked.</span></span> <span data-ttu-id="58523-179">이 문제를 확실하게 해결하는 유일한 방법은 DLL을 로드한 PowerShell 세션을 닫는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-179">The only reliable way to resolve this is to close the PowerShell session that loaded the DLL.</span></span>

### <a name="vs-code-reload-window-action"></a><span data-ttu-id="58523-180">VS Code 창 다시 로드 작업</span><span class="sxs-lookup"><span data-stu-id="58523-180">VS Code reload window action</span></span>

<span data-ttu-id="58523-181">PowerShell 개발 작업 대부분을 [VS 코드][]에서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-181">I do most of my PowerShell dev work in [VS Code][].</span></span> <span data-ttu-id="58523-182">이진 모듈(또는 클래스가 포함된 모듈)에서 작업할 때는 빌드할 때마다 VS Code를 다시 로드하곤 했습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-182">When I'm working on a binary module (or a module with classes), I've gotten into the habit of reloading VS Code every time I build.</span></span>
<span data-ttu-id="58523-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>를 누르면 명령 창을 나타나며 `Reload Window`가 항상 목록 최상단에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> pops the command window and `Reload Window` is always at the top of my list.</span></span>

### <a name="nested-powershell-sessions"></a><span data-ttu-id="58523-184">중첩된 PowerShell 세션</span><span class="sxs-lookup"><span data-stu-id="58523-184">Nested PowerShell sessions</span></span>

<span data-ttu-id="58523-185">우수한 Pester 테스트 검사를 확보하는 것도 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-185">One other option is to have good Pester test coverage.</span></span> <span data-ttu-id="58523-186">그러면 build.ps1 스크립트를 수정하여 새 PowerShell 세션을 시작하고, 빌드를 수행하고, 테스트를 실행하고, 세션을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-186">Then you can adjust the build.ps1 script to start a new PowerShell session, perform the build, run the tests, and close the session.</span></span>

### <a name="updating-installed-modules"></a><span data-ttu-id="58523-187">설치된 모듈 업데이트</span><span class="sxs-lookup"><span data-stu-id="58523-187">Updating installed modules</span></span>

<span data-ttu-id="58523-188">로컬로 설치한 모듈을 업데이트할 때 이러한 잠금이 방해가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-188">This locking can be annoying when trying to update your locally installed module.</span></span> <span data-ttu-id="58523-189">모듈을 로드한 세션이 있다면 추적하여 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-189">If any session has it loaded, you have to go hunt it down and close it.</span></span> <span data-ttu-id="58523-190">PSGallery에서 설치할 때는 큰 문제가 되지 않는데, 모듈 버전 지정에서 새 모듈을 다른 폴더에 배치하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-190">This is less of an issue when installing from a PSGallery because module versioning places the new one in a different folder.</span></span>

<span data-ttu-id="58523-191">로컬 PSGallery를 설정하고 빌드의 일부로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-191">You can set up a local PSGallery and publish to that as part of your build.</span></span> <span data-ttu-id="58523-192">그러면 PSGallery에서 로컬 설치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-192">Then do your local install from that PSGallery.</span></span> <span data-ttu-id="58523-193">일이 많아 보이지만 docker 컨테이너를 시작하는 것만큼 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-193">This sounds like a lot of work, but this can be as simple as starting a docker container.</span></span> <span data-ttu-id="58523-194">[PSRepository에 NuGet 서버 사용][]이라는 제 게시물에서 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-194">I cover a way to do that in my post on [Using a NuGet server for a PSRepository][].</span></span>

## <a name="why-binary-modules"></a><span data-ttu-id="58523-195">이진 모듈이란 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="58523-195">Why binary modules?</span></span>

<span data-ttu-id="58523-196">이진 모듈을 만드는 방법부터 설명했고 만드는 이유는 설명하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-196">I jumped right into how to make a binary module and didn't mention why you want to make one.</span></span> <span data-ttu-id="58523-197">현실에서는 C#을 작성하고 PowerShell Cmdlet 및 함수에 대한 쉬운 액세스는 포기해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-197">In reality, you are writing C# and give up easy access to PowerShell Cmdlets and functions.</span></span> <span data-ttu-id="58523-198">바로 이점 때문에 이진 모듈을 바로 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-198">That is the main reason why I have not shifted to binary modules sooner.</span></span>

<span data-ttu-id="58523-199">하지만 다른 많은 PowerShell 명령에 의존하지 않는 모듈을 만든다면 성능 혜택이 대단히 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-199">But if you are creating a module that doesn't depend on a lot of other PowerShell commands, the performance benefit can be significant.</span></span> <span data-ttu-id="58523-200">C#에 드롭하면 PowerShell이 유발하는 오버헤드를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-200">By dropping into C#, you get to shed the overhead added by PowerShell.</span></span> <span data-ttu-id="58523-201">PowerShell은 컴퓨터가 아닌 관리자를 위해 최적화되었으며 따라서 약간의 오버헤드가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-201">PowerShell was optimized for the administrator, not the computer, and that adds a little overhead.</span></span>

<span data-ttu-id="58523-202">작업 시에는 JSON 및 해시 테이블을 이용해 수많은 일을 수행하는 중요 프로세스를 진행하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-202">At work, we have a critical process that does a lot of work with JSON and Hashtables.</span></span> <span data-ttu-id="58523-203">PowerShell을 최대한 최적화했지만 이 프로세스는 지금도 12분 동안 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-203">We optimized the PowerShell as much as we could but this process was still running for 12 minutes.</span></span> <span data-ttu-id="58523-204">모듈에는 이미 다양한 C# PowerShell이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-204">The module already contained a lot of C# style PowerShell.</span></span> <span data-ttu-id="58523-205">따라서 이진 모듈로의 변환을 쉽고 깔끔하게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-205">This made the conversion to a binary module clean and easy to do.</span></span> <span data-ttu-id="58523-206">변환 덕분에 프로세스 시간이 12분 이상에서 4분 이내로 단축되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-206">Our conversion cut that process down from over 12 minutes to under four minutes.</span></span>

### <a name="hybrid-modules"></a><span data-ttu-id="58523-207">하이브리드 모듈</span><span class="sxs-lookup"><span data-stu-id="58523-207">Hybrid modules</span></span>

<span data-ttu-id="58523-208">PowerShell 고급 함수를 사용하여 이진 Cmdlet을 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-208">You can mix binary Cmdlets with PowerShell advanced functions.</span></span> <span data-ttu-id="58523-209">이 가이드에서 수행하는 작업이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-209">That is exactly what I'm doing in this guide.</span></span> <span data-ttu-id="58523-210">스크립트 모듈 관련 사항은 모두 동일한 방식으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-210">You can take everything you know about script modules and it all applies the same way.</span></span>
<span data-ttu-id="58523-211">오늘 만든 빈 `psm1` 파일이 있으니 나중에 다른 PowerShell 함수에 드롭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-211">The empty `psm1` file that I created today is there just so you can drop in other PowerShell functions later.</span></span>

<span data-ttu-id="58523-212">우리가 만든 거의 모든 컴파일된 cmdlet은 먼저 PowerShell 함수로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="58523-212">Almost all of the compiled cmdlets that we created started out as a PowerShell function first.</span></span> <span data-ttu-id="58523-213">우리의 모든 이진 모듈은 실제로는 하이브리드 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-213">All of our binary modules are really hybrid modules.</span></span>

### <a name="build-scripts"></a><span data-ttu-id="58523-214">빌드 스크립트</span><span class="sxs-lookup"><span data-stu-id="58523-214">Build scripts</span></span>

<span data-ttu-id="58523-215">여기서는 간단한 빌드 스크립트만 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-215">I kept the build script simple here.</span></span> <span data-ttu-id="58523-216">보통은 긴 `Invoke-Build` 스크립트를 CI/CD 파이프라인의 일부로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-216">I generally use a large `Invoke-Build` script as part of my CI/CD pipeline.</span></span> <span data-ttu-id="58523-217">Pester 테스트 실행, PSScriptAnalyzer 실행, 버전 지정 관리, PSGallery에 게시 같은 놀라운 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="58523-217">It does more magic like running Pester tests, running PSScriptAnalyzer, managing versioning, and publishing to the PSGallery.</span></span> <span data-ttu-id="58523-218">제 모듈에 빌드 스크립트를 사용했을 때 추가할 항목 다수를 발견할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-218">Once I started using a build script for my modules, I was able to find lots of things to add to it.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="58523-219">맺음말</span><span class="sxs-lookup"><span data-stu-id="58523-219">Final thoughts</span></span>

<span data-ttu-id="58523-220">이진 모듈은 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-220">Binary modules are easy to create.</span></span> <span data-ttu-id="58523-221">C# 구문을 이용한 Cmdlet 제작은 다루지 않았지만 [Windows PowerShell SDK][]에서 다양한 문서를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58523-221">I didn't touch on the C# syntax for creating a Cmdlet, but there is plenty of documentation on it in the [Windows PowerShell SDK][].</span></span> <span data-ttu-id="58523-222">C#을 심층적으로 살펴보기 전의 준비 단계로 탁월한 효과가 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="58523-222">It is definitely something worth experimenting with as a stepping stone into more serious C#.</span></span>

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[original version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell Standard Library]: https://github.com/PowerShell/PowerShellStandard
[플랫폼 간 이진 모듈 만들기]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[Creating a cross-platform binary module]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[PSRepository에 NuGet 서버 사용]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Using a NuGet server for a PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS 코드]: https://code.visualstudio.com
[VS Code]: https://code.visualstudio.com
[nuget 패키지]: https://www.nuget.org/packages/PowerShellStandard.Library/
[nuget package]: https://www.nuget.org/packages/PowerShellStandard.Library/
