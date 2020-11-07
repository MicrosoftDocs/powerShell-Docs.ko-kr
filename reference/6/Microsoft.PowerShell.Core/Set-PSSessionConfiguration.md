---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 30950cb31a6d70b61416883a16603262c297f0d1
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345411"
---
# Set-PSSessionConfiguration

## 개요
등록된 세션 구성의 속성을 변경합니다.

## SYNTAX

### NameParameterSet (기본값)

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Set-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에서 세션 구성의 속성을 변경 합니다.

**Name** 매개 변수를 사용하여 변경할 세션 구성을 식별합니다. 다른 매개 변수를 사용하여 세션 구성의 속성에 대해 새 값을 지정할 수도 있습니다. 구성에서 속성 값을 삭제 하 고 기본값을 사용 하려면 해당 매개 변수에 대해 빈 문자열 ("") 또는 값을 입력 `$Null` 합니다.

PowerShell 3.0부터 세션 구성 파일을 사용 하 여 세션 구성을 정의할 수 있습니다. 이 기능은 세션 구성을 사용하는 세션의 속성을 설정 및 변경하는 간단하고 검색 가능한 방법을 제공합니다. 세션 구성 파일을 지정 하려면의 **Path** 매개 변수를 사용 `Set-PSSessionConfiguration` 합니다. 세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.
세션 구성 파일을 만들고 수정 하는 방법에 대 한 자세한 내용은 cmdlet을 참조 하십시오 `New-PSSessionConfigurationFile` .

세션 구성은 로컬 컴퓨터에 연결 되는 원격 세션 ( **pssessions** ) 환경을 정의 합니다. 모든 **PSSession** 은 세션 구성을 사용 합니다. 세션 구성은 세션에서 사용 가능한 모듈, 실행할 수 있는 cmdlet, 언어 모드, 할당량 및 시간 제한과 같은 **PSSession** 의 기능을 결정 합니다. 세션 구성의 보안 설명자는 세션 구성을 사용 하 여 로컬 컴퓨터에 연결할 수 있는 사용자를 결정 합니다. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

세션 구성의 속성을 보려면 `Get-PSSessionConfiguration` cmdlet 또는 WSMan 공급자를 사용 합니다. WSMan 공급자에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help WSMan` .

## 예제

### 예제 1: 세션 구성 만들기 및 변경

이 예제에서는 구성에서 시작 스크립트를 추가 하 고 제거 하는 방법을 보여 줍니다.

첫 번째 명령은 **Adminshell** 구성을 만듭니다. 두 번째 명령은 `AdminConfig.ps1` 구성에 스크립트를 추가 합니다. **WinRM** 을 다시 시작할 때 변경 내용이 적용 됩니다.
세 번째 명령은 `AdminConfig.ps1` 구성에서 스크립트를 제거 합니다.

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### 예제 2: 결과 표시

이 예에서는 **MaximumReceivedObjectSizeMB** 속성의 값을 20으로 늘립니다. 이 명령은 또한 **WinRM** 서비스를 다시 시작 하 라는 메시지를 표시 합니다. **WinRM** 서비스를 다시 시작할 때까지 변경 내용이 적용 되지 않습니다.

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### 예제 3: 다양 한 방법으로 결과 표시

이 예에서는 `Set-PSSessionConfiguration` **MaintenanceShell** 세션 구성의 시작 스크립트를로 변경 합니다 `Maintenance.ps1` . 출력은 변경 내용을 표시 하 고 **WinRM** 서비스를 다시 시작 하 라는 메시지를 표시 합니다. "y"(예)로 응답합니다.

`Get-PSSessionConfiguration`**MaintenanceShell** 세션 구성을 가져옵니다. 파이프라인 연산자 (|)는 명령 결과를으로 보냅니다. 그러면 `Format-List` 이 목록에 있는 구성 개체의 모든 속성을 표시 합니다. 그런 다음 WSMan 공급자를 사용 하 여 **MaintenanceShell** 구성에 대 한 초기화 매개 변수를 확인 합니다. `Get-ChildItem`(별칭 `dir` ) **MaintenanceShell** 플러그 인에 대 한 **InitializationParameters** 노드의 자식 항목을 가져옵니다. WSMan 공급자에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help wsman` .

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## PARAMETERS

