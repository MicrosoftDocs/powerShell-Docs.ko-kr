---
description: PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다. 스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 4951ac2c14c0685fbf2ead16bc52c64096231260
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93224594"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="f49e4-105">스레드 작업 정보</span><span class="sxs-lookup"><span data-stu-id="f49e4-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="f49e4-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="f49e4-106">Short description</span></span>

<span data-ttu-id="f49e4-107">PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="f49e4-108">스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="f49e4-109">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-109">Long description</span></span>

<span data-ttu-id="f49e4-110">이 문서에서는 로컬 컴퓨터의 PowerShell에서 스레드 작업을 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-110">This article explains how to run thread jobs in PowerShell on a local computer.</span></span>
<span data-ttu-id="f49e4-111">로컬 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f49e4-111">For information about running background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span>

<span data-ttu-id="f49e4-112">Cmdlet을 사용 하 여 스레드 작업을 시작 `Start-ThreadJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-112">Start a thread job by using the `Start-ThreadJob` cmdlet.</span></span> <span data-ttu-id="f49e4-113">이 cmdlet은 PowerShell과 함께 제공 되는 **Threadjob** 모듈에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-113">This cmdlet is available in the **ThreadJob** module that ships with PowerShell.</span></span>
<span data-ttu-id="f49e4-114">`Start-ThreadJob` 실행 중인 명령이 나 스크립트를 캡슐화 하 고 모든 PowerShell 작업에서 cmdlet을 조작 하는 데 사용할 수 있는 단일 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-114">`Start-ThreadJob` returns a single job object that encapsulates the running command or script, and can be used with all PowerShell job manipulating cmdlets.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="f49e4-115">작업 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f49e4-115">The job cmdlets</span></span>

|<span data-ttu-id="f49e4-116">cmdlet</span><span class="sxs-lookup"><span data-stu-id="f49e4-116">Cmdlet</span></span>           |<span data-ttu-id="f49e4-117">Description</span><span class="sxs-lookup"><span data-stu-id="f49e4-117">Description</span></span>                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|<span data-ttu-id="f49e4-118">로컬 컴퓨터에서 스레드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-118">Starts a thread job on a local computer.</span></span>               |
|`Get-Job`        |<span data-ttu-id="f49e4-119">현재 세션에서 시작 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-119">Gets the jobs that were started in the current session.</span></span>|
|`Receive-Job`    |<span data-ttu-id="f49e4-120">작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-120">Gets the results of jobs.</span></span>                              |
|`Stop-Job`       |<span data-ttu-id="f49e4-121">실행 중인 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-121">Stops a running job.</span></span>                                   |
|`Wait-Job`       |<span data-ttu-id="f49e4-122">하나 또는 모든 작업이 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-122">Suppresses the command prompt until one or all jobs are</span></span>|
|                 |<span data-ttu-id="f49e4-123">완료.</span><span class="sxs-lookup"><span data-stu-id="f49e4-123">complete.</span></span>                                              |
|`Remove-Job`     |<span data-ttu-id="f49e4-124">작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-124">Deletes a job.</span></span>                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a><span data-ttu-id="f49e4-125">로컬 컴퓨터에서 스레드 작업을 시작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="f49e4-125">How to start a thread job on the local computer</span></span>

<span data-ttu-id="f49e4-126">로컬 컴퓨터에서 스레드 작업을 시작 하려면 cmdlet을 사용 `Start-ThreadJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-126">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet.</span></span>

<span data-ttu-id="f49e4-127">명령을 작성 하려면 `Start-ThreadJob` 명령이 나 스크립트를 중괄호 ()로 묶습니다 `{ }` .</span><span class="sxs-lookup"><span data-stu-id="f49e4-127">To write a `Start-ThreadJob` command, enclose the command or script the job runs in curly braces (`{ }`).</span></span>

<span data-ttu-id="f49e4-128">다음 명령은 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 스레드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-128">The following command starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="f49e4-129">`Start-ThreadJob`명령은 `ThreadJob` 실행 중인 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-129">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="f49e4-130">작업 개체에는 현재 실행 상태를 포함 하 여 작업에 대 한 유용한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-130">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="f49e4-131">결과를 생성 하는 중에 작업의 결과를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-131">It collects the results of the job as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="f49e4-132">작업이 완료 될 때까지 대기 하 고 작업 결과를 검색 하는 방법</span><span class="sxs-lookup"><span data-stu-id="f49e4-132">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="f49e4-133">PowerShell 작업 cmdlet (예: 및)을 `Wait-Job` 사용 `Receive-Job` 하 여 작업이 완료 될 때까지 기다린 다음 작업에 의해 생성 된 모든 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-133">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="f49e4-134">다음 명령은 명령을 실행 하는 스레드 작업을 시작 하 고 `Get-Process` 명령이 완료 될 때까지 대기한 다음 명령에 의해 생성 된 모든 데이터 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-134">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

