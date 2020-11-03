---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213425"
---
# <span data-ttu-id="51dd1-103">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-103">New-JobTrigger</span></span>

## <span data-ttu-id="51dd1-104">개요</span><span class="sxs-lookup"><span data-stu-id="51dd1-104">SYNOPSIS</span></span>
<span data-ttu-id="51dd1-105">예약된 작업에 대한 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-105">Creates a job trigger for a scheduled job.</span></span>

## <span data-ttu-id="51dd1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="51dd1-106">SYNTAX</span></span>

### <span data-ttu-id="51dd1-107">한 번 (기본값)</span><span class="sxs-lookup"><span data-stu-id="51dd1-107">Once (Default)</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### <span data-ttu-id="51dd1-108">매일</span><span class="sxs-lookup"><span data-stu-id="51dd1-108">Daily</span></span>

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### <span data-ttu-id="51dd1-109">매주</span><span class="sxs-lookup"><span data-stu-id="51dd1-109">Weekly</span></span>

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### <span data-ttu-id="51dd1-110">AtStartup</span><span class="sxs-lookup"><span data-stu-id="51dd1-110">AtStartup</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### <span data-ttu-id="51dd1-111">AtLogon</span><span class="sxs-lookup"><span data-stu-id="51dd1-111">AtLogon</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## <span data-ttu-id="51dd1-112">설명</span><span class="sxs-lookup"><span data-stu-id="51dd1-112">DESCRIPTION</span></span>
<span data-ttu-id="51dd1-113">**새 JobTrigger** cmdlet은 일회성 또는 되풀이 일정에 따라 또는 이벤트가 발생 하는 경우 예약 된 작업을 시작 하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-113">The **New-JobTrigger** cmdlet creates a job trigger that starts a scheduled job on a one-time or recurring schedule, or when an event occurs.</span></span>

<span data-ttu-id="51dd1-114">**New-JobTrigger** 가 반환하는 **ScheduledJobTrigger** 개체를 사용하여 새 예약된 작업이나 기존 예약된 작업에 대한 작업 트리거를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-114">You can use the **ScheduledJobTrigger** object that **New-JobTrigger** returns to set a job trigger for a new or existing scheduled job.</span></span>
<span data-ttu-id="51dd1-115">Get-JobTrigger cmdlet을 사용 하 여 기존 예약 된 작업의 작업 트리거를 가져오거나, 해시 테이블 값을 사용 하 여 작업 트리거를 나타내는 작업 트리거를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-115">You can also create a job trigger by using the Get-JobTrigger cmdlet to get the job trigger of an existing scheduled job, or by using a hash table value to represent a job trigger.</span></span>

<span data-ttu-id="51dd1-116">작업 트리거를 만들 때 New-ScheduledJobOption cmdlet에 지정 된 옵션의 기본값을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-116">When creating a job trigger, review the default values of the options specified by the New-ScheduledJobOption cmdlet.</span></span>
<span data-ttu-id="51dd1-117">이러한 옵션은 유효한 값과 기본값이 **Task Scheduler** 의 해당 옵션과 같으며 예약된 작업의 일정과 타이밍에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-117">These options, which have the same valid and default values as the corresponding options in **Task Scheduler** , affect the scheduling and timing of scheduled jobs.</span></span>

<span data-ttu-id="51dd1-118">**새 JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-118">**New-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="51dd1-119">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51dd1-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="51dd1-120">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51dd1-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="51dd1-121">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="51dd1-122">예제</span><span class="sxs-lookup"><span data-stu-id="51dd1-122">EXAMPLES</span></span>

### <span data-ttu-id="51dd1-123">예 1: 한 번 예약</span><span class="sxs-lookup"><span data-stu-id="51dd1-123">Example 1: Once Schedule</span></span>

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

