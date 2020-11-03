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
# <a name="about-scheduled-jobs-basics"></a>예약 된 작업 기본 사항 정보

## <a name="short-description"></a>간단한 설명

예약된 작업을 만들고 관리하는 방법에 대해 설명합니다.

## <a name="long-description"></a>자세한 설명입니다.

이 문서에서는 예약 된 작업을 만들고 관리 하는 기본 작업을 수행 하는 방법을 보여 줍니다. 고급 태스크에 대 한 자세한 내용은 [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)를 참조 하세요.

**PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.

## <a name="how-to-create-a-scheduled-job"></a>예약 된 작업을 만드는 방법

예약 된 작업을 만들려면 cmdlet을 사용 `Register-ScheduledJob` 합니다. Cmdlet에는 작업에서 실행 되는 이름 및 명령 또는 스크립트가 필요 합니다. **Runnow** 매개 변수를 추가 하거나 작업 트리거를 만들고 작업을 만들 때 작업 옵션을 설정 하거나 기존 작업을 편집 하 여 작업을 즉시 실행할 수 있습니다.

스크립트를 실행 하는 작업을 만들려면 **FilePath** 매개 변수를 사용 하 여 스크립트 파일의 경로를 지정 합니다. 명령을 실행 하는 작업을 만들려면 **ScriptBlock** 매개 변수를 사용 합니다.

`Register-ScheduledJob`Cmdlet은 명령을 실행 하는 **processjob** 을 만듭니다 `Get-Process` . 이 예약 된 작업에는 기본 작업 옵션이 있으며 작업 트리거는 없습니다.

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a>작업 트리거를 만드는 방법

작업 트리거는 예약 된 작업을 자동으로 시작 합니다. 작업 트리거는 일회성 또는 되풀이 일정 이거나 사용자가 로그온 하거나 Windows가 시작 되는 경우와 같은 이벤트 일 수 있습니다. 각 작업에는 0 개, 1 개 또는 여러 개의 작업 트리거가 있을 수 있습니다.

작업 트리거를 만들려면 cmdlet을 사용 `New-JobTrigger` 합니다. 다음 명령은 월요일과 목요일 오전 5:00에 작업을 시작 하는 작업 트리거를 만듭니다.
이 명령은 작업 트리거를 `$T` 변수에 저장 합니다.

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

작업 트리거는 선택 사항입니다. **Runnow** 매개 변수를 명령에 추가 하거나 cmdlet을 사용 하 여 언제 든 지 예약 된 작업을 시작할 수 있습니다 `Register-ScheduledJob` `Start-Job` .

## <a name="how-to-add-a-job-trigger"></a>작업 트리거를 추가 하는 방법

예약 된 작업에 작업 트리거를 추가 하면 작업 트리거가 예약 된 작업에 대 한 예약 된 작업 XML 파일에 추가 되 고 예약 된 작업의 일부가 됩니다.

예약 된 작업을 만들 때 예약 된 작업에 작업 트리거를 추가 하거나 기존 작업을 편집할 수 있습니다. 언제 든 지 예약 된 작업의 작업 트리거를 변경할 수 있습니다.

PowerShell은 작업 스케줄러에서 사용 하는 것과 동일한 작업 트리거를 사용 합니다. 작업 트리거에 대 한 자세한 내용은 [새-JobTrigger](xref:PSScheduledJob.New-JobTrigger) cmdlet에 대 한 도움말 항목을 참조 하세요.

