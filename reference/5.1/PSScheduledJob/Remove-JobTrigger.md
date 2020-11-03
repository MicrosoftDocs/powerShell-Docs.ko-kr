---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213410"
---
# <span data-ttu-id="779cd-103">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-103">Remove-JobTrigger</span></span>

## <span data-ttu-id="779cd-104">개요</span><span class="sxs-lookup"><span data-stu-id="779cd-104">SYNOPSIS</span></span>
<span data-ttu-id="779cd-105">예약 된 작업에서 작업 트리거를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-105">Delete job triggers from scheduled jobs.</span></span>

## <span data-ttu-id="779cd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="779cd-106">SYNTAX</span></span>

### <span data-ttu-id="779cd-107">JobDefinition (기본값)</span><span class="sxs-lookup"><span data-stu-id="779cd-107">JobDefinition (Default)</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### <span data-ttu-id="779cd-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="779cd-108">JobDefinitionId</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="779cd-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="779cd-109">JobDefinitionName</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="779cd-110">설명</span><span class="sxs-lookup"><span data-stu-id="779cd-110">DESCRIPTION</span></span>
<span data-ttu-id="779cd-111">**Remove JobTrigger** cmdlet은 예약 된 작업에서 작업 트리거를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-111">The **Remove-JobTrigger** cmdlet deletes job triggers from scheduled jobs.</span></span>

<span data-ttu-id="779cd-112">작업 트리거는 예약 된 작업을 시작 하기 위한 되풀이 일정 또는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-112">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="779cd-113">작업 트리거를 관리 하려면 New-JobTrigger, Add JobTrigger, Set JobTrigger 및 Set-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-113">To manage job triggers, use the New-JobTrigger, Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJob cmdlets.</span></span>

<span data-ttu-id="779cd-114">*Remove-JobTrigger* 의 *Name* , *ID* 또는 **InputObject** 매개 변수를 사용하여 트리거를 제거할 예약된 작업을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-114">Use the *Name* , *ID* , or *InputObject* parameters of **Remove-JobTrigger** to identify the scheduled jobs from which the triggers are removed.</span></span>
<span data-ttu-id="779cd-115">*TriggerID* 매개 변수를 사용 하 여 삭제할 작업 트리거를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-115">Use the *TriggerID* parameter to identify the job triggers to delete.</span></span>
<span data-ttu-id="779cd-116">기본적으로 **Remove-JobTrigger** 는 예약된 작업의 모든 작업 트리거를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-116">By default, **Remove-JobTrigger** deletes all job triggers of a scheduled job.</span></span>

<span data-ttu-id="779cd-117">**Remove JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-117">**Remove-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="779cd-118">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="779cd-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="779cd-119">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="779cd-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="779cd-120">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="779cd-121">예제</span><span class="sxs-lookup"><span data-stu-id="779cd-121">EXAMPLES</span></span>

### <span data-ttu-id="779cd-122">예제 1: 모든 작업 트리거 삭제</span><span class="sxs-lookup"><span data-stu-id="779cd-122">Example 1: Delete all job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

<span data-ttu-id="779cd-123">이 명령은 예약 된 작업에서 이름이 Test로 시작 하는 모든 작업 트리거를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-123">This command deletes all job triggers from scheduled job that have names that begin with Test.</span></span>

### <span data-ttu-id="779cd-124">예 2: 선택한 작업 트리거 삭제</span><span class="sxs-lookup"><span data-stu-id="779cd-124">Example 2: Delete selected job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

<span data-ttu-id="779cd-125">이 명령은 BackupArchive 예약된 작업에서 세 번째 트리거(ID = 3)만 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-125">This command deletes only the third trigger (ID = 3) from the BackupArchive scheduled job.</span></span>

### <span data-ttu-id="779cd-126">예 3: 모든 예약 된 작업에서 AtStartup 작업 트리거 삭제</span><span class="sxs-lookup"><span data-stu-id="779cd-126">Example 3: Delete AtStartup job triggers from all scheduled jobs</span></span>

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

<span data-ttu-id="779cd-127">이 함수는 로컬 컴퓨터의 모든 작업에서 모든 AtStartup 작업 트리거를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-127">This function deletes all AtStartup job triggers from all jobs on the local computer.</span></span>
<span data-ttu-id="779cd-128">함수를 사용 하려면 세션에서 함수를 실행 한 다음를 입력 `Delete-AtStartup` 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-128">To use the function, run the function in your session and then type `Delete-AtStartup`.</span></span>

