---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: 6417881880cb7f317e7a42d6749b8b7f2cb712fb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345479"
---
# Register-PSSessionConfiguration

## 개요
새 세션 구성을 만들어 등록합니다.

## SYNTAX

### NameParameterSet (기본값)

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-SessionType <PSSessionType>]
 [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Register-PSSessionConfiguration`Cmdlet은 로컬 컴퓨터에 새 세션 구성을 만들어 등록 합니다. 이 cmdlet은 원격 사용자에 대 한 사용자 지정 세션을 만드는 데 사용할 수 있는 고급 cmdlet입니다.

모든 PowerShell 세션 ( **PSSession** )은 끝점 이라고 하는 세션 구성을 사용 합니다.
사용자가 컴퓨터에 연결 하는 세션을 만드는 경우 세션 구성을 선택 하거나 PowerShell 원격을 사용 하도록 설정할 때 등록 된 기본 세션 구성을 사용할 수 있습니다.
현재 세션에서 만들어진 원격 세션에 대한 기본 구성을 지정하는 $PSSessionConfigurationName 기본 설정 변수를 설정할 수도 있습니다.

세션 구성은 원격 세션에 대한 환경을 정의합니다. 구성에 따라 세션에서 사용 가능한 명령 및 언어가 결정되며, 세션이 하나의 개체나 명령을 통해 원격으로 받을 수 있는 데이터양을 제한하는 설정과 같이 컴퓨터를 보호하는 설정이 구성에 포함될 수 있습니다. 세션 구성의 보안 설명자는 세션 구성을 사용할 권한이 있는 사용자를 결정 합니다.

새 구성 클래스를 구현하는 어셈블리와 세션에서 실행되는 스크립트를 사용하여 구성 요소를 정의할 수 있습니다. PowerShell 3.0부터 세션 구성 파일을 사용 하 여 세션 구성을 정의할 수도 있습니다.

세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.
세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.

## 예제

### 예제 1: NewShell 세션 구성 등록

이 예제에서는 **Newshell** 세션 구성을 등록 합니다. **AssemblyName** 및 **ApplicationBase** 매개 변수는 세션 구성에서 cmdlet 및 공급자를 지정 하는 **MyShell.dll** 파일의 위치를 지정 합니다. **Configurationtypename** 매개 변수는 어셈블리에서 사용할 구성 클래스를 지정 합니다.

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

이 구성을 사용 하려면을 입력 `New-PSSession -ConfigurationName newshell` 합니다.

### 예제 2: MaintenanceShell 세션 구성 등록

이 예에서는 로컬 컴퓨터에 **MaintenanceShell** 세션 구성을 등록 합니다. **Startupscript** 매개 변수는 스크립트를 지정 합니다 `Maintenance.ps1` .

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

사용자가 명령을 사용 하 `New-PSSession` 고 **MaintenanceShell** 구성을 선택 하면 `Maintenance.ps1` 스크립트는 새 세션에서 실행 됩니다. 스크립트에서 세션을 구성할 수 있습니다. 여기에는 모듈 가져오기 및 세션에 대 한 실행 정책 설정이 포함 됩니다. 종료 되지 않는 오류를 포함 하 여 스크립트에서 오류를 생성 하는 경우 `New-PSSession` 명령이 실패 합니다.

### 예제 3: 세션 구성 등록

이 예제에서는 **Adminshell** 세션 구성을 등록 합니다.

`$sessionParams`변수는 모든 매개 변수 값을 포함 하는 해시 테이블입니다. 이 해시 테이블은 PowerShell 스 플랫을 사용 하 여 cmdlet에 전달 됩니다. 이 `Register-PSSessionConfiguration` 명령은 **SecurityDescritorSDDL** 매개 변수를 사용 하 여 변수 값에 SDDL을 지정 하 `$sddl` 고 **MaximumReceivedObjectSizeMB** 매개 변수를 사용 하 여 개체 크기 제한을 늘립니다. 또한 **StartupScript** 매개 변수를 사용하여 세션을 구성하는 스크립트를 지정합니다.

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### 예제 4: 구성 컨테이너 요소 반환

이 예제에서는 **MaintenanceShell** 구성을 등록 하는 방법을 보여 줍니다.
`Register-PSSessionConfiguration` 변수에 저장 된 **에서 wsmanconfigcontainerelement가** 개체를 반환 `$s` 합니다. `Format-List` 반환 된 개체의 모든 속성을 표시 합니다. **PSPath** 속성은 개체가 WSMan: 드라이브의 디렉터리에 저장됨을 보여 줍니다. `Get-ChildItem` (별칭 `dir` ) 경로의 항목을 표시 합니다 `WSMan:\LocalHost\PlugIn` . 여기에는 새로운 **MaintenanceShell** 구성과 PowerShell과 함께 제공 되는 두 가지 기본 구성이 포함 됩니다.

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### 예 5: 시작 스크립트를 사용 하 여 세션 구성 등록

이 예제에서는 **Withprofile** 세션 구성을 만들고 등록 합니다. **Startupscript** 매개 변수는 세션 구성을 사용 하는 모든 세션에 대해 지정 된 스크립트를 실행 하도록 PowerShell에 지시 합니다.

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

스크립트에는 도트 소싱을 사용하여 현재 세션 범위에서 사용자의 **CurrentUserAllHosts** 프로필을 실행하는 하나의 명령이 포함되어 있습니다.

프로필에 대한 자세한 내용은 [about_Profiles](./About/about_Profiles.md)를 참조하세요. 도트 소싱에 대한 자세한 내용은 [about_Scopes](./About/about_Scopes.md)를 참조하세요.

## PARAMETERS

### -AccessMode

세션 구성을 사용하거나 사용하지 않도록 설정하고 컴퓨터에서 원격 또는 로컬 세션에 사용할 수 있는지를 결정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 사용 안 함. 세션 구성을 사용할 수 없습니다. 컴퓨터에 대한 원격 또는 로컬 액세스에 세션 구성을 사용할 수 없습니다.
- 로컬. 로컬 컴퓨터의 사용자가 세션 구성을 사용 하 여 동일한 컴퓨터에 로컬 루프백 세션을 만들 수 있지만 원격 사용자에 대 한 액세스를 거부 합니다.
- 리모콘. 로컬 및 원격 컴퓨터의 사용자가 세션 구성을 사용하여 이 컴퓨터에서 세션을 만들고 명령을 실행할 수 있습니다.

기본값은 Remote입니다.

다른 cmdlet은 나중에이 매개 변수의 값을 재정의할 수 있습니다. 예를 들어 `Enable-PSRemoting` cmdlet은 모든 세션 구성에 대 한 원격 액세스를 허용 하 `Enable-PSSessionConfiguration` 고, cmdlet은 세션 구성을 사용 하도록 설정 하 고, `Disable-PSRemoting` cmdlet은 모든 세션 구성에 대 한 원격 액세스를 방지 합니다.

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

\* **AssemblyName** 매개 변수 값에 지정 된 어셈블리 파일 (.dll)의 경로를 지정 합니다. **AssemblyName** 매개 변수 값에 경로가 포함되지 않은 경우 이 매개 변수를 사용합니다. 기본값은 현재 디렉터리입니다.

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

구성 형식이 정의 된 어셈블리 파일 (.dll)의 이름을 지정 합니다 \* . 이 매개 변수 또는 **ApplicationBase** 매개 변수 값에서 .dll의 경로를 지정할 수 있습니다.

**Configurationtypename** 매개 변수를 지정 하는 경우이 매개 변수는 필수입니다.

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

이 구성에 사용되는 Microsoft .NET Framework 유형의 정규화된 이름을 지정합니다. 지정한 유형은 **System.Management.Automation.Remoting.PSSessionConfiguration** 클래스를 구현해야 합니다.

\*구성 유형을 구현 하는 어셈블리 파일 (.dll)을 지정 하려면 **AssemblyName** 및 **ApplicationBase** 매개 변수를 지정 합니다.

유형을 만들면 cmdlet의 특정 매개 변수를 표시 또는 숨기 거 나 사용자가 재정의할 수 없는 데이터 크기 및 개체 크기 제한을 설정 하는 등 세션 구성의 여러 측면을 제어할 수 있습니다.

이 매개 변수를 생략하면 **DefaultRemotePowerShellConfiguration** 클래스가 세션 구성에 사용됩니다.

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

다시 시작을 방지 하 고 다시 시작 메시지를 표시 하지 않으려면 **NoServiceRestart** 매개 변수를 지정 합니다.

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

**ConfigurationTypeName** 매개 변수에 지정된 구성 유형에 데이터 크기 제한이 정의되어 있을 경우 구성 유형의 제한이 사용되고 이 매개 변수 값은 무시됩니다.

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

**ConfigurationTypeName** 매개 변수에 지정된 구성 유형에 개체 크기 제한이 정의되어 있을 경우 구성 유형의 제한이 사용되고 이 매개 변수 값은 무시됩니다.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

세션 구성을 사용 하는 세션에 자동으로 가져오는 모듈을 지정 합니다.

기본적으로 **Microsoft. PowerShell. Core** 만 세션으로 가져옵니다. Cmdlet을 제외 하지 않으면를 사용 하 여 `Import-Module` 세션에 모듈을 추가할 수 있습니다.

이 매개 변수 값에 지정 된 모듈은 **SessionType** 매개 변수로 지정 된 모듈과 세션 구성 파일 ()의 **ModulesToImport** 키에 나열 된 모듈에 추가 하 여 가져옵니다 `New-PSSessionConfigurationFile` . 그러나 세션 구성 파일의 설정은 모듈에서 내보낸 명령을 숨기거나 사용자가 명령을 사용하지 못하도록 할 수 있습니다.

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

세션 구성의 이름을 지정합니다. 이 매개 변수는 필수적 요소입니다.

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

기본적으로 명령을 실행 하면 `Register-PSSessionConfiguration` **WinRM** 서비스를 다시 시작 하 라는 메시지가 표시 됩니다. 이렇게 하면 새 세션 구성을 효과적으로 수행할 수 있습니다. **WinRM** 서비스를 다시 시작할 때까지 새 세션 구성이 유효 하지 않습니다.

메시지를 표시 하지 않고 **WinRM** 서비스를 다시 시작 하려면 **Force** 매개 변수를 지정 합니다. **WinRM** 서비스를 수동으로 다시 시작 하려면 cmdlet을 사용 합니다 `Restart-Service` .

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

에서 만든 것과 같은 세션 구성 파일 (.psc)의 경로와 파일 이름을 지정 합니다 `New-PSSessionConfigurationFile` . 경로를 생략할 경우 기본값은 현재 디렉터리입니다.

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

### -ProcessorArchitecture

이 세션 구성을 사용 하는 세션에서 32 비트 또는 64 비트 버전의 PowerShell 프로세스가 시작 되는지 여부를 결정 합니다. 이 매개 변수에 허용 되는 값은 x86 (32 비트) 및 AMD64 (64 비트)입니다. 기본값은 세션 구성을 호스트하는 컴퓨터의 프로세서 아키텍처에 따라 결정됩니다.

이 매개 변수를 사용하여 64비트 컴퓨터에 32비트 세션을 만들 수 있습니다. 32비트 컴퓨터에 64비트 프로세스를 만들려고 하면 실패합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
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

구성에 대한 SDDL(Security Descriptor Definition Language) 문자열을 지정합니다.

이 문자열은 새 세션 구성을 사용하는 데 필요한 권한을 결정합니다. 세션에서 세션 구성을 사용 하려면 사용자에 게 구성에 대 한 Execute (Invoke) 이상의 권한이 있어야 합니다.

보안 설명자가 복잡한 경우 이 매개 변수 대신 **ShowSecurityDescriptorUI** 매개 변수를 사용하는 것이 좋습니다. 동일한 명령에 두 매개 변수를 함께 사용할 수는 없습니다.

이 매개 변수를 생략 하면 **WinRM** 서비스에 대 한 루트 SDDL이이 구성에 사용 됩니다.
루트 SDDL을 보거나 변경하려면 WSMan 공급자를 사용합니다. 예: `Get-Item wsman:\localhost\service\rootSDDL`. WSMan 공급자에 대 한 자세한 내용을 보려면를 입력 하십시오 `Get-Help wsman` .

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

### -SessionType

세션 구성을 사용하여 만들어진 세션의 유형을 지정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 비어 있음. 기본적으로 세션에는 모듈이 추가 되지 않습니다. 이 cmdlet의 매개 변수를 사용하여 모듈, 함수, 스크립트 및 기타 기능을 세션에 추가할 수 있습니다.
- 기본값 세션에 Microsoft. PowerShell을 추가 합니다. 이 모듈에는 `Import-Module` cmdlet을 명시적으로 금지 하지 않는 한 사용자가 다른 모듈을 가져오는 데 사용할 수 있는 cmdlet이 포함 되어 있습니다.
- RestrictedRemoteServer. 에는,,,, `Exit-PSSession` , `Get-Command` `Get-FormatData` `Get-Help` `Measure-Object` `Out-Default` 및 `Select-Object` cmdlet만 포함 됩니다. 스크립트 또는 어셈블리나 세션 구성 파일의 키를 사용하여 모듈, 함수, 스크립트 및 기타 기능을 세션에 추가할 수 있습니다.

기본값은 Default입니다.

이 매개 변수 값은 세션 구성 파일에 있는 **SessionType** 키의 값 보다 우선 적용 됩니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionType
Parameter Sets: NameParameterSet
Aliases:
Accepted values: DefaultRemoteShell, Workflow

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

이 cmdlet이 세션 구성에 대 한 SDDL을 만드는 데 도움이 되는 속성 시트를 표시 함을 나타냅니다. 속성 시트는 명령을 입력 한 `Register-PSSessionConfiguration` 다음 **WinRM** 서비스를 다시 시작 하면 나타납니다.

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

PowerShell 스크립트의 정규화 된 경로를 지정 합니다. 지정한 스크립트는 세션 구성을 사용하는 새 세션에서 실행됩니다.

스크립트를 사용 하 여 세션을 추가로 구성할 수 있습니다. 종료 되지 않은 오류를 포함 하 여 스크립트에서 오류를 생성 하는 경우 세션은 만들어지지 않으며 `New-PSSession` 명령이 실패 합니다.

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

세션에서 명령을 실행할 때 스레드를 만들고 사용 하는 방법을 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- ReuseThread
- UseCurrentThread
- UseNewThread

기본값은 **UseCurrentThread** 입니다.

자세한 내용은 [Psthreadoptions 열거](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)를 참조 하세요.

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

전송 옵션을 지정 합니다.

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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

### 에서 wsmanconfigcontainerelement가.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

이 cmdlet은 WS-MANAGEMENT (Web Services for Management) 플러그 인 구성을 나타내는 XML을 생성 하 고 WS-MANAGEMENT로 XML을 보냅니다 .이는 로컬 컴퓨터 ()에 플러그 인을 등록 합니다 `New-Item wsman:\localhost\plugin` .

세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다. 또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
