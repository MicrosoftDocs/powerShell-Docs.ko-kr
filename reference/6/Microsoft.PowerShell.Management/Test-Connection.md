---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 54ba1d7db60db7b4bb64f3161bba9c1fba124219
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212194"
---
# Test-Connection

## 개요
하나 이상의 컴퓨터에 ICMP 에코 요청 패킷 또는 ping을 보냅니다.

## SYNTAX

### 수 (기본값)

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### 계속

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### DetectionOfMTUSize

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### 경로 추적

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### ConnectionByTCPPort

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## 설명

`Test-Connection`Cmdlet은 ICMP (Internet Control Message Protocol) 에코 요청 패킷 또는 ping을 하나 이상의 원격 컴퓨터로 보내고 에코 응답을 반환 합니다. 이 cmdlet을 사용 하 여 IP 네트워크를 통해 특정 컴퓨터에 연결할 수 있는지 여부를 확인할 수 있습니다.

의 매개 변수를 사용 `Test-Connection` 하 여 송신 및 수신 컴퓨터를 모두 지정 하 고, 명령을 백그라운드 작업으로 실행 하 고, 제한 시간 및 ping 수를 설정 하 고, 연결 및 인증을 구성할 수 있습니다.

친숙 한 **ping** 명령과 달리은 `Test-Connection` PowerShell에서 조사할 수 있는 **Testconnectioncommand +을 보고** 하는 개체를 반환 합니다. **Quiet** 매개 변수는 **테스트 된 각** 연결에 대해 system.string 개체에서 **부울** 값을 반환 합니다. 여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.

## 예제

### 예제 1: 원격 컴퓨터에 에코 요청 보내기

이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 echo request 패킷을 보냅니다.

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
Pinging Server01 [10.59.137.44] with 32 bytes of data:
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Ping complete.

