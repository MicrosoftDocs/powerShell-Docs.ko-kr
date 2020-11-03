---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213401"
---
# <span data-ttu-id="3c2b5-103">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-103">Set-JobTrigger</span></span>

## <span data-ttu-id="3c2b5-104">개요</span><span class="sxs-lookup"><span data-stu-id="3c2b5-104">SYNOPSIS</span></span>
<span data-ttu-id="3c2b5-105">예약된 작업의 작업 트리거를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-105">Changes the job trigger of a scheduled job.</span></span>

## <span data-ttu-id="3c2b5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3c2b5-106">SYNTAX</span></span>

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="3c2b5-107">설명</span><span class="sxs-lookup"><span data-stu-id="3c2b5-107">DESCRIPTION</span></span>
<span data-ttu-id="3c2b5-108">**Set-JobTrigger** cmdlet은 예약된 작업의 작업 트리거 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-108">The **Set-JobTrigger** cmdlet changes the properties of the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="3c2b5-109">이 cmdlet을 사용하여 작업이 시작되는 시간 또는 빈도를 변경하거나 시간 기반 일정에서 로그온 또는 시작에 의해 트리거되는 일정으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-109">You can use it to change the time or frequency at which the jobs start or to change from a time-based schedules to schedules that are triggered by a logon or startup.</span></span>

<span data-ttu-id="3c2b5-110">작업 트리거는 예약 된 작업을 시작 하기 위한 되풀이 일정 또는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-110">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="3c2b5-111">작업 트리거는 디스크에 저장되지 않지만 디스크에 저장된 예약된 작업의 작업 트리거를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-111">Although job triggers are not saved to disk, you can change the job triggers of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="3c2b5-112">예약 된 작업의 작업 트리거를 변경 하려면 먼저 Get-JobTrigger cmdlet을 사용 하 여 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-112">To change a job trigger of a scheduled job, begin by using the Get-JobTrigger cmdlet to get the job trigger of a scheduled job.</span></span>
<span data-ttu-id="3c2b5-113">그런 다음 트리거를 **Set-JobTrigger** 로 파이프하거나 변수에 저장하고 *Set-JobTrigger* cmdlet의 **InputObject** 매개 변수를 사용하여 트리거를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-113">Then, pipe the trigger to **Set-JobTrigger** or save the trigger in a variable and use the *InputObject* parameter of **Set-JobTrigger** cmdlet to identify the trigger.</span></span>
<span data-ttu-id="3c2b5-114">**Set-JobTrigger** 의 나머지 매개 변수를 사용하여 작업 트리거를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-114">Use the remaining parameters of **Set-JobTrigger** to change the job trigger.</span></span>

<span data-ttu-id="3c2b5-115">작업 트리거의 유형을 변경 하는 경우 (예: 매일 또는 매주 트리거에서 *Atlogon* 트리거로 작업 트리거를 변경 하는 경우) 원래 트리거 속성이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-115">When you change the type of a job trigger, such as changing a job trigger from a daily or weekly trigger to an *AtLogon* trigger, the original trigger properties are deleted.</span></span>
<span data-ttu-id="3c2b5-116">그러나 트리거 값만 변경하고 유형을 변경하지 않을 경우(예: 주별 트리거의 요일 변경) 지정한 속성만 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-116">However, if you change the values of the trigger, but not its type, such as changing the days in a weekly trigger, only the properties that you specify are changed.</span></span>
<span data-ttu-id="3c2b5-117">원래 작업 트리거의 다른 모든 속성은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-117">All other properties of the original job trigger are retained.</span></span>

<span data-ttu-id="3c2b5-118">**Set JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-118">**Set-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="3c2b5-119">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="3c2b5-120">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*`  하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*`  or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="3c2b5-121">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3c2b5-122">예제</span><span class="sxs-lookup"><span data-stu-id="3c2b5-122">EXAMPLES</span></span>

### <span data-ttu-id="3c2b5-123">예제 1: 작업 트리거의 날짜 변경</span><span class="sxs-lookup"><span data-stu-id="3c2b5-123">Example 1: Change the days in a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

<span data-ttu-id="3c2b5-124">이 예제에서는 주별 작업 트리거의 요일을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-124">This example shows how to change the days in a weekly job trigger.</span></span>

<span data-ttu-id="3c2b5-125">첫 번째 명령은 Get-JobTrigger cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-125">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="3c2b5-126">출력은 트리거가 수요일과 토요일마다 자정에 작업을 시작함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-126">The output shows that the trigger starts the job at midnight on Wednesdays and Saturdays.</span></span>