<span data-ttu-id="51dd1-124">이 명령은 **New-JobTrigger** cmdlet을 사용하여 예약된 작업을 한 번만 시작하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-124">This command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a scheduled job only one time.</span></span>
<span data-ttu-id="51dd1-125">*At* 매개 변수 값은 Windows PowerShell이 **DateTime** 개체로 변환하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-125">The value of the *At* parameter is a string that Windows PowerShell converts into a **DateTime** object.</span></span>
<span data-ttu-id="51dd1-126">*At* 매개 변수 값에는 시간뿐 아니라 명시적 날짜도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-126">The *At* parameter value includes an explicit date, not just a time.</span></span>
<span data-ttu-id="51dd1-127">날짜를 생략하면 현재 날짜와 오전 3:00 시간으로 트리거가 만들어지며 과거 시간을 나타낼 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-127">If the date were omitted, the trigger would be created with the current date and 3:00 AM time, which is likely to represent a time in the past.</span></span>

### <span data-ttu-id="51dd1-128">예 2: 일별 일정</span><span class="sxs-lookup"><span data-stu-id="51dd1-128">Example 2: Daily Schedule</span></span>

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

<span data-ttu-id="51dd1-129">이 명령은 3일마다 오전 4:15에 예약된 작업을 시작하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-129">This command creates a job trigger that starts a scheduled job every 3 days at 4:15 a.m.</span></span>

<span data-ttu-id="51dd1-130">*At* 매개 변수 값에 날짜가 없으므로 현재 날짜가 **DateTime** 개체의 날짜 값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-130">Because the value of the *At* parameter does not include a date, the current date is used as the date value in the **DateTime** object.</span></span>
<span data-ttu-id="51dd1-131">날짜와 시간이 과거이면 *At* 매개 변수 값에서 3일 후인 다음 발생 시 예약된 작업이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-131">If the date and time is in the past, the scheduled job is started at the next occurrence, which is 3 days later from the *At* parameter value.</span></span>

### <span data-ttu-id="51dd1-132">예 3: 주간 일정</span><span class="sxs-lookup"><span data-stu-id="51dd1-132">Example 3: Weekly Schedule</span></span>

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

<span data-ttu-id="51dd1-133">이 명령은 4주마다 월요일, 수요일 및 금요일 23시(오후 11:00)에 예약된 작업을 시작하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-133">This command creates a job trigger that starts a scheduled job every 4 weeks on Monday, Wednesday, and Friday at 2300 hours (11:00 PM).</span></span>

<span data-ttu-id="51dd1-134">*DaysOfWeek* 매개 변수 값을와 같은 정수로 입력할 수도 있습니다 `-DaysOfWeek 1, 5` .</span><span class="sxs-lookup"><span data-stu-id="51dd1-134">You can also enter the *DaysOfWeek* parameter value in integers, such as `-DaysOfWeek 1, 5`.</span></span>

### <span data-ttu-id="51dd1-135">예 4: 로그온 일정</span><span class="sxs-lookup"><span data-stu-id="51dd1-135">Example 4: Logon Schedule</span></span>

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

<span data-ttu-id="51dd1-136">이 명령은 도메인 관리자가 컴퓨터에 로그온할 때마다 예약된 작업을 시작하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-136">This command creates a job trigger that starts a scheduled job whenever the domain administrator logs onto the computer.</span></span>

### <span data-ttu-id="51dd1-137">예 5: 임의 지연 사용</span><span class="sxs-lookup"><span data-stu-id="51dd1-137">Example 5: Using a Random Delay</span></span>

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

<span data-ttu-id="51dd1-138">이 명령은 매일 오전 1:00에 예약된 작업을 시작하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-138">This command creates a job trigger that starts a scheduled job every day at 1:00 in the morning.</span></span>
<span data-ttu-id="51dd1-139">*RandomDelay* 매개 변수를 사용하여 최대 지연을 20분으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-139">The command uses the *RandomDelay* parameter to set the maximum delay to 20 minutes.</span></span>
<span data-ttu-id="51dd1-140">따라서 작업이 오전 1:00에서 오전 1:20 사이에 실행되며 간격은 의사 임의로 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-140">As a result, the job runs every day between 1:00 AM and 1:20 AM, with the interval varying pseudo-randomly.</span></span>

<span data-ttu-id="51dd1-141">샘플링, 부하 분산 및 기타 관리 작업에 임의 지연을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-141">You can use a random delay for sampling, load balancing, and other administrative tasks.</span></span>
<span data-ttu-id="51dd1-142">지연 값을 설정 하는 경우 New-ScheduledJobOption cmdlet의 유효 및 기본값을 검토 하 고 옵션 설정을 사용 하 여 지연을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-142">When setting the delay value, review the effective and default values of the New-ScheduledJobOption cmdlet and coordinate the delay with the option settings.</span></span>

