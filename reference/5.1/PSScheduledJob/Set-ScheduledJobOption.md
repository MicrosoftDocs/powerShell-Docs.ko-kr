---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213377"
---
# <span data-ttu-id="999d5-103">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="999d5-103">Set-ScheduledJobOption</span></span>

## <span data-ttu-id="999d5-104">개요</span><span class="sxs-lookup"><span data-stu-id="999d5-104">SYNOPSIS</span></span>
<span data-ttu-id="999d5-105">예약된 작업의 작업 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-105">Changes the job options of a scheduled job.</span></span>

## <span data-ttu-id="999d5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="999d5-106">SYNTAX</span></span>

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="999d5-107">설명</span><span class="sxs-lookup"><span data-stu-id="999d5-107">DESCRIPTION</span></span>
<span data-ttu-id="999d5-108">**Set-ScheduledJobOptions** cmdlet은 예약된 작업의 작업 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-108">The **Set-ScheduledJobOptions** cmdlet changes the job options of scheduled jobs.</span></span>

<span data-ttu-id="999d5-109">예약 된 작업의 옵션을 변경 하려면 먼저 Get-ScheduledJobOption cmdlet을 사용 하 여 예약 된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-109">To change the options of a scheduled job, begin by using the Get-ScheduledJobOption cmdlet to get the job options of a scheduled job.</span></span>
<span data-ttu-id="999d5-110">그런 다음 옵션을 **Set-ScheduledJobOption** 으로 파이프하거나 변수에 저장하고 *Set-ScheduledJobOption* cmdlet의 **InputObject** 매개 변수를 사용하여 옵션을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-110">Then, pipe the options to **Set-ScheduledJobOption** or save the options in a variable and use the *InputObject* parameter of **Set-ScheduledJobOption** cmdlet to identify the options.</span></span>
<span data-ttu-id="999d5-111">**Set-ScheduledJobOption** 의 나머지 매개 변수를 사용하여 작업 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-111">Use the remaining parameters of **Set-ScheduledJobOption** to change the job options.</span></span>

