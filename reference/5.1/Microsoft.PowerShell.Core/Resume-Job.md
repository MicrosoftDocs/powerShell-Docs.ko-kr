---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 6d08d9053e100cb53d37a6e4931d118f90c35a6a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388538"
---
# <span data-ttu-id="6c1f5-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-103">Resume-Job</span></span>

## <span data-ttu-id="6c1f5-104">개요</span><span class="sxs-lookup"><span data-stu-id="6c1f5-104">SYNOPSIS</span></span>
<span data-ttu-id="6c1f5-105">일시 중단된 작업을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="6c1f5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6c1f5-106">SYNTAX</span></span>

### <span data-ttu-id="6c1f5-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="6c1f5-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c1f5-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="6c1f5-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c1f5-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6c1f5-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c1f5-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6c1f5-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c1f5-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="6c1f5-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6c1f5-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="6c1f5-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6c1f5-113">설명</span><span class="sxs-lookup"><span data-stu-id="6c1f5-113">DESCRIPTION</span></span>

<span data-ttu-id="6c1f5-114">Cmdlet은 `Resume-Job` `Suspend-Job` cmdlet 또는 [about_Suspend 워크플로](../PSWorkflow/about/about_Suspend-Workflow.md) 작업을 사용 하는 등 일시 중단 된 워크플로 작업을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-114">The `Resume-Job` cmdlet resumes a workflow job that was suspended, such as by using the `Suspend-Job` cmdlet or the [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) activity.</span></span> <span data-ttu-id="6c1f5-115">워크플로 작업이 다시 시작 되 면 작업 엔진은 검사점과 같은 저장 된 리소스에서 상태, 메타 데이터 및 출력을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span> <span data-ttu-id="6c1f5-116">상태 또는 데이터의 손실 없이 작업이 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="6c1f5-117">작업 상태가 **Suspended** 에서 **Running** 으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-117">The job state is changed from **Suspended** to **Running**.</span></span>

<span data-ttu-id="6c1f5-118">의 매개 변수를 사용 `Resume-Job` 하 여 이름, ID, 인스턴스 id 또는 cmdlet에서 반환 된 작업 개체 (예: cmdlet에서 반환 되는 개체)에 대 한 파이프로 작업을 선택 `Get-Job` `Resume-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-118">Use the parameters of `Resume-Job` to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the `Get-Job` cmdlet, to `Resume-Job`.</span></span> <span data-ttu-id="6c1f5-119">속성 필터를 사용하여 다시 시작할 작업을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="6c1f5-120">`Resume-Job`모든 작업이 아직 다시 시작 되지 않은 경우에도 기본적으로는 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-120">By default, `Resume-Job` returns immediately, even though all jobs might not yet be resumed.</span></span> <span data-ttu-id="6c1f5-121">지정한 모든 작업이 다시 시작될 때까지 명령 프롬프트를 표시하지 않으려면 **Wait** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-121">To suppress the command prompt until all specified jobs are resumed, use the **Wait** parameter.</span></span>

<span data-ttu-id="6c1f5-122">`Resume-Job`Cmdlet은 워크플로 작업과 같은 사용자 지정 작업 유형 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-122">The `Resume-Job` cmdlet works only on custom job types, such as workflow jobs.</span></span> <span data-ttu-id="6c1f5-123">Cmdlet을 사용 하 여 시작한 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="6c1f5-123">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="6c1f5-124">지원 되지 않는 유형의 작업을 제출 하는 경우에서 `Resume-Job` 종료 오류를 생성 하 고 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-124">If you submit a job of an unsupported type, `Resume-Job` generates a terminating error and stops running.</span></span>

<span data-ttu-id="6c1f5-125">워크플로 작업을 식별하려면 작업의 **PSJobTypeName** 속성에서 **PSWorkflowJob** 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="6c1f5-126">특정 사용자 지정 작업 유형이 cmdlet을 지원 하는지 여부를 확인 하려면 `Resume-Job` 사용자 지정 작업 유형에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-126">To determine whether a particular custom job type supports the `Resume-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="6c1f5-127">사용자 지정 작업 유형에 대해 Job cmdlet을 사용 하기 전에 cmdlet을 사용 `Import-Module` 하거나 모듈에서 cmdlet을 가져오거나 사용 하 여 사용자 지정 작업 유형을 지 원하는 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the `Import-Module` cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="6c1f5-128">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6c1f5-129">예제</span><span class="sxs-lookup"><span data-stu-id="6c1f5-129">EXAMPLES</span></span>

