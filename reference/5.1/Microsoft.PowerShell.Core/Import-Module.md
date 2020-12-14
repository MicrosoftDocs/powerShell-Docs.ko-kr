---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 모듈 가져오기
ms.openlocfilehash: 6b87074f6053189b20b5cc0983f978324420c99b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564393"
---
# 모듈 가져오기

## 개요
현재 세션에 모듈을 추가합니다.

## SYNTAX

### 이름 (기본값)

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### PSSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### FullyQualifiedName

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### FullyQualifiedNameAndPSSession

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### 어셈블리

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber] [-Scope <String>]
 [<CommonParameters>]
```

### ModuleInfo

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru] [-AsCustomObject]
 [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

## 설명

`Import-Module`Cmdlet은 현재 세션에 하나 이상의 모듈을 추가 합니다. PowerShell 3.0부터 모듈의 명령이 나 공급자를 사용 하면 설치 된 모듈을 자동으로 세션으로 가져옵니다. 그러나 여전히 `Import-Module` 명령을 사용 하 여 모듈을 가져올 수 있습니다.
기본 설정 변수를 사용 하 여 자동 모듈 가져오기를 사용 하지 않도록 설정할 수 있습니다 `$PSModuleAutoloadingPreference` . 변수에 대 한 자세한 내용은 `$PSModuleAutoloadingPreference` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

모듈은 PowerShell에서 사용할 수 있는 멤버를 포함 하는 패키지입니다. 멤버에는 cmdlet, 공급자, 스크립트, 함수, 변수, 기타 도구 및 파일이 포함 됩니다. 모듈을 가져온 후 세션에서 해당 모듈 멤버를 사용할 수 있습니다. 모듈에 대 한 자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.

기본적으로 `Import-Module` 은 모듈이 내보내는 모든 멤버를 가져오지만 **Alias**, **Function**, **Cmdlet** 및 **Variable** 매개 변수를 사용 하 여 가져올 멤버를 제한할 수 있습니다. **NoClobber** 매개 변수는 `Import-Module` 현재 세션의 멤버와 이름이 같은 멤버를 가져오지 못하게 합니다.

`Import-Module` 현재 세션에만 모듈을 가져옵니다. 모든 새 세션으로 모듈을 가져오려면 `Import-Module` PowerShell 프로필에 명령을 추가 합니다. 프로필에 대한 자세한 내용은 [about_Profiles](About/about_Profiles.md)를 참조하세요.

원격 컴퓨터에서 **PSSession** 을 만들어 PowerShell 원격을 사용 하도록 설정한 원격 Windows 컴퓨터를 관리할 수 있습니다. 그런 다음의 **PSSession** 매개 변수를 사용 `Import-Module` 하 여 원격 컴퓨터에 설치 된 모듈을 가져옵니다. 현재 세션에서 가져온 명령을 사용 하면 명령이 원격 컴퓨터에서 암시적으로 실행 됩니다.

Windows PowerShell 3.0부터를 사용 `Import-Module` 하 여 CIM (CIM(Common Information Model)) 모듈을 가져올 수 있습니다. CIM 모듈은 CDXML (Cmdlet 정의 XML) 파일에 cmdlet을 정의 합니다. 이 기능을 사용 하면 c + +로 작성 된 코드 어셈블리와 같이 관리 되지 않는 코드 어셈블리에 구현 된 cmdlet을 사용할 수 있습니다.

Windows 운영 체제를 실행 하지 않는 컴퓨터를 포함 하 여 PowerShell 원격을 사용 하지 않는 원격 컴퓨터의 경우의 **CIMSession** 매개 변수를 사용 `Import-Module` 하 여 원격 컴퓨터에서 CIM 모듈을 가져올 수 있습니다. 가져온 명령은 원격 컴퓨터에서 암시적으로 실행 됩니다. **CIMSession** 은 원격 컴퓨터의 WMI(WINDOWS MANAGEMENT INSTRUMENTATION) (WMI)에 대 한 연결입니다.

## 예제

### 예제 1: 모듈의 멤버를 현재 세션으로 가져오기

이 예제에서는 **Psdiagnostics** 모듈의 멤버를 현재 세션으로 가져옵니다.

```powershell
Import-Module -Name PSDiagnostics
```

### 예제 2: 모듈 경로로 지정 된 모든 모듈 가져오기

이 예에서는 환경 변수로 지정 된 경로에서 사용 가능한 모든 모듈을 `$env:PSModulePath` 현재 세션으로 가져옵니다.

```powershell
Get-Module -ListAvailable | Import-Module
```

### 예제 3: 여러 모듈의 멤버를 현재 세션으로 가져오기

이 예제에서는 **Psdiagnostics** 및 **Dism** 모듈의 멤버를 현재 세션으로 가져옵니다.

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

`Get-Module`Cmdlet은 **Psdiagnostics** 및 **Dism** 모듈을 가져오고 개체를 변수에 저장 합니다 `$m` . **ListAvailable** 매개 변수는 아직 세션으로 가져오지 않은 모듈을 가져오는 경우에 필요 합니다.

의 **Moduleinfo** 매개 변수를 `Import-Module` 사용 하 여 모듈을 현재 세션으로 가져올 수 있습니다.

### 예제 4: 경로로 지정 된 모든 모듈 가져오기

이 예에서는 명시적 경로를 사용 하 여 가져올 모듈을 식별 합니다.

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

**Verbose** 매개 변수를 사용 하면 `Import-Module` 에서 모듈을 로드할 때 진행률을 보고 합니다.
**Verbose**, **PassThru** 또는 **AsCustomObject** 매개 변수를 사용 하지 않으면에서 `Import-Module` 모듈을 가져올 때 출력이 생성 되지 않습니다.

### 예 5: 세션으로 가져온 모듈 멤버 제한

이 예에서는 세션으로 가져오는 모듈 멤버와 세션에 대 한이 명령의 영향을 제한 하는 방법을 보여 줍니다. **함수** 매개 변수는 모듈에서 가져온 멤버를 제한 합니다. **별칭**, **변수** 및 **Cmdlet** 매개 변수를 사용 하 여 모듈이 가져오는 다른 멤버를 제한할 수도 있습니다.

`Get-Module`Cmdlet은 **psdiagnostics** 모듈을 나타내는 개체를 가져옵니다. **ExportedCmdlets** 속성은 모듈이 내보내는 모든 cmdlet을 나열 하지만 모두 가져오지는 않습니다.

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

Cmdlet의 **Module** 매개 변수를 사용 하면 `Get-Command` **psdiagnostics** 모듈에서 가져온 명령이 표시 됩니다. 결과는 `Disable-PSTrace` 및 cmdlet만 가져왔는지 확인 합니다 `Enable-PSTrace` .

### 예제 6: 모듈의 멤버를 가져오고 접두사 추가

이 예제에서는 **Psdiagnostics** 모듈을 현재 세션으로 가져오고, 멤버 이름에 접두사를 추가한 다음, 접두사가 있는 멤버 이름을 표시 합니다. 의 **prefix** 매개 변수는 `Import-Module` 모듈에서 가져온 모든 멤버에 **x** 접두사를 추가 합니다. 접두사는 현재 세션의 멤버에만 적용 됩니다. 모듈을 변경하지는 않습니다. **PassThru** 매개 변수는 가져온 모듈을 나타내는 module 개체를 반환 합니다.

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

`Get-Command` 모듈에서 가져온 멤버를 가져옵니다. 출력에는 모듈 멤버에 접두사가 올바르게 추가된 것으로 표시됩니다.

### 예제 7: 사용자 지정 개체 가져오기 및 사용

이 예제에서는에서 반환 하는 사용자 지정 개체를 가져오고 사용 하는 방법을 보여 줍니다 `Import-Module` .

사용자 지정 개체에는 가져온 각각의 모듈 멤버를 나타내는 합성 멤버가 포함되어 있습니다. 예를 들어 모듈의 함수와 cmdlet은 사용자 지정 개체의 스크립트 메서드로 변환됩니다.

사용자 지정 개체는 스크립팅에 유용 합니다. 또한 가져온 몇몇 개체의 이름이 같은 경우에도 유용합니다. 개체의 스크립트 메서드를 사용하는 것은 모듈 이름을 포함하여 가져온 멤버의 정규화된 이름을 지정하는 것과 동일합니다.

**AsCustomObject** 매개 변수는 스크립트 모듈을 가져오는 경우에만 사용할 수 있습니다. 사용 `Get-Module` 가능한 모듈 중 스크립트 모듈을 확인 하는 데 사용 합니다.

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

`Show-Calendar` **AsCustomObject** 매개 변수를 사용 하 여 스크립트 모듈을 가져와서 사용자 지정 개체를 요청 하 고 **PassThru** 매개 변수를 사용 하 여 개체를 반환 합니다. 결과 사용자 지정 개체는 변수에 저장 됩니다 `$a` .

`$a`변수는 `Get-Member` 저장 된 개체의 속성 및 메서드를 표시 하기 위해 cmdlet으로 파이프 됩니다. 출력은 스크립트 메서드를 보여 줍니다 `Show-Calendar` .

스크립트 메서드를 호출 하려면 `Show-Calendar` 이름에 하이픈이 포함 되므로 메서드 이름을 따옴표로 묶어야 합니다.

### 예 8: 모듈을 동일한 세션으로 다시 가져오기

이 예제에서는  `Import-Module` 모듈을 동일한 세션으로 다시 가져오는 때의 Force 매개 변수를 사용 하는 방법을 보여 줍니다. **Force** 매개 변수는 로드 된 모듈을 제거한 다음 다시 가져옵니다.

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

첫 번째 명령은 **Psdiagnostics** 모듈을 가져옵니다. 두 번째 명령은 모듈을 다시 가져오는데, 이번에는 **Prefix** 매개 변수를 사용합니다.

**Force** 매개 변수를 사용 하지 않으면 세션에 각 **psdiagnostics** cmdlet의 복사본 두 개가 포함 됩니다. 하나에는 표준 이름과 접두사가 붙은 이름이 있습니다.

### 예제 9: 가져온 명령에 의해 숨겨진 명령 실행

이 예제에서는 가져온 명령에서 숨긴 명령을 실행하는 방법을 보여 줍니다. **Testmodule** 모듈에는 연도 `Get-Date` 와 날짜를 반환 하는 라는 함수가 포함 되어 있습니다.

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

첫 번째 `Get-Date` cmdlet은 현재 날짜를 사용 하 여 **DateTime** 개체를 반환 합니다. **Testmodule** 모듈을 가져온 후는 연도의 `Get-Date` 연도와 일자를 반환 합니다.

의 **all** 매개 변수를 사용 하 여 `Get-Command` `Get-Date` 세션의 모든 명령을 표시 합니다. 결과에는 세션에 두 개의 `Get-Date` 명령, 즉 **testmodule** 모듈의 함수 및 **Microsoft PowerShell** 모듈의 cmdlet이 표시 됩니다.

함수는 cmdlet 보다 우선 하므로 `Get-Date` cmdlet 대신 **testmodule** 모듈의 함수를 실행 합니다 `Get-Date` . 원래 버전의를 실행 하려면 `Get-Date` 모듈 이름으로 명령 이름을 정규화 해야 합니다.

PowerShell의 명령 우선 순위에 대 한 자세한 내용은 [about_Command_Precedence](about/about_Command_Precedence.md)를 참조 하세요.

### 예 10: 모듈의 최소 버전 가져오기

이 예제에서는 **PowerShellGet** 모듈을 가져옵니다. 의 **MinimumVersion** 매개 변수를 사용 하 여 `Import-Module` 버전 2.0.0 모듈을 가져옵니다.

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

또한 **RequiredVersion** 매개 변수를 사용 하 여 모듈의 특정 버전을 가져오거나 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 `#Requires` 스크립트에서 모듈의 특정 버전을 요구할 수 있습니다.

