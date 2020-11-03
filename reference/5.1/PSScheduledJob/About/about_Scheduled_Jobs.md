---
description: 예약 된 작업에 대해 설명 하 고 PowerShell 및 작업 스케줄러에서 예약 된 작업을 사용 하 고 관리 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221938"
---
# <a name="about-scheduled-jobs"></a><span data-ttu-id="517ab-104">예약 된 작업 정보</span><span class="sxs-lookup"><span data-stu-id="517ab-104">About Scheduled Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="517ab-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="517ab-105">Short description</span></span>

<span data-ttu-id="517ab-106">예약 된 작업에 대해 설명 하 고 PowerShell 및 작업 스케줄러에서 예약 된 작업을 사용 하 고 관리 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-106">Describes scheduled jobs and explains how to use and manage scheduled jobs in PowerShell and in Task Scheduler.</span></span>

## <a name="long-description"></a><span data-ttu-id="517ab-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-107">Long description</span></span>

<span data-ttu-id="517ab-108">PowerShell 예약 된 작업은 PowerShell 백그라운드 작업 및 작업 스케줄러 작업의 유용한 하이브리드입니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-108">PowerShell scheduled jobs are a useful hybrid of PowerShell background jobs and Task Scheduler tasks.</span></span>

<span data-ttu-id="517ab-109">PowerShell 백그라운드 작업과 마찬가지로 예약 된 작업은 백그라운드에서 비동기적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-109">Like PowerShell background jobs, scheduled jobs run asynchronously in the background.</span></span> <span data-ttu-id="517ab-110">실행 된 예약 된 작업의 인스턴스는 작업 cmdlet (예:,, 및)을 사용 하 여 관리할 수 있습니다 `Start-Job` `Get-Job` `Stop-Job` `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="517ab-110">Instances of scheduled jobs that have run can be managed by using the job cmdlets, such as `Start-Job`, `Get-Job`, `Stop-Job`, and `Receive-Job`.</span></span>

<span data-ttu-id="517ab-111">작업 스케줄러 작업과 마찬가지로 예약 된 작업은 디스크에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-111">Like Task Scheduler tasks, scheduled jobs are saved to disk.</span></span> <span data-ttu-id="517ab-112">작업 스케줄러에서 작업을 보고 관리 하 고, 필요에 따라 사용/사용 하지 않도록 설정 하거나, 작업을 실행 하거나 템플릿으로 사용 하거나, 작업 시작을 위한 일회성 또는 되풀이 일정을 설정 하거나, 작업 시작 조건을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-112">You can view and manage the jobs in Task Scheduler, enable and disable them as needed, run them or use them as templates, establish a one-time or recurring schedules for starting the jobs, or set conditions under which the jobs start.</span></span>

<span data-ttu-id="517ab-113">또한 예약 된 작업 인스턴스의 결과는 쉽게 액세스할 수 있는 형식으로 디스크에 저장 되므로 실행 중인 작업 출력 로그를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-113">In addition, the results of scheduled job instances are saved to disk in an easily accessible format, providing a running log of job output.</span></span> <span data-ttu-id="517ab-114">예약 된 작업은 관리를 위해 사용자 지정 된 cmdlet 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-114">Scheduled jobs come with a customized set of cmdlets for managing them.</span></span> <span data-ttu-id="517ab-115">Cmdlet을 사용 하 여 예약 된 작업, 작업 트리거 및 작업 옵션을 만들고, 편집 하 고, 관리 하 고, 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-115">The cmdlets let you create, edit, manage, disable, and re-enable scheduled jobs, job triggers and job options.</span></span>

<span data-ttu-id="517ab-116">이러한 광범위 하 고 유연한 도구 집합은 많은 전문 PowerShell IT 솔루션의 필수 구성 요소로 예약 된 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-116">This comprehensive and flexible set of tools make scheduled jobs an essential component of many professional PowerShell IT solutions.</span></span>

<span data-ttu-id="517ab-117">예약 된 작업 cmdlet은 PowerShell과 함께 설치 되는 **PSScheduledJob** 모듈에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-117">The scheduled job cmdlets are included in the **PSScheduledJob** module that is installed with PowerShell.</span></span> <span data-ttu-id="517ab-118">이 모듈은 powershell 3.0에서 도입 되었으며 powershell 3.0 이상 버전에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-118">This module was introduced in PowerShell 3.0 and works in PowerShell 3.0 and later versions of PowerShell.</span></span> <span data-ttu-id="517ab-119">**PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="517ab-119">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

