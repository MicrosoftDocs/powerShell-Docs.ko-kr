---
description: PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다. 스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: ba6251a195d3efdebd427b3f705386336b069211
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524844"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="ff72a-105">스레드 작업 정보</span><span class="sxs-lookup"><span data-stu-id="ff72a-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="ff72a-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ff72a-106">Short description</span></span>

<span data-ttu-id="ff72a-107">PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="ff72a-108">스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="ff72a-109">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-109">Long description</span></span>

<span data-ttu-id="ff72a-110">PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-110">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="ff72a-111">PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-111">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="ff72a-112">`RemoteJob` -명령 및 스크립트가 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-112">`RemoteJob` - Commands and scripts run in a remote session.</span></span> <span data-ttu-id="ff72a-113">자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff72a-113">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="ff72a-114">`BackgroundJob` -명령 및 스크립트는 로컬 컴퓨터에서 별도의 프로세스로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-114">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="ff72a-115">자세한 내용은 [about_Jobs](about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff72a-115">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="ff72a-116">`PSTaskJob` 또는 `ThreadJob` -명령 및 스크립트는 로컬 컴퓨터에서 동일한 프로세스 내에서 별도의 스레드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-116">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span>

<span data-ttu-id="ff72a-117">스레드 기반 작업은 여러 스레드에서 동일한 프로세스로 실행 되기 때문에 원격 및 백그라운드 작업 만큼 강력 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-117">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="ff72a-118">한 작업에 프로세스를 중단 하는 중대 한 오류가 있는 경우 프로세스의 다른 모든 작업이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-118">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="ff72a-119">그러나 스레드 기반 작업에는 오버 헤드가 적게 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-119">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="ff72a-120">Remoting 계층 또는 serialization은 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-120">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="ff72a-121">결과 개체는 현재 세션의 라이브 개체에 대 한 참조로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-121">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="ff72a-122">이러한 오버 헤드가 없으면 스레드 기반 작업은 더 빠르게 실행 되 고 다른 작업 유형에 비해 리소스를 적게 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-122">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff72a-123">작업을 만든 부모 세션도 작업 상태를 모니터링 하 고 파이프라인 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-123">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="ff72a-124">작업이 완료 된 상태에 도달 하면 부모 프로세스가 작업 자식 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-124">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="ff72a-125">부모 세션이 종료 되 면 모든 실행 중인 자식 작업은 자식 프로세스와 함께 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-125">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="ff72a-126">이러한 상황을 해결 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-126">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="ff72a-127">`Invoke-Command`를 사용 하 여 연결 되지 않은 세션에서 실행 되는 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-127">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="ff72a-128">자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff72a-128">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="ff72a-129">`Start-Process`작업 대신 새 프로세스를 만들려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-129">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="ff72a-130">자세한 내용은 [시작-처리](xref:Microsoft.PowerShell.Management.Start-Process)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff72a-130">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="how-to-start-and-manage-thread-based-jobs"></a><span data-ttu-id="ff72a-131">스레드 기반 작업을 시작 하 고 관리 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ff72a-131">How to start and manage thread-based jobs</span></span>

<span data-ttu-id="ff72a-132">스레드 기반 작업을 시작 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-132">There are two ways to start thread-based jobs:</span></span>

- <span data-ttu-id="ff72a-133">`Start-ThreadJob` - **Threadjob** 모듈에서</span><span class="sxs-lookup"><span data-stu-id="ff72a-133">`Start-ThreadJob` - from the **ThreadJob** module</span></span>
- <span data-ttu-id="ff72a-134">`ForEach-Object -Parallel -AsJob` -병렬 기능이 PowerShell 7.0에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-134">`ForEach-Object -Parallel -AsJob` - the parallel feature was added in PowerShell 7.0</span></span>

<span data-ttu-id="ff72a-135">[About_Jobs](about_Jobs.md) 에 설명 된 것과 동일한 **작업** cmdlet을 사용 하 여 스레드 기반 작업을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-135">Use the same **Job** cmdlets described in [about_Jobs](about_Jobs.md) to manage thread-based jobs.</span></span>

### <a name="using-start-threadjob"></a><span data-ttu-id="ff72a-136">`Start-ThreadJob` 사용</span><span class="sxs-lookup"><span data-stu-id="ff72a-136">Using `Start-ThreadJob`</span></span>

<span data-ttu-id="ff72a-137">**Threadjob** 모듈은 먼저 PowerShell 6과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-137">The **ThreadJob** module first shipped with PowerShell 6.</span></span> <span data-ttu-id="ff72a-138">Windows PowerShell 5.1에 대 한 PowerShell 갤러리에서 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-138">It can also be installed from the PowerShell Gallery for Windows PowerShell 5.1.</span></span>