### <span data-ttu-id="51dd1-143">예 6: 새 예약 된 작업에 대 한 작업 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="51dd1-143">Example 6: Create a Job Trigger for a New Scheduled Job</span></span>

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

<span data-ttu-id="51dd1-144">이 명령은 작업 트리거를 사용하여 새 예약된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-144">These commands use a job trigger to create a new scheduled job.</span></span>

### <span data-ttu-id="51dd1-145">예 7: 예약 된 작업에 작업 트리거 추가</span><span class="sxs-lookup"><span data-stu-id="51dd1-145">Example 7: Add a Job Trigger to a Scheduled Job</span></span>

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

<span data-ttu-id="51dd1-146">이 예제에서는 기존 예약된 작업에 작업 트리거를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-146">This example shows how to add a job trigger to an existing scheduled job.</span></span>
<span data-ttu-id="51dd1-147">여러 개의 작업 트리거를 예약된 작업에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-147">You can add multiple job triggers to any scheduled job.</span></span>

<span data-ttu-id="51dd1-148">이 명령은 Add-JobTrigger cmdlet을 사용 하 여 시 synchronizeapps 예약 된 작업에 작업 트리거를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-148">The command uses the Add-JobTrigger cmdlet to add the job trigger to the SynchronizeApps scheduled job.</span></span>
<span data-ttu-id="51dd1-149">*Trigger* 매개 변수 값은 매일 오전 3:10에 작업을 실행하는 **New-JobTrigger** 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-149">The value of the *Trigger* parameter is a **New-JobTrigger** command that runs the job every day at 3:10 AM.</span></span>

<span data-ttu-id="51dd1-150">명령 완료 시 SynchronizeApps는 작업 트리거에 의해 지정된 시간에 실행되는 예약된 작업이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-150">When the command completes, SynchronizeApps is a scheduled job that runs at the times specified by the job trigger.</span></span>

### <span data-ttu-id="51dd1-151">예 8: 반복 작업 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="51dd1-151">Example 8: Create a repeating job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

<span data-ttu-id="51dd1-152">이 명령은 2013 9 월 12 일에 시작 하 여 48 시간 동안 60 분 마다 작업을 실행 하는 작업 트리거를 1:00 AM으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-152">This command creates a job trigger that runs a job every 60 minutes for 48 hours beginning on September 12, 2013 at 1:00 AM.</span></span>

### <span data-ttu-id="51dd1-153">예 9: 되풀이 작업 트리거 중지</span><span class="sxs-lookup"><span data-stu-id="51dd1-153">Example 9: Stop a repeating job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

<span data-ttu-id="51dd1-154">이 명령은 작업 트리거가 만료될 때까지 60분마다 실행되도록 트리거되는 SecurityCheck 작업을 강제로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-154">This command forcibly stops the SecurityCheck job, which is triggered to run every 60 minutes until its job trigger expires.</span></span>

<span data-ttu-id="51dd1-155">작업의 반복을 방지 하기 위해이 명령은 Get-JobTrigger를 사용 하 여 SecurityCheck 작업의 작업 트리거를 가져오고 Set-JobTrigger cmdlet을 사용 하 여 작업 트리거의 반복 간격 및 반복 기간을 0으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-155">To prevent the job from repeating, the command uses the Get-JobTrigger to get the job trigger of the SecurityCheck job and the Set-JobTrigger cmdlet to change the repetition interval and repetition duration of the job trigger to zero (0).</span></span>

### <span data-ttu-id="51dd1-156">예 10: 매시간 작업 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="51dd1-156">Example 10: Create an hourly job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

<span data-ttu-id="51dd1-157">다음 명령은 무기한 동안 12시간마다 한 번 예약된 작업을 실행하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-157">The following command creates a job trigger that runs a scheduled job once every 12 hours for an indefinite period of time.</span></span>
<span data-ttu-id="51dd1-158">내일(9/21/2012) 자정(오전 0:00)에 일정이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-158">The schedule begins tomorrow (9/21/2012) at midnight (0:00 AM).</span></span>

