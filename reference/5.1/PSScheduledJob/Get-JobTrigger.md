---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213441"
---
# <span data-ttu-id="3b1e0-103">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-103">Get-JobTrigger</span></span>

## <span data-ttu-id="3b1e0-104">개요</span><span class="sxs-lookup"><span data-stu-id="3b1e0-104">SYNOPSIS</span></span>
<span data-ttu-id="3b1e0-105">예약된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-105">Gets the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="3b1e0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3b1e0-106">SYNTAX</span></span>

### <span data-ttu-id="3b1e0-107">JobDefinition (기본값)</span><span class="sxs-lookup"><span data-stu-id="3b1e0-107">JobDefinition (Default)</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="3b1e0-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="3b1e0-108">JobDefinitionId</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="3b1e0-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="3b1e0-109">JobDefinitionName</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="3b1e0-110">설명</span><span class="sxs-lookup"><span data-stu-id="3b1e0-110">DESCRIPTION</span></span>
<span data-ttu-id="3b1e0-111">**Get-JobTrigger** cmdlet은 예약된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-111">The **Get-JobTrigger** cmdlet gets the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="3b1e0-112">이 명령을 사용하여 작업 트리거를 검사하거나 작업 트리거를 다른 cmdlet으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-112">You can use this command to examine the job triggers or to pipe the job triggers to other cmdlets.</span></span>

<span data-ttu-id="3b1e0-113">작업 트리거는 예약 된 작업을 시작 하기 위한 되풀이 일정 또는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-113">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="3b1e0-114">작업 트리거는 독립적으로 디스크에 저장되지 않고 예약된 작업의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-114">Job triggers are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="3b1e0-115">작업 트리거를 가져오려면 트리거가 시작하는 예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-115">To get a job trigger, specify the scheduled job that the trigger starts.</span></span>

<span data-ttu-id="3b1e0-116">**Get-JobTrigger** cmdlet의 매개 변수를 사용하여 예약된 작업을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-116">Use the parameters of the **Get-JobTrigger** cmdlet to identify the scheduled jobs.</span></span>
<span data-ttu-id="3b1e0-117">이름 또는 id 번호를 기준으로 예약 된 작업을 식별 하거나, Get-ScheduledJob cmdlet에서 반환 되 **는 개체 (** 예: cmdlet에서 반환 하는 개체)를 입력 하거나 파이프 하 여 **가져올** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-117">You can identify the scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-JobTrigger** .</span></span>

<span data-ttu-id="3b1e0-118">**JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-118">**Get-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="3b1e0-119">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="3b1e0-120">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="3b1e0-121">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3b1e0-122">예제</span><span class="sxs-lookup"><span data-stu-id="3b1e0-122">EXAMPLES</span></span>

### <span data-ttu-id="3b1e0-123">예제 1: 예약 된 작업 이름으로 작업 트리거 가져오기</span><span class="sxs-lookup"><span data-stu-id="3b1e0-123">Example 1: Get a job trigger by scheduled job name</span></span>

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

<span data-ttu-id="3b1e0-124">이 명령은 **Get JobTrigger** 의 *Name* 매개 변수를 사용 하 여 backupjob 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-124">The command uses the *Name* parameter of **Get-JobTrigger** to get the job triggers of the BackupJob scheduled job.</span></span>

### <span data-ttu-id="3b1e0-125">예제 2: ID로 작업 트리거 가져오기</span><span class="sxs-lookup"><span data-stu-id="3b1e0-125">Example 2: Get a job trigger by ID</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

<span data-ttu-id="3b1e0-126">이 예에서는 **Get JobTrigger** 의 *ID* 매개 변수를 사용 하 여 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-126">The example uses the *ID* parameter of **Get-JobTrigger** to get the job triggers of a scheduled job.</span></span>

### <span data-ttu-id="3b1e0-127">예 3: 작업을 파이프 하 여 작업 트리거 가져오기</span><span class="sxs-lookup"><span data-stu-id="3b1e0-127">Example 3: Get job triggers by piping a job</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

