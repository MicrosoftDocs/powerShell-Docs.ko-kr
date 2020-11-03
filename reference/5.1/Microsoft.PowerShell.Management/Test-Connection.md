---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: a8d3923db69a20cfada58391944b592cf999e6ef
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214337"
---
# Test-Connection

## 개요
하나 이상의 컴퓨터에 ICMP 에코 요청 패킷 또는 ping을 보냅니다.

## SYNTAX

### Default (기본값)

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### 원본

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### Quiet

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## 설명

`Test-Connection`Cmdlet은 ICMP (Internet Control Message Protocol) 에코 요청 패킷 또는 ping을 하나 이상의 원격 컴퓨터로 보내고 에코 응답을 반환 합니다. 이 cmdlet을 사용 하 여 IP 네트워크를 통해 특정 컴퓨터에 연결할 수 있는지 여부를 확인할 수 있습니다.

의 매개 변수를 사용 `Test-Connection` 하 여 송신 및 수신 컴퓨터를 모두 지정 하 고, 명령을 백그라운드 작업으로 실행 하 고, 제한 시간 및 ping 수를 설정 하 고, 연결 및 인증을 구성할 수 있습니다.

친숙 한 **ping** 명령과 달리은 `Test-Connection` PowerShell에서 조사할 수 있는 **Win32_PingStatus** 개체를 반환 합니다. **Quiet** 매개 변수는 **테스트 된 각** 연결에 대해 system.string 개체에서 **부울** 값을 반환 합니다. 여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.

## 예제

### 예제 1: 원격 컴퓨터에 에코 요청 보내기

이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 echo request 패킷을 보냅니다.

```powershell
Test-Connection -ComputerName Server01
```

```Output
Source        Destination     IPV4Address     IPV6Address  Bytes    Time(ms)
------        -----------     -----------     -----------  -----    --------
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       1
```

`Test-Connection`**ComputerName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다.

### 예 2: 여러 컴퓨터에 에코 요청 보내기

이 예제에서는 로컬 컴퓨터에서 여러 원격 컴퓨터로 ping을 보냅니다.

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### 예 3: 여러 컴퓨터에서 컴퓨터로 에코 요청 보내기

이 예제에서는 여러 원본 컴퓨터의 ping을 단일 원격 컴퓨터 (Server01)로 보냅니다.

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

`Test-Connection`**Credential** 매개 변수를 사용 하 여 원본 컴퓨터에서 ping 요청을 보낼 수 있는 권한이 있는 사용자의 자격 증명을 지정 합니다. 이 명령 형식을 사용하여 여러 지점으로부터의 연결 지연을 테스트할 수 있습니다.

### 예제 4: 매개 변수를 사용 하 여 테스트 명령 사용자 지정

이 예제에서는의 매개 변수를 사용 하 여 `Test-Connection` 명령을 사용자 지정 합니다. 로컬 컴퓨터에서 원격 컴퓨터로 ping 테스트를 보냅니다.

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

`Test-Connection`**ComputerName** 매개 변수를 사용 하 여 Server01를 지정 합니다. **Count** 매개 변수는 2 초 간격으로 Server01 컴퓨터로 전송 되는 세 개의 **ping을 지정** 합니다.

홉 수가 연장 되거나 트래픽이 많은 네트워크 조건으로 인해 ping 응답이 평소 보다 오래 걸릴 것으로 예상 되는 경우 이러한 옵션을 사용할 수 있습니다.

### 예 5: 백그라운드 작업으로 테스트 실행

이 예제에서는 `Test-Connection` 명령을 PowerShell 백그라운드 작업으로 실행 하는 방법을 보여 줍니다.

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

`Test-Connection`명령은 기업에서 많은 컴퓨터를 ping 합니다. **ComputerName** 매개 변수 값은 `Get-Content` 에서 컴퓨터 이름 목록을 읽는 명령입니다 `Servers.txt file` . 이 명령은 **AsJob** 매개 변수를 사용 하 여 명령을 백그라운드 작업으로 실행 하 고 해당 작업을 변수에 저장 `$job` 합니다.

`if`명령은 작업이 아직 실행 되 고 있지 않은지 확인 합니다. 작업이 실행 되 고 있지 않으면 `Receive-Job` 결과를 가져와서 `$Results` 변수에 저장 합니다.

### 예 6: 자격 증명을 사용 하 여 원격 컴퓨터 Ping

이 명령은 cmdlet을 사용 하 여 `Test-Connection` 원격 컴퓨터를 ping 합니다.

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

이 명령은 **Credential** 매개 변수를 사용 하 여 원격 컴퓨터를 ping 할 수 있는 권한을 가진 사용자 계정을 지정 하 고 **가장** 매개 변수를 사용 하 여를 **식별** 하도록 가장 수준을 변경 합니다.

### 예 7: 연결 테스트에 성공 하는 경우에만 세션 만들기

이 예에서는 컴퓨터로 전송 된 ping 중 하나 이상이 성공한 경우에만 Server01 컴퓨터에서 세션을 만듭니다.

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

이 `if` 명령은 cmdlet을 사용 하 여 `Test-Connection` Server01 컴퓨터를 ping 합니다. 이 명령은 **Win32_PingStatus** 개체 대신 **부울** 값을 반환 하는 **Quiet** 매개 변수를 사용 합니다. 이 값은 `$True` 4 개의 ping 중 하나라도 성공 하면이 고, 그렇지 않으면입니다 `$False` .

명령에서 값을 반환 하는 경우이 `Test-Connection` `$True` 명령은 cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다.

## PARAMETERS

### -AsJob

이 cmdlet이 백그라운드 작업으로 실행 됨을 나타냅니다.

