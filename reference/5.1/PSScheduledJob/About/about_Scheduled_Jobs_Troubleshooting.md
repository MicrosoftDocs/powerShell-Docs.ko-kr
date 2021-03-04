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
# <a name="about-scheduled-jobs-troubleshooting"></a>예약 된 작업에 대 한 문제 해결

## <a name="short-description"></a>간단한 설명

예약 된 작업과 관련 된 문제를 해결 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

이 문서에서는 PowerShell의 예약 된 작업 기능을 사용할 때 발생할 수 있는 몇 가지 문제에 대해 설명 하 고 이러한 문제에 대 한 해결 방법을 제안 합니다.

PowerShell 예약 된 작업을 사용 하기 전에 [about_Scheduled_Jobs](about_Scheduled_Jobs.md) 및 관련 예약 된 작업 항목을 참조 하세요.

**PSScheduledJob** 모듈에 포함 된 cmdlet에 대 한 자세한 내용은 [PSScheduledJob](xref:PSScheduledJob)를 참조 하세요.

## <a name="cant-find-job-results"></a>작업 결과를 찾을 수 없음

### <a name="basic-method-for-getting-job-results-in-powershell"></a>PowerShell에서 작업 결과를 가져오는 기본 방법

예약 된 작업이 실행 되 면 예약 된 작업의 인스턴스를 만듭니다. 예약 된 작업 인스턴스의 결과를 보고 관리 하 고 얻으려면 작업 cmdlet을 사용 합니다.

> [!NOTE]
> 예약 된 작업의 인스턴스에서 작업 cmdlet을 사용 하려면 **PSScheduledJob** 모듈을 세션으로 가져와야 합니다. **PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` 와 같은 예약 된 작업 cmdlet을 입력 하거나 사용 `Get-ScheduledJob` 합니다.

예약 된 작업의 모든 인스턴스 목록을 가져오려면 cmdlet을 사용 합니다 `Get-Job` .

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

`Get-Job`Cmdlet은 **processjob** 개체를 파이프라인 아래로 보냅니다. `Format-Table`Cmdlet은 예약 된 작업 인스턴스의 **Name**, **ID** 및 **psbegintime** 속성을 테이블에 표시 합니다.

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

예약 된 작업의 인스턴스 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` . 다음 명령은 ProcessJob의 최신 인스턴스 (ID = 50)의 결과를 가져옵니다.

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a>디스크에서 작업 결과를 찾는 기본 방법

예약 된 작업을 관리 하려면 및와 같은 작업 cmdlet을 `Get-Job` 사용 `Receive-Job` 합니다.

`Get-Job`에서 작업 인스턴스를 가져오지 않거나 `Receive-Job` 작업 결과를 얻지 못하는 경우 디스크에서 작업에 대 한 실행 기록 파일을 검색할 수 있습니다.
실행 기록은 모든 트리거된 작업 인스턴스의 레코드를 포함 합니다.

다음 경로에서 예약 된 작업에 대 한 디렉터리에 타임 스탬프 이름 디렉터리가 있는지 확인 합니다.

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

다음은 그 예입니다. 

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

예를 들어 `Get-ChildItem` cmdlet은 **processjob** 예약 된 작업의 디스크에 있는 실행 기록을 가져옵니다.

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

각 타임 스탬프 명명 디렉터리는 작업 인스턴스를 나타냅니다. 각 작업 인스턴스의 결과는 타임 스탬프 명명 디렉터리의 **Results.xml** 파일에 저장 됩니다.

예를 들어 다음 명령은 **processjob** 예약 된 작업의 저장 된 모든 인스턴스에 대 한 **Results.xml** 파일을 가져옵니다. **Results.xml** 파일이 없으면 PowerShell에서 작업 결과를 반환 하거나 표시할 수 없습니다.

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