## <span data-ttu-id="51dd1-159">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51dd1-159">PARAMETERS</span></span>

### <span data-ttu-id="51dd1-160">-At</span><span class="sxs-lookup"><span data-stu-id="51dd1-160">-At</span></span>
<span data-ttu-id="51dd1-161">지정한 날짜 및 시간에 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-161">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="51dd1-162">Get-Date cmdlet에서 반환 하는 것과 같은 **DateTime** 개체를 입력 하거나 날짜 및 시간으로 변환할 수 있는 문자열 (예: "4 월 19 일 2012 15:00", "12/31" 또는 "3am")을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-162">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a date and time, such as "April 19, 2012 15:00", "12/31", or "3am".</span></span>
<span data-ttu-id="51dd1-163">연도와 같은 날짜의 요소를 지정하지 않으면 트리거의 날짜에 현재 날짜의 해당 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-163">If you don't specify an element of the date, such as the year, the date in the trigger has the corresponding element from the current date.</span></span>

<span data-ttu-id="51dd1-164">*Once* 매개 변수를 사용할 경우 *At* 매개 변수 값을 미래 날짜와 시간으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-164">When using the *Once* parameter, set the value of the *At* parameter to a future date and time.</span></span>
<span data-ttu-id="51dd1-165">**DateTime** 개체의 기본 날짜는 현재 날짜이기 때문에 명시적 날짜 없이 현재 시간 이전의 시간을 지정할 경우 과거 시간에 대한 작업 트리거가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-165">Because the default date in a **DateTime** object is the current date, if you specify a time before the current time without an explicit date, the job trigger is created for a time in the past.</span></span>

<span data-ttu-id="51dd1-166">Datetime **개체와** **datetime** 개체로 변환 되는 문자열은 제어판의 지역 및 언어에서 로컬 컴퓨터에 대해 선택한 날짜 및 시간 형식과 호환 되도록 자동으로 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-166">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-167">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="51dd1-167">-AtLogOn</span></span>
<span data-ttu-id="51dd1-168">지정한 사용자가 컴퓨터에 로그온할 때 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-168">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="51dd1-169">사용자를 지정하려면 *User* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-169">To specify a user, use the *User* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-170">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="51dd1-170">-AtStartup</span></span>
<span data-ttu-id="51dd1-171">Windows가 시작될 때 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-171">Starts the scheduled job when Windows starts.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-172">-매일</span><span class="sxs-lookup"><span data-stu-id="51dd1-172">-Daily</span></span>
<span data-ttu-id="51dd1-173">매일 되풀이되는 작업 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-173">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="51dd1-174">*매일* 매개 변수 집합의 다른 매개 변수를 사용 하 여 일정 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-174">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-175">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="51dd1-175">-DaysInterval</span></span>
<span data-ttu-id="51dd1-176">일별 일정의 발생 간격(일)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-176">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="51dd1-177">예를 들어 값이 3이면 예약된 작업이 1, 4, 7일 등에 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-177">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="51dd1-178">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-178">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-179">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="51dd1-179">-DaysOfWeek</span></span>
<span data-ttu-id="51dd1-180">주별 예약된 작업이 실행되는 요일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-180">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="51dd1-181">요일 이름(예: "Monday") 또는 정수 0-6을 입력합니다. 여기서 0은 일요일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-181">Enter day names, such as "Monday" or integers 0-6, where 0 represents Sunday.</span></span>
<span data-ttu-id="51dd1-182">이 매개 변수는 Weekly 매개 변수 집합에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-182">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="51dd1-183">요일 이름은 작업 트리거에서 해당 정수 값으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-183">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="51dd1-184">명령에서 요일 이름을 따옴표로 묶을 경우 "Monday", "Tuesday"와 같이 각 요일 이름을 별도의 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-184">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="51dd1-185">여러 요일 이름을 하나의 따옴표 쌍으로 묶으면 해당 정수 값이 합산됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-185">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="51dd1-186">예를 들어 "Monday, Tuesday"(1, 2)는 "Wednesday"(3) 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-186">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-187">-한 번</span><span class="sxs-lookup"><span data-stu-id="51dd1-187">-Once</span></span>
<span data-ttu-id="51dd1-188">되풀이되지 않는(일회성) 일정이나 사용자 지정 되풀이 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-188">Specifies a non-recurring (one time) or custom repeating schedule.</span></span>
<span data-ttu-id="51dd1-189">되풀이 일정을 만들려면 *Once* 매개 변수를 *RepetitionDuration* 및 *RepetitionInterval* 매개 변수와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-189">To create a repeating schedule, use the *Once* parameter with the *RepetitionDuration* and *RepetitionInterval* parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-190">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="51dd1-190">-RandomDelay</span></span>
<span data-ttu-id="51dd1-191">예약된 시작 시간에 시작되는 임의 지연을 사용하도록 설정하고 최대 지연 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-191">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="51dd1-192">지연 길이는 각 시작에 대해 의사 임의로 설정되며 지연 없음에서 이 매개 변수 값으로 지정된 시간까지 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-192">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="51dd1-193">기본값 0(00:00:00)은 임의 지연을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-193">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="51dd1-194">New-TimeSpan cmdlet에서 반환 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: format에 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-194">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a **TimeSpan** object.</span></span>

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

