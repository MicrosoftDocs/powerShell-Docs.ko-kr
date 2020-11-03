---
description: PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다. 스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: d3f7c2754a2e54bc1b6f9fb95d1cf6ce2fed5b9b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93224593"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="1e1df-105">스레드 작업 정보</span><span class="sxs-lookup"><span data-stu-id="1e1df-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="1e1df-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="1e1df-106">Short description</span></span>

<span data-ttu-id="1e1df-107">PowerShell 스레드 기반 작업에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="1e1df-108">스레드 작업은 현재 세션 프로세스 내에서 별도의 스레드에서 명령 또는 식을 실행 하는 백그라운드 작업의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="1e1df-109">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-109">Long description</span></span>

<span data-ttu-id="1e1df-110">이 문서에서는 로컬 컴퓨터의 PowerShell에서 스레드 작업을 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-110">This article explains how to run thread jobs in PowerShell on a local computer.</span></span>
<span data-ttu-id="1e1df-111">로컬 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1e1df-111">For information about running background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span>

<span data-ttu-id="1e1df-112">다음 두 가지 방법 중 하나로 스레드 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-112">You can start a thread job in one of two ways.</span></span>

<span data-ttu-id="1e1df-113">첫 번째 방법은 cmdlet을 사용 하는 것입니다 `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="1e1df-113">The first way is with the `Start-ThreadJob` cmdlet.</span></span> <span data-ttu-id="1e1df-114">이 cmdlet은 PowerShell과 함께 제공 되는 **Threadjob** 모듈에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-114">This cmdlet is available in the **ThreadJob** module that ships with PowerShell.</span></span> <span data-ttu-id="1e1df-115">`Start-ThreadJob` 실행 중인 명령이 나 스크립트를 캡슐화 하 고 모든 PowerShell 작업에서 cmdlet을 조작 하는 데 사용할 수 있는 단일 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-115">`Start-ThreadJob` returns a single job object that encapsulates the running command or script, and can be used with all PowerShell job manipulating cmdlets.</span></span>

<span data-ttu-id="1e1df-116">두 번째 방법은 cmdlet을 사용 하 고 매개 변수 `ForEach-Object` `-Parallel` 스위치와 매개 변수 스크립트 블록 인수를 함께 사용 하는 것입니다 `-AsJob` .</span><span class="sxs-lookup"><span data-stu-id="1e1df-116">The second way is with the `ForEach-Object` cmdlet, with the `-Parallel` parameter script block argument along with the `-AsJob` parameter switch.</span></span> <span data-ttu-id="1e1df-117">이 cmdlet은 cmdlet에 파이프 된 각 입력에 대 한 자식 작업을 포함 하는 단일 (부모) 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-117">This cmdlet returns a single (parent) job object that contains a child job for each input piped to the cmdlet.</span></span> <span data-ttu-id="1e1df-118">각 자식 작업은 `-ThrottleLimit` 지정 된 시간에 실행 되는 자식 작업 수에 대 한 () 제한을 사용 하 여 별도의 스레드에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-118">Each child job runs script in a separate thread with a (`-ThrottleLimit`) limit to how many child jobs run at a given time.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="1e1df-119">작업 CMDLET</span><span class="sxs-lookup"><span data-stu-id="1e1df-119">THE JOB CMDLETS</span></span>

|<span data-ttu-id="1e1df-120">cmdlet</span><span class="sxs-lookup"><span data-stu-id="1e1df-120">Cmdlet</span></span>           |<span data-ttu-id="1e1df-121">Description</span><span class="sxs-lookup"><span data-stu-id="1e1df-121">Description</span></span>                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|<span data-ttu-id="1e1df-122">로컬 컴퓨터에서 스레드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-122">Starts a thread job on a local computer.</span></span>               |
|`ForEach-Object` |<span data-ttu-id="1e1df-123">각 파이프 입력 개체에 대 한 스레드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-123">Starts thread jobs for each piped input object, when</span></span>   |
|                 |<span data-ttu-id="1e1df-124">-Parallel 및-AsJob 매개 변수와 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-124">used with -Parallel and -AsJob parameters.</span></span>             |
|`Get-Job`        |<span data-ttu-id="1e1df-125">현재 세션에서 시작 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-125">Gets the jobs that were started in the current session.</span></span>|
|`Receive-Job`    |<span data-ttu-id="1e1df-126">작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-126">Gets the results of jobs.</span></span>                              |
|`Stop-Job`       |<span data-ttu-id="1e1df-127">실행 중인 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-127">Stops a running job.</span></span>                                   |
|`Wait-Job`       |<span data-ttu-id="1e1df-128">하나 또는 모든 작업이 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-128">Suppresses the command prompt until one or all jobs are</span></span>|
|                 |<span data-ttu-id="1e1df-129">완료.</span><span class="sxs-lookup"><span data-stu-id="1e1df-129">complete.</span></span>                                              |
|`Remove-Job`     |<span data-ttu-id="1e1df-130">작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-130">Deletes a job.</span></span>                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a><span data-ttu-id="1e1df-131">로컬 컴퓨터에서 스레드 작업을 시작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e1df-131">How to start a thread job on the local computer</span></span>

<span data-ttu-id="1e1df-132">로컬 컴퓨터에서 스레드 작업을 시작 하려면 cmdlet을 사용 `Start-ThreadJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-132">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet.</span></span>

