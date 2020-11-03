---
description: 예약된 작업의 기본이 되는 파일 구조를 비롯하여 예약된 고급 작업 항목에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221937"
---
# <a name="about-scheduled-jobs-advanced"></a><span data-ttu-id="f5291-104">예약 된 작업에 대 한 고급 정보</span><span class="sxs-lookup"><span data-stu-id="f5291-104">About Scheduled Jobs Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="f5291-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="f5291-105">Short description</span></span>

<span data-ttu-id="f5291-106">예약된 작업의 기본이 되는 파일 구조를 비롯하여 예약된 고급 작업 항목에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-106">Explains advanced scheduled job topics, including the file structure that underlies scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="f5291-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-107">Long description</span></span>

<span data-ttu-id="f5291-108">**PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5291-108">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="scheduled-job-directories-and-files"></a><span data-ttu-id="f5291-109">예약 된 작업 디렉터리 및 파일</span><span class="sxs-lookup"><span data-stu-id="f5291-109">Scheduled job directories and files</span></span>

<span data-ttu-id="f5291-110">PowerShell 예약 된 작업은 둘 다 PowerShell 작업 및 작업 스케줄러 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-110">PowerShell scheduled jobs are both PowerShell jobs and Task Scheduler tasks.</span></span>
<span data-ttu-id="f5291-111">각 예약 된 작업은 작업 스케줄러에 등록 되 고 Microsoft .NET Framework 직렬화 XML 형식으로 디스크에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-111">Each scheduled job is registered in Task Scheduler and saved on disk in Microsoft .NET Framework Serialization XML format.</span></span>

<span data-ttu-id="f5291-112">예약 된 작업을 만들 때 PowerShell은 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 로컬 컴퓨터의 디렉터리에 예약 된 작업에 대 한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-112">When you create a scheduled job, PowerShell creates a directory for the scheduled job in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span> <span data-ttu-id="f5291-113">디렉터리 이름은 작업 이름과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-113">The directory name is the same as the job name.</span></span>

<span data-ttu-id="f5291-114">다음은 샘플 **ScheduledJobs** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-114">The following is a sample **ScheduledJobs** directory.</span></span>

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

<span data-ttu-id="f5291-115">각 예약 된 작업에는 고유한 디렉터리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-115">Each scheduled job has its own directory.</span></span> <span data-ttu-id="f5291-116">디렉터리에는 예약 된 작업 XML 파일과 **출력** 하위 디렉터리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-116">The directory contains the scheduled job XML file and an **Output** subdirectory.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

<span data-ttu-id="f5291-117">예약 된 작업의 **출력** 디렉터리에는 실행 기록이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-117">The **Output** directory for a scheduled job contains its execution history.</span></span>
<span data-ttu-id="f5291-118">작업 트리거가 예약 된 작업을 시작할 때마다 PowerShell은 출력 디렉터리에 타임 스탬프 라는 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-118">Each time a job trigger starts a scheduled job, PowerShell creates a timestamp-named directory in the output directory.</span></span> <span data-ttu-id="f5291-119">Timestamp 디렉터리는 **Results.xml** 파일의 작업 결과와 **Status.xml** 파일의 작업 상태를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-119">The timestamp directory contains the results of the job in a **Results.xml** file and the job status in a **Status.xml** file.</span></span>

<span data-ttu-id="f5291-120">다음 명령은 **processjob** 예약 된 작업에 대 한 실행 기록 디렉터리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-120">The following command shows the execution history directories for the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

<span data-ttu-id="f5291-121">**ScheduledJobDefinition.xml** , **Results.xml** 및 **Status.xml** 파일을 열고 검사 하거나 cmdlet을 사용 하 여 `Select-XML` 파일을 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-121">You can open and examine the **ScheduledJobDefinition.xml** , **Results.xml** and **Status.xml** files or use the `Select-XML` cmdlet to parse the files.</span></span>

> [!WARNING]
> <span data-ttu-id="f5291-122">XML 파일을 편집 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f5291-122">Do not edit the XML files.</span></span> <span data-ttu-id="f5291-123">XML 파일에 잘못 된 XML이 포함 된 경우 PowerShell은 작업 결과를 포함 하 여 예약 된 작업 및 해당 실행 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-123">If any XML file contains invalid XML, PowerShell deletes the scheduled job and its execution history, including job results.</span></span>