<span data-ttu-id="3b1e0-128">이 명령은 이름에 백업이 나 보관 된 모든 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-128">This command gets the job triggers of all jobs that have Backup or Archive in their names.</span></span>

### <span data-ttu-id="3b1e0-129">예 4: 원격 컴퓨터에서 작업의 작업 트리거 가져오기</span><span class="sxs-lookup"><span data-stu-id="3b1e0-129">Example 4: Get the job trigger of a job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

<span data-ttu-id="3b1e0-130">이 명령은 원격 컴퓨터에 있는 예약된 작업의 작업 트리거 2개 중 하나를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-130">This command gets one of the two job triggers of a scheduled job on a remote computer.</span></span>

<span data-ttu-id="3b1e0-131">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-131">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>
<span data-ttu-id="3b1e0-132">Get-ScheduledJob cmdlet을 사용 하 여 Backup 예약 된 작업을 가져옵니다 .이 작업은 **Get JobTrigger** cmdlet에 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-132">It uses the Get-ScheduledJob cmdlet to get the Backup scheduled job, which it pipes to the **Get-JobTrigger** cmdlet.</span></span>
<span data-ttu-id="3b1e0-133">*TriggerID* 매개 변수를 사용 하 여 두 번째 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-133">It uses the *TriggerID* parameter to get only the second trigger.</span></span>

### <span data-ttu-id="3b1e0-134">예 5: 모든 작업 트리거 가져오기</span><span class="sxs-lookup"><span data-stu-id="3b1e0-134">Example 5: Get all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

<span data-ttu-id="3b1e0-135">이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업의 모든 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-135">This command gets all job triggers of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="3b1e0-136">이 명령은 Get-ScheduledJob를 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져온 다음 각 예약 된 작업 (있는 경우)의 작업 트리거를 **가져오는 jobtrigger** 로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-136">The command uses the Get-ScheduledJob to get the scheduled jobs on the local computer and pipes them to **Get-JobTrigger** , which gets the job trigger of each scheduled job (if any).</span></span>

<span data-ttu-id="3b1e0-137">작업 트리거 표시에 예약 된 작업의 이름을 추가 하기 위해이 명령은 Format-Table cmdlet의 계산 된 속성 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-137">To add the name of the scheduled job to the job trigger display, the command uses the calculated property feature of the Format-Table cmdlet.</span></span>
<span data-ttu-id="3b1e0-138">이 명령은 기본적으로 표시 되는 작업 트리거 속성 외에 예약 된 작업의 이름을 표시 하는 새 Set-scheduledjob 속성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-138">In addition to the job trigger properties that are displayed by default, the command creates a new ScheduledJob property that displays the name of the scheduled job.</span></span>

### <span data-ttu-id="3b1e0-139">예 6: 예약 된 작업의 작업 트리거 속성 가져오기</span><span class="sxs-lookup"><span data-stu-id="3b1e0-139">Example 6: Get the job trigger property of a scheduled job</span></span>

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

<span data-ttu-id="3b1e0-140">예약된 작업의 작업 트리거는 작업의 JobTriggers 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-140">The job triggers of a scheduled job are stored in the JobTriggers property of the job.</span></span>
<span data-ttu-id="3b1e0-141">이 예에서는 **Get JobTrigger** cmdlet을 사용 하 여 작업 트리거를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-141">This example shows alternatives to using the **Get-JobTrigger** cmdlet to get job triggers.</span></span>
<span data-ttu-id="3b1e0-142">결과는 **Get-JobTrigger** cmdlet을 사용하는 것과 동일하며 교환해서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-142">The results are identical to using the **Get-JobTrigger** cmdlet and the techniques can be used interchangeably.</span></span>

### <span data-ttu-id="3b1e0-143">예 7: 작업 트리거 비교</span><span class="sxs-lookup"><span data-stu-id="3b1e0-143">Example 7: Compare job triggers</span></span>

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

<span data-ttu-id="3b1e0-144">이 예제에서는 두 예약된 작업의 작업 트리거를 비교하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-144">This example shows how to compare the job triggers of two scheduled jobs.</span></span>