<span data-ttu-id="1e1df-133">명령을 작성 하려면 `Start-ThreadJob` 명령이 나 스크립트를 중괄호 ()로 묶습니다 `{ }` .</span><span class="sxs-lookup"><span data-stu-id="1e1df-133">To write a `Start-ThreadJob` command, enclose the command or script the job runs in curly braces (`{ }`).</span></span>

<span data-ttu-id="1e1df-134">다음 명령은 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 스레드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-134">The following command starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="1e1df-135">`Start-ThreadJob`명령은 `ThreadJob` 실행 중인 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-135">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="1e1df-136">작업 개체에는 현재 실행 상태를 포함 하 여 작업에 대 한 유용한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-136">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="1e1df-137">결과를 생성 하는 중에 작업의 결과를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-137">It collects the results of the job as the results are being generated.</span></span>

<span data-ttu-id="1e1df-138">명령을 작성 하려면 `ForEach-Object -Parallel` 데이터를 명령에 파이프 하 고 명령이 나 스크립트를 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="1e1df-138">To write a `ForEach-Object -Parallel` command, pipe data to the command and enclose the command or script the job runs in curly braces(`{}`).</span></span> <span data-ttu-id="1e1df-139">`-AsJob`작업 개체가 반환 되도록 매개 변수 스위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-139">Use the `-AsJob` parameter switch so that a job object is returned.</span></span>

<span data-ttu-id="1e1df-140">다음 명령은 명령으로 파이프 된 각 입력 값에 대 한 자식 작업을 포함 하는 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-140">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="1e1df-141">각 자식 작업은 `Write-Output` 파이프 된 입력 값을 인수로 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-141">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="1e1df-142">`ForEach-Object -Parallel`이 명령은 파이프 된 `PSTaskJob` 각 입력 값에 대 한 자식 작업을 포함 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-142">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="1e1df-143">작업 개체에는 자식 작업 실행 상태에 대 한 유용한 정보가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-143">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="1e1df-144">결과를 생성 하는 중에 자식 작업의 결과를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-144">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="1e1df-145">작업이 완료 될 때까지 대기 하 고 작업 결과를 검색 하는 방법</span><span class="sxs-lookup"><span data-stu-id="1e1df-145">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="1e1df-146">PowerShell 작업 cmdlet (예: 및)을 `Wait-Job` 사용 `Receive-Job` 하 여 작업이 완료 될 때까지 기다린 다음 작업에 의해 생성 된 모든 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-146">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="1e1df-147">다음 명령은 명령을 실행 하는 스레드 작업을 시작 하 고 `Get-Process` 명령이 완료 될 때까지 대기한 다음 명령에 의해 생성 된 모든 데이터 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-147">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="1e1df-148">다음 명령은 파이프 된 각 입력에 대해 명령을 실행 하는 작업을 시작한 `Write-Output` 다음 모든 자식 작업이 완료 될 때까지 대기 하 고, 마지막으로 자식 작업에 의해 생성 된 모든 데이터 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-148">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="1e1df-149">이 `Receive-Job` cmdlet은 자식 작업의 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-149">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="1e1df-150">각 자식 작업은 병렬로 실행 되므로 생성 된 결과의 순서는 보장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-150">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="powershell-concurrency-and-jobs"></a><span data-ttu-id="1e1df-151">PowerShell 동시성 및 작업</span><span class="sxs-lookup"><span data-stu-id="1e1df-151">PowerShell concurrency and jobs</span></span>

