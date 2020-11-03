---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213426"
---
# <span data-ttu-id="3a5b8-103">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3a5b8-103">Get-ScheduledJobOption</span></span>

## <span data-ttu-id="3a5b8-104">개요</span><span class="sxs-lookup"><span data-stu-id="3a5b8-104">SYNOPSIS</span></span>
<span data-ttu-id="3a5b8-105">예약된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-105">Gets the job options of scheduled jobs.</span></span>

## <span data-ttu-id="3a5b8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3a5b8-106">SYNTAX</span></span>

### <span data-ttu-id="3a5b8-107">JobDefinition (기본값)</span><span class="sxs-lookup"><span data-stu-id="3a5b8-107">JobDefinition (Default)</span></span>

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="3a5b8-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="3a5b8-108">JobDefinitionId</span></span>

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="3a5b8-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="3a5b8-109">JobDefinitionName</span></span>

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="3a5b8-110">설명</span><span class="sxs-lookup"><span data-stu-id="3a5b8-110">DESCRIPTION</span></span>
<span data-ttu-id="3a5b8-111">**Set-scheduledjoboption** cmdlet은 예약 된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-111">The **Get-ScheduledJobOption** cmdlet gets the job options of scheduled jobs.</span></span>
<span data-ttu-id="3a5b8-112">이 명령을 사용하여 작업 옵션을 검사하거나 작업 옵션을 다른 cmdlet으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-112">You can use this command to examine the job options or to pipe the job options to other cmdlets.</span></span>

<span data-ttu-id="3a5b8-113">작업 옵션은 독립적으로 디스크에 저장되지 않고 예약된 작업의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-113">Job options are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="3a5b8-114">예약된 작업의 작업 옵션을 가져오려면 예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-114">To get the job options of a scheduled job, specify the scheduled job.</span></span>

<span data-ttu-id="3a5b8-115">**Get-ScheduledJobOption** cmdlet의 매개 변수를 사용하여 예약된 작업을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-115">Use the parameters of the **Get-ScheduledJobOption** cmdlet to identify the scheduled job.</span></span>
<span data-ttu-id="3a5b8-116">이름 또는 id 번호를 기준으로 예약 된 작업을 식별 하거나 Get-ScheduledJob cmdlet에서 반환 되는 개체 (예: **set-scheduledjoboption** 로 반환 되는 개체)를 입력 하거나 파이프 하 여 **set-scheduledjob** 개체를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-116">You can identify scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-ScheduledJobOption** .</span></span>

<span data-ttu-id="3a5b8-117">**Set-scheduledjoboption** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-117">**Get-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="3a5b8-118">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="3a5b8-119">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="3a5b8-120">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3a5b8-121">예제</span><span class="sxs-lookup"><span data-stu-id="3a5b8-121">EXAMPLES</span></span>

### <span data-ttu-id="3a5b8-122">예제 1: 작업 옵션 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a5b8-122">Example 1: Get job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : False

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="3a5b8-123">이 명령은 이름에 백업이 있는 예약 된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-123">This command gets the job options of scheduled jobs that have BackUp in their names.</span></span>
<span data-ttu-id="3a5b8-124">결과는 **Get-ScheduledJobOption** 에서 반환된 작업 옵션 개체를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-124">The results show the job options object that **Get-ScheduledJobOption** returned.</span></span>

### <span data-ttu-id="3a5b8-125">예제 2: 모든 작업 옵션 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a5b8-125">Example 2: Get all job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

<span data-ttu-id="3a5b8-126">이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-126">This command gets the job options of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="3a5b8-127">Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-127">It uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="3a5b8-128">파이프라인 연산자 (|)가 예약 된 작업을 **set-scheduledjoboption** cmdlet으로 보내면이 cmdlet이 각 예약 된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-128">A pipeline operator (|) sends the scheduled jobs to the **Get-ScheduledJobOption** cmdlet, which gets the job options of each scheduled job.</span></span>

### <span data-ttu-id="3a5b8-129">예 3: 선택한 작업 옵션 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a5b8-129">Example 3: Get selected job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

<span data-ttu-id="3a5b8-130">이 예제에서는 특정 값을 가진 작업 옵션 개체를 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-130">This example shows how to find job options object with particular values.</span></span>

<span data-ttu-id="3a5b8-131">첫 번째 명령은 RunElevated 된 속성 값이 $True이 고 RunWithoutNetwork 속성 값이 $False 인 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-131">The first command gets job options in which the RunElevated property has a value of $True and the RunWithoutNetwork property has a value of $False.</span></span>
<span data-ttu-id="3a5b8-132">출력에는 선택한 **JobOptions** 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-132">The output shows the **JobOptions** object that was selected.</span></span>

### <span data-ttu-id="3a5b8-133">예 4: 작업 옵션을 사용 하 여 새 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="3a5b8-133">Example 4: Use job options to create a new job</span></span>

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

<span data-ttu-id="3a5b8-134">이 예에서는 Get-ScheduledJobOption 새 예약 된 작업에 가져오는 작업 옵션을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-134">This example shows how to use the job options that Get-ScheduledJobOption gets in a new scheduled job.</span></span>

