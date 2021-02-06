---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52613dae3ba73227818c6c0dec40183ba20ce2a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602068"
---
# <span data-ttu-id="fe221-102">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="fe221-102">Remove-Job</span></span>

## <span data-ttu-id="fe221-103">개요</span><span class="sxs-lookup"><span data-stu-id="fe221-103">SYNOPSIS</span></span>
<span data-ttu-id="fe221-104">PowerShell 백그라운드 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-104">Deletes a PowerShell background job.</span></span>

## <span data-ttu-id="fe221-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fe221-105">SYNTAX</span></span>

### <span data-ttu-id="fe221-106">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="fe221-106">SessionIdParameterSet (Default)</span></span>

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe221-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="fe221-107">JobParameterSet</span></span>

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe221-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="fe221-108">NameParameterSet</span></span>

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe221-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="fe221-109">InstanceIdParameterSet</span></span>

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe221-110">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="fe221-110">FilterParameterSet</span></span>

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe221-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="fe221-111">StateParameterSet</span></span>

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe221-112">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="fe221-112">CommandParameterSet</span></span>

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fe221-113">설명</span><span class="sxs-lookup"><span data-stu-id="fe221-113">DESCRIPTION</span></span>

<span data-ttu-id="fe221-114">`Remove-Job`Cmdlet은 `Start-Job` Cmdlet 또는 `Invoke-Command` **AsJob** 매개 변수를 지 원하는 Cmdlet에 의해 시작 된 PowerShell 백그라운드 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-114">The `Remove-Job` cmdlet deletes PowerShell background jobs that were started by the `Start-Job` cmdlet or by cmdlets such as `Invoke-Command` that support the **AsJob** parameter.</span></span>

<span data-ttu-id="fe221-115">`Remove-Job`를 사용 하 여 모든 작업을 삭제 하거나 선택한 작업을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-115">You can use `Remove-Job` to delete all jobs or delete selected jobs.</span></span> <span data-ttu-id="fe221-116">작업은 **이름**, **ID**, **인스턴스 id**, **명령** 또는 **상태로** 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-116">The jobs are identified by their **Name**, **ID**, **Instance ID**, **Command**, or **State**.</span></span> <span data-ttu-id="fe221-117">또는 파이프라인에서로 작업 개체를 보낼 수 있습니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-117">Or, a job object can be sent down the pipeline to `Remove-Job`.</span></span> <span data-ttu-id="fe221-118">매개 변수 또는 매개 변수 값이 없으면는 영향을 주지 `Remove-Job` 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-118">Without parameters or parameter values, `Remove-Job` has no effect.</span></span>

<span data-ttu-id="fe221-119">PowerShell 3.0부터는 `Remove-Job` 예약 된 작업 및 워크플로 작업과 같은 사용자 지정 작업 유형을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-119">Since PowerShell 3.0, `Remove-Job` can delete custom job types, such as scheduled jobs and workflow jobs.</span></span> <span data-ttu-id="fe221-120">예를 들어는 예약 된 작업 `Remove-Job` , 디스크에 있는 예약 된 작업의 모든 인스턴스 및 모든 트리거된 작업 인스턴스의 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-120">For example, `Remove-Job` deletes the scheduled job, all instances of the scheduled job on disk, and the results of all triggered job instances.</span></span>

<span data-ttu-id="fe221-121">실행 중인 작업을 삭제 하려고 하면이 `Remove-Job` 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-121">If you try to delete a running job, `Remove-Job` fails.</span></span> <span data-ttu-id="fe221-122">Cmdlet을 사용 `Stop-Job` 하 여 실행 중인 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-122">Use the `Stop-Job` cmdlet to stop a running job.</span></span> <span data-ttu-id="fe221-123">또는 `Remove-Job` **Force** 매개 변수와 함께를 사용 하 여 실행 중인 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-123">Or, use `Remove-Job` with the **Force** parameter to delete a running job.</span></span>

<span data-ttu-id="fe221-124">백그라운드 작업을 삭제 하거나 PowerShell 세션을 닫을 때까지 작업이 전역 작업 캐시에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-124">Jobs remain in the global job cache until you delete the background job or close the PowerShell session.</span></span>

## <span data-ttu-id="fe221-125">예제</span><span class="sxs-lookup"><span data-stu-id="fe221-125">EXAMPLES</span></span>

### <span data-ttu-id="fe221-126">예제 1: 이름을 사용 하 여 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fe221-126">Example 1: Delete a job by using its name</span></span>

