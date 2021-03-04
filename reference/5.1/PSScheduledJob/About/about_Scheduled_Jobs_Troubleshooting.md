---
description: 예약 된 작업과 관련 된 문제를 해결 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: aac2133cee4abdd7e50e7b433104b9578d74b0a8
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685878"
---
# <a name="about-scheduled-jobs-troubleshooting"></a><span data-ttu-id="dcf49-104">예약 된 작업에 대 한 문제 해결</span><span class="sxs-lookup"><span data-stu-id="dcf49-104">About Scheduled Jobs Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="dcf49-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="dcf49-105">Short description</span></span>

<span data-ttu-id="dcf49-106">예약 된 작업과 관련 된 문제를 해결 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-106">Explains how to resolve problems with scheduled jobs</span></span>

## <a name="long-description"></a><span data-ttu-id="dcf49-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-107">Long description</span></span>

<span data-ttu-id="dcf49-108">이 문서에서는 PowerShell의 예약 된 작업 기능을 사용할 때 발생할 수 있는 몇 가지 문제에 대해 설명 하 고 이러한 문제에 대 한 해결 방법을 제안 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-108">This document describes some of the problems that you might experience when using the scheduled job features of PowerShell and it suggests solutions to these problems.</span></span>

<span data-ttu-id="dcf49-109">PowerShell 예약 된 작업을 사용 하기 전에 [about_Scheduled_Jobs](about_Scheduled_Jobs.md) 및 관련 예약 된 작업 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcf49-109">Before using PowerShell scheduled jobs, see [about_Scheduled_Jobs](about_Scheduled_Jobs.md) and the related scheduled jobs about topics.</span></span>

<span data-ttu-id="dcf49-110">**PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcf49-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="cant-find-job-results"></a><span data-ttu-id="dcf49-111">작업 결과를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="dcf49-111">Can't find job results</span></span>

### <a name="basic-method-for-getting-job-results-in-powershell"></a><span data-ttu-id="dcf49-112">PowerShell에서 작업 결과를 가져오는 기본 방법</span><span class="sxs-lookup"><span data-stu-id="dcf49-112">Basic method for getting job results in PowerShell</span></span>

<span data-ttu-id="dcf49-113">예약 된 작업이 실행 되 면 예약 된 작업의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-113">When a scheduled job runs, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="dcf49-114">예약 된 작업 인스턴스의 결과를 보고 관리 하 고 얻으려면 작업 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-114">To view, manage, and get the results of scheduled job instances, use the Job cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="dcf49-115">예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-115">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="dcf49-116">**PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-116">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="dcf49-117">예약 된 작업의 모든 인스턴스 목록을 가져오려면 cmdlet을 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="dcf49-117">To get a list of all instances of a scheduled job, use the `Get-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

<span data-ttu-id="dcf49-118">`Get-Job`Cmdlet은 **processjob** 개체를 파이프라인 아래로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-118">The `Get-Job` cmdlet sends **ProcessJob** objects down the pipeline.</span></span> <span data-ttu-id="dcf49-119">`Format-Table`Cmdlet은 예약 된 작업 인스턴스의 **Name**, **ID** 및 **psbegintime** 속성을 테이블에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-119">The `Format-Table` cmdlet displays the **Name**, **ID**, and **PSBeginTime** properties of a scheduled job instance in a table.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
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

<span data-ttu-id="dcf49-120">예약 된 작업의 인스턴스 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="dcf49-120">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="dcf49-121">다음 명령은 ProcessJob의 최신 인스턴스 (ID = 50)의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-121">The following command gets the results of the newest instance of the ProcessJob (ID = 50).</span></span>

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a><span data-ttu-id="dcf49-122">디스크에서 작업 결과를 찾는 기본 방법</span><span class="sxs-lookup"><span data-stu-id="dcf49-122">Basic method for finding job results on disk</span></span>

<span data-ttu-id="dcf49-123">예약 된 작업을 관리 하려면 및와 같은 작업 cmdlet을 `Get-Job` 사용 `Receive-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-123">To manage scheduled jobs, use the job cmdlets, such as `Get-Job` and `Receive-Job`.</span></span>