다음 예에서는 스 플랫를 사용 하 여 `$JobParms` cmdlet에 전달 되는 매개 변수 값을 만듭니다 `Register-ScheduledJob` . 자세한 내용은 [about_Splatting](../../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.
는를 사용 하 여 `Register-ScheduledJob` `@JobParms` 예약 된 작업을 만듭니다. **Trigger** 매개 변수를 사용 하 여 변수에서 작업 트리거를 지정 `$T` 합니다.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

언제 든 지 기존 예약 된 작업에 작업 트리거를 추가할 수도 있습니다. `Add-JobTrigger`Cmdlet은 `$T` **processjob** 예약 된 작업에 변수의 작업 트리거를 추가 합니다.

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

결과적으로 작업 트리거는 월요일과 목요일 오전 5:00 시에 자동으로 **Processjob** 을 시작 합니다.

## <a name="how-to-get-a-job-trigger"></a>작업 트리거를 가져오는 방법

예약 된 작업의 작업 트리거를 가져오려면 cmdlet을 사용 합니다 `Get-JobTrigger` . **Name** , **ID** 및 **InputObject** 매개 변수를 사용 하 여 작업 트리거가 아닌 예약 된 작업을 지정 합니다.

`Get-JobTrigger`**Processjob** 의 작업 트리거를 가져옵니다.

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a>작업 옵션을 만드는 방법

작업 옵션은 작업을 시작 하 고 실행 하는 조건을 설정 합니다. 모든 작업에는 변경 하지 않는 한 기본 작업 옵션이 있습니다. 작업 옵션은 예약 된 시간에 작업이 실행 되는 것을 방지할 수 있으므로 작업 옵션을 이해 하 고 신중 하 게 사용 해야 합니다.

PowerShell은 작업 스케줄러에서 사용 하는 것과 동일한 작업 옵션을 사용 합니다. 작업 옵션에 대 한 자세한 내용은 [set-scheduledjoboption](xref:PSScheduledJob.New-ScheduledJobOption)에 대 한 도움말 항목을 참조 하세요.

작업 옵션은 예약 된 작업 XML 파일에 저장 됩니다. 예약 된 작업을 만들 때 작업 옵션을 설정 하거나 언제 든 지 변경할 수 있습니다.

`New-ScheduledJobOption`Cmdlet은 **WakeToRun** 예약 된 작업 옵션이 True로 설정 된 예약 된 작업 옵션을 만듭니다. **WakeToRun** 옵션은 컴퓨터가 예약 된 시작 시간에 절전 모드 또는 최대 절전 모드에 있는 경우에도 예약 된 작업을 실행 합니다. 이 명령은 작업 옵션을 `$O` 변수에 저장 합니다.

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a>작업 옵션을 가져오는 방법

예약 된 작업의 작업 옵션을 가져오려면 cmdlet을 사용 합니다 `Get-ScheduledJobOption` . **이름** , **ID** 및 **InputObject** 매개 변수를 사용 하 여 작업 옵션이 아닌 예약 된 작업을 지정 합니다.

`Get-ScheduledJobOption`**Processjob** 의 작업 옵션을 가져옵니다.

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

## <a name="how-to-change-job-options"></a>작업 옵션을 변경 하는 방법

예약 된 작업을 만들거나 기존 작업을 편집할 때 예약 된 작업의 작업 옵션을 변경할 수 있습니다.

Splatted는 `$JobParms` cmdlet에 전달 되어 `Add-JobTrigger` 프로세스 작업을 만듭니다. **Set-scheduledjoboption** 매개 변수를 사용 하 여 변수에서 작업 옵션을 지정 `$O` 합니다.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

언제 든 지 기존 예약 된 작업으로 작업 옵션을 변경할 수도 있습니다.
다음 명령은 cmdlet을 사용 하 여 `Set-ScheduledJobOption` **processjob** set-scheduledjob의 **WakeToRun** 옵션 값을 **True** 로 변경 합니다.

`Set`Cmdlet과 같은 **PSScheduledJob** 모듈의 cmdlet은 `Set-ScheduledJobOption` **Name** 또는 **ID** 매개 변수를 사용할 수 없습니다. **InputObject** 매개 변수를 사용 하 여 예약 된 작업 옵션을 지정 하거나 cmdlet에서로 예약 된 작업을 파이프로 파이프 할 수 있습니다 `Get-ScheduledJobOption` `Set-ScheduledJobOption` .

이 예에서는 cmdlet을 사용 하 여 `Get-ScheduledJob` ProcessJob을 가져옵니다. Cmdlet을 사용 하 여 `Get-ScheduledJobOption` **processjob** 의 작업 옵션을 가져오고 cmdlet을 사용 하 여 `Set-ScheduledJobOption` processjob의 **WakeToRun** job 옵션을 True로 변경 합니다.

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a>예약 된 작업 인스턴스를 가져오는 방법

예약 된 작업이 시작 되 면 PowerShell은 표준 PowerShell 백그라운드 작업과 유사한 작업 인스턴스를 만듭니다. 작업 cmdlet (예: 및)을 사용 `Get-Job` `Stop-Job` 하 여 `Receive-Job` 작업 인스턴스를 관리할 수 있습니다.

> [!NOTE]
> 예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다. **PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.

PowerShell 예약 된 작업 및 모든 활성 표준 작업의 모든 인스턴스를 가져오려면 cmdlet을 사용 `Get-Job` 합니다. `Import-Module`Cmdlet은 **PSScheduledJob** 모듈을 가져오고 `Get-Job` 로컬 컴퓨터의 작업을 가져옵니다.

```powershell
Import-Module PSScheduledJob
Get-Job
```

`Get-Job` 로컬 컴퓨터에서 **Processjob** 의 인스턴스를 가져옵니다.

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

기본 표시에는 일반적으로 동일한 예약 된 작업의 인스턴스를 구분 하는 시작 시간이 표시 되지 않습니다.

`Get-Job`Cmdlet은 개체를 파이프라인으로 보냅니다. `Format-Table`Cmdlet은 예약 된 작업의 **이름** , **ID** 및 **begintime** 속성을 표시 합니다.

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

## <a name="get-scheduled-job-results"></a>예약 된 작업 결과 가져오기

예약 된 작업의 인스턴스 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .

> [!NOTE]
> 예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다. **PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.

이 예에서는 **processjob** 예약 된 작업 (ID = 51)의 최신 인스턴스의 결과를 가져옵니다.

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

예약 된 작업의 결과는 디스크에 저장 되므로의 **Keep** 매개 변수는 `Receive-Job` 필요 하지 않습니다. 그러나 **Keep** 매개 변수를 사용 하지 않으면 각 PowerShell 세션에서 예약 된 작업의 결과를 한 번만 가져올 수 있습니다. 새 PowerShell 세션을 시작 하려면 `PowerShell` 새 powershell 창을 입력 하거나 엽니다.

## <a name="see-also"></a>참고 항목

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet

[작업 Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference)