<span data-ttu-id="fe221-127">이 예제에서는 변수와 파이프라인을 사용 하 여 이름을 기준으로 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-127">This example uses a variable and the pipeline to delete a job by name.</span></span>

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

<span data-ttu-id="fe221-128">`Get-Job`**Name** 매개 변수를 사용 하 여 **batchjob** 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-128">`Get-Job` uses the **Name** parameter to specify the job, **BatchJob**.</span></span> <span data-ttu-id="fe221-129">작업 개체는 변수에 저장 됩니다 `$batch` .</span><span class="sxs-lookup"><span data-stu-id="fe221-129">The job object is stored in the `$batch` variable.</span></span> <span data-ttu-id="fe221-130">의 개체는 `$batch` 파이프라인에서로 전송 됩니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-130">The object in `$batch` is sent down the pipeline to `Remove-Job`.</span></span>

<span data-ttu-id="fe221-131">대신 **작업** 매개 변수 (예:)를 사용 `Remove-Job -Job $batch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-131">An alternative is to use the **Job** parameter, such as `Remove-Job -Job $batch`.</span></span>

### <span data-ttu-id="fe221-132">예 2: 세션의 모든 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fe221-132">Example 2: Delete all jobs in a session</span></span>

<span data-ttu-id="fe221-133">이 예에서는 현재 PowerShell 세션의 모든 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-133">In this example, all the jobs in the current PowerShell session are deleted.</span></span>

```powershell
Get-job | Remove-Job
```

<span data-ttu-id="fe221-134">`Get-Job` 현재 PowerShell 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-134">`Get-Job` gets all the jobs in the current PowerShell session.</span></span> <span data-ttu-id="fe221-135">작업 개체는 파이프라인에서로 전송 됩니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-135">The job objects are sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="fe221-136">예 3: NotStarted 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fe221-136">Example 3: Delete NotStarted jobs</span></span>

<span data-ttu-id="fe221-137">이 예에서는 현재 PowerShell 세션에서 아직 시작 되지 않은 모든 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-137">This example deletes all jobs from the current PowerShell session that haven't started.</span></span>

```powershell
Remove-Job -State NotStarted
```

<span data-ttu-id="fe221-138">`Remove-Job`**State** 매개 변수를 사용 하 여 작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-138">`Remove-Job` uses the **State** parameter to specify the job status.</span></span>

### <span data-ttu-id="fe221-139">예제 4: 친숙 한 이름을 사용 하 여 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fe221-139">Example 4: Delete jobs by using a friendly name</span></span>

<span data-ttu-id="fe221-140">이 예에서는를 실행 하는 작업을 포함 하 여 이름이 \* batch \* \*로 끝나는 현재 세션에서 모든 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-140">This example deletes all jobs from the current session with friendly names that end with \*batch\*\*, including jobs that are running.</span></span>

```powershell
Remove-Job -Name *batch -Force
```

<span data-ttu-id="fe221-141">`Remove-Job`**name** 매개 변수를 사용 하 여 작업 이름 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-141">`Remove-Job` uses the **Name** parameter to specify a job name pattern.</span></span> <span data-ttu-id="fe221-142">패턴에는 `*` **batch** 로 끝나는 모든 작업 이름을 찾기 위한 별표 () 와일드 카드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-142">The pattern includes the asterisk (`*`) wildcard to find all job names that end with **batch**.</span></span> <span data-ttu-id="fe221-143">**Force** 매개 변수는를 실행 하는 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-143">The **Force** parameter deletes jobs that running.</span></span>

### <span data-ttu-id="fe221-144">예 5: Invoke-Command 여 만든 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fe221-144">Example 5: Delete a job that was created by Invoke-Command</span></span>

<span data-ttu-id="fe221-145">이 예에서는를 사용 하 여 원격 컴퓨터에서 시작 된 작업을 `Invoke-Command` **AsJob** 매개 변수와 함께 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-145">This example removes a job that was started on a remote computer using `Invoke-Command` with the **AsJob** parameter.</span></span>

<span data-ttu-id="fe221-146">이 예제에서는 **AsJob** 매개 변수를 사용 하기 때문에 작업 개체는 로컬 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-146">Because the example uses the **AsJob** parameter, the job object is created on the local computer.</span></span>
<span data-ttu-id="fe221-147">그러나이 작업은 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-147">But, the job runs on a remote computer.</span></span> <span data-ttu-id="fe221-148">따라서 로컬 명령을 사용하여 작업을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-148">As a result, you use local commands to manage the job.</span></span>

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

<span data-ttu-id="fe221-149">`Invoke-Command`**Server01** 컴퓨터에서 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-149">`Invoke-Command` runs a job on the **Server01** computer.</span></span> <span data-ttu-id="fe221-150">**AsJob** 매개 변수는 **ScriptBlock** 을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-150">The **AsJob** parameter runs the **ScriptBlock** as a background job.</span></span> <span data-ttu-id="fe221-151">작업 개체는 변수에 저장 됩니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-151">The job object is stored in the `$job` variable.</span></span> <span data-ttu-id="fe221-152">`$job`변수 개체는 파이프라인에서로 전송 됩니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-152">The `$job` variable object is sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="fe221-153">예 6: Invoke-Command 및 Start-Job에서 만든 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fe221-153">Example 6: Delete a job that was created by Invoke-Command and Start-Job</span></span>

<span data-ttu-id="fe221-154">이 예제에서는를 실행 하 여를 실행 하는 원격 컴퓨터에서 작업을 제거 하는 방법을 보여 줍니다 `Invoke-Command` `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-154">This example shows how to remove a job on a remote computer that was started by using `Invoke-Command` to run `Start-Job`.</span></span> <span data-ttu-id="fe221-155">작업 개체는 원격 컴퓨터에서 만들어지며 원격 명령은 작업을 관리 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-155">The job object is created on the remote computer and remote commands are used to manage the job.</span></span> <span data-ttu-id="fe221-156">원격 명령을 실행 하는 경우 영구 연결이 필요 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-156">A persistent connection is required when running a remote `Start-Job` command.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