<span data-ttu-id="dcf49-124">`Get-Job`에서 작업 인스턴스를 가져오지 않거나 `Receive-Job` 작업 결과를 얻지 못하는 경우 디스크에서 작업에 대 한 실행 기록 파일을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-124">If `Get-Job` does not get the job instance or `Receive-Job` does not get the job results, you can search the execution history files for the job on disk.</span></span>
<span data-ttu-id="dcf49-125">실행 기록은 모든 트리거된 작업 인스턴스의 레코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-125">The execution history contains a record of all triggered job instances.</span></span>

<span data-ttu-id="dcf49-126">다음 경로에서 예약 된 작업에 대 한 디렉터리에 타임 스탬프 이름 디렉터리가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-126">Verify that there is a timestamp-named directory in the directory for a scheduled job in the following path:</span></span>

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="dcf49-127">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="dcf49-127">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="dcf49-128">예를 들어 `Get-ChildItem` cmdlet은 **processjob** 예약 된 작업의 디스크에 있는 실행 기록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-128">For example, the `Get-ChildItem` cmdlet gets the on-disk execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

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

<span data-ttu-id="dcf49-129">각 타임 스탬프 명명 디렉터리는 작업 인스턴스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-129">Each timestamp-named directory represents a job instance.</span></span> <span data-ttu-id="dcf49-130">각 작업 인스턴스의 결과는 타임 스탬프 명명 디렉터리의 **Results.xml** 파일에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-130">The results of each job instance are saved in a **Results.xml** file in the timestamp-named directory.</span></span>

<span data-ttu-id="dcf49-131">예를 들어 다음 명령은 **processjob** 예약 된 작업의 저장 된 모든 인스턴스에 대 한 **Results.xml** 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-131">For example, the following command gets the **Results.xml** files for every saved instance of the **ProcessJob** scheduled job.</span></span> <span data-ttu-id="dcf49-132">**Results.xml** 파일이 없으면 PowerShell에서 작업 결과를 반환 하거나 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-132">If the **Results.xml** file is missing, PowerShell cannot return or display the job results.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

<span data-ttu-id="dcf49-133">**PSScheduledJob** 모듈을 세션으로 가져오지 않았으므로 작업 cmdlet이 예약 된 작업 인스턴스 또는 해당 결과를 가져오지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-133">The job cmdlet might not be able to get scheduled job instances or their results because the **PSScheduledJob** module is not imported into the session.</span></span>

> [!NOTE]
> <span data-ttu-id="dcf49-134">예약 된 작업 인스턴스에 작업 cmdlet을 사용 하기 전에 **PSScheduledJob** 모듈이 세션에 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-134">Before using a job cmdlet on scheduled job instances, verify that the **PSScheduledJob** module is included in the session.</span></span> <span data-ttu-id="dcf49-135">**PSScheduledJob** 모듈이 없으면 작업 cmdlet은 예약 된 작업 인스턴스 또는 해당 결과를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-135">Without the **PSScheduledJob** module, the job cmdlets cannot get scheduled job instances or their results.</span></span>

<span data-ttu-id="dcf49-136">**PSScheduledJob** 모듈을 가져오려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-136">To import the **PSScheduledJob** module:</span></span>

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a><span data-ttu-id="dcf49-137">Receive-Job cmdlet은 이미 결과를 반환 했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-137">Receive-Job cmdlet might already have returned the results</span></span>

<span data-ttu-id="dcf49-138">`Receive-Job`에서 작업 인스턴스 결과를 반환 하지 않는 경우에는 `Receive-Job` **Keep** 매개 변수 없이 현재 세션에서 해당 작업 인스턴스에 대해 명령을 실행 했기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-138">If `Receive-Job` does not return job instance results, it might be because a `Receive-Job` command has been run for that job instance in the current session without the **Keep** parameter.</span></span>