**PSScheduledJob** 모듈을 세션으로 가져오지 않았으므로 작업 cmdlet이 예약 된 작업 인스턴스 또는 해당 결과를 가져오지 못할 수 있습니다.

> [!NOTE]
> 예약 된 작업 인스턴스에 작업 cmdlet을 사용 하기 전에 **PSScheduledJob** 모듈이 세션에 포함 되어 있는지 확인 합니다. **PSScheduledJob** 모듈이 없으면 작업 cmdlet은 예약 된 작업 인스턴스 또는 해당 결과를 가져올 수 없습니다.

**PSScheduledJob** 모듈을 가져오려면 다음을 수행 합니다.

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a>Receive-Job cmdlet은 이미 결과를 반환 했을 수 있습니다.

`Receive-Job`에서 작업 인스턴스 결과를 반환 하지 않는 경우에는 `Receive-Job` **Keep** 매개 변수 없이 현재 세션에서 해당 작업 인스턴스에 대해 명령을 실행 했기 때문일 수 있습니다.

`Receive-Job` **Keep** 매개 변수 없이를 사용 하는 경우 `Receive-Job` 은 작업 결과를 반환 하 고 작업 인스턴스의 **HasMoreData** 속성을 **False** 로 설정 합니다. **False** 값은 `Receive-Job` 작업의 결과를 반환 했 고 인스턴스에 반환할 결과가 더 이상 없음을 의미 합니다. 이 설정은 표준 백그라운드 작업에 적합 하지만, 디스크에 저장 된 예약 된 작업의 인스턴스에는 적합 하지 않습니다.

작업 인스턴스 결과를 다시 가져오려면를 입력 하 여 새 PowerShell 세션을 시작 `PowerShell` 합니다. **PSScheduledJob** 모듈을 가져온 후 `Receive-Job` 명령을 다시 시도 하십시오.

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

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a>Keep 매개 변수를 사용 하 여 세션에서 두 번 이상 결과 가져오기

세션에서 작업 인스턴스의 결과를 두 번 이상 가져오려면 cmdlet의 **Keep** 매개 변수를 사용 합니다 `Receive-Job` .

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

### <a name="the-scheduled-job-might-be-corrupted"></a>예약 된 작업이 손상 되었을 수 있습니다.

예약 된 작업이 손상 되 면 PowerShell은 손상 된 예약 된 작업 및 해당 결과를 삭제 합니다. 손상 된 예약 된 작업의 결과를 복구할 수 없습니다.

예약 된 작업이 아직 있는지 확인 하려면 cmdlet을 사용 `Get-ScheduledJob` 합니다.

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a>결과 수가 ExecutionHistoryLength을 초과 했을 수 있습니다.

예약 된 작업의 **ExecutionHistoryLength** 속성은 디스크에 저장 되는 작업 인스턴스 수 및 해당 결과를 결정 합니다. 기본값은 32입니다.
예약 된 작업의 인스턴스 수가이 값을 초과 하면 PowerShell은 가장 오래 된 작업 인스턴스를 삭제 하 여 각각의 새 작업 인스턴스를 위한 공간을 만듭니다.

예약 된 작업의 **ExecutionHistoryLength** 속성 값을 가져오려면 다음 명령 형식을 사용 합니다.

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

예를 들어 다음 명령은 **processjob** 예약 된 작업의 **ExecutionHistoryLength** 속성 값을 가져옵니다.

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

**ExecutionHistoryLength** 속성의 값을 설정 하거나 변경 하려면 및 Cmdlet의 **MaxResultCount** 매개 변수를 사용 `Register-ScheduledJob` 합니다 `Set-ScheduledJob` .

다음 명령은 **ExecutionHistoryLength** 속성의 값을 50로 늘립니다.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a>작업 인스턴스 결과가 삭제 되었을 수 있습니다.