### <span data-ttu-id="6c1f5-130">예제 1: ID로 작업 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6c1f5-130">Example 1: Resume a job by ID</span></span>

<span data-ttu-id="6c1f5-131">이 예제의 명령은 작업이 일시 중단된 워크플로 작업인지 확인한 다음 작업을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span> <span data-ttu-id="6c1f5-132">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Job` 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-132">The first command uses the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="6c1f5-133">출력은 작업이 일시 중단된 워크플로 작업임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-133">The output shows that the job is a suspended workflow job.</span></span> <span data-ttu-id="6c1f5-134">두 번째 명령은 cmdlet의 **id** 매개 변수를 사용 `Resume-Job` 하 여 **id** 값이 4 인 작업을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-134">The second command uses the **Id** parameter of the `Resume-Job` cmdlet to resume the job with an **Id** value of 4.</span></span>

```
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

PS C:\> Resume-Job -Id 4
```

### <span data-ttu-id="6c1f5-135">예 2: 이름으로 작업 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6c1f5-135">Example 2: Resume a job by name</span></span>

<span data-ttu-id="6c1f5-136">이 명령은 **Name** 매개 변수를 사용하여 로컬 컴퓨터에서 여러 개의 워크플로 작업을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-136">This command uses the **Name** parameter to resume several workflow jobs on the local computer.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

### <span data-ttu-id="6c1f5-137">예제 3: 사용자 지정 속성 값 사용</span><span class="sxs-lookup"><span data-stu-id="6c1f5-137">Example 3: Use custom property values</span></span>

<span data-ttu-id="6c1f5-138">이 명령은 사용자 지정 속성 값을 사용하여 다시 시작할 워크플로 작업을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-138">This command uses the value of a custom property to identify the workflow job to resume.</span></span> <span data-ttu-id="6c1f5-139">**Filter** 매개 변수를 사용하여 **CustomID** 속성으로 워크플로 작업을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-139">It uses the **Filter** parameter to identify the workflow job by its **CustomID** property.</span></span> <span data-ttu-id="6c1f5-140">또한 **State** 매개 변수를 사용하여 다시 시작하기 전에 워크플로 작업이 일시 중단되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-140">It also uses the **State** parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

### <span data-ttu-id="6c1f5-141">예제 4: 원격 컴퓨터에서 모든 일시 중단 된 작업 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6c1f5-141">Example 4: Resume all suspended jobs on a remote computer</span></span>

<span data-ttu-id="6c1f5-142">이 명령은 Srv01 원격 컴퓨터에서 모든 일시 중단된 작업을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-142">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="6c1f5-143">이 명령은 cmdlet을 사용 `Invoke-Command` 하 여 Srv01 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-143">The command uses the `Invoke-Command` cmdlet to run a command on the Srv01 computer.</span></span> <span data-ttu-id="6c1f5-144">원격 명령은 cmdlet의 **State** 매개 변수를 사용 하 여 `Get-Job` 컴퓨터의 모든 일시 중단 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-144">The remote command uses the **State** parameter of the `Get-Job` cmdlet to get all suspended jobs on the computer.</span></span> <span data-ttu-id="6c1f5-145">파이프라인 연산자 ( `|` )는 일시 중단 된 작업을 다시 시작 하는 cmdlet으로 보냅니다 `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="6c1f5-145">A pipeline operator (`|`) sends the suspended jobs to the `Resume-Job` cmdlet, which resumes them.</span></span>

### <span data-ttu-id="6c1f5-146">예 5: 작업이 다시 시작 될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="6c1f5-146">Example 5: Wait for jobs to resume</span></span>

<span data-ttu-id="6c1f5-147">이 명령은 **Wait** `Resume-Job` 지정 된 모든 작업이 다시 시작 된 후에만 Wait 매개 변수를 사용 하 여를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-147">This command uses the **Wait** parameter to direct `Resume-Job` to return only after all specified jobs are resumed.</span></span> <span data-ttu-id="6c1f5-148">**Wait** 매개 변수는 작업이 다시 시작된 후 스크립트가 계속된다고 가정하는 스크립트에서 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-148">The **Wait** parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