<span data-ttu-id="dcf49-139">`Receive-Job` **Keep** 매개 변수 없이를 사용 하는 경우 `Receive-Job` 은 작업 결과를 반환 하 고 작업 인스턴스의 **HasMoreData** 속성을 **False** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-139">When you use `Receive-Job` without the **Keep** parameter, `Receive-Job` returns the job results and sets the job instance's **HasMoreData** property to **False**.</span></span> <span data-ttu-id="dcf49-140">**False** 값은 `Receive-Job` 작업의 결과를 반환 했 고 인스턴스에 반환할 결과가 더 이상 없음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-140">The **False** value means that `Receive-Job` returned the job's results and the instance has no more results to return.</span></span> <span data-ttu-id="dcf49-141">이 설정은 표준 백그라운드 작업에 적합 하지만, 디스크에 저장 된 예약 된 작업의 인스턴스에는 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-141">This setting is appropriate for standard background jobs, but not for instances of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="dcf49-142">작업 인스턴스 결과를 다시 가져오려면를 입력 하 여 새 PowerShell 세션을 시작 `PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-142">To get the job instance results again, start a new PowerShell session by typing `PowerShell`.</span></span> <span data-ttu-id="dcf49-143">**PSScheduledJob** 모듈을 가져온 후 `Receive-Job` 명령을 다시 시도 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dcf49-143">Import the **PSScheduledJob** module, and try the `Receive-Job` command again.</span></span>

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a><span data-ttu-id="dcf49-144">Keep 매개 변수를 사용 하 여 세션에서 두 번 이상 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="dcf49-144">Using Keep parameter to get results more than one time in a session</span></span>

<span data-ttu-id="dcf49-145">세션에서 작업 인스턴스의 결과를 두 번 이상 가져오려면 cmdlet의 **Keep** 매개 변수를 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="dcf49-145">To get the result of a job instance more than one time in a session, use the **Keep** parameter of the `Receive-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a><span data-ttu-id="dcf49-146">예약 된 작업이 손상 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-146">The scheduled job might be corrupted</span></span>

<span data-ttu-id="dcf49-147">예약 된 작업이 손상 되 면 PowerShell은 손상 된 예약 된 작업 및 해당 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-147">If a scheduled job becomes corrupted, PowerShell deletes the corrupted scheduled job and its results.</span></span> <span data-ttu-id="dcf49-148">손상 된 예약 된 작업의 결과를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-148">You cannot recover the results of a corrupted scheduled job.</span></span>

<span data-ttu-id="dcf49-149">예약 된 작업이 아직 있는지 확인 하려면 cmdlet을 사용 `Get-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-149">To determine if a scheduled job still exists, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a><span data-ttu-id="dcf49-150">결과 수가 ExecutionHistoryLength을 초과 했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-150">The number of results might have exceeded the ExecutionHistoryLength</span></span>

<span data-ttu-id="dcf49-151">예약 된 작업의 **ExecutionHistoryLength** 속성은 디스크에 저장 되는 작업 인스턴스 수 및 해당 결과를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-151">The **ExecutionHistoryLength** property of a scheduled job determines how many job instances, and their results, are saved to disk.</span></span> <span data-ttu-id="dcf49-152">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-152">The default value is 32.</span></span>
<span data-ttu-id="dcf49-153">예약 된 작업의 인스턴스 수가이 값을 초과 하면 PowerShell은 가장 오래 된 작업 인스턴스를 삭제 하 여 각각의 새 작업 인스턴스를 위한 공간을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-153">When the number of instances of a scheduled job exceeds this value, PowerShell deletes the oldest job instance to make room for each new job instance.</span></span>

