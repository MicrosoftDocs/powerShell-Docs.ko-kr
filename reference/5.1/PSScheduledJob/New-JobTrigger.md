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
# New-JobTrigger

## 개요
예약된 작업에 대한 작업 트리거를 만듭니다.

## SYNTAX

### 한 번 (기본값)

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### 매일

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### 매주

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### AtStartup

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### AtLogon

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## 설명
**새 JobTrigger** cmdlet은 일회성 또는 되풀이 일정에 따라 또는 이벤트가 발생 하는 경우 예약 된 작업을 시작 하는 작업 트리거를 만듭니다.

**New-JobTrigger** 가 반환하는 **ScheduledJobTrigger** 개체를 사용하여 새 예약된 작업이나 기존 예약된 작업에 대한 작업 트리거를 설정할 수 있습니다.
Get-JobTrigger cmdlet을 사용 하 여 기존 예약 된 작업의 작업 트리거를 가져오거나, 해시 테이블 값을 사용 하 여 작업 트리거를 나타내는 작업 트리거를 만들 수도 있습니다.

작업 트리거를 만들 때 New-ScheduledJobOption cmdlet에 지정 된 옵션의 기본값을 검토 합니다.
이러한 옵션은 유효한 값과 기본값이 **Task Scheduler** 의 해당 옵션과 같으며 예약된 작업의 일정과 타이밍에 영향을 줍니다.

**새 JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예 1: 한 번 예약

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

이 명령은 **New-JobTrigger** cmdlet을 사용하여 예약된 작업을 한 번만 시작하는 작업 트리거를 만듭니다.
*At* 매개 변수 값은 Windows PowerShell이 **DateTime** 개체로 변환하는 문자열입니다.
*At* 매개 변수 값에는 시간뿐 아니라 명시적 날짜도 포함됩니다.
날짜를 생략하면 현재 날짜와 오전 3:00 시간으로 트리거가 만들어지며 과거 시간을 나타낼 가능성이 큽니다.

### 예 2: 일별 일정

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

이 명령은 3일마다 오전 4:15에 예약된 작업을 시작하는 작업 트리거를 만듭니다.

*At* 매개 변수 값에 날짜가 없으므로 현재 날짜가 **DateTime** 개체의 날짜 값으로 사용됩니다.
날짜와 시간이 과거이면 *At* 매개 변수 값에서 3일 후인 다음 발생 시 예약된 작업이 시작됩니다.

### 예 3: 주간 일정

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

이 명령은 4주마다 월요일, 수요일 및 금요일 23시(오후 11:00)에 예약된 작업을 시작하는 작업 트리거를 만듭니다.

*DaysOfWeek* 매개 변수 값을와 같은 정수로 입력할 수도 있습니다 `-DaysOfWeek 1, 5` .

### 예 4: 로그온 일정

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

이 명령은 도메인 관리자가 컴퓨터에 로그온할 때마다 예약된 작업을 시작하는 작업 트리거를 만듭니다.

### 예 5: 임의 지연 사용

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

이 명령은 매일 오전 1:00에 예약된 작업을 시작하는 작업 트리거를 만듭니다.
*RandomDelay* 매개 변수를 사용하여 최대 지연을 20분으로 설정합니다.
따라서 작업이 오전 1:00에서 오전 1:20 사이에 실행되며 간격은 의사 임의로 달라집니다.

샘플링, 부하 분산 및 기타 관리 작업에 임의 지연을 사용할 수 있습니다.
지연 값을 설정 하는 경우 New-ScheduledJobOption cmdlet의 유효 및 기본값을 검토 하 고 옵션 설정을 사용 하 여 지연을 조정 합니다.

### 예 6: 새 예약 된 작업에 대 한 작업 트리거 만들기

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

이 명령은 작업 트리거를 사용하여 새 예약된 작업을 만듭니다.

### 예 7: 예약 된 작업에 작업 트리거 추가

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

이 예제에서는 기존 예약된 작업에 작업 트리거를 추가하는 방법을 보여 줍니다.
여러 개의 작업 트리거를 예약된 작업에 추가할 수 있습니다.

이 명령은 Add-JobTrigger cmdlet을 사용 하 여 시 synchronizeapps 예약 된 작업에 작업 트리거를 추가 합니다.
*Trigger* 매개 변수 값은 매일 오전 3:10에 작업을 실행하는 **New-JobTrigger** 명령입니다.

