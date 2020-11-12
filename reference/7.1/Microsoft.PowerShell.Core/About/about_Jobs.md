---
description: PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: d4d4f4b8a2f57edcfa72247d9f9bc224b848789a
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524776"
---
# <a name="about-jobs"></a><span data-ttu-id="79382-104">작업 정보</span><span class="sxs-lookup"><span data-stu-id="79382-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="79382-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="79382-105">Short description</span></span>
<span data-ttu-id="79382-106">PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="79382-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="79382-107">Long description</span></span>

<span data-ttu-id="79382-108">PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="79382-109">PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="79382-110">`RemoteJob` -명령 및 스크립트가 원격 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-110">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="79382-111">자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79382-111">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="79382-112">`BackgroundJob` -명령 및 스크립트는 로컬 컴퓨터에서 별도의 프로세스로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-112">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="79382-113">`PSTaskJob` 또는 `ThreadJob` -명령 및 스크립트는 로컬 컴퓨터에서 동일한 프로세스 내에서 별도의 스레드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="79382-114">자세한 내용은 [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79382-114">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="79382-115">별도의 컴퓨터에서 또는 별도의 프로세스로 스크립트를 원격으로 실행 하는 것이 뛰어난 격리를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-115">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="79382-116">원격 작업에서 발생 하는 모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 부모 세션에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="79382-117">그러나 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="79382-118">모든 개체는 부모 세션과 원격 (작업) 세션 간에 전달 될 때 serialize 되 고 deserialize 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="79382-119">크고 복잡 한 데이터 개체의 Serialization은 많은 양의 계산 및 메모리 리소스를 사용 하 고 네트워크를 통해 많은 양의 데이터를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="79382-120">스레드 기반 작업은 여러 스레드에서 동일한 프로세스로 실행 되기 때문에 원격 및 백그라운드 작업 만큼 강력 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-120">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="79382-121">한 작업에 프로세스를 중단 하는 중대 한 오류가 있는 경우 프로세스의 다른 모든 작업이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-121">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="79382-122">그러나 스레드 기반 작업에는 오버 헤드가 적게 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-122">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="79382-123">Remoting 계층 또는 serialization은 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-123">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="79382-124">결과 개체는 현재 세션의 라이브 개체에 대 한 참조로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-124">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="79382-125">이러한 오버 헤드가 없으면 스레드 기반 작업은 더 빠르게 실행 되 고 다른 작업 유형에 비해 리소스를 적게 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-125">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79382-126">작업을 만든 부모 세션도 작업 상태를 모니터링 하 고 파이프라인 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-126">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="79382-127">작업이 완료 된 상태에 도달 하면 부모 프로세스가 작업 자식 프로세스를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-127">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="79382-128">부모 세션이 종료 되 면 모든 실행 중인 자식 작업은 자식 프로세스와 함께 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-128">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="79382-129">이러한 상황을 해결 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-129">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="79382-130">`Invoke-Command`를 사용 하 여 연결 되지 않은 세션에서 실행 되는 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79382-130">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="79382-131">자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79382-131">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="79382-132">`Start-Process`작업 대신 새 프로세스를 만들려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-132">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="79382-133">자세한 내용은 [시작-처리](xref:Microsoft.PowerShell.Management.Start-Process)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79382-133">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="79382-134">작업 cmdlet</span><span class="sxs-lookup"><span data-stu-id="79382-134">The job cmdlets</span></span>

|<span data-ttu-id="79382-135">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="79382-135">Cmdlet</span></span>          |<span data-ttu-id="79382-136">Description</span><span class="sxs-lookup"><span data-stu-id="79382-136">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="79382-137">로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-137">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="79382-138">에서 시작 된 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79382-138">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="79382-139">현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="79382-139">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="79382-140">백그라운드 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79382-140">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="79382-141">백그라운드 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-141">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="79382-142">하나 또는 모든 작업이 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-142">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="79382-143">완료.</span><span class="sxs-lookup"><span data-stu-id="79382-143">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="79382-144">백그라운드 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-144">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="79382-145">**AsJob** 매개 변수는에 대 한 백그라운드 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="79382-145">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="79382-146">원격 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="79382-146">remote computer.</span></span> <span data-ttu-id="79382-147">`Invoke-Command`를 사용 하 여를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-147">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="79382-148">을 포함 하 여 원격으로 작업 명령 `Start-Job`</span><span class="sxs-lookup"><span data-stu-id="79382-148">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="79382-149">로컬 컴퓨터에서 작업을 시작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="79382-149">How to start a job on the local computer</span></span>

