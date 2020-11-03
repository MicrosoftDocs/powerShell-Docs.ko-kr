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
# Set-JobTrigger

## 개요
예약된 작업의 작업 트리거를 변경합니다.

## SYNTAX

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## 설명
**Set-JobTrigger** cmdlet은 예약된 작업의 작업 트리거 속성을 변경합니다.
이 cmdlet을 사용하여 작업이 시작되는 시간 또는 빈도를 변경하거나 시간 기반 일정에서 로그온 또는 시작에 의해 트리거되는 일정으로 변경할 수 있습니다.

작업 트리거는 예약 된 작업을 시작 하기 위한 되풀이 일정 또는 조건을 정의 합니다.
작업 트리거는 디스크에 저장되지 않지만 디스크에 저장된 예약된 작업의 작업 트리거를 변경할 수 있습니다.

예약 된 작업의 작업 트리거를 변경 하려면 먼저 Get-JobTrigger cmdlet을 사용 하 여 예약 된 작업의 작업 트리거를 가져옵니다.
그런 다음 트리거를 **Set-JobTrigger** 로 파이프하거나 변수에 저장하고 *Set-JobTrigger* cmdlet의 **InputObject** 매개 변수를 사용하여 트리거를 식별합니다.
**Set-JobTrigger** 의 나머지 매개 변수를 사용하여 작업 트리거를 변경할 수 있습니다.

작업 트리거의 유형을 변경 하는 경우 (예: 매일 또는 매주 트리거에서 *Atlogon* 트리거로 작업 트리거를 변경 하는 경우) 원래 트리거 속성이 삭제 됩니다.
그러나 트리거 값만 변경하고 유형을 변경하지 않을 경우(예: 주별 트리거의 요일 변경) 지정한 속성만 변경됩니다.
원래 작업 트리거의 다른 모든 속성은 유지됩니다.

