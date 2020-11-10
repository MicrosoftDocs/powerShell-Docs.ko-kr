---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388470"
---
# <span data-ttu-id="6b9ff-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-103">Suspend-Job</span></span>

## <span data-ttu-id="6b9ff-104">개요</span><span class="sxs-lookup"><span data-stu-id="6b9ff-104">SYNOPSIS</span></span>
<span data-ttu-id="6b9ff-105">워크플로 작업을 일시적으로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="6b9ff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b9ff-106">SYNTAX</span></span>

### <span data-ttu-id="6b9ff-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="6b9ff-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6b9ff-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="6b9ff-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6b9ff-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6b9ff-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6b9ff-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6b9ff-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6b9ff-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="6b9ff-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6b9ff-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="6b9ff-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6b9ff-113">설명</span><span class="sxs-lookup"><span data-stu-id="6b9ff-113">DESCRIPTION</span></span>

<span data-ttu-id="6b9ff-114">`Suspend-Job`Cmdlet은 워크플로 작업을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-114">The `Suspend-Job` cmdlet suspends workflow jobs.</span></span> <span data-ttu-id="6b9ff-115">일시 중단은 워크플로 작업을 일시적으로 중단 하거나 일시 중지 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span> <span data-ttu-id="6b9ff-116">이 cmdlet을 사용하면 워크플로를 실행하는 사용자가 워크플로를 일시 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span> <span data-ttu-id="6b9ff-117">워크플로를 https://go.microsoft.com/fwlink/?LinkId=267141 일시 중단 하는 워크플로의 명령 인 일시 중단 워크플로 작업을 보완 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="6b9ff-118">`Suspend-Job`Cmdlet은 워크플로 작업 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-118">The `Suspend-Job` cmdlet works only on workflow jobs.</span></span> <span data-ttu-id="6b9ff-119">Cmdlet을 사용 하 여 시작한 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="6b9ff-119">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="6b9ff-120">워크플로 작업을 식별 하려면 작업의 **PSJobTypeName** 속성에서 PSWorkflowJob 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="6b9ff-121">특정 사용자 지정 작업 유형이 cmdlet을 지원 하는지 여부를 확인 하려면 `Suspend-Job` 사용자 지정 작업 유형에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-121">To determine whether a particular custom job type supports the `Suspend-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="6b9ff-122">워크플로 작업을 일시 중단하면 워크플로 작업이 다음 검사점까지 실행된 다음 일시 중단되고 워크플로 작업 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span> <span data-ttu-id="6b9ff-123">작업을 가져오기 전에 일시 중단이 완료 될 때까지 기다리려면의 **wait** 매개 변수 또는 cmdlet을 사용 합니다 `Suspend-Job` `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="6b9ff-123">To wait for the suspension to complete before getting the job, use the **Wait** parameter of `Suspend-Job` or the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="6b9ff-124">워크플로 작업이 일시 중단 되 면 작업의 **State** 속성 값이 일시 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="6b9ff-125">정확한 일시 중단은 검사점을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-125">Suspending correctly relies on checkpoints.</span></span> <span data-ttu-id="6b9ff-126">상태 또는 데이터의 손실 없이 워크플로 작업을 다시 시작할 수 있도록 현재 작업 상태, 메타 데이터 및 출력이 검사점에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span> <span data-ttu-id="6b9ff-127">워크플로 작업에 검사점이 없으면 제대로 일시 중단할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span> <span data-ttu-id="6b9ff-128">실행 중인 워크플로에 검사점을 추가하려면 **PSPersist** 워크플로 일반 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-128">To add checkpoints to a workflow that you are running, use the **PSPersist** workflow common parameter.</span></span> <span data-ttu-id="6b9ff-129">**Force** 매개 변수를 사용 하 여 워크플로 작업을 즉시 일시 중단 하 고 검사점이 없는 워크플로 작업을 일시 중단할 수 있지만 상태 및 데이터가 손실 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-129">You can use the **Force** parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="6b9ff-130">워크플로 작업 ( **PSWorkflowJob** )과 같은 사용자 지정 작업 유형에 대해 Job cmdlet을 사용 하기 전에 cmdlet을 사용 하거나 `Import-Module` 모듈에서 cmdlet을 사용 하거나 사용 하 여 사용자 지정 작업 유형을 지 원하는 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the `Import-Module` cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="6b9ff-131">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6b9ff-132">예제</span><span class="sxs-lookup"><span data-stu-id="6b9ff-132">EXAMPLES</span></span>

