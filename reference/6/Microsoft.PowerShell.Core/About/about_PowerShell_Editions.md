---
description: 다른 버전의 PowerShell은 서로 다른 기본 런타임에서 실행 됩니다.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 4649c1b47a69423eb2f11a119583f441191882dd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221377"
---
# <a name="about-powershell-editions"></a>PowerShell 버전 정보

## <a name="short-description"></a>간단한 설명
다른 버전의 PowerShell은 서로 다른 기본 런타임에서 실행 됩니다.

## <a name="long-description"></a>자세한 설명

PowerShell 5.1에는 각각 서로 다른 .NET 런타임에서 실행 되는 여러 _버전_ 의 powershell이 있습니다. PowerShell 6.2을 통해 PowerShell에는 두 가지 버전이 있습니다.

- .NET Framework에서 실행 되는 **데스크톱** Windows 데스크톱, Windows Server, Windows Server Core 및 대부분의 다른 Windows 운영 체제와 같은 완전 한 기능을 갖춘 Windows 버전의 powershell 5.1 뿐만 아니라 PowerShell 4는 데스크톱 버전입니다. 이는 원래 PowerShell 버전입니다.
- **Core** -.net core에서 실행 됩니다. .NET Framework를 사용할 수 없는 windows Nano Server 및 Windows IoT와 같은 일부 공간을 차지 하는 windows 버전의 powershell 5.1 뿐만 아니라 PowerShell 6.0 이상.

PowerShell 버전은 .net 런타임에 해당 하므로 .NET API 및 PowerShell 모듈 호환성의 기본 표시기입니다. 일부 .NET Api, 형식 또는 메서드는 두 .NET 런타임 모두에서 사용할 수 없으며이에 종속 된 PowerShell 스크립트 및 모듈에 영향을 줍니다.

## <a name="the-psedition-automatic-variable"></a>`$PSEdition`자동 변수

PowerShell 5.1 이상에서는 자동 변수를 사용 하 여 실행 중인 버전을 확인할 수 있습니다 `$PSEdition` .

```powershell
$PSEdition
```

```Output
Core
```

PowerShell 4이 하에서이 변수는 존재 하지 않습니다. `$PSEdition` null 인 경우 값을 갖는 것과 동일 하 게 처리 되어야 합니다 `Desktop` .

### <a name="edition-in-psversiontable"></a>의 버전 `$PSVersionTable`

`$PSVersionTable`또한 자동 변수는 PowerShell 5.1 이상 버전 정보를 포함 합니다.

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

`PSEdition`필드는 자동 변수와 동일한 값을 갖습니다 `$PSEdition` .

## <a name="the-compatiblepseditions-module-manifest-field"></a>`CompatiblePSEditions`모듈 매니페스트 필드

PowerShell 모듈은 모듈 매니페스트의 필드를 사용 하 여 호환 되는 PowerShell 버전을 선언할 수 있습니다 `CompatiblePSEditions` .

예를 들어 모듈 매니페스트는 `Desktop` 및 `Core` 버전의 PowerShell과의 호환성을 선언 합니다.

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

호환성이 있는 모듈 매니페스트의 예는 `Desktop` 다음과 같습니다.

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

`CompatiblePSEditions` `Desktop` 이 필드 앞에 생성 된 모듈이이 버전에 대해 암시적으로 작성 되었으므로 모듈 매니페스트에서 필드를 생략 하면로 설정 하는 것과 동일한 효과가 있습니다.

Windows의 일부로 제공 되지 않은 모듈 (예: 갤러리에서 작성 하거나 설치 하는 모듈)의 경우이 필드는 정보 제공 용입니다. PowerShell은 필드를 기반으로 하는 동작을 변경 하지 `CompatiblePSEditions` 않지만 `PSModuleInfo` 사용자의 논리에 따라 개체 (에 의해 반환 됨)에이를 노출 합니다 `Get-Module` .

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> `CompatiblePSEditions`모듈 필드는 PowerShell 5.1 이상 에서만 호환 됩니다. 이 필드를 포함 하면 모듈이 PowerShell 4와 호환 되지 않습니다. 필드는 전적으로 정보를 제공 하기 때문에 이후 PowerShell 버전에서 안전 하 게 생략할 수 있습니다.

PowerShell 6.1에서 `Get-Module -ListAvailable` 포맷터는 각 모듈의 버전 호환성을 표시 하도록 업데이트 되었습니다.

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                   PSEdition ExportedCommands
---------- -------    ----                   --------- ----------------
Script     1.4.0      Az                     Core,Desk
Script     1.3.1      Az.Accounts            Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                 Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                 Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer       Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility   Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a>버전-Windows의 일부로 제공 되는 모듈에 대 한 호환성

