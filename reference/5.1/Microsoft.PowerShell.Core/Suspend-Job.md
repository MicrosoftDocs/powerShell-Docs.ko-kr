---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212722"
---
# <span data-ttu-id="d5467-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-103">Suspend-Job</span></span>

## <span data-ttu-id="d5467-104">개요</span><span class="sxs-lookup"><span data-stu-id="d5467-104">SYNOPSIS</span></span>
<span data-ttu-id="d5467-105">워크플로 작업을 일시적으로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="d5467-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d5467-106">SYNTAX</span></span>

### <span data-ttu-id="d5467-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="d5467-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5467-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="d5467-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5467-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="d5467-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5467-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d5467-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5467-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="d5467-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5467-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="d5467-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d5467-113">설명</span><span class="sxs-lookup"><span data-stu-id="d5467-113">DESCRIPTION</span></span>
<span data-ttu-id="d5467-114">**작업 일시 중단** cmdlet은 워크플로 작업을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-114">The **Suspend-Job** cmdlet suspends workflow jobs.</span></span>
<span data-ttu-id="d5467-115">일시 중단은 워크플로 작업을 일시적으로 중단 하거나 일시 중지 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span>
<span data-ttu-id="d5467-116">이 cmdlet을 사용하면 워크플로를 실행하는 사용자가 워크플로를 일시 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span>
<span data-ttu-id="d5467-117">워크플로를 https://go.microsoft.com/fwlink/?LinkId=267141 일시 중단 하는 워크플로의 명령 인 일시 중단 워크플로 작업을 보완 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="d5467-118">**Suspend-Job** cmdlet은 워크플로 작업에서만 작동하고</span><span class="sxs-lookup"><span data-stu-id="d5467-118">The **Suspend-Job** cmdlet works only on workflow jobs.</span></span>
<span data-ttu-id="d5467-119">Start-Job cmdlet을 사용 하 여 시작한 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-119">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="d5467-120">워크플로 작업을 식별 하려면 작업의 **PSJobTypeName** 속성에서 PSWorkflowJob 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="d5467-121">특정 사용자 지정 작업 유형이 **Suspend-Job** cmdlet을 지원하는지 확인하려면 사용자 지정 작업 유형에 대한 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5467-121">To determine whether a particular custom job type supports the **Suspend-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="d5467-122">워크플로 작업을 일시 중단하면 워크플로 작업이 다음 검사점까지 실행된 다음 일시 중단되고 워크플로 작업 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span>
<span data-ttu-id="d5467-123">작업을 가져오기 전에 일시 중단이 완료 될 때까지 기다리려면 **일시 중단-작업** 또는 Wait-Job Cmdlet의 *wait* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-123">To wait for the suspension to complete before getting the job, use the *Wait* parameter of **Suspend-Job** or the Wait-Job cmdlet.</span></span>
<span data-ttu-id="d5467-124">워크플로 작업이 일시 중단 되 면 작업의 **State** 속성 값이 일시 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="d5467-125">정확한 일시 중단은 검사점을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-125">Suspending correctly relies on checkpoints.</span></span>
<span data-ttu-id="d5467-126">상태 또는 데이터의 손실 없이 워크플로 작업을 다시 시작할 수 있도록 현재 작업 상태, 메타 데이터 및 출력이 검사점에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span>
<span data-ttu-id="d5467-127">워크플로 작업에 검사점이 없으면 제대로 일시 중단할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span>
<span data-ttu-id="d5467-128">실행 중인 워크플로에 검사점을 추가하려면 *PSPersist* 워크플로 일반 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-128">To add checkpoints to a workflow that you are running, use the *PSPersist* workflow common parameter.</span></span>
<span data-ttu-id="d5467-129">*Force* 매개 변수를 사용 하 여 워크플로 작업을 즉시 일시 중단 하 고 검사점이 없는 워크플로 작업을 일시 중단할 수 있지만 상태 및 데이터가 손실 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-129">You can use the *Force* parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="d5467-130">워크플로 작업 ( **PSWorkflowJob** )과 같은 사용자 지정 작업 유형에 대해 Job cmdlet을 사용 하기 전에 Import-Module cmdlet을 사용 하거나 모듈에서 cmdlet을 사용 하거나 사용 하 여 사용자 지정 작업 유형을 지 원하는 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the Import-Module cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="d5467-131">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="d5467-132">예제</span><span class="sxs-lookup"><span data-stu-id="d5467-132">EXAMPLES</span></span>