### 예 11: 정규화 된 이름을 사용 하 여 가져오기

이 예제에서는 FullyQualifiedName를 사용 하 여 모듈의 특정 버전을 가져옵니다.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### 예 12: 정규화 된 경로를 사용 하 여 가져오기

이 예에서는 정규화 된 경로를 사용 하 여 모듈의 특정 버전을 가져옵니다.

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### 예제 13: 원격 컴퓨터에서 모듈 가져오기

이 예제에서는 cmdlet을 사용 하 여 `Import-Module` 원격 컴퓨터에서 모듈을 가져오는 방법을 보여 줍니다.
이 명령은 PowerShell의 암시적 원격 기능을 사용 합니다.

다른 세션에서 모듈을 가져오면 현재 세션에서 해당 cmdlet을 사용할 수 있습니다.
그러나 cmdlet을 사용 하는 명령은 원격 세션에서 실행 됩니다.

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

`New-PSSession` Server01 컴퓨터에 대 한 원격 세션 (**PSSession**)을 만듭니다. **PSSession** 은 변수에 저장 됩니다 `$s` .

`Get-Module` **PSSession** 매개 변수를 사용 하 여를 실행 하는 경우 **netsecurity** 모듈이 설치 되어 원격 컴퓨터에 사용 가능 하다는 것을 표시 합니다. 이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Module` 원격 세션에서 명령을 실행 하는 것과 같습니다. 예: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`