### <span data-ttu-id="6c1f5-149">예제 6: 자신을 일시 중단 하는 워크플로 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6c1f5-149">Example 6: Resume a workflow that suspends itself</span></span>

<span data-ttu-id="6c1f5-150">이 코드 샘플은 워크플로의 활동을 보여 줍니다 `Suspend-Workflow` .</span><span class="sxs-lookup"><span data-stu-id="6c1f5-150">This code sample shows the `Suspend-Workflow` activity in a workflow.</span></span>

<span data-ttu-id="6c1f5-151">`Test-Suspend`Server01 컴퓨터의 워크플로입니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-151">The `Test-Suspend` workflow on the Server01 computer.</span></span> <span data-ttu-id="6c1f5-152">워크플로를 실행 하면 워크플로는 활동을 실행 `Get-Date` 하 고 결과를 `$a` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-152">When you run the workflow, the workflow runs the `Get-Date` activity and stores the result in the `$a` variable.</span></span> <span data-ttu-id="6c1f5-153">그런 다음 작업을 실행 `Suspend-Workflow` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-153">Then it runs the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="6c1f5-154">이에 대한 응답으로 검사점을 사용하고 워크플로를 일시 중단한 다음 워크플로 작업 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-154">In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.</span></span> <span data-ttu-id="6c1f5-155">`Suspend-Workflow` 워크플로가 명시적으로 작업으로 실행 되지 않는 경우에도 워크플로 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-155">`Suspend-Workflow` returns a workflow job object even if the workflow is not explicitly run as a job.</span></span>

<span data-ttu-id="6c1f5-156">`Resume-Job``Test-Suspend`Job8에서 워크플로를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-156">`Resume-Job` resumes the `Test-Suspend` workflow in Job8.</span></span> <span data-ttu-id="6c1f5-157">**Wait** 매개 변수를 사용하여 작업이 다시 시작될 때까지 명령 프롬프트를 보류합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-157">It uses the **Wait** parameter to hold the command prompt until the job is resumed.</span></span>

<span data-ttu-id="6c1f5-158">`Receive-Job`Cmdlet은 워크플로의 결과를 가져옵니다 `Test-Suspend` .</span><span class="sxs-lookup"><span data-stu-id="6c1f5-158">The `Receive-Job` cmdlet gets the results of the `Test-Suspend` workflow.</span></span> <span data-ttu-id="6c1f5-159">워크플로의 마지막 명령은 현재 날짜 및 시간과 **TimeSpan** `$a` 워크플로가 일시 중단 되기 전에 변수에 저장 된 날짜 및 시간 사이의 경과 시간을 나타내는 TimeSpan 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-159">The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the `$a` variable before the workflow was suspended.</span></span>

```
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

<span data-ttu-id="6c1f5-160">`Resume-Job`Cmdlet을 사용 하면 작업을 사용 하 여 일시 중단 된 워크플로 작업을 다시 시작할 수 있습니다 `Suspend-Workflow` .</span><span class="sxs-lookup"><span data-stu-id="6c1f5-160">The `Resume-Job` cmdlet lets you resume a workflow job that was suspend by using the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="6c1f5-161">이 활동은 워크플로 내에서 워크플로를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-161">This activity suspends a workflow from within a workflow.</span></span> <span data-ttu-id="6c1f5-162">이는 워크플로에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-162">It is valid only in workflows.</span></span>

<span data-ttu-id="6c1f5-163">에 대 한 자세한 내용은 `Suspend-Workflow` About_Suspend 워크플로를 참조 하세요. /PSWorkflow/about/about_Suspend.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-163">For information about the `Suspend-Workflow`, see about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md).</span></span>

## <span data-ttu-id="6c1f5-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6c1f5-164">PARAMETERS</span></span>

### <span data-ttu-id="6c1f5-165">-Filter</span><span class="sxs-lookup"><span data-stu-id="6c1f5-165">-Filter</span></span>

<span data-ttu-id="6c1f5-166">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-166">Specifies a hash table of conditions.</span></span> <span data-ttu-id="6c1f5-167">이 cmdlet은 해시 테이블의 모든 조건을 충족 하는 작업을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-167">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="6c1f5-168">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-168">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="6c1f5-169">-Id</span><span class="sxs-lookup"><span data-stu-id="6c1f5-169">-Id</span></span>

<span data-ttu-id="6c1f5-170">이 cmdlet이 다시 시작 하는 작업의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-170">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="6c1f5-171">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-171">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="6c1f5-172">인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-172">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="6c1f5-173">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-173">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="6c1f5-174">작업 ID를 찾으려면를 실행 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-174">To find the ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="6c1f5-175">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6c1f5-175">-InstanceId</span></span>

<span data-ttu-id="6c1f5-176">이 cmdlet이 다시 시작 하는 작업의 인스턴스 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-176">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="6c1f5-177">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-177">The default is all jobs.</span></span>

<span data-ttu-id="6c1f5-178">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-178">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="6c1f5-179">작업의 인스턴스 ID를 찾으려면를 실행 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-179">To find the instance ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="6c1f5-180">-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-180">-Job</span></span>

<span data-ttu-id="6c1f5-181">다시 시작할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-181">Specifies the jobs to be resumed.</span></span> <span data-ttu-id="6c1f5-182">작업이 포함된 변수 또는 작업을 가져오는 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-182">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="6c1f5-183">작업을 cmdlet으로 파이프 할 수도 있습니다 `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="6c1f5-183">You can also pipe jobs to the `Resume-Job` cmdlet.</span></span>

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