## <span data-ttu-id="3b1e0-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3b1e0-145">PARAMETERS</span></span>

### <span data-ttu-id="3b1e0-146">-Id</span><span class="sxs-lookup"><span data-stu-id="3b1e0-146">-Id</span></span>
<span data-ttu-id="3b1e0-147">예약된 작업의 ID 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-147">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="3b1e0-148">**Get-JobTrigger** 는 지정한 예약된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-148">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>

<span data-ttu-id="3b1e0-149">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 id 번호를 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-149">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="3b1e0-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3b1e0-150">-InputObject</span></span>
<span data-ttu-id="3b1e0-151">예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-151">Specifies a scheduled job.</span></span>
<span data-ttu-id="3b1e0-152">**Set-scheduledjob** 개체가 포함 된 변수를 입력 하거나 **set-scheduledjob** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-152">Enter a variable that contains  **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="3b1e0-153">**Set-scheduledjob** 개체를 **가져오기-jobtrigger** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-153">You can also pipe **ScheduledJob** objects to **Get-JobTrigger** .</span></span>

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

### <span data-ttu-id="3b1e0-154">-Name</span><span class="sxs-lookup"><span data-stu-id="3b1e0-154">-Name</span></span>
<span data-ttu-id="3b1e0-155">예약된 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-155">Specifies the name of a scheduled job.</span></span>
<span data-ttu-id="3b1e0-156">**Get-JobTrigger** 는 지정한 예약된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-156">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>
<span data-ttu-id="3b1e0-157">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-157">Wildcards are supported.</span></span>

<span data-ttu-id="3b1e0-158">로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 이름을 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-158">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3b1e0-159">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="3b1e0-159">-TriggerId</span></span>
<span data-ttu-id="3b1e0-160">지정한 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-160">Gets the specified job triggers.</span></span>
<span data-ttu-id="3b1e0-161">예약된 작업의 하나 이상 작업 트리거에 대한 트리거 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="3b1e0-162">*Name* , *ID* 또는 *InputObject* 매개 변수로 지정된 예약된 작업에 여러 개의 작업 트리거가 있을 때 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-162">Use this parameter when the scheduled job that is specified by the *Name* , *ID* , or *InputObject* parameters has multiple job triggers.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3b1e0-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3b1e0-163">CommonParameters</span></span>
<span data-ttu-id="3b1e0-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3b1e0-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3b1e0-166">입력</span><span class="sxs-lookup"><span data-stu-id="3b1e0-166">INPUTS</span></span>

### <span data-ttu-id="3b1e0-167">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="3b1e0-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="3b1e0-168">Get-ScheduledJob에서 **가져오기-JobTrigger** 로 예약 된 작업을 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b1e0-168">You can pipe a scheduled job from Get-ScheduledJob to **Get-JobTrigger** .</span></span>

## <span data-ttu-id="3b1e0-169">출력</span><span class="sxs-lookup"><span data-stu-id="3b1e0-169">OUTPUTS</span></span>

### <span data-ttu-id="3b1e0-170">Set-scheduledjob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-170">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="3b1e0-171">참고</span><span class="sxs-lookup"><span data-stu-id="3b1e0-171">NOTES</span></span>

## <span data-ttu-id="3b1e0-172">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3b1e0-172">RELATED LINKS</span></span>

[<span data-ttu-id="3b1e0-173">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-173">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="3b1e0-174">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-174">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="3b1e0-175">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3b1e0-175">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="3b1e0-176">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-176">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="3b1e0-177">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3b1e0-177">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="3b1e0-178">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-178">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="3b1e0-179">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3b1e0-179">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="3b1e0-180">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3b1e0-180">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="3b1e0-181">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-181">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="3b1e0-182">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3b1e0-182">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="3b1e0-183">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3b1e0-183">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="3b1e0-184">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-184">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="3b1e0-185">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3b1e0-185">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="3b1e0-186">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3b1e0-186">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="3b1e0-187">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3b1e0-187">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="3b1e0-188">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3b1e0-188">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
