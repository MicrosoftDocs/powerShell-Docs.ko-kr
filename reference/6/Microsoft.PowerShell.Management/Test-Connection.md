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
# <span data-ttu-id="8b064-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="8b064-103">Test-Connection</span></span>

## <span data-ttu-id="8b064-104">개요</span><span class="sxs-lookup"><span data-stu-id="8b064-104">SYNOPSIS</span></span>
<span data-ttu-id="8b064-105">하나 이상의 컴퓨터에 ICMP 에코 요청 패킷 또는 ping을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="8b064-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b064-106">SYNTAX</span></span>

### <span data-ttu-id="8b064-107">수 (기본값)</span><span class="sxs-lookup"><span data-stu-id="8b064-107">PingCount (Default)</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8b064-108">계속</span><span class="sxs-lookup"><span data-stu-id="8b064-108">PingContinues</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8b064-109">DetectionOfMTUSize</span><span class="sxs-lookup"><span data-stu-id="8b064-109">DetectionOfMTUSize</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8b064-110">경로 추적</span><span class="sxs-lookup"><span data-stu-id="8b064-110">TraceRoute</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8b064-111">ConnectionByTCPPort</span><span class="sxs-lookup"><span data-stu-id="8b064-111">ConnectionByTCPPort</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="8b064-112">설명</span><span class="sxs-lookup"><span data-stu-id="8b064-112">DESCRIPTION</span></span>

<span data-ttu-id="8b064-113">`Test-Connection`Cmdlet은 ICMP (Internet Control Message Protocol) 에코 요청 패킷 또는 ping을 하나 이상의 원격 컴퓨터로 보내고 에코 응답을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="8b064-114">이 cmdlet을 사용 하 여 IP 네트워크를 통해 특정 컴퓨터에 연결할 수 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="8b064-115">의 매개 변수를 사용 `Test-Connection` 하 여 송신 및 수신 컴퓨터를 모두 지정 하 고, 명령을 백그라운드 작업으로 실행 하 고, 제한 시간 및 ping 수를 설정 하 고, 연결 및 인증을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="8b064-116">친숙 한 **ping** 명령과 달리은 `Test-Connection` PowerShell에서 조사할 수 있는 **Testconnectioncommand +을 보고** 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingReport** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="8b064-117">**Quiet** 매개 변수는 **테스트 된 각** 연결에 대해 system.string 개체에서 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="8b064-118">여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="8b064-119">예제</span><span class="sxs-lookup"><span data-stu-id="8b064-119">EXAMPLES</span></span>

### <span data-ttu-id="8b064-120">예제 1: 원격 컴퓨터에 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="8b064-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="8b064-121">이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 echo request 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="8b064-122">`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="8b064-123">**IPv4** 매개 변수는 테스트에 대 한 프로토콜을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="8b064-124">**Testconnectioncommand + a report** 개체가 **성공** 스트림으로 전송 되는 동안 ping 출력이 **정보** 스트림으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-124">The ping output is sent to the **Information** stream while the **TestConnectionCommand+PingReport** object sent to the **Success** stream.</span></span> <span data-ttu-id="8b064-125">출력 스트림에 대 한 자세한 내용은 [about_Redirection](../microsoft.powershell.core/about/about_redirection.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8b064-125">For more information about the output streams, see [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).</span></span>

### <span data-ttu-id="8b064-126">예 2: 여러 컴퓨터에 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="8b064-126">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="8b064-127">이 예제에서는 로컬 컴퓨터에서 여러 원격 컴퓨터로 ping을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-127">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="8b064-128">예 3: 여러 컴퓨터에서 컴퓨터로 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="8b064-128">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="8b064-129">이 예제에서는 여러 원본 컴퓨터의 ping을 단일 원격 컴퓨터 (Server01)로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-129">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

