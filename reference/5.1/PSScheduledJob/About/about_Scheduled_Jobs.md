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
# <a name="about-scheduled-jobs"></a>예약 된 작업 정보

## <a name="short-description"></a>간단한 설명

예약 된 작업에 대해 설명 하 고 PowerShell 및 작업 스케줄러에서 예약 된 작업을 사용 하 고 관리 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 예약 된 작업은 PowerShell 백그라운드 작업 및 작업 스케줄러 작업의 유용한 하이브리드입니다.

PowerShell 백그라운드 작업과 마찬가지로 예약 된 작업은 백그라운드에서 비동기적으로 실행 됩니다. 실행 된 예약 된 작업의 인스턴스는 작업 cmdlet (예:,, 및)을 사용 하 여 관리할 수 있습니다 `Start-Job` `Get-Job` `Stop-Job` `Receive-Job` .

작업 스케줄러 작업과 마찬가지로 예약 된 작업은 디스크에 저장 됩니다. 작업 스케줄러에서 작업을 보고 관리 하 고, 필요에 따라 사용/사용 하지 않도록 설정 하거나, 작업을 실행 하거나 템플릿으로 사용 하거나, 작업 시작을 위한 일회성 또는 되풀이 일정을 설정 하거나, 작업 시작 조건을 설정할 수 있습니다.

또한 예약 된 작업 인스턴스의 결과는 쉽게 액세스할 수 있는 형식으로 디스크에 저장 되므로 실행 중인 작업 출력 로그를 제공 합니다. 예약 된 작업은 관리를 위해 사용자 지정 된 cmdlet 집합과 함께 제공 됩니다. Cmdlet을 사용 하 여 예약 된 작업, 작업 트리거 및 작업 옵션을 만들고, 편집 하 고, 관리 하 고, 사용 하지 않도록 설정할 수 있습니다.

이러한 광범위 하 고 유연한 도구 집합은 많은 전문 PowerShell IT 솔루션의 필수 구성 요소로 예약 된 작업을 수행 합니다.

예약 된 작업 cmdlet은 PowerShell과 함께 설치 되는 **PSScheduledJob** 모듈에 포함 됩니다. 이 모듈은 powershell 3.0에서 도입 되었으며 powershell 3.0 이상 버전에서 작동 합니다. **PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.

PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조 하세요.

작업 스케줄러에 대 한 자세한 내용은 [작업 스케줄러](/windows/desktop/TaskSchd/task-scheduler-reference)을 참조 하세요.

> [!NOTE]
> 작업 스케줄러에서 PowerShell 예약 된 작업을 보고 관리할 수 있습니다. Powershell 작업 및 예약 된 작업 cmdlet은 PowerShell에서 만든 예약 된 작업에 대해서만 작동 합니다.

## <a name="quick-start"></a>빠른 시작

이 예에서는 매일 오전 3:00에 시작 하 고 cmdlet을 실행 하는 예약 된 작업을 만듭니다 `Get-Process` . 컴퓨터가 배터리로 실행 되는 경우에도 작업이 시작 됩니다.

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

`Get-ScheduledJob`Cmdlet은 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

`Get-JobTrigger`**processjob** 의 작업 트리거를 가져옵니다. 트리거가 예약 된 작업에 저장 되기 때문에 입력 매개 변수는 트리거가 아니라 예약 된 작업을 지정 합니다.

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

이 예에서는 cmdlet의 **ContinueIfGoingOnBattery** 매개 변수를 사용 하 여 `Set-ScheduledJob` **processjob** 의 **StopIfGoingOnBatteries** 속성을 **False** 로 변경 합니다.

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

`Get-ScheduledJob`Cmdlet은 **processjob** 예약 된 작업을 가져옵니다.

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

`Get-Job`Cmdlet은 지금까지 실행 된 **processjob** 예약 된 작업의 모든 인스턴스를 가져옵니다. `Get-Job`Cmdlet은 **PSScheduledJob** 모듈을 현재 세션으로 가져올 때만 예약 된 작업을 가져옵니다.

> [!TIP]
> 예약 된 작업 cmdlet을 사용 하 여 예약 된 작업을 관리 하지만 작업 cmdlet을 사용 하 여 예약 된 작업의 인스턴스를 관리 하는 것을 알 수 있습니다.

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

`Receive-Job`Cmdlet은 **processjob** 예약 된 작업의 가장 최근 인스턴스 (ID = 51)의 결과를 가져옵니다.

```powershell
Receive-Job -ID 51
```

