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
# <span data-ttu-id="50a54-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="50a54-103">Test-Connection</span></span>

## <span data-ttu-id="50a54-104">개요</span><span class="sxs-lookup"><span data-stu-id="50a54-104">SYNOPSIS</span></span>
<span data-ttu-id="50a54-105">하나 이상의 컴퓨터에 ICMP 에코 요청 패킷 또는 ping을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="50a54-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="50a54-106">SYNTAX</span></span>

### <span data-ttu-id="50a54-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="50a54-107">Default (Default)</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="50a54-108">원본</span><span class="sxs-lookup"><span data-stu-id="50a54-108">Source</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="50a54-109">Quiet</span><span class="sxs-lookup"><span data-stu-id="50a54-109">Quiet</span></span>

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## <span data-ttu-id="50a54-110">설명</span><span class="sxs-lookup"><span data-stu-id="50a54-110">DESCRIPTION</span></span>

<span data-ttu-id="50a54-111">`Test-Connection`Cmdlet은 ICMP (Internet Control Message Protocol) 에코 요청 패킷 또는 ping을 하나 이상의 원격 컴퓨터로 보내고 에코 응답을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-111">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="50a54-112">이 cmdlet을 사용 하 여 IP 네트워크를 통해 특정 컴퓨터에 연결할 수 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-112">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="50a54-113">의 매개 변수를 사용 `Test-Connection` 하 여 송신 및 수신 컴퓨터를 모두 지정 하 고, 명령을 백그라운드 작업으로 실행 하 고, 제한 시간 및 ping 수를 설정 하 고, 연결 및 인증을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-113">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="50a54-114">친숙 한 **ping** 명령과 달리은 `Test-Connection` PowerShell에서 조사할 수 있는 **Win32_PingStatus** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-114">Unlike the familiar **ping** command, `Test-Connection` returns a **Win32_PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="50a54-115">**Quiet** 매개 변수는 **테스트 된 각** 연결에 대해 system.string 개체에서 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-115">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="50a54-116">여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-116">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="50a54-117">예제</span><span class="sxs-lookup"><span data-stu-id="50a54-117">EXAMPLES</span></span>

### <span data-ttu-id="50a54-118">예제 1: 원격 컴퓨터에 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="50a54-118">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="50a54-119">이 예제에서는 로컬 컴퓨터에서 Server01 컴퓨터로 echo request 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-119">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="50a54-120">`Test-Connection`**ComputerName** 매개 변수를 사용 하 여 Server01 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-120">`Test-Connection` uses the **ComputerName** parameter to specify the Server01 computer.</span></span>

### <span data-ttu-id="50a54-121">예 2: 여러 컴퓨터에 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="50a54-121">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="50a54-122">이 예제에서는 로컬 컴퓨터에서 여러 원격 컴퓨터로 ping을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-122">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### <span data-ttu-id="50a54-123">예 3: 여러 컴퓨터에서 컴퓨터로 에코 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="50a54-123">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="50a54-124">이 예제에서는 여러 원본 컴퓨터의 ping을 단일 원격 컴퓨터 (Server01)로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-124">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="50a54-125">`Test-Connection`**Credential** 매개 변수를 사용 하 여 원본 컴퓨터에서 ping 요청을 보낼 수 있는 권한이 있는 사용자의 자격 증명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-125">`Test-Connection` uses the **Credential** parameter to specify the credentials of a user who has permission to send a ping request from the source computers.</span></span> <span data-ttu-id="50a54-126">이 명령 형식을 사용하여 여러 지점으로부터의 연결 지연을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-126">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="50a54-127">예제 4: 매개 변수를 사용 하 여 테스트 명령 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="50a54-127">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="50a54-128">이 예제에서는의 매개 변수를 사용 하 여 `Test-Connection` 명령을 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="50a54-129">로컬 컴퓨터에서 원격 컴퓨터로 ping 테스트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

<span data-ttu-id="50a54-130">`Test-Connection`**ComputerName** 매개 변수를 사용 하 여 Server01를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-130">`Test-Connection` uses the **ComputerName** parameter to specify Server01.</span></span> <span data-ttu-id="50a54-131">**Count** 매개 변수는 2 초 간격으로 Server01 컴퓨터로 전송 되는 세 개의 **ping을 지정** 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="50a54-132">홉 수가 연장 되거나 트래픽이 많은 네트워크 조건으로 인해 ping 응답이 평소 보다 오래 걸릴 것으로 예상 되는 경우 이러한 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="50a54-133">예 5: 백그라운드 작업으로 테스트 실행</span><span class="sxs-lookup"><span data-stu-id="50a54-133">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="50a54-134">이 예제에서는 `Test-Connection` 명령을 PowerShell 백그라운드 작업으로 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