<span data-ttu-id="dcf49-154">예약 된 작업의 **ExecutionHistoryLength** 속성 값을 가져오려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-154">To get the value of the **ExecutionHistoryLength** property of a scheduled job, use the following command format:</span></span>

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

<span data-ttu-id="dcf49-155">예를 들어 다음 명령은 **processjob** 예약 된 작업의 **ExecutionHistoryLength** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-155">For example, the following command gets the value of the **ExecutionHistoryLength** property of the **ProcessJob** scheduled job.</span></span>

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

<span data-ttu-id="dcf49-156">**ExecutionHistoryLength** 속성의 값을 설정 하거나 변경 하려면 및 Cmdlet의 **MaxResultCount** 매개 변수를 사용 `Register-ScheduledJob` 합니다 `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="dcf49-156">To set or change the value of the **ExecutionHistoryLength** property, use the **MaxResultCount** parameter of the `Register-ScheduledJob` and `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="dcf49-157">다음 명령은 **ExecutionHistoryLength** 속성의 값을 50로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-157">The following command increases the value of the **ExecutionHistoryLength** property to 50.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a><span data-ttu-id="dcf49-158">작업 인스턴스 결과가 삭제 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-158">The job instance results might have been deleted</span></span>

<span data-ttu-id="dcf49-159">Cmdlet의 **ClearExecutionHistory** 매개 변수는 `Set-ScheduledJob` 작업의 실행 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-159">The **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet deletes the execution history of a job.</span></span> <span data-ttu-id="dcf49-160">이 기능을 사용 하 여 디스크 공간을 확보 하거나 필요 하지 않거나 이미 사용, 분석 또는 다른 위치에 저장 된 결과를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-160">You can use this feature to free up disk space or delete results that are not needed, or already used, analyzed or saved in a different location.</span></span>

<span data-ttu-id="dcf49-161">예약 된 작업의 실행 기록을 삭제 하려면 예약 된 작업의 **ClearExecutionHistory** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-161">To delete the execution history of a scheduled job, use the **ClearExecutionHistory** parameter of the scheduled job.</span></span>

<span data-ttu-id="dcf49-162">다음 명령은 **processjob** 예약 된 작업의 실행 기록을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-162">The following command deletes the execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="dcf49-163">또한 cmdlet은 `Remove-Job` 작업 결과를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-163">Also, the `Remove-Job` cmdlet deletes job results.</span></span> <span data-ttu-id="dcf49-164">를 사용 하 여 `Remove-Job` 예약 된 작업을 삭제 하면 실행 기록과 모든 작업 결과를 포함 하 여 디스크에 있는 작업의 모든 인스턴스가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-164">When you use `Remove-Job` to delete a scheduled job, it deletes all instances of the job on disk, including the execution history and all job results.</span></span>

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a><span data-ttu-id="dcf49-165">Start-Job cmdlet을 사용 하 여 시작 된 작업은 디스크에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-165">Jobs started by using the Start-Job cmdlet are not saved to disk</span></span>

<span data-ttu-id="dcf49-166">를 사용 하 여 `Start-Job` 예약 된 작업을 시작할 때 작업 트리거를 사용 하는 대신는 `Start-Job` 표준 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-166">When you use `Start-Job` to start a scheduled job, instead of using a job trigger, `Start-Job` starts a standard background job.</span></span> <span data-ttu-id="dcf49-167">백그라운드 작업 및 그 결과는 디스크에 있는 작업의 실행 기록에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-167">The background job and its results are not stored in the execution history of the job on disk.</span></span>

