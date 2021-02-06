---
description: 원격 컴퓨터에서 작업을 실행 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 93e1d3aba1f4037cc3c5c18386488bf321fc2a64
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602653"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="3a857-103">원격 작업 정보</span><span class="sxs-lookup"><span data-stu-id="3a857-103">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="3a857-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="3a857-104">Short Description</span></span>
<span data-ttu-id="3a857-105">원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-105">Describes how to run background jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="3a857-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="3a857-106">Detailed Description</span></span>

<span data-ttu-id="3a857-107">PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-107">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="3a857-108">PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-108">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="3a857-109">`RemoteJob` -명령 및 스크립트가 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-109">`RemoteJob` - Commands and scripts run in a remote session.</span></span>
- <span data-ttu-id="3a857-110">`BackgroundJob` -명령 및 스크립트는 로컬 컴퓨터에서 별도의 프로세스로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-110">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="3a857-111">자세한 내용은 [about_Jobs](about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a857-111">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="3a857-112">`PSTaskJob` 또는 `ThreadJob` -명령 및 스크립트는 로컬 컴퓨터에서 동일한 프로세스 내에서 별도의 스레드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-112">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="3a857-113">자세한 내용은 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a857-113">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="3a857-114">별도의 컴퓨터에서 또는 별도의 프로세스로 스크립트를 원격으로 실행 하면 뛰어난 격리를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-114">Running scripts remotely, on a separate machine or in a separate process, provide great isolation.</span></span> <span data-ttu-id="3a857-115">원격 작업에서 발생 하는 모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 부모 세션에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-115">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="3a857-116">그러나 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-116">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="3a857-117">모든 개체는 부모 세션과 원격 (작업) 세션 간에 전달 될 때 serialize 되 고 deserialize 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-117">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="3a857-118">크고 복잡 한 데이터 개체의 Serialization은 많은 양의 계산 및 메모리 리소스를 사용 하 고 네트워크를 통해 많은 양의 데이터를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-118">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a857-119">작업을 만든 부모 세션도 작업 상태를 모니터링 하 고 파이프라인 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-119">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="3a857-120">작업이 완료 된 상태에 도달 하면 부모 프로세스가 작업 자식 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-120">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="3a857-121">부모 세션이 종료 되 면 모든 실행 중인 자식 작업은 자식 프로세스와 함께 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-121">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="3a857-122">이러한 상황을 해결 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-122">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="3a857-123">`Invoke-Command`를 사용 하 여 연결 되지 않은 세션에서 실행 되는 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-123">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="3a857-124">이 문서의 [분리 된 프로세스](#how-to-run-as-a-detached-process) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a857-124">See the [detached processes](#how-to-run-as-a-detached-process) section of this article.</span></span>
1. <span data-ttu-id="3a857-125">`Start-Process`작업 대신 새 프로세스를 만들려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-125">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="3a857-126">자세한 내용은 [시작-처리](xref:Microsoft.PowerShell.Management.Start-Process)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a857-126">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="remote-jobs"></a><span data-ttu-id="3a857-127">원격 작업</span><span class="sxs-lookup"><span data-stu-id="3a857-127">Remote Jobs</span></span>

<span data-ttu-id="3a857-128">3 가지 방법을 사용 하 여 원격 컴퓨터에서 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-128">You can run jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="3a857-129">원격 컴퓨터에서 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-129">Start an interactive session on a remote computer.</span></span> <span data-ttu-id="3a857-130">그런 다음 대화형 세션에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-130">Then start a job in the interactive session.</span></span> <span data-ttu-id="3a857-131">모든 작업은 원격 컴퓨터에서 수행 되지만 절차는 로컬 작업 실행과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-131">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="3a857-132">로컬 컴퓨터에 결과를 반환 하는 원격 컴퓨터에서 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-132">Run a job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="3a857-133">작업의 결과를 수집 하 고 로컬 컴퓨터의 중앙 위치에서 유지 관리 하려는 경우이 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-133">Use this method when you want to collect the results of jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="3a857-134">원격 컴퓨터에 대 한 결과를 유지 하는 원격 컴퓨터에서 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-134">Run a job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="3a857-135">작업 데이터가 원래 컴퓨터에서 더 안전 하 게 유지 되는 경우이 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-135">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-job-in-an-interactive-session"></a><span data-ttu-id="3a857-136">대화형 세션에서 작업 시작</span><span class="sxs-lookup"><span data-stu-id="3a857-136">Start a job in an interactive session</span></span>

<span data-ttu-id="3a857-137">원격 컴퓨터를 사용 하 여 대화형 세션을 시작한 다음 대화형 세션 중에 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-137">You can start an interactive session with a remote computer and then start a job during the interactive session.</span></span> <span data-ttu-id="3a857-138">대화형 세션에 대 한 자세한 내용은 about_Remote 및을 참조 하세요 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3a857-138">For more information about interactive sessions, see about_Remote, and see `Enter-PSSession`.</span></span>

<span data-ttu-id="3a857-139">대화형 세션에서 작업을 시작 하는 절차는 로컬 컴퓨터에서 백그라운드 작업을 시작 하는 절차와 거의 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-139">The procedure for starting a job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="3a857-140">그러나 모든 작업은 로컬 컴퓨터가 아닌 원격 컴퓨터에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-140">However, all of the operations occur on the remote computer, not the local computer.</span></span>

1. <span data-ttu-id="3a857-141">Cmdlet을 사용 `Enter-PSSession` 하 여 원격 컴퓨터와의 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-141">Use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="3a857-142">의 ComputerName 매개 변수를 사용 `Enter-PSSession` 하 여 대화형 세션에 대 한 임시 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-142">You can use the ComputerName parameter of `Enter-PSSession` to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="3a857-143">또는 Session 매개 변수를 사용 하 여 PowerShell 세션 (PSSession)에서 대화형 세션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-143">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

   <span data-ttu-id="3a857-144">다음 명령은 Server01 컴퓨터에서 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-144">The following command starts an interactive session on the Server01 computer.</span></span>

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   <span data-ttu-id="3a857-145">명령 프롬프트가 변경 되어 이제 Server01 컴퓨터에 연결 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-145">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

   ```
   Server01\C:>
   ```

1. <span data-ttu-id="3a857-146">세션에서 원격 작업을 시작 하려면 cmdlet을 사용 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-146">To start a remote job in the session, use the `Start-Job` cmdlet.</span></span> <span data-ttu-id="3a857-147">다음 명령은 Server01 컴퓨터의 Windows PowerShell 이벤트 로그에 있는 이벤트를 가져오는 원격 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-147">The following command runs a remote job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="3a857-148">`Start-Job`Cmdlet은 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-148">The `Start-Job` cmdlet returns an object that represents the job.</span></span>

   <span data-ttu-id="3a857-149">이 명령은 작업 개체를 `$job` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-149">This command saves the job object in the `$job` variable.</span></span>

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   <span data-ttu-id="3a857-150">작업이 실행 되는 동안 대화형 세션을 사용 하 여 다른 작업을 비롯 한 다른 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-150">While the job runs, you can use the interactive session to run other commands, including other jobs.</span></span> <span data-ttu-id="3a857-151">그러나 작업이 완료 될 때까지 대화형 세션을 열어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-151">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="3a857-152">세션을 종료 하면 작업이 중단 되 고 결과가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-152">If you end the session, the job is interrupted, and the results are lost.</span></span>

1. <span data-ttu-id="3a857-153">작업이 완료 되었는지 확인 하려면 변수 값을 표시 `$job` 하거나 cmdlet을 사용 `Get-Job` 하 여 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-153">To find out if the job is complete, display the value of the `$job` variable, or use the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="3a857-154">다음 명령은 cmdlet을 사용 하 여 `Get-Job` 작업을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-154">The following command uses the `Get-Job` cmdlet to display the job.</span></span>

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   <span data-ttu-id="3a857-155">`Get-Job`작업은 작업을 시작 하 고 동일한 컴퓨터에서 실행 되 고 있기 때문에 (이 경우 Server01) "localhost" 컴퓨터에서 작업이 실행 되는 것을 출력에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-155">The `Get-Job` output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

1. <span data-ttu-id="3a857-156">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3a857-156">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="3a857-157">대화형 세션에서 결과를 표시 하거나 원격 컴퓨터의 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-157">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="3a857-158">다음 명령은 $job 변수의 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-158">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="3a857-159">이 명령은 리디렉션 연산자 ()를 사용 `>` 하 여 작업 결과를 Server01 컴퓨터의 PsLog.txt 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-159">The command uses the redirection operator (`>`) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. <span data-ttu-id="3a857-160">대화형 세션을 종료 하려면 cmdlet을 사용 `Exit-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-160">To end the interactive session, use the `Exit-PSSession` cmdlet.</span></span> <span data-ttu-id="3a857-161">명령 프롬프트가 변경 되어 로컬 컴퓨터의 원래 세션으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-161">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. <span data-ttu-id="3a857-162">언제 `PsLog.txt` 든 지 Server01 컴퓨터에서 파일의 내용을 보려면 다른 대화형 세션을 시작 하거나 원격 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-162">To view the contents of the `PsLog.txt` file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="3a857-163">여러 명령을 사용 하 여 파일의 데이터를 조사 하 고 관리 하려는 경우이 유형의 명령은 PSSession (영구 연결)에서 가장 잘 실행 됩니다 `PsLog.txt` .</span><span class="sxs-lookup"><span data-stu-id="3a857-163">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the `PsLog.txt` file.</span></span> <span data-ttu-id="3a857-164">Pssession에 대 한 자세한 내용은 [about_PSSessions](about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a857-164">For more information about PSSessions, see [about_PSSessions](about_PSSessions.md).</span></span>

   <span data-ttu-id="3a857-165">다음 명령은 cmdlet을 사용 `New-PSSession` 하 여 Server01 컴퓨터에 연결 된 **pssession** 을 만들고, cmdlet을 사용 하 여 `Invoke-Command` `Get-Content` pssession에서 명령을 실행 하 여 파일의 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-165">The following commands use the `New-PSSession` cmdlet to create a **PSSession** that is connected to the Server01 computer, and they use the `Invoke-Command` cmdlet to run a `Get-Content` command in the PSSession to view the contents of the file.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="3a857-166">결과를 로컬 컴퓨터 (AsJob)로 반환 하는 원격 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-166">Start a remote job that returns the results to the local computer (AsJob)</span></span>

<span data-ttu-id="3a857-167">로컬 컴퓨터에 명령 결과를 반환 하는 원격 컴퓨터에서 작업을 시작 하려면 cmdlet과 같은 cmdlet의 **AsJob** 매개 변수를 사용 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="3a857-167">To start a job on a remote computer that returns the command results to the local computer, use the **AsJob** parameter of a cmdlet such as the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="3a857-168">**AsJob** 매개 변수를 사용 하는 경우 작업이 원격 컴퓨터에서 실행 되는 경우에도 실제로 작업 개체는 로컬 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-168">When you use the **AsJob** parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="3a857-169">작업이 완료 되 면 결과는 로컬 컴퓨터에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-169">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="3a857-170">작업 명사 (Job cmdlet)를 포함 하는 cmdlet을 사용 하 여 모든 cmdlet에 의해 생성 된 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-170">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="3a857-171">**AsJob** 매개 변수를 포함 하는 많은 Cmdlet은 PowerShell 원격을 사용 하지 않으므로 원격 기능을 사용 하도록 구성 되지 않고 원격 기능에 대 한 요구 사항을 충족 하지 않는 컴퓨터 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-171">Many of the cmdlets that have **AsJob** parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

1. <span data-ttu-id="3a857-172">다음 명령은의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` Server01 컴퓨터에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-172">The following command uses the **AsJob** parameter of `Invoke-Command` to start a job on the Server01 computer.</span></span> <span data-ttu-id="3a857-173">작업은 `Get-Eventlog` 시스템 로그의 이벤트를 가져오는 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-173">The job runs a `Get-Eventlog` command that gets the events in the System log.</span></span> <span data-ttu-id="3a857-174">JobName 매개 변수를 사용 하 여 작업에 표시 이름을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-174">You can use the JobName parameter to assign a display name to the job.</span></span>

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   <span data-ttu-id="3a857-175">명령의 결과는 다음 샘플 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-175">The results of the command resemble the following sample output.</span></span>

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   <span data-ttu-id="3a857-176">**AsJob** 매개 변수를 사용 하는 경우는를 `Invoke-Command` 반환 하는 동일한 유형의 작업 개체를 반환 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3a857-176">When the **AsJob** parameter is used, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="3a857-177">작업 개체를 변수에 저장 하거나 명령을 사용 하 여 작업을 가져올 수 있습니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="3a857-177">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="3a857-178">Location 속성의 값은 작업이 Server01 컴퓨터에서 실행 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-178">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

1. <span data-ttu-id="3a857-179">Cmdlet의 **AsJob** 매개 변수를 사용 하 여 시작 된 작업을 관리 하려면 `Invoke-Command` job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-179">To manage a job started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="3a857-180">원격 작업을 나타내는 작업 개체는 로컬 컴퓨터에 있기 때문에 작업을 관리 하기 위해 원격 명령을 실행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-180">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

   <span data-ttu-id="3a857-181">작업이 완료 되었는지 여부를 확인 하려면 `Get-Job` 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-181">To determine whether the job is complete, use a `Get-Job` command.</span></span> <span data-ttu-id="3a857-182">다음 명령은 현재 세션에서 시작 된 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-182">The following command gets all of the jobs that were started in the current session.</span></span>

   ```powershell
   Get-Job
   ```

   <span data-ttu-id="3a857-183">원격 작업이 현재 세션에서 시작 되었기 때문에 로컬 `Get-Job` 명령은 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-183">Because the remote job was started in the current session, a local `Get-Job` command gets the job.</span></span> <span data-ttu-id="3a857-184">작업 개체의 State 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-184">The State property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. <span data-ttu-id="3a857-185">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3a857-185">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="3a857-186">작업 결과가 작업 개체가 있는 컴퓨터에 자동으로 반환 되므로 로컬 명령을 사용 하 여 결과를 가져올 수 있습니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3a857-186">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local `Receive-Job` command.</span></span>

   <span data-ttu-id="3a857-187">다음 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-187">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="3a857-188">세션 ID를 사용 하 여 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-188">It uses the session ID to identify the job.</span></span> <span data-ttu-id="3a857-189">이 명령은 $results 변수에 작업 결과를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-189">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="3a857-190">또한 결과를 파일로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-190">You can also redirect the results to a file.</span></span>

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="3a857-191">원격 컴퓨터에 결과를 보관 하는 원격 작업 시작</span><span class="sxs-lookup"><span data-stu-id="3a857-191">Start a remote job that keeps the results on the remote computer</span></span>

<span data-ttu-id="3a857-192">원격 컴퓨터에서 명령 결과를 유지 하는 원격 컴퓨터에서 작업을 시작 하려면 cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-192">To start a job on a remote computer that keeps the command results on the remote computer, use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="3a857-193">이 메서드를 사용 하 여 여러 컴퓨터에서 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-193">You can use this method to run jobs on multiple computers.</span></span>

<span data-ttu-id="3a857-194">명령을 원격으로 실행 하는 경우 `Start-Job` 작업 개체가 원격 컴퓨터에 만들어지고 작업 결과가 원격 컴퓨터에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-194">When you run a `Start-Job` command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="3a857-195">작업의 관점에서 보면 모든 작업은 로컬입니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-195">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="3a857-196">원격 컴퓨터에서 로컬 작업을 관리 하기 위해 원격으로 명령을 실행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-196">You are just running commands remotely to manage a local job on the remote computer.</span></span>

1. <span data-ttu-id="3a857-197">Cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-197">Use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span>

   <span data-ttu-id="3a857-198">이 명령에는 PSSession (영구 연결)이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-198">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="3a857-199">의 ComputerName 매개 변수를 사용 하 여 임시 연결을 설정 하는 경우 `Invoke-Command` `Invoke-Command` 작업 개체가 반환 될 때 명령이 완료 된 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-199">If you use the ComputerName parameter of `Invoke-Command` to establish a temporary connection, the `Invoke-Command` command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="3a857-200">결과적으로 임시 연결이 닫히고 작업이 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-200">As a result, the temporary connection is closed, and the job is canceled.</span></span>

   <span data-ttu-id="3a857-201">다음 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 컴퓨터에 연결 된 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-201">The following command uses the `New-PSSession` cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="3a857-202">이 명령은 PSSession을 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="3a857-202">The command saves the PSSession in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   <span data-ttu-id="3a857-203">다음 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` PSSession에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-203">The next command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the PSSession.</span></span> <span data-ttu-id="3a857-204">`Start-Job`명령과 `Get-Eventlog` 명령이 중괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-204">The `Start-Job` command and the `Get-Eventlog` command are enclosed in braces.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   <span data-ttu-id="3a857-205">결과는 다음 예제 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-205">The results resemble the following sample output.</span></span>

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   <span data-ttu-id="3a857-206">명령을 원격으로 실행 하는 경우는 `Start-Job` 를 `Invoke-Command` 반환 하는 동일한 유형의 작업 개체를 반환 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3a857-206">When you run a `Start-Job` command remotely, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="3a857-207">작업 개체를 변수에 저장 하거나 명령을 사용 하 여 작업을 가져올 수 있습니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="3a857-207">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="3a857-208">**Location** 속성의 값은 작업이 Server01 컴퓨터에서 실행 된 경우에도 "LocalHost" 라는 로컬 컴퓨터에서 실행 된 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-208">Note that the value of the **Location** property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="3a857-209">작업 개체는 Server01 컴퓨터에 생성 되 고 작업은 동일한 컴퓨터에서 실행 되기 때문에 로컬 백그라운드 작업으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-209">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

1. <span data-ttu-id="3a857-210">원격 작업을 관리 하려면 **job** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-210">To manage a remote job, use the **Job** cmdlets.</span></span> <span data-ttu-id="3a857-211">작업 개체가 원격 컴퓨터에 있기 때문에 작업 결과를 가져오기, 중지, 대기 또는 검색 하기 위해 원격 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-211">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

   <span data-ttu-id="3a857-212">작업이 완료 되었는지 확인 하려면 명령을 사용 하 여 `Invoke-Command` `Get-Job` Server01 컴퓨터에 연결 된 PSSession에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-212">To see if the job is complete, use an `Invoke-Command` command to run a `Get-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   <span data-ttu-id="3a857-213">작업 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-213">The command returns a job object.</span></span> <span data-ttu-id="3a857-214">작업 개체의 **State** 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-214">The **State** property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. <span data-ttu-id="3a857-215">작업 결과를 가져오려면 cmdlet을 사용 `Invoke-Command` 하 여 `Receive-Job` Server01 컴퓨터에 연결 된 PSSession에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-215">To get the results of the job, use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   <span data-ttu-id="3a857-216">다음 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-216">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="3a857-217">세션 ID를 사용 하 여 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-217">It uses the session ID to identify the job.</span></span> <span data-ttu-id="3a857-218">이 명령은 작업 결과를 `$results` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-218">This command saves the job results in the `$results` variable.</span></span> <span data-ttu-id="3a857-219">의 Keep 매개 변수를 사용 하 여 `Receive-Job` 결과를 원격 컴퓨터의 작업 캐시에 보관 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-219">It uses the Keep parameter of `Receive-Job` to keep the result in the job cache on the remote computer.</span></span>

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   <span data-ttu-id="3a857-220">로컬 또는 원격 컴퓨터의 파일로 결과를 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-220">You can also redirect the results to a file on the local or remote computer.</span></span>
   <span data-ttu-id="3a857-221">다음 명령은 리디렉션 연산자를 사용 하 여 Server01 컴퓨터의 파일에 결과를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-221">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a><span data-ttu-id="3a857-222">분리 된 프로세스로 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="3a857-222">How to run as a detached process</span></span>

<span data-ttu-id="3a857-223">앞서 언급 했 듯이 부모 세션이 종료 되 면 실행 중인 모든 자식 작업은 자식 프로세스와 함께 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-223">As previously mentioned, when the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span> <span data-ttu-id="3a857-224">로컬 컴퓨터에서 원격을 사용 하 여 현재 PowerShell 세션에 연결 되지 않은 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-224">You can use remoting on the local machine to run jobs that are not attached to the current PowerShell session.</span></span>

<span data-ttu-id="3a857-225">로컬 컴퓨터에서 새 PowerShell 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-225">Create a new PowerShell session on the local machine.</span></span> <span data-ttu-id="3a857-226">`Invoke-Command`이 세션에서 작업을 시작 하는 데 사용 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-226">The use `Invoke-Command` to start a job in this session.</span></span> <span data-ttu-id="3a857-227">`Invoke-Command` 원격 세션의 연결을 끊고 부모 세션을 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-227">`Invoke-Command` allows you to disconnect a remote session and terminate the parent session.</span></span> <span data-ttu-id="3a857-228">나중에 새 PowerShell 세션을 시작 하 고 이전에 연결이 끊어진 세션에 연결 하 여 작업 모니터링을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-228">Later, you can start a new PowerShell session and connect to the previously disconnected session to resume monitoring the job.</span></span> <span data-ttu-id="3a857-229">그러나 해당 세션이 종료 되 면 원래 PowerShell 세션에 반환 된 모든 데이터가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-229">However, any data that was returned to the original PowerShell session is lost when that session is terminated.</span></span> <span data-ttu-id="3a857-230">다시 연결할 때 연결 끊기 후에 생성 된 새 데이터 개체만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-230">Only new data objects generated after the disconnect are returned when re-connected.</span></span>

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

<span data-ttu-id="3a857-231">이 예에서는 작업이 부모 PowerShell 세션에 계속 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a857-231">For this example, the jobs are still attached to a parent PowerShell session.</span></span>
<span data-ttu-id="3a857-232">그러나 부모 세션은가 실행 되는 원래 PowerShell 세션이 아닙니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="3a857-232">However, the parent session is not the original PowerShell session where `Invoke-Command` was run.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a857-233">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a857-233">See also</span></span>

- [<span data-ttu-id="3a857-234">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="3a857-234">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="3a857-235">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="3a857-235">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="3a857-236">about_Remote</span><span class="sxs-lookup"><span data-stu-id="3a857-236">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="3a857-237">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="3a857-237">about_Remote_Variables</span></span>](about_Remote_Variables.md)
- [<span data-ttu-id="3a857-238">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3a857-238">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="3a857-239">Start-Job</span><span class="sxs-lookup"><span data-stu-id="3a857-239">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="3a857-240">Get-Job</span><span class="sxs-lookup"><span data-stu-id="3a857-240">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="3a857-241">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="3a857-241">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="3a857-242">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="3a857-242">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="3a857-243">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="3a857-243">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="3a857-244">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a857-244">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="3a857-245">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a857-245">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="3a857-246">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a857-246">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