`Import-Module` **PSSession** 매개 변수를 사용 하 여를 실행 하면 원격 컴퓨터에서 현재 세션으로 **netsecurity** 모듈을 가져옵니다. `Get-Command`Cmdlet은 **netsecurity** 모듈의 **get** 및 include **방화벽** 으로 시작 하는 명령을 가져오는 데 사용 됩니다. 출력은 모듈과 해당 cmdlet을 현재 세션으로 가져왔는지 확인 합니다.

그런 다음 `Get-NetFirewallRule` cmdlet은 Server01 컴퓨터에 Windows 원격 관리 방화벽 규칙을 가져옵니다. 이는 cmdlet을 사용 하 여 `Invoke-Command` `Get-NetFirewallRule` 원격 세션에서 실행 하는 것과 같습니다.

### 예 14: Windows 운영 체제를 사용 하지 않고 원격 컴퓨터의 저장소 관리

이 예에서는 컴퓨터의 관리자가 모듈 검색 WMI 공급자를 설치 하 여 공급자 용으로 설계 된 CIM 명령을 사용할 수 있습니다.

`New-CimSession`Cmdlet은 여 rsdgf03 이라는 원격 컴퓨터에서 세션을 만듭니다. 세션은 원격 컴퓨터의 WMI 서비스에 연결 됩니다. CIM 세션은 변수에 저장 됩니다 `$cs` .
`Import-Module` 는의 **CimSession** 를 사용 하 여 `$cs` 여 rsdgf03 컴퓨터에서 **저장소** CIM 모듈을 가져옵니다.