<span data-ttu-id="dcf49-168">Cmdlet을 사용 하 여 작업 `Get-Job` `Receive-Job` 결과를 가져올 수 있지만 Cmdlet의 Keep 매개 변수를 사용 하지 않는 한 결과는 수신 될 때 까지만 사용할 수 있습니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="dcf49-168">You can use the `Get-Job` cmdlet to get the job and the `Receive-Job` cmdlet to get the job results, but the results are available only until you receive them, unless you use the Keep parameter of the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="dcf49-169">또한 백그라운드 작업과 그 결과는 세션 별로 다릅니다. 이러한 사용자는 생성 된 세션에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-169">Also, background jobs and their results are session-specific; they exist only in the session in which they are created.</span></span> <span data-ttu-id="dcf49-170">을 사용 하 여 작업을 삭제 하는 경우 `Remove-Job` 세션을 닫거나 PowerShell을 닫으면 작업 인스턴스와 해당 결과가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-170">If you delete the job with `Remove-Job`, close the session or close PowerShell, the job instance and its results are deleted.</span></span>

## <a name="scheduled-job-doesnt-run"></a><span data-ttu-id="dcf49-171">예약 된 작업이 실행 되지 않음</span><span class="sxs-lookup"><span data-stu-id="dcf49-171">Scheduled job doesn't run</span></span>

<span data-ttu-id="dcf49-172">작업 트리거 또는 예약 된 작업을 사용 하지 않도록 설정 하면 예약 된 작업이 자동으로 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-172">Scheduled jobs don't run automatically if the job triggers or the scheduled job are disabled.</span></span>

<span data-ttu-id="dcf49-173">Cmdlet을 사용 `Get-ScheduledJob` 하 여 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-173">Use the `Get-ScheduledJob` cmdlet to get the scheduled job.</span></span> <span data-ttu-id="dcf49-174">예약 된 작업의 **Enabled** 속성 값이 **True** 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-174">Verify that the value of the **Enabled** property of the scheduled job is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

<span data-ttu-id="dcf49-175">Cmdlet을 사용 `Get-JobTrigger` 하 여 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-175">Use the `Get-JobTrigger` cmdlet to get the job triggers of the scheduled job.</span></span>
<span data-ttu-id="dcf49-176">작업 트리거의 **Enabled** 속성 값이 **True** 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-176">Verify that the value of the **Enabled** property of the job trigger is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a><span data-ttu-id="dcf49-177">작업 트리거가 유효 하지 않으면 예약 된 작업이 자동으로 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-177">Scheduled jobs don't run automatically if job triggers are invalid</span></span>

<span data-ttu-id="dcf49-178">예를 들어 작업 트리거는 과거의 날짜 또는 발생 하지 않는 날짜를 지정할 수 있습니다 (예: 해당 월의 5 번째 월요일).</span><span class="sxs-lookup"><span data-stu-id="dcf49-178">For example, a job trigger might specify a date in the past or a date that does not occur, such as the 5th Monday of the month.</span></span>

<span data-ttu-id="dcf49-179">작업 트리거의 조건이 나 작업 옵션이 충족 되지 않으면 예약 된 작업이 자동으로 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-179">Scheduled jobs do not run automatically if the conditions of the job trigger or the job options are not satisfied.</span></span>

<span data-ttu-id="dcf49-180">예를 들어 사용자가 로그온 하지 않거나 원격 으로만 연결 하는 경우 특정 사용자가 컴퓨터에 로그온 할 때만 실행 되는 예약 된 작업이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-180">For example, a scheduled job that runs only when a particular user logs on to the computer will not run if that user does not log on or only connects remotely.</span></span>

<span data-ttu-id="dcf49-181">예약 된 작업의 옵션을 검토 하 고 충족 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-181">Examine the options of the scheduled job and make sure that they are satisfied.</span></span>
<span data-ttu-id="dcf49-182">예를 들어 컴퓨터가 유휴 상태 이거나 네트워크에 연결 되어 있거나, 긴 **IdleDuration** 있거나, 짧은 **IdleTimeout** 을 사용 해야 하는 예약 된 작업이 실행 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-182">For example, a scheduled job that requires that the computer be idle or requires a network connection, or has a long **IdleDuration** or a brief **IdleTimeout** might never run.</span></span>

