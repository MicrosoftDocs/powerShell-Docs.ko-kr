---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213490"
---
# <span data-ttu-id="8a39a-103">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-103">Disable-JobTrigger</span></span>

## <span data-ttu-id="8a39a-104">개요</span><span class="sxs-lookup"><span data-stu-id="8a39a-104">SYNOPSIS</span></span>
<span data-ttu-id="8a39a-105">예약된 작업의 작업 트리거를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-105">Disables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="8a39a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a39a-106">SYNTAX</span></span>

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8a39a-107">설명</span><span class="sxs-lookup"><span data-stu-id="8a39a-107">DESCRIPTION</span></span>
<span data-ttu-id="8a39a-108">**Disable-JobTrigger** cmdlet은 예약된 작업의 작업 트리거를 일시적으로 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-108">The **Disable-JobTrigger** cmdlet temporarily disables the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="8a39a-109">사용하지 않도록 설정할 경우 모든 작업 트리거 속성이 유지되지만 작업 트리거가 예약된 작업을 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-109">Disabling preserves all job trigger properties, but it prevents the job trigger from starting the scheduled job.</span></span>

<span data-ttu-id="8a39a-110">이 cmdlet을 사용 하려면 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-110">To use this cmdlet, use the Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="8a39a-111">작업 트리거를 **Disable-JobTrigger** 로 파이프하거나 해당 *InputObject* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-111">Then pipe the job triggers to **Disable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="8a39a-112">작업 트리거를 사용 하지 않도록 설정 하기 위해 no **jobtrigger** cmdlet은 작업 트리거의 Enabled 속성을 $False 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-112">To disable a job trigger, the **Disable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $False.</span></span>
<span data-ttu-id="8a39a-113">작업 트리거를 다시 사용 하도록 설정 하려면 Enable-JobTrigger cmdlet을 사용 합니다 .이 cmdlet은 작업 트리거의 **Enabled** 속성을 $True로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-113">To re-enable the job trigger, use the Enable-JobTrigger cmdlet, which sets the **Enabled** property of the job trigger to $True.</span></span>
<span data-ttu-id="8a39a-114">작업 트리거를 사용 하지 않도록 설정 해도 Disable-ScheduledJob cmdlet에서 수행 하는 것과 같이 예약 된 작업을 사용 하지 않도록 설정 하는 것은 아니지만 모든 작업 트리거를 사용 하지 않도록 설정 하는 경우 효과는 예약 된 작업을 사용 하지 않도록</span><span class="sxs-lookup"><span data-stu-id="8a39a-114">Disabling a job trigger does not disable the scheduled job, such as is done by the Disable-ScheduledJob cmdlet, but if you disable all job triggers, the effect is the same as disabling the scheduled job.</span></span>

<span data-ttu-id="8a39a-115">예약 된 작업을 사용 하지 않도록 설정 하거나 예약 된 작업의 모든 작업 트리거를 사용 하지 않도록 설정 하는 경우에도 Start-Job cmdlet을 사용 하 여 작업을 시작 하거나 사용 되지 않는 예약 된 작업을 템플릿으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-115">If you disable a scheduled job or disable all job triggers of a scheduled job, you can still start the job by using the Start-Job cmdlet or use the disabled scheduled job as a template.</span></span>

<span data-ttu-id="8a39a-116">**Set-scheduledjob** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="8a39a-117">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a39a-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="8a39a-118">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8a39a-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="8a39a-119">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="8a39a-120">예제</span><span class="sxs-lookup"><span data-stu-id="8a39a-120">EXAMPLES</span></span>

### <span data-ttu-id="8a39a-121">예제 1: 작업 트리거 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="8a39a-121">Example 1: Disable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

<span data-ttu-id="8a39a-122">이 명령은 로컬 컴퓨터에 있는 Backup-Archives 예약된 작업의 첫 번째 트리거(ID=1)를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-122">This command disables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="8a39a-123">이 명령은 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-123">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="8a39a-124">파이프라인 연산자가 작업 트리거를 **Disable-JobTrigger** cmdlet으로 보내면 이 cmdlet이 작업 트리거를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-124">A pipeline operator sends the job trigger to the **Disable-JobTrigger** cmdlet, which disables it.</span></span>

