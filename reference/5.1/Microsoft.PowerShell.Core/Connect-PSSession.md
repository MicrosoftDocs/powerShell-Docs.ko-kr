---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 3352055e9c77dd944ffd66fa5db9863166ad7e95
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388810"
---
# Connect-PSSession

## 개요
연결이 끊긴 세션에 다시 연결합니다.

## SYNTAX

### 이름 (기본값)

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 세션

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 컴퓨터 이름

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameGuid

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUri

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriGuid

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Connect-PSSession`이 cmdlet은 연결을 끊은 사용자 관리 PowerShell 세션 ( **pssessions** )에 다시 연결 합니다. 이 cmdlet은 cmdlet의 cmdlet 또는 InDisconnectedSession 매개 변수를 사용 하는 등의 방법으로 의도적으로 연결 되지 않은 세션에서 작동 `Disconnect-PSSession` 하며, **InDisconnectedSession** `Invoke-Command` 일시적인 네트워크 중단 등으로 인해 실수로 연결 해제 된 세션 에서도 작동 합니다.

`Connect-PSSession` 동일한 사용자가 시작한 연결이 끊어진 세션에 연결할 수 있습니다. 여기에는 다른 컴퓨터의 다른 세션에서 시작 되거나 연결 해제 된 항목이 포함 됩니다.

그러나 `Connect-PSSession` 은 (는) cmdlet을 사용 하 여 시작 된 끊어진 세션 또는 대화형 세션에 연결할 수 없습니다 `Enter-PSSession` . 또한 세션을 만든 사용자의 자격 증명을 제공할 수 없는 경우 다른 사용자가 시작한 세션에 세션을 연결할 수는 없습니다.

연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)를 참조하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예 1: 세션에 다시 연결

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

이 명령은 Server01 컴퓨터의 ITTask 세션에 다시 연결합니다.

출력은 명령이 성공했음을 보여 줍니다. 세션의 **상태가** 열리고 **가용성** 을 사용할 수 있습니다 .이는 세션에서 명령을 실행할 수 있음을 나타냅니다.

### 예 2: 연결 끊기 및 다시 연결 효과

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

이 예제에서는 세션의 연결을 끊고 세션에 다시 연결할 경우의 결과를 보여 줍니다.

첫 번째 명령은 cmdlet을 사용 합니다 `Get-PSSession` . **ComputerName** 매개 변수가 없을 경우 명령은 현재 세션에서 만들어진 세션만 가져옵니다.

출력은 명령이 로컬 컴퓨터의 백업 세션을 가져옴을 보여 줍니다. 세션 **상태가** 열리고 **가용성** 을 사용할 수 있습니다.

두 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 현재 세션에서 만들어진 **PSSession** 개체를 가져오고, cmdlet을 사용 하 여 `Disconnect-PSSession` 세션의 연결을 끊습니다. 출력은 백업 세션의 연결이 끊겼음을 보여 줍니다. 세션 **상태가** Disconnected이 고 **Availability** 가 None입니다.

세 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` 현재 세션에서 만들어진 **PSSession** 개체를 가져오고, cmdlet을 사용 하 여 `Connect-PSSession` 세션을 다시 연결 합니다. 출력은 백업 세션이 다시 연결되었음을 보여 줍니다. 세션 **상태가** 열리고 **가용성** 을 사용할 수 있습니다.

연결이 끊어지지 않은 세션에서 cmdlet을 사용 하는 경우이 `Connect-PSSession` 명령은 세션에 영향을 주지 않으며 오류를 생성 하지 않습니다.

### 예 3: 엔터프라이즈 시나리오의 일련의 명령

이 일련의 명령은 `Connect-PSSession` 엔터프라이즈 시나리오에서 cmdlet을 사용 하는 방법을 보여 줍니다. 여기서는 시스템 관리자가 원격 컴퓨터의 세션에서 장기 실행 작업을 시작합니다. 관리자가 작업을 시작한 후 세션에서 연결을 끊고 집으로 갑니다.
나중에 관리자가 가정용 컴퓨터에 로그온 하 여 작업이 완료 될 때까지 실행 되는지 확인 합니다.

관리자는 원격 컴퓨터에서 세션을 만들고 세션에서 스크립트를 실행 하 여 시작 합니다. 첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 원격 컴퓨터에서 ITTask 세션을 만듭니다. **ConfigurationName** 매개 변수를 사용하여 ITTasks 세션 구성을 지정한 다음 이 명령은 세션을 `$s` 변수에 저장 합니다.

두 번째 명령 `Invoke-Command` cmdlet은 변수의 세션에서 백그라운드 작업을 시작 `$s` 합니다. **FilePath** 매개 변수를 사용하여 백그라운드 작업에서 스크립트를 실행합니다.

