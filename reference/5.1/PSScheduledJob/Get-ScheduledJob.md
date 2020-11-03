---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213434"
---
# Get-ScheduledJob

## 개요
로컬 컴퓨터에 있는 예약된 작업을 가져옵니다.

## SYNTAX

### 인 (기본값)

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### Build.definitionname

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## 설명
**Get-ScheduledJob** cmdlet은 로컬 컴퓨터에 있는 예약된 작업을 가져옵니다.
**Set-scheduledjob** 는 Register-ScheduledJob cmdlet을 사용 하 여 현재 사용자가 만든 예약 된 작업만 가져옵니다.

**Register-ScheduledJob** cmdlet을 사용하여 만든 작업이 작업 Scheduler에 표시되어도 **Get-ScheduledJob** 은 예약된 작업만 가져옵니다.
작업 스케줄러에서 만들어진 예약된 작업은 가져오지 않습니다.

매개 변수가 없을 경우 **Get-ScheduledJob** 은 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.
**Get-ScheduledJob** 의 매개 변수를 사용하여 ID 또는 이름으로 예약된 작업을 가져온 다음 검사하거나 다른 cmdlet으로 파이프할 수 있습니다.

**Set-scheduledjob** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 모든 예약 된 작업 가져오기

```
PS C:\> Get-ScheduledJob
```

이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.

### 예 2: 이름으로 예약 된 작업 가져오기

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

이 명령은 백업 또는 보관을 포함 하는 이름을 가진 컴퓨터의 모든 예약 된 작업을 가져옵니다.
이 명령 형식을 사용하여 특정 작업을 검색할 수 있습니다.

### 예 3: 원격 컴퓨터에서 예약 된 작업 가져오기

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

이 명령은 컴퓨터에서 Servers.txt 파일에 나열된 모든 예약된 작업을 가져옵니다.
이 명령은 Invoke-Command cmdlet을 사용 하 여 각 컴퓨터에서 **ScheduleJob** 명령을 실행 합니다.

### 예제 4: 예약 된 작업을 다른 cmdlet으로 파이프

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

이 명령은 DailyBackup 및 WeeklyBackup 예약된 작업의 작업 트리거를 가져옵니다.
**Set-scheduledjob** cmdlet을 사용 하 여 예약 된 작업을 가져오고 Get-JobTrigger cmdlet을 사용 하 여 예약 된 작업의 작업 트리거를 가져옵니다.

## PARAMETERS

### -Id
지정한 ID를 가진 예약된 작업만 가져옵니다.
컴퓨터에 있는 예약된 작업의 ID 번호(ID)를 하나 이상 입력합니다.
기본적으로 **Get-ScheduledJob** 은 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
지정한 이름을 가진 예약된 작업만 가져옵니다.
컴퓨터에 있는 예약된 작업의 이름을 하나 이상 입력합니다.
와일드카드가 지원됩니다.
기본적으로 **Get-ScheduledJob** 은 컴퓨터에 있는 모든 예약된 작업을 가져옵니다.

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음
**Get-ScheduledJob** 에 입력을 파이프할 수 없습니다.

## 출력

### Set-scheduledjob. ScheduledJobDefinition

## 참고

* 각 예약된 작업은 로컬 컴퓨터에 있는 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 디렉터리의 하위 디렉터리에 저장됩니다. 하위 디렉터리는 예약된 작업에 따라 이름이 지정되며 예약된 작업에 대한 XML 파일과 실행 기록 레코드를 포함합니다. 예약된 작업에 대한 자세한 내용은 about_Scheduled_Jobs_Advanced를 참조하세요.
* Windows PowerShell에서 만든 예약된 작업은 작업 스케줄러의 Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs 폴더에 표시됩니다. 작업 스케줄러를 사용하여 예약된 작업을 보고 편집할 수 있습니다.
* 작업 스케줄러, SchTasks.exe 명령줄 도구 및 작업 스케줄러 cmdlet을 사용하여 예약된 작업 cmdlet으로 만든 예약된 작업을 관리할 수 있습니다. 그러나 예약된 작업 cmdlet을 사용하여 작업 스케줄러에서 만든 작업을 관리할 수는 없습니다.

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
