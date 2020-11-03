---
description: 예약된 작업을 만들고 관리하는 방법에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221929"
---
# <a name="about-scheduled-jobs-basics"></a><span data-ttu-id="304e0-104">예약 된 작업 기본 사항 정보</span><span class="sxs-lookup"><span data-stu-id="304e0-104">About Scheduled Jobs Basics</span></span>

## <a name="short-description"></a><span data-ttu-id="304e0-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="304e0-105">Short description</span></span>

<span data-ttu-id="304e0-106">예약된 작업을 만들고 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-106">Explains how to create and manage scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="304e0-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-107">Long description</span></span>

<span data-ttu-id="304e0-108">이 문서에서는 예약 된 작업을 만들고 관리 하는 기본 작업을 수행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-108">This document shows how to perform basic tasks of creating and managing scheduled jobs.</span></span> <span data-ttu-id="304e0-109">고급 태스크에 대 한 자세한 내용은 [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="304e0-109">For information about more advanced tasks, see [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).</span></span>

<span data-ttu-id="304e0-110">**PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="304e0-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="how-to-create-a-scheduled-job"></a><span data-ttu-id="304e0-111">예약 된 작업을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-111">How to create a scheduled job</span></span>

<span data-ttu-id="304e0-112">예약 된 작업을 만들려면 cmdlet을 사용 `Register-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-112">To create a scheduled job, use the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="304e0-113">Cmdlet에는 작업에서 실행 되는 이름 및 명령 또는 스크립트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-113">The cmdlet requires a name and the commands or script that the job runs.</span></span> <span data-ttu-id="304e0-114">**Runnow** 매개 변수를 추가 하거나 작업 트리거를 만들고 작업을 만들 때 작업 옵션을 설정 하거나 기존 작업을 편집 하 여 작업을 즉시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-114">You can either run the job immediately by adding the **RunNow** parameter, or create a job trigger and set job options when you create the job, or edit an existing job.</span></span>

<span data-ttu-id="304e0-115">스크립트를 실행 하는 작업을 만들려면 **FilePath** 매개 변수를 사용 하 여 스크립트 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-115">To create a job that runs a script, use the **FilePath** parameter to specify the path to the script file.</span></span> <span data-ttu-id="304e0-116">명령을 실행 하는 작업을 만들려면 **ScriptBlock** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-116">To create a job that runs commands, use the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="304e0-117">`Register-ScheduledJob`Cmdlet은 명령을 실행 하는 **processjob** 을 만듭니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="304e0-117">The `Register-ScheduledJob` cmdlet creates the **ProcessJob** , which runs a `Get-Process` command.</span></span> <span data-ttu-id="304e0-118">이 예약 된 작업에는 기본 작업 옵션이 있으며 작업 트리거는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-118">This scheduled job has the default job options and no job trigger.</span></span>

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a><span data-ttu-id="304e0-119">작업 트리거를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-119">How to create a job trigger</span></span>

<span data-ttu-id="304e0-120">작업 트리거는 예약 된 작업을 자동으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-120">Job triggers start a scheduled job automatically.</span></span> <span data-ttu-id="304e0-121">작업 트리거는 일회성 또는 되풀이 일정 이거나 사용자가 로그온 하거나 Windows가 시작 되는 경우와 같은 이벤트 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-121">A job trigger can be one-time or recurring schedule or an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="304e0-122">각 작업에는 0 개, 1 개 또는 여러 개의 작업 트리거가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-122">Each job can have zero, one, or multiple job triggers.</span></span>

<span data-ttu-id="304e0-123">작업 트리거를 만들려면 cmdlet을 사용 `New-JobTrigger` 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-123">To create a job trigger, use the `New-JobTrigger` cmdlet.</span></span> <span data-ttu-id="304e0-124">다음 명령은 월요일과 목요일 오전 5:00에 작업을 시작 하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-124">The following command creates a job trigger that starts a job every Monday and Thursday at 5:00 AM.</span></span>
<span data-ttu-id="304e0-125">이 명령은 작업 트리거를 `$T` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-125">The command saves the job trigger in the `$T` variable.</span></span>

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

<span data-ttu-id="304e0-126">작업 트리거는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-126">Job triggers are optional.</span></span> <span data-ttu-id="304e0-127">**Runnow** 매개 변수를 명령에 추가 하거나 cmdlet을 사용 하 여 언제 든 지 예약 된 작업을 시작할 수 있습니다 `Register-ScheduledJob` `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="304e0-127">You can start a scheduled job at any time by adding the **RunNow** parameter to your `Register-ScheduledJob` command, or by using the `Start-Job` cmdlets.</span></span>