Cmdlet의 **ClearExecutionHistory** 매개 변수는 `Set-ScheduledJob` 작업의 실행 기록을 삭제 합니다. 이 기능을 사용 하 여 디스크 공간을 확보 하거나 필요 하지 않거나 이미 사용, 분석 또는 다른 위치에 저장 된 결과를 삭제할 수 있습니다.

예약 된 작업의 실행 기록을 삭제 하려면 예약 된 작업의 **ClearExecutionHistory** 매개 변수를 사용 합니다.

다음 명령은 **processjob** 예약 된 작업의 실행 기록을 삭제 합니다.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

또한 cmdlet은 `Remove-Job` 작업 결과를 삭제 합니다. 를 사용 하 여 `Remove-Job` 예약 된 작업을 삭제 하면 실행 기록과 모든 작업 결과를 포함 하 여 디스크에 있는 작업의 모든 인스턴스가 삭제 됩니다.

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a>Start-Job cmdlet을 사용 하 여 시작 된 작업은 디스크에 저장 되지 않습니다.

를 사용 하 여 `Start-Job` 예약 된 작업을 시작할 때 작업 트리거를 사용 하는 대신는 `Start-Job` 표준 백그라운드 작업을 시작 합니다. 백그라운드 작업 및 그 결과는 디스크에 있는 작업의 실행 기록에 저장 되지 않습니다.

Cmdlet을 사용 하 여 작업 `Get-Job` `Receive-Job` 결과를 가져올 수 있지만 Cmdlet의 Keep 매개 변수를 사용 하지 않는 한 결과는 수신 될 때 까지만 사용할 수 있습니다 `Receive-Job` .

또한 백그라운드 작업과 그 결과는 세션 별로 다릅니다. 이러한 사용자는 생성 된 세션에만 존재 합니다. 을 사용 하 여 작업을 삭제 하는 경우 `Remove-Job` 세션을 닫거나 PowerShell을 닫으면 작업 인스턴스와 해당 결과가 삭제 됩니다.

## <a name="scheduled-job-doesnt-run"></a>예약 된 작업이 실행 되지 않음

작업 트리거 또는 예약 된 작업을 사용 하지 않도록 설정 하면 예약 된 작업이 자동으로 실행 되지 않습니다.

Cmdlet을 사용 `Get-ScheduledJob` 하 여 예약 된 작업을 가져옵니다. 예약 된 작업의 **Enabled** 속성 값이 **True** 인지 확인 합니다.

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

Cmdlet을 사용 `Get-JobTrigger` 하 여 예약 된 작업의 작업 트리거를 가져옵니다.
작업 트리거의 **Enabled** 속성 값이 **True** 인지 확인 합니다.

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

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a>작업 트리거가 유효 하지 않으면 예약 된 작업이 자동으로 실행 되지 않습니다.

예를 들어 작업 트리거는 과거의 날짜 또는 발생 하지 않는 날짜를 지정할 수 있습니다 (예: 해당 월의 5 번째 월요일).

작업 트리거의 조건이 나 작업 옵션이 충족 되지 않으면 예약 된 작업이 자동으로 실행 되지 않습니다.

예를 들어 사용자가 로그온 하지 않거나 원격 으로만 연결 하는 경우 특정 사용자가 컴퓨터에 로그온 할 때만 실행 되는 예약 된 작업이 실행 되지 않습니다.

예약 된 작업의 옵션을 검토 하 고 충족 되는지 확인 합니다.
예를 들어 컴퓨터가 유휴 상태 이거나 네트워크에 연결 되어 있거나, 긴 **IdleDuration** 있거나, 짧은 **IdleTimeout** 을 사용 해야 하는 예약 된 작업이 실행 되지 않을 수 있습니다.

Cmdlet을 사용 `Get-ScheduledJobOption` 하 여 작업 옵션 및 해당 값을 검사 합니다.

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

예약 된 작업 옵션에 대 한 설명은 [set-scheduledjoboption](xref:PSScheduledJob.New-ScheduledJobOption)를 참조 하세요.

