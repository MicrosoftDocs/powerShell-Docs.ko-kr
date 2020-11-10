---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 3572d95724158b0ad4462d76d8d2aceb75d2fa18
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387280"
---
# Receive-PSSession

## 개요

연결이 끊긴 세션에서 명령의 결과를 가져옵니다.

## SYNTAX

### 세션(기본값)

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### Id

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ComputerSessionName 이름

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerInstanceId

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriSessionName 이름

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Receive-PSSession [-InstanceId] <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### 이름

```
Receive-PSSession [-Name] <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Receive-PSSession`Cmdlet은 분리 된 PowerShell 세션 ( **PSSession** )에서 실행 되는 명령 결과를 가져옵니다. 세션이 현재 연결 되어 있는 경우 `Receive-PSSession` 세션 연결이 끊어질 때 실행 중 이었던 명령의 결과를 가져옵니다. 세션의 연결이 끊어지면에서 세션에 `Receive-PSSession` 연결 하 여 일시 중단 된 모든 명령을 다시 시작 하 고 세션에서 실행 중인 명령의 결과를 가져옵니다.

이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.

`Receive-PSSession`명령 대신 또는를 사용할 수 있습니다 `Connect-PSSession` .
`Receive-PSSession` 다른 세션이 나 다른 컴퓨터에서 시작 된 연결이 끊어졌거나 다시 연결 된 세션에 연결할 수 있습니다.

`Receive-PSSession`cmdlet 또는 InDisconnectedSession 매개 변수를 사용 하 여 의도적으로 **분리 된 pssession에서 작동** `Disconnect-PSSession` `Invoke-Command` **InDisconnectedSession** 합니다. 또는 실수로 네트워크 중단으로 인해 연결을 끊었습니다.

`Receive-PSSession`실행 중이거나 일시 중단 된 명령이 없는 세션에 연결 하기 위해 cmdlet을 사용 하는 경우 `Receive-PSSession` 은 세션에 연결 하지만 출력 또는 오류를 반환 하지 않습니다.

연결이 끊긴 세션 기능에 대한 자세한 내용은 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)를 참조하세요.

일부 예제에서는 스 플랫를 사용 하 여 줄 길이를 줄이고 가독성을 향상 시킵니다. 자세한 내용은 [about_Splatting](./About/about_Splatting.md)를 참조 하세요.

## 예제

### 예제 1: PSSession에 연결

이 예에서는 원격 컴퓨터의 세션에 연결 하 고 세션에서 실행 중인 명령의 결과를 가져옵니다.

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

는 `Receive-PSSession` **ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다. **Name** 매개 변수는 Server01 컴퓨터의 ittask 세션을 식별 합니다. 이 예에서는 ITTask 세션에서 실행 중인 명령의 결과를 가져옵니다.

명령이 **Outtarget** 매개 변수를 사용 하지 않으므로 결과는 명령줄에 표시 됩니다.

### 예 2: 연결 되지 않은 세션에서 모든 명령의 결과 가져오기

이 예제에서는 두 원격 컴퓨터의 연결 되지 않은 모든 세션에서 실행 중인 모든 명령의 결과를 가져옵니다.

세션의 연결이 끊어졌거나 명령이 실행 되 고 있지 않은 경우 `Receive-PSSession` 은 세션에 연결 하지 않고 출력 또는 오류를 반환 하지 않습니다.

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

`Get-PSSession`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다. 개체는 파이프라인에서로 전송 됩니다 `Receive-PSSession` .

### 예 3: 세션에서 실행 중인 스크립트의 결과 가져오기

이 예에서는 cmdlet을 사용 하 여 `Receive-PSSession` 원격 컴퓨터의 세션에서 실행 중인 스크립트의 결과를 가져옵니다.

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

**ComputerName** 및 **Name** 매개 변수를 사용하여 연결이 끊긴 세션을 식별합니다.
작업으로 결과를 반환 하기 위해 작업 값과 함께 **Outtarget** 매개 변수를 사용 `Receive-PSSession` 합니다. **JobName** 매개 변수는 다시 연결 된 세션에서 작업 이름을 지정 합니다.
**Credential** 매개 변수는 `Receive-PSSession` 도메인 관리자의 사용 권한을 사용 하 여 명령을 실행 합니다.

출력은 결과를 `Receive-PSSession` 현재 세션에서 작업으로 반환 되었음을 보여 줍니다. 작업 결과를 가져오려면 명령을 사용 합니다. `Receive-Job`

