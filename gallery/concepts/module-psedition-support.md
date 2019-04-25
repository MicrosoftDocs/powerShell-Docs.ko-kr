---
ms.date: 03/28/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: 호환되는 PowerShell 버전이 있는 모듈
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084728"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="a6473-103">호환되는 PowerShell 버전이 있는 모듈</span><span class="sxs-lookup"><span data-stu-id="a6473-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="a6473-104">버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="a6473-105">**Desktop Edition:** .NET Framework에 빌드되어 있으며, Windows 데스크톱, Windows Server, Windows Server Core 및 기타 대부분 Windows 버전에서 Windows PowerShell v4.0 이하 및 Windows PowerShell 5.1에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="a6473-106">**Core Edition:** .NET Core에 빌드되어 있으며, Windows IoT 및 Windows Nanoserver 등의 공간이 축소된 Windows 버전에서 PowerShell Core 6.0 이상 및 Windows PowerShell 5.1에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="a6473-107">PowerShell 버전에 대한 자세한 내용은 [about_PowerShell_Editions][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6473-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="a6473-108">호환되는 버전 선언</span><span class="sxs-lookup"><span data-stu-id="a6473-108">Declaring compatible editions</span></span>

<span data-ttu-id="a6473-109">모듈 작성자는 CompatiblePSEditions 모듈 매니페스트 키를 사용하여 하나 이상의 PowerShell 에디션과 호환된다고 해당 모듈을 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="a6473-110">이 키는 PowerShell 5.1 이상에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="a6473-111">모듈 매니페스트를 CompatiblePSEditions 키로 지정하면 PowerShell 버전 4 이하에서 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="a6473-112">사용 가능한 모듈 목록을 가져올 경우 PowerShell 에디션별로 목록을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="a6473-113">여러 버전 대상 지정</span><span class="sxs-lookup"><span data-stu-id="a6473-113">Targeting multiple editions</span></span>

<span data-ttu-id="a6473-114">모듈 작성자는 PowerShell 버전(Desktop 및 Core) 중 하나 또는 둘 다를 대상으로 하는 단일 모듈을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="a6473-115">단일 모듈은 Desktop 및 Core 에디션 둘 다에서 작동할 수 있습니다. 이 경우 모듈 작성자는 $PSEdition 변수를 사용하여 RootModule 또는 모듈 매니페스트에 필수 논리를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="a6473-116">모듈에는 CoreCLR 및 FullCLR 둘 다를 대상으로 하는 컴파일된 두 가지 DLL 집합이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="a6473-117">적절한 dll을 로드하기 위한 논리를 사용하여 모듈을 패키징하는 몇 가지 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="a6473-118">옵션 1: PowerShell의 여러 버전 및 여러 에디션을 대상으로 하도록 모듈 패키징</span><span class="sxs-lookup"><span data-stu-id="a6473-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="a6473-119">모듈 폴더 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="a6473-119">Module folder contents</span></span>

- <span data-ttu-id="a6473-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="a6473-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="a6473-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="a6473-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="a6473-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="a6473-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="a6473-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="a6473-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="a6473-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="a6473-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="a6473-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="a6473-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="a6473-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="a6473-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="a6473-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="a6473-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="a6473-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="a6473-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="a6473-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="a6473-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="a6473-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="a6473-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="a6473-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="a6473-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="a6473-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="a6473-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="a6473-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="a6473-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="a6473-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="a6473-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="a6473-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="a6473-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="a6473-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="a6473-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="a6473-137">PSScriptAnalyzer.psd1 파일의 내용</span><span class="sxs-lookup"><span data-stu-id="a6473-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<span data-ttu-id="a6473-138">아래 논리는 현재 에디션 또는 버전에 따라 필요한 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="a6473-139">PSScriptAnalyzer.psm1 파일의 내용:</span><span class="sxs-lookup"><span data-stu-id="a6473-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="a6473-140">옵션 2: PSD1 파일의 $PSEdition 변수를 사용하여 적절한 DLL 및 중첩/필수 모듈 로드</span><span class="sxs-lookup"><span data-stu-id="a6473-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="a6473-141">PS 5.1 이상에서 $PSEdition 전역 변수는 모듈 매니페스트 파일에서 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="a6473-142">모듈 작성자는 이 변수를 사용하여 모듈 매니페스트 파일에 조건부 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="a6473-143">$PSEdition 변수는 제한된 언어 모드 또는 데이터 섹션에서 참조될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="a6473-144">모듈 매니페스트를 CompatiblePSEditions 키로 지정하거나 `$PSEdition` 변수를 사용하면 낮은 버전의 PowerShell에서 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="a6473-145">CompatiblePSEditions 키가 있는 샘플 모듈 매니페스트 파일</span><span class="sxs-lookup"><span data-stu-id="a6473-145">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

### <a name="module-contents"></a><span data-ttu-id="a6473-146">모듈 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="a6473-146">Module contents</span></span>

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

<span data-ttu-id="a6473-147">PowerShell 갤러리 사용자는 PSEdition_Desktop 및 PSEdition_Core 태그를 사용하여 특정 PowerShell 버전에서 지원되는 모듈 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="a6473-148">PSEdition_Desktop 및 PSEdition_Core 태그가 없는 모듈은 PowerShell Desktop 버전에서 제대로 작동하는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6473-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="a6473-149">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="a6473-149">More details</span></span>

[<span data-ttu-id="a6473-150">PSEditions가 있는 스크립트</span><span class="sxs-lookup"><span data-stu-id="a6473-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="a6473-151">PowerShellGallery의 PSEditions 지원</span><span class="sxs-lookup"><span data-stu-id="a6473-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="a6473-152">모듈 매니페스트 업데이트</span><span class="sxs-lookup"><span data-stu-id="a6473-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="a6473-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="a6473-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