<span data-ttu-id="3c2b5-127">이 명령은 필수가 아닙니다. 단지 트리거 변경의 결과를 보여 주기 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-127">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="3c2b5-128">예 2: 작업 트리거 형식 변경</span><span class="sxs-lookup"><span data-stu-id="3c2b5-128">Example 2: Change the job trigger type</span></span>

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

<span data-ttu-id="3c2b5-129">이 예제에서는 작업을 시작하는 작업 트리거의 유형을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-129">This example shows how to change the type of job trigger that starts a job.</span></span>
<span data-ttu-id="3c2b5-130">이 예제의 명령은 AtStartup 작업 트리거를 주별 트리거로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-130">The commands in this example replace an AtStartup job trigger with a weekly trigger.</span></span>

<span data-ttu-id="3c2b5-131">첫 번째 명령은 Get-JobTrigger cmdlet을 사용 하 여 Inventory 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-131">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the Inventory scheduled job.</span></span>
<span data-ttu-id="3c2b5-132">출력은 작업에 매일 트리거와 *Atstartup* 트리거의 두 트리거가 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-132">The output shows that the job has two triggers a daily trigger and an *AtStartup* trigger.</span></span>

<span data-ttu-id="3c2b5-133">이 명령은 필수가 아닙니다. 단지 트리거 변경의 결과를 보여 주기 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-133">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="3c2b5-134">예 3: 원격 작업 트리거의 사용자 변경</span><span class="sxs-lookup"><span data-stu-id="3c2b5-134">Example 3: Change the user on a remote job trigger</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

<span data-ttu-id="3c2b5-135">이 명령은 Server01 컴퓨터에서 예약 된 작업의 모든 *Atlogon* 작업 트리거에 있는 사용자를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-135">This command changes the user in all *AtLogon* job triggers of scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="3c2b5-136">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-136">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="3c2b5-137">원격 명령은 컴퓨터의 모든 예약 된 작업을 가져오는 Get-ScheduledJob 명령으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-137">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="3c2b5-138">예약 된 작업은 Get-JobTrigger cmdlet으로 파이프 되며, 예약 된 작업의 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-138">The scheduled jobs are piped to the Get-JobTrigger cmdlet, which gets the job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="3c2b5-139">각 작업 트리거에는 예약된 작업을 포함하는 JobDefinition 속성이 있으므로 트리거가 변경된 경우에도 예약된 작업과 연결된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-139">Each job trigger contains a JobDefinition property that contains the scheduled job, so the trigger remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="3c2b5-140">작업 트리거는 사용자 속성이 있는 작업 트리거를 가져오는 Where-Object cmdlet으로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-140">The job triggers are piped to the Where-Object cmdlet, which gets job triggers that have the User property.</span></span>
<span data-ttu-id="3c2b5-141">선택한 작업 트리거가 **Set-JobTrigger** cmdlet으로 파이프되면 이 cmdlet이 사용자를 Domain01\Admin02로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-141">The selected job triggers are piped to the **Set-JobTrigger** cmdlet, which changes the user to Domain01\Admin02.</span></span>

### <span data-ttu-id="3c2b5-142">예제 4: 여러 작업 트리거 중 하나 변경</span><span class="sxs-lookup"><span data-stu-id="3c2b5-142">Example 4: Change one of many job triggers</span></span>

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="3c2b5-143">이 예제의 명령은 SecurityCheck 예약된 작업의 *Once* 작업 트리거 되풀이 간격을 60분에서 90분으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-143">The commands in this example changes the repetition interval of the *Once* job trigger of SecurityCheck scheduled job from every 60 minutes to every 90 minutes.</span></span>
<span data-ttu-id="3c2b5-144">SecurityCheck 예약 된 작업에는 세 개의 작업 트리거가 있으므로 명령은 Get-JobTrigger cmdlet의 *TriggerId* 매개 변수를 사용 하 여 변경할 작업 트리거를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-144">The SecurityCheck scheduled job has three job triggers, so the commands use the *TriggerId* parameter of the Get-JobTrigger cmdlet to identify the job trigger that is being changed.</span></span>

<span data-ttu-id="3c2b5-145">첫 번째 명령은 **Get-JobTrigger** cmdlet을 사용하여 SecurityCheck 예약된 작업의 모든 작업 트리거를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-145">The first command uses the **Get-JobTrigger** cmdlet to get all job triggers of the SecurityCheck scheduled job.</span></span>
<span data-ttu-id="3c2b5-146">작업 트리거의 ID를 표시하는 출력은 *Once* 작업 트리거의 ID가 3임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-146">The output, which displays the IDs of the job triggers, reveals that the *Once* job trigger has an ID of 3.</span></span>