### 예 4: 네트워크 중단 후 결과 가져오기

이 예에서는 cmdlet을 사용 하 여 `Receive-PSSession` 네트워크 중단으로 인해 세션 연결이 중단 된 후 작업 결과를 가져옵니다. PowerShell은 다음 4 분 동안 초당 한 번 세션을 다시 연결 하려고 시도 하 고 4 분 간격의 모든 시도가 실패 한 경우에만 활동을 중단 합니다.

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

`New-PSSession`Cmdlet은 Server01 컴퓨터에서 세션을 만들고이 세션을 변수에 저장 합니다 `$s` . `$s`변수가 **상태** 를 열고 **가용성** 을 사용할 수 있음을 표시 합니다. 이러한 값은 세션에 연결 되어 세션에서 명령을 실행할 수 있음을 의미 합니다.

`Invoke-Command`Cmdlet은 변수의 세션에서 스크립트를 실행 `$s` 합니다. 스크립트 실행이 시작되고 데이터를 반환하지만 네트워크 중단이 발생하여 세션이 중단됩니다. 사용자는 세션을 끝내고 로컬 컴퓨터를 다시 시작해야 합니다.

컴퓨터가 다시 시작 되 면 사용자가 PowerShell을 시작 하 고 `Get-PSSession` 명령을 실행 하 여 Server01 컴퓨터에서 세션을 가져옵니다. 출력에는 **AD** 세션이 여전히 Server01 컴퓨터에 존재 하는 것으로 표시 됩니다. **상태** 는 **AD** 세션의 연결이 끊어졌음을 나타냅니다. None의 **가용성** 값은 세션이 클라이언트 세션에 연결 되지 않았음을 나타냅니다.

`Receive-PSSession`Cmdlet은 **AD** 세션에 다시 연결 하 고 세션에서 실행 된 스크립트의 결과를 가져옵니다. 이 명령은 **Outtarget** 매개 변수를 사용 하 여 **adjob** 이라는 작업에서 결과를 요청 합니다. 이 명령은 작업 개체를 반환 하 고 출력은 스크립트가 아직 실행 되 고 있음을 나타냅니다.

`Get-PSSession`Cmdlet은 작업 상태를 확인 하는 데 사용 됩니다. 출력은 `Receive-PSSession` cmdlet이 **AD** 세션에 다시 연결 된 것을 확인 하 여 명령에 사용할 수 있습니다. 스크립트가 실행을 다시 시작 하 고 스크립트 결과를 가져옵니다.

### 예 5: 연결이 끊어진 세션에 다시 연결

이 예에서는 cmdlet을 사용 하 여 `Receive-PSSession` 의도적으로 연결이 끊어진 세션에 다시 연결 하 고 세션에서 실행 중인 작업의 결과를 가져옵니다.

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

이 `Invoke-Command` cmdlet은 3 개의 원격 컴퓨터에서 스크립트를 실행 합니다. 스크립트는 여러 데이터베이스의 데이터를 수집 하 고 요약 하기 때문에 스크립트를 완료 하는 데 오랜 시간이 걸립니다. 이 명령은 스크립트를 시작 하는 **InDisconnectedSession** 매개 변수를 사용 하 여 세션의 연결을 즉시 해제 합니다. **Sessionoption** 매개 변수는 연결 되지 않은 세션의 **IdleTimeout** 값을 확장 합니다. 연결 되지 않은 세션은 연결을 끊은 순간부터 유휴 상태로 간주 됩니다. 명령이 완료 되 고 세션에 다시 연결할 수 있도록 충분 한 시간 동안 유휴 시간 제한 시간을 설정 하는 것이 중요 합니다. **PSSession** 을 만든 경우에만 **IdleTimeout** 을 설정 하 고 연결을 끊을 때만이를 변경할 수 있습니다. **PSSession** 에 연결 하거나 결과를 받을 때에는 **IdleTimeout** 값을 변경할 수 없습니다. 명령을 실행 한 후 사용자가 PowerShell을 종료 하 고 컴퓨터를 닫습니다.

다음 날에는 사용자가 Windows를 다시 시작 하 고, PowerShell을 시작 하 고,를 사용 하 여 `Get-PSSession` 스크립트가 실행 되는 세션을 가져옵니다. 이 명령은 컴퓨터 이름, 세션 이름 및 세션 구성의 이름을 기준으로 세션을 식별 하 고이 세션을 `$s` 변수에 저장 합니다. `$s`변수의 값이 표시 되 고 세션의 연결이 끊어져 있지만 사용 중이 아닌 것을 보여 줍니다.