### <span data-ttu-id="6b9ff-133">예제 1: 이름을 기준으로 워크플로 작업 일시 중단</span><span class="sxs-lookup"><span data-stu-id="6b9ff-133">Example 1: Suspend a workflow job by name</span></span>

<span data-ttu-id="6b9ff-134">이 예제에서는 워크플로 작업을 일시 중단하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-134">This example shows how to suspend a workflow job.</span></span>

<span data-ttu-id="6b9ff-135">첫 번째 명령은 워크플로를 만듭니다 `Get-SystemLog` .</span><span class="sxs-lookup"><span data-stu-id="6b9ff-135">The first command creates the `Get-SystemLog` workflow.</span></span> <span data-ttu-id="6b9ff-136">워크플로는 활동을 사용 하 여 `CheckPoint-Workflow` 워크플로에서 검사점을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-136">The workflow uses the `CheckPoint-Workflow` activity to define a checkpoint in the workflow.</span></span>

<span data-ttu-id="6b9ff-137">두 번째 명령은 모든 워크플로에 공통적으로 사용 되는 **AsJob** 매개 변수를 사용 하 여 `Get-SystemLog` 워크플로를 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-137">The second command uses the **AsJob** parameter that is common to all workflows to run the `Get-SystemLog` workflow as a background job.</span></span> <span data-ttu-id="6b9ff-138">**JobName** 워크플로 일반 매개 변수를 사용하여 워크플로 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-138">The command uses the **JobName** workflow common parameter to specify a friendly name for the workflow job.</span></span>

<span data-ttu-id="6b9ff-139">세 번째 명령은 cmdlet을 사용 하 여 `Get-Job` `Get-SystemLogJob` 워크플로 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-139">The third command uses the `Get-Job` cmdlet to get the `Get-SystemLogJob` workflow job.</span></span> <span data-ttu-id="6b9ff-140">출력은 **PSJobTypeName** 속성의 값이 PSWorkflowJob 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-140">The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.</span></span>

<span data-ttu-id="6b9ff-141">네 번째 명령은 cmdlet을 사용 하 여 `Suspend-Job` 작업을 일시 중단 합니다 `Get-SystemLogJob` .</span><span class="sxs-lookup"><span data-stu-id="6b9ff-141">The fourth command uses the `Suspend-Job` cmdlet to suspend the `Get-SystemLogJob` job.</span></span> <span data-ttu-id="6b9ff-142">작업이 검사점까지 실행된 다음 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-142">The job runs to the checkpoint and then suspends.</span></span>

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### <span data-ttu-id="6b9ff-143">예 2: 워크플로 작업 일시 중단 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6b9ff-143">Example 2: Suspend and resume a workflow job</span></span>

<span data-ttu-id="6b9ff-144">이 예제에서는 워크플로 작업을 일시 중단하고 다시 시작하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-144">This example shows how to suspend and resume a workflow job.</span></span>

<span data-ttu-id="6b9ff-145">첫 번째 명령은 LogWorkflowJob 작업을 일시 중단 합니다. 명령이 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-145">The first command suspends the LogWorkflowJob job.The command returns immediately.</span></span> <span data-ttu-id="6b9ff-146">출력은 워크플로 작업이 일시 중단 된 경우에도 여전히 실행 되 고 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-146">The output shows that the workflow job is still running, even though it is being suspended.</span></span>

<span data-ttu-id="6b9ff-147">두 번째 명령은 cmdlet을 사용 하 여 `Get-Job` LogWorkflowJob 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-147">The second command uses the `Get-Job` cmdlet to get the LogWorkflowJob job.</span></span> <span data-ttu-id="6b9ff-148">출력은 워크플로 작업이 성공적으로 일시 중단되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-148">The output shows that the workflow job suspended successfully.</span></span>