<span data-ttu-id="dcf49-183">Cmdlet을 사용 `Get-ScheduledJobOption` 하 여 작업 옵션 및 해당 값을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-183">Use the `Get-ScheduledJobOption` cmdlet to examine the job options and their values.</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="dcf49-184">예약 된 작업 옵션에 대 한 설명은 [set-scheduledjoboption](xref:PSScheduledJob.New-ScheduledJobOption)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcf49-184">For descriptions of the scheduled job options, see [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

### <a name="the-scheduled-job-instance-might-have-failed"></a><span data-ttu-id="dcf49-185">예약 된 작업 인스턴스가 실패 했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-185">The scheduled job instance might have failed</span></span>

<span data-ttu-id="dcf49-186">예약 된 작업 명령이 실패 하면 PowerShell에서 오류 메시지를 생성 하 여 즉시 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-186">If a scheduled job command fails, PowerShell reports it immediately by generating an error message.</span></span> <span data-ttu-id="dcf49-187">그러나 작업 스케줄러 실행 하려고 할 때 작업이 실패 하면 PowerShell에서 오류를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-187">However, if the job fails when Task Scheduler tries to run it, the error is not available to PowerShell.</span></span>

<span data-ttu-id="dcf49-188">작업 오류를 검색 하 고 수정 하려면 다음 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-188">Use the following methods to detect and correct job failures:</span></span>

<span data-ttu-id="dcf49-189">작업 스케줄러 이벤트 로그에서 오류를 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dcf49-189">Check the Task Scheduler event log for errors.</span></span> <span data-ttu-id="dcf49-190">로그를 확인 하려면 다음과 같이 이벤트 뷰어 또는 PowerShell 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-190">To check the log, use Event Viewer or a PowerShell command such as the following:</span></span>

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

<span data-ttu-id="dcf49-191">작업 스케줄러에서 작업 레코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-191">Check the job record in Task Scheduler.</span></span> <span data-ttu-id="dcf49-192">PowerShell 예약 된 작업은 다음 작업 예약 폴더에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-192">PowerShell scheduled jobs are stored in the following Task Scheduled folder:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a><span data-ttu-id="dcf49-193">권한이 부족 하 여 예약 된 작업이 실행 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-193">The scheduled job might not run because of insufficient permission</span></span>

<span data-ttu-id="dcf49-194">예약 된 작업은 작업을 만든 사용자의 사용 권한 또는 또는 명령의 **Credential** 매개 변수로 지정 된 사용자의 사용 권한으로 실행 `Register-ScheduledJob` `Set-ScheduledJob` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-194">Scheduled jobs run with the permissions of the user who created the job or the permissions of the user who is specified by the **Credential** parameter in the `Register-ScheduledJob` or `Set-ScheduledJob` command.</span></span>

<span data-ttu-id="dcf49-195">해당 사용자에 게 명령 또는 스크립트를 실행할 수 있는 권한이 없는 경우 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-195">If that user does not have permission to run the commands or scripts, the job fails.</span></span>

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a><span data-ttu-id="dcf49-196">예약 된 작업을 가져올 수 없거나 예약 된 작업이 손상 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-196">Can't get scheduled job or scheduled job is corrupted</span></span>

<span data-ttu-id="dcf49-197">드문 경우 지만 예약 된 작업이 손상 되거나 해결할 수 없는 내부 모순 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-197">On rare occasions, scheduled jobs can become corrupted or contain internal contradictions that cannot be resolved.</span></span> <span data-ttu-id="dcf49-198">일반적으로이 작업은 예약 된 작업에 대 한 XML 파일을 수동으로 편집 하 여 잘못 된 XML을 생성 하는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-198">Typically, this happens when the XML files for the scheduled job are manually edited, resulting in invalid XML.</span></span>

<span data-ttu-id="dcf49-199">예약 된 작업이 손상 되 면 PowerShell에서 예약 된 작업, 해당 실행 기록 및 디스크의 결과를 삭제 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-199">When a scheduled job is corrupted, PowerShell attempts to delete the scheduled job, its execution history, and its results from disk.</span></span>

<span data-ttu-id="dcf49-200">예약 된 작업을 제거할 수 없는 경우 cmdlet을 실행할 때마다 손상 된 작업 오류 메시지가 표시 됩니다 `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="dcf49-200">If it cannot remove the scheduled job, you will get a corrupted job error message each time you run the `Get-ScheduledJob` cmdlet.</span></span>

<span data-ttu-id="dcf49-201">손상 된 예약 된 작업을 제거 하려면 다음 방법 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-201">To remove a corrupted scheduled job, use either one of the following methods:</span></span>

<span data-ttu-id="dcf49-202">예약 된 `<ScheduledJobName>` 작업에 대 한 디렉터리를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-202">Delete the `<ScheduledJobName>` directory for the scheduled job.</span></span> <span data-ttu-id="dcf49-203">**Set-scheduledjob** 디렉터리를 삭제 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="dcf49-203">Don't delete the **ScheduledJob** directory.</span></span>

<span data-ttu-id="dcf49-204">디렉터리의 위치:</span><span class="sxs-lookup"><span data-stu-id="dcf49-204">The directory's location:</span></span>

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

<span data-ttu-id="dcf49-205">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="dcf49-205">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

<span data-ttu-id="dcf49-206">작업 스케줄러를 사용 하 여 예약 된 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-206">Use Task Scheduler to delete the scheduled job.</span></span> <span data-ttu-id="dcf49-207">PowerShell 예약 된 작업은 다음 작업 스케줄러 경로에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-207">PowerShell scheduled tasks appear in the following Task Scheduler path:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a><span data-ttu-id="dcf49-208">작업 cmdlet이 예약 된 작업을 일관 되 게 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="dcf49-208">Job cmdlets can't consistently find scheduled jobs</span></span>

<span data-ttu-id="dcf49-209">**PSScheduledJob** 모듈이 현재 세션에 없으면 작업 cmdlet은 예약 된 작업을 가져오거나, 시작 하거나, 결과를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-209">When the **PSScheduledJob** module isn't in the current session, the job cmdlets cannot get scheduled jobs, start them, or get their results.</span></span>

<span data-ttu-id="dcf49-210">**PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` cmdlet과 같이 모듈에서 cmdlet을 입력 하거나 실행 하거나 가져옵니다 `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="dcf49-210">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or run or get any cmdlet in the module, such as the `Get-ScheduledJob` cmdlet.</span></span>
<span data-ttu-id="dcf49-211">PowerShell 3.0부터 모듈에서 cmdlet을 가져오거나 사용 하면 모듈을 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-211">Beginning in PowerShell 3.0, modules are imported automatically when you get or use any cmdlet in the module.</span></span>

<span data-ttu-id="dcf49-212">**PSScheduledJob** 모듈이 현재 세션에 없는 경우 다음 명령 시퀀스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-212">When the **PSScheduledJob** module isn't in the current session, the following command sequence is possible.</span></span>

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

<span data-ttu-id="dcf49-213">이 동작은 `Get-ScheduledJob` 명령이 **PSScheduledJob** 모듈을 자동으로 가져온 다음 명령을 실행 하기 때문에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcf49-213">This behavior occurs because the `Get-ScheduledJob` command automatically imports the **PSScheduledJob** module, and then runs the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcf49-214">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dcf49-214">See also</span></span>

[<span data-ttu-id="dcf49-215">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="dcf49-215">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="dcf49-216">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="dcf49-216">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="dcf49-217">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="dcf49-217">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

<span data-ttu-id="dcf49-218">[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet</span><span class="sxs-lookup"><span data-stu-id="dcf49-218">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="dcf49-219">작업 Scheduler</span><span class="sxs-lookup"><span data-stu-id="dcf49-219">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
