---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: af8a953536bb9683ba737522ad738348c5c695e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602683"
---
# Test-Connection

## 개요
하나 이상의 컴퓨터에 ICMP 에코 요청 패킷 또는 ping을 보냅니다.

## SYNTAX

### DefaultPing (기본값)

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### 반복 Ping

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### MtuSizeDetect

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### 경로 추적

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TcpPort

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## 설명

`Test-Connection`Cmdlet은 ICMP (Internet Control Message Protocol) 에코 요청 패킷 또는 ping을 하나 이상의 원격 컴퓨터로 보내고 에코 응답을 반환 합니다. 이 cmdlet을 사용 하 여 IP 네트워크를 통해 특정 컴퓨터에 연결할 수 있는지 여부를 확인할 수 있습니다.

의 매개 변수를 사용 `Test-Connection` 하 여 송신 및 수신 컴퓨터를 모두 지정 하 고, 명령을 백그라운드 작업으로 실행 하 고, 제한 시간 및 ping 수를 설정 하 고, 연결 및 인증을 구성할 수 있습니다.

친숙 한 **ping** 명령과 달리은 `Test-Connection` PowerShell에서 조사할 수 있는 **testconnectioncommand +** 가 나 상태 개체를 반환 합니다. **Quiet** 매개 변수는 **테스트 된 각** 연결에 대해 system.string 개체에서 **부울** 값을 반환 합니다. 여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.

## 예제

### 예제 1: 원격 컴퓨터에 에코 요청 보내기

이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 echo request 패킷을 보냅니다.

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
   Destination: Server01

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 ADMIN1           10.59.137.44                   24         32 Success
   2 ADMIN1           10.59.137.44                   39         32 Success
   3 ADMIN1           *                               *          * TimedOut
   4 ADMIN1           10.59.137.44                   28         32 Success
```

`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다. **IPv4** 매개 변수는 테스트에 대 한 프로토콜을 지정 합니다.

대상 컴퓨터에서 ping 응답 당 하나의 개체를 출력 스트림으로 전송 하는 일련의 **Testconnectioncommand +** ...

### 예 2: 여러 컴퓨터에 에코 요청 보내기

이 예제에서는 로컬 컴퓨터에서 여러 원격 컴퓨터로 ping을 보냅니다.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### 예제 3: 매개 변수를 사용 하 여 테스트 명령 사용자 지정

이 예제에서는의 매개 변수를 사용 하 여 `Test-Connection` 명령을 사용자 지정 합니다. 로컬 컴퓨터에서 원격 컴퓨터로 ping 테스트를 보냅니다.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01를 지정 합니다. **Count** 매개 변수는 2 초 간격으로 Server01 컴퓨터로 전송 되는 세 개의 **ping을 지정** 합니다.

홉 수가 연장 되거나 트래픽이 많은 네트워크 조건으로 인해 ping 응답이 평소 보다 오래 걸릴 것으로 예상 되는 경우 이러한 옵션을 사용할 수 있습니다.

### 예제 4: 백그라운드 작업으로 테스트 실행

이 예제에서는 `Test-Connection` 명령을 PowerShell 백그라운드 작업으로 실행 하는 방법을 보여 줍니다.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

이 `Start-Job` 명령은 cmdlet을 사용 하 여 `Test-Connection` 기업에서 많은 컴퓨터를 ping 합니다.
**TargetName** 매개 변수 값은 `Get-Content` 파일에서 컴퓨터 이름 목록을 읽는 명령입니다 `Servers.txt` . 이 명령은 cmdlet을 사용 하 여 `Start-Job` 명령을 백그라운드 작업으로 실행 하 고 해당 작업을 `$job` 변수에 저장 합니다.

이 `Receive-Job` 명령은 `-Wait` 작업이 완료 될 때까지로 지시한 다음 결과를 가져와서 `$Results` 변수에 저장 합니다.

### 예 5: 연결 테스트에 성공 하는 경우에만 세션 만들기

이 예에서는 컴퓨터로 전송 된 ping 중 하나 이상이 성공한 경우에만 Server01 컴퓨터에서 세션을 만듭니다.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

`Test-Connection`Cmdlet은 `Server01` **자동** 매개 변수를 제공 하 여 컴퓨터를 ping 합니다.
결과 값은 `$True` 4 개의 ping 중 하나라도 성공한 경우입니다. Ping이 실패 한 경우 값은 `$False` 입니다.