<span data-ttu-id="517ab-120">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="517ab-120">For more information about PowerShell background jobs, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

<span data-ttu-id="517ab-121">작업 스케줄러에 대 한 자세한 내용은 [작업 스케줄러](/windows/desktop/TaskSchd/task-scheduler-reference)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="517ab-121">For more information about Task Scheduler, see [Task Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference).</span></span>

> [!NOTE]
> <span data-ttu-id="517ab-122">작업 스케줄러에서 PowerShell 예약 된 작업을 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-122">You can view and manage PowerShell scheduled jobs in Task Scheduler.</span></span> <span data-ttu-id="517ab-123">Powershell 작업 및 예약 된 작업 cmdlet은 PowerShell에서 만든 예약 된 작업에 대해서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-123">The PowerShell jobs and scheduled job cmdlets work only on scheduled jobs that are created in PowerShell.</span></span>

## <a name="quick-start"></a><span data-ttu-id="517ab-124">빠른 시작</span><span class="sxs-lookup"><span data-stu-id="517ab-124">Quick start</span></span>

<span data-ttu-id="517ab-125">이 예에서는 매일 오전 3:00에 시작 하 고 cmdlet을 실행 하는 예약 된 작업을 만듭니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="517ab-125">This example creates a scheduled job that starts every day at 3:00 AM and runs the `Get-Process` cmdlet.</span></span> <span data-ttu-id="517ab-126">컴퓨터가 배터리로 실행 되는 경우에도 작업이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-126">The job starts even if the computer is running on batteries.</span></span>

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

<span data-ttu-id="517ab-127">`Get-ScheduledJob`Cmdlet은 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-127">The `Get-ScheduledJob` cmdlet gets the scheduled jobs on the local computer.</span></span>

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

<span data-ttu-id="517ab-128">`Get-JobTrigger`**processjob** 의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-128">`Get-JobTrigger` gets the job triggers of **ProcessJob**.</span></span> <span data-ttu-id="517ab-129">트리거가 예약 된 작업에 저장 되기 때문에 입력 매개 변수는 트리거가 아니라 예약 된 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-129">The input parameters specify the scheduled job, not the trigger, because triggers are saved in a scheduled job.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

<span data-ttu-id="517ab-130">이 예에서는 cmdlet의 **ContinueIfGoingOnBattery** 매개 변수를 사용 하 여 `Set-ScheduledJob` **processjob** 의 **StopIfGoingOnBatteries** 속성을 **False** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-130">This example uses the **ContinueIfGoingOnBattery** parameter of the `Set-ScheduledJob` cmdlet to change the **StopIfGoingOnBatteries** property of **ProcessJob** to **False**.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="517ab-131">`Get-ScheduledJob`Cmdlet은 **processjob** 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-131">The `Get-ScheduledJob` cmdlet gets the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

<span data-ttu-id="517ab-132">`Get-Job`Cmdlet은 지금까지 실행 된 **processjob** 예약 된 작업의 모든 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-132">The `Get-Job` cmdlet gets all instances of the **ProcessJob** scheduled job that have run thus far.</span></span> <span data-ttu-id="517ab-133">`Get-Job`Cmdlet은 **PSScheduledJob** 모듈을 현재 세션으로 가져올 때만 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-133">The `Get-Job` cmdlet gets scheduled jobs only when the **PSScheduledJob** module is imported into the current session.</span></span>

> [!TIP]
> <span data-ttu-id="517ab-134">예약 된 작업 cmdlet을 사용 하 여 예약 된 작업을 관리 하지만 작업 cmdlet을 사용 하 여 예약 된 작업의 인스턴스를 관리 하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-134">Notice that you use the scheduled job cmdlets to manage scheduled jobs, but you use the job cmdlets to manage instances of scheduled jobs.</span></span>

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

