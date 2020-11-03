---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213497"
---
# <span data-ttu-id="52544-103">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-103">Add-JobTrigger</span></span>

## <span data-ttu-id="52544-104">개요</span><span class="sxs-lookup"><span data-stu-id="52544-104">SYNOPSIS</span></span>
<span data-ttu-id="52544-105">예약된 작업에 작업 트리거를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-105">Adds job triggers to scheduled jobs.</span></span>

## <span data-ttu-id="52544-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52544-106">SYNTAX</span></span>

### <span data-ttu-id="52544-107">JobDefinition (기본값)</span><span class="sxs-lookup"><span data-stu-id="52544-107">JobDefinition (Default)</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### <span data-ttu-id="52544-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="52544-108">JobDefinitionId</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="52544-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="52544-109">JobDefinitionName</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="52544-110">설명</span><span class="sxs-lookup"><span data-stu-id="52544-110">DESCRIPTION</span></span>
<span data-ttu-id="52544-111">**Add-JobTrigger** cmdlet은 예약된 작업에 작업 트리거를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-111">The **Add-JobTrigger** cmdlet adds job triggers to scheduled jobs.</span></span>
<span data-ttu-id="52544-112">이 cmdlet을 사용하여 여러 개의 예약된 작업에 여러 트리거를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52544-112">You can use it to add multiple triggers to multiple scheduled jobs.</span></span>

<span data-ttu-id="52544-113">작업 트리거는 일회성 또는 되풀이 일정에 따라 또는 이벤트가 발생 하는 경우 예약 된 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-113">A job trigger starts a scheduled job on a one-time or recurring schedule or when an event occurs.</span></span>

<span data-ttu-id="52544-114">추가 **jobtrigger** 의 *trigger* 매개 변수를 사용 하 여 추가할 작업 트리거를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52544-114">Use the *Trigger* parameter of **Add-JobTrigger** to identify the job triggers to add.</span></span>
<span data-ttu-id="52544-115">**추가 JobTrigger** 의 *Name* , *ID* 또는 *InputObject* 매개 변수를 사용 하 여 트리거가 추가 되는 예약 된 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-115">Use the *Name* , *ID* , or *InputObject* parameters of **Add-JobTrigger** to identify the scheduled job to which the triggers are added.</span></span>

<span data-ttu-id="52544-116">*Trigger* 매개 변수 값에 대 한 작업 트리거를 만들려면 New-JobTrigger cmdlet을 사용 하거나 해시 테이블을 사용 하 여 작업 트리거를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-116">To create job triggers for the value of the *Trigger* parameter, use the New-JobTrigger cmdlet or use a hash table to specify the job trigger.</span></span>

<span data-ttu-id="52544-117">**추가 JobTrigger** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="52544-117">**Add-JobTrigger** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="52544-118">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52544-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="52544-119">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52544-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="52544-120">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="52544-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="52544-121">예제</span><span class="sxs-lookup"><span data-stu-id="52544-121">EXAMPLES</span></span>

### <span data-ttu-id="52544-122">예제 1: 예약 된 작업에 작업 트리거 추가</span><span class="sxs-lookup"><span data-stu-id="52544-122">Example 1: Add a job trigger to a scheduled job</span></span>

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

<span data-ttu-id="52544-123">이 명령은 TestJob 예약된 작업에 Daily 작업 트리거를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-123">These commands add the Daily job trigger to the TestJob scheduled job.</span></span>

<span data-ttu-id="52544-124">첫 번째 명령은 New-JobTrigger cmdlet을 사용 하 여 매일 오전 3:00에 예약 된 작업을 시작 하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52544-124">The first command uses the New-JobTrigger cmdlet to create a job trigger that starts a scheduled job every day at 3:00 a.m.</span></span>
<span data-ttu-id="52544-125">이 명령은 $Daily 변수에 작업 트리거를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-125">The command saves the job trigger in the $Daily variable.</span></span>

<span data-ttu-id="52544-126">두 번째 명령은 **Add-JobTrigger** cmdlet을 사용하여 $Startup 변수의 작업 트리거를 TestJob 예약된 작업에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-126">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in the $Startup variable to the TestJob scheduled job.</span></span>

### <span data-ttu-id="52544-127">예제 2: 몇 개의 예약 된 작업에 작업 트리거 추가</span><span class="sxs-lookup"><span data-stu-id="52544-127">Example 2: Add a job trigger to several scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

<span data-ttu-id="52544-128">이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업에 AtStartup 작업 트리거를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-128">This command adds an AtStartup job trigger to all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="52544-129">Get-ScheduledJob를 사용 하 여 컴퓨터에 있는 모든 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52544-129">It uses the Get-ScheduledJob to get all of the scheduled jobs on the computer.</span></span>
<span data-ttu-id="52544-130">파이프라인 연산자(|)를 사용하여 작업을 **Add-JobTrigger** cmdlet으로 보내면 이 cmdlet이 각 예약된 작업에 작업 트리거를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-130">It uses a pipeline operator (|) to send the jobs to the **Add-JobTrigger** cmdlet, which adds the job trigger to each of the scheduled jobs.</span></span>
<span data-ttu-id="52544-131">*Trigger* 매개 변수 값은 atstartup 작업 트리거를 만드는 New-JobTrigger 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="52544-131">The value of the *Trigger* parameter is a New-JobTrigger command that creates the AtStartup job trigger.</span></span>