명령에서 값을 반환 하는 경우이 `Test-Connection` `$True` 명령은 cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다.

### 예제 6: 경로 추적 매개 변수 사용

PowerShell 6.0에 도입 된 **경로 추적** 매개 변수는 로컬 컴퓨터와 지정한 원격 대상 간의 경로를 **TargetName** 매개 변수로 매핑합니다.

```powershell
Test-Connection -TargetName www.google.com -Traceroute
```

```Output
   Target: google.com

Hop Hostname                  Ping Latency Status           Source       TargetAddress
                                      (ms)
--- --------                  ---- ------- ------           ------       -------------
  1 172.20.0.1                   1       4 Success          Lira         172.217.9.174
  1 172.20.0.1                   2       3 Success          Lira         172.217.9.174
  1 172.20.0.1                   3       2 Success          Lira         172.217.9.174
  2 12.108.153.193               1       3 Success          Lira         172.217.9.174
  2 12.108.153.193               2       3 Success          Lira         172.217.9.174
  2 12.108.153.193               3       2 Success          Lira         172.217.9.174
  3 12.244.85.177                1      11 Success          Lira         172.217.9.174
  3 12.244.85.177                2      12 Success          Lira         172.217.9.174
  3 12.244.85.177                3      12 Success          Lira         172.217.9.174
  4 *                            1      14 DestinationNetw… Lira         172.217.9.174
  4 *                            2       * TimedOut         Lira         172.217.9.174
  4 *                            3      20 DestinationNetw… Lira         172.217.9.174
  5 *                            1       * TimedOut         Lira         172.217.9.174
  5 *                            2      15 DestinationNetw… Lira         172.217.9.174
  5 *                            3       * TimedOut         Lira         172.217.9.174
  6 *                            1      18 DestinationNetw… Lira         172.217.9.174
  6 *                            2       * TimedOut         Lira         172.217.9.174
  6 *                            3      16 DestinationNetw… Lira         172.217.9.174
  7 *                            1       * TimedOut         Lira         172.217.9.174
  7 *                            2       * TimedOut         Lira         172.217.9.174
  7 *                            3       * TimedOut         Lira         172.217.9.174
  8 *                            1       * TimedOut         Lira         172.217.9.174
  8 *                            2       * TimedOut         Lira         172.217.9.174
  8 *                            3       * TimedOut         Lira         172.217.9.174
  9 *                            1       * TimedOut         Lira         172.217.9.174
  9 *                            2       * TimedOut         Lira         172.217.9.174
  9 *                            3       * TimedOut         Lira         172.217.9.174
 10 *                            1       * TimedOut         Lira         172.217.9.174
 10 *                            2       * TimedOut         Lira         172.217.9.174
 10 *                            3       * TimedOut         Lira         172.217.9.174
 11 172.217.9.174                1      23 Success          Lira         172.217.9.174
 11 172.217.9.174                2      21 Success          Lira         172.217.9.174
 11 172.217.9.174                3      22 Success          Lira         172.217.9.174
```