**Set JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*`  하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 작업 트리거의 날짜 변경

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

이 예제에서는 주별 작업 트리거의 요일을 변경하는 방법을 보여 줍니다.

첫 번째 명령은 Get-JobTrigger cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 트리거를 가져옵니다.
출력은 트리거가 수요일과 토요일마다 자정에 작업을 시작함을 보여 줍니다.

이 명령은 필수가 아닙니다. 단지 트리거 변경의 결과를 보여 주기 위해 포함되었습니다.

### 예 2: 작업 트리거 형식 변경

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

이 예제에서는 작업을 시작하는 작업 트리거의 유형을 변경하는 방법을 보여 줍니다.
이 예제의 명령은 AtStartup 작업 트리거를 주별 트리거로 바꿉니다.

첫 번째 명령은 Get-JobTrigger cmdlet을 사용 하 여 Inventory 예약 된 작업의 작업 트리거를 가져옵니다.
출력은 작업에 매일 트리거와 *Atstartup* 트리거의 두 트리거가 있음을 보여 줍니다.

이 명령은 필수가 아닙니다. 단지 트리거 변경의 결과를 보여 주기 위해 포함되었습니다.

### 예 3: 원격 작업 트리거의 사용자 변경

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

이 명령은 Server01 컴퓨터에서 예약 된 작업의 모든 *Atlogon* 작업 트리거에 있는 사용자를 변경 합니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.

원격 명령은 컴퓨터의 모든 예약 된 작업을 가져오는 Get-ScheduledJob 명령으로 시작 합니다.
예약 된 작업은 Get-JobTrigger cmdlet으로 파이프 되며, 예약 된 작업의 작업 트리거를 가져옵니다.
각 작업 트리거에는 예약된 작업을 포함하는 JobDefinition 속성이 있으므로 트리거가 변경된 경우에도 예약된 작업과 연결된 상태로 유지됩니다.

작업 트리거는 사용자 속성이 있는 작업 트리거를 가져오는 Where-Object cmdlet으로 파이프 됩니다.
선택한 작업 트리거가 **Set-JobTrigger** cmdlet으로 파이프되면 이 cmdlet이 사용자를 Domain01\Admin02로 변경합니다.

### 예제 4: 여러 작업 트리거 중 하나 변경

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

이 예제의 명령은 SecurityCheck 예약된 작업의 *Once* 작업 트리거 되풀이 간격을 60분에서 90분으로 변경합니다.
SecurityCheck 예약 된 작업에는 세 개의 작업 트리거가 있으므로 명령은 Get-JobTrigger cmdlet의 *TriggerId* 매개 변수를 사용 하 여 변경할 작업 트리거를 식별 합니다.

첫 번째 명령은 **Get-JobTrigger** cmdlet을 사용하여 SecurityCheck 예약된 작업의 모든 작업 트리거를 가져옵니다.
작업 트리거의 ID를 표시하는 출력은 *Once* 작업 트리거의 ID가 3임을 보여 줍니다.

## PARAMETERS

### -At
지정한 날짜 및 시간에 작업을 시작합니다.
Get-Date cmdlet에서 반환 하는 것과 같은 **DateTime** 개체를 입력 하거나 시간으로 변환할 수 있는 문자열 (예: "4 월 19 일 2012 15:00", "12/31/2013 9:00 PM" 또는 "3am")을 입력 합니다.

**DateTime** 개체의 요소 (예: 초)를 지정 하지 않으면 작업 트리거의 해당 요소는 변경 되지 않습니다.
원래 작업 트리거에 **DateTime** 개체가 포함 되어 있지 않은 상태에서 요소를 생략 하면 현재 날짜 및 시간에서 해당 요소로 작업 트리거가 만들어집니다.

*Once* 매개 변수를 사용할 경우 *At* 매개 변수 값을 특정 날짜와 시간으로 설정합니다.
**DateTime** 개체의 기본 날짜는 현재 날짜이기 때문에 명시적 날짜 없이 현재 시간 이전의 시간을 설정할 경우 과거 시간에 대한 작업 트리거가 만들어집니다.

Datetime **개체와** **datetime** 개체로 변환 되는 문자열은 제어판의 지역 및 언어에서 로컬 컴퓨터에 대해 선택한 날짜 및 시간 형식과 호환 되도록 자동으로 조정 됩니다.

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

### -AtLogOn
지정한 사용자가 컴퓨터에 로그온할 때 예약된 작업을 시작합니다.
사용자를 지정하려면 *User* 매개 변수를 사용합니다.

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

### -AtStartup
Windows가 시작될 때 예약된 작업을 시작합니다.

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

### -매일
매일 되풀이되는 작업 일정을 지정합니다.
*매일* 매개 변수 집합의 다른 매개 변수를 사용 하 여 일정 정보를 지정할 수 있습니다.

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

### -DaysInterval
일별 일정의 발생 간격(일)을 지정합니다.
예를 들어 값이 3이면 예약된 작업이 1, 4, 7일 등에 시작됩니다.
기본값은 1입니다.

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

### -DaysOfWeek
주별 예약된 작업이 실행되는 요일을 지정합니다.
요일 이름 (예: 월요일, 목요일, 정수 0-6)을 입력 합니다. 여기서 0은 일요일을 나타내고, 별표 ()는 매일을 나타냅니다 \* .
이 매개 변수는 Weekly 매개 변수 집합에 필요합니다.

요일 이름은 작업 트리거에서 해당 정수 값으로 변환됩니다.
명령에서 요일 이름을 따옴표로 묶을 경우 "Monday", "Tuesday"와 같이 각 요일 이름을 별도의 따옴표로 묶습니다.
여러 요일 이름을 하나의 따옴표 쌍으로 묶으면 해당 정수 값이 합산됩니다.
예를 들어 "Monday, Tuesday"(1, 2)는 "Wednesday"(3) 값이 됩니다.

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

### -InputObject
작업 트리거를 지정합니다.
**ScheduledJobTrigger** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.
**ScheduledJobTrigger** 개체를 **설정-jobtrigger** 로 파이프 할 수도 있습니다.

여러 개의 작업 트리거를 지정할 경우 **Set-JobTrigger** 는 모든 작업 트리거에 동일한 변경을 수행합니다.

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

### -한 번
되풀이되지 않는(일회성) 일정을 지정합니다.

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

### -PassThru
변경된 작업 트리거를 반환합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -RandomDelay
예약된 시작 시간에 시작되는 임의 지연을 사용하도록 설정하고 최대 지연 값을 설정합니다.
지연 길이는 각 시작에 대해 의사 임의로 설정되며 지연 없음에서 이 매개 변수 값으로 지정된 시간까지 다양합니다.
기본값 0(00:00:00)은 임의 지연을 사용하지 않도록 설정합니다.

New-TimeSpan cmdlet에서 반환 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 timespan 개체로 변환 되는:: format에 값을 입력 합니다.

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
Parameter Sets: (All)
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
예를 들어 **RepetitionInterval** 값이 5분이고 *RepetitionDuration* 값이 2시간이면 2시간 동안 5분마다 작업이 트리거됩니다.

New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.

작업을 무기한 실행하려면 *RepeatIndefinitely* 매개 변수를 대신 추가합니다.

작업 트리거 되풀이 기간이 만료되기 전에 작업을 중지하려면 **RepetitionDuration** 값을 0으로 설정합니다.

*Once* 작업 트리거의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 **RepetitionInterval** 및 **RepetitionDuration** 매개 변수가 둘 다 포함되어야 합니다.
다른 작업 트리거 유형의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 *Once* , *At* , *RepetitionInterval* 및 *RepetitionDuration* 매개 변수가 포함되어야 합니다.

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

### -RepetitionInterval
지정한 시간 간격에 작업을 되풀이합니다.
예를 들어 이 매개 변수 값이 2시간이면 2시간마다 작업이 트리거됩니다.
기본값 0은 작업을 되풀이하지 않습니다.

New-TimeSpan cmdlet에서 반환 하는 것과 같은 timespan 개체 또는 timespan 개체로 변환할 수 있는 문자열 (예: "1:05:30")을 입력 합니다.

**Once** 작업 트리거의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 **RepetitionInterval** 및 **RepetitionDuration** 매개 변수가 둘 다 포함되어야 합니다.
다른 작업 트리거 유형의 되풀이 기간이나 되풀이 간격을 변경하려면 명령에 **Once** , **At** , **RepetitionInterval** 및 **RepetitionDuration** 매개 변수가 포함되어야 합니다.

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

### -User
예약된 작업의 *AtLogon* 시작을 트리거하는 사용자를 지정합니다.
사용자의 이름을 또는 형식으로 입력 \<UserName\> \<Domain\Username\> 하거나 별표 ( \* )를 입력 하 여 모든 사용자를 나타냅니다.
기본값은 모든 사용자입니다.

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

### -매주
매주 되풀이되는 작업 일정을 지정합니다.
*주별* 매개 변수 집합의 다른 매개 변수를 사용 하 여 일정 정보를 지정할 수 있습니다.

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

### -WeeksInterval
주별 작업 일정의 발생 간격(주)을 지정합니다.
예를 들어 값이 3이면 예약된 작업이 1, 4, 7주 등에 시작됩니다.
기본값은 1입니다.

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

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Set-scheduledjob. ScheduledJobTrigger
여러 작업 트리거를 **설정-JobTrigger** 로 파이프 할 수 있습니다.

## 출력

### None 또는 Set-scheduledjob. ScheduledJobTrigger
*Passthru* 매개 변수를 사용할 경우 **Set-JobTrigger** 은 변경된 작업 트리거를 반환합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 작업 트리거에는 작업 트리거를 예약된 작업에 연결하는 JobDefintion 속성이 있습니다. 예약된 작업의 작업 트리거를 변경하면 작업이 변경됩니다. Set-ScheduledJob 명령을 사용 하 여 예약 된 작업에 변경 된 트리거를 적용할 필요가 없습니다.

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