세 번째 명령은 cmdlet을 사용 하 여 `Disconnect-PSSession` 변수의 세션에서 연결을 끊습니다 `$s` . 이 명령은 Drop 값과 함께 **OutputBufferingMode** 매개 변수를 사용 하 여 세션에 출력을 전달 하 여 스크립트가 차단 되지 않도록 합니다. **IdleTimeoutSec** 매개 변수를 사용 하 여 세션 제한 시간을 15 시간으로 연장 합니다. 명령이 완료 되 면 관리자가 자신의 컴퓨터를 잠그고 저녁에 대해 홈으로 전환 합니다.

나중에 관리자가 가정용 컴퓨터를 시작 하 고, 회사 네트워크에 로그온 하 고, PowerShell을 시작 합니다. 네 번째 명령은 cmdlet을 사용 하 여 `Get-PSSession` Server01 컴퓨터의 세션을 가져옵니다. 이 명령은 ITTask 세션을 찾습니다. 다섯 번째 명령은 cmdlet을 사용 하 여 `Connect-PSSession` ITTask 세션에 연결 합니다. 이 명령은 세션을 `$s` 변수에 저장합니다.

여섯 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Job` 변수의 세션에서 명령을 실행 합니다 `$s` . 출력은 작업이 성공적으로 완료 되었음을 보여 줍니다. 일곱 번째 명령은 cmdlet을 사용 하 여 세션에서 `Invoke-Command` `Receive-Job` 변수의 명령을 실행 합니다 `$s` . 이 명령은 결과를 `$BackupSpecs` 변수에 저장 합니다. 여덟 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` 세션에서 다른 스크립트를 실행 합니다. 이 명령은 `$BackupSpecs` 세션의 변수 값을 스크립트에 대 한 입력으로 사용 합니다.

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

아홉 번째 명령은 변수의 세션에서 연결을 끊습니다 `$s` . 관리자가 PowerShell을 닫고 컴퓨터를 닫습니다. 관리자는 다음 날 세션에 다시 연결하고 회사 컴퓨터에서 스크립트 상태를 확인할 수 있습니다.

## PARAMETERS

### -AllowRedirection

이 cmdlet이이 연결을 대체 URI로 리디렉션할 수 있음을 나타냅니다.

**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다. 기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있습니다.

또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다. Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 **$PSSessionOption** 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 합니다. 기본값은 5입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

애플리케이션의 이름을 지정합니다. 이 cmdlet은 지정 된 응용 프로그램을 사용 하는 세션에만 연결 합니다.

연결 URI의 애플리케이션 이름 세그먼트를 입력합니다. 예를 들어, 다음 연결 URI에서 응용 프로그램 이름은 WSMan입니다 `http://localhost:5985/WSMAN` . 세션의 응용 프로그램 이름은 세션의 **Runspace.ConnectionInfo.AppName** 속성에 저장됩니다.

이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다. 세션에서 사용하는 애플리케이션을 변경하지 않습니다.

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -인증

연결이 끊어진 세션에 다시 연결 하기 위해 명령에서 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 기본값
- Basic
- Credssp
- 다이제스트
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

기본값은 Default입니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.