<span data-ttu-id="1e1df-152">PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-152">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="1e1df-153">PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 기반 솔루션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-153">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="1e1df-154">작업</span><span class="sxs-lookup"><span data-stu-id="1e1df-154">Job</span></span>            |<span data-ttu-id="1e1df-155">Description</span><span class="sxs-lookup"><span data-stu-id="1e1df-155">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="1e1df-156">명령 및 스크립트가 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-156">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="1e1df-157">명령 및 스크립트가 로컬에서 별도의 프로세스로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-157">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="1e1df-158">할당합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-158">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="1e1df-159">명령 및 스크립트가 동일한 내에서 별도의 스레드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-159">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="1e1df-160">로컬 컴퓨터의 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-160">process on the local machine.</span></span>                                |

<span data-ttu-id="1e1df-161">각 유형의 작업에는 장점과 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-161">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="1e1df-162">별도의 컴퓨터나 별도의 프로세스에서 원격으로 스크립트를 실행 하는 것은 매우 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-162">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="1e1df-163">모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 클라이언트에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-163">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="1e1df-164">하지만 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-164">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="1e1df-165">원격 세션과 주고 받은 모든 개체는 클라이언트와 대상 세션 간에 전달 될 때 serialize 된 다음 deserialize 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-165">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="1e1df-166">Serialization 작업은 복잡 한 데이터 개체에 많은 계산 및 메모리 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-166">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

## <a name="powershell-thread-based-jobs"></a><span data-ttu-id="1e1df-167">PowerShell 스레드 기반 작업</span><span class="sxs-lookup"><span data-stu-id="1e1df-167">PowerShell thread based jobs</span></span>

<span data-ttu-id="1e1df-168">스레드 기반 작업은 여러 스레드에서 동일한 프로세스로 실행 되기 때문에 원격 및 백그라운드 작업 만큼 강력 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-168">Thread based jobs are not as robust as Remote and Background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="1e1df-169">한 작업에 프로세스를 중단 하는 중대 한 오류가 있는 경우 프로세스의 다른 작업도 모두 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-169">If one job has a critical error that crashes the process, then all other jobs in the process will also fail.</span></span>

<span data-ttu-id="1e1df-170">그러나 스레드 기반 작업의 오버 헤드가 훨씬 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-170">However, thread-based jobs have much less overhead.</span></span> <span data-ttu-id="1e1df-171">원격 계층 또는 serialization을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-171">They don't need to use the remoting layer or serialization.</span></span> <span data-ttu-id="1e1df-172">따라서 스레드 기반 작업은 훨씬 더 빨리 실행 되 고 다른 작업 유형에 비해 훨씬 더 작은 리소스를 사용 하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-172">The result is that thread-based jobs tend to run much faster and use far less resources than the other job types.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="1e1df-173">스레드 작업 성능</span><span class="sxs-lookup"><span data-stu-id="1e1df-173">Thread job performance</span></span>

<span data-ttu-id="1e1df-174">스레드 작업은 다른 유형의 작업 보다 더 빠르고 가벼운 가중치입니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-174">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="1e1df-175">하지만 작업에서 수행 하는 작업에 비해 오버 헤드가 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-175">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="1e1df-176">PowerShell은 세션에서 명령 및 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-176">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="1e1df-177">세션에서 한 번에 하나의 명령 또는 스크립트만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-177">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="1e1df-178">따라서 여러 작업을 실행할 때 각 작업은 별도의 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-178">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="1e1df-179">각 세션은 오버 헤드에 기여 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-179">Each session contributes to the overhead.</span></span>