<span data-ttu-id="6b9ff-149">세 번째 명령은 cmdlet을 사용 하 여 `Get-Job` LogWorkflowJob 작업을 가져온 다음 cmdlet을 사용 하 여 `Resume-Job` 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-149">The third command uses the `Get-Job` cmdlet to get the LogWorkflowJob job and the `Resume-Job` cmdlet to resume it.</span></span> <span data-ttu-id="6b9ff-150">출력은 워크플로 작업이 성공적으로 다시 시작되었으며 현재 실행 중임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-150">The output shows that the workflow job resumed successfully and is now running.</span></span>

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### <span data-ttu-id="6b9ff-151">예 3: 원격 컴퓨터에서 워크플로 작업 일시 중단</span><span class="sxs-lookup"><span data-stu-id="6b9ff-151">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="6b9ff-152">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` Srv01 원격 컴퓨터에서 워크플로 작업을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-152">This command uses the `Invoke-Command` cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span> <span data-ttu-id="6b9ff-153">**Filter** 매개 변수의 값은 CustomID 값을 지정 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-153">The value of the **Filter** parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="6b9ff-154">이 **CustomID** 는 작업 메타데이터( **PSPrivateMetadata** )입니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-154">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="6b9ff-155">예제 4: 워크플로 작업이 일시 중단 될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="6b9ff-155">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="6b9ff-156">이 명령은 VersionCheck 워크플로 작업을 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-156">This command suspends the VersionCheck workflow job.</span></span> <span data-ttu-id="6b9ff-157">**Wait** 매개 변수를 사용하여 워크플로 작업이 일시 중단될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-157">The command uses the **Wait** parameter to wait until the workflow job is suspended.</span></span> <span data-ttu-id="6b9ff-158">워크플로 작업이 다음 검사점까지 실행 되 고 일시 중단 되 면 명령이 완료 되 고 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-158">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="6b9ff-159">예 5: 워크플로 작업을 강제로 일시 중단</span><span class="sxs-lookup"><span data-stu-id="6b9ff-159">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="6b9ff-160">이 명령은 Maintenance 워크플로 작업을 강제로 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-160">This command suspends the Maintenance workflow job forcibly.</span></span> <span data-ttu-id="6b9ff-161">유지 관리 작업에 검사점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-161">The Maintenance job does not have checkpoints.</span></span> <span data-ttu-id="6b9ff-162">이 파일은 올바르게 일시 중단 될 수 없으며 제대로 다시 시작 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-162">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="6b9ff-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6b9ff-163">PARAMETERS</span></span>

### <span data-ttu-id="6b9ff-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="6b9ff-164">-Filter</span></span>

<span data-ttu-id="6b9ff-165">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-165">Specifies a hash table of conditions.</span></span> <span data-ttu-id="6b9ff-166">이 cmdlet은 모든 조건을 충족 하는 작업을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-166">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="6b9ff-167">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-167">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="6b9ff-168">-Force</span><span class="sxs-lookup"><span data-stu-id="6b9ff-168">-Force</span></span>

<span data-ttu-id="6b9ff-169">워크플로 작업을 즉시 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-169">Suspends the workflow job immediately.</span></span> <span data-ttu-id="6b9ff-170">이 작업으로 인해 상태 및 데이터가 손실 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-170">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="6b9ff-171">기본적으로에서는 `Suspend-Job` 워크플로 작업이 다음 검사점까지 실행 된 다음 일시 중단 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-171">By default, `Suspend-Job` lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="6b9ff-172">이 매개 변수를 사용하여 검사점이 없는 워크플로 작업을 일시 중단할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-172">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6b9ff-173">-Id</span><span class="sxs-lookup"><span data-stu-id="6b9ff-173">-Id</span></span>

<span data-ttu-id="6b9ff-174">이 cmdlet이 일시 중단 하는 작업의 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-174">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="6b9ff-175">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-175">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="6b9ff-176">인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-176">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="6b9ff-177">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-177">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="6b9ff-178">작업 ID를 찾으려면 cmdlet을 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="6b9ff-178">To find the ID of a job, use the `Get-Job` cmdlet.</span></span>

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

