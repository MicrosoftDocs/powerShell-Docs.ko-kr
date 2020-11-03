---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213426"
---
# Get-ScheduledJobOption

## 개요
예약된 작업의 작업 옵션을 가져옵니다.

## SYNTAX

### JobDefinition (기본값)

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## 설명
**Set-scheduledjoboption** cmdlet은 예약 된 작업의 작업 옵션을 가져옵니다.
이 명령을 사용하여 작업 옵션을 검사하거나 작업 옵션을 다른 cmdlet으로 파이프할 수 있습니다.

작업 옵션은 독립적으로 디스크에 저장되지 않고 예약된 작업의 일부입니다.
예약된 작업의 작업 옵션을 가져오려면 예약된 작업을 지정합니다.

**Get-ScheduledJobOption** cmdlet의 매개 변수를 사용하여 예약된 작업을 식별할 수 있습니다.
이름 또는 id 번호를 기준으로 예약 된 작업을 식별 하거나 Get-ScheduledJob cmdlet에서 반환 되는 개체 (예: **set-scheduledjoboption** 로 반환 되는 개체)를 입력 하거나 파이프 하 여 **set-scheduledjob** 개체를 입력할 수 있습니다.

**Set-scheduledjoboption** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 작업 옵션 가져오기

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
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

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

이 명령은 이름에 백업이 있는 예약 된 작업의 작업 옵션을 가져옵니다.
결과는 **Get-ScheduledJobOption** 에서 반환된 작업 옵션 개체를 보여 줍니다.

### 예제 2: 모든 작업 옵션 가져오기

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업의 작업 옵션을 가져옵니다.

Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.
파이프라인 연산자 (|)가 예약 된 작업을 **set-scheduledjoboption** cmdlet으로 보내면이 cmdlet이 각 예약 된 작업의 작업 옵션을 가져옵니다.

### 예 3: 선택한 작업 옵션 가져오기

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

이 예제에서는 특정 값을 가진 작업 옵션 개체를 찾는 방법을 보여 줍니다.

첫 번째 명령은 RunElevated 된 속성 값이 $True이 고 RunWithoutNetwork 속성 값이 $False 인 작업 옵션을 가져옵니다.
출력에는 선택한 **JobOptions** 개체가 표시 됩니다.

### 예 4: 작업 옵션을 사용 하 여 새 작업 만들기

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

이 예에서는 Get-ScheduledJobOption 새 예약 된 작업에 가져오는 작업 옵션을 사용 하는 방법을 보여 줍니다.

첫 번째 명령은 **set-scheduledjoboption** 를 사용 하 여 BackupTestLogs 예약 된 작업의 작업 옵션을 가져옵니다.
옵션을 $Opts 변수에 저장합니다.

두 번째 명령은 Register-ScheduledJob cmdlet을 사용 하 여 새 예약 된 작업을 만듭니다.
*ScheduledJobOption* 매개 변수 값은 $Opts 변수에 있는 옵션 개체입니다.

### 예 5: 원격 컴퓨터에서 작업 옵션 가져오기

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 컴퓨터에서 DataDemon 작업의 예약 된 작업 옵션을 가져옵니다.
이 명령은 $O 변수의 옵션을 저장 합니다.

## PARAMETERS

### -Id
예약된 작업의 ID 번호를 지정합니다.
**Get-ScheduledJobOption** 은 지정한 예약된 작업의 작업 옵션을 가져옵니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 id 번호를 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
예약된 작업을 지정합니다.
**Set-scheduledjob** 개체가 포함 된 변수를 입력 하거나 **set-scheduledjob** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.
**Set-scheduledjob** 개체를 **set-scheduledjoboption** 로 파이프 할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
예약된 작업의 이름을 지정합니다.
**Get-ScheduledJobOption** 은 지정한 예약된 작업의 작업 옵션을 가져옵니다.
와일드카드가 지원됩니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 이름을 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Set-scheduledjob. ScheduledJobDefinition
Get-ScheduledJob에서 **set-scheduledjoboption** 로 예약 된 작업을 파이프 할 수 있습니다.

## 출력

### Set-scheduledjob. ScheduledJobOptions

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