Source     Destination Replies
------     ----------- -------
Server01   Server01    {System.Net.NetworkInformation.PingReply, System.Net.NetworkInformation ...
```

`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다. **IPv4** 매개 변수는 테스트에 대 한 프로토콜을 지정 합니다.

**Testconnectioncommand + a report** 개체가 **성공** 스트림으로 전송 되는 동안 ping 출력이 **정보** 스트림으로 전송 됩니다. 출력 스트림에 대 한 자세한 내용은 [about_Redirection](../microsoft.powershell.core/about/about_redirection.md)를 참조 하세요.

### 예 2: 여러 컴퓨터에 에코 요청 보내기

이 예제에서는 로컬 컴퓨터에서 여러 원격 컴퓨터로 ping을 보냅니다.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### 예 3: 여러 컴퓨터에서 컴퓨터로 에코 요청 보내기

이 예제에서는 여러 원본 컴퓨터의 ping을 단일 원격 컴퓨터 (Server01)로 보냅니다.

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

이 명령 형식을 사용하여 여러 지점으로부터의 연결 지연을 테스트할 수 있습니다.

### 예제 4: 매개 변수를 사용 하 여 테스트 명령 사용자 지정

이 예제에서는의 매개 변수를 사용 하 여 `Test-Connection` 명령을 사용자 지정 합니다. 로컬 컴퓨터에서 원격 컴퓨터로 ping 테스트를 보냅니다.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01를 지정 합니다. **Count** 매개 변수는 2 초 간격으로 Server01 컴퓨터로 전송 되는 세 개의 **ping을 지정** 합니다.

홉 수가 연장 되거나 트래픽이 많은 네트워크 조건으로 인해 ping 응답이 평소 보다 오래 걸릴 것으로 예상 되는 경우 이러한 옵션을 사용할 수 있습니다.

### 예 5: 백그라운드 작업으로 테스트 실행

이 예제에서는 `Test-Connection` 명령을 PowerShell 백그라운드 작업으로 실행 하는 방법을 보여 줍니다.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

이 `Start-Job` 명령은 cmdlet을 사용 하 여 `Test-Connection` 기업에서 많은 컴퓨터를 ping 합니다.
**TargetName** 매개 변수 값은 `Get-Content` 파일에서 컴퓨터 이름 목록을 읽는 명령입니다 `Servers.txt` . 이 명령은 cmdlet을 사용 하 여 `Start-Job` 명령을 백그라운드 작업으로 실행 하 고 해당 작업을 `$job` 변수에 저장 합니다.

`if`명령은 작업이 아직 실행 되 고 있지 않은지 확인 합니다. 작업이 실행 되 고 있지 않으면 `Receive-Job` 결과를 가져와서 `$Results` 변수에 저장 합니다.

### 예 6: 연결 테스트에 성공 하는 경우에만 세션 만들기

이 예에서는 컴퓨터로 전송 된 ping 중 하나 이상이 성공한 경우에만 Server01 컴퓨터에서 세션을 만듭니다.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

이 `if` 명령은 cmdlet을 사용 하 여 `Test-Connection` Server01 컴퓨터를 ping 합니다. 이 명령은 **Testconnectioncommand +** 를 사용 하는 대신 **부울** 값을 반환 하는 **Quiet** 매개 변수를 사용 합니다.

`$True`4 개의 ping 중 하나라도 성공한 경우이 값은입니다. Ping이 실패 한 경우 값은 `$False` 입니다.

명령에서 값을 반환 하는 경우이 `Test-Connection` `$True` 명령은 cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다.

### 예 7: 경로 추적 매개 변수 사용

PowerShell 6.0부터 **경로 추적** 매개 변수는 로컬 컴퓨터와 지정한 원격 대상 간의 경로를 **TargetName** 매개 변수로 매핑합니다.

```powershell
Test-Connection -TargetName www.microsoft.com -Traceroute | ForEach-Object {
  $_ | Format-Table Source, DestinationAddress, DestinationHost
  $_.Replies | ForEach-Object {
      $_ | Format-Table Hop, ReplyRouterAddress
      $_.PingReplies | Format-Table
  }
}
```

```Output
Tracing route to www.microsoft.com [96.6.27.90] over a maximum of 128 hops:
  1   0 ms   0 ms   0 ms   192.168.0.3 [192.168.0.3]
  2   0 ms   0 ms   0 ms   192.168.1.1 [192.168.1.1]
  3   3 ms   29 ms   4 ms   96.6.27.90 [96.6.27.90]
Trace complete.

Source      DestinationAddress DestinationHost   Replies
------      ------------------ ---------------   -------
SERVER01    96.6.27.90         www.microsoft.com {, , }

Hop ReplyRouterAddress
--- ------------------
  1 192.168.0.3

    Status Address      RoundtripTime Options Buffer
    ------ -------      ------------- ------- ------
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  2 192.168.1.1

    Status Address     RoundtripTime Options Buffer
    ------ -------     ------------- ------- ------
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  3 96.6.27.90

 Status Address    RoundtripTime Options                                   Buffer
 ------ -------    ------------- -------                                   ------
Success 96.6.27.90             3 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             2 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             4 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
```

이 `Test-Connection` 명령은 **경로 추적** 매개 변수를 사용 합니다. 개체인 결과는 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` cmdlet으로 파이프 됩니다 `ForEach-Object` . `ForEach-Object` 포함 된 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` 개체와 후속 개체의 구조적 출력을 만듭니다 `[System.Net.NetworkInformation.PingReply]` .

## PARAMETERS

### -BufferSize

이 명령과 함께 보낸 버퍼의 크기(바이트)를 지정합니다. 기본값은 32입니다.

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -개수

보낼 에코 요청의 수를 지정합니다. 기본값은 4입니다.

```yaml
Type: System.Int32
Parameter Sets: PingCount
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
Parameter Sets: PingCount, PingContinues
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
Parameter Sets: PingCount, PingContinues
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
Parameter Sets: PingCount, PingContinues, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

Cmdlet이 기본 작업 인 ping 테스트를 수행 하도록 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: Ping test
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

**Quiet** 매개 변수는 **System.string 개체에서** **부울** 값을 반환 합니다. 이 매개 변수를 사용 하면 모든 오류가 표시 되지 않습니다.

테스트 된 각 연결은 **부울** 값을 반환 합니다. **TargetName** 매개 변수가 여러 컴퓨터를 지정 하는 경우에는 **부울** 값의 배열이 반환 됩니다.

Ping **any** 이 성공 하면 `$True` 이 반환 됩니다.

**모든** ping이 실패 하면 `$False` 이 반환 됩니다.

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

Cmdlet이 대상의 DNS 이름을 확인 하려고 합니다.

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

```yaml
Type: System.String
Parameter Sets: PingCount, PingContinues, TraceRoute, ConnectionByTCPPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetName

테스트할 컴퓨터를 지정 합니다. 컴퓨터 이름을 입력하거나 IP 주소를 IPv4 또는 IPv6 형식으로 입력합니다. 와일드 카드 문자는 허용 되지 않습니다. 이 매개 변수는 필수적 요소입니다. **ComputerName** 은이 매개 변수에 대 한 별칭입니다.

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

### -TCPPort

TCP 연결 테스트에 사용할 대상의 TCP 포트 번호를 지정 합니다. 이 cmdlet은 대상의 지정 된 포트에 대 한 TCP 연결을 시도 합니다.

```yaml
Type: System.Int32
Parameter Sets: ConnectionByTCPPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
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

Cmdlet이 경로 추적 테스트를 수행 하도록 합니다. 이 매개 변수를 사용 하는 경우 cmdlet은 개체를 반환 합니다 `TestConnectionCommand+TraceRouteResult` .

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

### -계속

Cmdlet이 ping 요청을 계속 해 서 보냅니다. 이 매개 변수는 **Count** 매개 변수와 함께 사용할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MTUSizeDetect

이 매개 변수는 경로 MTU 크기를 검색 하는 데 사용 됩니다. 이 cmdlet은 대상에 대 한 경로 MTU 크기를 포함 하는 트 대 여 **회신 # MTUSize** 개체를 반환 합니다. 경로 MTU에 대 한 자세한 내용은 위키백과의 [경로 Mtu 검색](https://wikipedia.org/wiki/Path_MTU_Discovery) 문서를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetectionOfMTUSize
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에는 입력을 파이프 할 수 없습니다.

## 출력

### Testconnectioncommand + TraceRouteResult report, testconnectioncommand +, Boolean, anreply # mtusing

**Quiet** 매개 변수를 지정 하면 **부울** 값이 반환 됩니다. 여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다. 그렇지 않으면 `Test-Connection` 각 ping에 대 한 **Testconnectioncommand + a report** 개체를 반환 합니다.

## 참고

## 관련 링크

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