### <span data-ttu-id="6b9ff-179">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6b9ff-179">-InstanceId</span></span>

<span data-ttu-id="6b9ff-180">이 cmdlet이 일시 중단 하는 작업의 인스턴스 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-180">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="6b9ff-181">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-181">The default is all jobs.</span></span>

<span data-ttu-id="6b9ff-182">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-182">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="6b9ff-183">작업의 인스턴스 ID를 찾으려면를 사용 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-183">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="6b9ff-184">-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-184">-Job</span></span>

<span data-ttu-id="6b9ff-185">이 cmdlet이 중지 하는 워크플로 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-185">Specifies the workflow jobs that this cmdlet stops.</span></span> <span data-ttu-id="6b9ff-186">워크플로 작업이 포함된 변수 또는 워크플로 작업을 가져오는 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-186">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span> <span data-ttu-id="6b9ff-187">워크플로 작업을 cmdlet으로 파이프 할 수도 있습니다 `Suspend-Job` .</span><span class="sxs-lookup"><span data-stu-id="6b9ff-187">You can also pipe workflow jobs to the `Suspend-Job` cmdlet.</span></span>

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

### <span data-ttu-id="6b9ff-188">-Name</span><span class="sxs-lookup"><span data-stu-id="6b9ff-188">-Name</span></span>

<span data-ttu-id="6b9ff-189">이 cmdlet이 일시 중단 하는 작업의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-189">Specifies friendly names of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="6b9ff-190">워크플로 작업 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-190">Enter one or more workflow job names.</span></span>
<span data-ttu-id="6b9ff-191">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-191">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="6b9ff-192">-상태</span><span class="sxs-lookup"><span data-stu-id="6b9ff-192">-State</span></span>

<span data-ttu-id="6b9ff-193">작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-193">Specifies a job state.</span></span> <span data-ttu-id="6b9ff-194">이 cmdlet은 지정 된 상태의 작업만 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-194">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="6b9ff-195">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6b9ff-196">NotStarted</span><span class="sxs-lookup"><span data-stu-id="6b9ff-196">NotStarted</span></span>
- <span data-ttu-id="6b9ff-197">실행 중</span><span class="sxs-lookup"><span data-stu-id="6b9ff-197">Running</span></span>
- <span data-ttu-id="6b9ff-198">완료됨</span><span class="sxs-lookup"><span data-stu-id="6b9ff-198">Completed</span></span>
- <span data-ttu-id="6b9ff-199">실패</span><span class="sxs-lookup"><span data-stu-id="6b9ff-199">Failed</span></span>
- <span data-ttu-id="6b9ff-200">중지됨</span><span class="sxs-lookup"><span data-stu-id="6b9ff-200">Stopped</span></span>
- <span data-ttu-id="6b9ff-201">차단</span><span class="sxs-lookup"><span data-stu-id="6b9ff-201">Blocked</span></span>
- <span data-ttu-id="6b9ff-202">일시 중단</span><span class="sxs-lookup"><span data-stu-id="6b9ff-202">Suspended</span></span>
- <span data-ttu-id="6b9ff-203">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="6b9ff-203">Disconnected</span></span>
- <span data-ttu-id="6b9ff-204">Suspending</span><span class="sxs-lookup"><span data-stu-id="6b9ff-204">Suspending</span></span>
- <span data-ttu-id="6b9ff-205">중지 중</span><span class="sxs-lookup"><span data-stu-id="6b9ff-205">Stopping</span></span>

<span data-ttu-id="6b9ff-206">`Suspend-Job`**실행** 상태의 워크플로 작업만 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-206">`Suspend-Job` suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="6b9ff-207">작업 상태에 대 한 자세한 내용은 [JobState 열거](/dotnet/api/system.management.automation.jobstate)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-207">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="6b9ff-208">-Wait</span><span class="sxs-lookup"><span data-stu-id="6b9ff-208">-Wait</span></span>