<span data-ttu-id="79382-150">로컬 컴퓨터에서 백그라운드 작업을 시작 하려면 cmdlet을 사용 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-150">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="79382-151">명령을 작성 하려면 `Start-Job` 작업을 실행 하는 명령을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="79382-151">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="79382-152">**ScriptBlock** 매개 변수를 사용 하 여 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-152">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="79382-153">다음 명령은 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-153">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="79382-154">백그라운드 작업을 시작 하면 작업을 완료 하는 데 오랜 시간이 소요 되는 경우에도 명령 프롬프트가 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-154">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="79382-155">작업이 실행되는 동안 중단 없이 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-155">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="79382-156">`Start-Job`이 명령은 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-156">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="79382-157">작업 개체에는 작업에 대한 유용한 정보가 포함되어 있지만 작업 결과는 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-157">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="79382-158">작업 개체를 변수에 저장 한 다음 다른 **작업** cmdlet과 함께 사용 하 여 백그라운드 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-158">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="79382-159">다음 명령은 작업 개체를 시작 하 고 결과 작업 개체를 변수에 저장 합니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="79382-159">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="79382-160">PowerShell 6.0부터 파이프라인 끝에 백그라운드 연산자 ()를 사용 `&` 하 여 백그라운드 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-160">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="79382-161">자세한 내용은 [background operator](about_Operators.md#background-operator-)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79382-161">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="79382-162">백그라운드 연산자를 사용 하는 것은 이전 예제에서 cmdlet을 사용 하는 것과 기능적으로 동일 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-162">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="79382-163">작업 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="79382-163">Getting job objects</span></span>

<span data-ttu-id="79382-164">`Get-Job`Cmdlet은 현재 세션에서 시작 된 백그라운드 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-164">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="79382-165">매개 변수가 없으면 `Get-Job` 현재 세션에서 시작 된 모든 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-165">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="79382-166">작업 개체에는 작업이 완료 되었는지 여부를 나타내는 작업의 상태가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-166">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="79382-167">완료 된 작업의 상태가 **완료** 또는 **실패** 입니다.</span><span class="sxs-lookup"><span data-stu-id="79382-167">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="79382-168">작업이 **차단** 되거나 **실행 중일** 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-168">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="79382-169">작업 개체를 변수에 저장 하 고이를 사용 하 여 이후 명령에서 작업을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-169">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="79382-170">다음 명령은 ID가 1 인 작업을 가져와서 변수에 저장 합니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="79382-170">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="79382-171">작업 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="79382-171">Getting the results of a job</span></span>

<span data-ttu-id="79382-172">백그라운드 작업을 실행 하면 결과가 즉시 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-172">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="79382-173">백그라운드 작업의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="79382-173">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="79382-174">다음 예에서는 cmdlet이 `Receive-Job` 변수에 job 개체를 사용 하 여 작업의 결과를 가져옵니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="79382-174">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

<span data-ttu-id="79382-175">작업의 결과를 변수에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-175">You can save the results of a job in a variable.</span></span> <span data-ttu-id="79382-176">다음 명령은 변수에 있는 작업의 결과를 변수에 저장 합니다 `$job` `$results` .</span><span class="sxs-lookup"><span data-stu-id="79382-176">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="79382-177">부분 작업 결과 가져오기 및 유지</span><span class="sxs-lookup"><span data-stu-id="79382-177">Getting and keeping partial job results</span></span>

<span data-ttu-id="79382-178">`Receive-Job`Cmdlet은 백그라운드 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79382-178">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="79382-179">작업이 완료 되 면 `Receive-Job` 모든 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79382-179">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="79382-180">작업이 계속 실행 중인 경우 `Receive-Job` 지금까지 생성 된 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79382-180">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="79382-181">`Receive-Job`명령을 다시 실행 하 여 나머지 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-181">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="79382-182">기본적으로는 `Receive-Job` 작업 결과가 저장 되는 캐시에서 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-182">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="79382-183">`Receive-Job`을 다시 실행 하면 첫 번째 실행 후 도착 한 새 결과만 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-183">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="79382-184">다음 명령은 `Receive-Job` 작업이 완료 되기 전에 실행 된 명령의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79382-184">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

<span data-ttu-id="79382-185">**Keep** 매개 변수를 사용 하 여 반환 되는 `Receive-Job` 작업 결과를 삭제 하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-185">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="79382-186">다음 명령은 아직 완료 되지 않은 작업에 대해 **Keep** 매개 변수를 사용 하는 경우의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79382-186">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a><span data-ttu-id="79382-187">결과를 기다리는 중</span><span class="sxs-lookup"><span data-stu-id="79382-187">Waiting for the results</span></span>

