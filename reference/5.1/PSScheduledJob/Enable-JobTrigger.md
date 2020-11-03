---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213442"
---
# <span data-ttu-id="41671-103">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-103">Enable-JobTrigger</span></span>

## <span data-ttu-id="41671-104">개요</span><span class="sxs-lookup"><span data-stu-id="41671-104">SYNOPSIS</span></span>
<span data-ttu-id="41671-105">예약된 작업의 작업 트리거를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-105">Enables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="41671-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41671-106">SYNTAX</span></span>

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="41671-107">설명</span><span class="sxs-lookup"><span data-stu-id="41671-107">DESCRIPTION</span></span>
<span data-ttu-id="41671-108">**JobTrigger** cmdlet은 Disable-JobTrigger cmdlet을 사용 하 여 사용 하지 않도록 설정한 것과 같은 예약 된 작업의 작업 트리거를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-108">The **Enable-JobTrigger** cmdlet re-enables job triggers of scheduled jobs, such as those that were disabled by using the Disable-JobTrigger cmdlet.</span></span>
<span data-ttu-id="41671-109">사용되는 작업 트리거 및 다시 사용하도록 설정된 작업 트리거는 예약된 작업을 즉시 시작할 수 있으므로 Windows 또는 Windows PowerShell을 다시 시작하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41671-109">Enabled and re-enabled job triggers can start scheduled jobs immediately; there is no need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="41671-110">이 cmdlet을 사용 하려면 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41671-110">To use this cmdlet, use the  Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="41671-111">그런 다음 작업 트리거를 **-JobTrigger** 를 사용 하도록 파이프 하거나 *InputObject* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-111">Then pipe the job triggers to **Enable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="41671-112">작업 트리거를 사용 하도록 설정 하기 위해 **-jobtrigger** cmdlet은 작업 트리거의 Enabled 속성을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-112">To enable a job trigger, the **Enable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $True.</span></span>

<span data-ttu-id="41671-113">**Set-scheduledjob** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="41671-113">**Enable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="41671-114">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41671-114">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="41671-115">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41671-115">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="41671-116">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="41671-117">예제</span><span class="sxs-lookup"><span data-stu-id="41671-117">EXAMPLES</span></span>

### <span data-ttu-id="41671-118">예제 1: 작업 트리거를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="41671-118">Example 1: Enable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

<span data-ttu-id="41671-119">이 명령은 로컬 컴퓨터에 있는 Backup-Archives 예약된 작업의 첫 번째 트리거(ID=1)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-119">This command enables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="41671-120">이 명령은 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41671-120">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="41671-121">파이프라인 연산자가 작업 트리거를 **Enable-JobTrigger** cmdlet으로 보내면 이 cmdlet이 작업 트리거를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-121">A pipeline operator sends the job trigger to the **Enable-JobTrigger** cmdlet, which enables it.</span></span>

### <span data-ttu-id="41671-122">예제 2: 모든 작업 트리거를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="41671-122">Example 2: Enable all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

<span data-ttu-id="41671-123">이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41671-123">The command uses the Get-ScheduledJob cmdlet to get  the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="41671-124">파이프라인 연산자 (|)가 예약 된 작업의 모든 작업 트리거를 가져오는 Get-JobTrigger cmdlet으로 예약 된 작업을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41671-124">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="41671-125">다른 파이프라인 연산자가 작업 트리거를 **Enable-JobTrigger** cmdlet으로 보내면 이 cmdlet이 작업 트리거를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-125">Another pipeline operator sends the job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="41671-126">예 3: 원격 컴퓨터에서 예약 된 작업의 작업 트리거를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="41671-126">Example 3: Enable the job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

<span data-ttu-id="41671-127">이 명령은 Server01 원격 컴퓨터에 있는 DeployPackage 예약된 작업의 AtLogon 작업 트리거를 다시 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-127">This command re-enables the AtLogon job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="41671-128">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-128">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="41671-129">원격 명령은 Get-JobTrigger cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41671-129">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="41671-130">파이프라인 연산자는 AtLogon 작업 트리거도 반환 하는 Where-Object cmdlet으로 작업 트리거를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41671-130">A pipeline operator sends the job triggers to the Where-Object cmdlet which returns only AtLogon job triggers.</span></span>
<span data-ttu-id="41671-131">파이프라인 연산자가 AtLogon 작업 트리거를 사용 하도록 설정 하는 **jobtrigger** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41671-131">A pipeline operator sends the AtLogon job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="41671-132">예 4: 비활성화 된 작업 트리거 표시</span><span class="sxs-lookup"><span data-stu-id="41671-132">Example 4: Display disabled job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="41671-133">이 명령은 모든 예약된 작업의 사용되지 않는 모든 작업 트리거를 테이블로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-133">This command displays all disabled job triggers of all scheduled jobs in a table.</span></span>
<span data-ttu-id="41671-134">이러한 명령을 통해 사용하도록 설정해야 하는 작업 트리거를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-134">You can use a command like this one to discover job triggers that might need to be enabled.</span></span>