<span data-ttu-id="fe221-157">`New-PSSession`**Server01** 컴퓨터에 대 한 **PSSession**(영구 연결)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-157">`New-PSSession` creates a **PSSession**, a persistent connection, to the **Server01** computer.</span></span> <span data-ttu-id="fe221-158">연결은 변수에 저장 됩니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="fe221-158">The connection is saved in the `$S` variable.</span></span>

<span data-ttu-id="fe221-159">`Invoke-Command` 에 저장 된 세션에 연결 `$S` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-159">`Invoke-Command` connects to the session saved in `$S`.</span></span> <span data-ttu-id="fe221-160">**ScriptBlock** 은 `Start-Job` 를 사용 하 여 원격 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-160">The **ScriptBlock** uses `Start-Job` to start a remote job.</span></span> <span data-ttu-id="fe221-161">작업은 명령을 실행 하 `Get-Process` 고 **name** 매개 변수를 사용 하 여 친숙 한 작업 이름 **myjob** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-161">The job runs a `Get-Process` command and uses the **Name** parameter to specify a friendly job name, **MyJob**.</span></span>

<span data-ttu-id="fe221-162">`Invoke-Command` 세션을 사용 하 `$S` 고를 실행 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-162">`Invoke-Command` uses the `$S` session and runs `Remove-Job`.</span></span> <span data-ttu-id="fe221-163">**Name** 매개 변수는 **myjob** 이라는 작업을 삭제 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-163">The **Name** parameter specifies that the job named **MyJob** is deleted.</span></span>

### <span data-ttu-id="fe221-164">예 7: InstanceId를 사용 하 여 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fe221-164">Example 7: Delete a job by using its InstanceId</span></span>

<span data-ttu-id="fe221-165">이 예에서는 **InstanceId** 를 기준으로 작업을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-165">This example removes a job based on its **InstanceId**.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="fe221-166">`Start-Job` 백그라운드 작업을 시작 하 고 작업 개체가 변수에 저장 됩니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-166">`Start-Job` starts a background job and the job object is saved in the `$job` variable.</span></span>

<span data-ttu-id="fe221-167">의 개체는 `$job` 파이프라인에서로 전송 됩니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="fe221-167">The object in `$job` is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="fe221-168">**Property** 매개 변수는 별표 ()를 사용 하 여 `*` 모든 개체의 속성이 목록에 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-168">The **Property** parameter uses an asterisk (`*`) to specify that all the object's properties are displayed in a list.</span></span>

<span data-ttu-id="fe221-169">`Remove-Job`**InstanceId** 매개 변수를 사용 하 여 삭제할 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-169">`Remove-Job` uses the **InstanceId** parameter to specify the job to delete.</span></span>

## <span data-ttu-id="fe221-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fe221-170">PARAMETERS</span></span>

### <span data-ttu-id="fe221-171">-Command</span><span class="sxs-lookup"><span data-stu-id="fe221-171">-Command</span></span>

<span data-ttu-id="fe221-172">지정한 단어가 명령에 포함된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-172">Deletes jobs that include the specified words in the command.</span></span> <span data-ttu-id="fe221-173">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-173">You can enter a comma-separated array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe221-174">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fe221-174">-Confirm</span></span>

