---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218265"
---
# <span data-ttu-id="bab36-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="bab36-103">Restart-Computer</span></span>

## <span data-ttu-id="bab36-104">개요</span><span class="sxs-lookup"><span data-stu-id="bab36-104">SYNOPSIS</span></span>
<span data-ttu-id="bab36-105">로컬 및 원격 컴퓨터에서 운영 체제를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="bab36-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bab36-106">SYNTAX</span></span>

### <span data-ttu-id="bab36-107">DefaultSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="bab36-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bab36-108">AsJobSet</span><span class="sxs-lookup"><span data-stu-id="bab36-108">AsJobSet</span></span>

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bab36-109">설명</span><span class="sxs-lookup"><span data-stu-id="bab36-109">DESCRIPTION</span></span>

<span data-ttu-id="bab36-110">`Restart-Computer`Cmdlet은 로컬 및 원격 컴퓨터에서 운영 체제를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-110">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="bab36-111">의 매개 변수를 사용 하 여 `Restart-Computer` 다시 시작 작업을 백그라운드 작업으로 실행 하 고, 인증 수준 및 대체 자격 증명을 지정 하 고, 동시에 실행 되는 작업을 제한 하 고, 강제로 즉시 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-111">You can use the parameters of `Restart-Computer` to run the restart operations as a background job, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="bab36-112">Windows PowerShell 3.0부터 다음 명령을 실행 하기 전에 다시 시작이 완료 될 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-112">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="bab36-113">대기 시간 제한 및 쿼리 간격을 지정 하 고, 다시 시작 된 컴퓨터에서 특정 서비스를 사용할 수 있을 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-113">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="bab36-114">이 기능을 사용 하면 `Restart-Computer` 스크립트 및 함수에서 효과적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-114">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

<span data-ttu-id="bab36-115">엔터프라이즈 방화벽과 같이 DCOM (Distributed Component Object Model) 호출이 차단 된 경우 WSMan (WS-Management) 프로토콜을 사용 하 여 컴퓨터를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-115">You can use the WS-Management (WSMan) protocol to restart the computer, in case Distributed Component Object Model (DCOM) calls are blocked, such as by an enterprise firewall.</span></span> <span data-ttu-id="bab36-116">자세한 내용은 [WS-Management 프로토콜](/windows/desktop/WinRM/ws-management-protocol)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bab36-116">For more information, see [WS-Management Protocol](/windows/desktop/WinRM/ws-management-protocol).</span></span>

<span data-ttu-id="bab36-117">이 cmdlet은 명령에 **AsJob** 매개 변수를 사용하는 경우에만 Windows PowerShell 원격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-117">This cmdlet requires Windows PowerShell remoting only when you use the **AsJob** parameter in a command.</span></span>

## <span data-ttu-id="bab36-118">예제</span><span class="sxs-lookup"><span data-stu-id="bab36-118">EXAMPLES</span></span>

### <span data-ttu-id="bab36-119">예 1: 로컬 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="bab36-119">Example 1: Restart the local computer</span></span>

<span data-ttu-id="bab36-120">`Restart-Computer` 로컬 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-120">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="bab36-121">예 2: 여러 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="bab36-121">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="bab36-122">`Restart-Computer` 원격 컴퓨터와 로컬 컴퓨터를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-122">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="bab36-123">**ComputerName** 매개 변수는 컴퓨터 이름 배열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-123">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="bab36-124">예 3: 백그라운드 작업으로 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="bab36-124">Example 3: Restart computers as a background job</span></span>

<span data-ttu-id="bab36-125">이 명령은 `Restart-Computer` 두 원격 컴퓨터에서 명령을 백그라운드 작업으로 실행 한 다음 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-125">These commands run a `Restart-Computer` command as a background job on two remote computers, and then get the results.</span></span>

<span data-ttu-id="bab36-126">**AsJob** 은 로컬 컴퓨터에 작업을 만들고 결과를 로컬 컴퓨터에 자동으로 반환 하기 때문에 로컬 명령으로를 실행할 수 있습니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="bab36-126">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