`Get-Command`Cmdlet은 `Get-Disk` **저장소** 모듈의 명령을 표시 합니다. CIM 모듈을 로컬 세션으로 가져오면 PowerShell은 각 명령의 CDXML 파일을 로컬 세션의 함수로 표시 되는 PowerShell 스크립트로 변환 합니다.

`Get-Disk`는 로컬 세션에서 형식화 되었지만 cmdlet은 해당 파일을 가져온 원격 컴퓨터에서 암시적으로 실행 됩니다. 이 명령은 원격 컴퓨터에서 로컬 세션으로 개체를 반환 합니다.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## PARAMETERS

### -별칭

이 cmdlet이 모듈에서 현재 세션으로 가져오는 별칭을 지정 합니다. 쉼표로 구분된 별칭 목록을 입력하세요. 와일드카드 문자를 사용할 수 있습니다.

모듈을 가져올 때 선택된 별칭을 해당 세션으로 자동으로 내보내는 모듈도 있습니다.
이 매개 변수를 사용하면 내보내는 별칭 중에서 선택할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ArgumentList

명령 중에 스크립트 모듈로 전달 되는 인수 또는 매개 변수 값의 배열을 지정 합니다 `Import-Module` . 이 매개 변수는 스크립트 모듈을 가져오는 경우에만 유효 합니다.

또한 **인수** 에 따라 **argumentlist** 매개 변수를 참조할 수 있습니다. **Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

이 cmdlet은 가져온 모듈 멤버를 나타내는 멤버가 있는 사용자 지정 개체를 반환 함을 나타냅니다. 이 매개 변수는 스크립트 모듈에만 유효합니다.

**AsCustomObject** 매개 변수를 사용 하는 경우는 `Import-Module` 모듈 멤버를 세션으로 가져온 다음 **Psmoduleinfo** 개체 대신 **PSCustomObject** 개체를 반환 합니다. 사용자 지정 개체를 변수에 저장하고 점 표기법을 사용하여 멤버를 호출할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -어셈블리

어셈블리 개체의 배열을 지정 합니다. 이 cmdlet은 지정 된 어셈블리 개체에 구현 된 cmdlet 및 공급자를 가져옵니다. 어셈블리 개체가 포함된 변수나 어셈블리 개체를 만드는 명령을 입력하세요. 어셈블리 개체를로 파이프 할 수도 있습니다 `Import-Module` .

이 매개 변수를 사용하면 지정된 어셈블리에서 구현한 cmdlet과 공급자만 가져옵니다. 모듈에 다른 파일이 포함 되어 있으면 해당 파일을 가져오지 않으며 모듈의 중요 한 멤버가 누락 될 수 있습니다. 모듈을 디버깅 하 고 테스트 하는 데이 매개 변수를 사용 하거나 모듈 작성자가 사용 하도록 지시 하는 경우이 매개 변수를 사용 합니다.

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimNamespace

CIM 모듈을 표시하는 대체 CIM 공급자의 네임스페이스를 지정합니다. 기본값은 모듈 검색 WMI 공급자의 네임스페이스입니다.

이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

CIM 모듈의 대체 위치를 지정합니다. 기본값은 원격 컴퓨터의 모듈 검색 WMI 공급자에 대 한 리소스 URI입니다.

이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치에서 CIM 모듈을 가져옵니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

원격 컴퓨터에서 CIM 세션을 지정합니다. Cim 세션을 포함 하는 변수 또는 CIM 세션을 가져오는 명령 (예: [CimSession](../CimCmdlets/Get-CimSession.md) 명령)을 입력 합니다.