<span data-ttu-id="779cd-129">Delete-AtStartup 함수에는 하나의 명령이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-129">The Delete-AtStartup function contains a single command.</span></span>
<span data-ttu-id="779cd-130">이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-130">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="779cd-131">파이프라인 연산자 (|)가 예약 된 작업을 Get-JobTrigger cmdlet으로 보내면이 cmdlet이 각 예약 된 작업의 모든 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-131">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all of the job triggers from each of the scheduled jobs.</span></span>
<span data-ttu-id="779cd-132">파이프라인 연산자가 작업 트리거를 Where-Object cmdlet으로 보냅니다 .이 cmdlet은 작업 트리거의 Frequency 속성 값이 AtStartup과 같은 작업 트리거를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-132">A pipeline operator sends the job triggers to the Where-Object cmdlet, which selects job triggers where the value of the Frequency property of the job trigger equals AtStartup.</span></span>

<span data-ttu-id="779cd-133">**Jobtrigger** 개체에는 트리거하는 예약 된 작업을 포함 하는 **JobDefinition** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-133">**JobTrigger** objects have a **JobDefinition** property that contains the scheduled job that they trigger.</span></span>
<span data-ttu-id="779cd-134">명령의 나머지 부분에서는 이 유용한 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-134">The remainder of the command uses that valuable feature.</span></span>

<span data-ttu-id="779cd-135">파이프라인 연산자는 AtStartup 작업 트리거를 ForEach-Object cmdlet으로 보냅니다 .이 cmdlet은 각 AtStartup 트리거에서 **Remove jobtrigger** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-135">A pipeline operator sends the AtStartup job triggers to the ForEach-Object cmdlet, which runs a **Remove-JobTrigger** command on each AtStartup trigger.</span></span>
<span data-ttu-id="779cd-136">**JobTrigger** 의 *InputObject* 매개 변수 값은 작업 트리거의 JobDefinition 속성에 있는 예약 된 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-136">The value of the *InputObject* parameter of **Remove-JobTrigger** is the scheduled job in the JobDefinition property of the job trigger.</span></span>
<span data-ttu-id="779cd-137">*TriggerID* 매개 변수의 값은 작업 트리거의 ID 속성에 있는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-137">The value of the *TriggerID* parameter is the identifier in the ID property of the job trigger.</span></span>

### <span data-ttu-id="779cd-138">예 4: 원격 예약 된 작업에서 작업 트리거 삭제</span><span class="sxs-lookup"><span data-stu-id="779cd-138">Example 4: Delete a job trigger from a remote scheduled job</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

<span data-ttu-id="779cd-139">이 명령은 Server01 컴퓨터의 Inventory 작업에서 첫 번째 작업 트리거를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-139">This command deletes the first job trigger from the Inventory job on the Server01 computer.</span></span>

<span data-ttu-id="779cd-140">이 명령은 **Invoke 명령** cmdlet을 사용 하 여 Server01 컴퓨터에서 **Remove jobtrigger** cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-140">The command uses the **Invoke-Command** cmdlet to run the **Remove-JobTrigger** cmdlet on the Server01 computer.</span></span>
<span data-ttu-id="779cd-141">**Remove JobTrigger** Cmdlet은 *ID* 매개 변수를 사용 하 여 Inventory 예약 된 작업을 식별 하 고 *TriggerID* 매개 변수를 사용 하 여 첫 번째 트리거를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-141">The **Remove-JobTrigger** cmdlet uses the *ID* parameter to identify the Inventory scheduled job and the *TriggerID* parameter to specify the first trigger.</span></span>
<span data-ttu-id="779cd-142">*ID* 매개 변수는 특히 여러 개의 예약 된 작업에서 이름이 같거나 비슷한 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-142">The *ID* parameter is especially useful when multiple scheduled jobs have the same or similar names.</span></span>

## <span data-ttu-id="779cd-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="779cd-143">PARAMETERS</span></span>