<span data-ttu-id="bab36-127">`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 **Server01** 및 **Server02** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-127">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** and **Server02**.</span></span> <span data-ttu-id="bab36-128">**AsJob** 매개 변수는 명령을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-128">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="bab36-129">작업 개체는 변수에 저장 됩니다 `$Job` .</span><span class="sxs-lookup"><span data-stu-id="bab36-129">The job object is stored in the `$Job` variable.</span></span> <span data-ttu-id="bab36-130">`$Job` 는 결과를 가져오는 cmdlet에 파이프라인으로 전송 됩니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="bab36-130">`$Job` is sent down the pipeline to the `Receive-Job` cmdlet that gets the results.</span></span>

### <span data-ttu-id="bab36-131">예제 4: 원격 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="bab36-131">Example 4: Restart a remote computer</span></span>

<span data-ttu-id="bab36-132">`Restart-Computer` 사용자 지정 가장 및 인증 설정을 사용 하 여 원격 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-132">`Restart-Computer` restarts a remote computer with customized impersonation and authentication settings.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="bab36-133">`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 **Server01** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-133">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="bab36-134">**가장** 매개 변수는 요청자의 id를 숨기도록 익명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-134">The **Impersonation** parameter specifies Anonymous to hide the requester's identity.</span></span> <span data-ttu-id="bab36-135">**DcomAuthentication** 매개 변수는 연결의 인증 수준으로 PacketIntegrity를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-135">The **DcomAuthentication** parameter specifies PacketIntegrity as the connection's authentication level.</span></span>

### <span data-ttu-id="bab36-136">예 5: 텍스트 파일에 나열 된 컴퓨터를 강제로 다시 시작</span><span class="sxs-lookup"><span data-stu-id="bab36-136">Example 5: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="bab36-137">이 예제에서는 파일에 나열 된 컴퓨터를 강제로 즉시 다시 시작 `Domain01.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-137">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="bab36-138">텍스트 파일의 컴퓨터 이름은 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-138">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="bab36-139">**Force** 매개 변수는 강제로 즉시 다시 시작 되 고 **ThrottleLimit** 매개 변수는 동시 연결 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-139">The **Force** parameter forces an immediate restart and the **ThrottleLimit** parameter limits the number of concurrent connections.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

<span data-ttu-id="bab36-140">`Get-Content` 는 **Path** 매개 변수를 사용 하 여 텍스트 파일에서 컴퓨터 이름 목록을 가져올 **Domain01.txt** 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-140">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="bab36-141">컴퓨터 이름은 변수에 저장 됩니다 `$Names` .</span><span class="sxs-lookup"><span data-stu-id="bab36-141">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="bab36-142">`Get-Credential` 사용자 이름과 암호를 묻는 메시지를 표시 하 고 해당 값을 변수에 저장 `$Creds` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-142">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="bab36-143">`Restart-Computer` 는 해당 변수와 함께 **ComputerName** 및 **Credential** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-143">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="bab36-144">**Force** 매개 변수를 설정 하면 각 컴퓨터를 즉시 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-144">The **Force** parameter causes an immediate restart of each computer.</span></span> <span data-ttu-id="bab36-145">**ThrottleLimit** 매개 변수는 명령을 10 개의 동시 연결로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-145">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span>

### <span data-ttu-id="bab36-146">예 6: 원격 컴퓨터를 다시 시작 하 고 PowerShell 대기</span><span class="sxs-lookup"><span data-stu-id="bab36-146">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="bab36-147">`Restart-Computer` 는 원격 컴퓨터를 다시 시작 하 고, 계속 하기 전에 다시 시작 된 컴퓨터에서 PowerShell을 사용할 수 있게 될 때까지 최대 5 분 (300 초) 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-147">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="bab36-148">`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 **Server01** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-148">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="bab36-149">**Wait** 매개 변수는 다시 시작이 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-149">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="bab36-150">**의** 은 PowerShell에서 원격 컴퓨터의 명령을 실행할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-150">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="bab36-151">**Timeout** 매개 변수는 5 분 대기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-151">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="bab36-152">**Delay** 매개 변수는 2 초 마다 원격 컴퓨터를 쿼리하여 다시 시작할지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-152">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="bab36-153">예 7: WSMan 프로토콜을 사용 하 여 컴퓨터 다시 시작</span><span class="sxs-lookup"><span data-stu-id="bab36-153">Example 7: Restart a computer by using the WSMan Protocol</span></span>