이 매개 변수를 사용 하려면 원격을 사용 하도록 로컬 및 원격 컴퓨터를 구성 해야 하 고 Windows Vista 이상 버전의 Windows 운영 체제에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 열어야 합니다. 자세한 내용은 [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md)을 참조하세요.

**AsJob** 매개 변수를 지정 하면이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환 합니다. 작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다. AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다. 작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -BufferSize

이 명령과 함께 보낸 버퍼의 크기(바이트)를 지정합니다. 기본값은 32입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Ping할 컴퓨터를 지정합니다. 컴퓨터 이름을 입력하거나 IP 주소를 IPv4 또는 IPv6 형식으로 입력합니다. 와일드카드 문자는 사용할 수 없습니다. 이 매개 변수는 필수적 요소입니다.

이 매개 변수는 PowerShell 원격을 사용 하지 않습니다. 컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.

> [!NOTE]
> **ComputerName** 매개 변수는 PowerShell 6.0 이상에서 **TargetName** 으로 이름이 변경 됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, IPAddress, __SERVER, Server, Destination

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -개수

보낼 에코 요청의 수를 지정합니다. 기본값은 4입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

원본 컴퓨터에서 ping 요청에서 보낼 수 있는 권한을 가진 사용자 계정을 지정합니다. User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나, cmdlet의 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

**Credential** 매개 변수는 명령에 **Source** 매개 변수가 사용된 경우에만 유효합니다. 자격 증명은 대상 컴퓨터에 영향을 주지 않습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Source
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

이 cmdlet이 WMI와 함께 사용 하는 인증 수준을 지정 합니다.
`Test-Connection` WMI를 사용 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- **Default** 입니다. Windows 인증
- **없음** . COM 인증 없음
- **연결** . 연결 수준 COM 인증
- 을 **호출** 합니다. 호출 수준 COM 인증
- **패킷입니다** . 패킷 수준 COM 인증
- **PacketIntegrity** . 패킷 개인 정보 수준 COM 인증
- **PacketPrivacy** . 패킷 개인 정보 수준 COM 인증
- **변경 되지 않았습니다** . 이전 명령과 동일

기본값은 열거형 값이 **4** 인 **패킷입니다** . 이 매개 변수 값에 대 한 자세한 내용은 [Authenticationlevel](/dotnet/api/system.management.authenticationlevel) 열거를 참조 하세요.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet (enumerated value of 4)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Delay

Ping 간격을 초 단위로 지정합니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1 (second)
Accept pipeline input: False
Accept wildcard characters: False
```

### -가장

이 cmdlet이 WMI를 호출할 때 사용할 가장 수준을 지정 합니다. `Test-Connection` WMI를 사용 합니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- **Default** 입니다. 기본 가장입니다.
- **익명** . 호출자의 ID를 숨깁니다.
- 를 **식별** 합니다. 개체가 호출자의 자격 증명을 쿼리할 수 있습니다.
- **가장** . 개체가 호출자의 자격 증명을 사용할 수 있습니다.

기본값은 **Impersonate** 입니다.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

프로토콜을 지정 합니다. 이 매개 변수에 허용 되는 값은 DCOM 및 WSMan입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

**Quiet** 매개 변수는 **System.string 개체에서** **부울** 값을 반환 합니다. 이 매개 변수를 사용 하면 모든 오류가 표시 되지 않습니다.

테스트 된 각 연결은 **부울** 값을 반환 합니다. **ComputerName** 매개 변수가 여러 컴퓨터를 지정 하는 경우에는 **부울** 값의 배열이 반환 됩니다.

Ping **any** 이 성공 하면 `$True` 이 반환 됩니다.

**모든** ping이 실패 하면 `$False` 이 반환 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Quiet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Ping이 시작되는 컴퓨터의 이름을 지정합니다. 쉼표로 구분된 컴퓨터 이름의 목록을 입력합니다. 기본값은 로컬 컴퓨터입니다.

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: FCN, SRC

Required: True
Position: 1
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.
이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.

제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeToLive

패킷을 전달할 수 있는 최대 시간을 지정 합니다. 게이트웨이, 라우터 등의 모든 홉에 대해 **TimeToLive** 값이 1 씩 감소 합니다. 0에서 패킷이 삭제 되 고 오류가 반환 됩니다.
**Windows** 에서 기본값은 **128** 입니다. **TimeToLive** 매개 변수의 별칭은 **TTL** 입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TTL

Required: False
Position: Named
Default value: 128 in Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

이 cmdlet이 WSMan 프로토콜을 사용 하는 경우 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- Basic
- CredSSP
- 기본값
- 다이제스트
- Kerberos
- Negotiate

기본값은 Default입니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0)를 참조 하세요.

주의: 사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 경우와 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.
이렇게 하면 원격 작업의 보안 위험이 커집니다.
원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에는 입력을 파이프 할 수 없습니다.

## 출력

### Root\cimv2\ 개체 # Win32_PingStatus, system.web. Remorerere.

**AsJob** 매개 변수를 지정 하는 경우이 cmdlet은 작업 개체를 반환 합니다.

**Quiet** 매개 변수를 지정 하면 **부울** 값이 반환 됩니다. 여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다. 그렇지 않으면 `Test-Connection` 각 ping에 대 한 **Win32_PingStatus** 개체를 반환 합니다.

## 참고

이 cmdlet은 **Win32_PingStatus** 클래스를 사용 합니다. 명령은 `Get-WMIObject Win32_PingStatus` `Test-Connection` 명령과 동일 합니다.

**원본** 매개 변수 집합은 PowerShell 3.0에서 도입 되었습니다.

## 관련 링크

[Add-Computer](Add-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
