---
description: PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 838e142fe39260b759e9a44c6d69b80d3c5b293e
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93224633"
---
# <a name="about-jobs"></a><span data-ttu-id="8f838-104">작업 정보</span><span class="sxs-lookup"><span data-stu-id="8f838-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="8f838-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="8f838-105">Short description</span></span>
<span data-ttu-id="8f838-106">PowerShell 백그라운드 작업에서 현재 세션과 상호 작용 하지 않고 백그라운드에서 명령 또는 식을 실행 하는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="8f838-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-107">Long description</span></span>

<span data-ttu-id="8f838-108">PowerShell은 작업을 통해 명령과 스크립트를 동시에 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-108">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="8f838-109">PowerShell에서 동시성을 지원 하기 위해 제공 하는 세 가지 작업 기반 솔루션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-109">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="8f838-110">작업</span><span class="sxs-lookup"><span data-stu-id="8f838-110">Job</span></span>            |<span data-ttu-id="8f838-111">Description</span><span class="sxs-lookup"><span data-stu-id="8f838-111">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="8f838-112">명령 및 스크립트가 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-112">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="8f838-113">명령 및 스크립트가 로컬에서 별도의 프로세스로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-113">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="8f838-114">할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-114">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="8f838-115">명령 및 스크립트가 동일한 내에서 별도의 스레드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-115">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="8f838-116">로컬 컴퓨터의 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-116">process on the local machine.</span></span>                                |

<span data-ttu-id="8f838-117">각 유형의 작업에는 장점과 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-117">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="8f838-118">별도의 컴퓨터나 별도의 프로세스에서 원격으로 스크립트를 실행 하는 것은 매우 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-118">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="8f838-119">모든 오류는 실행 중인 다른 작업이 나 작업을 시작한 클라이언트에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-119">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="8f838-120">하지만 원격 계층은 개체 serialization을 포함 하 여 오버 헤드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-120">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="8f838-121">원격 세션과 주고 받은 모든 개체는 클라이언트와 대상 세션 간에 전달 될 때 serialize 된 다음 deserialize 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-121">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="8f838-122">Serialization 작업은 복잡 한 데이터 개체에 많은 계산 및 메모리 리소스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-122">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