<span data-ttu-id="bab36-154">`Restart-Computer` 기본 DCOM 대신 WSMan 프로토콜을 사용 하 여 원격 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-154">`Restart-Computer` restarts the remote computer by using the WSMan protocol instead of the default, DCOM.</span></span> <span data-ttu-id="bab36-155">Kerberos 인증 현재 사용자에 게 원격 컴퓨터를 다시 시작할 수 있는 권한이 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-155">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span>

<span data-ttu-id="bab36-156">이러한 설정은 DCOM이 차단 되어 DCOM 기반 다시 시작이 실패 하는 기업을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-156">These settings are designed for enterprises in which DCOM-based restarts fail because DCOM is blocked.</span></span> <span data-ttu-id="bab36-157">예를 들어 방화벽을 사용할 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-157">For example, by a firewall.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

<span data-ttu-id="bab36-158">`Restart-Computer`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터 **Server01** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-158">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01**.</span></span>
<span data-ttu-id="bab36-159">**프로토콜** 매개 변수는 WSMan 프로토콜을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-159">The **Protocol** parameter specifies to use the WSMan protocol.</span></span> <span data-ttu-id="bab36-160">**WsmanAuthentication** 매개 변수는 인증 방법을 **Kerberos** 로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-160">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos**.</span></span>

## <span data-ttu-id="bab36-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bab36-161">PARAMETERS</span></span>

### <span data-ttu-id="bab36-162">-AsJob</span><span class="sxs-lookup"><span data-stu-id="bab36-162">-AsJob</span></span>

<span data-ttu-id="bab36-163">가 `Restart-Computer` 백그라운드 작업으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-163">Indicates that `Restart-Computer` runs as a background job.</span></span>

<span data-ttu-id="bab36-164">이 매개 변수를 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-164">To use this parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="bab36-165">Windows Vista 이상 버전의 Windows 운영 체제에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-165">On Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as Administrator** option.</span></span> <span data-ttu-id="bab36-166">자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bab36-166">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="bab36-167">**AsJob** 매개 변수를 지정 하면이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-167">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="bab36-168">작업을 마치는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-168">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="bab36-169">AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-169">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="bab36-170">작업을 관리하려면 **Job** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-170">To manage the job, use the **Job** cmdlets.</span></span> <span data-ttu-id="bab36-171">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="bab36-171">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="bab36-172">Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bab36-172">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bab36-173">-ComputerName</span></span>

<span data-ttu-id="bab36-174">컴퓨터 이름 하나 또는 쉼표로 구분 된 컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-174">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="bab36-175">`Restart-Computer` 파이프라인 또는 변수의 **ComputerName** 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-175">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="bab36-176">원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="bab36-176">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="bab36-177">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 또는 localhost를 입력 합니다 `.` .</span><span class="sxs-lookup"><span data-stu-id="bab36-177">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="bab36-178">이 매개 변수는 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-178">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="bab36-179">컴퓨터에서 원격 명령을 실행 하도록 구성 되지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-179">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="bab36-180">**ComputerName** 매개 변수를 지정 하지 않으면에서 `Restart-Computer` 로컬 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-180">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="bab36-181">-Credential</span></span>

<span data-ttu-id="bab36-182">이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-182">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="bab36-183">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-183">The default is the current user.</span></span>

<span data-ttu-id="bab36-184">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="bab36-184">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="bab36-185">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-185">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="bab36-186">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-186">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="bab36-187">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="bab36-187">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-188">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="bab36-188">-DcomAuthentication</span></span>