### <span data-ttu-id="51dd1-195">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="51dd1-195">-RepeatIndefinitely</span></span>
<span data-ttu-id="51dd1-196">Windows PowerShell 4.0부터 제공되는 이 매개 변수를 사용하면 예약된 작업을 무기한 동안 되풀이해서 실행하기 위해 **RepetitionDuration** 매개 변수에 *TimeSpan.MaxValue* 값을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-196">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-197">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="51dd1-197">-RepetitionDuration</span></span>
<span data-ttu-id="51dd1-198">지정한 시간이 만료될 때까지 작업을 되풀이합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-198">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="51dd1-199">되풀이 빈도는 *RepetitionInterval* 매개 변수 값에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-199">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="51dd1-200">예를 들어 **RepetitionInterval** 값이 5분이고 **RepetitionDuration** 값이 2시간이면 2시간 동안 5분마다 작업이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-200">For example, if the value of **RepetitionInterval** is 5 minutes and the value of **RepetitionDuration** is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="51dd1-201">New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-201">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="51dd1-202">작업을 무기한 실행하려면 *RepeatIndefinitely* 매개 변수를 대신 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-202">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="51dd1-203">작업 트리거 반복 기간이 만료 되기 전에 작업을 중지 하려면 Set-JobTrigger cmdlet을 사용 하 여 *RepetitionDuration* 값을 영 (0)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-203">To stop a job before the job trigger repetition duration expires, use the Set-JobTrigger cmdlet to set the *RepetitionDuration* value to zero (0).</span></span>

<span data-ttu-id="51dd1-204">이 매개 변수는 명령에 *Once* , *At* 및 *RepetitionInterval* 매개 변수가 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-204">This parameter is valid only when the *Once* , *At* and *RepetitionInterval* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-205">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="51dd1-205">-RepetitionInterval</span></span>
<span data-ttu-id="51dd1-206">지정한 시간 간격에 작업을 되풀이합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-206">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="51dd1-207">예를 들어 이 매개 변수 값이 2시간이면 2시간마다 작업이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-207">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="51dd1-208">기본값 0은 작업을 되풀이하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-208">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="51dd1-209">New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-209">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="51dd1-210">이 매개 변수는 명령에 *Once* , *At* 및 *RepetitionDuration* 매개 변수가 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-210">This parameter is valid only when the *Once* , *At* , and *RepetitionDuration* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-211">-User</span><span class="sxs-lookup"><span data-stu-id="51dd1-211">-User</span></span>
<span data-ttu-id="51dd1-212">예약된 작업의 *AtLogon* 시작을 트리거하는 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-212">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="51dd1-213">사용자의 이름을 또는 형식으로 입력 \<UserName\> \<Domain\Username\> 하거나 별표 ( \* )를 입력 하 여 모든 사용자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-213">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="51dd1-214">기본값은 모든 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-214">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-215">-매주</span><span class="sxs-lookup"><span data-stu-id="51dd1-215">-Weekly</span></span>
<span data-ttu-id="51dd1-216">매주 되풀이되는 작업 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-216">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="51dd1-217">Weekly 매개 변수 집합의 다른 매개 변수를 사용하여 일정 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-217">Use the other parameters in the Weekly parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-218">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="51dd1-218">-WeeksInterval</span></span>
<span data-ttu-id="51dd1-219">주별 작업 일정의 발생 간격(주)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-219">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="51dd1-220">예를 들어 값이 3이면 예약된 작업이 1, 4, 7주 등에 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-220">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="51dd1-221">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-221">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Weekly
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51dd1-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51dd1-222">CommonParameters</span></span>
<span data-ttu-id="51dd1-223">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51dd1-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51dd1-224">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51dd1-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51dd1-225">입력</span><span class="sxs-lookup"><span data-stu-id="51dd1-225">INPUTS</span></span>

