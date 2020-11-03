---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213418"
---
# New-ScheduledJobOption

## 개요
예약된 작업에 대한 고급 옵션을 포함하는 개체를 만듭니다.

## SYNTAX

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## 설명
**New-ScheduledJobOption** cmdlet은 예약된 작업에 대한 고급 옵션을 포함하는 개체를 만듭니다.

**ScheduledJobOptions** 가 반환하는 **New-ScheduledJobOption** 개체를 사용하여 새 예약된 작업이나 기존 예약된 작업에 대한 작업 옵션을 설정할 수 있습니다.
또는 Get-ScheduledJobOption cmdlet을 사용 하 여 작업 옵션을 설정 하 여 기존 예약 된 작업의 작업 옵션을 가져오거나 해시 테이블 값을 사용 하 여 작업 옵션을 표시할 수 있습니다.

매개 변수가 없으면 **set-scheduledjoboption** 는 모든 옵션에 대 한 기본값을 포함 하는 개체를 생성 합니다.
JobDefinition 속성을 제외한 모든 속성을 편집할 수 있으므로 결과 개체를 템플릿으로 사용하고 엔터프라이즈에 대한 표준 옵션 개체를 만들 수 있습니다.

예약된 작업을 만들고 예약된 작업 옵션을 설정하는 경우 모든 예약된 작업 옵션의 기본값을 검토합니다.
예약된 작업은 설정된 모든 실행 조건이 충족될 경우에만 실행됩니다.

**Set-scheduledjoboption** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예 1: 기본값을 사용 하 여 예약 된 작업 옵션 개체 만들기