<span data-ttu-id="bab36-189">WMI 연결에 사용 되는 인증 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-189">Specifies the authentication level that is used for the WMI connection.</span></span> <span data-ttu-id="bab36-190">`Restart-Computer` WMI를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-190">`Restart-Computer` uses WMI.</span></span>

<span data-ttu-id="bab36-191">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-191">Valid values are:</span></span>

- <span data-ttu-id="bab36-192">**호출** : 호출 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="bab36-192">**Call** :            Call-level COM authentication</span></span>
- <span data-ttu-id="bab36-193">**연결** : 연결 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="bab36-193">**Connect** :         Connect-level COM authentication</span></span>
- <span data-ttu-id="bab36-194">**기본값** : Windows 인증</span><span class="sxs-lookup"><span data-stu-id="bab36-194">**Default** :         Windows Authentication</span></span>
- <span data-ttu-id="bab36-195">**없음** : COM 인증 없음</span><span class="sxs-lookup"><span data-stu-id="bab36-195">**None** :            No COM authentication</span></span>
- <span data-ttu-id="bab36-196">**패킷** : 패킷 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-196">**Packet** :          Packet-level COM authentication.</span></span>
- <span data-ttu-id="bab36-197">**PacketIntegrity** : 패킷 무결성 수준 COM 인증</span><span class="sxs-lookup"><span data-stu-id="bab36-197">**PacketIntegrity** : Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="bab36-198">**PacketPrivacy** : 패킷 개인 정보 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-198">**PacketPrivacy** :   Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="bab36-199">**변경 되지 않음** : 인증 수준이 이전 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-199">**Unchanged** :       The authentication level is the same as the previous command.</span></span>

<span data-ttu-id="bab36-200">자세한 내용은 [Authenticationlevel 열거](/dotnet/api/system.management.authenticationlevel)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bab36-200">For more information, see [AuthenticationLevel Enumeration](/dotnet/api/system.management.authenticationlevel).</span></span>

<span data-ttu-id="bab36-201">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-201">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-202">-Delay</span><span class="sxs-lookup"><span data-stu-id="bab36-202">-Delay</span></span>

<span data-ttu-id="bab36-203">쿼리의 빈도 (초)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-203">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="bab36-204">PowerShell은 **For** 매개 변수로 지정 된 서비스를 쿼리하여 컴퓨터를 다시 시작한 후 서비스를 사용할 수 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-204">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="bab36-205">이 매개 변수는 **Wait** 및 **For** 매개 변수와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-205">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="bab36-206">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="bab36-207">**Delay** 매개 변수를 지정 하지 않으면에서 `Restart-Computer` 5 초 지연 시간을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-207">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-208">-의 경우</span><span class="sxs-lookup"><span data-stu-id="bab36-208">-For</span></span>

<span data-ttu-id="bab36-209">컴퓨터를 다시 시작한 후 지정 된 서비스 또는 기능을 사용할 수 있을 때까지 기다리는 PowerShell의 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-209">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="bab36-210">이 매개 변수는 **Wait** 매개 변수에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-210">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="bab36-211">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bab36-212">**기본값** : PowerShell이 다시 시작 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-212">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="bab36-213">**Powershell** : 컴퓨터의 powershell 원격 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-213">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="bab36-214">**WMI** : 컴퓨터에 대 한 Win32_ComputerSystem 쿼리에 대 한 응답을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-214">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="bab36-215">**WinRM** : ws-management를 사용 하 여 컴퓨터에 대 한 원격 세션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-215">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="bab36-216">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-217">-Force</span><span class="sxs-lookup"><span data-stu-id="bab36-217">-Force</span></span>

<span data-ttu-id="bab36-218">컴퓨터를 강제로 즉시 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-218">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-219">-가장</span><span class="sxs-lookup"><span data-stu-id="bab36-219">-Impersonation</span></span>