### <span data-ttu-id="d5467-133">예제 1: 이름을 기준으로 워크플로 작업 일시 중단</span><span class="sxs-lookup"><span data-stu-id="d5467-133">Example 1: Suspend a workflow job by name</span></span>

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

<span data-ttu-id="d5467-134">이 예제에서는 워크플로 작업을 일시 중단하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-134">This example shows how to suspend a workflow job.</span></span>

### <span data-ttu-id="d5467-135">예 2: 워크플로 작업 일시 중단 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="d5467-135">Example 2: Suspend and resume a workflow job</span></span>

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

<span data-ttu-id="d5467-136">이 예제에서는 워크플로 작업을 일시 중단하고 다시 시작하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-136">This example shows how to suspend and resume a workflow job.</span></span>

### <span data-ttu-id="d5467-137">예 3: 원격 컴퓨터에서 워크플로 작업 일시 중단</span><span class="sxs-lookup"><span data-stu-id="d5467-137">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="d5467-138">이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 원격 컴퓨터에서 워크플로 작업을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-138">This command uses the Invoke-Command cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span>
<span data-ttu-id="d5467-139">*Filter* 매개 변수의 값은 CustomID 값을 지정 하는 해시 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-139">The value of the *Filter* parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="d5467-140">이 **CustomID** 는 작업 메타데이터( **PSPrivateMetadata** )입니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-140">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="d5467-141">예제 4: 워크플로 작업이 일시 중단 될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="d5467-141">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="d5467-142">이 명령은 VersionCheck 워크플로 작업을 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-142">This command suspends the VersionCheck workflow job.</span></span>
<span data-ttu-id="d5467-143">*Wait* 매개 변수를 사용하여 워크플로 작업이 일시 중단될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-143">The command uses the *Wait* parameter to wait until the workflow job is suspended.</span></span>
<span data-ttu-id="d5467-144">워크플로 작업이 다음 검사점까지 실행 되 고 일시 중단 되 면 명령이 완료 되 고 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-144">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="d5467-145">예 5: 워크플로 작업을 강제로 일시 중단</span><span class="sxs-lookup"><span data-stu-id="d5467-145">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="d5467-146">이 명령은 Maintenance 워크플로 작업을 강제로 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-146">This command suspends the Maintenance workflow job forcibly.</span></span>
<span data-ttu-id="d5467-147">유지 관리 작업에 검사점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-147">The Maintenance job does not have checkpoints.</span></span>
<span data-ttu-id="d5467-148">이 파일은 올바르게 일시 중단 될 수 없으며 제대로 다시 시작 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-148">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="d5467-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d5467-149">PARAMETERS</span></span>

### <span data-ttu-id="d5467-150">-Filter</span><span class="sxs-lookup"><span data-stu-id="d5467-150">-Filter</span></span>
<span data-ttu-id="d5467-151">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-151">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="d5467-152">이 cmdlet은 모든 조건을 충족 하는 작업을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-152">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="d5467-153">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-153">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="d5467-154">-Force</span><span class="sxs-lookup"><span data-stu-id="d5467-154">-Force</span></span>
<span data-ttu-id="d5467-155">워크플로 작업을 즉시 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-155">Suspends the workflow job immediately.</span></span>
<span data-ttu-id="d5467-156">이 작업으로 인해 상태 및 데이터가 손실 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-156">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="d5467-157">기본적으로 **Suspend-Job** 은 워크플로 작업이 다음 검사점까지 실행되도록 한 다음 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-157">By default, **Suspend-Job** lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="d5467-158">이 매개 변수를 사용하여 검사점이 없는 워크플로 작업을 일시 중단할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-158">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

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