<span data-ttu-id="3a5b8-135">첫 번째 명령은 **set-scheduledjoboption** 를 사용 하 여 BackupTestLogs 예약 된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-135">The first command uses **Get-ScheduledJobOption** to get the jobs options of the BackupTestLogs scheduled job.</span></span>
<span data-ttu-id="3a5b8-136">옵션을 $Opts 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-136">The command saves the options in the $Opts variable.</span></span>

<span data-ttu-id="3a5b8-137">두 번째 명령은 Register-ScheduledJob cmdlet을 사용 하 여 새 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-137">The second command uses Register-ScheduledJob cmdlet to create a new scheduled job.</span></span>
<span data-ttu-id="3a5b8-138">*ScheduledJobOption* 매개 변수 값은 $Opts 변수에 있는 옵션 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-138">The value of the *ScheduledJobOption* parameter is the options object in the $Opts variable.</span></span>

### <span data-ttu-id="3a5b8-139">예 5: 원격 컴퓨터에서 작업 옵션 가져오기</span><span class="sxs-lookup"><span data-stu-id="3a5b8-139">Example 5: Get job options from a remote computer</span></span>

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

<span data-ttu-id="3a5b8-140">이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 컴퓨터에서 DataDemon 작업의 예약 된 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-140">This command uses the Invoke-Command cmdlet to get the scheduled job options of the DataDemon job on the Srv01 computer.</span></span>
<span data-ttu-id="3a5b8-141">이 명령은 $O 변수의 옵션을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-141">The command saves the options in the $O variable.</span></span>

## <span data-ttu-id="3a5b8-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3a5b8-142">PARAMETERS</span></span>

### <span data-ttu-id="3a5b8-143">-Id</span><span class="sxs-lookup"><span data-stu-id="3a5b8-143">-Id</span></span>
<span data-ttu-id="3a5b8-144">예약된 작업의 ID 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-144">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="3a5b8-145">**Get-ScheduledJobOption** 은 지정한 예약된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-145">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>

<span data-ttu-id="3a5b8-146">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 id 번호를 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-146">To get the identification numbers of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3a5b8-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3a5b8-147">-InputObject</span></span>
<span data-ttu-id="3a5b8-148">예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-148">Specifies a scheduled job.</span></span>
<span data-ttu-id="3a5b8-149">**Set-scheduledjob** 개체가 포함 된 변수를 입력 하거나 **set-scheduledjob** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-149">Enter a variable that contains a **ScheduledJob** object or type a command or expression that gets a **ScheduledJob** object, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="3a5b8-150">**Set-scheduledjob** 개체를 **set-scheduledjoboption** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-150">You can also pipe a **ScheduledJob** object to **Get-ScheduledJobOption** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3a5b8-151">-Name</span><span class="sxs-lookup"><span data-stu-id="3a5b8-151">-Name</span></span>
<span data-ttu-id="3a5b8-152">예약된 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-152">Specifies the names of scheduled jobs.</span></span>
<span data-ttu-id="3a5b8-153">**Get-ScheduledJobOption** 은 지정한 예약된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-153">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>
<span data-ttu-id="3a5b8-154">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-154">Wildcards are supported.</span></span>

<span data-ttu-id="3a5b8-155">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 이름을 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-155">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3a5b8-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3a5b8-156">CommonParameters</span></span>
<span data-ttu-id="3a5b8-157">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3a5b8-158">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3a5b8-159">입력</span><span class="sxs-lookup"><span data-stu-id="3a5b8-159">INPUTS</span></span>

### <span data-ttu-id="3a5b8-160">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="3a5b8-160">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="3a5b8-161">Get-ScheduledJob에서 **set-scheduledjoboption** 로 예약 된 작업을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a5b8-161">You can pipe a scheduled job from Get-ScheduledJob to **Get-ScheduledJobOption** .</span></span>

## <span data-ttu-id="3a5b8-162">출력</span><span class="sxs-lookup"><span data-stu-id="3a5b8-162">OUTPUTS</span></span>

### <span data-ttu-id="3a5b8-163">Set-scheduledjob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="3a5b8-163">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="3a5b8-164">참고</span><span class="sxs-lookup"><span data-stu-id="3a5b8-164">NOTES</span></span>

## <span data-ttu-id="3a5b8-165">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3a5b8-165">RELATED LINKS</span></span>

[<span data-ttu-id="3a5b8-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a5b8-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="3a5b8-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a5b8-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="3a5b8-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a5b8-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="3a5b8-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a5b8-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="3a5b8-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a5b8-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="3a5b8-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a5b8-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="3a5b8-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a5b8-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="3a5b8-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3a5b8-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="3a5b8-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a5b8-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="3a5b8-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3a5b8-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="3a5b8-176">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a5b8-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="3a5b8-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a5b8-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="3a5b8-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3a5b8-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="3a5b8-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a5b8-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="3a5b8-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3a5b8-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="3a5b8-181">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3a5b8-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