명령 완료 시 SynchronizeApps는 작업 트리거에 의해 지정된 시간에 실행되는 예약된 작업이 됩니다.

### 예 8: 반복 작업 트리거 만들기

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

이 명령은 2013 9 월 12 일에 시작 하 여 48 시간 동안 60 분 마다 작업을 실행 하는 작업 트리거를 1:00 AM으로 만듭니다.

### 예 9: 되풀이 작업 트리거 중지

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

이 명령은 작업 트리거가 만료될 때까지 60분마다 실행되도록 트리거되는 SecurityCheck 작업을 강제로 중지합니다.

작업의 반복을 방지 하기 위해이 명령은 Get-JobTrigger를 사용 하 여 SecurityCheck 작업의 작업 트리거를 가져오고 Set-JobTrigger cmdlet을 사용 하 여 작업 트리거의 반복 간격 및 반복 기간을 0으로 변경 합니다.

### 예 10: 매시간 작업 트리거 만들기

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

다음 명령은 무기한 동안 12시간마다 한 번 예약된 작업을 실행하는 작업 트리거를 만듭니다.
내일(9/21/2012) 자정(오전 0:00)에 일정이 시작됩니다.

## PARAMETERS

### -At
지정한 날짜 및 시간에 작업을 시작합니다.
Get-Date cmdlet에서 반환 하는 것과 같은 **DateTime** 개체를 입력 하거나 날짜 및 시간으로 변환할 수 있는 문자열 (예: "4 월 19 일 2012 15:00", "12/31" 또는 "3am")을 입력 합니다.
연도와 같은 날짜의 요소를 지정하지 않으면 트리거의 날짜에 현재 날짜의 해당 요소가 포함됩니다.

*Once* 매개 변수를 사용할 경우 *At* 매개 변수 값을 미래 날짜와 시간으로 설정합니다.
**DateTime** 개체의 기본 날짜는 현재 날짜이기 때문에 명시적 날짜 없이 현재 시간 이전의 시간을 지정할 경우 과거 시간에 대한 작업 트리거가 만들어집니다.

Datetime **개체와** **datetime** 개체로 변환 되는 문자열은 제어판의 지역 및 언어에서 로컬 컴퓨터에 대해 선택한 날짜 및 시간 형식과 호환 되도록 자동으로 조정 됩니다.

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

### -AtLogOn
지정한 사용자가 컴퓨터에 로그온할 때 예약된 작업을 시작합니다.
사용자를 지정하려면 *User* 매개 변수를 사용합니다.

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

### -AtStartup
Windows가 시작될 때 예약된 작업을 시작합니다.

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

### -매일
매일 되풀이되는 작업 일정을 지정합니다.
*매일* 매개 변수 집합의 다른 매개 변수를 사용 하 여 일정 정보를 지정할 수 있습니다.

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

### -DaysInterval
일별 일정의 발생 간격(일)을 지정합니다.
예를 들어 값이 3이면 예약된 작업이 1, 4, 7일 등에 시작됩니다.
기본값은 1입니다.

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

### -DaysOfWeek
주별 예약된 작업이 실행되는 요일을 지정합니다.
요일 이름(예: "Monday") 또는 정수 0-6을 입력합니다. 여기서 0은 일요일을 나타냅니다.
이 매개 변수는 Weekly 매개 변수 집합에 필요합니다.

요일 이름은 작업 트리거에서 해당 정수 값으로 변환됩니다.
명령에서 요일 이름을 따옴표로 묶을 경우 "Monday", "Tuesday"와 같이 각 요일 이름을 별도의 따옴표로 묶습니다.
여러 요일 이름을 하나의 따옴표 쌍으로 묶으면 해당 정수 값이 합산됩니다.
예를 들어 "Monday, Tuesday"(1, 2)는 "Wednesday"(3) 값이 됩니다.

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

### -한 번
되풀이되지 않는(일회성) 일정이나 사용자 지정 되풀이 일정을 지정합니다.
되풀이 일정을 만들려면 *Once* 매개 변수를 *RepetitionDuration* 및 *RepetitionInterval* 매개 변수와 함께 사용합니다.

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