<span data-ttu-id="bab36-220">이 cmdlet이 WMI를 호출 하는 데 사용 하는 가장 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-220">Specifies the impersonation level that this cmdlet uses to call WMI.</span></span> <span data-ttu-id="bab36-221">`Restart-Computer` WMI를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-221">`Restart-Computer` uses WMI.</span></span>
<span data-ttu-id="bab36-222">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bab36-223">**기본값** : 기본 가장.</span><span class="sxs-lookup"><span data-stu-id="bab36-223">**Default** : Default impersonation.</span></span> <span data-ttu-id="bab36-224">이름에도 불구 하 고 기본값은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-224">Despite the name, this isn't the default value.</span></span>
- <span data-ttu-id="bab36-225">**Anonymous** : 호출자의 id를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-225">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="bab36-226">**식별** : 개체가 호출자의 자격 증명을 쿼리할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-226">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="bab36-227">**Impersonate** : 개체가 호출자의 자격 증명을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-227">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-228">-Protocol</span><span class="sxs-lookup"><span data-stu-id="bab36-228">-Protocol</span></span>

<span data-ttu-id="bab36-229">컴퓨터를 다시 시작하는 데 사용할 프로토콜을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-229">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="bab36-230">유효한 값은 **WSMan** 및 **DCOM** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-230">The valid values are **WSMan** and **DCOM**.</span></span>

<span data-ttu-id="bab36-231">이 매개 변수는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-232">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="bab36-232">-ThrottleLimit</span></span>

<span data-ttu-id="bab36-233">이 명령을 실행하도록 설정할 수 있는 최대 동시 연결 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-233">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="bab36-234">제한 한도는 현재 명령에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-234">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="bab36-235">**ThrottleLimit** 매개 변수를 지정 하지 않거나 0 값을 사용 하는 경우는 `Restart-Computer` 최대 32의 동시 연결을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-235">If the **ThrottleLimit** parameter isn't specified or a value of 0 is used, `Restart-Computer` uses a maximum of 32 concurrent connections.</span></span>

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-236">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="bab36-236">-Timeout</span></span>

<span data-ttu-id="bab36-237">대기 기간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-237">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="bab36-238">시간이 경과할 때 컴퓨터를 `Restart-Computer` 다시 시작 하지 않아도 명령 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-238">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="bab36-239">**Timeout** 매개 변수는 **Wait** 매개 변수에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-239">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="bab36-240">**Timeout** 은 **대기** 매개 변수의 무한 대기 기간을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-240">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="bab36-241">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-241">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-242">-Wait</span><span class="sxs-lookup"><span data-stu-id="bab36-242">-Wait</span></span>

<span data-ttu-id="bab36-243">`Restart-Computer` PowerShell 프롬프트를 표시 하지 않고 컴퓨터가 다시 시작 될 때까지 파이프라인을 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-243">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="bab36-244">스크립트에서이 매개 변수를 사용 하 여 컴퓨터를 다시 시작한 다음 다시 시작이 완료 되 면 계속 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-244">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="bab36-245">**Wait** 매개 변수는 컴퓨터를 다시 시작할 때까지 무기한 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-245">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="bab36-246">**시간 제한** 을 사용 하 여 타이밍을 조정 하 고 **For** 및 **Delay** 매개 변수를 사용 하 여 다시 시작 된 컴퓨터에서 특정 서비스를 사용할 수 있을 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-246">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="bab36-247">로컬 컴퓨터를 다시 시작 하는 경우에는 **Wait** 매개 변수가 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-247">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="bab36-248">**ComputerName** 매개 변수 값에 원격 컴퓨터와 로컬 컴퓨터의 이름이 포함 된 경우에서 `Restart-Computer` 로컬 컴퓨터의 **대기** 에 대 한 종료 되지 않는 오류를 생성 하지만 원격 컴퓨터를 다시 시작할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-248">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="bab36-249">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-250">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="bab36-250">-WsmanAuthentication</span></span>

<span data-ttu-id="bab36-251">사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-251">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="bab36-252">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-252">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="bab36-253">이 매개 변수에 허용 되는 값은 **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** 및 **Negotiate** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-253">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate**.</span></span>

<span data-ttu-id="bab36-254">자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bab36-254">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="bab36-255">사용자 자격 증명을 인증을 위해 원격 컴퓨터에 전달 하는 CredSSP (Credential Security Service Provider) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-255">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="bab36-256">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-256">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="bab36-257">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-257">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bab36-258">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bab36-258">-Confirm</span></span>

