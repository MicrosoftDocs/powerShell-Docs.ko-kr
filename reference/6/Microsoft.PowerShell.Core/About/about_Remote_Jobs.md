---
description: 원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: ad0400c4b4c25c9b0c7133bd916af5056dab1430
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221266"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="ad2a5-104">원격 작업 정보</span><span class="sxs-lookup"><span data-stu-id="ad2a5-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="ad2a5-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ad2a5-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ad2a5-106">원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-106">Describes how to run background jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="ad2a5-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ad2a5-107">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="ad2a5-108">백그라운드 작업은 현재 세션과 상호 작용 하지 않고 비동기적으로 실행 되는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-108">A background job is a command that runs asynchronously without interacting with the current session.</span></span> <span data-ttu-id="ad2a5-109">명령 프롬프트가 즉시 반환 되며 작업이 실행 되는 동안 세션을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-109">The command prompt returns immediately, and you can continue to use the session while the job runs.</span></span>

<span data-ttu-id="ad2a5-110">기본적으로 백그라운드 작업은 로컬 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-110">By default, background jobs run on the local computer.</span></span> <span data-ttu-id="ad2a5-111">그러나 여러 가지 절차를 사용 하 여 원격 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-111">However, you can use several different procedures to run background jobs on remote computers.</span></span>