<span data-ttu-id="1e1df-180">스레드 작업은 수행 하는 작업이 작업을 실행 하는 데 사용 되는 세션의 오버 헤드 보다 큰 경우 최적의 성능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-180">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="1e1df-181">이 조건을 충족 하는 두 가지 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-181">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="1e1df-182">작업은 계산 집약적입니다. 여러 스레드 작업에서 스크립트를 실행 하면 여러 프로세서 코어를 활용 하 여 더 빨리 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-182">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="1e1df-183">작업은 i/o 또는 원격 호출 결과를 대기 하는 데 시간을 소비 하는 스크립트를 대기 하는 중요 한 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-183">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="1e1df-184">병렬로 실행 하는 것은 일반적으로 순차적으로 실행 하는 경우 보다 더 빨리 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-184">Running in parallel usually completes quicker than if run sequentially.</span></span>

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

<span data-ttu-id="1e1df-185">위의 첫 번째 예제에서는 간단한 문자열 쓰기를 수행 하는 1000 스레드 작업을 만드는 foreach 루프를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-185">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="1e1df-186">작업 오버 헤드로 인해 완료 하는 데 33 초 이상이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-186">Due to job overhead, it takes over 33 seconds to complete.</span></span>

<span data-ttu-id="1e1df-187">두 번째 예제에서는 cmdlet을 실행 `ForEach` 하 여 동일한 1000 작업을 수행 하 고 각 문자열 쓰기가 작업 오버 헤드 없이 순차적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-187">The second example runs the `ForEach` cmdlet to do the same 1000 operations and each string write is executed sequentially without any job overhead.</span></span> <span data-ttu-id="1e1df-188">25 밀리초 안에 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-188">It completes in a mere 25 milliseconds.</span></span>

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

<span data-ttu-id="1e1df-189">위의 예제에서는 10 개의 개별 시스템 로그에 대해 최대 5000 개의 항목이 수집 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-189">In the above example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="1e1df-190">스크립트에는 많은 로그 읽기가 포함 되므로 작업을 병렬로 수행 하는 것이 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-190">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span> <span data-ttu-id="1e1df-191">그리고 작업은 스크립트를 순차적으로 실행 하는 것 처럼 두 번 이상 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-191">And the job completes over twice as fast as when the script is run sequentially.</span></span>

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

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="1e1df-192">스레드 작업 및 변수</span><span class="sxs-lookup"><span data-stu-id="1e1df-192">Thread jobs and variables</span></span>

<span data-ttu-id="1e1df-193">변수는 다양 한 방식으로 스레드 작업에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-193">Variables are passed into thread jobs in various ways.</span></span>

<span data-ttu-id="1e1df-194">`Start-ThreadJob` 는 cmdlet으로 파이프 되는 변수, 키워드를 통해 스크립트 블록으로 전달 `$using` 되거나 **argumentlist** 매개 변수를 통해 전달 되는 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-194">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job

`ForEach-Object -Parallel` accepts piped in variables, and variables passed
directly to the script block via the `$using` keyword.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="1e1df-195">스레드 작업은 동일한 프로세스에서 실행 되므로 작업에 전달 되는 변수 참조 형식은 신중 하 게 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-195">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="1e1df-196">스레드로부터 안전한 개체가 아닌 경우에는 할당 되지 않아야 하 고 메서드 및 속성을 호출 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-196">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

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

<span data-ttu-id="1e1df-197">위의 예제에서는 `ConcurrentDictionary` 모든 자식 작업에 스레드로부터 안전한 dotNet 개체를 전달 하 여 고유 하 게 명명 된 프로세스 개체를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-197">The above example passes a thread safe dotNet `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="1e1df-198">스레드로부터 안전한 개체 이므로 작업이 프로세스에서 동시에 실행 되는 동안 안전 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1df-198">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e1df-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e1df-199">See also</span></span>

- [<span data-ttu-id="1e1df-200">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="1e1df-200">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="1e1df-201">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="1e1df-201">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="1e1df-202">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="1e1df-202">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="1e1df-203">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1e1df-203">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="1e1df-204">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1e1df-204">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="1e1df-205">Start-Job</span><span class="sxs-lookup"><span data-stu-id="1e1df-205">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="1e1df-206">Get-Job</span><span class="sxs-lookup"><span data-stu-id="1e1df-206">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="1e1df-207">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="1e1df-207">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="1e1df-208">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="1e1df-208">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="1e1df-209">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="1e1df-209">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="1e1df-210">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="1e1df-210">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