<span data-ttu-id="50a54-135">`Test-Connection`명령은 기업에서 많은 컴퓨터를 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-135">The `Test-Connection` command pings many computers in an enterprise.</span></span> <span data-ttu-id="50a54-136">**ComputerName** 매개 변수 값은 `Get-Content` 에서 컴퓨터 이름 목록을 읽는 명령입니다 `Servers.txt file` .</span><span class="sxs-lookup"><span data-stu-id="50a54-136">The value of the **ComputerName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt file`.</span></span> <span data-ttu-id="50a54-137">이 명령은 **AsJob** 매개 변수를 사용 하 여 명령을 백그라운드 작업으로 실행 하 고 해당 작업을 변수에 저장 `$job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-137">The command uses the **AsJob** parameter to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="50a54-138">`if`명령은 작업이 아직 실행 되 고 있지 않은지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-138">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="50a54-139">작업이 실행 되 고 있지 않으면 `Receive-Job` 결과를 가져와서 `$Results` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-139">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="50a54-140">예 6: 자격 증명을 사용 하 여 원격 컴퓨터 Ping</span><span class="sxs-lookup"><span data-stu-id="50a54-140">Example 6: Ping a remote computer with credentials</span></span>

<span data-ttu-id="50a54-141">이 명령은 cmdlet을 사용 하 여 `Test-Connection` 원격 컴퓨터를 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-141">This command uses the `Test-Connection` cmdlet to ping a remote computer.</span></span>

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

<span data-ttu-id="50a54-142">이 명령은 **Credential** 매개 변수를 사용 하 여 원격 컴퓨터를 ping 할 수 있는 권한을 가진 사용자 계정을 지정 하 고 **가장** 매개 변수를 사용 하 여를 **식별** 하도록 가장 수준을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-142">The command uses the **Credential** parameter to specify a user account that has permission to ping the remote computer and the **Impersonation** parameter to change the impersonation level to **Identify** .</span></span>

### <span data-ttu-id="50a54-143">예 7: 연결 테스트에 성공 하는 경우에만 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="50a54-143">Example 7: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="50a54-144">이 예에서는 컴퓨터로 전송 된 ping 중 하나 이상이 성공한 경우에만 Server01 컴퓨터에서 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-144">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="50a54-145">이 `if` 명령은 cmdlet을 사용 하 여 `Test-Connection` Server01 컴퓨터를 ping 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-145">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="50a54-146">이 명령은 **Win32_PingStatus** 개체 대신 **부울** 값을 반환 하는 **Quiet** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-146">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **Win32_PingStatus** object.</span></span> <span data-ttu-id="50a54-147">이 값은 `$True` 4 개의 ping 중 하나라도 성공 하면이 고, 그렇지 않으면입니다 `$False` .</span><span class="sxs-lookup"><span data-stu-id="50a54-147">The value is `$True` if any of the four pings succeed and is, otherwise, `$False`.</span></span>

<span data-ttu-id="50a54-148">명령에서 값을 반환 하는 경우이 `Test-Connection` `$True` 명령은 cmdlet을 사용 하 여 `New-PSSession` **PSSession** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-148">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession** .</span></span>

## <span data-ttu-id="50a54-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="50a54-149">PARAMETERS</span></span>

### <span data-ttu-id="50a54-150">-AsJob</span><span class="sxs-lookup"><span data-stu-id="50a54-150">-AsJob</span></span>