### -AccessMode

세션 구성을 사용하거나 사용하지 않도록 설정하고 컴퓨터에서 원격 또는 로컬 세션에 사용할 수 있는지를 결정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 사용 안 함. 세션 구성을 사용할 수 없습니다. 컴퓨터에 대한 원격 또는 로컬 액세스에 세션 구성을 사용할 수 없습니다. 이 값은 세션 구성의 **Enabled** 속성 ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` )을 **False** 로 설정 합니다.
- 로컬. 세션 구성의 보안 설명자에 **Network_Deny_All** 항목을 추가합니다.
  로컬 컴퓨터의 사용자는 세션 구성을 사용 하 여 동일한 컴퓨터에 로컬 루프백 세션을 만들 수 있지만 원격 사용자는 액세스가 거부 됩니다.
- 리모콘. 세션 구성의 보안 설명자에서 **Deny_All** 및 **Network_Deny_All** 항목을 제거합니다. 로컬 및 원격 컴퓨터의 사용자가 세션 구성을 사용하여 이 컴퓨터에서 세션을 만들고 명령을 실행할 수 있습니다.

기본값은 **Remote** 입니다.

다른 cmdlet은 나중에이 매개 변수의 값을 재정의할 수 있습니다. 예를 들어 `Enable-PSRemoting` cmdlet은 컴퓨터의 모든 세션 구성을 사용 하도록 설정 하 고 원격 액세스를 허용 하며, `Disable-PSRemoting` cmdlet은 컴퓨터의 모든 세션 구성에 대 한 로컬 액세스만 허용 합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationBase

\* **AssemblyName** 매개 변수 값에 지정 된 어셈블리 파일 (.dll)의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssemblyName

어셈블리 이름을 지정합니다. 이 cmdlet은 어셈블리에 정의 된 클래스를 기반으로 하 여 세션 구성을 만듭니다.

세션 구성을 정의 하는 어셈블리 .dll 파일의 파일 이름 또는 전체 경로를 입력 합니다. 파일 이름만 입력 하는 경우 **ApplicationBase** 매개 변수 값에 경로를 입력할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTypeName

**AssemblyName** 매개 변수의 어셈블리에 정의된 세션 구성의 유형을 지정합니다. 지정한 유형은 **System.Management.Automation.Remoting.PSSessionConfiguration** 클래스를 구현해야 합니다.

이 매개 변수는 어셈블리 이름을 지정할 때 필요합니다.

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

모든 사용자 프롬프트를 표시 하지 않고 **WinRM** 서비스를 다시 시작 합니다. 서비스를 다시 시작하면 구성 변경 내용이 적용됩니다.

다시 시작하지 않고 다시 시작 프롬프트를 표시하지 않으려면 **NoServiceRestart** 매개 변수를 사용합니다.

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

### -MaximumReceivedDataSizePerCommandMB

단일 원격 명령으로이 컴퓨터에 보낼 수 있는 데이터 양에 대 한 제한을 지정 합니다. 데이터 크기를 MB 단위로 입력하세요. 기본값은 50입니다.

**Configurationtypename** 매개 변수에 지정 된 구성 유형에 데이터 크기 제한이 정의 되어 있으면 구성 유형의 제한이 사용 됩니다. 이 매개 변수 값은 무시 됩니다.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSizeMB

단일 개체에서이 컴퓨터에 보낼 수 있는 데이터 양에 대 한 제한을 지정 합니다.
데이터 크기 (mb)를 입력 합니다. 기본값은 10MB입니다.

**Configurationtypename** 매개 변수에 지정 된 구성 유형에 개체 크기 제한이 정의 되어 있으면 구성 유형의 제한이 사용 됩니다. 이 매개 변수 값은 무시 됩니다.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

세션 구성을 사용하는 세션에 자동으로 가져오는 모듈 및 스냅인을 지정합니다. 모듈 및 스냅인 이름을 입력합니다.

기본적으로 **Microsoft. PowerShell. 코어** 스냅인만 세션으로 가져오지만, cmdlet을 제외 하지 않으면 `Import-Module` 및 Add-PSSnapin cmdlet을 사용 하 여 모듈 및 스냅인을 세션에 추가할 수 있습니다.

이 매개 변수 값에 지정 된 모듈은 세션 구성 파일 ()에 지정 된 모듈에 추가 하 여 가져옵니다 `New-PSSessionConfigurationFile` . 그러나 세션 구성 파일의 설정은 모듈에서 내보낸 명령을 숨기거나 사용자가 명령을 사용하지 못하도록 할 수 있습니다.

이 매개 변수 값에 지정 된 모듈은 cmdlet의 **ModulesToImport** 매개 변수를 사용 하 여 지정 된 모듈 목록을 바꿉니다 `Register-PSSessionConfiguration` .

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

변경할 세션 구성의 이름을 지정합니다.

이 매개 변수를 사용하여 세션 구성의 이름을 변경할 수는 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoServiceRestart

**WinRM** 서비스를 다시 시작 하지 않고 서비스를 다시 시작 하 라는 메시지를 표시 하지 않습니다.

기본적으로를 실행할 때 `Set-PSSessionConfiguration` 새 세션 구성을 적용 하려면 **WinRM** 서비스를 다시 시작 하 라는 메시지가 표시 됩니다. **WinRM** 서비스를 다시 시작할 때까지 새 세션 구성이 유효 하지 않습니다.

메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하려면 **Force** 매개 변수를 사용 합니다. **WinRM** 서비스를 수동으로 다시 시작 하려면 cmdlet을 사용 합니다 `Restart-Service` .

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

### -Path

Cmdlet에서 만든 것과 같은 세션 구성 파일 (.psc)의 경로를 지정 합니다. `New-PSSessionConfigurationFile` 경로를 생략할 경우 기본값은 현재 디렉터리입니다.

세션 구성 파일을 수정 하는 방법에 대 한 자세한 내용은 cmdlet에 대 한 도움말 항목을 참조 하십시오 `New-PSSessionConfigurationFile` .

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSVersion

이 세션 구성을 사용 하는 세션의 PowerShell 버전을 지정 합니다.

이 매개 변수 값은 세션 구성 파일에 있는 **PowerShellVersion** 키의 값보다 우선합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsCredential

세션의 명령에 대 한 자격 증명을 지정 합니다. 기본적으로 명령은 현재 사용자의 사용 권한으로 실행됩니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecurityDescriptorSddl

구성에 대해 다른 SDDL(Security Descriptor Definition Language) 문자열을 지정합니다.

이 문자열은 새 세션 구성을 사용하는 데 필요한 권한을 결정합니다. 세션에서 세션 구성을 사용 하려면 사용자에 게 구성에 대 한 Execute (Invoke) 이상의 권한이 있어야 합니다.

구성에 대 한 기본 보안 설명자를 사용 하려면 빈 문자열 ("") 또는 값을 입력 `$Null` 합니다. 기본값은 WSMan: 드라이브의 루트 SDDL입니다.

보안 설명자가 복잡 한 경우이 매개 변수 대신 **ShowSecurityDescriptorUI** 매개 변수를 사용 하는 것이 좋습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.

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

### -SessionTypeOption

세션 구성에 대 한 유형별 옵션을 지정 합니다. Cmdlet에서 반환 하는 **Psworkflowexecutionoption** 개체와 같은 세션 유형 옵션 개체를 입력 `New-PSWorkflowExecutionOption` 합니다.

세션 구성을 사용하는 세션의 옵션은 세션 옵션 값과 세션 구성 옵션에 따라 결정됩니다. 지정 하지 않은 경우에는 cmdlet을 사용 하는 등의 방법으로 세션에 설정 된 옵션이 `New-PSSessionOption` 세션 구성에 설정 된 옵션 보다 우선 적용 됩니다. 그러나 세션 옵션 값은 세션 구성에서 설정된 최대값을 초과할 수 없습니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowSecurityDescriptorUI

이 cmdlet이 세션 구성에 대 한 새 SDDL을 만드는 데 도움이 되는 속성 시트 임을 나타냅니다. 속성 시트는 명령을 실행 한 `Set-PSSessionConfiguration` 다음 **WinRM** 서비스를 다시 시작 하면 나타납니다.

구성에 대 한 사용 권한을 설정 하는 경우 세션에서 세션 구성을 사용 하려면 사용자에 게 적어도 실행 (호출) 권한이 있어야 합니다.

동일한 명령에 **SecurityDescriptorSDDL** 매개 변수와 이 매개 변수를 함께 사용할 수는 없습니다.

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

### -StartupScript

구성에 대 한 시작 스크립트를 지정 합니다. PowerShell 스크립트의 정규화 된 경로를 입력 합니다. 지정한 스크립트는 세션 구성을 사용하는 새 세션에서 실행됩니다.

세션 구성에서 시작 스크립트를 삭제 하려면 빈 문자열 ("") 또는 값을 입력 `$Null` 합니다.

시작 스크립트를 사용 하 여 사용자 세션을 추가로 구성할 수 있습니다. 종료 되지 않은 오류를 포함 하 여 스크립트에서 오류를 생성 하는 경우 세션은 만들어지지 않으며 `New-PSSession` 명령이 실패 합니다.

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

### -ThreadOptions

구성의 스레드 옵션 설정을 지정 합니다. 이 설정은 세션에서 명령을 실행할 때 스레드가 만들어져 사용되는 방법을 정의합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- ReuseThread
- UseCurrentThread
- UseNewThread

기본값은 **UseCurrentThread** 입니다.

자세한 내용은 [Psthreadoptions 열거](/dotnet/api/system.management.automation.runspaces.psthreadoptions)를 참조 하세요.

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -로 옵션

세션 구성에 대 한 전송 옵션을 지정 합니다. Cmdlet이 반환 하는 **Wsmanconfigurationoption** 개체와 같은 전송 옵션 개체를 입력 `New-PSTransportOption` 합니다.

세션 구성을 사용하는 세션의 옵션은 세션 옵션 값과 세션 구성 옵션에 따라 결정됩니다. 지정 하지 않은 경우에는 cmdlet을 사용 하는 등의 방법으로 세션에 설정 된 옵션이 `New-PSSessionOption` 세션 구성에 설정 된 옵션 보다 우선 적용 됩니다. 그러나 세션 옵션 값은 세션 구성에서 설정된 최대값을 초과할 수 없습니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSharedProcess

한 프로세스만 사용 하 여 동일한 사용자에 의해 시작 되 고 동일한 세션 구성을 사용 하는 모든 세션을 호스팅합니다. 기본적으로 각 세션은 해당 프로세스에 호스트됩니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

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

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### WSManConfigLeafElement.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

이 cmdlet을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.

`Set-PSSessionConfiguration`Cmdlet는 구성 이름을 변경 하지 않으며 **WSMan** 공급자는이 cmdlet을 지원 하지 않습니다 `Rename-Item` . 세션 구성의 이름을 변경 하려면 cmdlet을 사용 하 여 `Unregister-PSSessionConfiguration` 구성을 삭제 한 다음 cmdlet을 사용 하 여 `Register-PSSessionConfiguration` 새 세션 구성을 만들고 등록 합니다.

Cmdlet을 사용 하 여 `Set-PSSessionConfiguration` 기본 microsoft.powershell32 세션 구성을 변경할 수 있습니다. 이 구성은 보호되지 않습니다. 기본 세션 구성의 원래 버전으로 되돌리려면 cmdlet을 사용 하 여 `Unregister-PSSessionConfiguration` 기본 세션 구성을 삭제 한 다음 cmdlet을 사용 하 여 `Enable-PSRemoting` 복원 합니다.

세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다. 또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.

WSMan: 드라이브에서 명령을 사용하여 세션 구성의 속성을 변경할 수 있습니다.
그러나 powershell 2.0의 WSMan: 드라이브를 사용 하 여 **OutputBufferingMode** 와 같은 powershell 3.0에 도입 된 세션 구성 속성을 변경할 수는 없습니다. Windows PowerShell 2.0 명령은 오류를 생성하지 않지만 이런 시도가 아무런 영향을 주지 않습니다. PowerShell 3.0에 도입 된 속성을 변경 하려면 PowerShell 3.0에서 WSMan: 드라이브를 사용 합니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
