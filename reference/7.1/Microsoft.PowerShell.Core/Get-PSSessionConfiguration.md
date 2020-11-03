---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 300fc3dee2e0d625e5aea42bfdcf45ea2e8b5a7f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218777"
---
# Get-PSSessionConfiguration

## 개요
컴퓨터에 등록된 세션 구성을 가져옵니다.

## SYNTAX

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## 설명

`Get-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에 등록 된 세션 구성을 가져옵니다. 이 cmdlet은 시스템 관리자가 사용자에 대한 사용자 지정 세션을 관리하는 데 사용할 수 있는 고급 cmdlet입니다.

PowerShell 3.0부터 세션 구성 (pssc) 파일을 사용 하 여 세션 구성의 속성을 정의할 수 있습니다. 이 기능을 사용하면 컴퓨터 프로그램은 작성하지 않고도 사용자 지정 및 제한된 세션을 만들 수 있습니다. 세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조하세요.

또한 PowerShell 3.0 부터는에서 반환 하는 세션 구성 개체에 새로운 메모 속성이 추가 되었습니다 `Get-PSSessionConfiguration` . 이러한 속성 덕분에 사용자 및 세션 구성 작성자가 세션 구성을 쉽게 확인하고 비교할 수 있습니다.

세션 구성을 만들고 등록 하려면 cmdlet을 사용 `Register-PSSessionConfiguration` 합니다.
세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

## 예제

### 예 1-로컬 컴퓨터에서 세션 구성 가져오기

```powershell
Get-PSSessionConfiguration
```

### 예 2-두 개의 기본 세션 구성을 가져옵니다.

이 명령은의 **Name** 매개 변수를 사용 하 여 `Get-PSSessionConfiguration` 이름이 "Microsoft"로 시작 하는 세션 구성만 가져옵니다.

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### 예 3-세션 구성의 속성 및 값 가져오기

이 예제에서는 세션 구성 파일을 사용하여 만든 세션 구성의 속성 및 속성 값을 표시합니다.

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

이 예에서는 cmdlet을 사용 하 여 `Get-PSSessionConfiguration` 전체 세션 구성을 가져옵니다. 파이프라인 연산자는 전체 세션 구성을 cmdlet으로 보냅니다 `Format-List` . 값이 (모두) 인 **Property** 매개 변수는 `*` `Format-List` 목록에 개체의 모든 속성 및 값을 표시 하도록 지시 합니다.

출력은 세션 구성의 작성자, 세션 유형, 언어 모드,이 세션 구성으로 만든 세션의 실행 정책, 세션 할당량, 세션 구성 파일에 대 한 전체 경로를 포함 하 여 유용한 정보를 포함 합니다.

이 세션 구성의 보기는 세션 구성 파일을 포함하는 세션에 사용됩니다.
세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조하세요.

### 예 4-세션 구성을 확인 하는 다른 방법

이 예에서는 `Get-ChildItem` `dir` WSMan: 공급자 드라이브의 cmdlet (별칭)을 사용 하 여 플러그 인 노드의 내용을 확인 합니다. 이 방법으로 컴퓨터의 세션 구성을 확인할 수도 있습니다.

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

**플러그 인** 노드에는 ws-management 용 다른 플러그 인과 함께 등록 된 PowerShell 세션 구성을 나타내는 **ContainerElement** 개체 (에서 wsmanconfigcontainerelement가)가 포함 되어 있습니다.

### 예 6-원격 컴퓨터에서 세션 구성 보기

이 예제에서는 WSMan 공급자를 사용하여 원격 컴퓨터에서 세션 구성을 보는 방법을 보여 줍니다. 이 메서드는 명령으로 많은 정보를 제공 하지 `Get-PSSessionConfiguration` 않지만이 cmdlet을 실행 하기 위해 사용자가 Administrators 그룹의 멤버가 될 필요는 없습니다.

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

`Connect-WSMan`Cmdlet은 Server01 원격 컴퓨터의 WinRM 서비스에 연결 합니다. `Get-ChildItem` `dir` WSMan: 드라이브의 cmdlet (별칭)은 **Server01\Plugin** 경로에 있는 항목을 가져옵니다. 출력에는 Server01 컴퓨터의 Plugin 디렉터리에 있는 항목을 표시합니다. 이 항목에는 컴퓨터의 다른 플러그 인 유형과 함께 WSMan 플러그 인 유형인 세션 구성이 포함됩니다.

### 예 7-원격 컴퓨터에서 자세한 세션 구성 가져오기

이 예제에서는 `Get-PSSessionConfiguration` 원격 컴퓨터에서 명령을 실행 하는 방법을 보여 줍니다. 이 명령을 실행하려면 로컬 컴퓨터의 클라이언트 설정과 원격 컴퓨터의 서비스 설정에서 CredSSP 위임을 사용하도록 설정해야 합니다.

이 예제의 명령을 실행 하려면 로컬 및 원격 컴퓨터에서 Administrators 그룹의 구성원 이어야 하며 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

`Enable-WSManCredSSP`Cmdlet은 로컬 컴퓨터인 Server01에서 **CredSSP** 위임을 사용 하도록 설정 합니다. `Connect-WSMan`Cmdlet는 Server02 컴퓨터에 연결 합니다. 이 작업은 로컬 컴퓨터의 WSMan: 드라이브에 Server02에 대 한 노드를 추가 하 여 Server02 컴퓨터의 WS-Management 설정을 보고 변경할 수 있도록 합니다. `Set-Item`Cmdlet은 Server02 컴퓨터의 Service 노드에 있는 **CredSSP** 항목의 값을 **True** 로 변경 합니다. 이렇게 하면 원격 컴퓨터의 서비스 설정이 구성됩니다. `Invoke-Command`Cmdlet은 `Get-PSSessionConfiguration` Server02 컴퓨터에서 명령을 실행 합니다. 이 명령은 **Credential** 매개 변수를 사용하고 **CredSSP** 값과 함께 **Authentication** 매개 변수를 사용합니다. 출력은 Server02 원격 컴퓨터의 세션 구성을 표시합니다.

### 예 8-세션 구성의 리소스 URI 가져오기

이 예제는 `$PSSessionConfigurationName` 리소스 URI를 사용 하는 기본 설정 변수의 값을 설정 하는 데 유용 합니다.

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

`$PSSessionConfigurationName`변수는 세션을 만들 때 사용 되는 기본 구성을 지정 합니다. 이 변수는 로컬 컴퓨터에 설정되지만 원격 컴퓨터의 구성을 지정합니다. 변수에 대 한 자세한 내용은 `$PSSessionConfiguration` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

## PARAMETERS

### -Force

서비스가 아직 실행되고 있지 않으면 WinRM 서비스를 다시 시작할 것인지 묻는 메시지를 표시하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

지정된 이름이나 이름 패턴의 세션 구성만 가져옵니다. 하나 이상의 세션 구성 이름을 입력합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### Microsoft. PowerShell. PSSessionConfigurationCommands # Register-pssessionconfiguration

## 참고

- 이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

- 컴퓨터의 세션 구성을 보려면 컴퓨터에서 Administrators 그룹의 구성원이어야 합니다.

- `Get-PSSessionConfiguration`원격 컴퓨터에서 명령을 실행 하려면 CredSSP (자격 증명 보안 서비스 공급자) 인증을 로컬 컴퓨터의 클라이언트 설정에서 사용 하도록 설정 해야 합니다 ( `Enable-WSManCredSSP` cmdlet 사용) 및 원격 컴퓨터의 서비스 설정에서 사용 하도록 설정 해야 합니다. 또한 원격 세션을 설정할 때 **인증** 매개 변수의 **CredSSP** 값을 사용 해야 합니다. 그러지 않으면 액세스가 거부됩니다.

- 가 반환 하는 개체의 메모 속성은 `Get-PSSessionConfiguration` 값이 있는 경우에만 개체에 나타납니다. 세션 구성 파일을 사용 하 여 만든 세션 구성에만 정의 된 속성이 모두 있습니다.

- 세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다. 또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.

- WSMan: 드라이브에서 명령을 사용하여 세션 구성의 속성을 변경할 수 있습니다.
  그러나 powershell 2.0의 WSMan: 드라이브를 사용 하 여 **OutputBufferingMode** 와 같은 powershell 3.0에 도입 된 세션 구성 속성을 변경할 수는 없습니다. PowerShell 2.0 명령은 오류를 생성 하지 않지만이는 의미가 없습니다. PowerShell 3.0에 도입 된 속성을 변경 하려면 PowerShell 3.0에서 WSMan: 드라이브를 사용 합니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)