## <a name="powershell-concurrency-and-jobs"></a><span data-ttu-id="f49e4-135">PowerShell 동시성 및 작업</span><span class="sxs-lookup"><span data-stu-id="f49e4-135">PowerShell concurrency and jobs</span></span>

<span data-ttu-id="f49e4-136">PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-136">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="f49e4-137">PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 기반 솔루션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-137">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="f49e4-138">작업</span><span class="sxs-lookup"><span data-stu-id="f49e4-138">Job</span></span>            |<span data-ttu-id="f49e4-139">Description</span><span class="sxs-lookup"><span data-stu-id="f49e4-139">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="f49e4-140">명령 및 스크립트가 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-140">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="f49e4-141">명령 및 스크립트가 로컬에서 별도의 프로세스로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-141">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="f49e4-142">할당합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-142">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="f49e4-143">명령 및 스크립트가 동일한 내에서 별도의 스레드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-143">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="f49e4-144">로컬 컴퓨터의 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-144">process on the local machine.</span></span>                                |

<span data-ttu-id="f49e4-145">각 유형의 작업에는 장점과 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-145">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="f49e4-146">별도의 컴퓨터나 별도의 프로세스에서 원격으로 스크립트를 실행 하는 것은 매우 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-146">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="f49e4-147">모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 클라이언트에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-147">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="f49e4-148">하지만 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-148">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="f49e4-149">원격 세션과 주고 받은 모든 개체는 클라이언트와 대상 세션 간에 전달 될 때 serialize 된 다음 deserialize 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-149">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="f49e4-150">Serialization 작업은 복잡 한 데이터 개체에 많은 계산 및 메모리 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-150">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

## <a name="powershell-thread-based-jobs"></a><span data-ttu-id="f49e4-151">PowerShell 스레드 기반 작업</span><span class="sxs-lookup"><span data-stu-id="f49e4-151">PowerShell thread based jobs</span></span>

<span data-ttu-id="f49e4-152">스레드 기반 작업은 여러 스레드에서 동일한 프로세스로 실행 되기 때문에 원격 및 백그라운드 작업 만큼 강력 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-152">Thread based jobs are not as robust as Remote and Background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="f49e4-153">한 작업에 프로세스를 중단 하는 중대 한 오류가 있는 경우 프로세스의 다른 작업도 모두 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-153">If one job has a critical error that crashes the process, then all other jobs in the process will also fail.</span></span>

<span data-ttu-id="f49e4-154">그러나 스레드 기반 작업의 오버 헤드가 훨씬 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-154">However, thread-based jobs have much less overhead.</span></span> <span data-ttu-id="f49e4-155">원격 계층 또는 serialization을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-155">They don't need to use the remoting layer or serialization.</span></span> <span data-ttu-id="f49e4-156">따라서 스레드 기반 작업은 훨씬 더 빨리 실행 되 고 다른 작업 유형에 비해 훨씬 더 작은 리소스를 사용 하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-156">The result is that thread-based jobs tend to run much faster and use far less resources than the other job types.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="f49e4-157">스레드 작업 성능</span><span class="sxs-lookup"><span data-stu-id="f49e4-157">Thread job performance</span></span>

<span data-ttu-id="f49e4-158">스레드 작업은 다른 유형의 작업 보다 더 빠르고 가벼운 가중치입니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-158">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="f49e4-159">하지만 작업에서 수행 하는 작업에 비해 오버 헤드가 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-159">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="f49e4-160">PowerShell은 세션에서 명령 및 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-160">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="f49e4-161">세션에서 한 번에 하나의 명령 또는 스크립트만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-161">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="f49e4-162">따라서 여러 작업을 실행할 때 각 작업은 별도의 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-162">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="f49e4-163">각 세션은 오버 헤드에 기여 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-163">Each session contributes to the overhead.</span></span>