### <span data-ttu-id="8a39a-125">예제 2: 모든 작업 트리거 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="8a39a-125">Example 2: Disable all job triggers</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="8a39a-126">이 명령은 두 예약된 작업의 모든 작업 트리거를 사용하지 않도록 설정하고 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-126">These commands disable all job triggers on two scheduled jobs and display the results.</span></span>

### <span data-ttu-id="8a39a-127">예 3: 원격 컴퓨터에서 예약 된 작업의 작업 트리거를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="8a39a-127">Example 3: Disable job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

<span data-ttu-id="8a39a-128">이 명령은 Server01 원격 컴퓨터에 있는 DeployPackage 예약된 작업의 일별 작업 트리거를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-128">This command disables the daily job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="8a39a-129">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-129">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="8a39a-130">원격 명령은 Get-JobTrigger cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-130">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="8a39a-131">파이프라인 연산자가 작업 트리거를 Where-Object cmdlet으로 보내면이 cmdlet이 일별 작업 트리거도 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-131">A pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only daily job triggers.</span></span>
<span data-ttu-id="8a39a-132">파이프라인 연산자는 일별 작업 트리거를 사용 하지 않도록 설정 하는 **jobtrigger** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-132">A pipeline operator sends the daily job triggers to the **Disable-JobTrigger** cmdlet, which disables them.</span></span>

## <span data-ttu-id="8a39a-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a39a-133">PARAMETERS</span></span>

### <span data-ttu-id="8a39a-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8a39a-134">-InputObject</span></span>
<span data-ttu-id="8a39a-135">사용하지 않도록 설정할 작업 트리거를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-135">Specifies the job trigger to be disabled.</span></span>
<span data-ttu-id="8a39a-136">**ScheduledJobTrigger** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-136">Enter a variable that contains  **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="8a39a-137">**ScheduledJobTrigger** 개체를 파이프 하 여 **-Jobtrigger를 사용 하지 않도록 설정할** 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-137">You can also pipe a **ScheduledJobTrigger** object to **Disable-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8a39a-138">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8a39a-138">-PassThru</span></span>
<span data-ttu-id="8a39a-139">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="8a39a-140">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8a39a-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8a39a-141">-Confirm</span></span>
<span data-ttu-id="8a39a-142">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8a39a-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8a39a-143">-WhatIf</span></span>
<span data-ttu-id="8a39a-144">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8a39a-145">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8a39a-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a39a-146">CommonParameters</span></span>
<span data-ttu-id="8a39a-147">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8a39a-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a39a-148">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a39a-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a39a-149">입력</span><span class="sxs-lookup"><span data-stu-id="8a39a-149">INPUTS</span></span>

### <span data-ttu-id="8a39a-150">Set-scheduledjob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-150">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="8a39a-151">작업 트리거를 **Disable-JobTrigger** 로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-151">You can pipe job triggers to **Disable-JobTrigger** .</span></span>

## <span data-ttu-id="8a39a-152">출력</span><span class="sxs-lookup"><span data-stu-id="8a39a-152">OUTPUTS</span></span>

### <span data-ttu-id="8a39a-153">없음</span><span class="sxs-lookup"><span data-stu-id="8a39a-153">None</span></span>
<span data-ttu-id="8a39a-154">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8a39a-155">참고</span><span class="sxs-lookup"><span data-stu-id="8a39a-155">NOTES</span></span>

* <span data-ttu-id="8a39a-156">이미 사용 하지 않도록 설정 된 작업 트리거를 사용 하지 않도록 설정 하는 경우 **-JobTrigger** 는 오류 또는 경고를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a39a-156">**Disable-JobTrigger** does not generate errors or warnings if you disable a job trigger that is already disabled.</span></span>

## <span data-ttu-id="8a39a-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8a39a-157">RELATED LINKS</span></span>

[<span data-ttu-id="8a39a-158">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-158">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="8a39a-159">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-159">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="8a39a-160">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8a39a-160">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="8a39a-161">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-161">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="8a39a-162">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8a39a-162">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="8a39a-163">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-163">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="8a39a-164">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8a39a-164">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="8a39a-165">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="8a39a-165">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="8a39a-166">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-166">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="8a39a-167">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="8a39a-167">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="8a39a-168">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8a39a-168">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="8a39a-169">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-169">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="8a39a-170">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8a39a-170">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="8a39a-171">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8a39a-171">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="8a39a-172">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="8a39a-172">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="8a39a-173">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8a39a-173">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
