---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 6a03d5a644e3d4be515a93a702d0ef0aff23a8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212186"
---
# <span data-ttu-id="1fac5-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="1fac5-103">Test-Connection</span></span>

## <span data-ttu-id="1fac5-104">개요</span><span class="sxs-lookup"><span data-stu-id="1fac5-104">SYNOPSIS</span></span>
<span data-ttu-id="1fac5-105">하나 이상의 컴퓨터에 ICMP 에코 요청 패킷 또는 ping을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="1fac5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1fac5-106">SYNTAX</span></span>

### <span data-ttu-id="1fac5-107">DefaultPing (기본값)</span><span class="sxs-lookup"><span data-stu-id="1fac5-107">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="1fac5-108">반복 Ping</span><span class="sxs-lookup"><span data-stu-id="1fac5-108">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="1fac5-109">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="1fac5-109">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="1fac5-110">경로 추적</span><span class="sxs-lookup"><span data-stu-id="1fac5-110">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="1fac5-111">TcpPort</span><span class="sxs-lookup"><span data-stu-id="1fac5-111">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="1fac5-112">설명</span><span class="sxs-lookup"><span data-stu-id="1fac5-112">DESCRIPTION</span></span>

<span data-ttu-id="1fac5-113">`Test-Connection`Cmdlet은 ICMP (Internet Control Message Protocol) 에코 요청 패킷 또는 ping을 하나 이상의 원격 컴퓨터로 보내고 에코 응답을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="1fac5-114">이 cmdlet을 사용 하 여 IP 네트워크를 통해 특정 컴퓨터에 연결할 수 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="1fac5-115">의 매개 변수를 사용 `Test-Connection` 하 여 송신 및 수신 컴퓨터를 모두 지정 하 고, 명령을 백그라운드 작업으로 실행 하 고, 제한 시간 및 ping 수를 설정 하 고, 연결 및 인증을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="1fac5-116">친숙 한 **ping** 명령과 달리은 `Test-Connection` PowerShell에서 조사할 수 있는 **testconnectioncommand +** 가 나 상태 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="1fac5-117">**Quiet** 매개 변수는 **테스트 된 각** 연결에 대해 system.string 개체에서 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="1fac5-118">여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="1fac5-119">예제</span><span class="sxs-lookup"><span data-stu-id="1fac5-119">EXAMPLES</span></span>