### -RandomDelay
예약된 시작 시간에 시작되는 임의 지연을 사용하도록 설정하고 최대 지연 값을 설정합니다.
지연 길이는 각 시작에 대해 의사 임의로 설정되며 지연 없음에서 이 매개 변수 값으로 지정된 시간까지 다양합니다.
기본값 0(00:00:00)은 임의 지연을 사용하지 않도록 설정합니다.

New-TimeSpan cmdlet에서 반환 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: format에 값을 입력 합니다.

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

### -RepeatIndefinitely
Windows PowerShell 4.0부터 제공되는 이 매개 변수를 사용하면 예약된 작업을 무기한 동안 되풀이해서 실행하기 위해 **RepetitionDuration** 매개 변수에 *TimeSpan.MaxValue* 값을 지정할 필요가 없습니다.

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

### -RepetitionDuration
지정한 시간이 만료될 때까지 작업을 되풀이합니다.
되풀이 빈도는 *RepetitionInterval* 매개 변수 값에 따라 결정됩니다.
예를 들어 **RepetitionInterval** 값이 5분이고 **RepetitionDuration** 값이 2시간이면 2시간 동안 5분마다 작업이 트리거됩니다.

New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.

작업을 무기한 실행하려면 *RepeatIndefinitely* 매개 변수를 대신 추가합니다.

작업 트리거 반복 기간이 만료 되기 전에 작업을 중지 하려면 Set-JobTrigger cmdlet을 사용 하 여 *RepetitionDuration* 값을 영 (0)으로 설정 합니다.

이 매개 변수는 명령에 *Once* , *At* 및 *RepetitionInterval* 매개 변수가 사용된 경우에만 유효합니다.

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

### -RepetitionInterval
지정한 시간 간격에 작업을 되풀이합니다.
예를 들어 이 매개 변수 값이 2시간이면 2시간마다 작업이 트리거됩니다.
기본값 0은 작업을 되풀이하지 않습니다.

New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.

이 매개 변수는 명령에 *Once* , *At* 및 *RepetitionDuration* 매개 변수가 사용된 경우에만 유효합니다.

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

### -User
예약된 작업의 *AtLogon* 시작을 트리거하는 사용자를 지정합니다.
사용자의 이름을 또는 형식으로 입력 \<UserName\> \<Domain\Username\> 하거나 별표 ( \* )를 입력 하 여 모든 사용자를 나타냅니다.
기본값은 모든 사용자입니다.

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

### -매주
매주 되풀이되는 작업 일정을 지정합니다.
Weekly 매개 변수 집합의 다른 매개 변수를 사용하여 일정 정보를 지정할 수 있습니다.

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

### -WeeksInterval
주별 작업 일정의 발생 간격(주)을 지정합니다.
예를 들어 값이 3이면 예약된 작업이 1, 4, 7주 등에 시작됩니다.
기본값은 1입니다.

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

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### Set-scheduledjob. ScheduledJobTrigger

## 참고

* 작업 트리거는 디스크에 저장되지 않습니다. 그러나 예약 된 작업은 디스크에 저장 되 고 Get-JobTrigger를 사용 하 여 예약 된 작업의 작업 트리거를 가져올 수 있습니다.
* **새 JobTrigger** 는 과거 날짜에 대 한 일회성 트리거와 같이 예약 된 작업을 실행 하지 않는 작업 트리거를 만들 수 없도록 합니다.
* Register-ScheduledJob cmdlet은 **New-JobTrigger** 또는 Get-JobTrigger cmdlet에서 반환 된 개체 또는 트리거 값을 포함 하는 해시 테이블을 비롯 한 ScheduledJobTrigger 개체를 허용 합니다.

  해시 테이블을 제출하려면 다음 키를 사용합니다.

  `@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` 또는 유효한 시간 문자열입니다. `DaysOfWeek="Monday", "Wednesday"` (또는 요일 이름의 조합) `Interval=2` (또는 유효한 빈도 간격); `RandomDelay="30minutes"` (또는 유효한 timespan 문자열) `User="Domain1\User01` 또는 모든 유효한 사용자 ( *Atlogon* frequency 값 에서만 사용)}

## 관련 링크

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Register-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Unregister-ScheduledJob](Unregister-ScheduledJob.md)