## <a name="how-to-add-a-job-trigger"></a><span data-ttu-id="304e0-128">작업 트리거를 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-128">How to add a job trigger</span></span>

<span data-ttu-id="304e0-129">예약 된 작업에 작업 트리거를 추가 하면 작업 트리거가 예약 된 작업에 대 한 예약 된 작업 XML 파일에 추가 되 고 예약 된 작업의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-129">When you add a job trigger to a scheduled job, the job trigger is added to the scheduled job XML file for the scheduled job and becomes part of the scheduled job.</span></span>

<span data-ttu-id="304e0-130">예약 된 작업을 만들 때 예약 된 작업에 작업 트리거를 추가 하거나 기존 작업을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-130">You can add a job trigger to a scheduled job when you create the scheduled job, or edit an existing job.</span></span> <span data-ttu-id="304e0-131">언제 든 지 예약 된 작업의 작업 트리거를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-131">You can change the job trigger of a scheduled job at any time.</span></span>

<span data-ttu-id="304e0-132">PowerShell은 작업 스케줄러에서 사용 하는 것과 동일한 작업 트리거를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-132">PowerShell uses some of the same job triggers that Task Scheduler uses.</span></span> <span data-ttu-id="304e0-133">작업 트리거에 대 한 자세한 내용은 [새-JobTrigger](xref:PSScheduledJob.New-JobTrigger) cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="304e0-133">For detailed information about job triggers, see the help topic for the [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) cmdlet.</span></span>

<span data-ttu-id="304e0-134">다음 예에서는 스 플랫를 사용 하 여 `$JobParms` cmdlet에 전달 되는 매개 변수 값을 만듭니다 `Register-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="304e0-134">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="304e0-135">자세한 내용은 [about_Splatting](../../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="304e0-135">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="304e0-136">는를 사용 하 여 `Register-ScheduledJob` `@JobParms` 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-136">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="304e0-137">**Trigger** 매개 변수를 사용 하 여 변수에서 작업 트리거를 지정 `$T` 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-137">It uses the **Trigger** parameter to specify the job trigger in the `$T` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="304e0-138">언제 든 지 기존 예약 된 작업에 작업 트리거를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-138">You can also add a job trigger to an existing scheduled job at any time.</span></span> <span data-ttu-id="304e0-139">`Add-JobTrigger`Cmdlet은 `$T` **processjob** 예약 된 작업에 변수의 작업 트리거를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-139">The `Add-JobTrigger` cmdlet adds the job trigger in the `$T` variable to the **ProcessJob** scheduled job.</span></span>

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

<span data-ttu-id="304e0-140">결과적으로 작업 트리거는 월요일과 목요일 오전 5:00 시에 자동으로 **Processjob** 을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-140">As a result, the job trigger starts the **ProcessJob** automatically every Monday and Thursday at 5:00 AM.</span></span>

## <a name="how-to-get-a-job-trigger"></a><span data-ttu-id="304e0-141">작업 트리거를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-141">How to get a job trigger</span></span>

<span data-ttu-id="304e0-142">예약 된 작업의 작업 트리거를 가져오려면 cmdlet을 사용 합니다 `Get-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="304e0-142">To get the job trigger of a scheduled job, use the `Get-JobTrigger` cmdlet.</span></span> <span data-ttu-id="304e0-143">**Name** , **ID** 및 **InputObject** 매개 변수를 사용 하 여 작업 트리거가 아닌 예약 된 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-143">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job trigger.</span></span>

<span data-ttu-id="304e0-144">`Get-JobTrigger`**Processjob** 의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-144">`Get-JobTrigger` gets the job trigger of the **ProcessJob**.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a><span data-ttu-id="304e0-145">작업 옵션을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-145">How to create job options</span></span>

<span data-ttu-id="304e0-146">작업 옵션은 작업을 시작 하 고 실행 하는 조건을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-146">Job options establish conditions for starting and running the job.</span></span> <span data-ttu-id="304e0-147">모든 작업에는 변경 하지 않는 한 기본 작업 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-147">Every job has the default job options unless you change them.</span></span> <span data-ttu-id="304e0-148">작업 옵션은 예약 된 시간에 작업이 실행 되는 것을 방지할 수 있으므로 작업 옵션을 이해 하 고 신중 하 게 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-148">Because job options can prevent a job from running at the scheduled time, it is important to understand the job options and use them carefully.</span></span>

<span data-ttu-id="304e0-149">PowerShell은 작업 스케줄러에서 사용 하는 것과 동일한 작업 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-149">PowerShell uses the same job options that Task Scheduler uses.</span></span> <span data-ttu-id="304e0-150">작업 옵션에 대 한 자세한 내용은 [set-scheduledjoboption](xref:PSScheduledJob.New-ScheduledJobOption)에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="304e0-150">For detailed information about the job options, see the help topic for [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