`Receive-Job`명령이 **Keep** 매개 변수를 포함 하지 않은 경우에도 삭제 하거나 최대 결과 수를 초과할 때까지 작업 결과가 디스크에 저장 됩니다.

작업 결과는이 세션에서 더 이상 사용할 수 없지만, 새 세션을 시작 하거나 새 PowerShell 창을 열 경우 작업 결과를 다시 사용할 수 있습니다.

다음 명령은 cmdlet의 **Definitionname** 매개 변수를 사용 하 여 `Start-Job` **processjob** 예약 된 작업을 시작 합니다.

Cmdlet을 사용 하 여 시작 하는 작업 `Start-Job` 은 예약 된 작업의 인스턴스가 아닌 표준 PowerShell 백그라운드 작업입니다. 모든 백그라운드 작업과 마찬가지로, 이러한 작업은 즉시 시작 되 고 작업 옵션이 나 작업 트리거의 영향을 받지 않으며, 해당 출력은 예약 된 작업 디렉터리의 출력 디렉터리에 저장 되지 않습니다.

```powershell
Start-Job -DefinitionName ProcessJob
```

`Unregister-ScheduledJob`Cmdlet은 **processjob** 예약 된 작업과 해당 작업 인스턴스의 모든 저장 된 결과를 삭제 합니다.

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a>예약 된 작업 개념

예약 된 작업은 명령 또는 스크립트를 실행 합니다. 예약 된 작업에는 작업을 시작 하는 작업 트리거와 작업 실행을 위한 조건을 설정 하는 작업 옵션이 포함 될 수 있습니다.

작업 트리거는 예약 된 작업을 자동으로 시작 합니다. 작업 트리거는 일회성 또는 되풀이 일정을 포함 하거나 사용자가 로그온 하거나 Windows가 시작 되는 경우와 같은 이벤트를 지정할 수 있습니다. 예약 된 작업에는 하나 이상의 작업 트리거가 있을 수 있으며, 작업 트리거를 만들고, 추가 하 고, 활성화 하 고, 사용 하지 않도록 설정 하 고, 가져올 수 있습니다.

작업 트리거는 선택 사항입니다. `Start-Job cmdlet`를 사용 하거나 명령에 **runnow** 매개 변수를 추가 하 여 예약 된 작업을 즉시 시작할 수 있습니다 `Register-ScheduledJob` .

작업 옵션은 예약 된 작업을 실행 하는 조건을 설정 합니다. 모든 예약 된 작업에는 하나의 작업 옵션 개체가 있습니다. 작업 옵션 개체를 만들고 편집 하 여 하나 이상의 예약 된 작업에 추가할 수 있습니다.

예약 된 작업이 시작 될 때마다 작업 인스턴스가 생성 됩니다. PowerShell 작업 cmdlet을 사용 하 여 작업 인스턴스를 보고 관리할 수 있습니다.

예약 된 작업은 디스크에 저장 되 고 대신 cmdlet 동사를 사용 `Register` `New` 합니다. XML 파일은 로컬 컴퓨터의 디렉터리에 있습니다 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .

PowerShell은 예약 된 각 작업에 대 한 디렉터리를 만들고 작업 명령, 작업 트리거, 작업 옵션 및 작업 결과를 예약 된 작업 디렉터리에 저장 합니다. 작업 트리거 및 작업 옵션은 독립적으로 디스크에 저장 되지 않습니다.
이러한 작업은 연결 된 각 예약 된 작업의 예약 된 작업 XML에 저장 됩니다.

예약 된 작업, 작업 트리거 및 작업 옵션은 PowerShell에서 개체로 표시 됩니다.
개체는 interlinked 이며 명령 및 스크립트에서 쉽게 검색 하 고 사용할 수 있습니다.

예약 된 작업은 **ScheduledJobDefinition** 개체로 표시 됩니다. **ScheduledJobDefinition** 개체에는 예약 된 작업의 작업 트리거 및 작업 옵션을 포함 하는 **options** 속성이 포함 된 **jobtriggers** 속성이 있습니다. 작업 트리거 및 작업 옵션을 나타내는 **ScheduledJobTriggers** 및 **ScheduledJobOptions** 개체는 각각 연결 된 예약 된 작업을 포함 하는 **JobDefinition** 속성을 가집니다. 이 재귀 연결을 사용 하면 예약 된 작업의 트리거와 옵션을 쉽게 찾고, 작업 트리거 또는 작업 옵션이 연결 된 예약 된 작업을 찾고 스크립팅 하 고 표시할 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet

[작업 Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference)
