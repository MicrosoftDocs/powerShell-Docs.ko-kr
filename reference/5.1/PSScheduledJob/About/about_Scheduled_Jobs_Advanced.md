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
# <a name="about-scheduled-jobs-advanced"></a>예약 된 작업에 대 한 고급 정보

## <a name="short-description"></a>간단한 설명

예약된 작업의 기본이 되는 파일 구조를 비롯하여 예약된 고급 작업 항목에 대해 설명합니다.

## <a name="long-description"></a>자세한 설명입니다.

**PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.

## <a name="scheduled-job-directories-and-files"></a>예약 된 작업 디렉터리 및 파일

PowerShell 예약 된 작업은 둘 다 PowerShell 작업 및 작업 스케줄러 작업입니다.
각 예약 된 작업은 작업 스케줄러에 등록 되 고 Microsoft .NET Framework 직렬화 XML 형식으로 디스크에 저장 됩니다.

예약 된 작업을 만들 때 PowerShell은 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 로컬 컴퓨터의 디렉터리에 예약 된 작업에 대 한 디렉터리를 만듭니다. 디렉터리 이름은 작업 이름과 동일 합니다.

다음은 샘플 **ScheduledJobs** 디렉터리입니다.

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

각 예약 된 작업에는 고유한 디렉터리가 있습니다. 디렉터리에는 예약 된 작업 XML 파일과 **출력** 하위 디렉터리가 포함 되어 있습니다.

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

예약 된 작업의 **출력** 디렉터리에는 실행 기록이 포함 됩니다.
작업 트리거가 예약 된 작업을 시작할 때마다 PowerShell은 출력 디렉터리에 타임 스탬프 라는 디렉터리를 만듭니다. Timestamp 디렉터리는 **Results.xml** 파일의 작업 결과와 **Status.xml** 파일의 작업 상태를 포함 합니다.

다음 명령은 **processjob** 예약 된 작업에 대 한 실행 기록 디렉터리를 보여 줍니다.

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

**ScheduledJobDefinition.xml** , **Results.xml** 및 **Status.xml** 파일을 열고 검사 하거나 cmdlet을 사용 하 여 `Select-XML` 파일을 구문 분석할 수 있습니다.

> [!WARNING]
> XML 파일을 편집 하지 마십시오. XML 파일에 잘못 된 XML이 포함 된 경우 PowerShell은 작업 결과를 포함 하 여 예약 된 작업 및 해당 실행 기록을 삭제 합니다.

## <a name="start-a-scheduled-job-immediately"></a>예약 된 작업 즉시 시작

다음 두 가지 방법 중 하나를 수행 하 여 예약 된 작업을 즉시 시작할 수 있습니다.

- Cmdlet을 실행 `Start-Job` 하 여 예약 된 작업을 시작 합니다.
- 명령이 실행 되는 즉시 작업을 시작 하려면 **Runnow** 매개 변수를 명령에 추가 `Register-ScheduledJob` 합니다.

Cmdlet을 사용 하 여 시작 하는 작업 `Start-Job` 은 예약 된 작업의 인스턴스가 아닌 표준 PowerShell 백그라운드 작업입니다. 모든 백그라운드 작업과 마찬가지로, 이러한 작업은 즉시 시작 되며, 작업 옵션이 나 작업 트리거의 영향을 받지 않습니다. 작업 출력은 예약 된 작업 디렉터리의 **출력** 디렉터리에 저장 되지 않습니다.

다음 명령은 cmdlet의 **Definitionname** 매개 변수를 사용 하 여 `Start-Job` processjob 예약 된 작업을 시작 합니다.

```powershell
Start-Job -DefinitionName ProcessJob
```

작업을 관리 하 고 작업 결과를 가져오려면 작업 cmdlet을 사용 합니다. 작업 cmdlet에 대 한 자세한 내용은 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조 하세요.

> [!NOTE]
> 예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다. **PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.

## <a name="rename-a-scheduled-job"></a>예약 된 작업 이름 바꾸기

예약 된 작업의 이름을 바꾸려면 cmdlet의 Name 매개 변수를 사용 합니다 `Set-ScheduledJob` . 예약 된 작업의 이름을 바꾸면 PowerShell에서 예약 된 작업의 이름과 예약 된 작업 디렉터리를 변경 합니다. 그러나 이미 실행 된 예약 된 작업 인스턴스의 이름은 변경 되지 않습니다.

## <a name="get-start-and-end-times"></a>시작 및 종료 시간 가져오기

작업 인스턴스의 시작 및 종료 날짜와 시간을 가져오려면 예약 된 작업에 대해 반환 되는 Set-scheduledjob 개체의 **Psbegintime** 및 **psendtime** 속성을 사용 합니다 `Get-Job` .

다음 예에서는 cmdlet의 **Property** 매개 변수를 사용 하 여 `Format-Table` 각 작업 인스턴스의 **Psbegintime** 및 **psendtime** 속성을 테이블에 표시 합니다. **레이블** 이라는 계산 된 속성은 각 작업 인스턴스의 경과 된 시간을 표시 합니다.

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

## <a name="manage-execution-history"></a>실행 기록 관리

예약 된 각 작업에 대해 저장 되는 작업 인스턴스 결과의 수를 확인 하 고 예약 된 작업의 실행 기록과 저장 된 작업 결과를 삭제할 수 있습니다.

예약 된 작업의 **ExecutionHistoryLength** 속성은 예약 된 작업에 대해 저장 되는 작업 인스턴스 결과 수를 결정 합니다. 저장 된 결과 수가 **ExecutionHistoryLength** 속성의 값을 초과할 경우 PowerShell은 가장 오래 된 인스턴스의 결과를 삭제 하 여 최신 인스턴스의 결과를 위한 공간을 만듭니다.

기본적으로 PowerShell은 각 예약 된 작업의 32 인스턴스의 실행 기록과 결과를 저장 합니다. 이 값을 변경 하려면 또는 cmdlet의 **MaxResultCount** 매개 변수를 사용 합니다 `Register-ScheduledJob` `Set-ScheduledJob` .

예약 된 작업에 대 한 실행 기록 및 모든 결과를 삭제 하려면 cmdlet의 **ClearExecutionHistory** 매개 변수를 사용 합니다 `Set-ScheduledJob` . 이 실행 기록을 삭제 해도 PowerShell에서 예약 된 작업의 새 인스턴스 결과를 저장 하는 것은 차단 되지 않습니다.

다음 예에서는 스 플랫를 사용 하 여 `$JobParms` cmdlet에 전달 되는 매개 변수 값을 만듭니다 `Register-ScheduledJob` . 자세한 내용은 [about_Splatting](../../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.
는를 사용 하 여 `Register-ScheduledJob` `@JobParms` 예약 된 작업을 만듭니다. 이 명령은 **MaxResultCount** 매개 변수 값으로 12를 사용 하 여 예약 된 작업의 최신 작업 인스턴스 결과 12 개만 저장 합니다.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

다음 명령은 cmdlet의 **MaxResultCount** 매개 변수를 사용 하 여 `Set-ScheduledJob` 저장 된 인스턴스 결과의 수를 늘립니다.
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

다음 명령은 **processjob** 예약 된 작업의 실행 기록과 현재 저장 된 결과를 삭제 합니다.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

다음 명령은 컴퓨터에 있는 모든 예약 된 작업의 name 및 **ExecutionHistoryLength** 속성 값을 가져와 테이블에 표시 합니다.

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a>참고 항목

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet

[작업 Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference)