<span data-ttu-id="41671-135">이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="41671-135">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="41671-136">파이프라인 연산자 (|)가 예약 된 작업의 모든 작업 트리거를 가져오는 Get-JobTrigger cmdlet으로 예약 된 작업을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41671-136">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="41671-137">다른 파이프라인 연산자가 작업 트리거를 Where-Object cmdlet으로 보냅니다 .이 cmdlet은 비활성화 된 작업 트리거만 반환 합니다. 즉, 작업 트리거의 Enabled 속성 값이 (!) true가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="41671-137">Another pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only job triggers that are disabled, that is, where the value of the Enabled property of the job trigger is not (!) true.</span></span>

<span data-ttu-id="41671-138">다른 파이프라인 연산자는 사용 하지 않도록 설정 된 작업 트리거를 Format-Table cmdlet으로 보냅니다 .이 cmdlet은 테이블에서 작업 트리거의 선택 된 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-138">Another pipeline operator sends the disabled job triggers to the Format-Table cmdlet, which displays the selected properties of the job triggers in a table.</span></span>
<span data-ttu-id="41671-139">속성에는 작업 트리거의 JobDefinition 속성에 있는 예약된 작업의 이름을 표시하는 새 JobName 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="41671-139">The properties include a new JobName property that displays the name of the scheduled job in the JobDefinition property of the job trigger.</span></span>

## <span data-ttu-id="41671-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41671-140">PARAMETERS</span></span>

### <span data-ttu-id="41671-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="41671-141">-InputObject</span></span>
<span data-ttu-id="41671-142">사용 하도록 설정할 작업 트리거를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-142">Specifies the job trigger to enable.</span></span>
<span data-ttu-id="41671-143">**ScheduledJobTrigger** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-143">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="41671-144">**ScheduledJobTrigger** 개체를 파이프 하 여 **-Jobtrigger를 사용 하도록 설정할** 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-144">You can also pipe a **ScheduledJobTrigger** object to **Enable-JobTrigger** .</span></span>

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

### <span data-ttu-id="41671-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="41671-145">-PassThru</span></span>
<span data-ttu-id="41671-146">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-146">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="41671-147">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="41671-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="41671-148">-Confirm</span></span>
<span data-ttu-id="41671-149">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="41671-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="41671-150">-WhatIf</span></span>
<span data-ttu-id="41671-151">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="41671-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="41671-152">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="41671-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41671-153">CommonParameters</span></span>
<span data-ttu-id="41671-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41671-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41671-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41671-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41671-156">입력</span><span class="sxs-lookup"><span data-stu-id="41671-156">INPUTS</span></span>

### <span data-ttu-id="41671-157">Set-scheduledjob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="41671-158">작업 트리거를 사용 하도록 설정 하 여 **JobTrigger를 설정할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-158">You can pipe job triggers to **Enable-JobTrigger** .</span></span>

## <span data-ttu-id="41671-159">출력</span><span class="sxs-lookup"><span data-stu-id="41671-159">OUTPUTS</span></span>

### <span data-ttu-id="41671-160">없음</span><span class="sxs-lookup"><span data-stu-id="41671-160">None</span></span>
<span data-ttu-id="41671-161">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="41671-162">참고</span><span class="sxs-lookup"><span data-stu-id="41671-162">NOTES</span></span>

* <span data-ttu-id="41671-163">이미 사용 하도록 설정 된 작업 트리거를 사용 하도록 설정 하는 경우 **-JobTrigger** 는 오류 또는 경고를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41671-163">**Enable-JobTrigger** does not generate errors or warnings if you enable a job trigger that is already enabled.</span></span>

## <span data-ttu-id="41671-164">관련 링크</span><span class="sxs-lookup"><span data-stu-id="41671-164">RELATED LINKS</span></span>

[<span data-ttu-id="41671-165">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-165">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="41671-166">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-166">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="41671-167">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="41671-167">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="41671-168">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-168">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="41671-169">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="41671-169">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="41671-170">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-170">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="41671-171">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="41671-171">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="41671-172">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="41671-172">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="41671-173">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-173">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="41671-174">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="41671-174">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="41671-175">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="41671-175">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="41671-176">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-176">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="41671-177">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="41671-177">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="41671-178">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="41671-178">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="41671-179">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="41671-179">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="41671-180">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="41671-180">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