<span data-ttu-id="50a54-151">이 cmdlet이 백그라운드 작업으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-151">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="50a54-152">이 매개 변수를 사용 하려면 원격을 사용 하도록 로컬 및 원격 컴퓨터를 구성 해야 하 고 Windows Vista 이상 버전의 Windows 운영 체제에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-152">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="50a54-153">자세한 내용은 [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50a54-153">For more information, see [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="50a54-154">**AsJob** 매개 변수를 지정 하면이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-154">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="50a54-155">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-155">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="50a54-156">AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-156">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="50a54-157">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="50a54-157">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="50a54-158">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50a54-158">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).</span></span>

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

### <span data-ttu-id="50a54-159">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="50a54-159">-BufferSize</span></span>

<span data-ttu-id="50a54-160">이 명령과 함께 보낸 버퍼의 크기(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-160">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="50a54-161">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-161">The default value is 32.</span></span>

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

### <span data-ttu-id="50a54-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="50a54-162">-ComputerName</span></span>

<span data-ttu-id="50a54-163">Ping할 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-163">Specifies the computers to ping.</span></span> <span data-ttu-id="50a54-164">컴퓨터 이름을 입력하거나 IP 주소를 IPv4 또는 IPv6 형식으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-164">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="50a54-165">와일드카드 문자는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-165">Wildcard characters are not permitted.</span></span> <span data-ttu-id="50a54-166">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-166">This parameter is required.</span></span>

<span data-ttu-id="50a54-167">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-167">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="50a54-168">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-168">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

> [!NOTE]
> <span data-ttu-id="50a54-169">**ComputerName** 매개 변수는 PowerShell 6.0 이상에서 **TargetName** 으로 이름이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-169">The **ComputerName** parameter is renamed to **TargetName** in PowerShell 6.0 and above.</span></span>

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

### <span data-ttu-id="50a54-170">-개수</span><span class="sxs-lookup"><span data-stu-id="50a54-170">-Count</span></span>

<span data-ttu-id="50a54-171">보낼 에코 요청의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-171">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="50a54-172">기본값은 4입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-172">The default value is 4.</span></span>

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

### <span data-ttu-id="50a54-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="50a54-173">-Credential</span></span>

<span data-ttu-id="50a54-174">원본 컴퓨터에서 ping 요청에서 보낼 수 있는 권한을 가진 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-174">Specifies a user account that has permission to send a ping request from the source computer.</span></span> <span data-ttu-id="50a54-175">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나, cmdlet의 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="50a54-175">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="50a54-176">**Credential** 매개 변수는 명령에 **Source** 매개 변수가 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-176">The **Credential** parameter is valid only when the **Source** parameter is used in the command.</span></span> <span data-ttu-id="50a54-177">자격 증명은 대상 컴퓨터에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-177">The credentials don't affect the destination computer.</span></span>

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

### <span data-ttu-id="50a54-178">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="50a54-178">-DcomAuthentication</span></span>

<span data-ttu-id="50a54-179">이 cmdlet이 WMI와 함께 사용 하는 인증 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-179">Specifies the authentication level that this cmdlet uses with WMI.</span></span>
<span data-ttu-id="50a54-180">`Test-Connection` WMI를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-180">`Test-Connection` uses WMI.</span></span>
<span data-ttu-id="50a54-181">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="50a54-182">**Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-182">**Default** .</span></span> <span data-ttu-id="50a54-183">Windows 인증</span><span class="sxs-lookup"><span data-stu-id="50a54-183">Windows Authentication</span></span>
- <span data-ttu-id="50a54-184">**없음** .</span><span class="sxs-lookup"><span data-stu-id="50a54-184">**None** .</span></span> <span data-ttu-id="50a54-185">COM 인증 없음</span><span class="sxs-lookup"><span data-stu-id="50a54-185">No COM authentication</span></span>
- <span data-ttu-id="50a54-186">**연결** .</span><span class="sxs-lookup"><span data-stu-id="50a54-186">**Connect** .</span></span> <span data-ttu-id="50a54-187">연결 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="50a54-187">Connect-level COM authentication</span></span>
- <span data-ttu-id="50a54-188">을 **호출** 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-188">**Call** .</span></span> <span data-ttu-id="50a54-189">호출 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="50a54-189">Call-level COM authentication</span></span>
- <span data-ttu-id="50a54-190">**패킷입니다** .</span><span class="sxs-lookup"><span data-stu-id="50a54-190">**Packet** .</span></span> <span data-ttu-id="50a54-191">패킷 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="50a54-191">Packet-level COM authentication</span></span>
- <span data-ttu-id="50a54-192">**PacketIntegrity** .</span><span class="sxs-lookup"><span data-stu-id="50a54-192">**PacketIntegrity** .</span></span> <span data-ttu-id="50a54-193">패킷 개인 정보 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="50a54-193">Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="50a54-194">**PacketPrivacy** .</span><span class="sxs-lookup"><span data-stu-id="50a54-194">**PacketPrivacy** .</span></span> <span data-ttu-id="50a54-195">패킷 개인 정보 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="50a54-195">Packet Privacy-level COM authentication</span></span>
- <span data-ttu-id="50a54-196">**변경 되지 않았습니다** .</span><span class="sxs-lookup"><span data-stu-id="50a54-196">**Unchanged** .</span></span> <span data-ttu-id="50a54-197">이전 명령과 동일</span><span class="sxs-lookup"><span data-stu-id="50a54-197">Same as the previous command</span></span>

<span data-ttu-id="50a54-198">기본값은 열거형 값이 **4** 인 **패킷입니다** .</span><span class="sxs-lookup"><span data-stu-id="50a54-198">The default value is **Packet** that has an enumerated value of **4** .</span></span> <span data-ttu-id="50a54-199">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationlevel](/dotnet/api/system.management.authenticationlevel) 열거를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50a54-199">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) enumeration.</span></span>

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

### <span data-ttu-id="50a54-200">-Delay</span><span class="sxs-lookup"><span data-stu-id="50a54-200">-Delay</span></span>

<span data-ttu-id="50a54-201">Ping 간격을 초 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-201">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="50a54-202">-가장</span><span class="sxs-lookup"><span data-stu-id="50a54-202">-Impersonation</span></span>

<span data-ttu-id="50a54-203">이 cmdlet이 WMI를 호출할 때 사용할 가장 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-203">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="50a54-204">`Test-Connection` WMI를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-204">`Test-Connection` uses WMI.</span></span>

<span data-ttu-id="50a54-205">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-205">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="50a54-206">**Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-206">**Default** .</span></span> <span data-ttu-id="50a54-207">기본 가장입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-207">Default impersonation.</span></span>
- <span data-ttu-id="50a54-208">**익명** .</span><span class="sxs-lookup"><span data-stu-id="50a54-208">**Anonymous** .</span></span> <span data-ttu-id="50a54-209">호출자의 ID를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-209">Hides the identity of the caller.</span></span>
- <span data-ttu-id="50a54-210">를 **식별** 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-210">**Identify** .</span></span> <span data-ttu-id="50a54-211">개체가 호출자의 자격 증명을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-211">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="50a54-212">**가장** .</span><span class="sxs-lookup"><span data-stu-id="50a54-212">**Impersonate** .</span></span> <span data-ttu-id="50a54-213">개체가 호출자의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-213">Allows objects to use the credentials of the caller.</span></span>

<span data-ttu-id="50a54-214">기본값은 **Impersonate** 입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-214">The default value is **Impersonate** .</span></span>

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

### <span data-ttu-id="50a54-215">-Protocol</span><span class="sxs-lookup"><span data-stu-id="50a54-215">-Protocol</span></span>

<span data-ttu-id="50a54-216">프로토콜을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-216">Specifies a protocol.</span></span> <span data-ttu-id="50a54-217">이 매개 변수에 허용 되는 값은 DCOM 및 WSMan입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-217">The acceptable values for this parameter are DCOM and WSMan.</span></span>

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

### <span data-ttu-id="50a54-218">-Quiet</span><span class="sxs-lookup"><span data-stu-id="50a54-218">-Quiet</span></span>

<span data-ttu-id="50a54-219">**Quiet** 매개 변수는 **System.string 개체에서** **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-219">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="50a54-220">이 매개 변수를 사용 하면 모든 오류가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-220">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="50a54-221">테스트 된 각 연결은 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-221">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="50a54-222">**ComputerName** 매개 변수가 여러 컴퓨터를 지정 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-222">If the **ComputerName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="50a54-223">Ping **any** 이 성공 하면 `$True` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-223">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="50a54-224">**모든** ping이 실패 하면 `$False` 이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-224">If **all** pings fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="50a54-225">-Source</span><span class="sxs-lookup"><span data-stu-id="50a54-225">-Source</span></span>

<span data-ttu-id="50a54-226">Ping이 시작되는 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-226">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="50a54-227">쉼표로 구분된 컴퓨터 이름의 목록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-227">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="50a54-228">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-228">The default is the local computer.</span></span>

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

### <span data-ttu-id="50a54-229">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="50a54-229">-ThrottleLimit</span></span>

<span data-ttu-id="50a54-230">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-230">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="50a54-231">이 매개 변수를 생략하거나 값 0을 입력하면 기본값 32가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-231">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="50a54-232">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-232">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="50a54-233">-TimeToLive</span><span class="sxs-lookup"><span data-stu-id="50a54-233">-TimeToLive</span></span>

<span data-ttu-id="50a54-234">패킷을 전달할 수 있는 최대 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-234">Specifies the maximum times a packet can be forwarded.</span></span> <span data-ttu-id="50a54-235">게이트웨이, 라우터 등의 모든 홉에 대해 **TimeToLive** 값이 1 씩 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-235">For every hop in gateways, routers etc. the **TimeToLive** value is decreased by one.</span></span> <span data-ttu-id="50a54-236">0에서 패킷이 삭제 되 고 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-236">At zero the packet is discarded and an error is returned.</span></span>
<span data-ttu-id="50a54-237">**Windows** 에서 기본값은 **128** 입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-237">In **Windows** , The default value is **128** .</span></span> <span data-ttu-id="50a54-238">**TimeToLive** 매개 변수의 별칭은 **TTL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-238">The alias of the **TimeToLive** parameter is **TTL** .</span></span>

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

### <span data-ttu-id="50a54-239">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="50a54-239">-WsmanAuthentication</span></span>

<span data-ttu-id="50a54-240">이 cmdlet이 WSMan 프로토콜을 사용 하는 경우 사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-240">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span>
<span data-ttu-id="50a54-241">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="50a54-242">Basic</span><span class="sxs-lookup"><span data-stu-id="50a54-242">Basic</span></span>
- <span data-ttu-id="50a54-243">CredSSP</span><span class="sxs-lookup"><span data-stu-id="50a54-243">CredSSP</span></span>
- <span data-ttu-id="50a54-244">기본값</span><span class="sxs-lookup"><span data-stu-id="50a54-244">Default</span></span>
- <span data-ttu-id="50a54-245">다이제스트</span><span class="sxs-lookup"><span data-stu-id="50a54-245">Digest</span></span>
- <span data-ttu-id="50a54-246">Kerberos</span><span class="sxs-lookup"><span data-stu-id="50a54-246">Kerberos</span></span>
- <span data-ttu-id="50a54-247">Negotiate</span><span class="sxs-lookup"><span data-stu-id="50a54-247">Negotiate.</span></span>

<span data-ttu-id="50a54-248">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-248">The default value is Default.</span></span>

<span data-ttu-id="50a54-249">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50a54-249">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).</span></span>

<span data-ttu-id="50a54-250">주의: 사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 경우와 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-250">Caution: Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="50a54-251">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-251">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="50a54-252">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-252">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="50a54-253">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="50a54-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="50a54-254">CommonParameters</span></span>

<span data-ttu-id="50a54-255">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="50a54-255">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="50a54-256">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50a54-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="50a54-257">입력</span><span class="sxs-lookup"><span data-stu-id="50a54-257">INPUTS</span></span>

### <span data-ttu-id="50a54-258">없음</span><span class="sxs-lookup"><span data-stu-id="50a54-258">None</span></span>

<span data-ttu-id="50a54-259">이 cmdlet에는 입력을 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-259">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="50a54-260">출력</span><span class="sxs-lookup"><span data-stu-id="50a54-260">OUTPUTS</span></span>

### <span data-ttu-id="50a54-261">Root\cimv2\ 개체 # Win32_PingStatus, system.web. Remorerere.</span><span class="sxs-lookup"><span data-stu-id="50a54-261">System.Management.ManagementObject#root\cimv2\Win32_PingStatus, System.Management.Automation.RemotingJob, System.Boolean</span></span>

<span data-ttu-id="50a54-262">**AsJob** 매개 변수를 지정 하는 경우이 cmdlet은 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-262">This cmdlet returns a job object, if you specify the **AsJob** parameter.</span></span>

<span data-ttu-id="50a54-263">**Quiet** 매개 변수를 지정 하면 **부울** 값이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-263">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="50a54-264">여러 연결을 테스트 하는 경우에는 **부울** 값의 배열이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-264">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="50a54-265">그렇지 않으면 `Test-Connection` 각 ping에 대 한 **Win32_PingStatus** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-265">Otherwise, `Test-Connection` returns a **Win32_PingStatus** object for each ping.</span></span>

## <span data-ttu-id="50a54-266">참고</span><span class="sxs-lookup"><span data-stu-id="50a54-266">NOTES</span></span>

<span data-ttu-id="50a54-267">이 cmdlet은 **Win32_PingStatus** 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-267">This cmdlet uses the **Win32_PingStatus** class.</span></span> <span data-ttu-id="50a54-268">명령은 `Get-WMIObject Win32_PingStatus` `Test-Connection` 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-268">A `Get-WMIObject Win32_PingStatus` command is equivalent to a `Test-Connection` command.</span></span>

<span data-ttu-id="50a54-269">**원본** 매개 변수 집합은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50a54-269">The **Source** parameter set was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="50a54-270">관련 링크</span><span class="sxs-lookup"><span data-stu-id="50a54-270">RELATED LINKS</span></span>

[<span data-ttu-id="50a54-271">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="50a54-271">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="50a54-272">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="50a54-272">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="50a54-273">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="50a54-273">Stop-Computer</span></span>](Stop-Computer.md)