<span data-ttu-id="8f838-123">이 항목에서는 로컬 컴퓨터의 PowerShell에서 백그라운드 작업을 실행 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-123">This topic explains how to run background jobs in PowerShell on a local computer.</span></span> <span data-ttu-id="8f838-124">원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f838-124">For information about running background jobs on remote computers, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span> <span data-ttu-id="8f838-125">스레드 작업에 대 한 자세한 내용은 [about_Thread_Jobs](about_Thread_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f838-125">For more information about thread jobs, see [about_Thread_Jobs](about_Thread_Jobs.md).</span></span>

<span data-ttu-id="8f838-126">백그라운드 작업을 시작 하면 작업을 완료 하는 데 오랜 시간이 소요 되는 경우에도 명령 프롬프트가 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-126">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="8f838-127">작업이 실행되는 동안 중단 없이 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-127">You can continue to work in the session without interruption while the job runs.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="8f838-128">작업 cmdlet</span><span class="sxs-lookup"><span data-stu-id="8f838-128">The job cmdlets</span></span>

|<span data-ttu-id="8f838-129">cmdlet</span><span class="sxs-lookup"><span data-stu-id="8f838-129">Cmdlet</span></span>          |<span data-ttu-id="8f838-130">Description</span><span class="sxs-lookup"><span data-stu-id="8f838-130">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="8f838-131">로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-131">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="8f838-132">에서 시작 된 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-132">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="8f838-133">현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-133">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="8f838-134">백그라운드 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-134">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="8f838-135">백그라운드 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-135">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="8f838-136">하나 또는 모든 작업이 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-136">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="8f838-137">완료.</span><span class="sxs-lookup"><span data-stu-id="8f838-137">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="8f838-138">백그라운드 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-138">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="8f838-139">**AsJob** 매개 변수는에 대 한 백그라운드 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-139">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="8f838-140">원격 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="8f838-140">remote computer.</span></span> <span data-ttu-id="8f838-141">`Invoke-Command`를 사용 하 여를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-141">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="8f838-142">을 포함 하 여 원격으로 작업 명령 `Start-Job`</span><span class="sxs-lookup"><span data-stu-id="8f838-142">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="8f838-143">로컬 컴퓨터에서 작업을 시작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8f838-143">How to start a job on the local computer</span></span>

<span data-ttu-id="8f838-144">로컬 컴퓨터에서 백그라운드 작업을 시작 하려면 cmdlet을 사용 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-144">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="8f838-145">명령을 작성 하려면 `Start-Job` 작업을 실행 하는 명령을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="8f838-145">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="8f838-146">**ScriptBlock** 매개 변수를 사용 하 여 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-146">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="8f838-147">다음 명령은 `Get-Process` 로컬 컴퓨터에서 명령을 실행 하는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-147">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="8f838-148">`Start-Job`이 명령은 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-148">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="8f838-149">작업 개체에는 작업에 대한 유용한 정보가 포함되어 있지만 작업 결과는 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-149">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="8f838-150">작업 개체를 변수에 저장 한 다음 다른 작업 cmdlet과 함께 사용 하 여 백그라운드 작업을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-150">Save the job object in a variable, and then use it with the other Job cmdlets to manage the background job.</span></span> <span data-ttu-id="8f838-151">다음 명령은 작업 개체를 시작 하 고 결과 작업 개체를 변수에 저장 합니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="8f838-151">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="8f838-152">PowerShell 6.0부터 파이프라인 끝에 amersand ()를 사용 `&` 하 여 백그라운드 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-152">Beginning in PowerShell 6.0, you can use an amersand (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="8f838-153">다음 명령은 위의 명령과 기능적으로 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-153">The following command is functionally equivalent to the command above.</span></span>

```powershell
$job = Get-Process &
```

<span data-ttu-id="8f838-154">앰퍼샌드 ( `&` )를 background 연산자 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-154">The ampersand (`&`) is called the background operator.</span></span> <span data-ttu-id="8f838-155">자세한 내용은 [background operator](about_Operators.md#background-operator-)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f838-155">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="8f838-156">Cmdlet을 사용 하 여 `Get-Job` 현재 세션에서 시작 된 작업을 나타내는 개체를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-156">You can also use the `Get-Job` cmdlet to get objects that represent the jobs started in the current session.</span></span> <span data-ttu-id="8f838-157">`Get-Job` 에서 반환 하는 것과 동일한 작업 개체를 반환 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-157">`Get-Job` returns the same job object that `Start-Job` returns.</span></span>

## <a name="getting-job-objects"></a><span data-ttu-id="8f838-158">작업 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="8f838-158">Getting job objects</span></span>

<span data-ttu-id="8f838-159">현재 세션에서 시작 된 백그라운드 작업을 나타내는 개체를 가져오려면 cmdlet을 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="8f838-159">To get object that represent the background jobs that were started in the current session, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="8f838-160">매개 변수가 없으면 `Get-Job` 현재 세션에서 시작 된 모든 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-160">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

<span data-ttu-id="8f838-161">예를 들어 다음 명령은 현재 세션의 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-161">For example, the following command gets the jobs in the current session.</span></span>

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

<span data-ttu-id="8f838-162">작업 개체를 변수에 저장 하 고이를 사용 하 여 이후 명령에서 작업을 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-162">You can also save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="8f838-163">다음 명령은 ID가 1 인 작업을 가져와서 변수에 저장 합니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="8f838-163">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

<span data-ttu-id="8f838-164">작업 개체에는 작업이 완료 되었는지 여부를 나타내는 작업의 상태가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-164">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="8f838-165">완료 된 작업의 상태가 **완료** 또는 **실패** 입니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-165">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="8f838-166">작업이 **차단** 되거나 **실행 중일** 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-166">A job might also be **blocked** or **running**.</span></span>

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="8f838-167">작업 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="8f838-167">Getting the results of a job</span></span>

<span data-ttu-id="8f838-168">백그라운드 작업을 실행 하면 결과가 즉시 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-168">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="8f838-169">대신 `Start-Job` 이 cmdlet은 작업을 나타내는 작업 개체를 반환 하지만 결과는 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-169">Instead, the `Start-Job` cmdlet returns a job object that represents the job, but it does not contain the results.</span></span> <span data-ttu-id="8f838-170">백그라운드 작업의 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="8f838-170">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="8f838-171">다음 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-171">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="8f838-172">변수에 저장 된 작업 개체를 사용 하 여 `$job` 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-172">It uses a job object saved in the `$job` variable to identify the job.</span></span>

```powershell
Receive-Job -Job $job
```

<span data-ttu-id="8f838-173">`Receive-Job`Cmdlet은 작업의 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-173">The `Receive-Job` cmdlet returns the results of the job.</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

<span data-ttu-id="8f838-174">작업의 결과를 변수에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-174">You can also save the results of a job in a variable.</span></span> <span data-ttu-id="8f838-175">다음 명령은 변수에 있는 작업의 결과를 변수에 저장 합니다 `$job` `$results` .</span><span class="sxs-lookup"><span data-stu-id="8f838-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

<span data-ttu-id="8f838-176">그리고 리디렉션 연산자 () 또는 cmdlet을 사용 하 여 작업 결과를 파일에 저장할 수 있습니다 `>` `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="8f838-176">And, you can save the results of the job in a file by using the redirection operator (`>`) or the `Out-File` cmdlet.</span></span> <span data-ttu-id="8f838-177">다음 명령은 리디렉션 연산자를 사용 하 여 작업 결과를 `$job` 파일의 변수에 저장 `Results.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-177">The following command uses the redirection operator to save the results of the job in the `$job` variable in the `Results.txt` file.</span></span>

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="8f838-178">부분 작업 결과 가져오기 및 유지</span><span class="sxs-lookup"><span data-stu-id="8f838-178">Getting and keeping partial job results</span></span>

<span data-ttu-id="8f838-179">`Receive-Job`Cmdlet은 백그라운드 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-179">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="8f838-180">작업이 완료 되 면 `Receive-Job` 모든 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-180">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="8f838-181">작업이 계속 실행 중인 경우 `Receive-Job` 지금까지 생성 된 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-181">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="8f838-182">`Receive-Job`명령을 다시 실행 하 여 나머지 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-182">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="8f838-183">는 `Receive-Job` 결과를 반환할 때 기본적으로 작업 결과가 저장 되는 캐시에서 해당 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-183">When `Receive-Job` returns results, by default, it deletes those results from the cache where job results are stored.</span></span> <span data-ttu-id="8f838-184">다른 명령을 실행 하면 `Receive-Job` 아직 수신 되지 않은 결과만 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-184">If you run another `Receive-Job` command, you get only the results that are not yet received.</span></span>

<span data-ttu-id="8f838-185">다음 명령은 `Receive-Job` 작업이 완료 되기 전에 실행 된 명령의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-185">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="8f838-186">반환 된 `Receive-Job` 작업 결과를 삭제 하지 않으려면 **Keep** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-186">To prevent `Receive-Job` from deleting the job results that it has returned, use the **Keep** parameter.</span></span> <span data-ttu-id="8f838-187">결과적으로 `Receive-Job` 는 해당 시간까지 생성 된 모든 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-187">As a result, `Receive-Job` returns all of the results that have been generated until that time.</span></span>

<span data-ttu-id="8f838-188">다음 명령은 아직 완료 되지 않은 작업에 대해 **Keep** 매개 변수를 사용 하는 경우의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-188">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

## <a name="waiting-for-the-results"></a><span data-ttu-id="8f838-189">결과를 기다리는 중</span><span class="sxs-lookup"><span data-stu-id="8f838-189">Waiting for the results</span></span>

<span data-ttu-id="8f838-190">완료 하는 데 시간이 오래 걸리는 명령을 실행 하는 경우 작업 개체의 속성을 사용 하 여 작업이 완료 된 시간을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-190">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="8f838-191">다음 명령은 개체를 사용 하 여 `Get-Job` 현재 세션의 모든 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-191">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="8f838-192">결과는 테이블에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-192">The results appear in a table.</span></span> <span data-ttu-id="8f838-193">작업 상태가 **상태** 열에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-193">The status of the job appears in the **State** column.</span></span>

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="8f838-194">이 경우 State 속성은 작업 2가 여전히 실행 되 고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-194">In this case, the State property reveals that Job 2 is still running.</span></span> <span data-ttu-id="8f838-195">Cmdlet을 사용 하 여 `Receive-Job` 지금 작업 결과를 가져오는 경우 결과가 완전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-195">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="8f838-196">`Receive-Job`Cmdlet을 반복 해 서 사용 하 여 모든 결과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-196">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="8f838-197">기본적으로 사용할 때마다 아직 수신 되지 않은 결과만 가져오지만 cmdlet의 **Keep** 매개 변수를 사용 `Receive-Job` 하 여 결과를 이미 받은 경우라도 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-197">By default, each time you use it, you get only the results that were not already received, but you can use the **Keep** parameter of the `Receive-Job` cmdlet to retain the results, even though they were already received.</span></span>

<span data-ttu-id="8f838-198">파일에 부분 결과를 기록한 다음 도착 하면 최신 결과를 추가 하거나 나중에 작업 상태를 확인 하 고 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-198">You can write the partial results to a file and then append newer results as they arrive or you can wait and check the state of the job later.</span></span>

<span data-ttu-id="8f838-199">Cmdlet의 **Wait** 매개 변수를 사용할 수 있습니다 .이 매개 변수는 `Receive-Job` 작업이 완료 되 고 모든 결과를 사용할 수 있을 때까지 명령 프롬프트를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-199">You can use the **Wait** parameter of the `Receive-Job` cmdlet, which does not return the command prompt until the job is complete and all results are available.</span></span>

<span data-ttu-id="8f838-200">Cmdlet을 사용 하 여 `Wait-Job` 작업 결과의 일부 또는 모두를 기다릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-200">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="8f838-201">`Wait-Job` 모든 작업에 대해 특정 작업이 수행 될 때까지 기다리거나 작업을 완료할 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-201">`Wait-Job` lets you wait for a particular job, for all jobs, or for any of the jobs to be completed.</span></span>

<span data-ttu-id="8f838-202">다음 명령은 cmdlet을 사용 하 여 `Wait-Job` **ID가** 인 작업을 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-202">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="8f838-203">따라서 작업이 완료 될 때까지 PowerShell 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-203">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="8f838-204">미리 정해진 시간 동안 기다릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-204">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="8f838-205">이 명령은 Timeout 매개 변수를 사용 하 여 대기 **시간** 을 120 초로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-205">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="8f838-206">시간이 만료 되 면 명령 프롬프트가 반환 되지만 작업은 백그라운드에서 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-206">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="8f838-207">작업 중지</span><span class="sxs-lookup"><span data-stu-id="8f838-207">Stopping a job</span></span>

<span data-ttu-id="8f838-208">백그라운드 작업을 중지 하려면 cmdlet을 사용 `Stop-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-208">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="8f838-209">다음 명령을 실행 하 여 시스템 이벤트 로그의 모든 항목을 가져오는 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-209">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="8f838-210">작업 개체를 `$job` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-210">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="8f838-211">다음 명령은 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-211">The following command stops the job.</span></span> <span data-ttu-id="8f838-212">파이프라인 연산자 ()를 사용 하 여 `|` 변수에서 작업을 `$job` 로 보냅니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="8f838-212">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="8f838-213">작업 삭제</span><span class="sxs-lookup"><span data-stu-id="8f838-213">Deleting a job</span></span>

<span data-ttu-id="8f838-214">백그라운드 작업을 삭제 하려면 cmdlet을 사용 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-214">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="8f838-215">다음 명령은 변수에서 작업을 삭제 합니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="8f838-215">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="8f838-216">실패 한 작업 조사</span><span class="sxs-lookup"><span data-stu-id="8f838-216">Investigating a failed job</span></span>

<span data-ttu-id="8f838-217">작업이 실패 한 이유를 확인 하려면 작업 개체의 **Reason** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-217">To find out why a job failed, use the **Reason** property of the job object.</span></span>

<span data-ttu-id="8f838-218">다음 명령은 필수 자격 증명 없이 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-218">The following command starts a job without the required credentials.</span></span> <span data-ttu-id="8f838-219">작업 개체를 `$job` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-219">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="8f838-220">다음 명령은 Reason 속성을 사용 하 여 작업 실패를 일으킨 오류를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-220">The following command uses the Reason property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="8f838-221">이 경우 원격 컴퓨터에서 명령을 실행 하기 위한 명시적 자격 증명이 필요 하기 때문에 작업이 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-221">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="8f838-222">**Reason** 속성의 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-222">The value of the **Reason** property is:</span></span>

<span data-ttu-id="8f838-223">"액세스가 거부 되었습니다." 라는 오류 메시지와 함께 원격 서버에 연결 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="8f838-223">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="8f838-224">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f838-224">See also</span></span>

- [<span data-ttu-id="8f838-225">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="8f838-225">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="8f838-226">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="8f838-226">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="8f838-227">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="8f838-227">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="8f838-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8f838-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="8f838-229">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8f838-229">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="8f838-230">Start-Job</span><span class="sxs-lookup"><span data-stu-id="8f838-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="8f838-231">Get-Job</span><span class="sxs-lookup"><span data-stu-id="8f838-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="8f838-232">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="8f838-232">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="8f838-233">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="8f838-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="8f838-234">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="8f838-234">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="8f838-235">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="8f838-235">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="8f838-236">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8f838-236">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