<span data-ttu-id="517ab-135">`Receive-Job`Cmdlet은 **processjob** 예약 된 작업의 가장 최근 인스턴스 (ID = 51)의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-135">The `Receive-Job` cmdlet gets the results of the most recent instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Receive-Job -ID 51
```

<span data-ttu-id="517ab-136">`Receive-Job`명령이 **Keep** 매개 변수를 포함 하지 않은 경우에도 삭제 하거나 최대 결과 수를 초과할 때까지 작업 결과가 디스크에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-136">Even though the `Receive-Job` command did not include the **Keep** parameter, the results of the job are saved on disk until you delete them or the maximum number of results are exceeded.</span></span>

<span data-ttu-id="517ab-137">작업 결과는이 세션에서 더 이상 사용할 수 없지만, 새 세션을 시작 하거나 새 PowerShell 창을 열 경우 작업 결과를 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-137">The job results are no longer available in this session, but if you start a new session or open a new PowerShell window, the results of the job are available again.</span></span>

<span data-ttu-id="517ab-138">다음 명령은 cmdlet의 **Definitionname** 매개 변수를 사용 하 여 `Start-Job` **processjob** 예약 된 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-138">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the **ProcessJob** scheduled job.</span></span>

<span data-ttu-id="517ab-139">Cmdlet을 사용 하 여 시작 하는 작업 `Start-Job` 은 예약 된 작업의 인스턴스가 아닌 표준 PowerShell 백그라운드 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-139">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="517ab-140">모든 백그라운드 작업과 마찬가지로, 이러한 작업은 즉시 시작 되 고 작업 옵션이 나 작업 트리거의 영향을 받지 않으며, 해당 출력은 예약 된 작업 디렉터리의 출력 디렉터리에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-140">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers, and their output is not saved in the output directory of the scheduled job directory.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="517ab-141">`Unregister-ScheduledJob`Cmdlet은 **processjob** 예약 된 작업과 해당 작업 인스턴스의 모든 저장 된 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-141">The `Unregister-ScheduledJob` cmdlet deletes the **ProcessJob** scheduled job and all saved results of its job instances.</span></span>

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a><span data-ttu-id="517ab-142">예약 된 작업 개념</span><span class="sxs-lookup"><span data-stu-id="517ab-142">Scheduled jobs concepts</span></span>

<span data-ttu-id="517ab-143">예약 된 작업은 명령 또는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-143">A scheduled job runs commands or a script.</span></span> <span data-ttu-id="517ab-144">예약 된 작업에는 작업을 시작 하는 작업 트리거와 작업 실행을 위한 조건을 설정 하는 작업 옵션이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-144">A scheduled job can include job triggers that start the job and job options that set conditions for running the job.</span></span>

<span data-ttu-id="517ab-145">작업 트리거는 예약 된 작업을 자동으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-145">A job trigger starts a scheduled job automatically.</span></span> <span data-ttu-id="517ab-146">작업 트리거는 일회성 또는 되풀이 일정을 포함 하거나 사용자가 로그온 하거나 Windows가 시작 되는 경우와 같은 이벤트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-146">A job trigger can include a one-time or recurring schedule or specify an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="517ab-147">예약 된 작업에는 하나 이상의 작업 트리거가 있을 수 있으며, 작업 트리거를 만들고, 추가 하 고, 활성화 하 고, 사용 하지 않도록 설정 하 고, 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-147">A scheduled job can have one or more job triggers, and you can create, add, enable, disable, and get job triggers.</span></span>

<span data-ttu-id="517ab-148">작업 트리거는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-148">Job triggers are optional.</span></span> <span data-ttu-id="517ab-149">`Start-Job cmdlet`를 사용 하거나 명령에 **runnow** 매개 변수를 추가 하 여 예약 된 작업을 즉시 시작할 수 있습니다 `Register-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="517ab-149">You can start scheduled jobs immediately by using the `Start-Job cmdlet`, or by adding the **RunNow** parameter to your `Register-ScheduledJob` command.</span></span>

<span data-ttu-id="517ab-150">작업 옵션은 예약 된 작업을 실행 하는 조건을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-150">Job options set the conditions for running a scheduled job.</span></span> <span data-ttu-id="517ab-151">모든 예약 된 작업에는 하나의 작업 옵션 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-151">Every scheduled job has one job options object.</span></span> <span data-ttu-id="517ab-152">작업 옵션 개체를 만들고 편집 하 여 하나 이상의 예약 된 작업에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-152">You can create and edit job options objects and add them to one or more scheduled jobs.</span></span>

