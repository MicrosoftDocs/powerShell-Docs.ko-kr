---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: b65e990c8d03858705b167bd1712ab6fde305a82
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217025"
---
# <span data-ttu-id="01203-103">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="01203-103">Remove-Job</span></span>

## <span data-ttu-id="01203-104">개요</span><span class="sxs-lookup"><span data-stu-id="01203-104">SYNOPSIS</span></span>
<span data-ttu-id="01203-105">PowerShell 백그라운드 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-105">Deletes a PowerShell background job.</span></span>

## <span data-ttu-id="01203-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01203-106">SYNTAX</span></span>

### <span data-ttu-id="01203-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="01203-107">SessionIdParameterSet (Default)</span></span>

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="01203-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="01203-108">JobParameterSet</span></span>

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="01203-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="01203-109">NameParameterSet</span></span>

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="01203-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="01203-110">InstanceIdParameterSet</span></span>

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="01203-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="01203-111">FilterParameterSet</span></span>

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="01203-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="01203-112">StateParameterSet</span></span>

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="01203-113">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="01203-113">CommandParameterSet</span></span>

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="01203-114">설명</span><span class="sxs-lookup"><span data-stu-id="01203-114">DESCRIPTION</span></span>

<span data-ttu-id="01203-115">`Remove-Job`Cmdlet은 `Start-Job` Cmdlet 또는 `Invoke-Command` **AsJob** 매개 변수를 지 원하는 Cmdlet에 의해 시작 된 PowerShell 백그라운드 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-115">The `Remove-Job` cmdlet deletes PowerShell background jobs that were started by the `Start-Job` cmdlet or by cmdlets such as `Invoke-Command` that support the **AsJob** parameter.</span></span>

<span data-ttu-id="01203-116">`Remove-Job`를 사용 하 여 모든 작업을 삭제 하거나 선택한 작업을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-116">You can use `Remove-Job` to delete all jobs or delete selected jobs.</span></span> <span data-ttu-id="01203-117">작업은 **이름** , **ID** , **인스턴스 id** , **명령** 또는 **상태로** 식별 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-117">The jobs are identified by their **Name** , **ID** , **Instance ID** , **Command** , or **State**.</span></span> <span data-ttu-id="01203-118">또는 파이프라인에서로 작업 개체를 보낼 수 있습니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-118">Or, a job object can be sent down the pipeline to `Remove-Job`.</span></span> <span data-ttu-id="01203-119">매개 변수 또는 매개 변수 값이 없으면는 영향을 주지 `Remove-Job` 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-119">Without parameters or parameter values, `Remove-Job` has no effect.</span></span>

<span data-ttu-id="01203-120">PowerShell 3.0부터는 `Remove-Job` 예약 된 작업 및 워크플로 작업과 같은 사용자 지정 작업 유형을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-120">Since PowerShell 3.0, `Remove-Job` can delete custom job types, such as scheduled jobs and workflow jobs.</span></span> <span data-ttu-id="01203-121">예를 들어는 예약 된 작업 `Remove-Job` , 디스크에 있는 예약 된 작업의 모든 인스턴스 및 모든 트리거된 작업 인스턴스의 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-121">For example, `Remove-Job` deletes the scheduled job, all instances of the scheduled job on disk, and the results of all triggered job instances.</span></span>

<span data-ttu-id="01203-122">실행 중인 작업을 삭제 하려고 하면이 `Remove-Job` 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-122">If you try to delete a running job, `Remove-Job` fails.</span></span> <span data-ttu-id="01203-123">Cmdlet을 사용 `Stop-Job` 하 여 실행 중인 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-123">Use the `Stop-Job` cmdlet to stop a running job.</span></span> <span data-ttu-id="01203-124">또는 `Remove-Job` **Force** 매개 변수와 함께를 사용 하 여 실행 중인 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-124">Or, use `Remove-Job` with the **Force** parameter to delete a running job.</span></span>

<span data-ttu-id="01203-125">백그라운드 작업을 삭제 하거나 PowerShell 세션을 닫을 때까지 작업이 전역 작업 캐시에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-125">Jobs remain in the global job cache until you delete the background job or close the PowerShell session.</span></span>

## <span data-ttu-id="01203-126">예제</span><span class="sxs-lookup"><span data-stu-id="01203-126">EXAMPLES</span></span>

### <span data-ttu-id="01203-127">예제 1: 이름을 사용 하 여 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="01203-127">Example 1: Delete a job by using its name</span></span>

<span data-ttu-id="01203-128">이 예제에서는 변수와 파이프라인을 사용 하 여 이름을 기준으로 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-128">This example uses a variable and the pipeline to delete a job by name.</span></span>

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