### <span data-ttu-id="6c1f5-184">-Name</span><span class="sxs-lookup"><span data-stu-id="6c1f5-184">-Name</span></span>

<span data-ttu-id="6c1f5-185">이 cmdlet이 다시 시작 하는 작업의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-185">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="6c1f5-186">작업 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-186">Enter one or more job names.</span></span>
<span data-ttu-id="6c1f5-187">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-187">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c1f5-188">-상태</span><span class="sxs-lookup"><span data-stu-id="6c1f5-188">-State</span></span>

<span data-ttu-id="6c1f5-189">다시 시작할 작업의 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-189">Specifies the state of jobs to resume.</span></span> <span data-ttu-id="6c1f5-190">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6c1f5-191">NotStarted</span><span class="sxs-lookup"><span data-stu-id="6c1f5-191">NotStarted</span></span>
- <span data-ttu-id="6c1f5-192">실행 중</span><span class="sxs-lookup"><span data-stu-id="6c1f5-192">Running</span></span>
- <span data-ttu-id="6c1f5-193">완료됨</span><span class="sxs-lookup"><span data-stu-id="6c1f5-193">Completed</span></span>
- <span data-ttu-id="6c1f5-194">실패</span><span class="sxs-lookup"><span data-stu-id="6c1f5-194">Failed</span></span>
- <span data-ttu-id="6c1f5-195">중지됨</span><span class="sxs-lookup"><span data-stu-id="6c1f5-195">Stopped</span></span>
- <span data-ttu-id="6c1f5-196">차단</span><span class="sxs-lookup"><span data-stu-id="6c1f5-196">Blocked</span></span>
- <span data-ttu-id="6c1f5-197">일시 중단</span><span class="sxs-lookup"><span data-stu-id="6c1f5-197">Suspended</span></span>
- <span data-ttu-id="6c1f5-198">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="6c1f5-198">Disconnected</span></span>
- <span data-ttu-id="6c1f5-199">Suspending</span><span class="sxs-lookup"><span data-stu-id="6c1f5-199">Suspending</span></span>
- <span data-ttu-id="6c1f5-200">중지 중</span><span class="sxs-lookup"><span data-stu-id="6c1f5-200">Stopping</span></span>

<span data-ttu-id="6c1f5-201">이 cmdlet은 **일시 중단** 상태의 작업만 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-201">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="6c1f5-202">작업 상태에 대 한 자세한 내용은 [JobState 열거](/dotnet/api/system.management.automation.jobstate)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-202">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c1f5-203">-Wait</span><span class="sxs-lookup"><span data-stu-id="6c1f5-203">-Wait</span></span>

<span data-ttu-id="6c1f5-204">모든 작업 결과가 다시 시작 될 때까지이 cmdlet이 명령 프롬프트를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-204">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span> <span data-ttu-id="6c1f5-205">기본적으로이 cmdlet은 사용 가능한 결과를 즉시 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-205">By default, this cmdlet immediately returns the available results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6c1f5-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6c1f5-206">-Confirm</span></span>