### <span data-ttu-id="d5467-159">-Id</span><span class="sxs-lookup"><span data-stu-id="d5467-159">-Id</span></span>
<span data-ttu-id="d5467-160">이 cmdlet이 일시 중단 하는 작업의 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-160">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="d5467-161">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-161">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="d5467-162">인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-162">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="d5467-163">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-163">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="d5467-164">작업 ID를 찾으려면 Get-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-164">To find the ID of a job, use the Get-Job cmdlet.</span></span>

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

### <span data-ttu-id="d5467-165">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="d5467-165">-InstanceId</span></span>
<span data-ttu-id="d5467-166">이 cmdlet이 일시 중단 하는 작업의 인스턴스 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-166">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="d5467-167">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-167">The default is all jobs.</span></span>

<span data-ttu-id="d5467-168">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-168">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="d5467-169">작업의 인스턴스 ID를 찾으려면 **Get-Job** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-169">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="d5467-170">-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-170">-Job</span></span>
<span data-ttu-id="d5467-171">이 cmdlet이 중지 하는 워크플로 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-171">Specifies the workflow jobs that this cmdlet stops.</span></span>
<span data-ttu-id="d5467-172">워크플로 작업이 포함된 변수 또는 워크플로 작업을 가져오는 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-172">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span>
<span data-ttu-id="d5467-173">워크플로 작업을 **Suspend-Job** cmdlet으로 파이프할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-173">You can also pipe workflow jobs to the **Suspend-Job** cmdlet.</span></span>

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

### <span data-ttu-id="d5467-174">-Name</span><span class="sxs-lookup"><span data-stu-id="d5467-174">-Name</span></span>
<span data-ttu-id="d5467-175">이 cmdlet이 일시 중단 하는 작업의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-175">Specifies friendly names of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="d5467-176">워크플로 작업 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-176">Enter one or more workflow job names.</span></span>
<span data-ttu-id="d5467-177">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-177">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="d5467-178">-상태</span><span class="sxs-lookup"><span data-stu-id="d5467-178">-State</span></span>
<span data-ttu-id="d5467-179">작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-179">Specifies a job state.</span></span>
<span data-ttu-id="d5467-180">이 cmdlet은 지정 된 상태의 작업만 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-180">This cmdlet stops only jobs in the specified state.</span></span>
<span data-ttu-id="d5467-181">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d5467-182">NotStarted</span><span class="sxs-lookup"><span data-stu-id="d5467-182">NotStarted</span></span>
- <span data-ttu-id="d5467-183">실행 중</span><span class="sxs-lookup"><span data-stu-id="d5467-183">Running</span></span>
- <span data-ttu-id="d5467-184">완료됨</span><span class="sxs-lookup"><span data-stu-id="d5467-184">Completed</span></span>
- <span data-ttu-id="d5467-185">실패</span><span class="sxs-lookup"><span data-stu-id="d5467-185">Failed</span></span>
- <span data-ttu-id="d5467-186">중지됨</span><span class="sxs-lookup"><span data-stu-id="d5467-186">Stopped</span></span>
- <span data-ttu-id="d5467-187">차단</span><span class="sxs-lookup"><span data-stu-id="d5467-187">Blocked</span></span>
- <span data-ttu-id="d5467-188">일시 중단</span><span class="sxs-lookup"><span data-stu-id="d5467-188">Suspended</span></span>
- <span data-ttu-id="d5467-189">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="d5467-189">Disconnected</span></span>
- <span data-ttu-id="d5467-190">Suspending</span><span class="sxs-lookup"><span data-stu-id="d5467-190">Suspending</span></span>
- <span data-ttu-id="d5467-191">중지 중</span><span class="sxs-lookup"><span data-stu-id="d5467-191">Stopping</span></span>