`Receive-PSSession`Cmdlet은 변수의 세션에 연결 하 여 `$s` 해당 결과를 가져옵니다.
이 명령은 결과를 `$Results` 변수에 저장 합니다. `$s`변수가 표시 되 고 세션이 연결 되어 명령에 사용할 수 있음을 보여 줍니다.

변수의 스크립트 결과가 `$Results` PowerShell 콘솔에 표시 됩니다. 예기치 않은 결과가 발생 하는 경우 사용자는 세션에서 명령을 실행 하 여 근본 원인을 조사할 수 있습니다.

### 예 6: 연결 되지 않은 세션에서 작업 실행

이 예에서는 연결 되지 않은 세션에서 실행 되는 작업의 결과를 보여 줍니다.

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

`New-PSSession`Cmdlet은 Server01 컴퓨터에서 테스트 세션을 만듭니다. 이 명령은 세션을 `$s` 변수에 저장합니다.

`Invoke-Command`Cmdlet은 변수의 세션에서 명령을 실행 합니다 `$s` . 이 명령은 **AsJob** 매개 변수를 사용 하 여 명령을 작업으로 실행 하 고 현재 세션에서 작업 개체를 만듭니다.
이 명령은 변수에 저장 된 작업 개체를 반환 합니다 `$j` . `$j`변수는 작업 개체를 표시 합니다.

변수의 session 개체가 `$s` 파이프라인에서로 전송 되 `Disconnect-PSSession` 고 세션의 연결이 끊어집니다.

`$j`변수가 표시 되 고 변수에서 작업 개체의 연결이 끊어질 때의 영향을 보여 줍니다 `$j` . 이제 작업 상태가 Disconnected입니다.

는 `Receive-Job` 변수의 작업에서 실행 됩니다 `$j` . 출력은 세션 및 작업의 연결을 끊기 전에 작업에서 출력 반환을 시작 했다는 것을 보여 줍니다.

`Connect-PSSession`Cmdlet은 동일한 클라이언트 세션에서 실행 됩니다. 명령은 Server01 컴퓨터의 테스트 세션에 다시 연결 하 여 해당 세션을 변수에 저장 합니다 `$s2` .

`Receive-PSSession`Cmdlet은 세션에서 실행 중인 작업의 결과를 가져옵니다. 명령이 동일한 세션에서 실행 되기 때문에는 `Receive-PSSession` 기본적으로 결과를 작업으로 반환 하 고 동일한 작업 개체를 다시 실행 합니다. 이 명령은 작업을 `$j2` 변수에 저장 합니다. `Receive-Job`Cmdlet은 변수의 작업 결과를 가져옵니다 `$j` .

## PARAMETERS

### -AllowRedirection

이 cmdlet이이 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션할 수 있음을 나타냅니다.

**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다. 기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있도록 설정할 수 있습니다.

또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다. Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 `$PSSessionOption` 합니다. 기본값은 5입니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

응용 프로그램을 지정 합니다. 이 cmdlet은 지정 된 응용 프로그램을 사용 하는 세션에만 연결 합니다.

연결 URI의 애플리케이션 이름 세그먼트를 입력합니다. 예를 들어 다음 연결 URI에서 WSMan은 응용 프로그램 이름 `http://localhost:5985/WSMAN` 입니다.

세션의 응용 프로그램 이름은 세션의 **Runspace.ConnectionInfo.AppName** 속성에 저장됩니다.

매개 변수의 값은 세션을 선택 및 필터링 하는 데 사용 됩니다. 세션에서 사용 하는 응용 프로그램은 변경 되지 않습니다.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
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
> 사용자 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스 (예: 원격 네트워크 공유 액세스)에 대 한 인증이 필요한 명령에 대해 설계 되었습니다. 이렇게 하면 원격 작업의 보안 위험이 커집니다. 원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다. 인증서의 인증서 지문을 입력합니다.

인증서는 클라이언트 인증서 기반 인증에 사용됩니다. 인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정으로는 사용할 수 없습니다.

인증서 지문을 가져오려면 `Get-Item` `Get-ChildItem` PowerShell 드라이브에서 또는 명령을 사용 `Cert:` 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