<span data-ttu-id="8b064-130">이 명령 형식을 사용하여 여러 지점으로부터의 연결 지연을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-130">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="8b064-131">예제 4: 매개 변수를 사용 하 여 테스트 명령 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="8b064-131">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="8b064-132">이 예제에서는의 매개 변수를 사용 하 여 `Test-Connection` 명령을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-132">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="8b064-133">로컬 컴퓨터에서 원격 컴퓨터로 ping 테스트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-133">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="8b064-134">`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-134">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="8b064-135">**Count** 매개 변수는 2 초 간격으로 Server01 컴퓨터로 전송 되는 세 개의 **ping을 지정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-135">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="8b064-136">홉 수가 연장 되거나 트래픽이 많은 네트워크 조건으로 인해 ping 응답이 평소 보다 오래 걸릴 것으로 예상 되는 경우 이러한 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-136">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="8b064-137">예 5: 백그라운드 작업으로 테스트 실행</span><span class="sxs-lookup"><span data-stu-id="8b064-137">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="8b064-138">이 예제에서는 `Test-Connection` 명령을 PowerShell 백그라운드 작업으로 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-138">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

<span data-ttu-id="8b064-139">이 `Start-Job` 명령은 cmdlet을 사용 하 여 `Test-Connection` 기업에서 많은 컴퓨터를 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-139">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="8b064-140">**TargetName** 매개 변수 값은 `Get-Content` 파일에서 컴퓨터 이름 목록을 읽는 명령입니다 `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="8b064-140">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="8b064-141">이 명령은 cmdlet을 사용 하 여 `Start-Job` 명령을 백그라운드 작업으로 실행 하 고 해당 작업을 `$job` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-141">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="8b064-142">`if`명령은 작업이 아직 실행 되 고 있지 않은지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-142">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="8b064-143">작업이 실행 되 고 있지 않으면 `Receive-Job` 결과를 가져와서 `$Results` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-143">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="8b064-144">예 6: 연결 테스트에 성공 하는 경우에만 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="8b064-144">Example 6: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="8b064-145">이 예에서는 컴퓨터로 전송 된 ping 중 하나 이상이 성공한 경우에만 Server01 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-145">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="8b064-146">이 `if` 명령은 cmdlet을 사용 하 여 `Test-Connection` Server01 컴퓨터를 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-146">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="8b064-147">이 명령은 **Testconnectioncommand +** 를 사용 하는 대신 **부울** 값을 반환 하는 **Quiet** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-147">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **TestConnectionCommand+PingReport** object.</span></span>

<span data-ttu-id="8b064-148">`$True`4 개의 ping 중 하나라도 성공한 경우이 값은입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-148">The value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="8b064-149">Ping이 실패 한 경우 값은 `$False` 입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-149">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="8b064-150">명령에서 값을 반환 하는 경우이 `Test-Connection` `$True` 명령은 cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-150">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

### <span data-ttu-id="8b064-151">예 7: 경로 추적 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="8b064-151">Example 7: Use the Traceroute parameter</span></span>

