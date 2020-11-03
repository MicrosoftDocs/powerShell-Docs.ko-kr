---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213377"
---
# Set-ScheduledJobOption

## 개요
예약된 작업의 작업 옵션을 변경합니다.

## SYNTAX

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## 설명
**Set-ScheduledJobOptions** cmdlet은 예약된 작업의 작업 옵션을 변경합니다.

예약 된 작업의 옵션을 변경 하려면 먼저 Get-ScheduledJobOption cmdlet을 사용 하 여 예약 된 작업의 작업 옵션을 가져옵니다.
그런 다음 옵션을 **Set-ScheduledJobOption** 으로 파이프하거나 변수에 저장하고 *Set-ScheduledJobOption* cmdlet의 **InputObject** 매개 변수를 사용하여 옵션을 식별합니다.
**Set-ScheduledJobOption** 의 나머지 매개 변수를 사용하여 작업 옵션을 변경할 수 있습니다.

작업 옵션을 켜려면 해당 옵션을 설정하는 매개 변수를 사용합니다.
옵션을 해제 하려면 매개 변수 이름, 콜론 (:) 및 $False을 입력 합니다.
예를 들어, *Runelevated* 옵션을 해제 하려면를 입력 `-RunElevated:$False` 합니다.

각 작업 옵션 개체에는 매개 변수를 포함하는 JobDefinition 속성이 있으므로 작업 옵션을 변경할 때 예약된 작업과의 연결이 유지됩니다.

예약된 작업 옵션은 작업 스케줄러에서 작업을 시작할 경우 작업 실행 방법을 결정합니다.
Start-Job cmdlet을 사용 하 여 예약 된 작업을 시작할 때는 이러한 옵션이 적용 되지 않습니다.

**Set-scheduledjoboption** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 작업 옵션 변경

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
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
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
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
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

이 예제에서는 로컬 컴퓨터에서 예약된 작업의 옵션을 변경하는 방법을 보여 줍니다.

첫 번째 명령은 Get-ScheduledJobOption cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 옵션을 가져옵니다.
출력은 WakeToRun 및 RunElevated 된 속성이 $False로 설정 되어 있음을 보여 줍니다.

이 명령은 필수가 아닙니다. 단지 옵션 변경의 결과를 보여 주기 위해 포함되었습니다.

### 예제 2: 모든 원격 예약 된 작업에 대 한 옵션 변경

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

이 명령은 Server01 컴퓨터의 모든 예약 된 작업에서 *IdleTimeout* 값을 1 시간 (기본값)에서 2 시간으로 변경 합니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.

원격 명령은 컴퓨터의 모든 예약 된 작업을 가져오는 Get-ScheduledJob 명령으로 시작 합니다.
예약 된 작업은 Get-ScheduledJobOption cmdlet으로 파이프 되며, 예약 된 작업의 작업 옵션을 가져옵니다.
각 작업 옵션 개체에는 예약된 작업을 포함하는 JobDefinition 속성이 있으므로 옵션 개체가 변경된 경우에도 예약된 작업과 연결된 상태로 유지됩니다.

작업 트리거는 **set-scheduledjoboption** cmdlet으로 파이프 되며,이 Cmdlet은 *IdleTimeout* 옵션의 값을 2 시간 (2:00:00)으로 변경 합니다.

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

태스크가 숨겨진 경우에도 사용자는 작업 스케줄러에서 **숨겨진 작업 보기 표시** 옵션을 선택 하 여 작업을 표시할 수 있습니다.

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

New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.

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
작업이 시작되기 전에 컴퓨터가 유휴 상태여야 하는 기간을 지정합니다.
기본값은 10분입니다.
**IdleTimeout** 값이 만료되기 전에 컴퓨터가 지정한 기간 동안 유휴 상태가 아닐 경우 예약된 작업이 다음 예약된 시간(있을 경우)까지 실행되지 않습니다.

New-TimeSpan cmdlet에 의해 생성 된 timespan 개체와 같은 timespan 개체를 입력 하거나 \<hours\> \<minutes\> \<seconds\> 자동으로 **timespan** 개체로 변환 되는:: 형식 값을 입력 합니다.

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

### -InputObject
작업 옵션을 지정합니다.
**ScheduledJobOptions** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobOptions** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJobOption 명령)을 입력 합니다.
**ScheduledJobOptions** 개체를 **set-scheduledjoboption** 로 파이프 할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MultipleInstancePolicy
시스템에서 작업의 다른 인스턴스가 실행되는 동안 예약된 작업 인스턴스를 시작하는 요청에 응답하는 방법을 결정합니다.
이 매개 변수에 허용되는 값은 다음과 같습니다.

- IgnoreNew.
새 작업 인스턴스가 무시됩니다.
이것은 기본값입니다.
- 병렬입니다.
새 작업 인스턴스가 즉시 시작됩니다.
- 큐.
현재 인스턴스가 완료되는 즉시 새 작업 인스턴스가 시작됩니다.
- StopExisting.
현재 작업 인스턴스가 중지되고 새 인스턴스가 시작됩니다.

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

### -PassThru
작업 중인 항목을 나타내는 개체를 반환합니다.
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

**Runelevated** 된 매개 변수는 예약 된 작업의 **runelevated** 된 속성 값을 True로 설정 합니다.

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
**IdleTimeout** 매개 변수에 지정된 시간이 만료되기 전에 컴퓨터가 *IdleDuration* 매개 변수에 지정된 시간 동안 유휴 상태였을 경우 예약된 작업을 시작합니다.

기본적으로 *IdleDuration* 및 *IdleTimeout* 매개 변수는 무시되고 컴퓨터가 사용 중이라도 예약된 시작 시간에 작업이 시작됩니다.

이 매개 변수를 지정하고 예약된 시작 시간에 컴퓨터가 사용 중일 경우(유휴 상태 아님) 다음 예약된 시작 시간(있을 경우)까지 작업이 실행되지 않습니다.

*StartIfIdle* 매개 변수는 예약 된 작업의 **StartIfNotIdle** 속성 값을 False로 설정 합니다.

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
기본값은 False입니다.

*StartIfOnBattery* 매개 변수는 예약 된 작업의 **StartIfOnBatteries** 속성 값을 $True 설정 합니다.

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

### Set-scheduledjob. ScheduledJobOptions
예약된 작업 옵션을 **Set-ScheduledJobOption** 으로 파이프할 수 있습니다.

## 출력

### None 또는 Set-scheduledjob. ScheduledJobOptions
*Passthru* 매개 변수를 사용할 경우 **Set-ScheduledJobOption** 은 변경된 작업 옵션을 반환합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

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