### <span data-ttu-id="1fac5-120">예제 1: 원격 컴퓨터에 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="1fac5-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="1fac5-121">이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 echo request 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="1fac5-122">`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="1fac5-123">**IPv4** 매개 변수는 테스트에 대 한 프로토콜을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="1fac5-124">대상 컴퓨터에서 ping 응답 당 하나의 개체를 출력 스트림으로 전송 하는 일련의 **Testconnectioncommand +** ...</span><span class="sxs-lookup"><span data-stu-id="1fac5-124">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="1fac5-125">예 2: 여러 컴퓨터에 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="1fac5-125">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="1fac5-126">이 예제에서는 로컬 컴퓨터에서 여러 원격 컴퓨터로 ping을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-126">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="1fac5-127">예제 3: 매개 변수를 사용 하 여 테스트 명령 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="1fac5-127">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="1fac5-128">이 예제에서는의 매개 변수를 사용 하 여 `Test-Connection` 명령을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="1fac5-129">로컬 컴퓨터에서 원격 컴퓨터로 ping 테스트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="1fac5-130">`Test-Connection`**TargetName** 매개 변수를 사용 하 여 Server01를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-130">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="1fac5-131">**Count** 매개 변수는 2 초 간격으로 Server01 컴퓨터로 전송 되는 세 개의 **ping을 지정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="1fac5-132">홉 수가 연장 되거나 트래픽이 많은 네트워크 조건으로 인해 ping 응답이 평소 보다 오래 걸릴 것으로 예상 되는 경우 이러한 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="1fac5-133">예제 4: 백그라운드 작업으로 테스트 실행</span><span class="sxs-lookup"><span data-stu-id="1fac5-133">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="1fac5-134">이 예제에서는 `Test-Connection` 명령을 PowerShell 백그라운드 작업으로 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="1fac5-135">이 `Start-Job` 명령은 cmdlet을 사용 하 여 `Test-Connection` 기업에서 많은 컴퓨터를 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-135">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="1fac5-136">**TargetName** 매개 변수 값은 `Get-Content` 파일에서 컴퓨터 이름 목록을 읽는 명령입니다 `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="1fac5-136">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="1fac5-137">이 명령은 cmdlet을 사용 하 여 `Start-Job` 명령을 백그라운드 작업으로 실행 하 고 해당 작업을 `$job` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-137">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="1fac5-138">이 `Receive-Job` 명령은 `-Wait` 작업이 완료 될 때까지로 지시한 다음 결과를 가져와서 `$Results` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-138">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="1fac5-139">예 5: 연결 테스트에 성공 하는 경우에만 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="1fac5-139">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="1fac5-140">이 예에서는 컴퓨터로 전송 된 ping 중 하나 이상이 성공한 경우에만 Server01 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-140">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="1fac5-141">`Test-Connection`Cmdlet은 `Server01` **자동** 매개 변수를 제공 하 여 컴퓨터를 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-141">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="1fac5-142">결과 값은 `$True` 4 개의 ping 중 하나라도 성공한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-142">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="1fac5-143">Ping이 실패 한 경우 값은 `$False` 입니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-143">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="1fac5-144">명령에서 값을 반환 하는 경우이 `Test-Connection` `$True` 명령은 cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-144">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

### <span data-ttu-id="1fac5-145">예제 6: 경로 추적 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="1fac5-145">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="1fac5-146">PowerShell 6.0에 도입 된 **경로 추적** 매개 변수는 로컬 컴퓨터와 지정한 원격 대상 간의 경로를 **TargetName** 매개 변수로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-146">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="1fac5-147">`Test-Connection`명령은 **경로 추적** 매개 변수를 사용 하 여 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-147">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="1fac5-148">개체 인 결과는 `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` **성공** 출력 스트림으로 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-148">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="1fac5-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1fac5-149">PARAMETERS</span></span>

### <span data-ttu-id="1fac5-150">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="1fac5-150">-BufferSize</span></span>

