---
ms.date: 06/10/2020
title: 호환되는 PowerShell 버전이 있는 모듈
description: 이 문서에서는 PowerShellGet cmdlet이 PowerShell 모듈의 Desktop 및 Core 버전을 지원하는 방법을 설명합니다.
ms.openlocfilehash: 530101590cf83a1f43cbb9ce32d07a7e0ec79253
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661493"
---
# <a name="modules-with-compatible-powershell-editions"></a>호환되는 PowerShell 버전이 있는 모듈

버전 5.1부터 PowerShell은 다양한 기능 세트 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.

- **Desktop Edition:** .NET Framework에 빌드되어 있으며, Windows 데스크톱, Windows Server, Windows Server Core 및 기타 대부분 Windows 버전에서 Windows PowerShell v4.0 이하 및 Windows PowerShell 5.1에 적용됩니다.
- **Core Edition:** .NET Core에 빌드되어 있으며, Windows IoT 및 Windows Nanoserver 등의 공간이 축소된 Windows 버전에서 PowerShell Core 6.0 이상 및 Windows PowerShell 5.1에 적용됩니다.

PowerShell 버전에 대한 자세한 내용은 [about_PowerShell_Editions][]를 참조하세요.

## <a name="declaring-compatible-editions"></a>호환되는 버전 선언

모듈 작성자는 `CompatiblePSEditions` 모듈 매니페스트 키를 사용하여 하나 이상의 PowerShell 에디션과 호환된다고 해당 모듈을 선언할 수 있습니다. 이 키는 PowerShell 5.1 이상에서만 지원됩니다.

> [!NOTE]
> 모듈 매니페스트를 `CompatiblePSEditions` 키로 지정하거나 `$PSEdition` 변수를 사용하면 PowerShell v4 이하에서 가져올 수 없습니다.

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

사용 가능한 모듈 목록을 가져올 경우 PowerShell 에디션별로 목록을 필터링할 수 있습니다.

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

PowerShell 6부터 `$env:windir\System32\WindowsPowerShell\v1.0\Modules`에서 모듈을 가져올 때 `CompatiblePSEditions` 값을 사용하여 모듈이 호환되는지 여부를 결정합니다.
이 동작은 Windows에만 적용됩니다. 이 시나리오 외부에서 값은 메타데이터로만 사용됩니다.

## <a name="finding-compatible-modules"></a>호환되는 모듈 찾기

PowerShell 갤러리 사용자는 **PSEdition_Desktop** 및 **PSEdition_Core** 태그를 사용하여 특정 PowerShell 버전에서 지원되는 모듈 목록을 찾을 수 있습니다.

**PSEdition_Desktop** 및 **PSEdition_Core** 태그가 없는 모듈은 PowerShell Desktop 버전에서 제대로 작동하는 것으로 간주합니다.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a>여러 버전 대상 지정

모듈 작성자는 PowerShell 버전(Desktop 및 Core) 중 하나 또는 둘 다를 대상으로 하는 단일 모듈을 게시할 수 있습니다.

단일 모듈은 Desktop 및 Core 에디션 둘 다에서 작동할 수 있습니다. 이 경우 모듈 작성자는 `$PSEdition` 변수를 사용하여 RootModule 또는 모듈 매니페스트에 필수 논리를 추가해야 합니다. 모듈에는 **CoreCLR** 및 **FullCLR** 둘 다를 대상으로 하는 컴파일된 두 가지 DLL 세트가 있을 수 있습니다. 적절한 DLL을 로드하는 논리를 사용하는 패키징 옵션은 다음과 같습니다.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>옵션 1: PowerShell의 여러 버전 및 여러 에디션을 대상으로 하도록 모듈 패키징

모듈 폴더 콘텐츠

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

`PSScriptAnalyzer.psd1` 파일의 내용

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

아래 논리는 현재 에디션 또는 버전에 따라 필요한 어셈블리를 로드합니다.

`PSScriptAnalyzer.psm1` 파일의 내용:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a>옵션 2: PSD1 파일의 $PSEdition 변수를 사용하여 적절한 DLL 로드

PS 5.1 이상에서 `$PSEdition` 전역 변수는 모듈 매니페스트 파일에서 허용됩니다. 모듈 작성자는 이 변수를 사용하여 모듈 매니페스트 파일에 조건부 값을 지정할 수 있습니다. `$PSEdition` 변수는 제한된 언어 모드 또는 데이터 섹션에서 참조될 수 있습니다.

`CompatiblePSEditions` 키가 있는 샘플 모듈 매니페스트 파일입니다.

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

모듈 콘텐츠

- ModuleWithEditions\ModuleWithEditions.psd1
- ModuleWithEditions\clr\MyFullClrNM1.dll
- ModuleWithEditions\clr\MyFullClrNM2.dll
- ModuleWithEditions\clr\MyFullClrRM.dll
- ModuleWithEditions\coreclr\MyCoreClrNM1.dll
- ModuleWithEditions\coreclr\MyCoreClrNM2.dll
- ModuleWithEditions\coreclr\MyCoreClrRM.dll

## <a name="more-details"></a>자세한 내용

[PSEditions가 있는 스크립트](script-psedition-support.md)

[PowerShellGallery의 PSEditions 지원](../how-to/finding-packages/searching-by-compatibility.md)

[모듈 매니페스트 업데이트](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