<span data-ttu-id="517ab-153">예약 된 작업이 시작 될 때마다 작업 인스턴스가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-153">Each time a scheduled job starts, a job instance is created.</span></span> <span data-ttu-id="517ab-154">PowerShell 작업 cmdlet을 사용 하 여 작업 인스턴스를 보고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-154">Use the PowerShell job cmdlets to view and manage the job instance.</span></span>

<span data-ttu-id="517ab-155">예약 된 작업은 디스크에 저장 되 고 대신 cmdlet 동사를 사용 `Register` `New` 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-155">Scheduled jobs are saved to disk and use the cmdlet verb, `Register`, instead of `New`.</span></span> <span data-ttu-id="517ab-156">XML 파일은 로컬 컴퓨터의 디렉터리에 있습니다 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .</span><span class="sxs-lookup"><span data-stu-id="517ab-156">The XML files are located on the local computer in the directory `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

<span data-ttu-id="517ab-157">PowerShell은 예약 된 각 작업에 대 한 디렉터리를 만들고 작업 명령, 작업 트리거, 작업 옵션 및 작업 결과를 예약 된 작업 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-157">PowerShell creates a directory for each scheduled job and saves the job commands, job triggers, job options and job results in the scheduled job directory.</span></span> <span data-ttu-id="517ab-158">작업 트리거 및 작업 옵션은 독립적으로 디스크에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-158">Job triggers and job options aren't saved to disk independently.</span></span>
<span data-ttu-id="517ab-159">이러한 작업은 연결 된 각 예약 된 작업의 예약 된 작업 XML에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-159">They are saved in the scheduled job XML of each scheduled job with which they are associated.</span></span>

<span data-ttu-id="517ab-160">예약 된 작업, 작업 트리거 및 작업 옵션은 PowerShell에서 개체로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-160">Scheduled jobs, job triggers, and job options appear in PowerShell as objects.</span></span>
<span data-ttu-id="517ab-161">개체는 interlinked 이며 명령 및 스크립트에서 쉽게 검색 하 고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-161">The objects are interlinked, which makes them easy to discover and use in commands and scripts.</span></span>

<span data-ttu-id="517ab-162">예약 된 작업은 **ScheduledJobDefinition** 개체로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-162">Scheduled jobs appear as **ScheduledJobDefinition** objects.</span></span> <span data-ttu-id="517ab-163">**ScheduledJobDefinition** 개체에는 예약 된 작업의 작업 트리거 및 작업 옵션을 포함 하는 **options** 속성이 포함 된 **jobtriggers** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-163">The **ScheduledJobDefinition** object has a **JobTriggers** property that contains the job triggers of the scheduled job and an **Options** property that contains the job options.</span></span> <span data-ttu-id="517ab-164">작업 트리거 및 작업 옵션을 나타내는 **ScheduledJobTriggers** 및 **ScheduledJobOptions** 개체는 각각 연결 된 예약 된 작업을 포함 하는 **JobDefinition** 속성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-164">The **ScheduledJobTriggers** and **ScheduledJobOptions** objects that represent job triggers and job options, respectively, each have a **JobDefinition** property that contains the scheduled job with which they are associated.</span></span> <span data-ttu-id="517ab-165">이 재귀 연결을 사용 하면 예약 된 작업의 트리거와 옵션을 쉽게 찾고, 작업 트리거 또는 작업 옵션이 연결 된 예약 된 작업을 찾고 스크립팅 하 고 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="517ab-165">This recursive interconnection makes it easy to find the triggers and options of a scheduled job and to find, script, and display the scheduled job to which any job trigger or job option is associated.</span></span>

## <a name="see-also"></a><span data-ttu-id="517ab-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="517ab-166">See also</span></span>

[<span data-ttu-id="517ab-167">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="517ab-167">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="517ab-168">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="517ab-168">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="517ab-169">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="517ab-169">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

<span data-ttu-id="517ab-170">[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet</span><span class="sxs-lookup"><span data-stu-id="517ab-170">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="517ab-171">작업 Scheduler</span><span class="sxs-lookup"><span data-stu-id="517ab-171">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
