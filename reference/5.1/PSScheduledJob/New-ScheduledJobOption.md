---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213418"
---
# <span data-ttu-id="c04ef-103">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c04ef-103">New-ScheduledJobOption</span></span>

## <span data-ttu-id="c04ef-104">개요</span><span class="sxs-lookup"><span data-stu-id="c04ef-104">SYNOPSIS</span></span>
<span data-ttu-id="c04ef-105">예약된 작업에 대한 고급 옵션을 포함하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-105">Creates an object that contains advanced options for a scheduled job.</span></span>

## <span data-ttu-id="c04ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c04ef-106">SYNTAX</span></span>

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="c04ef-107">설명</span><span class="sxs-lookup"><span data-stu-id="c04ef-107">DESCRIPTION</span></span>
<span data-ttu-id="c04ef-108">**New-ScheduledJobOption** cmdlet은 예약된 작업에 대한 고급 옵션을 포함하는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-108">The **New-ScheduledJobOption** cmdlet creates an object that contains advanced options for a scheduled job.</span></span>

<span data-ttu-id="c04ef-109">**ScheduledJobOptions** 가 반환하는 **New-ScheduledJobOption** 개체를 사용하여 새 예약된 작업이나 기존 예약된 작업에 대한 작업 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-109">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set job options for a new or existing scheduled job.</span></span>
<span data-ttu-id="c04ef-110">또는 Get-ScheduledJobOption cmdlet을 사용 하 여 작업 옵션을 설정 하 여 기존 예약 된 작업의 작업 옵션을 가져오거나 해시 테이블 값을 사용 하 여 작업 옵션을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-110">Alternatively, you can set job options by using the Get-ScheduledJobOption cmdlet to get the job options of an existing scheduled job or by using a hash table value to represent the job options.</span></span>

<span data-ttu-id="c04ef-111">매개 변수가 없으면 **set-scheduledjoboption** 는 모든 옵션에 대 한 기본값을 포함 하는 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-111">Without parameters, **New-ScheduledJobOption** generates an object that contains the default values for all of the options.</span></span>
<span data-ttu-id="c04ef-112">JobDefinition 속성을 제외한 모든 속성을 편집할 수 있으므로 결과 개체를 템플릿으로 사용하고 엔터프라이즈에 대한 표준 옵션 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-112">Because all of the properties except for the JobDefinition property can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="c04ef-113">예약된 작업을 만들고 예약된 작업 옵션을 설정하는 경우 모든 예약된 작업 옵션의 기본값을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-113">When creating scheduled jobs and setting scheduled job options, review the default values of all scheduled job options.</span></span>
<span data-ttu-id="c04ef-114">예약된 작업은 설정된 모든 실행 조건이 충족될 경우에만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-114">Scheduled jobs run only when all conditions set for their execution are satisfied.</span></span>

<span data-ttu-id="c04ef-115">**Set-scheduledjoboption** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-115">**New-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="c04ef-116">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c04ef-116">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="c04ef-117">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c04ef-117">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="c04ef-118">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="c04ef-119">예제</span><span class="sxs-lookup"><span data-stu-id="c04ef-119">EXAMPLES</span></span>

### <span data-ttu-id="c04ef-120">예 1: 기본값을 사용 하 여 예약 된 작업 옵션 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="c04ef-120">Example 1: Create a scheduled job option object with default values</span></span>