Windows의 일부로 제공 되거나 역할이 나 기능의 일부로 설치 된 모듈의 경우 PowerShell 6.1 이상에서 `CompatiblePSEditions` 필드를 다르게 처리 합니다. 이러한 모듈은 Windows PowerShell 시스템 모듈 디렉터리 ()에서 찾을 수 있습니다 `%windir%\System\WindowsPowerShell\v1.0\Modules` .

이 디렉터리에서 로드 되거나 검색 된 모듈의 경우 PowerShell 6.1 이상에서는 필드를 사용 하 여 `CompatiblePSEditions` 모듈이 현재 세션과 호환 되는지 여부를 확인 하 고 적절 하 게 동작 합니다.

`Import-Module`을 사용 하는 경우에 없는 모듈을 `Core` 가져오지 않고 `CompatiblePSEditions` 오류가 표시 됩니다.

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsT
ransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'.
Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to i
gnore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsT
ransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Com
mands.ImportModuleCommand
```

`Get-Module -ListAvailable`을 사용 하는 경우에 없는 모듈 `Core` `CompatiblePSEditions` 은 표시 되지 않습니다.

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

두 경우 모두 `-SkipEditionCheck` switch 매개 변수를 사용 하 여이 동작을 재정의할 수 있습니다.

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name             PSEdition ExportedCommands
---------- -------    ----             --------- ----------------
Manifest   2.0.0.0    BitsTransfer     Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...
```

> [!WARNING]
> `Import-Module -SkipEditionCheck` 모듈에 대해 성공한 것 처럼 보일 수 있지만,이 모듈을 사용 하면 나중에 비 호환성이 발생할 위험이 있습니다. 처음에는 모듈을 로드 하는 데 성공 하지만 나중에 명령이 호환 되지 않는 API를 호출 하 고 자연스럽 게 실패할 수 있습니다.

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a>버전 간 호환성을 위한 PowerShell 모듈 작성

Powershell 모듈을 작성 하 여 및 버전의 PowerShell을 모두 대상으로 하는 경우 `Desktop` `Core` 버전 간 호환성을 위해 수행할 수 있는 작업이 있습니다.

그러나 호환성을 확인 하 고 지속적으로 유효성을 검사 하는 유일한 방법은 스크립트 또는 모듈에 대 한 테스트를 작성 하 고와 호환성이 필요한 PowerShell의 모든 버전 및 버전에서 실행 하는 것입니다. 이에 대 한 권장 테스트 프레임 워크는 [Pester][]입니다.

### <a name="powershell-script"></a>PowerShell 스크립트

PowerShell은 버전 간에 동일 하 게 작동 합니다. 버전 호환성의 영향을 받는 cmdlet, 모듈 및 .NET Api를 사용 합니다.

일반적으로 PowerShell 6.1 이상에서 작동 하는 스크립트는 Windows PowerShell 5.1에서 작동 하지만 몇 가지 예외가 있습니다.

버전 1.18.0 [Psscriptanalyzer][] 모듈에는 PowerShell 스크립트에서 호환 되지 않는 명령 및 .net api 사용을 검색할 수 있는 [PSUseCompatibleCommands][] 및 [PSUseCompatibleTypes][] 와 같은 규칙이 있습니다.

### <a name="net-assemblies"></a>.NET 어셈블리

소스 코드에서 생성 된 .NET 어셈블리 (Dll)를 통합 하는 모듈 또는 이진 모듈을 작성 하는 경우 .NET 및 PowerShell API 호환성의 컴파일 타임 호환성 유효성 검사를 위해 [.NET Standard][] 및 [powershell 표준][] 에 대해 컴파일해야 합니다.

이러한 라이브러리는 컴파일 시간에 일부 호환성을 확인할 수 있지만 버전 간에 가능한 동작 차이를 catch 할 수 없습니다.
이렇게 하려면 여전히 테스트를 작성 해야 합니다.

## <a name="see-also"></a>참고 항목

- [about_Automatic_Variables](about_Automatic_Variables.md)
- [모듈 가져오기](xref:Microsoft.PowerShell.Core.Import-Module)
- [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)
- [호환되는 PowerShell 버전이 있는 모듈](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
[PSUseCompatibleCommands]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
[PSUseCompatibleTypes]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