<span data-ttu-id="bab36-259">실행 하기 전에 확인 메시지를 표시 `Restart-Computer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-259">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="bab36-260">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bab36-260">-WhatIf</span></span>

<span data-ttu-id="bab36-261">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="bab36-261">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="bab36-262">`Restart-Computer`Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-262">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="bab36-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bab36-263">CommonParameters</span></span>

<span data-ttu-id="bab36-264">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bab36-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bab36-265">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bab36-265">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bab36-266">입력</span><span class="sxs-lookup"><span data-stu-id="bab36-266">INPUTS</span></span>

### <span data-ttu-id="bab36-267">System.String</span><span class="sxs-lookup"><span data-stu-id="bab36-267">System.String</span></span>

<span data-ttu-id="bab36-268">`Restart-Computer` 파이프라인 또는 변수의 컴퓨터 이름을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-268">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

<span data-ttu-id="bab36-269">Windows PowerShell 2.0에서 **ComputerName** 매개 변수는 속성 이름으로만 파이프라인의 입력을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-269">In Windows PowerShell 2.0, the **ComputerName** parameter takes input from the pipeline only by property name.</span></span> <span data-ttu-id="bab36-270">Windows PowerShell 3.0 이상에서 **ComputerName** 매개 변수는 값으로 파이프라인에서 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-270">In Windows PowerShell 3.0, and later, the **ComputerName** parameter takes input from the pipeline by value.</span></span>

## <span data-ttu-id="bab36-271">출력</span><span class="sxs-lookup"><span data-stu-id="bab36-271">OUTPUTS</span></span>

### <span data-ttu-id="bab36-272">없음, System.web. Remorerejob</span><span class="sxs-lookup"><span data-stu-id="bab36-272">None, System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="bab36-273">**AsJob** 매개 변수를 지정 하는 경우 `Restart-Computer` 은 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-273">If you specify the **AsJob** parameter, `Restart-Computer` returns a job object.</span></span> <span data-ttu-id="bab36-274">그렇지 않으면 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-274">Otherwise, no output is generated.</span></span>

## <span data-ttu-id="bab36-275">참고</span><span class="sxs-lookup"><span data-stu-id="bab36-275">NOTES</span></span>

- <span data-ttu-id="bab36-276">`Restart-Computer` Windows를 실행 하는 컴퓨터 에서만 작동 하 고 로컬 시스템을 포함 하 여 시스템을 종료 하는 WinRM 및 WMI가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-276">`Restart-Computer` only work on computers running Windows and requires WinRM and WMI to shutdown a system, including the local system.</span></span>
- <span data-ttu-id="bab36-277">`Restart-Computer`WMI(Windows Management Instrumentation) (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) 클래스의 [Win32Shutdown 메서드](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-277">`Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span>  <span data-ttu-id="bab36-278">이 메서드를 사용 하려면 컴퓨터를 다시 시작 하는 데 사용 되는 사용자 계정에 대해 **SeShutdownPrivilege** 권한을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-278">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="bab36-279">Windows PowerShell 2.0에서 **AsJob** 매개 변수는 원격 컴퓨터를 다시 시작 하거나 중지할 때 안정적으로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-279">In Windows PowerShell 2.0, the **AsJob** parameter doesn't work reliably when you are restarting or stopping remote computers.</span></span> <span data-ttu-id="bab36-280">Windows PowerShell 3.0에서는 이 문제를 해결하기 위해 구현이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bab36-280">In Windows PowerShell 3.0, the implementation is changed to resolve this problem.</span></span>

## <span data-ttu-id="bab36-281">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bab36-281">RELATED LINKS</span></span>

[<span data-ttu-id="bab36-282">Windows 원격 관리 정보</span><span class="sxs-lookup"><span data-stu-id="bab36-282">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="bab36-283">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="bab36-283">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="bab36-284">WS-Management 프로토콜</span><span class="sxs-lookup"><span data-stu-id="bab36-284">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