```
PS C:\> New-ScheduledJobOption
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
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="c04ef-121">이 명령은 모든 기본값이 포함된 예약된 작업 옵션 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-121">This command creates a scheduled job option object that has all of the default values.</span></span>

### <span data-ttu-id="c04ef-122">예제 2: 사용자 지정 값을 사용 하 여 예약 된 작업 옵션 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="c04ef-122">Example 2: Create a scheduled job option object with custom values</span></span>

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
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
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="c04ef-123">다음 명령은 네트워크가 필요한 예약된 작업 개체를 만들고 컴퓨터가 AC 전원에 연결되어 있지 않아도 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-123">The following command creates a scheduled job object that requires the network and runs the scheduled job even if the computer is not connected to AC power.</span></span>

<span data-ttu-id="c04ef-124">출력은 *RequireNetwork* 매개 변수가 RunWithoutNetwork 속성의 값을 $False로 변경 하 고 *StartIfOnBattery* 매개 변수가 StartIfOnBatteries 속성의 값을 $True로 변경 함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-124">The output shows that the *RequireNetwork* parameter changed the value of the RunWithoutNetwork property to $False and the *StartIfOnBattery* parameter changed the value of the StartIfOnBatteries property to $True.</span></span>

### <span data-ttu-id="c04ef-125">예 3: 새 예약 된 작업에 대 한 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c04ef-125">Example 3: Set options for a new scheduled job</span></span>

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="c04ef-126">이 예제에서는 **New-ScheduledJobOption** 이 반환하는 **ScheduledJobOptions** 개체를 사용하여 새 예약된 작업에 대한 옵션을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-126">This example shows how to use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set the options for a new scheduled job.</span></span>

### <span data-ttu-id="c04ef-127">예 4: 예약 된 작업 옵션 개체의 속성 정렬</span><span class="sxs-lookup"><span data-stu-id="c04ef-127">Example 4: Sort the properties of a scheduled job option object</span></span>

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

<span data-ttu-id="c04ef-128">이 예제에서는 **ScheduledJobOptions** 개체의 속성을 읽기 쉽도록 사전순으로 정렬하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-128">This example shows how to sort the properties of a **ScheduledJobOptions** object in alphabetical order for easy reading.</span></span>

<span data-ttu-id="c04ef-129">첫 번째 명령은 **New-ScheduledJobOption** cmdlet을 사용하여 **ScheduledJobOptions** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-129">The first command uses the **New-ScheduledJobOption** cmdlet to create a **ScheduledJobOptions** object.</span></span>
<span data-ttu-id="c04ef-130">*WakeToRun* 매개 변수를 사용하고 결과 개체를 $Options 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-130">The command uses the *WakeToRun* parameter and saves the resulting object in the $Options variable.</span></span>

<span data-ttu-id="c04ef-131">개체 $Options의 속성을 가져오기 위해 두 번째 명령은 모든 Windows PowerShell 개체의 **PSObject** 속성과 해당 속성 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-131">To get the properties of $Options as objects, the second command uses the **PSObject** property of all Windows PowerShell objects and its Properties property.</span></span>
<span data-ttu-id="c04ef-132">그런 다음이 명령은 속성 개체를 Sort-Object cmdlet으로 파이프 합니다 .이 cmdlet은 속성을 사전순으로 정렬 한 다음 Format-Table cmdlet으로 정렬 하 여 테이블에 속성의 이름과 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-132">The command then pipes the property objects to the Sort-Object cmdlet, which sorts the properties in alphabetical order by name, and then to the Format-Table cmdlet, which displays the names and values of the properties in a table.</span></span>

<span data-ttu-id="c04ef-133">이 형식을 사용 하면 $Options에서 **ScheduledJobOptions** 개체의 WakeToRun 속성을 보다 쉽게 찾을 수 있으며 해당 값이 $False에서 $True로 변경 되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-133">This format makes it much easier to find the WakeToRun property of the **ScheduledJobOptions** object in $Options and to verify that its value was changed from $False to $True.</span></span>

## <span data-ttu-id="c04ef-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c04ef-134">PARAMETERS</span></span>

### <span data-ttu-id="c04ef-135">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="c04ef-135">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="c04ef-136">작업이 실행되는 동안 컴퓨터가 배터리 전원으로 전환되어도(AC 전원에서 연결 끊김) 예약된 작업을 중지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-136">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="c04ef-137">기본적으로 예약된 작업은 컴퓨터가 AC 전원에서 연결이 끊길 때 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-137">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="c04ef-138">*ContinueIfGoingOnBattery* 매개 변수는 예약 된 작업의 StopIfGoingOnBatteries 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-138">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="c04ef-139">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="c04ef-139">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="c04ef-140">트리거된 경우에만 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-140">Start the job only when it is triggered.</span></span>
<span data-ttu-id="c04ef-141">사용자가 작업 스케줄러의 실행 기능 등을 사용하여 수동으로 작업을 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-141">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="c04ef-142">이 매개 변수는 작업 스케줄러에만 영향을 주며</span><span class="sxs-lookup"><span data-stu-id="c04ef-142">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="c04ef-143">사용자가 Start-Job cmdlet을 사용 하 여 작업을 시작할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-143">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="c04ef-144">*DoNotAllowDemandStart* 매개 변수는 예약 된 작업의 DoNotAllowDemandStart 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-144">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="c04ef-145">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="c04ef-145">-HideInTaskScheduler</span></span>
<span data-ttu-id="c04ef-146">작업 스케줄러에 작업을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-146">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="c04ef-147">이 값은 작업이 실행되는 컴퓨터에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-147">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="c04ef-148">기본적으로 예약된 작업은 작업 스케줄러에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-148">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="c04ef-149">태스크가 숨겨진 경우에도 사용자는 작업 스케줄러에서 숨겨진 작업 보기 표시 옵션을 선택 하 여 작업을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-149">Even if a task is hidden, users can display the task by selecting the Show hidden tasks view option in Task Scheduler.</span></span>

<span data-ttu-id="c04ef-150">*HideInTaskScheduler* 매개 변수는 예약 된 작업의 ShowInTaskScheduler 속성 값을 $False로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-150">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="c04ef-151">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="c04ef-151">-IdleDuration</span></span>
<span data-ttu-id="c04ef-152">작업이 시작되기 전에 컴퓨터가 유휴 상태여야 하는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-152">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="c04ef-153">기본값은 10분입니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-153">The default value is 10 minutes.</span></span>
<span data-ttu-id="c04ef-154">*IdleTimeout* 값이 만료되기 전에 컴퓨터가 지정한 기간 동안 유휴 상태가 아닐 경우 예약된 작업이 다음 예약된 시간(있을 경우)까지 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-154">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="c04ef-155">New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 **timespan** 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-155">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format  that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="c04ef-156">이 값을 사용하도록 설정하려면 *StartIfIdle* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-156">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="c04ef-157">기본적으로 예약 된 작업의 StartIfNotIdle 속성은 $True로 설정 되 고 Windows PowerShell은 *IdleDuration* 및 *IdleTimeout* 값을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-157">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="c04ef-158">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="c04ef-158">-IdleTimeout</span></span>
<span data-ttu-id="c04ef-159">예약된 작업이 컴퓨터가 유휴 상태가 되기를 기다리는 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-159">Specifies how long the scheduled job waits for the computer to be idle.</span></span>
<span data-ttu-id="c04ef-160">컴퓨터가 *IdleDuration* 매개 변수에 지정된 기간 동안 유휴 상태로 유지되기 전에 이 시간 제한이 만료될 경우 다음 예약된 시간(있을 경우)까지 작업이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-160">If this timeout expires before the computer remains idle for the time period that is specified by the *IdleDuration* parameter, the job does not run until the next scheduled time, if any.</span></span>
<span data-ttu-id="c04ef-161">기본값은 1시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-161">The default value is one hour.</span></span>

<span data-ttu-id="c04ef-162">New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 **timespan** 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-162">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="c04ef-163">이 값을 사용하도록 설정하려면 *StartIfIdle* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-163">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="c04ef-164">기본적으로 예약 된 작업의 StartIfNotIdle 속성은 $True로 설정 되 고 Windows PowerShell은 *IdleDuration* 및 *IdleTimeout* 값을 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-164">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="c04ef-165">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="c04ef-165">-MultipleInstancePolicy</span></span>
<span data-ttu-id="c04ef-166">시스템에서 작업의 다른 인스턴스가 실행되는 동안 예약된 작업 인스턴스를 시작하는 요청에 응답하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-166">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="c04ef-167">기본값은 IgnoreNew입니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-167">The default value is IgnoreNew.</span></span>
<span data-ttu-id="c04ef-168">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-168">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c04ef-169">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="c04ef-169">IgnoreNew.</span></span>
<span data-ttu-id="c04ef-170">새 작업 인스턴스가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-170">The new job instance is ignored.</span></span>
- <span data-ttu-id="c04ef-171">병렬입니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-171">Parallel.</span></span>
<span data-ttu-id="c04ef-172">새 작업 인스턴스가 즉시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-172">The new job instance starts immediately.</span></span>
- <span data-ttu-id="c04ef-173">큐.</span><span class="sxs-lookup"><span data-stu-id="c04ef-173">Queue.</span></span>
<span data-ttu-id="c04ef-174">현재 인스턴스가 완료되는 즉시 새 작업 인스턴스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-174">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="c04ef-175">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="c04ef-175">StopExisting.</span></span>
<span data-ttu-id="c04ef-176">현재 작업 인스턴스가 중지 되 고 새 인스턴스가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-176">The current instance of the job stops and the new instance starts.</span></span>

<span data-ttu-id="c04ef-177">작업을 실행하려면 작업 일정에 대한 모든 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-177">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="c04ef-178">예를 들어 *RequireNetwork* , *IdleDuration* 및 *IdleTimeout* 매개 변수에 의해 설정 된 조건이 충족 되지 않으면이 매개 변수의 값에 관계 없이 작업 인스턴스가 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-178">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

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

### <span data-ttu-id="c04ef-179">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="c04ef-179">-RequireNetwork</span></span>
<span data-ttu-id="c04ef-180">네트워크 연결을 사용할 수 있을 때만 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-180">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="c04ef-181">이 매개 변수를 지정하고 예약된 시작 시간에 네트워크를 사용할 수 없는 경우 다음 예약된 시작 시간(있을 경우)까지 작업이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-181">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="c04ef-182">*RequireNetwork* 매개 변수는 예약 된 작업의 RunWithoutNetwork 속성 값을 $False 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-182">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="c04ef-183">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="c04ef-183">-RestartOnIdleResume</span></span>
<span data-ttu-id="c04ef-184">컴퓨터가 유휴 상태가 되면 예약된 작업을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-184">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="c04ef-185">이 매개 변수는 컴퓨터가 활성 상태가 될 경우(유휴 상태 종료) 실행 중인 예약된 작업을 일시 중단하는 *StopIfGoingOffIdle* 매개 변수와 함께 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-185">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="c04ef-186">*RestartOnIdleResume* 매개 변수는 예약 된 작업의 RestartOnIdleResume 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-186">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="c04ef-187">-RunElevated 된</span><span class="sxs-lookup"><span data-stu-id="c04ef-187">-RunElevated</span></span>
<span data-ttu-id="c04ef-188">작업이 실행되는 컴퓨터의 Administrators 그룹 구성원 권한으로 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-188">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="c04ef-189">관리자 권한으로 예약 된 작업을 실행할 수 있도록 설정 하려면 Register-ScheduledJob의 *credential* 매개 변수를 사용 하 여 작업에 대 한 명시적 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-189">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="c04ef-190">*Runelevated* 된 매개 변수는 예약 된 작업의 runelevated 된 속성 값을 $True로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-190">The *RunElevated* parameter sets the value of the RunElevated property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="c04ef-191">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="c04ef-191">-StartIfIdle</span></span>
<span data-ttu-id="c04ef-192">*IdleTimeout* 매개 변수에 지정된 시간이 만료되기 전에 컴퓨터가 *IdleDuration* 매개 변수에 지정된 시간 동안 유휴 상태였을 경우 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-192">Starts the scheduled job if the computer has been idle for the time specified by the *IdleDuration* parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="c04ef-193">기본적으로 *IdleDuration* 및 *IdleTimeout* 매개 변수는 무시되고 컴퓨터가 사용 중이라도 예약된 시작 시간에 작업이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-193">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="c04ef-194">이 매개 변수를 지정하고 예약된 시작 시간에 컴퓨터가 사용 중일 경우(유휴 상태 아님) 다음 예약된 시작 시간(있을 경우)까지 작업이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-194">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="c04ef-195">*StartIfIdle* 매개 변수는 예약 된 작업의 StartIfNotIdle 속성 값을 $False 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-195">The *StartIfIdle* parameter sets the value of the StartIfNotIdle property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="c04ef-196">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="c04ef-196">-StartIfOnBattery</span></span>
<span data-ttu-id="c04ef-197">예약된 시작 시간에 컴퓨터가 배터리 전원으로 실행되고 있어도 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-197">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="c04ef-198">기본값은 $False입니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-198">The default value is $False.</span></span>

<span data-ttu-id="c04ef-199">*StartIfOnBattery* 매개 변수는 예약 된 작업의 StartIfOnBatteries 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-199">The *StartIfOnBattery* parameter sets the value of the StartIfOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="c04ef-200">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="c04ef-200">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="c04ef-201">작업이 실행되는 동안 컴퓨터가 활성 상태가 될 경우(유휴 상태 아님) 실행 중인 예약된 작업을 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-201">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="c04ef-202">기본적으로 컴퓨터가 활성 상태일 때 일시 중단되는 예약된 작업은 컴퓨터가 다시 유휴 상태가 되면 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-202">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="c04ef-203">이 기본 동작을 변경하려면 *RestartOnIdleResume* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-203">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="c04ef-204">*StopIfGoingOffIdle* 매개 변수는 예약 된 작업의 StopIfGoingOffIdle 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-204">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="c04ef-205">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="c04ef-205">-WakeToRun</span></span>
<span data-ttu-id="c04ef-206">작업을 실행할 수 있도록 예약된 시작 시간에 컴퓨터를 최대 절전 또는 절전 모드에서 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-206">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="c04ef-207">기본적으로 컴퓨터가 예약된 시작 시간에 최대 절전 또는 절전 모드에 있는 경우 작업이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-207">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="c04ef-208">*WakeToRun* 매개 변수는 예약 된 작업의 WakeToRun 속성 값을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-208">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="c04ef-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c04ef-209">CommonParameters</span></span>
<span data-ttu-id="c04ef-210">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c04ef-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c04ef-211">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c04ef-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c04ef-212">입력</span><span class="sxs-lookup"><span data-stu-id="c04ef-212">INPUTS</span></span>

### <span data-ttu-id="c04ef-213">없음</span><span class="sxs-lookup"><span data-stu-id="c04ef-213">None</span></span>
<span data-ttu-id="c04ef-214">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c04ef-215">출력</span><span class="sxs-lookup"><span data-stu-id="c04ef-215">OUTPUTS</span></span>

### <span data-ttu-id="c04ef-216">Set-scheduledjob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="c04ef-216">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="c04ef-217">참고</span><span class="sxs-lookup"><span data-stu-id="c04ef-217">NOTES</span></span>

* <span data-ttu-id="c04ef-218">**Set-scheduledjoboption** 에서 생성 하는 **ScheduledJobOptions** 개체를 Register-ScheduledJob cmdlet의 *set-scheduledjoboption* 매개 변수 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-218">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** creates as the value of the *ScheduledJobOption* parameter of the Register-ScheduledJob cmdlet.</span></span> <span data-ttu-id="c04ef-219">그러나 *set-scheduledjoboption* 매개 변수는 **ScheduledJobOptions** 개체의 속성과 해당 값 (예:)을 지정 하는 해시 테이블 값도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c04ef-219">However, the *ScheduledJobOption* parameter can also take a hash table value that specifies the properties of the **ScheduledJobOptions** object and their values, such as:</span></span>

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## <span data-ttu-id="c04ef-220">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c04ef-220">RELATED LINKS</span></span>

[<span data-ttu-id="c04ef-221">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c04ef-221">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="c04ef-222">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c04ef-222">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="c04ef-223">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c04ef-223">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="c04ef-224">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c04ef-224">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="c04ef-225">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c04ef-225">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="c04ef-226">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c04ef-226">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="c04ef-227">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c04ef-227">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="c04ef-228">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c04ef-228">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="c04ef-229">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c04ef-229">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="c04ef-230">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c04ef-230">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="c04ef-231">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c04ef-231">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="c04ef-232">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c04ef-232">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="c04ef-233">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c04ef-233">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="c04ef-234">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c04ef-234">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="c04ef-235">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c04ef-235">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="c04ef-236">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c04ef-236">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