<span data-ttu-id="01203-129">`Get-Job`**Name** 매개 변수를 사용 하 여 **batchjob** 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-129">`Get-Job` uses the **Name** parameter to specify the job, **BatchJob**.</span></span> <span data-ttu-id="01203-130">작업 개체는 변수에 저장 됩니다 `$batch` .</span><span class="sxs-lookup"><span data-stu-id="01203-130">The job object is stored in the `$batch` variable.</span></span> <span data-ttu-id="01203-131">의 개체는 `$batch` 파이프라인에서로 전송 됩니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-131">The object in `$batch` is sent down the pipeline to `Remove-Job`.</span></span>

<span data-ttu-id="01203-132">대신 **작업** 매개 변수 (예:)를 사용 `Remove-Job -Job $batch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-132">An alternative is to use the **Job** parameter, such as `Remove-Job -Job $batch`.</span></span>

### <span data-ttu-id="01203-133">예 2: 세션의 모든 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="01203-133">Example 2: Delete all jobs in a session</span></span>

<span data-ttu-id="01203-134">이 예에서는 현재 PowerShell 세션의 모든 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-134">In this example, all the jobs in the current PowerShell session are deleted.</span></span>

```powershell
Get-job | Remove-Job
```

<span data-ttu-id="01203-135">`Get-Job` 현재 PowerShell 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="01203-135">`Get-Job` gets all the jobs in the current PowerShell session.</span></span> <span data-ttu-id="01203-136">작업 개체는 파이프라인에서로 전송 됩니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-136">The job objects are sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="01203-137">예 3: NotStarted 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="01203-137">Example 3: Delete NotStarted jobs</span></span>

<span data-ttu-id="01203-138">이 예에서는 현재 PowerShell 세션에서 아직 시작 되지 않은 모든 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-138">This example deletes all jobs from the current PowerShell session that haven't started.</span></span>

```powershell
Remove-Job -State NotStarted
```

<span data-ttu-id="01203-139">`Remove-Job`**State** 매개 변수를 사용 하 여 작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-139">`Remove-Job` uses the **State** parameter to specify the job status.</span></span>

### <span data-ttu-id="01203-140">예제 4: 친숙 한 이름을 사용 하 여 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="01203-140">Example 4: Delete jobs by using a friendly name</span></span>

<span data-ttu-id="01203-141">이 예에서는를 실행 하는 작업을 포함 하 여 이름이 \* batch \* \*로 끝나는 현재 세션에서 모든 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-141">This example deletes all jobs from the current session with friendly names that end with \*batch\*\*, including jobs that are running.</span></span>

```powershell
Remove-Job -Name *batch -Force
```

<span data-ttu-id="01203-142">`Remove-Job`**name** 매개 변수를 사용 하 여 작업 이름 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-142">`Remove-Job` uses the **Name** parameter to specify a job name pattern.</span></span> <span data-ttu-id="01203-143">패턴에는 `*` **batch** 로 끝나는 모든 작업 이름을 찾기 위한 별표 () 와일드 카드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-143">The pattern includes the asterisk (`*`) wildcard to find all job names that end with **batch**.</span></span> <span data-ttu-id="01203-144">**Force** 매개 변수는를 실행 하는 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-144">The **Force** parameter deletes jobs that running.</span></span>

### <span data-ttu-id="01203-145">예 5: Invoke-Command 여 만든 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="01203-145">Example 5: Delete a job that was created by Invoke-Command</span></span>

<span data-ttu-id="01203-146">이 예에서는를 사용 하 여 원격 컴퓨터에서 시작 된 작업을 `Invoke-Command` **AsJob** 매개 변수와 함께 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-146">This example removes a job that was started on a remote computer using `Invoke-Command` with the **AsJob** parameter.</span></span>

<span data-ttu-id="01203-147">이 예제에서는 **AsJob** 매개 변수를 사용 하기 때문에 작업 개체는 로컬 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="01203-147">Because the example uses the **AsJob** parameter, the job object is created on the local computer.</span></span>
<span data-ttu-id="01203-148">그러나이 작업은 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-148">But, the job runs on a remote computer.</span></span> <span data-ttu-id="01203-149">따라서 로컬 명령을 사용하여 작업을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-149">As a result, you use local commands to manage the job.</span></span>

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

<span data-ttu-id="01203-150">`Invoke-Command`**Server01** 컴퓨터에서 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-150">`Invoke-Command` runs a job on the **Server01** computer.</span></span> <span data-ttu-id="01203-151">**AsJob** 매개 변수는 **ScriptBlock** 을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-151">The **AsJob** parameter runs the **ScriptBlock** as a background job.</span></span> <span data-ttu-id="01203-152">작업 개체는 변수에 저장 됩니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="01203-152">The job object is stored in the `$job` variable.</span></span> <span data-ttu-id="01203-153">`$job`변수 개체는 파이프라인에서로 전송 됩니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-153">The `$job` variable object is sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="01203-154">예 6: Invoke-Command 및 Start-Job에서 만든 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="01203-154">Example 6: Delete a job that was created by Invoke-Command and Start-Job</span></span>

<span data-ttu-id="01203-155">이 예제에서는를 실행 하 여를 실행 하는 원격 컴퓨터에서 작업을 제거 하는 방법을 보여 줍니다 `Invoke-Command` `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-155">This example shows how to remove a job on a remote computer that was started by using `Invoke-Command` to run `Start-Job`.</span></span> <span data-ttu-id="01203-156">작업 개체는 원격 컴퓨터에서 만들어지며 원격 명령은 작업을 관리 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-156">The job object is created on the remote computer and remote commands are used to manage the job.</span></span> <span data-ttu-id="01203-157">원격 명령을 실행 하는 경우 영구 연결이 필요 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-157">A persistent connection is required when running a remote `Start-Job` command.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