<span data-ttu-id="ad2a5-112">이 항목에서는 원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-112">This topic explains how to run a background job on a remote computer.</span></span> <span data-ttu-id="ad2a5-113">로컬 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-113">For information about how to run background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span> <span data-ttu-id="ad2a5-114">백그라운드 작업에 대 한 자세한 내용은 [about_Job_Details](about_Job_Details.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-114">For more information about background jobs, see [about_Job_Details](about_Job_Details.md).</span></span>

## <a name="remote-background-jobs"></a><span data-ttu-id="ad2a5-115">원격 백그라운드 작업</span><span class="sxs-lookup"><span data-stu-id="ad2a5-115">REMOTE BACKGROUND JOBS</span></span>

<span data-ttu-id="ad2a5-116">3 가지 방법을 사용 하 여 원격 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-116">You can run background jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="ad2a5-117">원격 컴퓨터와 대화형 세션을 시작 하 고 대화형 세션에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-117">Start an interactive session with a remote computer, and start a job in the interactive session.</span></span> <span data-ttu-id="ad2a5-118">모든 작업은 원격 컴퓨터에서 수행 되지만 절차는 로컬 작업 실행과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-118">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="ad2a5-119">로컬 컴퓨터에 결과를 반환 하는 원격 컴퓨터에서 백그라운드 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-119">Run a background job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="ad2a5-120">백그라운드 작업의 결과를 수집 하 고 로컬 컴퓨터의 중앙 위치에서 유지 관리 하려는 경우이 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-120">Use this method when you want to collect the results of background jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="ad2a5-121">원격 컴퓨터에 대 한 결과를 유지 하는 원격 컴퓨터에서 백그라운드 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-121">Run a background job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="ad2a5-122">작업 데이터가 원래 컴퓨터에서 더 안전 하 게 유지 되는 경우이 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-122">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-background-job-in-an-interactive-session"></a><span data-ttu-id="ad2a5-123">대화형 세션에서 백그라운드 작업 시작</span><span class="sxs-lookup"><span data-stu-id="ad2a5-123">START A BACKGROUND JOB IN AN INTERACTIVE SESSION</span></span>

<span data-ttu-id="ad2a5-124">원격 컴퓨터를 사용 하 여 대화형 세션을 시작한 다음 대화형 세션 중에 백그라운드 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-124">You can start an interactive session with a remote computer and then start a background job during the interactive session.</span></span> <span data-ttu-id="ad2a5-125">대화형 세션에 대 한 자세한 내용은 about_Remote를 참조 하 고 Enter-PSSession을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-125">For more information about interactive sessions, see about_Remote, and see Enter-PSSession.</span></span>

<span data-ttu-id="ad2a5-126">대화형 세션에서 백그라운드 작업을 시작 하는 절차는 로컬 컴퓨터에서 백그라운드 작업을 시작 하는 절차와 거의 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-126">The procedure for starting a background job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="ad2a5-127">그러나 모든 작업은 로컬 컴퓨터가 아닌 원격 컴퓨터에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-127">However, all of the operations occur on the remote computer, not the local computer.</span></span>

#### <a name="step-1-enter-pssession"></a><span data-ttu-id="ad2a5-128">1 단계: ENTER-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="ad2a5-128">STEP 1: ENTER-PSSESSION</span></span>

<span data-ttu-id="ad2a5-129">Enter-PSSession cmdlet을 사용 하 여 원격 컴퓨터와의 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-129">Use the Enter-PSSession cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="ad2a5-130">Enter-PSSession의 ComputerName 매개 변수를 사용 하 여 대화형 세션에 대 한 임시 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-130">You can use the ComputerName parameter of Enter-PSSession to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="ad2a5-131">또는 Session 매개 변수를 사용 하 여 PowerShell 세션 (PSSession)에서 대화형 세션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-131">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

<span data-ttu-id="ad2a5-132">다음 명령은 Server01 컴퓨터에서 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-132">The following command starts an interactive session on the Server01 computer.</span></span>

```powershell
C:\PS> Enter-PSSession -computername Server01
```

<span data-ttu-id="ad2a5-133">명령 프롬프트가 변경 되어 이제 Server01 컴퓨터에 연결 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-133">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

```
Server01\C:>
```

#### <a name="step-2-start-job"></a><span data-ttu-id="ad2a5-134">2 단계: 작업 시작</span><span class="sxs-lookup"><span data-stu-id="ad2a5-134">STEP 2: START-JOB</span></span>

<span data-ttu-id="ad2a5-135">세션에서 백그라운드 작업을 시작 하려면 Start-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-135">To start a background job in the session, use the Start-Job cmdlet.</span></span>

<span data-ttu-id="ad2a5-136">다음 명령은 Server01 컴퓨터의 Windows PowerShell 이벤트 로그에 있는 이벤트를 가져오는 백그라운드 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-136">The following command runs a background job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="ad2a5-137">Start-Job cmdlet은 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-137">The Start-Job cmdlet returns an object that represents the job.</span></span>

<span data-ttu-id="ad2a5-138">이 명령은 작업 변수에 작업 개체를 저장 \$ 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-138">This command saves the job object in the \$job variable.</span></span>

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

<span data-ttu-id="ad2a5-139">작업이 실행 되는 동안 대화형 세션을 사용 하 여 다른 백그라운드 작업을 비롯 한 다른 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-139">While the job runs, you can use the interactive session to run other commands, including other background jobs.</span></span> <span data-ttu-id="ad2a5-140">그러나 작업이 완료 될 때까지 대화형 세션을 열어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-140">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="ad2a5-141">세션을 종료 하면 작업이 중단 되 고 결과가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-141">If you end the session, the job is interrupted, and the results are lost.</span></span>

#### <a name="step-3-get-job"></a><span data-ttu-id="ad2a5-142">3 단계: 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="ad2a5-142">STEP 3: GET-JOB</span></span>

<span data-ttu-id="ad2a5-143">작업이 완료 되었는지 확인 하려면 작업 변수의 값을 표시 \$ 하거나 Get-Job cmdlet을 사용 하 여 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-143">To find out if the job is complete, display the value of the \$job variable, or use the Get-Job cmdlet to get the job.</span></span> <span data-ttu-id="ad2a5-144">다음 명령은 Get-Job cmdlet을 사용 하 여 작업을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-144">The following command uses the Get-Job cmdlet to display the job.</span></span>

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

<span data-ttu-id="ad2a5-145">Get-Job 출력은 작업이 시작 되어 동일한 컴퓨터에서 실행 되 고 있으므로 (이 경우 Server01) "localhost" 컴퓨터에서 작업이 실행 되 고 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-145">The Get-Job output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

#### <a name="step-4-receive-job"></a><span data-ttu-id="ad2a5-146">4 단계: 수신 작업</span><span class="sxs-lookup"><span data-stu-id="ad2a5-146">STEP 4: RECEIVE-JOB</span></span>

<span data-ttu-id="ad2a5-147">작업의 결과를 가져오려면 Receive-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-147">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="ad2a5-148">대화형 세션에서 결과를 표시 하거나 원격 컴퓨터의 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-148">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="ad2a5-149">다음 명령은 $job 변수의 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-149">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="ad2a5-150">이 명령은 리디렉션 연산자 (>)를 사용 하 여 작업 결과를 Server01 컴퓨터의 PsLog.txt 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-150">The command uses the redirection operator (>) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a><span data-ttu-id="ad2a5-151">5 단계: 종료 PSSESSION</span><span class="sxs-lookup"><span data-stu-id="ad2a5-151">STEP 5: EXIT-PSSESSION</span></span>

<span data-ttu-id="ad2a5-152">대화형 세션을 종료 하려면 Exit-PSSession cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-152">To end the interactive session, use the Exit-PSSession cmdlet.</span></span> <span data-ttu-id="ad2a5-153">명령 프롬프트가 변경 되어 로컬 컴퓨터의 원래 세션으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-153">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a><span data-ttu-id="ad2a5-154">6 단계: 명령 호출: GET 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="ad2a5-154">STEP 6: INVOKE-COMMAND: GET-CONTENT</span></span>

<span data-ttu-id="ad2a5-155">Server01 컴퓨터에서 언제 든 지 PsLog.txt 파일의 콘텐츠를 보려면 다른 대화형 세션을 시작 하거나 원격 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-155">To view the contents of the PsLog.txt file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="ad2a5-156">여러 명령을 사용 하 여 PsLog.txt 파일의 데이터를 조사 하 고 관리 하려는 경우이 유형의 명령은 PSSession (영구 연결)에서 가장 잘 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-156">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the PsLog.txt file.</span></span> <span data-ttu-id="ad2a5-157">Pssession에 대 한 자세한 내용은 about_PSSessions를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-157">For more information about PSSessions, see about_PSSessions.</span></span>

<span data-ttu-id="ad2a5-158">다음 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession을 만들고, Invoke-Command cmdlet을 사용 하 여 PSSession에서 Get-Content 명령을 실행 하 여 파일의 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-158">The following commands use the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer, and they use the Invoke-Command cmdlet to run a Get-Content command in the PSSession to view the contents of the file.</span></span>

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="ad2a5-159">로컬 컴퓨터 ASJOB에 결과를 반환 하는 원격 작업을 시작 합니다. \(\)</span><span class="sxs-lookup"><span data-stu-id="ad2a5-159">START A REMOTE JOB THAT RETURNS THE RESULTS TO THE LOCAL COMPUTER \(ASJOB\)</span></span>

<span data-ttu-id="ad2a5-160">로컬 컴퓨터에 명령 결과를 반환 하는 원격 컴퓨터에서 백그라운드 작업을 시작 하려면 Invoke-Command cmdlet과 같은 cmdlet의 AsJob 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-160">To start a background job on a remote computer that returns the command results to the local computer, use the AsJob parameter of a cmdlet such as the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="ad2a5-161">AsJob 매개 변수를 사용 하는 경우 작업이 원격 컴퓨터에서 실행 되는 경우에도 실제로 작업 개체는 로컬 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-161">When you use the AsJob parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="ad2a5-162">작업이 완료 되 면 결과는 로컬 컴퓨터에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-162">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="ad2a5-163">작업 명사 (Job cmdlet)를 포함 하는 cmdlet을 사용 하 여 모든 cmdlet에 의해 생성 된 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-163">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="ad2a5-164">AsJob 매개 변수를 포함 하는 많은 cmdlet은 PowerShell 원격을 사용 하지 않으므로 원격 기능을 사용 하도록 구성 되지 않고 원격 기능에 대 한 요구 사항을 충족 하지 않는 컴퓨터 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-164">Many of the cmdlets that have AsJob parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

#### <a name="step-1-invoke-command--asjob"></a><span data-ttu-id="ad2a5-165">1 단계: 명령 호출-ASJOB</span><span class="sxs-lookup"><span data-stu-id="ad2a5-165">STEP 1: INVOKE-COMMAND -ASJOB</span></span>

<span data-ttu-id="ad2a5-166">다음 명령은 Invoke-Command의 AsJob 매개 변수를 사용 하 여 Server01 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-166">The following command uses the AsJob parameter of Invoke-Command to start a background job on the Server01 computer.</span></span> <span data-ttu-id="ad2a5-167">이 작업은 시스템 로그에서 이벤트를 가져오는 Get-Eventlog 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-167">The job runs a Get-Eventlog command that gets the events in the System log.</span></span> <span data-ttu-id="ad2a5-168">JobName 매개 변수를 사용 하 여 작업에 표시 이름을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-168">You can use the JobName parameter to assign a display name to the job.</span></span>

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

<span data-ttu-id="ad2a5-169">명령의 결과는 다음 샘플 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-169">The results of the command resemble the following sample output.</span></span>

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

<span data-ttu-id="ad2a5-170">AsJob 매개 변수를 사용 하는 경우 Invoke-Command는 Start-Job 반환 하는 것과 동일한 유형의 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-170">When the AsJob parameter is used, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="ad2a5-171">작업 개체를 변수에 저장 하거나 Get-Job 명령을 사용 하 여 작업을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-171">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="ad2a5-172">Location 속성의 값은 작업이 Server01 컴퓨터에서 실행 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-172">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

#### <a name="step-2-get-job"></a><span data-ttu-id="ad2a5-173">2 단계: 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="ad2a5-173">STEP 2: GET-JOB</span></span>

<span data-ttu-id="ad2a5-174">Invoke-Command cmdlet의 AsJob 매개 변수를 사용 하 여 시작 된 작업을 관리 하려면 Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-174">To manage a job started by using the AsJob parameter of the Invoke-Command cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="ad2a5-175">원격 작업을 나타내는 작업 개체는 로컬 컴퓨터에 있기 때문에 작업을 관리 하기 위해 원격 명령을 실행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-175">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

<span data-ttu-id="ad2a5-176">작업이 완료 되었는지 여부를 확인 하려면 Get-Job 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-176">To determine whether the job is complete, use a Get-Job command.</span></span> <span data-ttu-id="ad2a5-177">다음 명령은 현재 세션에서 시작 된 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-177">The following command gets all of the jobs that were started in the current session.</span></span>

```powershell
get-job
```

<span data-ttu-id="ad2a5-178">원격 작업이 현재 세션에서 시작 되었기 때문에 로컬 Get-Job 명령은 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-178">Because the remote job was started in the current session, a local Get-Job command gets the job.</span></span> <span data-ttu-id="ad2a5-179">작업 개체의 State 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-179">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a><span data-ttu-id="ad2a5-180">3 단계: 수신 작업</span><span class="sxs-lookup"><span data-stu-id="ad2a5-180">STEP 3: RECEIVE-JOB</span></span>

<span data-ttu-id="ad2a5-181">작업의 결과를 가져오려면 Receive-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-181">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="ad2a5-182">작업 결과가 작업 개체가 있는 컴퓨터에 자동으로 반환 되므로 로컬 Receive-Job 명령을 사용 하 여 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-182">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local Receive-Job command.</span></span>

<span data-ttu-id="ad2a5-183">다음 명령은 Receive-Job cmdlet을 사용 하 여 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-183">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="ad2a5-184">세션 ID를 사용 하 여 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-184">It uses the session ID to identify the job.</span></span> <span data-ttu-id="ad2a5-185">이 명령은 $results 변수에 작업 결과를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-185">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="ad2a5-186">또한 결과를 파일로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-186">You can also redirect the results to a file.</span></span>

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="ad2a5-187">원격 컴퓨터에 결과를 보관 하는 원격 작업 시작</span><span class="sxs-lookup"><span data-stu-id="ad2a5-187">START A REMOTE JOB THAT KEEPS THE RESULTS ON THE REMOTE COMPUTER</span></span>

<span data-ttu-id="ad2a5-188">원격 컴퓨터에서 명령 결과를 유지 하는 원격 컴퓨터에서 백그라운드 작업을 시작 하려면 Invoke-Command cmdlet을 사용 하 여 원격 컴퓨터에서 Start-Job 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-188">To start a background job on a remote computer that keeps the command results on the remote computer, use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span> <span data-ttu-id="ad2a5-189">이 메서드를 사용 하 여 여러 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-189">You can use this method to run background jobs on multiple computers.</span></span>

<span data-ttu-id="ad2a5-190">Start-Job 명령을 원격으로 실행 하는 경우 작업 개체가 원격 컴퓨터에 만들어지고 작업 결과가 원격 컴퓨터에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-190">When you run a Start-Job command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="ad2a5-191">작업의 관점에서 보면 모든 작업은 로컬입니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-191">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="ad2a5-192">원격 컴퓨터에서 로컬 작업을 관리 하기 위해 원격으로 명령을 실행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-192">You are just running commands remotely to manage a local job on the remote computer.</span></span>

#### <a name="step-1-invoke-command-start-job"></a><span data-ttu-id="ad2a5-193">1 단계: 명령 시작-작업</span><span class="sxs-lookup"><span data-stu-id="ad2a5-193">STEP 1: INVOKE-COMMAND START-JOB</span></span>

<span data-ttu-id="ad2a5-194">Invoke-Command cmdlet을 사용 하 여 원격 컴퓨터에서 Start-Job 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-194">Use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span>

<span data-ttu-id="ad2a5-195">이 명령에는 PSSession (영구 연결)이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-195">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="ad2a5-196">Invoke-Command의 ComputerName 매개 변수를 사용 하 여 임시 연결을 설정 하는 경우 작업 개체가 반환 될 때 Invoke-Command 명령이 완료 된 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-196">If you use the ComputerName parameter of Invoke-Command to establish a temporary connection, the Invoke-Command command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="ad2a5-197">결과적으로 임시 연결이 닫히고 작업이 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-197">As a result, the temporary connection is closed, and the job is canceled.</span></span>

<span data-ttu-id="ad2a5-198">다음 명령은 New-PSSession cmdlet을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-198">The following command uses the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="ad2a5-199">이 명령은 PSSession을 \$ s 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-199">The command saves the PSSession in the \$s variable.</span></span>

```powershell
$s = new-pssession -computername Server01
```

<span data-ttu-id="ad2a5-200">다음 명령은 Invoke-Command cmdlet을 사용 하 여 PSSession에서 Start-Job 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-200">The next command uses the Invoke-Command cmdlet to run a Start-Job command in the PSSession.</span></span> <span data-ttu-id="ad2a5-201">Start-Job 명령과 Get-Eventlog 명령은 중괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-201">The Start-Job command and the Get-Eventlog command are enclosed in braces.</span></span>

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

<span data-ttu-id="ad2a5-202">결과는 다음 예제 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-202">The results resemble the following sample output.</span></span>

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

<span data-ttu-id="ad2a5-203">Start-Job 명령을 원격으로 실행 하는 경우 Invoke-Command는 Start-Job 반환 하는 것과 동일한 유형의 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-203">When you run a Start-Job command remotely, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="ad2a5-204">작업 개체를 변수에 저장 하거나 Get-Job 명령을 사용 하 여 작업을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-204">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="ad2a5-205">Location 속성의 값은 작업이 Server01 컴퓨터에서 실행 된 경우에도 "LocalHost" 라는 로컬 컴퓨터에서 실행 된 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-205">Note that the value of the Location property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="ad2a5-206">작업 개체는 Server01 컴퓨터에 생성 되 고 작업은 동일한 컴퓨터에서 실행 되기 때문에 로컬 백그라운드 작업으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-206">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

#### <a name="step-2-invoke-command-get-job"></a><span data-ttu-id="ad2a5-207">2 단계: 명령 호출 가져오기</span><span class="sxs-lookup"><span data-stu-id="ad2a5-207">STEP 2: INVOKE-COMMAND GET-JOB</span></span>

<span data-ttu-id="ad2a5-208">원격 백그라운드 작업을 관리 하려면 Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-208">To manage a remote background job, use the Job cmdlets.</span></span> <span data-ttu-id="ad2a5-209">작업 개체가 원격 컴퓨터에 있기 때문에 작업 결과를 가져오기, 중지, 대기 또는 검색 하기 위해 원격 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-209">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

<span data-ttu-id="ad2a5-210">작업이 완료 되었는지 확인 하려면 Invoke-Command 명령을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession에서 Get-Job 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-210">To see if the job is complete, use an Invoke-Command command to run a Get-Job command in the PSSession that is connected to the Server01 computer.</span></span>

```powershell
invoke-command -session $s -scriptblock {get-job}
```

<span data-ttu-id="ad2a5-211">작업 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-211">The command returns a job object.</span></span> <span data-ttu-id="ad2a5-212">작업 개체의 State 속성은 명령이 성공적으로 완료 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-212">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a><span data-ttu-id="ad2a5-213">3 단계: 명령 수신-작업</span><span class="sxs-lookup"><span data-stu-id="ad2a5-213">STEP 3: INVOKE-COMMAND RECEIVE-JOB</span></span>

<span data-ttu-id="ad2a5-214">작업의 결과를 가져오려면 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에 연결 된 PSSession에서 Receive-Job 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-214">To get the results of the job, use the Invoke-Command cmdlet to run a Receive-Job command in the PSSession that is connected to the Server01 computer.</span></span>

<span data-ttu-id="ad2a5-215">다음 명령은 Receive-Job cmdlet을 사용 하 여 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-215">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="ad2a5-216">세션 ID를 사용 하 여 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-216">It uses the session ID to identify the job.</span></span> <span data-ttu-id="ad2a5-217">이 명령은 결과 변수에 작업 결과를 저장 \$ 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-217">This command saves the job results in the \$results variable.</span></span> <span data-ttu-id="ad2a5-218">이는 Receive-Job의 Keep 매개 변수를 사용 하 여 결과를 원격 컴퓨터의 작업 캐시에 보관 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-218">It uses the Keep parameter of Receive-Job to keep the result in the job cache on the remote computer.</span></span>

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

<span data-ttu-id="ad2a5-219">로컬 또는 원격 컴퓨터의 파일로 결과를 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-219">You can also redirect the results to a file on the local or remote computer.</span></span>
<span data-ttu-id="ad2a5-220">다음 명령은 리디렉션 연산자를 사용 하 여 Server01 컴퓨터의 파일에 결과를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad2a5-220">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a><span data-ttu-id="ad2a5-221">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad2a5-221">SEE ALSO</span></span>

[<span data-ttu-id="ad2a5-222">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="ad2a5-222">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="ad2a5-223">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="ad2a5-223">about_Job_Details</span></span>](about_Job_Details.md)

[<span data-ttu-id="ad2a5-224">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ad2a5-224">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="ad2a5-225">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="ad2a5-225">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="ad2a5-226">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="ad2a5-226">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="ad2a5-227">Start-Job</span><span class="sxs-lookup"><span data-stu-id="ad2a5-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)

[<span data-ttu-id="ad2a5-228">Get-Job</span><span class="sxs-lookup"><span data-stu-id="ad2a5-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)

[<span data-ttu-id="ad2a5-229">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="ad2a5-229">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)

[<span data-ttu-id="ad2a5-230">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="ad2a5-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)

[<span data-ttu-id="ad2a5-231">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="ad2a5-231">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)

[<span data-ttu-id="ad2a5-232">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad2a5-232">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="ad2a5-233">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad2a5-233">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="ad2a5-234">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="ad2a5-234">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