<span data-ttu-id="d5467-192">**일시 중단-작업** 은 **실행 중** 상태의 워크플로 작업만 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-192">**Suspend-Job** suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="d5467-193">작업 상태에 대 한 자세한 내용은 MSDN library에서 [JobState 열거](https://msdn.microsoft.com/library/system.management.automation.jobstate) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5467-193">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="d5467-194">-Wait</span><span class="sxs-lookup"><span data-stu-id="d5467-194">-Wait</span></span>
<span data-ttu-id="d5467-195">이 cmdlet은 워크플로 작업이 일시 중단 상태가 될 때까지 명령 프롬프트를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-195">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span>
<span data-ttu-id="d5467-196">기본적으로 **일시 중단 작업** 은 워크플로 작업이 아직 일시 중단 된 상태가 아닌 경우에도 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-196">By default, **Suspend-Job** returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="d5467-197">*Wait* 매개 변수는 **작업 일시 중단** 명령을 **대기 작업** cmdlet으로 파이프 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-197">The *Wait* parameter is equivalent to piping a **Suspend-Job** command to the **Wait-Job** cmdlet.</span></span>

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

### <span data-ttu-id="d5467-198">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d5467-198">-Confirm</span></span>
<span data-ttu-id="d5467-199">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-199">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d5467-200">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d5467-200">-WhatIf</span></span>
<span data-ttu-id="d5467-201">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-201">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d5467-202">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-202">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d5467-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5467-203">CommonParameters</span></span>
<span data-ttu-id="d5467-204">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d5467-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5467-205">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5467-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5467-206">입력</span><span class="sxs-lookup"><span data-stu-id="d5467-206">INPUTS</span></span>

### <span data-ttu-id="d5467-207">System.object.</span><span class="sxs-lookup"><span data-stu-id="d5467-207">System.Management.Automation.Job</span></span>
<span data-ttu-id="d5467-208">모든 유형의 작업을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-208">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="d5467-209">그러나 **일시 중단 작업** 은 지원 되지 않는 유형의 작업을 가져오는 경우 종료 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-209">However, if **Suspend-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="d5467-210">출력</span><span class="sxs-lookup"><span data-stu-id="d5467-210">OUTPUTS</span></span>

### <span data-ttu-id="d5467-211">System.object.</span><span class="sxs-lookup"><span data-stu-id="d5467-211">System.Management.Automation.Job</span></span>
<span data-ttu-id="d5467-212">이 cmdlet은 일시 중단 된 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-212">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="d5467-213">참고</span><span class="sxs-lookup"><span data-stu-id="d5467-213">NOTES</span></span>

* <span data-ttu-id="d5467-214">일시 중단된 작업을 저장하는 메커니즘과 위치는 작업 유형에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="d5467-215">예를 들어 일시 중단된 워크플로 작업은 기본적으로 플랫 파일 저장소에 저장되지만 데이터베이스에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
* <span data-ttu-id="d5467-216">실행 중 상태가 아닌 워크플로 작업을 제출 하는 경우 **일시 중단 작업** 은 경고 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-216">If you submit a workflow job that is not in the Running state, **Suspend-Job** displays a warning message.</span></span> <span data-ttu-id="d5467-217">이 경고를 표시 하지 않으려면 SilentlyContinue의 값과 함께 *WarningAction* 일반 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-217">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="d5467-218">작업이 일시 중단을 지 원하는 형식이 아닌 경우 **일시 중단 작업** 은 종료 오류를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-218">If a job is not of a type that supports suspending, **Suspend-Job** returns a terminating error.</span></span>

* <span data-ttu-id="d5467-219">이 cmdlet에 의해 일시 중단 된 워크플로를 포함 하 여 일시 중단 된 워크플로 작업을 찾으려면 **작업** Cmdlet의 *State* 매개 변수를 사용 하 여 일시 중단 된 상태의 워크플로 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-219">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get workflow jobs in the Suspended state.</span></span>
* <span data-ttu-id="d5467-220">일부 작업 유형에는 Windows PowerShell에서 작업을 일시 중단할 수 없게 하는 옵션 또는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-220">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="d5467-221">작업을 일시 중단 하려는 시도가 실패 한 경우 작업 옵션 및 속성이 일시 중단을 허용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5467-221">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="d5467-222">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d5467-222">RELATED LINKS</span></span>

[<span data-ttu-id="d5467-223">Get-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-223">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="d5467-224">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-224">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="d5467-225">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-225">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="d5467-226">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-226">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="d5467-227">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-227">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="d5467-228">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-228">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="d5467-229">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-229">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="d5467-230">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="d5467-230">Wait-Job</span></span>](Wait-Job.md)