> [!CAUTION]
> 사용자의 자격 증명이 인증을 위해 원격 컴퓨터로 전달되는 CredSSP(자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스에서 인증이 필요한 명령(예: 원격 네트워크 공유 액세스)에 사용됩니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 로컬 사용자 계정에만 매핑할 수 있습니다. 도메인 계정에서는 작동 하지 않습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

연결이 끊긴 세션을 저장할 컴퓨터를 지정합니다. 세션은 연결의 서버 쪽 또는 수신 끝에 있는 컴퓨터에 저장 됩니다. 기본값은 로컬 컴퓨터입니다.

한 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요. 와일드카드 문자는 사용할 수 없습니다. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, ComputerNameGuid
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

지정한 세션 구성을 사용하는 세션에만 연결합니다.

세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다. 구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/powershell` 합니다. 세션의 구성 이름은 세션의 **ConfigurationName** 속성에 저장됩니다.

이 매개 변수 값은 세션을 선택 및 필터링하는 데 사용됩니다. 세션에서 사용하는 세션 구성을 변경하지 않습니다.

세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

연결이 끊어진 세션에 대 한 연결 끝점의 Uri를 지정 합니다.

URI는 정규화된 URI여야 합니다. 이 문자열의 형식은 다음과 같습니다.

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

기본값은 다음과 같습니다.

`http://localhost:5985/WSMAN`

연결 URI를 지정 하지 않으면 **UseSSL** 및 **Port** 매개 변수를 사용 하 여 연결 uri 값을 지정할 수 있습니다.

URI의 **Transport** 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다. 전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.

대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

또는와 같은 사용자 이름을 입력 `User01` `Domain01\User01` 하거나 `PSCredential` cmdlet에 의해 생성 된 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

연결이 끊긴 세션의 ID를 지정합니다. **Id** 매개 변수는 연결이 끊어진 세션이 이전에 현재 세션에 연결 된 경우에만 작동 합니다.

이 매개 변수는 유효하지만, 세션이 로컬 컴퓨터에 저장되어 있지만 현재 세션에 연결되지 않은 경우 적용되지 않습니다.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

연결이 끊긴 세션의 인스턴스 ID를 지정합니다.

인스턴스 ID는 로컬 또는 원격 컴퓨터의 **PSSession** 을 고유 하 게 식별 하는 GUID입니다.

인스턴스 ID는 **PSSession** 의 **InstanceID** 속성에 저장 됩니다.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

연결이 끊긴 세션의 이름을 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

세션에 다시 연결하는 데 사용할 원격 컴퓨터의 네트워크 포트를 지정합니다. 원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다. 기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.

대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다. 수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요. 이 명령에 설정된 포트는 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

연결이 끊긴 세션을 지정합니다. **Pssession** 개체를 포함 하는 변수를 입력 하거나 **pssession** 개체를 만들거나 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

세션에 대 한 고급 옵션을 지정 합니다. Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.

옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다. 그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.

세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다. 그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.

기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` . **$PSSessionOption** 기본 설정 변수에 대 한 자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)을 참조 하세요. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.
이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.

제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

이 cmdlet은 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 연결이 끊어진 세션에 연결 함을 나타냅니다. 기본적으로 SSL은 사용되지 않습니다.

WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다. **UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능입니다.

이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, ComputerNameGuid
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

### Runspace입니다.

세션 ( **PSSession** )을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### Runspace입니다.

이 cmdlet은 다시 연결 된 세션을 나타내는 개체를 반환 합니다.

## 참고

- 이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

- `Connect-PSSession` 는 연결이 끊어진 세션, 즉 **상태** 속성의 값이 disconnected 인 세션에만 다시 연결 합니다. Windows PowerShell 3.0 이상 버전을 실행 하는 컴퓨터에 연결 되었거나 종료 된 세션만 연결을 끊고 다시 연결할 수 있습니다.

- 연결이 끊어지지 않은 세션에서를 사용 하는 경우이 `Connect-PSSession` 명령은 세션에 영향을 주지 않으며 오류를 생성 하지 않습니다.

- **EnableNetworkAccess** 매개 변수를 사용 하 여 만든 대화형 토큰을 사용 하 여 연결 되지 않은 루프백 세션은 세션을 만든 컴퓨터 에서만 다시 연결할 수 있습니다. 이 제한은 악의적인 액세스로부터 컴퓨터를 보호합니다.

- **PSSession** 의 **State** 속성 값은 현재 세션을 기준으로 합니다.
  따라서 **연결 끊김** 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다. 그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다. 다른 세션에 연결되어 있을 수도 있습니다. 세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.

  **가용성** 값 None은 세션에 연결할 수 있음을 나타냅니다. 사용 중 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다.

  세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState 열거형](/dotnet/api/system.management.automation.runspaces.runspacestate)을 참조 하세요.

  세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability 열거형](/dotnet/api/system.management.automation.runspaces.runspaceavailability)을 참조 하세요.

- **Pssession** 에 연결할 때 **pssession** 의 유휴 시간 제한 값은 변경할 수 없습니다. 의 **sessionoption** 매개 변수는 `Connect-PSSession` **IdleTimeout** 값을 포함 하는 **sessionoption** 개체를 사용 합니다. 그러나 PSSession에 연결 하는 경우 **Sessionoption** 개체의 **idletimeout** 값과 해당 변수의 **idletimeout** 값은 `$PSSessionOption` **PSSession** 무시 됩니다.

  또는 cmdlet을 사용 하 **PSSession** 고 pssession에서 연결을 끊으면 pssession **을 만들 때 pssession** 의 유휴 시간 제한 시간을 설정 하 고 변경할 수 있습니다 `New-PSSession` `Invoke-Command` . **PSSession**

  **PSSession** 의 **IdleTimeout** 속성은 연결이 끊어진 세션이 원격 컴퓨터에서 유지 되는 기간을 결정 하기 때문에 연결이 끊어진 세션에 매우 중요 합니다. 연결이 끊긴 세션은 연결이 끊긴 세션에서 명령을 실행 중인 경우에도 연결이 끊긴 순간부터 유휴 상태로 간주됩니다.

## 관련 링크

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)
