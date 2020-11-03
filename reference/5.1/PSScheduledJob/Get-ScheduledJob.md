---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213434"
---
# <span data-ttu-id="bf817-103">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bf817-103">Get-ScheduledJob</span></span>

## <span data-ttu-id="bf817-104">개요</span><span class="sxs-lookup"><span data-stu-id="bf817-104">SYNOPSIS</span></span>
<span data-ttu-id="bf817-105">로컬 컴퓨터에 있는 예약된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-105">Gets scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="bf817-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf817-106">SYNTAX</span></span>

### <span data-ttu-id="bf817-107">인 (기본값)</span><span class="sxs-lookup"><span data-stu-id="bf817-107">DefinitionId (Default)</span></span>

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="bf817-108">Build.definitionname</span><span class="sxs-lookup"><span data-stu-id="bf817-108">DefinitionName</span></span>

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="bf817-109">설명</span><span class="sxs-lookup"><span data-stu-id="bf817-109">DESCRIPTION</span></span>
<span data-ttu-id="bf817-110">**Get-ScheduledJob** cmdlet은 로컬 컴퓨터에 있는 예약된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-110">The **Get-ScheduledJob** cmdlet gets scheduled jobs on the local computer.</span></span>
<span data-ttu-id="bf817-111">**Set-scheduledjob** 는 Register-ScheduledJob cmdlet을 사용 하 여 현재 사용자가 만든 예약 된 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-111">**Get-ScheduledJob** gets only scheduled jobs that are created by the current user using the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="bf817-112">**Register-ScheduledJob** cmdlet을 사용하여 만든 작업이 작업 Scheduler에 표시되어도 **Get-ScheduledJob** 은 예약된 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-112">Although jobs that are created by using the **Register-ScheduledJob** cmdlet appear in Task Scheduler, **Get-ScheduledJob** gets only scheduled jobs.</span></span>
<span data-ttu-id="bf817-113">작업 스케줄러에서 만들어진 예약된 작업은 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-113">It does not get scheduled tasks created in Task Scheduler.</span></span>

<span data-ttu-id="bf817-114">매개 변수가 없을 경우 **Get-ScheduledJob** 은 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-114">Without parameters, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="bf817-115">**Get-ScheduledJob** 의 매개 변수를 사용하여 ID 또는 이름으로 예약된 작업을 가져온 다음 검사하거나 다른 cmdlet으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-115">You can use the parameters of **Get-ScheduledJob** to get scheduled jobs by ID or name and examine them or pipe them to other cmdlets.</span></span>

<span data-ttu-id="bf817-116">**Set-scheduledjob** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-116">**Get-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="bf817-117">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf817-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="bf817-118">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf817-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="bf817-119">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="bf817-120">예제</span><span class="sxs-lookup"><span data-stu-id="bf817-120">EXAMPLES</span></span>