<span data-ttu-id="8b064-152">PowerShell 6.0부터 **경로 추적** 매개 변수는 로컬 컴퓨터와 지정한 원격 대상 간의 경로를 **TargetName** 매개 변수로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-152">Beginning in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="8b064-153">이 `Test-Connection` 명령은 **경로 추적** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-153">The `Test-Connection` command uses the **Traceroute** parameter.</span></span> <span data-ttu-id="8b064-154">개체인 결과는 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` cmdlet으로 파이프 됩니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="8b064-154">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objects, are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="8b064-155">`ForEach-Object` 포함 된 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` 개체와 후속 개체의 구조적 출력을 만듭니다 `[System.Net.NetworkInformation.PingReply]` .</span><span class="sxs-lookup"><span data-stu-id="8b064-155">`ForEach-Object` creates a structured output of the contained `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objects and subsequent `[System.Net.NetworkInformation.PingReply]` objects.</span></span>

## <span data-ttu-id="8b064-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b064-156">PARAMETERS</span></span>

### <span data-ttu-id="8b064-157">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="8b064-157">-BufferSize</span></span>

<span data-ttu-id="8b064-158">이 명령과 함께 보낸 버퍼의 크기(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-158">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="8b064-159">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-159">The default value is 32.</span></span>

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

### <span data-ttu-id="8b064-160">-개수</span><span class="sxs-lookup"><span data-stu-id="8b064-160">-Count</span></span>

<span data-ttu-id="8b064-161">보낼 에코 요청의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-161">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="8b064-162">기본값은 4입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-162">The default value is 4.</span></span>

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

### <span data-ttu-id="8b064-163">-Delay</span><span class="sxs-lookup"><span data-stu-id="8b064-163">-Delay</span></span>

<span data-ttu-id="8b064-164">Ping 간격을 초 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-164">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="8b064-165">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="8b064-165">-DontFragment</span></span>

<span data-ttu-id="8b064-166">이 매개 변수는 IP 헤더에서 **Don't Fragment** 플래그를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-166">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="8b064-167">이 매개 변수를 **BufferSize** 매개 변수와 함께 사용 하 여 경로 MTU 크기를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-167">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="8b064-168">경로 MTU에 대 한 자세한 내용은 위키백과의 [경로 Mtu 검색](https://wikipedia.org/wiki/Path_MTU_Discovery) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8b064-168">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="8b064-169">-IPv4</span><span class="sxs-lookup"><span data-stu-id="8b064-169">-IPv4</span></span>

<span data-ttu-id="8b064-170">Cmdlet이 테스트에 대 한 IPv4 프로토콜을 사용 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-170">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="8b064-171">-IPv6</span><span class="sxs-lookup"><span data-stu-id="8b064-171">-IPv6</span></span>

<span data-ttu-id="8b064-172">Cmdlet에서 테스트에 IPv6 프로토콜을 강제로 사용 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-172">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="8b064-173">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="8b064-173">-MaxHops</span></span>

<span data-ttu-id="8b064-174">ICMP 요청 메시지를 보낼 수 있는 최대 홉 수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-174">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="8b064-175">기본값은 운영 체제에 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-175">The default value is controlled by the operating system.</span></span> <span data-ttu-id="8b064-176">Windows 10의 기본값은 128 홉입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-176">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="8b064-177">-Ping</span><span class="sxs-lookup"><span data-stu-id="8b064-177">-Ping</span></span>

<span data-ttu-id="8b064-178">Cmdlet이 기본 작업 인 ping 테스트를 수행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-178">Causes the cmdlet to do a ping test, which is the default action.</span></span>

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

### <span data-ttu-id="8b064-179">-Quiet</span><span class="sxs-lookup"><span data-stu-id="8b064-179">-Quiet</span></span>

<span data-ttu-id="8b064-180">**Quiet** 매개 변수는 **System.string 개체에서** **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-180">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="8b064-181">이 매개 변수를 사용 하면 모든 오류가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-181">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="8b064-182">테스트 된 각 연결은 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-182">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="8b064-183">**TargetName** 매개 변수가 여러 컴퓨터를 지정 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-183">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="8b064-184">Ping **any** 이 성공 하면 `$True` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-184">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="8b064-185">**모든** ping이 실패 하면 `$False` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-185">If **all** pings fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="8b064-186">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="8b064-186">-ResolveDestination</span></span>

<span data-ttu-id="8b064-187">Cmdlet이 대상의 DNS 이름을 확인 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-187">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span>

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

### <span data-ttu-id="8b064-188">-Source</span><span class="sxs-lookup"><span data-stu-id="8b064-188">-Source</span></span>

<span data-ttu-id="8b064-189">Ping이 시작되는 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-189">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="8b064-190">쉼표로 구분된 컴퓨터 이름의 목록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-190">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="8b064-191">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-191">The default is the local computer.</span></span>

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

### <span data-ttu-id="8b064-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="8b064-192">-TargetName</span></span>

<span data-ttu-id="8b064-193">테스트할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-193">Specifies the computers to test.</span></span> <span data-ttu-id="8b064-194">컴퓨터 이름을 입력하거나 IP 주소를 IPv4 또는 IPv6 형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="8b064-195">와일드 카드 문자는 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-195">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="8b064-196">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-196">This parameter is required.</span></span> <span data-ttu-id="8b064-197">**ComputerName** 은이 매개 변수에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-197">**ComputerName** is an alias for this parameter.</span></span>

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

### <span data-ttu-id="8b064-198">-TCPPort</span><span class="sxs-lookup"><span data-stu-id="8b064-198">-TCPPort</span></span>

<span data-ttu-id="8b064-199">TCP 연결 테스트에 사용할 대상의 TCP 포트 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-199">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="8b064-200">이 cmdlet은 대상의 지정 된 포트에 대 한 TCP 연결을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-200">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

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

### <span data-ttu-id="8b064-201">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="8b064-201">-TimeoutSeconds</span></span>

<span data-ttu-id="8b064-202">테스트에 대 한 시간 제한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-202">Sets the timeout value for the test.</span></span> <span data-ttu-id="8b064-203">제한 시간이 만료 되기 전에 응답이 수신 되지 않으면 테스트가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-203">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="8b064-204">기본값은 5초입니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-204">The default is five seconds.</span></span>

<span data-ttu-id="8b064-205">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-205">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="8b064-206">-경로 추적</span><span class="sxs-lookup"><span data-stu-id="8b064-206">-Traceroute</span></span>

<span data-ttu-id="8b064-207">Cmdlet이 경로 추적 테스트를 수행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-207">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="8b064-208">이 매개 변수를 사용 하는 경우 cmdlet은 개체를 반환 합니다 `TestConnectionCommand+TraceRouteResult` .</span><span class="sxs-lookup"><span data-stu-id="8b064-208">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceRouteResult` object.</span></span>

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