## <span data-ttu-id="3c2b5-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c2b5-147">PARAMETERS</span></span>

### <span data-ttu-id="3c2b5-148">-At</span><span class="sxs-lookup"><span data-stu-id="3c2b5-148">-At</span></span>
<span data-ttu-id="3c2b5-149">지정한 날짜 및 시간에 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-149">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="3c2b5-150">Get-Date cmdlet에서 반환 하는 것과 같은 **DateTime** 개체를 입력 하거나 시간으로 변환할 수 있는 문자열 (예: "4 월 19 일 2012 15:00", "12/31/2013 9:00 PM" 또는 "3am")을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-150">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a time, such as "April 19, 2012 15:00", "12/31/2013 9:00 PM", or "3am".</span></span>

<span data-ttu-id="3c2b5-151">**DateTime** 개체의 요소 (예: 초)를 지정 하지 않으면 작업 트리거의 해당 요소는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-151">If you don't specify an element of the **DateTime** object, such as seconds, that element of the job trigger is not changed.</span></span>
<span data-ttu-id="3c2b5-152">원래 작업 트리거에 **DateTime** 개체가 포함 되어 있지 않은 상태에서 요소를 생략 하면 현재 날짜 및 시간에서 해당 요소로 작업 트리거가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-152">If the original job trigger didn't include a **DateTime** object and you omit an element, the job trigger is created with the corresponding element from the current date and time.</span></span>

<span data-ttu-id="3c2b5-153">*Once* 매개 변수를 사용할 경우 *At* 매개 변수 값을 특정 날짜와 시간으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-153">When using the *Once* parameter, set the value of the *At* parameter to a particular date and time.</span></span>
<span data-ttu-id="3c2b5-154">**DateTime** 개체의 기본 날짜는 현재 날짜이기 때문에 명시적 날짜 없이 현재 시간 이전의 시간을 설정할 경우 과거 시간에 대한 작업 트리거가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-154">Because the default date in a **DateTime** object is the current date, setting a time before the current time without an explicit date results in a job trigger for a time in the past.</span></span>

<span data-ttu-id="3c2b5-155">Datetime **개체와** **datetime** 개체로 변환 되는 문자열은 제어판의 지역 및 언어에서 로컬 컴퓨터에 대해 선택한 날짜 및 시간 형식과 호환 되도록 자동으로 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-155">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c2b5-156">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="3c2b5-156">-AtLogOn</span></span>
<span data-ttu-id="3c2b5-157">지정한 사용자가 컴퓨터에 로그온할 때 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-157">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="3c2b5-158">사용자를 지정하려면 *User* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-158">To specify a user, use the *User* parameter.</span></span>

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

### <span data-ttu-id="3c2b5-159">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="3c2b5-159">-AtStartup</span></span>
<span data-ttu-id="3c2b5-160">Windows가 시작될 때 예약된 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-160">Starts the scheduled job when Windows starts.</span></span>

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

### <span data-ttu-id="3c2b5-161">-매일</span><span class="sxs-lookup"><span data-stu-id="3c2b5-161">-Daily</span></span>
<span data-ttu-id="3c2b5-162">매일 되풀이되는 작업 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-162">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="3c2b5-163">*매일* 매개 변수 집합의 다른 매개 변수를 사용 하 여 일정 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-163">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="3c2b5-164">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="3c2b5-164">-DaysInterval</span></span>
<span data-ttu-id="3c2b5-165">일별 일정의 발생 간격(일)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-165">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="3c2b5-166">예를 들어 값이 3이면 예약된 작업이 1, 4, 7일 등에 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-166">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="3c2b5-167">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-167">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c2b5-168">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="3c2b5-168">-DaysOfWeek</span></span>
<span data-ttu-id="3c2b5-169">주별 예약된 작업이 실행되는 요일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-169">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="3c2b5-170">요일 이름 (예: 월요일, 목요일, 정수 0-6)을 입력 합니다. 여기서 0은 일요일을 나타내고, 별표 ()는 매일을 나타냅니다 \* .</span><span class="sxs-lookup"><span data-stu-id="3c2b5-170">Enter day names, such as Monday, Thursday, integers 0-6, where 0 represents Sunday, or an asterisk (\*) to represent every day.</span></span>
<span data-ttu-id="3c2b5-171">이 매개 변수는 Weekly 매개 변수 집합에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-171">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="3c2b5-172">요일 이름은 작업 트리거에서 해당 정수 값으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-172">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="3c2b5-173">명령에서 요일 이름을 따옴표로 묶을 경우 "Monday", "Tuesday"와 같이 각 요일 이름을 별도의 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-173">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="3c2b5-174">여러 요일 이름을 하나의 따옴표 쌍으로 묶으면 해당 정수 값이 합산됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-174">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="3c2b5-175">예를 들어 "Monday, Tuesday"(1, 2)는 "Wednesday"(3) 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-175">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c2b5-176">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3c2b5-176">-InputObject</span></span>
<span data-ttu-id="3c2b5-177">작업 트리거를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-177">Specifies the job triggers.</span></span>
<span data-ttu-id="3c2b5-178">**ScheduledJobTrigger** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-178">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="3c2b5-179">**ScheduledJobTrigger** 개체를 **설정-jobtrigger** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-179">You can also pipe a **ScheduledJobTrigger** object to **Set-JobTrigger** .</span></span>