<span data-ttu-id="ff72a-139">로컬 컴퓨터에서 스레드 작업을 시작 하려면 중괄호 `Start-ThreadJob` ()로 묶인 명령이 나 스크립트를 사용 하 여 cmdlet을 사용 `{ }` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-139">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet with a command or script enclosed in curly braces (`{ }`).</span></span>

<span data-ttu-id="ff72a-140">다음 예제에서는 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 스레드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-140">The following example starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="ff72a-141">`Start-ThreadJob`명령은 `ThreadJob` 실행 중인 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-141">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="ff72a-142">작업 개체에는 현재 실행 상태를 포함 하 여 작업에 대 한 유용한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-142">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="ff72a-143">결과를 생성 하는 중에 작업의 결과를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-143">It collects the results of the job as the results are being generated.</span></span>

### <a name="using-foreach-object--parallel--asjob"></a><span data-ttu-id="ff72a-144">`ForEach-Object -Parallel -AsJob` 사용</span><span class="sxs-lookup"><span data-stu-id="ff72a-144">Using `ForEach-Object -Parallel -AsJob`</span></span>

<span data-ttu-id="ff72a-145">PowerShell 7.0이 cmdlet에 새 매개 변수 집합을 추가 했습니다 `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="ff72a-145">PowerShell 7.0 added a new parameter set to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="ff72a-146">새 매개 변수를 사용 하 여 병렬 스레드에서 스크립트 블록을 PowerShell 작업으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-146">The new parameters allow you to run script blocks in parallel threads as PowerShell jobs.</span></span>

<span data-ttu-id="ff72a-147">데이터를로 파이프 할 수 있습니다 `ForEach-Object -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="ff72a-147">You can pipe data to `ForEach-Object -Parallel`.</span></span> <span data-ttu-id="ff72a-148">데이터는 병렬로 실행 되는 스크립트 블록으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-148">The data is passed to the script block that is run in parallel.</span></span> <span data-ttu-id="ff72a-149">`-AsJob`매개 변수는 각 병렬 스레드에 대해 작업 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-149">The `-AsJob` parameter creates jobs objects for each of the parallel threads.</span></span>

<span data-ttu-id="ff72a-150">다음 명령은 명령으로 파이프 된 각 입력 값에 대 한 자식 작업을 포함 하는 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-150">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="ff72a-151">각 자식 작업은 `Write-Output` 파이프 된 입력 값을 인수로 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-151">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="ff72a-152">`ForEach-Object -Parallel`이 명령은 파이프 된 `PSTaskJob` 각 입력 값에 대 한 자식 작업을 포함 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-152">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="ff72a-153">작업 개체에는 자식 작업 실행 상태에 대 한 유용한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-153">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="ff72a-154">결과를 생성 하는 중에 자식 작업의 결과를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-154">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="ff72a-155">작업이 완료 될 때까지 대기 하 고 작업 결과를 검색 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ff72a-155">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="ff72a-156">PowerShell 작업 cmdlet (예: 및)을 `Wait-Job` 사용 `Receive-Job` 하 여 작업이 완료 될 때까지 기다린 다음 작업에 의해 생성 된 모든 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-156">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="ff72a-157">다음 명령은 명령을 실행 하는 스레드 작업을 시작 하 고 `Get-Process` 명령이 완료 될 때까지 대기한 다음 명령에 의해 생성 된 모든 데이터 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-157">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="ff72a-158">다음 명령은 파이프 된 각 입력에 대해 명령을 실행 하는 작업을 시작한 `Write-Output` 다음 모든 자식 작업이 완료 될 때까지 대기 하 고, 마지막으로 자식 작업에 의해 생성 된 모든 데이터 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-158">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="ff72a-159">이 `Receive-Job` cmdlet은 자식 작업의 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-159">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="ff72a-160">각 자식 작업은 병렬로 실행 되므로 생성 된 결과의 순서는 보장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-160">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="ff72a-161">스레드 작업 성능</span><span class="sxs-lookup"><span data-stu-id="ff72a-161">Thread job performance</span></span>

<span data-ttu-id="ff72a-162">스레드 작업은 다른 유형의 작업 보다 더 빠르고 가벼운 가중치입니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-162">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="ff72a-163">하지만 작업에서 수행 하는 작업에 비해 오버 헤드가 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-163">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="ff72a-164">PowerShell은 세션에서 명령 및 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-164">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="ff72a-165">세션에서 한 번에 하나의 명령 또는 스크립트만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-165">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="ff72a-166">따라서 여러 작업을 실행할 때 각 작업은 별도의 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-166">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="ff72a-167">각 세션은 오버 헤드에 기여 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-167">Each session contributes to the overhead.</span></span>