### <span data-ttu-id="779cd-144">-Id</span><span class="sxs-lookup"><span data-stu-id="779cd-144">-Id</span></span>
<span data-ttu-id="779cd-145">예약된 작업의 ID 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-145">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="779cd-146">**Remove-JobTrigger** 는 지정한 예약된 작업에서 작업 트리거를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-146">**Remove-JobTrigger** deletes job triggers from the specified scheduled jobs.</span></span>

<span data-ttu-id="779cd-147">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 id 번호를 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-147">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="779cd-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="779cd-148">-InputObject</span></span>
<span data-ttu-id="779cd-149">예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-149">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="779cd-150">**Set-scheduledjob** 개체가 포함 된 변수를 입력 하거나 **set-scheduledjob** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-150">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="779cd-151">**Set-scheduledjob** 개체를 **제거-jobtrigger** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-151">You can also pipe **ScheduledJob** objects to **Remove-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="779cd-152">-Name</span><span class="sxs-lookup"><span data-stu-id="779cd-152">-Name</span></span>
<span data-ttu-id="779cd-153">예약된 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-153">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="779cd-154">**Remove-JobTrigger** 는 지정한 예약된 작업에서 작업 트리거를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-154">**Remove-JobTrigger** deletes the job triggers from the specified scheduled jobs.</span></span>
<span data-ttu-id="779cd-155">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-155">Wildcards are supported.</span></span>

<span data-ttu-id="779cd-156">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 이름을 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-156">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="779cd-157">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="779cd-157">-TriggerId</span></span>
<span data-ttu-id="779cd-158">지정한 작업 트리거만 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-158">Deletes only the specified job triggers.</span></span>
<span data-ttu-id="779cd-159">기본적으로 **Remove-JobTrigger** 는 예약된 작업에서 모든 트리거를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-159">By default, **Remove-JobTrigger** deletes all triggers from the scheduled jobs.</span></span>
<span data-ttu-id="779cd-160">예약된 작업에 여러 개의 작업 트리거가 있는 경우 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-160">Use this parameter when the scheduled jobs have multiple job triggers.</span></span>

<span data-ttu-id="779cd-161">예약된 작업의 하나 이상 작업 트리거에 대한 트리거 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="779cd-162">여러 개의 예약 된 작업을 지정 하는 경우 **JobTrigger** 는 모든 예약 된 작업에서 지정 된 ID의 작업 트리거를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-162">If you specify multiple scheduled jobs, **Remove-JobTrigger** deletes the job trigger with the specified ID from all scheduled jobs.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="779cd-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="779cd-163">CommonParameters</span></span>
<span data-ttu-id="779cd-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="779cd-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="779cd-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="779cd-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="779cd-166">입력</span><span class="sxs-lookup"><span data-stu-id="779cd-166">INPUTS</span></span>

### <span data-ttu-id="779cd-167">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="779cd-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="779cd-168">예약된 작업을 **Remove-JobTrigger** cmdlet으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-168">You can pipe scheduled jobs to the **Remove-JobTrigger** cmdlet.</span></span>

## <span data-ttu-id="779cd-169">출력</span><span class="sxs-lookup"><span data-stu-id="779cd-169">OUTPUTS</span></span>

### <span data-ttu-id="779cd-170">없음</span><span class="sxs-lookup"><span data-stu-id="779cd-170">None</span></span>
<span data-ttu-id="779cd-171">이 cmdlet에서 어떠한 출력도 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="779cd-171">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="779cd-172">참고</span><span class="sxs-lookup"><span data-stu-id="779cd-172">NOTES</span></span>

## <span data-ttu-id="779cd-173">관련 링크</span><span class="sxs-lookup"><span data-stu-id="779cd-173">RELATED LINKS</span></span>

[<span data-ttu-id="779cd-174">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-174">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="779cd-175">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-175">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="779cd-176">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="779cd-176">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="779cd-177">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-177">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="779cd-178">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="779cd-178">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="779cd-179">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-179">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="779cd-180">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="779cd-180">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="779cd-181">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="779cd-181">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="779cd-182">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-182">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="779cd-183">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="779cd-183">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="779cd-184">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="779cd-184">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="779cd-185">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-185">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="779cd-186">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="779cd-186">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="779cd-187">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="779cd-187">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="779cd-188">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="779cd-188">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="779cd-189">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="779cd-189">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