`Import-Module` CIM 세션 연결을 사용 하 여 원격 컴퓨터에서 현재 세션으로 모듈을 가져옵니다. 현재 세션에서 가져온 모듈의 명령을 사용 하면 명령이 원격 컴퓨터에서 실행 됩니다.

이 매개 변수를 사용 하 여 Windows 운영 체제를 실행 하지 않는 컴퓨터 및 장치와 PowerShell이 있지만 PowerShell 원격을 사용 하도록 설정 하지 않은 Windows 컴퓨터에서 모듈을 가져올 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cmdlet

이 cmdlet이 모듈에서 현재 세션으로 가져오는 cmdlet의 배열을 지정 합니다.
와일드카드 문자를 사용할 수 있습니다.

모듈을 가져올 때 선택된 cmdlet을 해당 세션으로 자동으로 내보내는 모듈도 있습니다.
이 매개 변수를 사용하면 내보내는 cmdlet 중에서 선택할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -DisableNameChecking

이 cmdlet은 이름에 승인 되지 않은 동사 나 금지 된 문자가 포함 된 cmdlet 또는 함수를 가져올 때 경고 메시지를 표시 하지 않음을 나타냅니다.

기본적으로 가져오는 모듈이 이름에 승인 되지 않은 동사가 포함 된 cmdlet 또는 함수를 내보내는 경우 PowerShell에서 다음과 같은 경고 메시지를 표시 합니다.

> 경고: 일부 가져온 명령 이름에는 검색 하기 어려울 수 있는 승인 되지 않은 동사가 포함 되어 있습니다. 자세한 내용을 보려면 Verbose 매개 변수를 사용하거나 승인된 동사 목록을 보려면 Get-Verb를 입력하세요.

이 메시지는 경고일 뿐입니다. 비준수 명령을 포함하여 전체 모듈을 계속 가져옵니다. 메시지가 모듈 사용자에게 표시되더라도 명명 문제는 모듈 작성자가 수정해야 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

이 매개 변수를 통해 모듈을 로드 하거나 현재 모듈 위에 다시 로드 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

모듈의 정규화 된 이름을 해시 테이블로 지정 합니다. 값은 문자열과 해시 테이블의 조합일 수 있습니다. 해시 테이블에는 다음과 같은 키가 있습니다.

- `ModuleName` - **필수** 모듈 이름을 지정 합니다.
- `GUID` - **선택 사항** 모듈의 GUID를 지정 합니다.
- 또한 아래 세 키 중 하나를 지정 **해야** 합니다. 이러한 키는 함께 사용할 수 없습니다.
  - `ModuleVersion` -모듈의 허용 가능한 최소 버전을 지정 합니다.
  - `RequiredVersion` -필요한 모듈의 정확한 버전을 지정 합니다.
  - `MaximumVersion` -모듈의 허용 되는 최대 버전을 지정 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -함수

이 cmdlet이 모듈에서 현재 세션으로 가져오는 함수 배열을 지정 합니다.
와일드카드 문자를 사용할 수 있습니다. 모듈을 가져올 때 선택된 함수를 해당 세션으로 자동으로 내보내는 모듈도 있습니다. 이 매개 변수를 사용하면 내보내는 함수 중에서 선택할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -전역

이 cmdlet은 모듈을 전역 세션 상태로 가져오므로 세션의 모든 명령에서 사용할 수 있음을 나타냅니다.

기본적으로 `Import-Module` 명령 프롬프트, 스크립트 파일 또는 scriptblock에서 cmdlet을 호출 하면 모든 명령을 전역 세션 상태로 가져옵니다.

다른 모듈에서 호출 되는 경우 `Import-Module` cmdlet은 중첩 모듈의 명령을 포함 하 여 모듈의 명령을 호출 하는 모듈의 세션 상태로 가져옵니다.

> [!TIP]
> `Import-Module`모듈 내에서를 호출 하지 않아야 합니다. 대신, 부모 모듈의 매니페스트에서 대상 모듈을 중첩 모듈로 선언 합니다. 중첩 모듈을 선언 하면 종속성의 검색 기능이 향상 됩니다.

**Global** 매개 변수는 **Global** 값을 사용하는 **Scope** 매개 변수와 동일한 결과를 낳습니다.

모듈에서 내보내는 명령을 제한 하려면 `Export-ModuleMember` 스크립트 모듈의 명령을 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

최대 버전을 지정 합니다. 이 cmdlet은 지정 된 값 보다 작거나 같은 버전의 모듈만 가져옵니다. 버전이 한정 되지 않은 경우는 `Import-Module` 오류를 반환 합니다.

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

최소 버전을 지정 합니다. 이 cmdlet은 지정 된 값 보다 크거나 같은 버전의 모듈만 가져옵니다. **MinimumVersion** 매개 변수 이름 또는 그 별칭인 **Version** 을 사용합니다. 버전이 한정 되지 않은 경우는 `Import-Module` 오류를 생성 합니다.