<span data-ttu-id="3c2b5-180">여러 개의 작업 트리거를 지정할 경우 **Set-JobTrigger** 는 모든 작업 트리거에 동일한 변경을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-180">If you specify multiple job triggers, **Set-JobTrigger** makes the same changes to all job triggers.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3c2b5-181">-한 번</span><span class="sxs-lookup"><span data-stu-id="3c2b5-181">-Once</span></span>
<span data-ttu-id="3c2b5-182">되풀이되지 않는(일회성) 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-182">Specifies a non-recurring (one time) schedule.</span></span>

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

### <span data-ttu-id="3c2b5-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="3c2b5-183">-PassThru</span></span>
<span data-ttu-id="3c2b5-184">변경된 작업 트리거를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-184">Returns the job triggers that changed.</span></span>
<span data-ttu-id="3c2b5-185">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-185">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="3c2b5-186">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="3c2b5-186">-RandomDelay</span></span>
<span data-ttu-id="3c2b5-187">예약된 시작 시간에 시작되는 임의 지연을 사용하도록 설정하고 최대 지연 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-187">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="3c2b5-188">지연 길이는 각 시작에 대해 의사 임의로 설정되며 지연 없음에서 이 매개 변수 값으로 지정된 시간까지 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-188">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="3c2b5-189">기본값 0(00:00:00)은 임의 지연을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-189">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="3c2b5-190">New-TimeSpan cmdlet에서 반환 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 timespan 개체로 변환 되는:: format에 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-190">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a timespan object.</span></span>

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

### <span data-ttu-id="3c2b5-191">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="3c2b5-191">-RepeatIndefinitely</span></span>
<span data-ttu-id="3c2b5-192">Windows PowerShell 4.0부터 제공되는 이 매개 변수를 사용하면 예약된 작업을 무기한 동안 되풀이해서 실행하기 위해 **RepetitionDuration** 매개 변수에 *TimeSpan.MaxValue* 값을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-192">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

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

### <span data-ttu-id="3c2b5-193">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="3c2b5-193">-RepetitionDuration</span></span>
<span data-ttu-id="3c2b5-194">지정한 시간이 만료될 때까지 작업을 되풀이합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-194">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="3c2b5-195">되풀이 빈도는 *RepetitionInterval* 매개 변수 값에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-195">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="3c2b5-196">예를 들어 **RepetitionInterval** 값이 5분이고 *RepetitionDuration* 값이 2시간이면 2시간 동안 5분마다 작업이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-196">For example, if the value of **RepetitionInterval** is 5 minutes and the value of *RepetitionDuration* is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="3c2b5-197">New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-197">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="3c2b5-198">작업을 무기한 실행하려면 *RepeatIndefinitely* 매개 변수를 대신 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-198">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="3c2b5-199">작업 트리거 되풀이 기간이 만료되기 전에 작업을 중지하려면 **RepetitionDuration** 값을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-199">To stop a job before the job trigger repetition duration expires, set the **RepetitionDuration** value to zero (0).</span></span>

<span data-ttu-id="3c2b5-200">*Once* 작업 트리거의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 **RepetitionInterval** 및 **RepetitionDuration** 매개 변수가 둘 다 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-200">To change the repetition duration or repetition interval of a *Once* job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="3c2b5-201">다른 작업 트리거 유형의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 *Once* , *At* , *RepetitionInterval* 및 *RepetitionDuration* 매개 변수가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-201">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the *Once* , *At* , *RepetitionInterval* and *RepetitionDuration* parameters.</span></span>

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