<span data-ttu-id="ff72a-168">스레드 작업은 수행 하는 작업이 작업을 실행 하는 데 사용 되는 세션의 오버 헤드 보다 큰 경우 최적의 성능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-168">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="ff72a-169">이 조건을 충족 하는 두 가지 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-169">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="ff72a-170">작업은 계산 집약적입니다. 여러 스레드 작업에서 스크립트를 실행 하면 여러 프로세서 코어를 활용 하 여 더 빨리 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-170">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="ff72a-171">작업은 i/o 또는 원격 호출 결과를 대기 하는 데 시간을 소비 하는 스크립트를 대기 하는 중요 한 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-171">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="ff72a-172">병렬로 실행 하는 것은 일반적으로 순차적으로 실행 하는 경우 보다 더 빨리 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-172">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

<span data-ttu-id="ff72a-173">위의 첫 번째 예제에서는 간단한 문자열 쓰기를 수행 하는 1000 스레드 작업을 만드는 foreach 루프를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-173">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="ff72a-174">작업 오버 헤드로 인해 완료 하는 데 36 초 이상이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-174">Due to job overhead, it takes over 36 seconds to complete.</span></span>

<span data-ttu-id="ff72a-175">두 번째 예제는 cmdlet을 실행 `ForEach` 하 여 동일한 1000 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-175">The second example runs the `ForEach` cmdlet to do the same 1000 operations.</span></span>
<span data-ttu-id="ff72a-176">이번에는 `ForEach-Object` 작업 오버 헤드 없이 단일 스레드에서 순차적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-176">This time, `ForEach-Object` runs sequentially, on a single thread, without any job overhead.</span></span> <span data-ttu-id="ff72a-177">이는 단지 7 밀리초 안에 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-177">It completes in a mere 7 milliseconds.</span></span>

<span data-ttu-id="ff72a-178">다음 예제에서는 10 개의 개별 시스템 로그에 대해 최대 5000 개의 항목이 수집 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-178">In the following example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="ff72a-179">스크립트에는 많은 로그 읽기가 포함 되므로 작업을 병렬로 수행 하는 것이 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-179">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span>

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

<span data-ttu-id="ff72a-180">작업을 병렬로 실행 하는 경우 스크립트가 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-180">The script completes in half the time when the jobs are run in parallel.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="ff72a-181">스레드 작업 및 변수</span><span class="sxs-lookup"><span data-stu-id="ff72a-181">Thread jobs and variables</span></span>

<span data-ttu-id="ff72a-182">여러 가지 방법으로 스레드 기반 작업에 값을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-182">There are multiple ways to pass values into the thread-based jobs.</span></span>

<span data-ttu-id="ff72a-183">`Start-ThreadJob` 는 cmdlet으로 파이프 되는 변수, 키워드를 통해 스크립트 블록으로 전달 `$using` 되거나 **argumentlist** 매개 변수를 통해 전달 되는 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-183">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="ff72a-184">`ForEach-Object -Parallel` 변수에서 파이프를 수락 하 고 키워드를 통해 스크립트 블록에 직접 전달 되는 변수를 허용 `$using` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-184">`ForEach-Object -Parallel` accepts piped in variables, and variables passed directly to the script block via the `$using` keyword.</span></span>

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="ff72a-185">스레드 작업은 동일한 프로세스에서 실행 되므로 작업에 전달 되는 변수 참조 형식은 신중 하 게 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-185">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="ff72a-186">스레드로부터 안전한 개체가 아닌 경우에는 할당 되지 않아야 하 고 메서드 및 속성을 호출 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-186">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

<span data-ttu-id="ff72a-187">다음 예제에서는 스레드로부터 안전한 .NET `ConcurrentDictionary` 개체를 모든 자식 작업에 전달 하 여 고유 하 게 명명 된 프로세스 개체를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-187">The following example passes a thread-safe .NET `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="ff72a-188">스레드로부터 안전한 개체 이므로 작업이 프로세스에서 동시에 실행 되는 동안 안전 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff72a-188">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

## <a name="see-also"></a><span data-ttu-id="ff72a-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff72a-189">See also</span></span>

- [<span data-ttu-id="ff72a-190">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="ff72a-190">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="ff72a-191">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="ff72a-191">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="ff72a-192">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="ff72a-192">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="ff72a-193">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ff72a-193">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="ff72a-194">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="ff72a-194">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="ff72a-195">Start-Job</span><span class="sxs-lookup"><span data-stu-id="ff72a-195">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="ff72a-196">Get-Job</span><span class="sxs-lookup"><span data-stu-id="ff72a-196">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="ff72a-197">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="ff72a-197">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="ff72a-198">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="ff72a-198">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="ff72a-199">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="ff72a-199">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="ff72a-200">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="ff72a-200">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