정확한 버전을 지정하려면 **RequiredVersion** 매개 변수를 사용합니다. **#Requires** 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 스크립트에서 모듈의 특정 버전을 요구할 수도 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleInfo

가져올 모듈 개체의 배열을 지정 합니다. 모듈 개체를 포함 하는 변수를 입력 하거나 모듈 개체를 가져오는 명령 (예:)을 입력 `Get-Module -ListAvailable` 합니다. 모듈 개체를로 파이프 할 수도 있습니다 `Import-Module` .

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

가져올 모듈의 이름을 지정합니다. 모듈 이름 또는 모듈의 파일 이름 (예: `.psd1` ,, `.psm1` `.dll` 또는 파일)을 입력 합니다 `.ps1` . 파일 경로는 선택 사항입니다. 와일드 카드 문자는 허용 되지 않습니다. 모듈 이름 및 파일 이름을로 파이프 할 수도 있습니다 `Import-Module` .

경로를 생략 하면는 `Import-Module` 환경 변수에 저장 된 경로에서 모듈을 찾습니다 `$env:PSModulePath` .

가능하면 항상 모듈 이름만 지정하세요. 파일 이름을 지정하는 경우 해당 파일에 구현된 멤버만 가져옵니다. 모듈에 다른 파일이 포함 되어 있으면 해당 파일을 가져오지 않으며 모듈의 중요 한 멤버가 누락 될 수 있습니다.