<span data-ttu-id="304e0-151">작업 옵션은 예약 된 작업 XML 파일에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-151">Job options are stored in the scheduled job XML file.</span></span> <span data-ttu-id="304e0-152">예약 된 작업을 만들 때 작업 옵션을 설정 하거나 언제 든 지 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-152">You can set job options when you create a scheduled job or change them at any time.</span></span>

<span data-ttu-id="304e0-153">`New-ScheduledJobOption`Cmdlet은 **WakeToRun** 예약 된 작업 옵션이 True로 설정 된 예약 된 작업 옵션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-153">The `New-ScheduledJobOption` cmdlet creates a scheduled job option in which the **WakeToRun** scheduled job option is set to True.</span></span> <span data-ttu-id="304e0-154">**WakeToRun** 옵션은 컴퓨터가 예약 된 시작 시간에 절전 모드 또는 최대 절전 모드에 있는 경우에도 예약 된 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-154">The **WakeToRun** option runs the scheduled job even if the computer is in the Sleep or Hibernate state at the scheduled start time.</span></span> <span data-ttu-id="304e0-155">이 명령은 작업 옵션을 `$O` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-155">The command saves the job options in the `$O` variable.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a><span data-ttu-id="304e0-156">작업 옵션을 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-156">How to get job options</span></span>

<span data-ttu-id="304e0-157">예약 된 작업의 작업 옵션을 가져오려면 cmdlet을 사용 합니다 `Get-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="304e0-157">To get the job options of a scheduled job, use the `Get-ScheduledJobOption` cmdlet.</span></span> <span data-ttu-id="304e0-158">**이름** , **ID** 및 **InputObject** 매개 변수를 사용 하 여 작업 옵션이 아닌 예약 된 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-158">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job options.</span></span>

<span data-ttu-id="304e0-159">`Get-ScheduledJobOption`**Processjob** 의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-159">`Get-ScheduledJobOption` gets the job options of the **ProcessJob**.</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

## <a name="how-to-change-job-options"></a><span data-ttu-id="304e0-160">작업 옵션을 변경 하는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-160">How to change job options</span></span>

<span data-ttu-id="304e0-161">예약 된 작업을 만들거나 기존 작업을 편집할 때 예약 된 작업의 작업 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-161">You can change the job options of a scheduled job when you create a scheduled job or edit an existing job.</span></span>

<span data-ttu-id="304e0-162">Splatted는 `$JobParms` cmdlet에 전달 되어 `Add-JobTrigger` 프로세스 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-162">The splatted `$JobParms` are passed to the `Add-JobTrigger` cmdlet to create the process job.</span></span> <span data-ttu-id="304e0-163">**Set-scheduledjoboption** 매개 변수를 사용 하 여 변수에서 작업 옵션을 지정 `$O` 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-163">It uses the **ScheduledJobOption** parameter to specify the job options in the `$O` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

<span data-ttu-id="304e0-164">언제 든 지 기존 예약 된 작업으로 작업 옵션을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-164">You can also change the job options to an existing scheduled job at any time.</span></span>
<span data-ttu-id="304e0-165">다음 명령은 cmdlet을 사용 하 여 `Set-ScheduledJobOption` **processjob** set-scheduledjob의 **WakeToRun** 옵션 값을 **True** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-165">The following command uses the `Set-ScheduledJobOption` cmdlet to change the value of the **WakeToRun** option of the **ProcessJob** scheduledJob to **True**.</span></span>

<span data-ttu-id="304e0-166">`Set`Cmdlet과 같은 **PSScheduledJob** 모듈의 cmdlet은 `Set-ScheduledJobOption` **Name** 또는 **ID** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-166">The `Set` cmdlets in the **PSScheduledJob** module, such as the `Set-ScheduledJobOption` cmdlet, don't have **Name** or **ID** parameters.</span></span> <span data-ttu-id="304e0-167">**InputObject** 매개 변수를 사용 하 여 예약 된 작업 옵션을 지정 하거나 cmdlet에서로 예약 된 작업을 파이프로 파이프 할 수 있습니다 `Get-ScheduledJobOption` `Set-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="304e0-167">You can use the **InputObject** parameter to specify the scheduled job options or pipe a scheduled job from `Get-ScheduledJobOption` cmdlet to `Set-ScheduledJobOption`.</span></span>