<span data-ttu-id="fe221-175">을 실행 하기 전에 확인 메시지를 표시 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-175">Prompts you for confirmation before `Remove-Job` is run.</span></span>

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

### <span data-ttu-id="fe221-176">-Filter</span><span class="sxs-lookup"><span data-stu-id="fe221-176">-Filter</span></span>

<span data-ttu-id="fe221-177">연결 된 해시 테이블에 설정 된 모든 조건을 충족 하는 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-177">Deletes jobs that satisfy all the conditions established in the associated hash table.</span></span> <span data-ttu-id="fe221-178">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-178">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="fe221-179">이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-179">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="fe221-180">을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-180">It doesn't work on standard background jobs, such as those created by using the `Start-Job`.</span></span>

<span data-ttu-id="fe221-181">이 매개 변수는 PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-181">This parameter is introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe221-182">-Force</span><span class="sxs-lookup"><span data-stu-id="fe221-182">-Force</span></span>

<span data-ttu-id="fe221-183">작업 상태를 **실행** 하는 경우에도 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-183">Deletes a job even if the job's state is **Running**.</span></span> <span data-ttu-id="fe221-184">**Force** 매개 변수가 지정 되지 않은 경우는 `Remove-Job` 실행 중인 작업을 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-184">If the **Force** parameter isn't specified, `Remove-Job` doesn't delete running jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe221-185">-Id</span><span class="sxs-lookup"><span data-stu-id="fe221-185">-Id</span></span>

<span data-ttu-id="fe221-186">지정 된 **Id** 를 가진 백그라운드 작업을 삭제 합니다. 쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-186">Deletes background jobs with the specified **Id**. You can enter a comma-separated array.</span></span> <span data-ttu-id="fe221-187">작업 **Id** 는 현재 세션 내에서 작업을 식별 하는 고유한 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-187">The job's **Id** is a unique integer that identifies a job within the current session.</span></span>

<span data-ttu-id="fe221-188">작업 **Id** 를 찾으려면 `Get-Job` 매개 변수 없이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-188">To find a job's **Id**, use `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe221-189">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="fe221-189">-InstanceId</span></span>

<span data-ttu-id="fe221-190">지정 된 **InstanceId** 를 사용 하 여 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-190">Deletes jobs with the specified **InstanceId**.</span></span> <span data-ttu-id="fe221-191">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-191">You can enter a comma-separated array.</span></span> <span data-ttu-id="fe221-192">**InstanceId** 는 작업을 식별 하는 고유 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-192">An **InstanceId** is a unique GUID that identifies a job.</span></span>

<span data-ttu-id="fe221-193">작업의 **InstanceId** 를 찾으려면를 사용 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-193">To find a job's **InstanceId**, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe221-194">-Job</span><span class="sxs-lookup"><span data-stu-id="fe221-194">-Job</span></span>

<span data-ttu-id="fe221-195">삭제할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-195">Specifies the jobs to be deleted.</span></span> <span data-ttu-id="fe221-196">작업이 포함된 변수 또는 작업을 가져오는 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-196">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="fe221-197">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-197">You can enter a comma-separated array.</span></span>

<span data-ttu-id="fe221-198">파이프라인에서 작업 개체를로 보낼 수 있습니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-198">You can send job objects down the pipeline to `Remove-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fe221-199">-Name</span><span class="sxs-lookup"><span data-stu-id="fe221-199">-Name</span></span>

<span data-ttu-id="fe221-200">지정한 이름을 가진 작업만 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-200">Only deletes jobs with the specified friendly name.</span></span> <span data-ttu-id="fe221-201">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-201">Wildcards are permitted.</span></span> <span data-ttu-id="fe221-202">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-202">You can enter a comma-separated array.</span></span>

<span data-ttu-id="fe221-203">작업 이름은 PowerShell 세션 내 에서도 고유 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-203">Friendly names for jobs aren't guaranteed to be unique, even within a PowerShell session.</span></span> <span data-ttu-id="fe221-204">이름을 기준으로 파일을 삭제 하는 경우 **WhatIf** 및 **Confirm** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-204">Use the **WhatIf** and **Confirm** parameters when you delete files by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fe221-205">-상태</span><span class="sxs-lookup"><span data-stu-id="fe221-205">-State</span></span>

<span data-ttu-id="fe221-206">지정 된 상태의 작업만 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-206">Only deletes jobs with the specified state.</span></span> <span data-ttu-id="fe221-207">**실행** 상태의 작업을 삭제 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-207">To delete jobs with a state of **Running**, use the **Force** parameter.</span></span>