### <span data-ttu-id="3c2b5-202">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="3c2b5-202">-RepetitionInterval</span></span>
<span data-ttu-id="3c2b5-203">지정한 시간 간격에 작업을 되풀이합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-203">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="3c2b5-204">예를 들어 이 매개 변수 값이 2시간이면 2시간마다 작업이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-204">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="3c2b5-205">기본값 0은 작업을 되풀이하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-205">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="3c2b5-206">New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-206">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="3c2b5-207">**Once** 작업 트리거의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 **RepetitionInterval** 및 **RepetitionDuration** 매개 변수가 둘 다 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-207">To change the repetition duration or repetition interval of a **Once** job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="3c2b5-208">다른 작업 트리거 유형의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 **Once** , **At** , **RepetitionInterval** 및 **RepetitionDuration** 매개 변수가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-208">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the **Once** , **At** , **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>

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

### <span data-ttu-id="3c2b5-209">-User</span><span class="sxs-lookup"><span data-stu-id="3c2b5-209">-User</span></span>
<span data-ttu-id="3c2b5-210">예약된 작업의 *AtLogon* 시작을 트리거하는 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-210">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="3c2b5-211">사용자의 이름을 또는 형식으로 입력 \<UserName\> \<Domain\Username\> 하거나 별표 ( \* )를 입력 하 여 모든 사용자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-211">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="3c2b5-212">기본값은 모든 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-212">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c2b5-213">-매주</span><span class="sxs-lookup"><span data-stu-id="3c2b5-213">-Weekly</span></span>
<span data-ttu-id="3c2b5-214">매주 되풀이되는 작업 일정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-214">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="3c2b5-215">*주별* 매개 변수 집합의 다른 매개 변수를 사용 하 여 일정 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-215">Use the other parameters in the *Weekly* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="3c2b5-216">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="3c2b5-216">-WeeksInterval</span></span>
<span data-ttu-id="3c2b5-217">주별 작업 일정의 발생 간격(주)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-217">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="3c2b5-218">예를 들어 값이 3이면 예약된 작업이 1, 4, 7주 등에 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-218">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="3c2b5-219">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-219">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c2b5-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c2b5-220">CommonParameters</span></span>
<span data-ttu-id="3c2b5-221">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c2b5-222">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c2b5-223">입력</span><span class="sxs-lookup"><span data-stu-id="3c2b5-223">INPUTS</span></span>

### <span data-ttu-id="3c2b5-224">Set-scheduledjob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-224">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="3c2b5-225">여러 작업 트리거를 **설정-JobTrigger** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-225">You can pipe multiple job triggers to **Set-JobTrigger** .</span></span>

## <span data-ttu-id="3c2b5-226">출력</span><span class="sxs-lookup"><span data-stu-id="3c2b5-226">OUTPUTS</span></span>

### <span data-ttu-id="3c2b5-227">None 또는 Set-scheduledjob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-227">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="3c2b5-228">*Passthru* 매개 변수를 사용할 경우 **Set-JobTrigger** 은 변경된 작업 트리거를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-228">When you use the *Passthru* parameter, **Set-JobTrigger** returns the job triggers that were changed.</span></span>
<span data-ttu-id="3c2b5-229">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-229">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3c2b5-230">참고</span><span class="sxs-lookup"><span data-stu-id="3c2b5-230">NOTES</span></span>

* <span data-ttu-id="3c2b5-231">작업 트리거에는 작업 트리거를 예약된 작업에 연결하는 JobDefintion 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-231">Job triggers have a JobDefintion property that associates them with the scheduled job.</span></span> <span data-ttu-id="3c2b5-232">예약된 작업의 작업 트리거를 변경하면 작업이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-232">When you change the job trigger of a scheduled job, the job is changed.</span></span> <span data-ttu-id="3c2b5-233">Set-ScheduledJob 명령을 사용 하 여 예약 된 작업에 변경 된 트리거를 적용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c2b5-233">You do not need to use a Set-ScheduledJob command to apply the changed trigger to the scheduled job.</span></span>

## <span data-ttu-id="3c2b5-234">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3c2b5-234">RELATED LINKS</span></span>

[<span data-ttu-id="3c2b5-235">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-235">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="3c2b5-236">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-236">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="3c2b5-237">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3c2b5-237">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="3c2b5-238">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-238">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="3c2b5-239">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3c2b5-239">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="3c2b5-240">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-240">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="3c2b5-241">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3c2b5-241">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="3c2b5-242">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3c2b5-242">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="3c2b5-243">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-243">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="3c2b5-244">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3c2b5-244">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="3c2b5-245">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3c2b5-245">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="3c2b5-246">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-246">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="3c2b5-247">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3c2b5-247">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="3c2b5-248">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3c2b5-248">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="3c2b5-249">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3c2b5-249">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="3c2b5-250">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3c2b5-250">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