### <a name="the-scheduled-job-instance-might-have-failed"></a>예약 된 작업 인스턴스가 실패 했을 수 있습니다.

예약 된 작업 명령이 실패 하면 PowerShell에서 오류 메시지를 생성 하 여 즉시 보고 합니다. 그러나 작업 스케줄러 실행 하려고 할 때 작업이 실패 하면 PowerShell에서 오류를 사용할 수 없습니다.

작업 오류를 검색 하 고 수정 하려면 다음 방법을 사용 합니다.

작업 스케줄러 이벤트 로그에서 오류를 확인 하십시오. 로그를 확인 하려면 다음과 같이 이벤트 뷰어 또는 PowerShell 명령을 사용 합니다.

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

작업 스케줄러에서 작업 레코드를 확인 합니다. PowerShell 예약 된 작업은 다음 작업 예약 폴더에 저장 됩니다.

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a>권한이 부족 하 여 예약 된 작업이 실행 되지 않을 수 있습니다.

예약 된 작업은 작업을 만든 사용자의 사용 권한 또는 또는 명령의 **Credential** 매개 변수로 지정 된 사용자의 사용 권한으로 실행 `Register-ScheduledJob` `Set-ScheduledJob` 됩니다.

해당 사용자에 게 명령 또는 스크립트를 실행할 수 있는 권한이 없는 경우 작업이 실패 합니다.

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a>예약 된 작업을 가져올 수 없거나 예약 된 작업이 손상 되었습니다.

드문 경우 지만 예약 된 작업이 손상 되거나 해결할 수 없는 내부 모순 포함 될 수 있습니다. 일반적으로이 작업은 예약 된 작업에 대 한 XML 파일을 수동으로 편집 하 여 잘못 된 XML을 생성 하는 경우에 발생 합니다.

예약 된 작업이 손상 되 면 PowerShell에서 예약 된 작업, 해당 실행 기록 및 디스크의 결과를 삭제 하려고 시도 합니다.

예약 된 작업을 제거할 수 없는 경우 cmdlet을 실행할 때마다 손상 된 작업 오류 메시지가 표시 됩니다 `Get-ScheduledJob` .

손상 된 예약 된 작업을 제거 하려면 다음 방법 중 하나를 사용 합니다.

예약 된 `<ScheduledJobName>` 작업에 대 한 디렉터리를 삭제 합니다. **Set-scheduledjob** 디렉터리를 삭제 하지 마세요.

디렉터리의 위치:

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

다음은 그 예입니다. 

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

작업 스케줄러를 사용 하 여 예약 된 작업을 삭제 합니다. PowerShell 예약 된 작업은 다음 작업 스케줄러 경로에 표시 됩니다.

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a>작업 cmdlet이 예약 된 작업을 일관 되 게 찾을 수 없음

**PSScheduledJob** 모듈이 현재 세션에 없으면 작업 cmdlet은 예약 된 작업을 가져오거나, 시작 하거나, 결과를 가져올 수 없습니다.

**PSScheduledJob** 모듈을 가져오려면 `Import-Module PSScheduledJob` cmdlet과 같이 모듈에서 cmdlet을 입력 하거나 실행 하거나 가져옵니다 `Get-ScheduledJob` .
PowerShell 3.0부터 모듈에서 cmdlet을 가져오거나 사용 하면 모듈을 자동으로 가져옵니다.

**PSScheduledJob** 모듈이 현재 세션에 없는 경우 다음 명령 시퀀스를 사용할 수 있습니다.

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

이 동작은 `Get-ScheduledJob` 명령이 **PSScheduledJob** 모듈을 자동으로 가져온 다음 명령을 실행 하기 때문에 발생 합니다.

## <a name="see-also"></a>참고 항목

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[PSScheduledJob](xref:PSScheduledJob) 모듈 cmdlet

[작업 Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference)