```
PS C:\> New-ScheduledJobOption
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
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

이 명령은 모든 기본값이 포함된 예약된 작업 옵션 개체를 만듭니다.

### 예제 2: 사용자 지정 값을 사용 하 여 예약 된 작업 옵션 개체 만들기

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

다음 명령은 네트워크가 필요한 예약된 작업 개체를 만들고 컴퓨터가 AC 전원에 연결되어 있지 않아도 예약된 작업을 실행합니다.

출력은 *RequireNetwork* 매개 변수가 RunWithoutNetwork 속성의 값을 $False로 변경 하 고 *StartIfOnBattery* 매개 변수가 StartIfOnBatteries 속성의 값을 $True로 변경 함을 보여 줍니다.

### 예 3: 새 예약 된 작업에 대 한 옵션 설정

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : True
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

이 예제에서는 **New-ScheduledJobOption** 이 반환하는 **ScheduledJobOptions** 개체를 사용하여 새 예약된 작업에 대한 옵션을 설정하는 방법을 보여 줍니다.

### 예 4: 예약 된 작업 옵션 개체의 속성 정렬

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

이 예제에서는 **ScheduledJobOptions** 개체의 속성을 읽기 쉽도록 사전순으로 정렬하는 방법을 보여 줍니다.

첫 번째 명령은 **New-ScheduledJobOption** cmdlet을 사용하여 **ScheduledJobOptions** 개체를 만듭니다.
*WakeToRun* 매개 변수를 사용하고 결과 개체를 $Options 변수에 저장합니다.

개체 $Options의 속성을 가져오기 위해 두 번째 명령은 모든 Windows PowerShell 개체의 **PSObject** 속성과 해당 속성 속성을 사용 합니다.
그런 다음이 명령은 속성 개체를 Sort-Object cmdlet으로 파이프 합니다 .이 cmdlet은 속성을 사전순으로 정렬 한 다음 Format-Table cmdlet으로 정렬 하 여 테이블에 속성의 이름과 값을 표시 합니다.

이 형식을 사용 하면 $Options에서 **ScheduledJobOptions** 개체의 WakeToRun 속성을 보다 쉽게 찾을 수 있으며 해당 값이 $False에서 $True로 변경 되었는지 확인할 수 있습니다.

## PARAMETERS

### -ContinueIfGoingOnBattery
작업이 실행되는 동안 컴퓨터가 배터리 전원으로 전환되어도(AC 전원에서 연결 끊김) 예약된 작업을 중지하지 않습니다.
기본적으로 예약된 작업은 컴퓨터가 AC 전원에서 연결이 끊길 때 중지됩니다.

*ContinueIfGoingOnBattery* 매개 변수는 예약 된 작업의 StopIfGoingOnBatteries 속성 값을 $True 설정 합니다.

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

### -DoNotAllowDemandStart
트리거된 경우에만 작업을 시작합니다.
사용자가 작업 스케줄러의 실행 기능 등을 사용하여 수동으로 작업을 시작할 수 없습니다.

이 매개 변수는 작업 스케줄러에만 영향을 주며
사용자가 Start-Job cmdlet을 사용 하 여 작업을 시작할 수는 없습니다.

*DoNotAllowDemandStart* 매개 변수는 예약 된 작업의 DoNotAllowDemandStart 속성 값을 $True 설정 합니다.

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

### -HideInTaskScheduler
작업 스케줄러에 작업을 표시하지 않습니다.
이 값은 작업이 실행되는 컴퓨터에만 영향을 줍니다.
기본적으로 예약된 작업은 작업 스케줄러에 표시됩니다.

태스크가 숨겨진 경우에도 사용자는 작업 스케줄러에서 숨겨진 작업 보기 표시 옵션을 선택 하 여 작업을 표시할 수 있습니다.

*HideInTaskScheduler* 매개 변수는 예약 된 작업의 ShowInTaskScheduler 속성 값을 $False로 설정 합니다.

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

### -IdleDuration
작업이 시작되기 전에 컴퓨터가 유휴 상태여야 하는 기간을 지정합니다.
기본값은 10분입니다.
*IdleTimeout* 값이 만료되기 전에 컴퓨터가 지정한 기간 동안 유휴 상태가 아닐 경우 예약된 작업이 다음 예약된 시간(있을 경우)까지 실행되지 않습니다.

New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 **timespan** 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.

이 값을 사용하도록 설정하려면 *StartIfIdle* 매개 변수를 사용합니다.
기본적으로 예약 된 작업의 StartIfNotIdle 속성은 $True로 설정 되 고 Windows PowerShell은 *IdleDuration* 및 *IdleTimeout* 값을 무시 합니다.

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

### -IdleTimeout
예약된 작업이 컴퓨터가 유휴 상태가 되기를 기다리는 기간을 지정합니다.
컴퓨터가 *IdleDuration* 매개 변수에 지정된 기간 동안 유휴 상태로 유지되기 전에 이 시간 제한이 만료될 경우 다음 예약된 시간(있을 경우)까지 작업이 실행되지 않습니다.
기본값은 1시간입니다.

New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 **timespan** 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.

이 값을 사용하도록 설정하려면 *StartIfIdle* 매개 변수를 사용합니다.
기본적으로 예약 된 작업의 StartIfNotIdle 속성은 $True로 설정 되 고 Windows PowerShell은 *IdleDuration* 및 *IdleTimeout* 값을 무시 합니다.

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

### -MultipleInstancePolicy
시스템에서 작업의 다른 인스턴스가 실행되는 동안 예약된 작업 인스턴스를 시작하는 요청에 응답하는 방법을 결정합니다.
기본값은 IgnoreNew입니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- IgnoreNew.
새 작업 인스턴스가 무시됩니다.
- 병렬입니다.
새 작업 인스턴스가 즉시 시작됩니다.
- 큐.
현재 인스턴스가 완료되는 즉시 새 작업 인스턴스가 시작됩니다.
- StopExisting.
현재 작업 인스턴스가 중지 되 고 새 인스턴스가 시작 됩니다.

작업을 실행하려면 작업 일정에 대한 모든 조건을 충족해야 합니다.
예를 들어 *RequireNetwork* , *IdleDuration* 및 *IdleTimeout* 매개 변수에 의해 설정 된 조건이 충족 되지 않으면이 매개 변수의 값에 관계 없이 작업 인스턴스가 시작 되지 않습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireNetwork
네트워크 연결을 사용할 수 있을 때만 예약된 작업을 실행합니다.

이 매개 변수를 지정하고 예약된 시작 시간에 네트워크를 사용할 수 없는 경우 다음 예약된 시작 시간(있을 경우)까지 작업이 실행되지 않습니다.

*RequireNetwork* 매개 변수는 예약 된 작업의 RunWithoutNetwork 속성 값을 $False 설정 합니다.

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

### -RestartOnIdleResume
컴퓨터가 유휴 상태가 되면 예약된 작업을 다시 시작합니다.
이 매개 변수는 컴퓨터가 활성 상태가 될 경우(유휴 상태 종료) 실행 중인 예약된 작업을 일시 중단하는 *StopIfGoingOffIdle* 매개 변수와 함께 작동합니다.

*RestartOnIdleResume* 매개 변수는 예약 된 작업의 RestartOnIdleResume 속성 값을 $True 설정 합니다.

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

### -RunElevated 된
작업이 실행되는 컴퓨터의 Administrators 그룹 구성원 권한으로 예약된 작업을 실행합니다.

관리자 권한으로 예약 된 작업을 실행할 수 있도록 설정 하려면 Register-ScheduledJob의 *credential* 매개 변수를 사용 하 여 작업에 대 한 명시적 자격 증명을 제공 합니다.

*Runelevated* 된 매개 변수는 예약 된 작업의 runelevated 된 속성 값을 $True로 설정 합니다.

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

### -StartIfIdle
*IdleTimeout* 매개 변수에 지정된 시간이 만료되기 전에 컴퓨터가 *IdleDuration* 매개 변수에 지정된 시간 동안 유휴 상태였을 경우 예약된 작업을 시작합니다.

기본적으로 *IdleDuration* 및 *IdleTimeout* 매개 변수는 무시되고 컴퓨터가 사용 중이라도 예약된 시작 시간에 작업이 시작됩니다.

이 매개 변수를 지정하고 예약된 시작 시간에 컴퓨터가 사용 중일 경우(유휴 상태 아님) 다음 예약된 시작 시간(있을 경우)까지 작업이 실행되지 않습니다.

*StartIfIdle* 매개 변수는 예약 된 작업의 StartIfNotIdle 속성 값을 $False 설정 합니다.

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

### -StartIfOnBattery
예약된 시작 시간에 컴퓨터가 배터리 전원으로 실행되고 있어도 예약된 작업을 시작합니다.
기본값은 $False입니다.

*StartIfOnBattery* 매개 변수는 예약 된 작업의 StartIfOnBatteries 속성 값을 $True 설정 합니다.

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

### -StopIfGoingOffIdle
작업이 실행되는 동안 컴퓨터가 활성 상태가 될 경우(유휴 상태 아님) 실행 중인 예약된 작업을 일시 중단합니다.

기본적으로 컴퓨터가 활성 상태일 때 일시 중단되는 예약된 작업은 컴퓨터가 다시 유휴 상태가 되면 다시 시작됩니다.
이 기본 동작을 변경하려면 *RestartOnIdleResume* 매개 변수를 사용합니다.

*StopIfGoingOffIdle* 매개 변수는 예약 된 작업의 StopIfGoingOffIdle 속성 값을 $True 설정 합니다.

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

### -WakeToRun
작업을 실행할 수 있도록 예약된 시작 시간에 컴퓨터를 최대 절전 또는 절전 모드에서 해제합니다.
기본적으로 컴퓨터가 예약된 시작 시간에 최대 절전 또는 절전 모드에 있는 경우 작업이 실행되지 않습니다.

*WakeToRun* 매개 변수는 예약 된 작업의 WakeToRun 속성 값을 $True 설정 합니다.

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

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### Set-scheduledjob. ScheduledJobOptions

## 참고

* **Set-scheduledjoboption** 에서 생성 하는 **ScheduledJobOptions** 개체를 Register-ScheduledJob cmdlet의 *set-scheduledjoboption* 매개 변수 값으로 사용할 수 있습니다. 그러나 *set-scheduledjoboption* 매개 변수는 **ScheduledJobOptions** 개체의 속성과 해당 값 (예:)을 지정 하는 해시 테이블 값도 사용할 수 있습니다.

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

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