<span data-ttu-id="01203-158">`New-PSSession`**Server01** 컴퓨터에 대 한 **PSSession** (영구 연결)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="01203-158">`New-PSSession` creates a **PSSession** , a persistent connection, to the **Server01** computer.</span></span> <span data-ttu-id="01203-159">연결은 변수에 저장 됩니다 `$S` .</span><span class="sxs-lookup"><span data-stu-id="01203-159">The connection is saved in the `$S` variable.</span></span>

<span data-ttu-id="01203-160">`Invoke-Command` 에 저장 된 세션에 연결 `$S` 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-160">`Invoke-Command` connects to the session saved in `$S`.</span></span> <span data-ttu-id="01203-161">**ScriptBlock** 은 `Start-Job` 를 사용 하 여 원격 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-161">The **ScriptBlock** uses `Start-Job` to start a remote job.</span></span> <span data-ttu-id="01203-162">작업은 명령을 실행 하 `Get-Process` 고 **name** 매개 변수를 사용 하 여 친숙 한 작업 이름 **myjob** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-162">The job runs a `Get-Process` command and uses the **Name** parameter to specify a friendly job name, **MyJob**.</span></span>

<span data-ttu-id="01203-163">`Invoke-Command` 세션을 사용 하 `$S` 고를 실행 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-163">`Invoke-Command` uses the `$S` session and runs `Remove-Job`.</span></span> <span data-ttu-id="01203-164">**Name** 매개 변수는 **myjob** 이라는 작업을 삭제 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-164">The **Name** parameter specifies that the job named **MyJob** is deleted.</span></span>

### <span data-ttu-id="01203-165">예 7: InstanceId를 사용 하 여 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="01203-165">Example 7: Delete a job by using its InstanceId</span></span>

<span data-ttu-id="01203-166">이 예에서는 **InstanceId** 를 기준으로 작업을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-166">This example removes a job based on its **InstanceId**.</span></span>

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

<span data-ttu-id="01203-167">`Start-Job` 백그라운드 작업을 시작 하 고 작업 개체가 변수에 저장 됩니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="01203-167">`Start-Job` starts a background job and the job object is saved in the `$job` variable.</span></span>

<span data-ttu-id="01203-168">의 개체는 `$job` 파이프라인에서로 전송 됩니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="01203-168">The object in `$job` is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="01203-169">**Property** 매개 변수는 별표 ()를 사용 하 여 `*` 모든 개체의 속성이 목록에 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-169">The **Property** parameter uses an asterisk (`*`) to specify that all the object's properties are displayed in a list.</span></span>

<span data-ttu-id="01203-170">`Remove-Job`**InstanceId** 매개 변수를 사용 하 여 삭제할 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-170">`Remove-Job` uses the **InstanceId** parameter to specify the job to delete.</span></span>

## <span data-ttu-id="01203-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="01203-171">PARAMETERS</span></span>

### <span data-ttu-id="01203-172">-Command</span><span class="sxs-lookup"><span data-stu-id="01203-172">-Command</span></span>

<span data-ttu-id="01203-173">지정한 단어가 명령에 포함된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-173">Deletes jobs that include the specified words in the command.</span></span> <span data-ttu-id="01203-174">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-174">You can enter a comma-separated array.</span></span>

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

### <span data-ttu-id="01203-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="01203-175">-Confirm</span></span>