<span data-ttu-id="fe221-208">허용 되는 값:</span><span class="sxs-lookup"><span data-stu-id="fe221-208">Accepted values:</span></span>

- <span data-ttu-id="fe221-209">AtBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fe221-209">AtBreakpoint</span></span>
- <span data-ttu-id="fe221-210">차단</span><span class="sxs-lookup"><span data-stu-id="fe221-210">Blocked</span></span>
- <span data-ttu-id="fe221-211">완료됨</span><span class="sxs-lookup"><span data-stu-id="fe221-211">Completed</span></span>
- <span data-ttu-id="fe221-212">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="fe221-212">Disconnected</span></span>
- <span data-ttu-id="fe221-213">Failed</span><span class="sxs-lookup"><span data-stu-id="fe221-213">Failed</span></span>
- <span data-ttu-id="fe221-214">NotStarted</span><span class="sxs-lookup"><span data-stu-id="fe221-214">NotStarted</span></span>
- <span data-ttu-id="fe221-215">실행 중</span><span class="sxs-lookup"><span data-stu-id="fe221-215">Running</span></span>
- <span data-ttu-id="fe221-216">중지됨</span><span class="sxs-lookup"><span data-stu-id="fe221-216">Stopped</span></span>
- <span data-ttu-id="fe221-217">중지 중</span><span class="sxs-lookup"><span data-stu-id="fe221-217">Stopping</span></span>
- <span data-ttu-id="fe221-218">일시 중단</span><span class="sxs-lookup"><span data-stu-id="fe221-218">Suspended</span></span>
- <span data-ttu-id="fe221-219">Suspending</span><span class="sxs-lookup"><span data-stu-id="fe221-219">Suspending</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe221-220">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fe221-220">-WhatIf</span></span>

<span data-ttu-id="fe221-221">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-221">Shows what would happen if `Remove-Job` runs.</span></span> <span data-ttu-id="fe221-222">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-222">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="fe221-223">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe221-223">CommonParameters</span></span>

<span data-ttu-id="fe221-224">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fe221-224">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe221-225">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe221-225">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fe221-226">입력</span><span class="sxs-lookup"><span data-stu-id="fe221-226">INPUTS</span></span>

### <span data-ttu-id="fe221-227">System.object.</span><span class="sxs-lookup"><span data-stu-id="fe221-227">System.Management.Automation.Job</span></span>

<span data-ttu-id="fe221-228">파이프라인에서 작업 개체를로 보낼 수 있습니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="fe221-228">You can send a job object down the pipeline to `Remove-Job`.</span></span>

## <span data-ttu-id="fe221-229">출력</span><span class="sxs-lookup"><span data-stu-id="fe221-229">OUTPUTS</span></span>

### <span data-ttu-id="fe221-230">없음</span><span class="sxs-lookup"><span data-stu-id="fe221-230">None</span></span>

<span data-ttu-id="fe221-231">`Remove-Job` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-231">`Remove-Job` doesn't generate any output.</span></span>

## <span data-ttu-id="fe221-232">참고</span><span class="sxs-lookup"><span data-stu-id="fe221-232">NOTES</span></span>

<span data-ttu-id="fe221-233">PowerShell 작업에서 새 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-233">A PowerShell job creates a new process.</span></span> <span data-ttu-id="fe221-234">작업이 완료 되 면 프로세스가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-234">When the job completes, the process exits.</span></span> <span data-ttu-id="fe221-235">`Remove-Job`을 실행 하면 작업의 상태가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-235">When `Remove-Job` is run, the job's state is removed.</span></span>

<span data-ttu-id="fe221-236">작업이 완료 되기 전에 중지 되 고 해당 프로세스가 종료 되지 않으면 프로세스가 강제로 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe221-236">If a job stops before completion and its process hasn't exited, the process is forcibly terminated.</span></span>

## <span data-ttu-id="fe221-237">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fe221-237">RELATED LINKS</span></span>

[<span data-ttu-id="fe221-238">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="fe221-238">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="fe221-239">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="fe221-239">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="fe221-240">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="fe221-240">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="fe221-241">Get-Job</span><span class="sxs-lookup"><span data-stu-id="fe221-241">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="fe221-242">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="fe221-242">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="fe221-243">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="fe221-243">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="fe221-244">Start-Job</span><span class="sxs-lookup"><span data-stu-id="fe221-244">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="fe221-245">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="fe221-245">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="fe221-246">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="fe221-246">Wait-Job</span></span>](Wait-Job.md)