<span data-ttu-id="999d5-112">작업 옵션을 켜려면 해당 옵션을 설정하는 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-112">To turn on a job option, use the parameter that sets that option.</span></span>
<span data-ttu-id="999d5-113">옵션을 해제 하려면 매개 변수 이름, 콜론 (:) 및 $False을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-113">To turn off an option, type the parameter name, a colon (:), and $False.</span></span>
<span data-ttu-id="999d5-114">예를 들어, *Runelevated* 옵션을 해제 하려면를 입력 `-RunElevated:$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-114">For example, to turn off the *RunElevated* option, type `-RunElevated:$False`.</span></span>

<span data-ttu-id="999d5-115">각 작업 옵션 개체에는 매개 변수를 포함하는 JobDefinition 속성이 있으므로 작업 옵션을 변경할 때 예약된 작업과의 연결이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-115">Each job options object includes a JobDefinition property that contains the scheduled job, so the association with the scheduled job is retained when the job options are changed.</span></span>

<span data-ttu-id="999d5-116">예약된 작업 옵션은 작업 스케줄러에서 작업을 시작할 경우 작업 실행 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-116">The scheduled job options determine how the job runs when it is started by Task Scheduler.</span></span>
<span data-ttu-id="999d5-117">Start-Job cmdlet을 사용 하 여 예약 된 작업을 시작할 때는 이러한 옵션이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-117">These options to not apply when you use the Start-Job cmdlet to start a scheduled job.</span></span>

<span data-ttu-id="999d5-118">**Set-scheduledjoboption** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-118">**Set-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="999d5-119">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="999d5-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="999d5-120">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="999d5-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="999d5-121">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="999d5-122">예제</span><span class="sxs-lookup"><span data-stu-id="999d5-122">EXAMPLES</span></span>

### <span data-ttu-id="999d5-123">예제 1: 작업 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="999d5-123">Example 1: Change job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

<span data-ttu-id="999d5-124">이 예제에서는 로컬 컴퓨터에서 예약된 작업의 옵션을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-124">This example shows how to change the options of a scheduled job on the local computer.</span></span>

<span data-ttu-id="999d5-125">첫 번째 명령은 Get-ScheduledJobOption cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-125">The first command uses the Get-ScheduledJobOption cmdlet to get the job options of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="999d5-126">출력은 WakeToRun 및 RunElevated 된 속성이 $False로 설정 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-126">The output shows that the WakeToRun and RunElevated properties are set to $False.</span></span>

<span data-ttu-id="999d5-127">이 명령은 필수가 아닙니다. 단지 옵션 변경의 결과를 보여 주기 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-127">This command is not required; it is included only to show the effect of the option change.</span></span>

### <span data-ttu-id="999d5-128">예제 2: 모든 원격 예약 된 작업에 대 한 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="999d5-128">Example 2: Change an option on all remote scheduled jobs</span></span>

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

<span data-ttu-id="999d5-129">이 명령은 Server01 컴퓨터의 모든 예약 된 작업에서 *IdleTimeout* 값을 1 시간 (기본값)에서 2 시간으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-129">This command changes the value of the *IdleTimeout* from one hour (the default value) to two hours on all scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="999d5-130">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-130">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="999d5-131">원격 명령은 컴퓨터의 모든 예약 된 작업을 가져오는 Get-ScheduledJob 명령으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-131">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="999d5-132">예약 된 작업은 Get-ScheduledJobOption cmdlet으로 파이프 되며, 예약 된 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-132">The scheduled jobs are piped to the Get-ScheduledJobOption cmdlet, which gets the job options of the scheduled jobs.</span></span>
<span data-ttu-id="999d5-133">각 작업 옵션 개체에는 예약된 작업을 포함하는 JobDefinition 속성이 있으므로 옵션 개체가 변경된 경우에도 예약된 작업과 연결된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-133">Each job options object contains a JobDefinition property that contains the scheduled job, so the options object remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="999d5-134">작업 트리거는 **set-scheduledjoboption** cmdlet으로 파이프 되며,이 Cmdlet은 *IdleTimeout* 옵션의 값을 2 시간 (2:00:00)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-134">The job triggers are piped to the **Set-ScheduledJobOption** cmdlet, which changes the value of the *IdleTimeout* option to two hours (2:00:00).</span></span>

## <span data-ttu-id="999d5-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="999d5-135">PARAMETERS</span></span>

### <span data-ttu-id="999d5-136">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="999d5-136">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="999d5-137">작업이 실행되는 동안 컴퓨터가 배터리 전원으로 전환되어도(AC 전원에서 연결 끊김) 예약된 작업을 중지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-137">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="999d5-138">기본적으로 예약된 작업은 컴퓨터가 AC 전원에서 연결이 끊길 때 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-138">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="999d5-139">*ContinueIfGoingOnBattery* 매개 변수는 예약 된 작업의 StopIfGoingOnBatteries 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-139">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="999d5-140">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="999d5-140">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="999d5-141">트리거된 경우에만 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-141">Start the job only when it is triggered.</span></span>
<span data-ttu-id="999d5-142">사용자가 작업 스케줄러의 실행 기능 등을 사용하여 수동으로 작업을 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-142">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="999d5-143">이 매개 변수는 작업 스케줄러에만 영향을 주며</span><span class="sxs-lookup"><span data-stu-id="999d5-143">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="999d5-144">사용자가 Start-Job cmdlet을 사용 하 여 작업을 시작할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-144">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="999d5-145">*DoNotAllowDemandStart* 매개 변수는 예약 된 작업의 DoNotAllowDemandStart 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-145">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="999d5-146">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="999d5-146">-HideInTaskScheduler</span></span>
<span data-ttu-id="999d5-147">작업 스케줄러에 작업을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-147">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="999d5-148">이 값은 작업이 실행되는 컴퓨터에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-148">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="999d5-149">기본적으로 예약된 작업은 작업 스케줄러에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-149">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="999d5-150">태스크가 숨겨진 경우에도 사용자는 작업 스케줄러에서 **숨겨진 작업 보기 표시** 옵션을 선택 하 여 작업을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-150">Even if a task is hidden, users can display the task by selecting the **Show hidden tasks** view option in Task Scheduler.</span></span>

<span data-ttu-id="999d5-151">*HideInTaskScheduler* 매개 변수는 예약 된 작업의 ShowInTaskScheduler 속성 값을 $False로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-151">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="999d5-152">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="999d5-152">-IdleDuration</span></span>
<span data-ttu-id="999d5-153">작업이 시작되기 전에 컴퓨터가 유휴 상태여야 하는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-153">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="999d5-154">기본값은 10분입니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-154">The default value is 10 minutes.</span></span>
<span data-ttu-id="999d5-155">*IdleTimeout* 값이 만료되기 전에 컴퓨터가 지정한 기간 동안 유휴 상태가 아닐 경우 예약된 작업이 다음 예약된 시간(있을 경우)까지 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-155">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="999d5-156">New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-156">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="999d5-157">이 값을 사용하도록 설정하려면 *StartIfIdle* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-157">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="999d5-158">기본적으로 예약 된 작업의 StartIfNotIdle 속성은 $True로 설정 되 고 Windows PowerShell은 *IdleDuration* 및 *IdleTimeout* 값을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-158">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="999d5-159">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="999d5-159">-IdleTimeout</span></span>
<span data-ttu-id="999d5-160">작업이 시작되기 전에 컴퓨터가 유휴 상태여야 하는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-160">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="999d5-161">기본값은 10분입니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-161">The default value is 10 minutes.</span></span>
<span data-ttu-id="999d5-162">**IdleTimeout** 값이 만료되기 전에 컴퓨터가 지정한 기간 동안 유휴 상태가 아닐 경우 예약된 작업이 다음 예약된 시간(있을 경우)까지 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-162">If the computer is not idle for the specified duration before the value of **IdleTimeout** expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="999d5-163">New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-163">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="999d5-164">이 값을 사용하도록 설정하려면 *StartIfIdle* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-164">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="999d5-165">기본적으로 예약 된 작업의 StartIfNotIdle 속성은 $True로 설정 되 고 Windows PowerShell은 *IdleDuration* 및 *IdleTimeout* 값을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-165">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="999d5-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="999d5-166">-InputObject</span></span>
<span data-ttu-id="999d5-167">작업 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-167">Specifies the job options.</span></span>
<span data-ttu-id="999d5-168">**ScheduledJobOptions** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobOptions** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJobOption 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-168">Enter a variable that contains **ScheduledJobOptions** objects or type a command or expression that gets **ScheduledJobOptions** objects, such as a Get-ScheduledJobOption command.</span></span>
<span data-ttu-id="999d5-169">**ScheduledJobOptions** 개체를 **set-scheduledjoboption** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-169">You can also pipe a **ScheduledJobOptions** object to **Set-ScheduledJobOption** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="999d5-170">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="999d5-170">-MultipleInstancePolicy</span></span>
<span data-ttu-id="999d5-171">시스템에서 작업의 다른 인스턴스가 실행되는 동안 예약된 작업 인스턴스를 시작하는 요청에 응답하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-171">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="999d5-172">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="999d5-173">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="999d5-173">IgnoreNew.</span></span>
<span data-ttu-id="999d5-174">새 작업 인스턴스가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-174">The new job instance is ignored.</span></span>
<span data-ttu-id="999d5-175">이것은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-175">This is the default value.</span></span>
- <span data-ttu-id="999d5-176">병렬입니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-176">Parallel.</span></span>
<span data-ttu-id="999d5-177">새 작업 인스턴스가 즉시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-177">The new job instance starts immediately.</span></span>
- <span data-ttu-id="999d5-178">큐.</span><span class="sxs-lookup"><span data-stu-id="999d5-178">Queue.</span></span>
<span data-ttu-id="999d5-179">현재 인스턴스가 완료되는 즉시 새 작업 인스턴스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-179">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="999d5-180">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="999d5-180">StopExisting.</span></span>
<span data-ttu-id="999d5-181">현재 작업 인스턴스가 중지되고 새 인스턴스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-181">The current instance of the job stop and the new instance starts.</span></span>

<span data-ttu-id="999d5-182">작업을 실행하려면 작업 일정에 대한 모든 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-182">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="999d5-183">예를 들어 *RequireNetwork* , *IdleDuration* 및 *IdleTimeout* 매개 변수에 의해 설정 된 조건이 충족 되지 않으면이 매개 변수의 값에 관계 없이 작업 인스턴스가 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-183">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="999d5-184">-PassThru</span><span class="sxs-lookup"><span data-stu-id="999d5-184">-PassThru</span></span>
<span data-ttu-id="999d5-185">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-185">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="999d5-186">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-186">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="999d5-187">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="999d5-187">-RequireNetwork</span></span>
<span data-ttu-id="999d5-188">네트워크 연결을 사용할 수 있을 때만 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-188">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="999d5-189">이 매개 변수를 지정하고 예약된 시작 시간에 네트워크를 사용할 수 없는 경우 다음 예약된 시작 시간(있을 경우)까지 작업이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-189">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="999d5-190">*RequireNetwork* 매개 변수는 예약 된 작업의 RunWithoutNetwork 속성 값을 $False 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-190">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="999d5-191">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="999d5-191">-RestartOnIdleResume</span></span>
<span data-ttu-id="999d5-192">컴퓨터가 유휴 상태가 되면 예약된 작업을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-192">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="999d5-193">이 매개 변수는 컴퓨터가 활성 상태가 될 경우(유휴 상태 종료) 실행 중인 예약된 작업을 일시 중단하는 *StopIfGoingOffIdle* 매개 변수와 함께 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-193">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="999d5-194">*RestartOnIdleResume* 매개 변수는 예약 된 작업의 RestartOnIdleResume 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-194">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="999d5-195">-RunElevated 된</span><span class="sxs-lookup"><span data-stu-id="999d5-195">-RunElevated</span></span>
<span data-ttu-id="999d5-196">작업이 실행되는 컴퓨터의 Administrators 그룹 구성원 권한으로 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-196">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="999d5-197">관리자 권한으로 예약 된 작업을 실행할 수 있도록 설정 하려면 Register-ScheduledJob의 *credential* 매개 변수를 사용 하 여 작업에 대 한 명시적 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-197">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="999d5-198">**Runelevated** 된 매개 변수는 예약 된 작업의 **runelevated** 된 속성 값을 True로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-198">The **RunElevated** parameter sets the value of the **RunElevated** property of scheduled jobs to True.</span></span>

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

### <span data-ttu-id="999d5-199">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="999d5-199">-StartIfIdle</span></span>
<span data-ttu-id="999d5-200">**IdleTimeout** 매개 변수에 지정된 시간이 만료되기 전에 컴퓨터가 *IdleDuration* 매개 변수에 지정된 시간 동안 유휴 상태였을 경우 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-200">Starts the scheduled job if the computer has been idle for the time specified by the **IdleDuration** parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="999d5-201">기본적으로 *IdleDuration* 및 *IdleTimeout* 매개 변수는 무시되고 컴퓨터가 사용 중이라도 예약된 시작 시간에 작업이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-201">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="999d5-202">이 매개 변수를 지정하고 예약된 시작 시간에 컴퓨터가 사용 중일 경우(유휴 상태 아님) 다음 예약된 시작 시간(있을 경우)까지 작업이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-202">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="999d5-203">*StartIfIdle* 매개 변수는 예약 된 작업의 **StartIfNotIdle** 속성 값을 False로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-203">The *StartIfIdle* parameter sets the value of the **StartIfNotIdle** property of scheduled jobs to False.</span></span>

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

### <span data-ttu-id="999d5-204">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="999d5-204">-StartIfOnBattery</span></span>
<span data-ttu-id="999d5-205">예약된 시작 시간에 컴퓨터가 배터리 전원으로 실행되고 있어도 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-205">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="999d5-206">기본값은 False입니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-206">The default value is False.</span></span>

<span data-ttu-id="999d5-207">*StartIfOnBattery* 매개 변수는 예약 된 작업의 **StartIfOnBatteries** 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-207">The *StartIfOnBattery* parameter sets the value of the **StartIfOnBatteries** property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="999d5-208">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="999d5-208">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="999d5-209">작업이 실행되는 동안 컴퓨터가 활성 상태가 될 경우(유휴 상태 아님) 실행 중인 예약된 작업을 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-209">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="999d5-210">기본적으로 컴퓨터가 활성 상태일 때 일시 중단되는 예약된 작업은 컴퓨터가 다시 유휴 상태가 되면 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-210">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="999d5-211">이 기본 동작을 변경하려면 *RestartOnIdleResume* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-211">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="999d5-212">*StopIfGoingOffIdle* 매개 변수는 예약 된 작업의 StopIfGoingOffIdle 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-212">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="999d5-213">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="999d5-213">-WakeToRun</span></span>
<span data-ttu-id="999d5-214">작업을 실행할 수 있도록 예약된 시작 시간에 컴퓨터를 최대 절전 또는 절전 모드에서 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-214">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="999d5-215">기본적으로 컴퓨터가 예약된 시작 시간에 최대 절전 또는 절전 모드에 있는 경우 작업이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-215">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="999d5-216">*WakeToRun* 매개 변수는 예약 된 작업의 WakeToRun 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-216">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="999d5-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="999d5-217">CommonParameters</span></span>
<span data-ttu-id="999d5-218">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="999d5-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="999d5-219">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="999d5-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="999d5-220">입력</span><span class="sxs-lookup"><span data-stu-id="999d5-220">INPUTS</span></span>

### <span data-ttu-id="999d5-221">Set-scheduledjob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="999d5-221">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="999d5-222">예약된 작업 옵션을 **Set-ScheduledJobOption** 으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-222">You can pipe a scheduled job options object to **Set-ScheduledJobOption** .</span></span>

## <span data-ttu-id="999d5-223">출력</span><span class="sxs-lookup"><span data-stu-id="999d5-223">OUTPUTS</span></span>

### <span data-ttu-id="999d5-224">None 또는 Set-scheduledjob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="999d5-224">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="999d5-225">*Passthru* 매개 변수를 사용할 경우 **Set-ScheduledJobOption** 은 변경된 작업 옵션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-225">When you use the *Passthru* parameter, **Set-ScheduledJobOption** returns the job options that were changed.</span></span>
<span data-ttu-id="999d5-226">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="999d5-226">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="999d5-227">참고</span><span class="sxs-lookup"><span data-stu-id="999d5-227">NOTES</span></span>

## <span data-ttu-id="999d5-228">관련 링크</span><span class="sxs-lookup"><span data-stu-id="999d5-228">RELATED LINKS</span></span>

[<span data-ttu-id="999d5-229">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="999d5-229">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="999d5-230">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="999d5-230">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="999d5-231">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="999d5-231">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="999d5-232">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="999d5-232">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="999d5-233">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="999d5-233">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="999d5-234">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="999d5-234">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="999d5-235">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="999d5-235">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="999d5-236">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="999d5-236">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="999d5-237">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="999d5-237">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="999d5-238">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="999d5-238">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="999d5-239">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="999d5-239">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="999d5-240">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="999d5-240">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="999d5-241">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="999d5-241">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="999d5-242">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="999d5-242">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="999d5-243">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="999d5-243">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="999d5-244">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="999d5-244">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