<span data-ttu-id="6b9ff-209">이 cmdlet은 워크플로 작업이 일시 중단 상태가 될 때까지 명령 프롬프트를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-209">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span> <span data-ttu-id="6b9ff-210">`Suspend-Job`워크플로 작업이 아직 일시 중단 된 상태가 아닌 경우에도 기본적으로는 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-210">By default, `Suspend-Job` returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="6b9ff-211">**Wait** 매개 변수는 `Suspend-Job` 명령을 cmdlet에 파이프 하는 것과 같습니다 `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="6b9ff-211">The **Wait** parameter is equivalent to piping a `Suspend-Job` command to the `Wait-Job` cmdlet.</span></span>

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

### <span data-ttu-id="6b9ff-212">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6b9ff-212">-Confirm</span></span>

<span data-ttu-id="6b9ff-213">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-213">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6b9ff-214">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6b9ff-214">-WhatIf</span></span>

<span data-ttu-id="6b9ff-215">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-215">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6b9ff-216">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-216">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6b9ff-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b9ff-217">CommonParameters</span></span>

<span data-ttu-id="6b9ff-218">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6b9ff-219">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6b9ff-220">입력</span><span class="sxs-lookup"><span data-stu-id="6b9ff-220">INPUTS</span></span>

### <span data-ttu-id="6b9ff-221">System.object.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-221">System.Management.Automation.Job</span></span>

<span data-ttu-id="6b9ff-222">모든 유형의 작업을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-222">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="6b9ff-223">그러나에서 `Suspend-Job` 지원 되지 않는 형식의 작업을 가져오는 경우 종료 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-223">However, if `Suspend-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="6b9ff-224">출력</span><span class="sxs-lookup"><span data-stu-id="6b9ff-224">OUTPUTS</span></span>

### <span data-ttu-id="6b9ff-225">System.object.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-225">System.Management.Automation.Job</span></span>
<span data-ttu-id="6b9ff-226">이 cmdlet은 일시 중단 된 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-226">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="6b9ff-227">참고</span><span class="sxs-lookup"><span data-stu-id="6b9ff-227">NOTES</span></span>

- <span data-ttu-id="6b9ff-228">일시 중단된 작업을 저장하는 메커니즘과 위치는 작업 유형에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-228">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="6b9ff-229">예를 들어 일시 중단된 워크플로 작업은 기본적으로 플랫 파일 저장소에 저장되지만 데이터베이스에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-229">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
- <span data-ttu-id="6b9ff-230">실행 중 상태가 아닌 워크플로 작업을 제출 하는 경우에서 `Suspend-Job` 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-230">If you submit a workflow job that is not in the Running state, `Suspend-Job` displays a warning message.</span></span> <span data-ttu-id="6b9ff-231">이 경고를 표시 하지 않으려면 SilentlyContinue의 값과 함께 **WarningAction** 일반 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-231">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="6b9ff-232">작업이 일시 중단을 지 원하는 형식이 아닌 경우는 `Suspend-Job` 종료 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-232">If a job is not of a type that supports suspending, `Suspend-Job` returns a terminating error.</span></span>

- <span data-ttu-id="6b9ff-233">이 cmdlet에 의해 일시 중단 된 워크플로를 포함 하 여 일시 중단 된 워크플로 작업을 찾으려면 cmdlet의 **State** 매개 변수를 사용 `Get-Job` 하 여 일시 중단 된 상태의 워크플로 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-233">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get workflow jobs in the Suspended state.</span></span>
- <span data-ttu-id="6b9ff-234">일부 작업 유형에는 Windows PowerShell에서 작업을 일시 중단할 수 없게 하는 옵션 또는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-234">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="6b9ff-235">작업을 일시 중단 하려는 시도가 실패 한 경우 작업 옵션 및 속성이 일시 중단을 허용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b9ff-235">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="6b9ff-236">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6b9ff-236">RELATED LINKS</span></span>

[<span data-ttu-id="6b9ff-237">Get-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-237">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="6b9ff-238">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-238">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="6b9ff-239">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-239">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="6b9ff-240">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-240">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="6b9ff-241">Start-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-241">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="6b9ff-242">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-242">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="6b9ff-243">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-243">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="6b9ff-244">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="6b9ff-244">Wait-Job</span></span>](Wait-Job.md)