### <span data-ttu-id="bf817-121">예제 1: 모든 예약 된 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="bf817-121">Example 1: Get all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob
```

<span data-ttu-id="bf817-122">이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-122">This command gets all scheduled jobs on the local computer.</span></span>

### <span data-ttu-id="bf817-123">예 2: 이름으로 예약 된 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="bf817-123">Example 2: Get scheduled jobs by name</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

<span data-ttu-id="bf817-124">이 명령은 백업 또는 보관을 포함 하는 이름을 가진 컴퓨터의 모든 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-124">This command gets all scheduled jobs on the computer that have names that include Backup or Archive.</span></span>
<span data-ttu-id="bf817-125">이 명령 형식을 사용하여 특정 작업을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-125">This command format lets you search for particular jobs.</span></span>

### <span data-ttu-id="bf817-126">예 3: 원격 컴퓨터에서 예약 된 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="bf817-126">Example 3: Get scheduled jobs on remote computers</span></span>

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

<span data-ttu-id="bf817-127">이 명령은 컴퓨터에서 Servers.txt 파일에 나열된 모든 예약된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-127">This command gets all scheduled jobs on the computers that are listed in the Servers.txt file.</span></span>
<span data-ttu-id="bf817-128">이 명령은 Invoke-Command cmdlet을 사용 하 여 각 컴퓨터에서 **ScheduleJob** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-128">The command uses the Invoke-Command cmdlet to run a **Get-ScheduleJob** command on each computer.</span></span>

### <span data-ttu-id="bf817-129">예제 4: 예약 된 작업을 다른 cmdlet으로 파이프</span><span class="sxs-lookup"><span data-stu-id="bf817-129">Example 4: Pipe scheduled jobs to other cmdlets</span></span>

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

<span data-ttu-id="bf817-130">이 명령은 DailyBackup 및 WeeklyBackup 예약된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-130">This command gets the job triggers of the DailyBackup and WeeklyBackup scheduled jobs.</span></span>
<span data-ttu-id="bf817-131">**Set-scheduledjob** cmdlet을 사용 하 여 예약 된 작업을 가져오고 Get-JobTrigger cmdlet을 사용 하 여 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-131">It uses the **Get-ScheduledJob** cmdlet to get the scheduled jobs and the Get-JobTrigger cmdlet to get the job triggers of the scheduled jobs.</span></span>

## <span data-ttu-id="bf817-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf817-132">PARAMETERS</span></span>

### <span data-ttu-id="bf817-133">-Id</span><span class="sxs-lookup"><span data-stu-id="bf817-133">-Id</span></span>
<span data-ttu-id="bf817-134">지정한 ID를 가진 예약된 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-134">Gets only the scheduled jobs with the specified identification number (ID).</span></span>
<span data-ttu-id="bf817-135">컴퓨터에 있는 예약된 작업의 ID 번호(ID)를 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-135">Enter one or more IDs of scheduled jobs on the computer.</span></span>
<span data-ttu-id="bf817-136">기본적으로 **Get-ScheduledJob** 은 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-136">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf817-137">-Name</span><span class="sxs-lookup"><span data-stu-id="bf817-137">-Name</span></span>
<span data-ttu-id="bf817-138">지정한 이름을 가진 예약된 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-138">Gets only the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="bf817-139">컴퓨터에 있는 예약된 작업의 이름을 하나 이상 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-139">Enter one or more names of scheduled jobs on the computer.</span></span>
<span data-ttu-id="bf817-140">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-140">Wildcards are supported.</span></span>
<span data-ttu-id="bf817-141">기본적으로 **Get-ScheduledJob** 은 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-141">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf817-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf817-142">CommonParameters</span></span>
<span data-ttu-id="bf817-143">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bf817-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf817-144">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf817-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf817-145">입력</span><span class="sxs-lookup"><span data-stu-id="bf817-145">INPUTS</span></span>

### <span data-ttu-id="bf817-146">없음</span><span class="sxs-lookup"><span data-stu-id="bf817-146">None</span></span>
<span data-ttu-id="bf817-147">**Get-ScheduledJob** 에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-147">You cannot pipe input to **Get-ScheduledJob** .</span></span>

## <span data-ttu-id="bf817-148">출력</span><span class="sxs-lookup"><span data-stu-id="bf817-148">OUTPUTS</span></span>

### <span data-ttu-id="bf817-149">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="bf817-149">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="bf817-150">참고</span><span class="sxs-lookup"><span data-stu-id="bf817-150">NOTES</span></span>

* <span data-ttu-id="bf817-151">각 예약된 작업은 로컬 컴퓨터에 있는 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 디렉터리의 하위 디렉터리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-151">Each scheduled job is saved in a subdirectory of the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the local computer.</span></span> <span data-ttu-id="bf817-152">하위 디렉터리는 예약된 작업에 따라 이름이 지정되며 예약된 작업에 대한 XML 파일과 실행 기록 레코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-152">The subdirectory is named for the scheduled job and contains the XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="bf817-153">예약된 작업에 대한 자세한 내용은 about_Scheduled_Jobs_Advanced를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf817-153">For more information about scheduled jobs on disk, see about_Scheduled_Jobs_Advanced.</span></span>
* <span data-ttu-id="bf817-154">Windows PowerShell에서 만든 예약된 작업은 작업 스케줄러의 Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs 폴더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-154">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs folder.</span></span> <span data-ttu-id="bf817-155">작업 스케줄러를 사용하여 예약된 작업을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-155">You can use Task Scheduler to view and edit the scheduled job.</span></span>
* <span data-ttu-id="bf817-156">작업 스케줄러, SchTasks.exe 명령줄 도구 및 작업 스케줄러 cmdlet을 사용하여 예약된 작업 cmdlet으로 만든 예약된 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-156">You can use Task Scheduler, the SchTasks.exe command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="bf817-157">그러나 예약된 작업 cmdlet을 사용하여 작업 스케줄러에서 만든 작업을 관리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf817-157">However, you cannot use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

## <span data-ttu-id="bf817-158">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bf817-158">RELATED LINKS</span></span>

[<span data-ttu-id="bf817-159">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bf817-159">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="bf817-160">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bf817-160">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="bf817-161">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bf817-161">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="bf817-162">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bf817-162">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="bf817-163">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bf817-163">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="bf817-164">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bf817-164">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="bf817-165">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bf817-165">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="bf817-166">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="bf817-166">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="bf817-167">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bf817-167">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="bf817-168">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="bf817-168">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="bf817-169">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bf817-169">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="bf817-170">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bf817-170">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="bf817-171">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="bf817-171">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="bf817-172">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bf817-172">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="bf817-173">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="bf817-173">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="bf817-174">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="bf817-174">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