<span data-ttu-id="1fac5-151">이 명령과 함께 보낸 버퍼의 크기(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-151">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="1fac5-152">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-152">The default value is 32.</span></span>

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

### <span data-ttu-id="1fac5-153">-반복</span><span class="sxs-lookup"><span data-stu-id="1fac5-153">-Repeat</span></span>

<span data-ttu-id="1fac5-154">Cmdlet이 ping 요청을 계속 해 서 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-154">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="1fac5-155">이 매개 변수는 **Count** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-155">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="1fac5-156">-개수</span><span class="sxs-lookup"><span data-stu-id="1fac5-156">-Count</span></span>

<span data-ttu-id="1fac5-157">보낼 에코 요청의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-157">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="1fac5-158">기본값은 4입니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-158">The default value is 4.</span></span>

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

### <span data-ttu-id="1fac5-159">-Delay</span><span class="sxs-lookup"><span data-stu-id="1fac5-159">-Delay</span></span>

<span data-ttu-id="1fac5-160">Ping 간격을 초 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-160">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="1fac5-161">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="1fac5-161">-DontFragment</span></span>

<span data-ttu-id="1fac5-162">이 매개 변수는 IP 헤더에서 **Don't Fragment** 플래그를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-162">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="1fac5-163">이 매개 변수를 **BufferSize** 매개 변수와 함께 사용 하 여 경로 MTU 크기를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-163">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="1fac5-164">경로 MTU에 대 한 자세한 내용은 위키백과의 [경로 Mtu 검색](https://wikipedia.org/wiki/Path_MTU_Discovery) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fac5-164">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="1fac5-165">-IPv4</span><span class="sxs-lookup"><span data-stu-id="1fac5-165">-IPv4</span></span>

<span data-ttu-id="1fac5-166">Cmdlet이 테스트에 대 한 IPv4 프로토콜을 사용 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-166">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="1fac5-167">-IPv6</span><span class="sxs-lookup"><span data-stu-id="1fac5-167">-IPv6</span></span>

<span data-ttu-id="1fac5-168">Cmdlet에서 테스트에 IPv6 프로토콜을 강제로 사용 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-168">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="1fac5-169">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="1fac5-169">-MaxHops</span></span>

<span data-ttu-id="1fac5-170">ICMP 요청 메시지를 보낼 수 있는 최대 홉 수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-170">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="1fac5-171">기본값은 운영 체제에 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-171">The default value is controlled by the operating system.</span></span> <span data-ttu-id="1fac5-172">Windows 10의 기본값은 128 홉입니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-172">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="1fac5-173">-Ping</span><span class="sxs-lookup"><span data-stu-id="1fac5-173">-Ping</span></span>

<span data-ttu-id="1fac5-174">Cmdlet이 ping 테스트를 수행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-174">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="1fac5-175">이는 cmdlet에 대 한 기본 모드입니다 `Test-Connection` .</span><span class="sxs-lookup"><span data-stu-id="1fac5-175">This is the default mode for the `Test-Connection` cmdlet.</span></span>

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

### <span data-ttu-id="1fac5-176">-Quiet</span><span class="sxs-lookup"><span data-stu-id="1fac5-176">-Quiet</span></span>

<span data-ttu-id="1fac5-177">**Quiet** 매개 변수는 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-177">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="1fac5-178">이 매개 변수를 사용 하면 모든 오류가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-178">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="1fac5-179">테스트 된 각 연결은 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-179">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="1fac5-180">**TargetName** 매개 변수가 여러 컴퓨터를 지정 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-180">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="1fac5-181">지정 된 대상에 대 **한 ping** 이 성공 하면 `$True` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-181">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="1fac5-182">지정 된 대상에 대 한 **모든** ping이 실패 하면 `$False` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-182">If **all** pings to a given target fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="1fac5-183">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="1fac5-183">-ResolveDestination</span></span>

<span data-ttu-id="1fac5-184">Cmdlet이 대상의 DNS 이름을 확인 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-184">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="1fac5-185">**경로 추적** 매개 변수와 함께 사용 하는 경우 모든 중간 호스트의 DNS 이름도 검색 됩니다 (가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="1fac5-185">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

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

### <span data-ttu-id="1fac5-186">-Source</span><span class="sxs-lookup"><span data-stu-id="1fac5-186">-Source</span></span>

<span data-ttu-id="1fac5-187">Ping이 시작되는 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-187">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="1fac5-188">쉼표로 구분된 컴퓨터 이름의 목록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-188">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="1fac5-189">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-189">The default is the local computer.</span></span>

<span data-ttu-id="1fac5-190">**참고:** 이 매개 변수는 PowerShell 버전 6 이상에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-190">**NOTE:** This parameter is not functional in PowerShell versions 6 and up.</span></span>
<span data-ttu-id="1fac5-191">이 매개 변수를 제공 해도 명령에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-191">Supplying this parameter will have no effect on the command.</span></span>

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

### <span data-ttu-id="1fac5-192">-TargetName</span><span class="sxs-lookup"><span data-stu-id="1fac5-192">-TargetName</span></span>

<span data-ttu-id="1fac5-193">테스트할 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-193">Specifies the computer(s) to test.</span></span> <span data-ttu-id="1fac5-194">컴퓨터 이름을 입력하거나 IP 주소를 IPv4 또는 IPv6 형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

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

### <span data-ttu-id="1fac5-195">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="1fac5-195">-TimeoutSeconds</span></span>

<span data-ttu-id="1fac5-196">테스트에 대 한 시간 제한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-196">Sets the timeout value for the test.</span></span> <span data-ttu-id="1fac5-197">제한 시간이 만료 되기 전에 응답이 수신 되지 않으면 테스트가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-197">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="1fac5-198">기본값은 5초입니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-198">The default is five seconds.</span></span>

<span data-ttu-id="1fac5-199">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-199">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="1fac5-200">-경로 추적</span><span class="sxs-lookup"><span data-stu-id="1fac5-200">-Traceroute</span></span>

<span data-ttu-id="1fac5-201">Cmdlet이 경로 추적 테스트를 수행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-201">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="1fac5-202">이 매개 변수를 사용 하는 경우 cmdlet은 개체를 반환 합니다 `TestConnectionCommand+TraceStatus` .</span><span class="sxs-lookup"><span data-stu-id="1fac5-202">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

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

### <span data-ttu-id="1fac5-203">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="1fac5-203">-MtuSize</span></span>

<span data-ttu-id="1fac5-204">이 매개 변수는 경로 MTU 크기를 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-204">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="1fac5-205">이 cmdlet은 대상에 대 한 경로 MTU 크기를 포함 하는 트 대 여 **회신 # MTUSize** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-205">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="1fac5-206">경로 MTU에 대 한 자세한 내용은 위키백과의 [경로 Mtu 검색](https://wikipedia.org/wiki/Path_MTU_Discovery) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fac5-206">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="1fac5-207">-TcpPort</span><span class="sxs-lookup"><span data-stu-id="1fac5-207">-TcpPort</span></span>

<span data-ttu-id="1fac5-208">TCP 연결 테스트에 사용할 대상의 TCP 포트 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-208">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="1fac5-209">이 cmdlet은 대상의 지정 된 포트에 대 한 TCP 연결을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-209">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="1fac5-210">연결을 설정할 수 있으면 `$True` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-210">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="1fac5-211">연결을 설정할 수 없는 경우이 `$False` 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-211">If a connection cannot be made, `$False` will be returned.</span></span>

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

### <span data-ttu-id="1fac5-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1fac5-212">CommonParameters</span></span>

<span data-ttu-id="1fac5-213">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1fac5-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1fac5-214">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1fac5-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1fac5-215">입력</span><span class="sxs-lookup"><span data-stu-id="1fac5-215">INPUTS</span></span>

### <span data-ttu-id="1fac5-216">없음</span><span class="sxs-lookup"><span data-stu-id="1fac5-216">None</span></span>

<span data-ttu-id="1fac5-217">이 cmdlet에는 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-217">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1fac5-218">출력</span><span class="sxs-lookup"><span data-stu-id="1fac5-218">OUTPUTS</span></span>

### <span data-ttu-id="1fac5-219">TestConnectionCommand + TraceStatus, TestConnectionCommand +, Boolean, TestConnectionCommand + PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="1fac5-219">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="1fac5-220">기본적으로는 `Test-Connection` 각 ping 회신에 대 한 **Testconnectioncommand +, 상태** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-220">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="1fac5-221">**경로 추적** 매개 변수를 지정 하는 경우 cmdlet은 경로를 따라 각 ping 응답에 대해 **testconnectioncommand + TraceStatus** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-221">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="1fac5-222">**Quiet** 또는 **TcpPort** 매개 변수를 지정 하면 **부울** 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-222">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="1fac5-223">여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fac5-223">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="1fac5-224">참고</span><span class="sxs-lookup"><span data-stu-id="1fac5-224">NOTES</span></span>

## <span data-ttu-id="1fac5-225">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1fac5-225">RELATED LINKS</span></span>

[<span data-ttu-id="1fac5-226">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="1fac5-226">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="1fac5-227">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="1fac5-227">Stop-Computer</span></span>](Stop-Computer.md)