`Test-Connection`명령은 **경로 추적** 매개 변수를 사용 하 여 호출 됩니다. 개체 인 결과는 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` **성공** 출력 스트림으로 출력 됩니다.

## PARAMETERS

### -BufferSize

이 명령과 함께 보낸 버퍼의 크기(바이트)를 지정합니다. 기본값은 32입니다.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -반복

Cmdlet이 ping 요청을 계속 해 서 보냅니다. 이 매개 변수는 **Count** 매개 변수와 함께 사용할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RepeatPing
Aliases: Continuous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -개수

보낼 에코 요청의 수를 지정합니다. 기본값은 4입니다.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Delay

Ping 간격을 초 단위로 지정합니다.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DontFragment

이 매개 변수는 IP 헤더에서 **Don't Fragment** 플래그를 설정 합니다. 이 매개 변수를 **BufferSize** 매개 변수와 함께 사용 하 여 경로 MTU 크기를 테스트할 수 있습니다. 경로 MTU에 대 한 자세한 내용은 위키백과의 [경로 Mtu 검색](https://wikipedia.org/wiki/Path_MTU_Discovery) 문서를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IPv4

Cmdlet이 테스트에 대 한 IPv4 프로토콜을 사용 하도록 합니다.

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

### -IPv6

Cmdlet에서 테스트에 IPv6 프로토콜을 강제로 사용 하도록 합니다.

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

### -MaxHops

ICMP 요청 메시지를 보낼 수 있는 최대 홉 수를 설정 합니다. 기본값은 운영 체제에 의해 제어 됩니다. Windows 10의 기본값은 128 홉입니다.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

Cmdlet이 ping 테스트를 수행 하도록 합니다. 이는 cmdlet에 대 한 기본 모드입니다 `Test-Connection` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

**Quiet** 매개 변수는 **부울** 값을 반환 합니다. 이 매개 변수를 사용 하면 모든 오류가 표시 되지 않습니다.

테스트 된 각 연결은 **부울** 값을 반환 합니다. **TargetName** 매개 변수가 여러 컴퓨터를 지정 하는 경우에는 **부울** 값의 배열이 반환 됩니다.

지정 된 대상에 대 **한 ping** 이 성공 하면 `$True` 이 반환 됩니다.

지정 된 대상에 대 한 **모든** ping이 실패 하면 `$False` 이 반환 됩니다.

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

### -ResolveDestination

Cmdlet이 대상의 DNS 이름을 확인 하려고 합니다. **경로 추적** 매개 변수와 함께 사용 하는 경우 모든 중간 호스트의 DNS 이름도 검색 됩니다 (가능한 경우).

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

### -Source

Ping이 시작되는 컴퓨터의 이름을 지정합니다. 쉼표로 구분된 컴퓨터 이름의 목록을 입력합니다. 기본값은 로컬 컴퓨터입니다.

**참고:** 이 매개 변수는 PowerShell 버전 6 이상에서 작동 하지 않습니다.
이 매개 변수를 제공 해도 명령에는 영향을 주지 않습니다.

```yaml
Type: System.String
Parameter Sets: DefaultPing, RepeatPing, TraceRoute, TcpPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetName

테스트할 컴퓨터를 지정 합니다. 컴퓨터 이름을 입력하거나 IP 주소를 IPv4 또는 IPv6 형식으로 입력합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ComputerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TimeoutSeconds

테스트에 대 한 시간 제한 값을 설정 합니다. 제한 시간이 만료 되기 전에 응답이 수신 되지 않으면 테스트가 실패 합니다. 기본값은 5초입니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5 seconds
Accept pipeline input: False
Accept wildcard characters: False
```

### -경로 추적

Cmdlet이 경로 추적 테스트를 수행 하도록 합니다. 이 매개 변수를 사용 하는 경우 cmdlet은 개체를 반환 합니다 `TestConnectionCommand+TraceStatus` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TraceRoute
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MtuSize

이 매개 변수는 경로 MTU 크기를 검색 하는 데 사용 됩니다. 이 cmdlet은 대상에 대 한 경로 MTU 크기를 포함 하는 트 대 여 **회신 # MTUSize** 개체를 반환 합니다. 경로 MTU에 대 한 자세한 내용은 위키백과의 [경로 Mtu 검색](https://wikipedia.org/wiki/Path_MTU_Discovery) 문서를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MtuSizeDetect
Aliases: MtuSizeDetect

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -TcpPort

TCP 연결 테스트에 사용할 대상의 TCP 포트 번호를 지정 합니다. 이 cmdlet은 대상의 지정 된 포트에 대 한 TCP 연결을 시도 합니다.

연결을 설정할 수 있으면 `$True` 이 반환 됩니다.

연결을 설정할 수 없는 경우이 `$False` 반환 됩니다.

```yaml
Type: System.Int32
Parameter Sets: TcpPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에는 입력을 파이프 할 수 없습니다.

## 출력

### TestConnectionCommand + TraceStatus, TestConnectionCommand +, Boolean, TestConnectionCommand + PingMtuStatus

기본적으로는 `Test-Connection` 각 ping 회신에 대 한 **Testconnectioncommand +, 상태** 개체를 반환 합니다.

**경로 추적** 매개 변수를 지정 하는 경우 cmdlet은 경로를 따라 각 ping 응답에 대해 **testconnectioncommand + TraceStatus** 개체를 반환 합니다.

**Quiet** 또는 **TcpPort** 매개 변수를 지정 하면 **부울** 값이 반환 됩니다. 여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.

## 참고

## 관련 링크

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)