<span data-ttu-id="79382-188">완료 하는 데 시간이 오래 걸리는 명령을 실행 하는 경우 작업 개체의 속성을 사용 하 여 작업이 완료 된 시간을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-188">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="79382-189">다음 명령은 개체를 사용 하 여 `Get-Job` 현재 세션의 모든 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="79382-189">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="79382-190">결과는 테이블에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-190">The results appear in a table.</span></span> <span data-ttu-id="79382-191">작업 상태가 **상태** 열에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-191">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="79382-192">이 경우 **State** 속성은 작업 2가 여전히 실행 되 고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="79382-192">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="79382-193">Cmdlet을 사용 하 여 `Receive-Job` 지금 작업 결과를 가져오는 경우 결과가 완전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-193">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="79382-194">`Receive-Job`Cmdlet을 반복 해 서 사용 하 여 모든 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-194">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="79382-195">**상태** 속성을 사용 하 여 작업이 완료 된 시기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-195">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="79382-196">또한 cmdlet의 **Wait** 매개 변수를 사용할 수 있습니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="79382-196">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="79382-197">이 매개 변수를 사용 하는 경우 작업이 완료 되 고 모든 결과를 사용할 수 있을 때까지 cmdlet은 명령 프롬프트를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-197">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="79382-198">Cmdlet을 사용 하 여 `Wait-Job` 작업 결과의 일부 또는 모두를 기다릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-198">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="79382-199">`Wait-Job` 하나 이상의 특정 작업 또는 모든 작업에 대해 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-199">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="79382-200">다음 명령은 cmdlet을 사용 하 여 `Wait-Job` **ID가** 인 작업을 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-200">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="79382-201">따라서 작업이 완료 될 때까지 PowerShell 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-201">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="79382-202">미리 정해진 시간 동안 기다릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-202">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="79382-203">이 명령은 Timeout 매개 변수를 사용 하 여 대기 **시간** 을 120 초로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-203">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="79382-204">시간이 만료 되 면 명령 프롬프트가 반환 되지만 작업은 백그라운드에서 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79382-204">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="79382-205">작업 중지</span><span class="sxs-lookup"><span data-stu-id="79382-205">Stopping a job</span></span>

<span data-ttu-id="79382-206">백그라운드 작업을 중지 하려면 cmdlet을 사용 `Stop-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-206">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="79382-207">다음 명령을 실행 하 여 시스템 이벤트 로그의 모든 항목을 가져오는 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-207">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="79382-208">작업 개체를 `$job` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-208">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="79382-209">다음 명령은 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-209">The following command stops the job.</span></span> <span data-ttu-id="79382-210">파이프라인 연산자 ()를 사용 하 여 `|` 변수에서 작업을 `$job` 로 보냅니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="79382-210">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="79382-211">작업 삭제</span><span class="sxs-lookup"><span data-stu-id="79382-211">Deleting a job</span></span>

<span data-ttu-id="79382-212">백그라운드 작업을 삭제 하려면 cmdlet을 사용 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-212">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="79382-213">다음 명령은 변수에서 작업을 삭제 합니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="79382-213">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="79382-214">실패 한 작업 조사</span><span class="sxs-lookup"><span data-stu-id="79382-214">Investigating a failed job</span></span>

<span data-ttu-id="79382-215">작업은 여러 가지 이유로 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-215">Jobs can fail for many reasons.</span></span> <span data-ttu-id="79382-216">작업 개체에는 실패 원인에 대 한 정보를 포함 하는 **Reason** 속성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-216">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="79382-217">다음 예에서는 필수 자격 증명 없이 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-217">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="79382-218">**Reason** 속성을 검사 하 여 작업이 실패 하 게 만든 오류를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-218">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="79382-219">이 경우 원격 컴퓨터에서 명령을 실행 하기 위한 명시적 자격 증명이 필요 하기 때문에 작업이 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-219">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="79382-220">**Reason** 속성은 다음과 같은 메시지를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="79382-220">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="79382-221">"액세스가 거부 되었습니다." 라는 오류 메시지와 함께 원격 서버에 연결 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="79382-221">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="79382-222">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79382-222">See also</span></span>

- [<span data-ttu-id="79382-223">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="79382-223">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="79382-224">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="79382-224">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="79382-225">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="79382-225">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="79382-226">about_Remote</span><span class="sxs-lookup"><span data-stu-id="79382-226">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="79382-227">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="79382-227">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="79382-228">Start-Job</span><span class="sxs-lookup"><span data-stu-id="79382-228">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="79382-229">Get-Job</span><span class="sxs-lookup"><span data-stu-id="79382-229">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="79382-230">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="79382-230">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="79382-231">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="79382-231">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="79382-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="79382-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="79382-233">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="79382-233">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="79382-234">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="79382-234">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