## <a name="start-a-scheduled-job-immediately"></a><span data-ttu-id="f5291-124">예약 된 작업 즉시 시작</span><span class="sxs-lookup"><span data-stu-id="f5291-124">Start a scheduled job immediately</span></span>

<span data-ttu-id="f5291-125">다음 두 가지 방법 중 하나를 수행 하 여 예약 된 작업을 즉시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-125">You can start a scheduled job immediately in one of two ways:</span></span>

- <span data-ttu-id="f5291-126">Cmdlet을 실행 `Start-Job` 하 여 예약 된 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-126">Run the `Start-Job` cmdlet to start any scheduled job.</span></span>
- <span data-ttu-id="f5291-127">명령이 실행 되는 즉시 작업을 시작 하려면 **Runnow** 매개 변수를 명령에 추가 `Register-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-127">Add the **RunNow** parameter to your `Register-ScheduledJob` command to start the job as soon as the command is run.</span></span>

<span data-ttu-id="f5291-128">Cmdlet을 사용 하 여 시작 하는 작업 `Start-Job` 은 예약 된 작업의 인스턴스가 아닌 표준 PowerShell 백그라운드 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-128">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="f5291-129">모든 백그라운드 작업과 마찬가지로, 이러한 작업은 즉시 시작 되며, 작업 옵션이 나 작업 트리거의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-129">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers.</span></span> <span data-ttu-id="f5291-130">작업 출력은 예약 된 작업 디렉터리의 **출력** 디렉터리에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-130">The job output isn't saved in the **Output** directory of the scheduled job directory.</span></span>

<span data-ttu-id="f5291-131">다음 명령은 cmdlet의 **Definitionname** 매개 변수를 사용 하 여 `Start-Job` processjob 예약 된 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-131">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the ProcessJob scheduled job.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="f5291-132">작업을 관리 하 고 작업 결과를 가져오려면 작업 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-132">To manage the job and get the job results, use the job cmdlets.</span></span> <span data-ttu-id="f5291-133">작업 cmdlet에 대 한 자세한 내용은 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5291-133">For more information about the job cmdlets, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f5291-134">예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-134">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="f5291-135">**PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-135">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

## <a name="rename-a-scheduled-job"></a><span data-ttu-id="f5291-136">예약 된 작업 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="f5291-136">Rename a scheduled job</span></span>

<span data-ttu-id="f5291-137">예약 된 작업의 이름을 바꾸려면 cmdlet의 Name 매개 변수를 사용 합니다 `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="f5291-137">To rename a scheduled job, use the Name parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="f5291-138">예약 된 작업의 이름을 바꾸면 PowerShell에서 예약 된 작업의 이름과 예약 된 작업 디렉터리를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-138">When you rename a scheduled job, PowerShell changes the name of the scheduled job and the scheduled job directory.</span></span> <span data-ttu-id="f5291-139">그러나 이미 실행 된 예약 된 작업 인스턴스의 이름은 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-139">However, it doesn't change the names of instances of the scheduled job that have already run.</span></span>

## <a name="get-start-and-end-times"></a><span data-ttu-id="f5291-140">시작 및 종료 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="f5291-140">Get start and end times</span></span>

<span data-ttu-id="f5291-141">작업 인스턴스의 시작 및 종료 날짜와 시간을 가져오려면 예약 된 작업에 대해 반환 되는 Set-scheduledjob 개체의 **Psbegintime** 및 **psendtime** 속성을 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f5291-141">To get the dates and times that job instances started and ended, use the **PSBeginTime** and **PSEndTime** properties of the ScheduledJob object that `Get-Job` returns for scheduled jobs.</span></span>

<span data-ttu-id="f5291-142">다음 예에서는 cmdlet의 **Property** 매개 변수를 사용 하 여 `Format-Table` 각 작업 인스턴스의 **Psbegintime** 및 **psendtime** 속성을 테이블에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-142">The following example uses the **Property** parameter of the `Format-Table` cmdlet to display the **PSBeginTime** and **PSEndTime** properties of each job instance in a table.</span></span> <span data-ttu-id="f5291-143">**레이블** 이라는 계산 된 속성은 각 작업 인스턴스의 경과 된 시간을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-143">A calculated property named **Label** displays the elapsed time of each job instance.</span></span>

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a><span data-ttu-id="f5291-144">실행 기록 관리</span><span class="sxs-lookup"><span data-stu-id="f5291-144">Manage execution history</span></span>