<span data-ttu-id="f49e4-164">스레드 작업은 수행 하는 작업이 작업을 실행 하는 데 사용 되는 세션의 오버 헤드 보다 큰 경우 최적의 성능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-164">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="f49e4-165">이 조건을 충족 하는 두 가지 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-165">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="f49e4-166">작업은 계산 집약적입니다. 여러 스레드 작업에서 스크립트를 실행 하면 여러 프로세서 코어를 활용 하 여 더 빨리 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-166">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="f49e4-167">작업은 i/o 또는 원격 호출 결과를 대기 하는 데 시간을 소비 하는 스크립트를 대기 하는 중요 한 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-167">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="f49e4-168">병렬로 실행 하는 것은 일반적으로 순차적으로 실행 하는 경우 보다 더 빨리 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-168">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

<span data-ttu-id="f49e4-169">위의 첫 번째 예제에서는 간단한 문자열 쓰기를 수행 하는 1000 스레드 작업을 만드는 foreach 루프를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-169">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="f49e4-170">작업 오버 헤드로 인해 완료 하는 데 33 초 이상이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-170">Due to job overhead, it takes over 33 seconds to complete.</span></span>

<span data-ttu-id="f49e4-171">두 번째 예제에서는 cmdlet을 실행 `ForEach` 하 여 동일한 1000 작업을 수행 하 고 각 문자열 쓰기가 작업 오버 헤드 없이 순차적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-171">The second example runs the `ForEach` cmdlet to do the same 1000 operations and each string write is executed sequentially without any job overhead.</span></span> <span data-ttu-id="f49e4-172">25 밀리초 안에 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-172">It completes in a mere 25 milliseconds.</span></span>

```powershell
$logNames.count
10

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

<span data-ttu-id="f49e4-173">위의 예제에서는 10 개의 개별 시스템 로그에 대해 최대 5000 개의 항목이 수집 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-173">In the above example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="f49e4-174">스크립트에는 많은 로그 읽기가 포함 되므로 작업을 병렬로 수행 하는 것이 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-174">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span> <span data-ttu-id="f49e4-175">그리고 작업은 스크립트를 순차적으로 실행 하는 것 처럼 두 번 이상 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-175">And the job completes over twice as fast as when the script is run sequentially.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="f49e4-176">스레드 작업 및 변수</span><span class="sxs-lookup"><span data-stu-id="f49e4-176">Thread jobs and variables</span></span>

<span data-ttu-id="f49e4-177">변수는 다양 한 방식으로 스레드 작업에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-177">Variables are passed into thread jobs in various ways.</span></span>

<span data-ttu-id="f49e4-178">`Start-ThreadJob` 는 cmdlet으로 파이프 되는 변수, 키워드를 통해 스크립트 블록으로 전달 `$using` 되거나 **argumentlist** 매개 변수를 통해 전달 되는 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-178">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="f49e4-179">스레드 작업은 동일한 프로세스에서 실행 되므로 작업에 전달 되는 변수 참조 형식은 신중 하 게 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-179">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="f49e4-180">스레드로부터 안전한 개체가 아닌 경우에는 할당 되지 않아야 하 고 메서드 및 속성을 호출 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-180">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

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

<span data-ttu-id="f49e4-181">위의 예제에서는 `ConcurrentDictionary` 모든 자식 작업에 스레드로부터 안전한 dotNet 개체를 전달 하 여 고유 하 게 명명 된 프로세스 개체를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-181">The above example passes a thread safe dotNet `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="f49e4-182">스레드로부터 안전한 개체 이므로 작업이 프로세스에서 동시에 실행 되는 동안 안전 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49e4-182">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

## <a name="see-also"></a><span data-ttu-id="f49e4-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f49e4-183">See also</span></span>

- [<span data-ttu-id="f49e4-184">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="f49e4-184">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="f49e4-185">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="f49e4-185">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="f49e4-186">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="f49e4-186">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="f49e4-187">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f49e4-187">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="f49e4-188">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="f49e4-188">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="f49e4-189">Start-Job</span><span class="sxs-lookup"><span data-stu-id="f49e4-189">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="f49e4-190">Get-Job</span><span class="sxs-lookup"><span data-stu-id="f49e4-190">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="f49e4-191">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="f49e4-191">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="f49e4-192">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f49e4-192">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="f49e4-193">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f49e4-193">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="f49e4-194">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="f49e4-194">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