<span data-ttu-id="01203-176">을 실행 하기 전에 확인 메시지를 표시 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-176">Prompts you for confirmation before `Remove-Job` is run.</span></span>

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

### <span data-ttu-id="01203-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="01203-177">-Filter</span></span>

<span data-ttu-id="01203-178">연결 된 해시 테이블에 설정 된 모든 조건을 충족 하는 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-178">Deletes jobs that satisfy all the conditions established in the associated hash table.</span></span> <span data-ttu-id="01203-179">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-179">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="01203-180">이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-180">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="01203-181">을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-181">It doesn't work on standard background jobs, such as those created by using the `Start-Job`.</span></span>

<span data-ttu-id="01203-182">이 매개 변수는 PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-182">This parameter is introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="01203-183">-Force</span><span class="sxs-lookup"><span data-stu-id="01203-183">-Force</span></span>

<span data-ttu-id="01203-184">작업 상태를 **실행** 하는 경우에도 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-184">Deletes a job even if the job's state is **Running**.</span></span> <span data-ttu-id="01203-185">**Force** 매개 변수가 지정 되지 않은 경우는 `Remove-Job` 실행 중인 작업을 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-185">If the **Force** parameter isn't specified, `Remove-Job` doesn't delete running jobs.</span></span>

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

### <span data-ttu-id="01203-186">-Id</span><span class="sxs-lookup"><span data-stu-id="01203-186">-Id</span></span>

<span data-ttu-id="01203-187">지정 된 **Id** 를 가진 백그라운드 작업을 삭제 합니다. 쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-187">Deletes background jobs with the specified **Id**. You can enter a comma-separated array.</span></span> <span data-ttu-id="01203-188">작업 **Id** 는 현재 세션 내에서 작업을 식별 하는 고유한 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="01203-188">The job's **Id** is a unique integer that identifies a job within the current session.</span></span>

<span data-ttu-id="01203-189">작업 **Id** 를 찾으려면 `Get-Job` 매개 변수 없이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-189">To find a job's **Id** , use `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="01203-190">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="01203-190">-InstanceId</span></span>

<span data-ttu-id="01203-191">지정 된 **InstanceId** 를 사용 하 여 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-191">Deletes jobs with the specified **InstanceId**.</span></span> <span data-ttu-id="01203-192">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-192">You can enter a comma-separated array.</span></span> <span data-ttu-id="01203-193">**InstanceId** 는 작업을 식별 하는 고유 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="01203-193">An **InstanceId** is a unique GUID that identifies a job.</span></span>

<span data-ttu-id="01203-194">작업의 **InstanceId** 를 찾으려면를 사용 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-194">To find a job's **InstanceId** , use `Get-Job`.</span></span>

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

### <span data-ttu-id="01203-195">-Job</span><span class="sxs-lookup"><span data-stu-id="01203-195">-Job</span></span>

<span data-ttu-id="01203-196">삭제할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-196">Specifies the jobs to be deleted.</span></span> <span data-ttu-id="01203-197">작업이 포함된 변수 또는 작업을 가져오는 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-197">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="01203-198">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-198">You can enter a comma-separated array.</span></span>

<span data-ttu-id="01203-199">파이프라인에서 작업 개체를로 보낼 수 있습니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-199">You can send job objects down the pipeline to `Remove-Job`.</span></span>

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

### <span data-ttu-id="01203-200">-Name</span><span class="sxs-lookup"><span data-stu-id="01203-200">-Name</span></span>

<span data-ttu-id="01203-201">지정한 이름을 가진 작업만 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-201">Only deletes jobs with the specified friendly name.</span></span> <span data-ttu-id="01203-202">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-202">Wildcards are permitted.</span></span> <span data-ttu-id="01203-203">쉼표로 구분 된 배열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-203">You can enter a comma-separated array.</span></span>

<span data-ttu-id="01203-204">작업 이름은 PowerShell 세션 내 에서도 고유 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-204">Friendly names for jobs aren't guaranteed to be unique, even within a PowerShell session.</span></span> <span data-ttu-id="01203-205">이름을 기준으로 파일을 삭제 하는 경우 **WhatIf** 및 **Confirm** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-205">Use the **WhatIf** and **Confirm** parameters when you delete files by name.</span></span>

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

### <span data-ttu-id="01203-206">-상태</span><span class="sxs-lookup"><span data-stu-id="01203-206">-State</span></span>

<span data-ttu-id="01203-207">지정 된 상태의 작업만 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-207">Only deletes jobs with the specified state.</span></span> <span data-ttu-id="01203-208">**실행** 상태의 작업을 삭제 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="01203-208">To delete jobs with a state of **Running** , use the **Force** parameter.</span></span>