> [!NOTE]
> 스크립트 파일 ()은 모듈로 가져올 수 있지만 스크립트 `.ps1` 파일은 일반적으로 스크립트 모듈 파일 () 파일 처럼 구조화 되지 않습니다 `.psm1` . 스크립트 파일을 가져오면 모듈로 사용할 수 있다는 보장이 없습니다. 자세한 내용은 [about_Modules](about/about_Modules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -NoClobber

현재 세션에 있는 기존 명령과 이름이 동일한 명령을 가져오지 않습니다. 기본적으로는 `Import-Module` 내보낸 모든 모듈 명령을 가져옵니다.

이름이 같은 명령은 세션의 명령을 숨기 거 나 바꿀 수 있습니다. 세션에서 명령 이름 충돌을 방지하려면 **Prefix** 또는 **NoClobber** 매개 변수를 사용합니다. 이름 충돌 및 명령 우선 순위에 대한 자세한 내용은 [about_Modules](about/about_Modules.md) 및 [about_Command_Precedence](about/about_Command_Precedence.md)의 "모듈 및 이름 충돌"을 참조하세요.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환 합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -접두사

이 cmdlet이 가져온 모듈 멤버의 이름에 있는 명사에 추가 하는 접두사를 지정 합니다.

세션에 있는 서로 다른 멤버의 이름이 동일한 경우 발생할 수 있는 이름 충돌을 방지하려면 이 매개 변수를 사용합니다. 이 매개 변수는 모듈을 변경 하지 않으며 모듈에서 자체적으로 사용 하기 위해 가져오는 파일에 영향을 주지 않습니다. 이를 중첩 모듈 이라고 합니다. 이 cmdlet은 현재 세션에 있는 멤버의 이름에만 영향을 줍니다.

예를 들어, 접두사 UTC를 지정 하 고 cmdlet을 가져오면이 `Get-Date` cmdlet은 세션에서로 알려져 `Get-UTCDate` 있으며 원래 cmdlet과는 혼동 되지 않습니다 `Get-Date` .

이 매개 변수 값은 기본 접두사를 지정하는 모듈의 **DefaultCommandPrefix** 속성보다 우선합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

이 cmdlet이 모듈을 현재 세션으로 가져오는 PowerShell 사용자 관리 세션 (**PSSession**)을 지정 합니다. **Pssession이** 포함 된 변수 또는 **pssession** 을 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .

다른 세션에서 현재 세션으로 모듈을 가져오면 로컬 모듈의 cmdlet을 사용할 때와 마찬가지로 현재 세션에서 해당 모듈의 cmdlet을 사용할 수 있습니다. 원격 cmdlet을 사용 하는 명령은 원격 세션에서 실행 되지만 원격 세부 정보는 PowerShell을 통해 백그라운드에서 관리 됩니다.

이 매개 변수는 PowerShell의 암시적 원격 기능을 사용 합니다. Cmdlet을 사용 하 여 `Import-PSSession` 세션에서 특정 모듈을 가져오는 것과 같습니다.

`Import-Module` 다른 세션에서 PowerShell 핵심 모듈을 가져올 수 없습니다. PowerShell 핵심 모듈의 이름은 Microsoft. PowerShell로 시작 합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

이 cmdlet이 가져오는 모듈의 버전을 지정 합니다. 버전이 설치 되어 있지 않으면에서 `Import-Module` 오류를 생성 합니다.

기본적으로는 `Import-Module` 버전 번호를 확인 하지 않고 모듈을 가져옵니다.

최소 버전을 지정하려면 **MinimumVersion** 매개 변수를 사용합니다. **#Requires** 키워드의 **module** 및 **version** 매개 변수를 사용 하 여 스크립트에서 모듈의 특정 버전을 요구할 수도 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

**RequiredVersion** 을 사용 하 여 기존 버전의 windows 운영 체제에 포함 된 모듈을 가져오는 스크립트는 이후 버전의 windows 운영 체제에서 자동으로 실행 되지 않습니다. 이는 Windows 운영 체제의 이후 릴리스에서 PowerShell 모듈 버전 번호가 기존 버전의 Windows 운영 체제에서 모듈 버전 번호 보다 높기 때문입니다.

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -범위

이 cmdlet이 모듈을 가져올 범위를 지정 합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- **전역**. 세션의 모든 명령에서 사용할 수 있습니다. **Global** 매개 변수를 사용하는 것과 동일합니다.
- **로컬**. 현재 범위에서만 사용할 수 있습니다.

기본적으로 `Import-Module` 명령 프롬프트, 스크립트 파일 또는 scriptblock에서 cmdlet을 호출 하면 모든 명령을 전역 세션 상태로 가져옵니다. 매개 변수를 사용 `-Scope Local` 하 여 모듈 콘텐츠를 스크립트 또는 scriptblock 범위로 가져올 수 있습니다.

다른 모듈에서 호출 되는 경우 `Import-Module` cmdlet은 중첩 모듈의 명령을 포함 하 여 모듈의 명령을 호출자의 세션 상태로 가져옵니다. 또는를 지정 하면 `-Scope Global` `-Global` 이 cmdlet이 모듈을 전역 세션 상태로 가져오므로 세션의 모든 명령에 사용할 수 있습니다.

**Global** 매개 변수는 **Global** 값을 사용하는 **Scope** 매개 변수와 동일한 결과를 낳습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

이 cmdlet이 모듈에서 현재 세션으로 가져오는 변수의 배열을 지정 합니다.
변수의 목록을 입력하세요. 와일드카드 문자를 사용할 수 있습니다.

모듈을 가져올 때 선택된 변수를 해당 세션으로 자동으로 내보내는 모듈도 있습니다.
이 매개 변수를 사용하면 내보내는 변수 중에서 선택할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string, System.web.. n a m a.

모듈 이름, 모듈 개체 또는 어셈블리 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None, PSCustomObject 또는. m i n. a p.

기본적으로는 `Import-Module` 출력을 생성 하지 않습니다. **PassThru** 매개 변수를 지정 하는 경우 cmdlet은 모듈을 나타내는 **system.object** 를 생성 합니다. **AsCustomObject** 매개 변수를 지정 하면 **PSCustomObject** 개체가 생성 됩니다.

## 참고

- 모듈을 가져오려면 모듈이 로컬 컴퓨터에 설치 되어 있어야 합니다. 즉, 모듈 디렉터리를 로컬 컴퓨터에서 액세스할 수 있는 디렉터리에 복사 해야 합니다. 자세한 내용은 [about_Modules](About/about_Modules.md)를 참조 하세요.

  **PSSession** 및 **CIMSession** 매개 변수를 사용하여 원격 컴퓨터에 설치된 모듈을 가져올 수도 있습니다. 그러나 이러한 모듈의 cmdlet을 사용 하는 명령은 원격 컴퓨터의 원격 세션에서 실행 됩니다.

- 이름과 형식이 같은 멤버를 세션에 가져오는 경우 PowerShell은 기본적으로 마지막으로 가져온 멤버를 사용 합니다. 변수와 별칭은 바뀌고 원본에는 액세스할 수 없습니다. 함수, cmdlet 및 공급자는 단순히 새 멤버로 숨겨집니다. 스냅인, 모듈 또는 함수 경로의 이름으로 명령 이름을 정규화 하 여 액세스할 수 있습니다.

- 모듈에서 가져온 명령에 대 한 형식 지정 데이터를 업데이트 하려면 cmdlet을 사용 `Update-FormatData` 합니다. `Update-FormatData` 는 모듈에서 가져온 세션의 명령에 대 한 형식 지정 데이터도 업데이트 합니다. 모듈에 대 한 형식 지정 파일이 변경 되 면 `Update-FormatData` 명령을 실행 하 여 가져온 명령에 대 한 형식 지정 데이터를 업데이트할 수 있습니다. 모듈을 다시 가져올 필요는 없습니다.

- Windows PowerShell 3.0 부터는 PowerShell과 함께 설치 되는 핵심 명령이 모듈에 패키지 됩니다. Windows PowerShell 2.0 및 이후 버전의 PowerShell에서 이전 스타일의 세션을 만드는 호스트 프로그램에서 핵심 명령은 스냅인 (**PSSnapins**)으로 패키지 됩니다. 예외는 항상 스냅인 인 **Microsoft. PowerShell. Core** 입니다. 또한 cmdlet에서 시작한 것과 같은 원격 세션 `New-PSSession` 은 핵심 스냅인을 포함 하는 이전 스타일의 세션입니다.

  핵심 모듈과 함께 최신 스타일의 세션을 만드는 **initialsessionstate.createdefault2** 메서드에 대 한 자세한 내용은 [initialsessionstate.createdefault2 메서드](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)를 참조 하세요.

- Windows PowerShell 2.0에서는 모듈을 가져올 때까지 **ExportedCmdlets** 및 **NestedModules** 속성 값과 같은 module 개체의 일부 속성 값이 채워지지 않았습니다.

- Windows PowerShell 3.0 +와 호환 되지 않는 혼합 모드 어셈블리를 포함 하는 모듈을 가져오려고 시도 하면에서 `Import-Module` 다음과 같은 오류 메시지를 반환 합니다.

  > Import-Module: 혼합 모드 어셈블리는 런타임의 버전 ' v 2.0.50727 '에 대해 빌드 되었으며 추가 구성 정보 없이 4.0 런타임에 로드 될 수 없습니다.

  이 오류는 Windows PowerShell 2.0 용으로 설계 된 모듈에 혼합 모듈 어셈블리가 하나 이상 포함 되어 있을 때 발생 합니다. C + + 및 c #과 같은 관리 코드 및 관리 되지 않는 코드를 모두 포함 하는 혼합 모듈 어셈블리입니다.

  혼합 모드 어셈블리를 포함 하는 모듈을 가져오려면 다음 명령을 사용 하 여 Windows PowerShell 2.0을 시작한 후 명령을 다시 시도 하십시오 `Import-Module` .

  `PowerShell.exe -Version 2.0`

- CIM 세션 기능을 사용하려면 원격 컴퓨터에 WS-Management 원격 기능과 CIM(Common Information Model) 표준에 대한 Microsoft 구현인 WMI(Windows Management Instrumentation)가 설정되어 있어야 합니다. 컴퓨터에도 모듈 검색 WMI 공급자 또는 동일한 기본 기능을 갖춘 대체 CIM 공급자가 있어야 합니다.

  Windows 운영 체제를 실행 하지 않는 컴퓨터 및 PowerShell이 있는 Windows 컴퓨터에서 CIM 세션 기능을 사용할 수 있지만 PowerShell 원격을 사용 하도록 설정 하지는 않습니다.

  CIM 매개 변수를 사용 하 여 로컬 컴퓨터를 포함 하 여 PowerShell 원격을 사용 하도록 설정한 컴퓨터에서 CIM 모듈을 가져올 수도 있습니다. 로컬 컴퓨터에서 CIM 세션을 만드는 경우 PowerShell은 WMI 대신 DCOM을 사용 하 여 세션을 만듭니다.

- 기본적으로는 `Import-Module` 하위 범위에서 호출 된 경우에도 전역 범위에서 모듈을 가져옵니다. 최상위 범위 및 모든 하위 범위는 모듈의 내보낸 요소에 액세스할 수 있습니다.

  하위 항목 범위에서 `-Scope Local` 는 해당 범위 및 모든 하위 항목 범위로 가져오기를 제한 합니다. 그러면 부모 범위에 가져온 멤버가 표시 되지 않습니다.

  > [!NOTE]
  > `Get-Module` 현재 세션에 로드 된 모든 모듈을 표시 합니다. 여기에는 하위 항목 범위에서 로컬로 로드 된 모듈이 포함 됩니다. `Get-Command -Module modulename`현재 범위에서 로드 된 멤버를 확인 하는 데 사용 합니다.

  `Import-Module` 는 모듈에서 클래스 및 열거형 정의를 로드 하지 않습니다. `using module`스크립트의 시작 부분에 문을 사용 합니다. 클래스 및 열거형 정의를 포함 하 여 모듈을 가져옵니다. 자세한 내용은 [about_Using](About/about_Using.md)를 참조 하세요.

## 관련 링크

[about_Modules](about/about_Modules.md)

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[New-Module](New-Module.md)

[Remove-Module](Remove-Module.md)