<span data-ttu-id="6c1f5-207">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6c1f5-208">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6c1f5-208">-WhatIf</span></span>

<span data-ttu-id="6c1f5-209">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-209">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6c1f5-210">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-210">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6c1f5-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c1f5-211">CommonParameters</span></span>

<span data-ttu-id="6c1f5-212">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6c1f5-213">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6c1f5-214">입력</span><span class="sxs-lookup"><span data-stu-id="6c1f5-214">INPUTS</span></span>

### <span data-ttu-id="6c1f5-215">System.object.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-215">System.Management.Automation.Job</span></span>

<span data-ttu-id="6c1f5-216">모든 유형의 작업을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-216">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="6c1f5-217">에서 `Resume-Job` 지원 되지 않는 형식의 작업을 가져오는 경우 종료 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-217">If `Resume-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="6c1f5-218">출력</span><span class="sxs-lookup"><span data-stu-id="6c1f5-218">OUTPUTS</span></span>

### <span data-ttu-id="6c1f5-219">없음, 시스템 관리. 작업</span><span class="sxs-lookup"><span data-stu-id="6c1f5-219">None, System.Management.Automation.Job</span></span>

<span data-ttu-id="6c1f5-220">이 cmdlet은 **PassThru** 매개 변수를 사용 하는 경우 다시 시작 하려고 하는 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-220">This cmdlet returns the jobs that it tries to resume, if you use the **PassThru** parameter.</span></span>
<span data-ttu-id="6c1f5-221">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-221">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6c1f5-222">참고</span><span class="sxs-lookup"><span data-stu-id="6c1f5-222">NOTES</span></span>

- <span data-ttu-id="6c1f5-223">`Resume-Job` 일시 중단 된 작업만 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-223">`Resume-Job` can only resume jobs that are suspended.</span></span> <span data-ttu-id="6c1f5-224">다른 상태로 작업을 제출 하는 경우은 `Resume-Job` 작업에서 다시 시작 작업을 실행 하지만 작업을 다시 시작할 수 없음을 알리는 경고를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-224">If you submit a job in a different state, `Resume-Job` runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="6c1f5-225">이 경고를 표시 하지 않으려면 SilentlyContinue의 값과 함께 **WarningAction** 일반 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-225">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>
- <span data-ttu-id="6c1f5-226">작업이 워크플로 작업 ( **PSWorkflowJob** )과 같은 다시 시작을 지 원하는 형식이 아닌 경우 `Resume-Job` 종료 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-226">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), `Resume-Job` returns a terminating error.</span></span>
- <span data-ttu-id="6c1f5-227">일시 중단된 작업을 저장하는 메커니즘과 위치는 작업 유형에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-227">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="6c1f5-228">예를 들어 일시 중단된 워크플로 작업은 기본적으로 플랫 파일 저장소에 저장되지만 SQL 데이터베이스에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-228">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
- <span data-ttu-id="6c1f5-229">작업을 다시 시작하면 작업 상태가 **Suspended** 에서 **Running** 으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-229">When you resume a job, the job state changes from **Suspended** to **Running**.</span></span> <span data-ttu-id="6c1f5-230">이 cmdlet에 의해 다시 시작 된 작업을 포함 하 여 실행 중인 작업을 찾으려면 cmdlet의 **state** 매개 변수를 사용 `Get-Job` 하 여 **실행 중인** 상태로 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-230">To find the jobs that are running, including those that were resumed by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get jobs in the **Running** state.</span></span>
- <span data-ttu-id="6c1f5-231">일부 작업 유형에는 Windows PowerShell에서 작업을 일시 중단할 수 없게 하는 옵션 또는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-231">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="6c1f5-232">작업을 일시 중단 하려는 시도가 실패 한 경우 작업 옵션 및 속성이 일시 중단을 허용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c1f5-232">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="6c1f5-233">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6c1f5-233">RELATED LINKS</span></span>

[<span data-ttu-id="6c1f5-234">Get-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="6c1f5-235">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-235">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="6c1f5-236">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-236">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="6c1f5-237">Start-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-237">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="6c1f5-238">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-238">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="6c1f5-239">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-239">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="6c1f5-240">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="6c1f5-240">Wait-Job</span></span>](Wait-Job.md)