연결이 끊긴 세션을 저장할 컴퓨터를 지정합니다. 세션은 서버 쪽 또는 연결 끝에 있는 컴퓨터에 저장 됩니다. 기본값은 로컬 컴퓨터입니다.

한 컴퓨터의 NetBIOS 이름, IP 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.
와일드 카드 문자는 허용 되지 않습니다. 로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 ( `.` ), 또는 localhost를 입력 합니다 `$env:COMPUTERNAME` .

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

세션 구성의 이름을 지정 합니다. 이 cmdlet은 지정 된 세션 구성을 사용 하는 세션에만 연결 합니다.

세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다. 구성 이름만 지정하는 경우 다음 스키마 URI가 추가됩니다.

`http://schemas.microsoft.com/powershell`.

세션의 구성 이름은 세션의 **ConfigurationName** 속성에 저장됩니다.

매개 변수의 값은 세션을 선택 및 필터링 하는 데 사용 됩니다. 세션에서 사용 하는 세션 구성을 변경 하지 않습니다.

세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](./About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

연결이 끊어진 세션에 다시 연결 하는 데 사용 되는 연결 끝점을 정의 하는 URI를 지정 합니다.

URI는 정규화된 URI여야 합니다. 문자열 형식은 다음과 같습니다.

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

기본값은 다음과 같습니다.

`http://localhost:5985/WSMAN`

연결 URI를 지정 하지 않으면 **UseSSL** , **ComputerName** , **Port** 및 **ApplicationName** 매개 변수를 사용 하 여 연결 uri 값을 지정할 수 있습니다.

URI의 **Transport** 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다. 전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션이 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다. PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.

대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

연결이 끊긴 세션에 연결할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

연결 되지 않은 세션의 ID를 지정 합니다. **Id** 매개 변수는 연결이 끊어진 세션이 이전에 현재 세션에 연결 된 경우에만 작동 합니다.

이 매개 변수는 유효 하지만, 세션이 로컬 컴퓨터에 저장 되어 있지만 현재 세션에 연결 되지 않은 경우 유효 하지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -InstanceId

연결이 끊긴 세션의 인스턴스 ID를 지정합니다. 인스턴스 ID는 로컬 또는 원격 컴퓨터의 **PSSession** 을 고유 하 게 식별 하는 GUID입니다. 인스턴스 ID는 **PSSession** 의 **InstanceID** 속성에 저장 됩니다.

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName

에서 반환 하는 작업의 이름을 지정 합니다 `Receive-PSSession` .

`Receive-PSSession`**Outtarget** 매개 변수 값이 job 이거나 연결이 끊어진 세션에서 실행 중인 작업이 현재 세션에서 시작 된 경우 작업을 반환 합니다.

연결 되지 않은 세션에서 실행 중인 작업이 현재 세션에서 시작 된 경우 PowerShell은 세션에서 원래 작업 개체를 재사용 하 고 **JobName** 매개 변수의 값을 무시 합니다.

연결 되지 않은 세션에서 실행 중인 작업이 다른 세션에서 시작 된 경우 PowerShell에서 새 작업 개체를 만듭니다. 기본 이름이 사용되지만 이 매개 변수를 사용하여 이름을 변경할 수 있습니다.

**Outtarget** 매개 변수의 기본값 또는 명시적 값이 Job이 아닌 경우 명령은 성공 하지만 **JobName** 매개 변수는 영향을 주지 않습니다.

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

### -Name

연결이 끊긴 세션의 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutTarget

세션 결과가 반환되는 방법을 결정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- **작업**. 작업 개체에 결과를 비동기적으로 반환합니다. **JobName** 매개 변수를 사용하여 작업의 이름이나 새 이름을 지정할 수 있습니다.
- **호스트**. 결과를 명령줄에 반환합니다(동기적). 명령을 다시 시작 중이거나 결과가 다수의 개체로 구성된 경우 응답이 지연될 수도 있습니다.

**Outtarget** 매개 변수의 기본값은 Host입니다. 연결이 끊어진 세션에서 수신 중인 명령이 현재 세션에서 시작 된 경우 **Outtarget** 매개 변수의 기본값은 명령이 시작 된 형식입니다. 명령이 작업으로 시작 된 경우 기본적으로 작업으로 반환 됩니다. 그렇지 않으면 기본적으로 호스트 프로그램에 반환 됩니다.

일반적으로 호스트 프로그램은 반환된 개체를 명령줄에 지연 없이 표시하지만 이 동작은 경우에 따라 달라질 수 있습니다.

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

세션에 다시 연결 하는 데 사용 되는 원격 컴퓨터의 네트워크 포트를 지정 합니다. 원격 컴퓨터에 연결 하려면 연결에서 사용 하는 포트에서 수신 대기 해야 합니다. 기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.

대체 포트를 사용 하기 전에 해당 포트에서 수신 대기 하도록 원격 컴퓨터의 WinRM 수신기를 구성 해야 합니다. 수신기를 구성 하려면 PowerShell 프롬프트에 다음 두 명령을 입력 합니다.

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

필요한 경우가 아니면 **Port** 매개 변수를 사용 하지 마세요. 명령에 설정 된 포트는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다. 대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.

```yaml
Type: System.Int32
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

연결이 끊긴 세션을 지정합니다. **Pssession이** 포함 된 변수 또는 **pssession** 을 만들거나 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .

```yaml
Type: System.Management.Automation.Runspaces.PSSession
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

옵션의 기본값은 설정 된 경우 기본 설정 변수의 값에 따라 결정 됩니다 `$PSSessionOption` . 그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.

세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다. 그러나 세션 구성에 설정 된 최대값, 할당량 또는 제한 보다 우선 적용 되지 않습니다.

기본값을 포함 하는 세션 옵션에 대 한 설명은를 참조 하십시오 `New-PSSessionOption` . **$PSSessionOption** 기본 설정 변수에 대 한 자세한 내용은 [about_Preference_Variables](./About/about_Preference_Variables.md)을 참조 하세요. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](./About/about_Session_Configurations.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

이 cmdlet은 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 연결이 끊어진 세션에 연결 함을 나타냅니다. 기본적으로 SSL은 사용 되지 않습니다.

WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다. **UseSSL** 은 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 보내는 추가 보호입니다.

이 매개 변수를 사용 하 고 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: False
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

Cmdlet에서 반환 된 개체와 같이 session 개체를이 cmdlet으로 파이프 할 수 있습니다 `Get-PSSession` .

### System.Int32

세션 Id를이 cmdlet으로 파이프 할 수 있습니다.

### System.Guid

이 cmdlet은 세션의 인스턴스 Id를 파이프 할 수 있습니다.

### System.String

세션 이름을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.object 또는 PSObject

이 cmdlet은 연결 되지 않은 세션에서 실행 된 명령의 결과를 반환 합니다 (있는 경우). **Outtarget** 매개 변수의 값 또는 기본값이 job 인 경우은 `Receive-PSSession` 작업 개체를 반환 합니다. 그러지 않으면 해당 명령 결과를 나타내는 개체를 반환합니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

`Receive-PSSession` 연결을 끊은 세션 에서만 결과를 가져옵니다. PowerShell 3.0 이상 버전을 실행 하는 컴퓨터에서는 연결 또는 종료 된 세션만 연결을 끊고 다시 연결할 수 있습니다.

연결 되지 않은 세션에서 실행 중 이었던 명령이 결과를 생성 하지 않거나 결과가 이미 다른 세션으로 반환 된 경우에서 `Receive-PSSession` 출력을 생성 하지 않습니다.

세션의 출력 버퍼링 모드는 세션의 연결이 끊어질 때 세션의 명령이 출력을 관리 하는 방법을 결정 합니다. 세션의 **OutputBufferingMode** 옵션 값이 Drop이 고 출력 버퍼가 가득 차면 명령이 출력을 삭제 하기 시작 합니다. `Receive-PSSession` 이 출력을 복구할 수 없습니다. 출력 버퍼링 모드 옵션에 대 한 자세한 내용은 [새-PSSessionOption](New-PSSessionOption.md) 및 [new-pstransportoption](New-PSTransportOption.md) cmdlet에 대 한 도움말 문서를 참조 하세요.

**Pssession** 에 연결 하거나 결과를 수신할 때 **pssession** 의 유휴 시간 제한 값을 변경할 수 없습니다. 의 **sessionoption** 매개 변수는 `Receive-PSSession` **IdleTimeout** 값을 포함 하는 **sessionoption** 개체를 사용 합니다. 그러나 **IdleTimeout** PSSession에 연결 하거나 결과를 수신할 때 **Sessionoption** 개체의 idletimeout 값과 **idletimeout** 값은 `$PSSessionOption` 무시 됩니다. **PSSession**

- 또는 cmdlet을 사용 하 **PSSession** 고 pssession에서 연결을 끊으면 pssession **을 만들 때 pssession** 의 유휴 시간 제한 시간을 설정 하 고 변경할 수 있습니다 `New-PSSession` `Invoke-Command` . **PSSession**
- **PSSession** 의 **IdleTimeout** 속성은 연결이 끊어진 세션이 원격 컴퓨터에서 유지 되는 기간을 결정 하기 때문에 연결이 끊어진 세션에 매우 중요 합니다. 연결이 끊긴 세션은 연결이 끊긴 세션에서 명령을 실행 중인 경우에도 연결이 끊긴 순간부터 유휴 상태로 간주됩니다.

Cmdlet의 **AsJob** 매개 변수를 사용 하 여 원격 세션에서 작업 시작을 시작 하면 작업이 `Invoke-Command` 원격 세션에서 실행 되는 경우에도 현재 세션에서 작업 개체가 만들어집니다. 원격 세션의 연결을 끊으면 현재 세션의 작업 개체를 작업에서 끊습니다. 작업 개체는 반환 된 결과를 포함 하지만 연결 되지 않은 세션의 작업에서 새 결과를 수신 하지는 않습니다.

다른 클라이언트가 실행 중인 작업을 포함 하는 세션에 연결 하는 경우 원래 세션의 원래 작업 개체에 전달 된 결과를 새로 연결 된 세션에서는 사용할 수 없습니다. 원래 작업 개체에 전달되지 않은 결과만 다시 연결된 세션에서 사용할 수 있습니다.

마찬가지로, 세션에서 스크립트를 시작한 다음 세션에서 연결을 끊는 경우에는 세션에 연결 하는 다른 클라이언트에서 연결을 끊기 전에 스크립트가 세션에 전달 하는 결과를 사용할 수 없습니다.

연결을 끊을 세션에서 데이터 손실을 방지 하려면 cmdlet의 **InDisconnectedSession** 매개 변수를 사용 합니다 `Invoke-Command` . 이 매개 변수는 결과가 현재 세션에 반환되지 않도록 하기 때문에 세션을 다시 연결할 때 모든 결과를 사용할 수 있습니다.

Cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` 원격 세션에서 명령을 실행 하 여 데이터 손실을 방지할 수도 있습니다. 이 경우 작업 개체가 원격 세션에서 만들어집니다. Cmdlet을 사용 `Receive-PSSession` 하 여 작업 결과를 가져올 수 없습니다. 대신 cmdlet을 사용 하 여 `Connect-PSSession` 세션에 연결한 다음 cmdlet을 사용 하 여 `Invoke-Command` `Receive-Job` 세션에서 명령을 실행 합니다.

실행 중인 작업을 포함 하는 세션의 연결을 끊은 다음 다시 연결 하면 작업의 연결이 끊어지고 동일한 세션에 다시 연결 된 경우에만 원래 작업 개체가 다시 사용 되며, 다시 연결 하는 명령에서 새 작업 이름을 지정 하지 않습니다. 세션이 다른 클라이언트 세션에 다시 연결 되어 있거나 새 작업 이름이 지정 된 경우 PowerShell에서 새 세션에 대 한 새 작업 개체를 만듭니다.

**PSSession** 의 연결을 끊으면 세션 상태가 Disconnected이 고 Availability가 None입니다.

- **State** 속성 값은 현재 세션을 기준으로 합니다. 연결 끊김 값은 **PSSession** 이 현재 세션에 연결 되지 않았음을 의미 합니다. 그러나 모든 세션에서 **PSSession** 의 연결이 끊어졌음을 의미 하는 것은 아닙니다. 다른 세션에 연결되어 있을 수도 있습니다.
  세션에 연결하거나 다시 연결할 수 있는지 확인하려면 **Availability** 속성을 사용합니다.
- **가용성** 값 None은 세션에 연결할 수 있음을 나타냅니다. 사용 중 값은 다른 세션에 연결 되어 있으므로 **PSSession** 에 연결할 수 없음을 나타냅니다.
- 세션의 **State** 속성 값에 대 한 자세한 내용은 [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)를 참조 하세요.
- 세션의 **Availability** 속성 값에 대 한 자세한 내용은 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)를 참조 하십시오.

## 관련 링크

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Session_Configurations](./About/about_Session_Configurations.md)

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Remove-PSSession](Remove-PSSession.md)