### <span data-ttu-id="51dd1-226">없음</span><span class="sxs-lookup"><span data-stu-id="51dd1-226">None</span></span>
<span data-ttu-id="51dd1-227">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-227">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="51dd1-228">출력</span><span class="sxs-lookup"><span data-stu-id="51dd1-228">OUTPUTS</span></span>

### <span data-ttu-id="51dd1-229">Set-scheduledjob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-229">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="51dd1-230">참고</span><span class="sxs-lookup"><span data-stu-id="51dd1-230">NOTES</span></span>

* <span data-ttu-id="51dd1-231">작업 트리거는 디스크에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-231">Job triggers are not saved to disk.</span></span> <span data-ttu-id="51dd1-232">그러나 예약 된 작업은 디스크에 저장 되 고 Get-JobTrigger를 사용 하 여 예약 된 작업의 작업 트리거를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-232">However, scheduled jobs are saved to disk, and you can use the Get-JobTrigger to get the job trigger of any scheduled job.</span></span>
* <span data-ttu-id="51dd1-233">**새 JobTrigger** 는 과거 날짜에 대 한 일회성 트리거와 같이 예약 된 작업을 실행 하지 않는 작업 트리거를 만들 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-233">**New-JobTrigger** does not prevent you from creating a job trigger that will not run a scheduled job, such as one-time trigger for a date in the past.</span></span>
* <span data-ttu-id="51dd1-234">Register-ScheduledJob cmdlet은 **New-JobTrigger** 또는 Get-JobTrigger cmdlet에서 반환 된 개체 또는 트리거 값을 포함 하는 해시 테이블을 비롯 한 ScheduledJobTrigger 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-234">The Register-ScheduledJob cmdlet accepts a ScheduledJobTrigger object, such as one returned by the **New-JobTrigger** or Get-JobTrigger cmdlets, or a hash table with trigger values.</span></span>

  <span data-ttu-id="51dd1-235">해시 테이블을 제출하려면 다음 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51dd1-235">To submit a hash table, use the following keys.</span></span>

  <span data-ttu-id="51dd1-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` 또는 유효한 시간 문자열입니다. `DaysOfWeek="Monday", "Wednesday"` (또는 요일 이름의 조합) `Interval=2` (또는 유효한 빈도 간격); `RandomDelay="30minutes"` (또는 유효한 timespan 문자열) `User="Domain1\User01` 또는 모든 유효한 사용자 ( *Atlogon* frequency 값 에서만 사용)}</span><span class="sxs-lookup"><span data-stu-id="51dd1-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01` (or any valid user; used only with the *AtLogon* frequency value) }</span></span>

## <span data-ttu-id="51dd1-237">관련 링크</span><span class="sxs-lookup"><span data-stu-id="51dd1-237">RELATED LINKS</span></span>

[<span data-ttu-id="51dd1-238">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-238">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="51dd1-239">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-239">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="51dd1-240">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="51dd1-240">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="51dd1-241">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-241">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="51dd1-242">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="51dd1-242">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="51dd1-243">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-243">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="51dd1-244">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="51dd1-244">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="51dd1-245">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="51dd1-245">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="51dd1-246">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-246">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="51dd1-247">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="51dd1-247">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="51dd1-248">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="51dd1-248">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="51dd1-249">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-249">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="51dd1-250">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="51dd1-250">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="51dd1-251">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="51dd1-251">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="51dd1-252">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="51dd1-252">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="51dd1-253">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="51dd1-253">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