### <span data-ttu-id="8b064-209">-계속</span><span class="sxs-lookup"><span data-stu-id="8b064-209">-Continues</span></span>

<span data-ttu-id="8b064-210">Cmdlet이 ping 요청을 계속 해 서 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-210">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="8b064-211">이 매개 변수는 **Count** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-211">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="8b064-212">-MTUSizeDetect</span><span class="sxs-lookup"><span data-stu-id="8b064-212">-MTUSizeDetect</span></span>

<span data-ttu-id="8b064-213">이 매개 변수는 경로 MTU 크기를 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-213">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="8b064-214">이 cmdlet은 대상에 대 한 경로 MTU 크기를 포함 하는 트 대 여 **회신 # MTUSize** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-214">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="8b064-215">경로 MTU에 대 한 자세한 내용은 위키백과의 [경로 Mtu 검색](https://wikipedia.org/wiki/Path_MTU_Discovery) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8b064-215">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="8b064-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b064-216">CommonParameters</span></span>

<span data-ttu-id="8b064-217">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b064-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b064-218">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8b064-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b064-219">입력</span><span class="sxs-lookup"><span data-stu-id="8b064-219">INPUTS</span></span>

### <span data-ttu-id="8b064-220">없음</span><span class="sxs-lookup"><span data-stu-id="8b064-220">None</span></span>

<span data-ttu-id="8b064-221">이 cmdlet에는 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-221">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8b064-222">출력</span><span class="sxs-lookup"><span data-stu-id="8b064-222">OUTPUTS</span></span>

### <span data-ttu-id="8b064-223">Testconnectioncommand + TraceRouteResult report, testconnectioncommand +, Boolean, anreply # mtusing</span><span class="sxs-lookup"><span data-stu-id="8b064-223">TestConnectionCommand+PingReport, TestConnectionCommand+TraceRouteResult, Boolean, PingReply#MTUSize</span></span>

<span data-ttu-id="8b064-224">**Quiet** 매개 변수를 지정 하면 **부울** 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-224">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="8b064-225">여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-225">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="8b064-226">그렇지 않으면 `Test-Connection` 각 ping에 대 한 **Testconnectioncommand + a report** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b064-226">Otherwise, `Test-Connection` returns a **TestConnectionCommand+PingReport** object for each ping.</span></span>

## <span data-ttu-id="8b064-227">참고</span><span class="sxs-lookup"><span data-stu-id="8b064-227">NOTES</span></span>

## <span data-ttu-id="8b064-228">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8b064-228">RELATED LINKS</span></span>

[<span data-ttu-id="8b064-229">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="8b064-229">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="8b064-230">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="8b064-230">Stop-Computer</span></span>](Stop-Computer.md)