<span data-ttu-id="01203-209">허용 되는 값:</span><span class="sxs-lookup"><span data-stu-id="01203-209">Accepted values:</span></span>

- <span data-ttu-id="01203-210">AtBreakpoint</span><span class="sxs-lookup"><span data-stu-id="01203-210">AtBreakpoint</span></span>
- <span data-ttu-id="01203-211">차단</span><span class="sxs-lookup"><span data-stu-id="01203-211">Blocked</span></span>
- <span data-ttu-id="01203-212">완료됨</span><span class="sxs-lookup"><span data-stu-id="01203-212">Completed</span></span>
- <span data-ttu-id="01203-213">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="01203-213">Disconnected</span></span>
- <span data-ttu-id="01203-214">실패</span><span class="sxs-lookup"><span data-stu-id="01203-214">Failed</span></span>
- <span data-ttu-id="01203-215">NotStarted</span><span class="sxs-lookup"><span data-stu-id="01203-215">NotStarted</span></span>
- <span data-ttu-id="01203-216">실행 중</span><span class="sxs-lookup"><span data-stu-id="01203-216">Running</span></span>
- <span data-ttu-id="01203-217">중지됨</span><span class="sxs-lookup"><span data-stu-id="01203-217">Stopped</span></span>
- <span data-ttu-id="01203-218">중지 중</span><span class="sxs-lookup"><span data-stu-id="01203-218">Stopping</span></span>
- <span data-ttu-id="01203-219">일시 중단</span><span class="sxs-lookup"><span data-stu-id="01203-219">Suspended</span></span>
- <span data-ttu-id="01203-220">Suspending</span><span class="sxs-lookup"><span data-stu-id="01203-220">Suspending</span></span>

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

### <span data-ttu-id="01203-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="01203-221">-WhatIf</span></span>

<span data-ttu-id="01203-222">가 실행 될 경우 발생 하는 상황을 보여 줍니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-222">Shows what would happen if `Remove-Job` runs.</span></span> <span data-ttu-id="01203-223">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-223">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="01203-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01203-224">CommonParameters</span></span>

<span data-ttu-id="01203-225">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01203-225">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01203-226">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01203-226">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01203-227">입력</span><span class="sxs-lookup"><span data-stu-id="01203-227">INPUTS</span></span>

### <span data-ttu-id="01203-228">System.object.</span><span class="sxs-lookup"><span data-stu-id="01203-228">System.Management.Automation.Job</span></span>

<span data-ttu-id="01203-229">파이프라인에서 작업 개체를로 보낼 수 있습니다 `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01203-229">You can send a job object down the pipeline to `Remove-Job`.</span></span>

## <span data-ttu-id="01203-230">출력</span><span class="sxs-lookup"><span data-stu-id="01203-230">OUTPUTS</span></span>

### <span data-ttu-id="01203-231">없음</span><span class="sxs-lookup"><span data-stu-id="01203-231">None</span></span>

<span data-ttu-id="01203-232">`Remove-Job` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01203-232">`Remove-Job` doesn't generate any output.</span></span>

## <span data-ttu-id="01203-233">참고</span><span class="sxs-lookup"><span data-stu-id="01203-233">NOTES</span></span>

<span data-ttu-id="01203-234">PowerShell 작업에서 새 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="01203-234">A PowerShell job creates a new process.</span></span> <span data-ttu-id="01203-235">작업이 완료 되 면 프로세스가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-235">When the job completes, the process exits.</span></span> <span data-ttu-id="01203-236">`Remove-Job`을 실행 하면 작업의 상태가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-236">When `Remove-Job` is run, the job's state is removed.</span></span>

<span data-ttu-id="01203-237">작업이 완료 되기 전에 중지 되 고 해당 프로세스가 종료 되지 않으면 프로세스가 강제로 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01203-237">If a job stops before completion and its process hasn't exited, the process is forcibly terminated.</span></span>

## <span data-ttu-id="01203-238">관련 링크</span><span class="sxs-lookup"><span data-stu-id="01203-238">RELATED LINKS</span></span>

[<span data-ttu-id="01203-239">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="01203-239">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="01203-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="01203-240">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="01203-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="01203-241">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="01203-242">Get-Job</span><span class="sxs-lookup"><span data-stu-id="01203-242">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="01203-243">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="01203-243">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="01203-244">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="01203-244">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="01203-245">Start-Job</span><span class="sxs-lookup"><span data-stu-id="01203-245">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="01203-246">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="01203-246">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="01203-247">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="01203-247">Wait-Job</span></span>](Wait-Job.md)