<span data-ttu-id="f5291-145">예약 된 각 작업에 대해 저장 되는 작업 인스턴스 결과의 수를 확인 하 고 예약 된 작업의 실행 기록과 저장 된 작업 결과를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-145">You can determine the number of job instance results that are saved for each scheduled job and delete the execution history and saved job results of any scheduled job.</span></span>

<span data-ttu-id="f5291-146">예약 된 작업의 **ExecutionHistoryLength** 속성은 예약 된 작업에 대해 저장 되는 작업 인스턴스 결과 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-146">The **ExecutionHistoryLength** property of a scheduled job determines how many job instance results are saved for the scheduled job.</span></span> <span data-ttu-id="f5291-147">저장 된 결과 수가 **ExecutionHistoryLength** 속성의 값을 초과할 경우 PowerShell은 가장 오래 된 인스턴스의 결과를 삭제 하 여 최신 인스턴스의 결과를 위한 공간을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-147">When the number of saved results exceeds the value of the **ExecutionHistoryLength** property, PowerShell deletes the results of the oldest instance to make room for the results of the newest instance.</span></span>

<span data-ttu-id="f5291-148">기본적으로 PowerShell은 각 예약 된 작업의 32 인스턴스의 실행 기록과 결과를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-148">By default, PowerShell saves the execution history and results of 32 instances of each scheduled job.</span></span> <span data-ttu-id="f5291-149">이 값을 변경 하려면 또는 cmdlet의 **MaxResultCount** 매개 변수를 사용 합니다 `Register-ScheduledJob` `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="f5291-149">To change that value, use the **MaxResultCount** parameters of the `Register-ScheduledJob` or `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="f5291-150">예약 된 작업에 대 한 실행 기록 및 모든 결과를 삭제 하려면 cmdlet의 **ClearExecutionHistory** 매개 변수를 사용 합니다 `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="f5291-150">To delete the execution history and all results for a scheduled job, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="f5291-151">이 실행 기록을 삭제 해도 PowerShell에서 예약 된 작업의 새 인스턴스 결과를 저장 하는 것은 차단 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-151">Deleting this execution history does not prevent PowerShell from saving the results of new instances of the scheduled job.</span></span>

<span data-ttu-id="f5291-152">다음 예에서는 스 플랫를 사용 하 여 `$JobParms` cmdlet에 전달 되는 매개 변수 값을 만듭니다 `Register-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="f5291-152">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="f5291-153">자세한 내용은 [about_Splatting](../../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5291-153">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="f5291-154">는를 사용 하 여 `Register-ScheduledJob` `@JobParms` 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-154">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="f5291-155">이 명령은 **MaxResultCount** 매개 변수 값으로 12를 사용 하 여 예약 된 작업의 최신 작업 인스턴스 결과 12 개만 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-155">The command uses the **MaxResultCount** parameter with a value of 12 to save only the 12 newest job instance results of the scheduled job.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="f5291-156">다음 명령은 cmdlet의 **MaxResultCount** 매개 변수를 사용 하 여 `Set-ScheduledJob` 저장 된 인스턴스 결과의 수를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-156">The following command uses the **MaxResultCount** parameter of the `Set-ScheduledJob` cmdlet to increase the number of saved instance results to</span></span>
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

<span data-ttu-id="f5291-157">다음 명령은 **processjob** 예약 된 작업의 실행 기록과 현재 저장 된 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-157">The following command deletes the execution history and the current saved results of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="f5291-158">다음 명령은 컴퓨터에 있는 모든 예약 된 작업의 name 및 **ExecutionHistoryLength** 속성 값을 가져와 테이블에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5291-158">The following command gets the values of the name and **ExecutionHistoryLength** properties of all scheduled jobs on the computer and displays them in a table.</span></span>

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a><span data-ttu-id="f5291-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5291-159">See also</span></span>

[<span data-ttu-id="f5291-160">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="f5291-160">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="f5291-161">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="f5291-161">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="f5291-162">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="f5291-162">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="f5291-163">about_Splatting. md</span><span class="sxs-lookup"><span data-stu-id="f5291-163">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="f5291-164">[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet</span><span class="sxs-lookup"><span data-stu-id="f5291-164">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="f5291-165">작업 Scheduler</span><span class="sxs-lookup"><span data-stu-id="f5291-165">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