### <span data-ttu-id="52544-132">예제 3: 작업 트리거 복사</span><span class="sxs-lookup"><span data-stu-id="52544-132">Example 3: Copy a job trigger</span></span>

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

<span data-ttu-id="52544-133">이 명령은 BackupArchives 예약된 작업에서 작업 트리거를 복사하여 TestBackup 및 BackupLogs 예약된 작업에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-133">These commands copy the job trigger from the BackupArchives scheduled job and add it to the TestBackup and BackupLogs scheduled jobs.</span></span>

<span data-ttu-id="52544-134">첫 번째 명령은 Get-JobTrigger cmdlet을 사용 하 여 명령은 backuparchives 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52544-134">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the BackupArchives scheduled job.</span></span>
<span data-ttu-id="52544-135">트리거를 $t 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-135">The command saves the trigger in the $t variable.</span></span>

<span data-ttu-id="52544-136">두 번째 명령은 **Add-JobTrigger** cmdlet을 사용하여 $t 변수의 작업 트리거를 TestBackup 및 BackupLogs 예약된 작업에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-136">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in $t to the TestBackup and BackupLogs scheduled jobs.</span></span>

## <span data-ttu-id="52544-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="52544-137">PARAMETERS</span></span>

### <span data-ttu-id="52544-138">-Id</span><span class="sxs-lookup"><span data-stu-id="52544-138">-Id</span></span>
<span data-ttu-id="52544-139">예약된 작업의 ID 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-139">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="52544-140">**Add-JobTrigger** 는 지정한 예약된 작업에 작업 트리거를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-140">**Add-JobTrigger** adds the job trigger to the specified scheduled jobs.</span></span>

<span data-ttu-id="52544-141">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 id 번호를 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-141">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="52544-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="52544-142">-InputObject</span></span>
<span data-ttu-id="52544-143">예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-143">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="52544-144">**Set-scheduledjob** 개체가 포함 된 변수를 입력 하거나 **set-scheduledjob** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-144">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="52544-145">**Set-scheduledjob** 개체를 **추가 jobtrigger** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52544-145">You can also pipe **ScheduledJob** objects to **Add-JobTrigger** .</span></span>

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

### <span data-ttu-id="52544-146">-Name</span><span class="sxs-lookup"><span data-stu-id="52544-146">-Name</span></span>
<span data-ttu-id="52544-147">예약된 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-147">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="52544-148">**Add-JobTrigger** 는 지정한 예약된 작업에 작업 트리거를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-148">**Add-JobTrigger** adds the job triggers to the specified scheduled jobs.</span></span>
<span data-ttu-id="52544-149">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="52544-149">Wildcards are supported.</span></span>

<span data-ttu-id="52544-150">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 이름을 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-150">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="52544-151">-트리거</span><span class="sxs-lookup"><span data-stu-id="52544-151">-Trigger</span></span>
<span data-ttu-id="52544-152">추가할 작업 트리거를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-152">Specifies the job triggers to add.</span></span>
<span data-ttu-id="52544-153">**ScheduledJobTrigger** 개체가 포함 된 작업 트리거 또는 변수를 지정 하는 해시 테이블을 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="52544-153">Enter a hash table that specifies job triggers or a variable that contains **ScheduledJobTrigger** objects, or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="52544-154">**ScheduledJobTrigger** 개체를 **추가 jobtrigger** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52544-154">You can also pipe **ScheduledJobTrigger** objects to **Add-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="52544-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52544-155">CommonParameters</span></span>
<span data-ttu-id="52544-156">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52544-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52544-157">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52544-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52544-158">입력</span><span class="sxs-lookup"><span data-stu-id="52544-158">INPUTS</span></span>

### <span data-ttu-id="52544-159">Set-scheduledjob. ScheduledJobTrigger, Set-scheduledjob. ScheduledJobDefinition.</span><span class="sxs-lookup"><span data-stu-id="52544-159">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger, Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="52544-160">작업 트리거 또는 예약된 작업을 **Add-JobTrigger** 로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52544-160">You can pipe job triggers or scheduled jobs to **Add-JobTrigger** .</span></span>

## <span data-ttu-id="52544-161">출력</span><span class="sxs-lookup"><span data-stu-id="52544-161">OUTPUTS</span></span>

### <span data-ttu-id="52544-162">없음</span><span class="sxs-lookup"><span data-stu-id="52544-162">None</span></span>
<span data-ttu-id="52544-163">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52544-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="52544-164">참고</span><span class="sxs-lookup"><span data-stu-id="52544-164">NOTES</span></span>

## <span data-ttu-id="52544-165">관련 링크</span><span class="sxs-lookup"><span data-stu-id="52544-165">RELATED LINKS</span></span>

[<span data-ttu-id="52544-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="52544-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="52544-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="52544-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="52544-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="52544-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="52544-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="52544-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="52544-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="52544-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="52544-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="52544-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="52544-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="52544-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="52544-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="52544-176">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="52544-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="52544-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="52544-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="52544-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="52544-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="52544-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="52544-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="52544-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="52544-181">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="52544-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