<span data-ttu-id="304e0-168">이 예에서는 cmdlet을 사용 하 여 `Get-ScheduledJob` ProcessJob을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-168">This example uses the `Get-ScheduledJob` cmdlet to get the ProcessJob.</span></span> <span data-ttu-id="304e0-169">Cmdlet을 사용 하 여 `Get-ScheduledJobOption` **processjob** 의 작업 옵션을 가져오고 cmdlet을 사용 하 여 `Set-ScheduledJobOption` processjob의 **WakeToRun** job 옵션을 True로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-169">It uses the `Get-ScheduledJobOption` cmdlet to get the job options in the **ProcessJob** and the `Set-ScheduledJobOption` cmdlet to change the **WakeToRun** job option in the ProcessJob to True.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a><span data-ttu-id="304e0-170">예약 된 작업 인스턴스를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="304e0-170">How to get scheduled job instances</span></span>

<span data-ttu-id="304e0-171">예약 된 작업이 시작 되 면 PowerShell은 표준 PowerShell 백그라운드 작업과 유사한 작업 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-171">When a scheduled job is started, PowerShell creates a job instance that is similar to a standard PowerShell background job.</span></span> <span data-ttu-id="304e0-172">작업 cmdlet (예: 및)을 사용 `Get-Job` `Stop-Job` 하 여 `Receive-Job` 작업 인스턴스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-172">You can use the job cmdlets, such as `Get-Job`, `Stop-Job` and `Receive-Job` to manage the job instances.</span></span>

> [!NOTE]
> <span data-ttu-id="304e0-173">예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-173">To use the job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="304e0-174">**PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-174">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="304e0-175">PowerShell 예약 된 작업 및 모든 활성 표준 작업의 모든 인스턴스를 가져오려면 cmdlet을 사용 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-175">To get all instances of PowerShell scheduled jobs, and all active standard jobs, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="304e0-176">`Import-Module`Cmdlet은 **PSScheduledJob** 모듈을 가져오고 `Get-Job` 로컬 컴퓨터의 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-176">The `Import-Module` cmdlet imports the **PSScheduledJob** module and `Get-Job` gets the jobs on the local computer.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job
```

<span data-ttu-id="304e0-177">`Get-Job` 로컬 컴퓨터에서 **Processjob** 의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-177">`Get-Job` gets instances of **ProcessJob** on the local computer.</span></span>

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

<span data-ttu-id="304e0-178">기본 표시에는 일반적으로 동일한 예약 된 작업의 인스턴스를 구분 하는 시작 시간이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-178">The default display does not show the start time, which typically distinguishes instances of the same scheduled job.</span></span>

<span data-ttu-id="304e0-179">`Get-Job`Cmdlet은 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-179">The `Get-Job` cmdlet sends objects down the pipeline.</span></span> <span data-ttu-id="304e0-180">`Format-Table`Cmdlet은 예약 된 작업의 **이름** , **ID** 및 **begintime** 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-180">The `Format-Table` cmdlet displays the **Name** , **ID** , and **BeginTime** properties of the scheduled job.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

## <a name="get-scheduled-job-results"></a><span data-ttu-id="304e0-181">예약 된 작업 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="304e0-181">Get scheduled job results</span></span>

<span data-ttu-id="304e0-182">예약 된 작업의 인스턴스 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="304e0-182">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="304e0-183">예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-183">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="304e0-184">**PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-184">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="304e0-185">이 예에서는 **processjob** 예약 된 작업 (ID = 51)의 최신 인스턴스의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-185">This examples gets the results of the newest instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

<span data-ttu-id="304e0-186">예약 된 작업의 결과는 디스크에 저장 되므로의 **Keep** 매개 변수는 `Receive-Job` 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-186">The results of scheduled jobs are saved on disk, so the **Keep** parameter of `Receive-Job` is not required.</span></span> <span data-ttu-id="304e0-187">그러나 **Keep** 매개 변수를 사용 하지 않으면 각 PowerShell 세션에서 예약 된 작업의 결과를 한 번만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-187">However, without the **Keep** parameter, you can get the results of a scheduled job only once in each PowerShell session.</span></span> <span data-ttu-id="304e0-188">새 PowerShell 세션을 시작 하려면 `PowerShell` 새 powershell 창을 입력 하거나 엽니다.</span><span class="sxs-lookup"><span data-stu-id="304e0-188">To start a new PowerShell session, type `PowerShell` or open a new PowerShell window.</span></span>

## <a name="see-also"></a><span data-ttu-id="304e0-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="304e0-189">See also</span></span>

[<span data-ttu-id="304e0-190">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="304e0-190">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="304e0-191">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="304e0-191">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="304e0-192">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="304e0-192">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="304e0-193">about_Splatting. md</span><span class="sxs-lookup"><span data-stu-id="304e0-193">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="304e0-194">[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet</span><span class="sxs-lookup"><span data-stu-id="304e0-194">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="304e0-195">작업 Scheduler</span><span class="sxs-lookup"><span data-stu-id="304e0-195">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
