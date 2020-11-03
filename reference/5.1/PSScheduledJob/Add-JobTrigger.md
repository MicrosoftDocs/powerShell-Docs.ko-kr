---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213497"
---
# Add-JobTrigger

## 개요
예약된 작업에 작업 트리거를 추가합니다.

## SYNTAX

### JobDefinition (기본값)

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### JobDefinitionId

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## 설명
**Add-JobTrigger** cmdlet은 예약된 작업에 작업 트리거를 추가합니다.
이 cmdlet을 사용하여 여러 개의 예약된 작업에 여러 트리거를 추가할 수 있습니다.

작업 트리거는 일회성 또는 되풀이 일정에 따라 또는 이벤트가 발생 하는 경우 예약 된 작업을 시작 합니다.

추가 **jobtrigger** 의 *trigger* 매개 변수를 사용 하 여 추가할 작업 트리거를 식별할 수 있습니다.
**추가 JobTrigger** 의 *Name* , *ID* 또는 *InputObject* 매개 변수를 사용 하 여 트리거가 추가 되는 예약 된 작업을 식별 합니다.

*Trigger* 매개 변수 값에 대 한 작업 트리거를 만들려면 New-JobTrigger cmdlet을 사용 하거나 해시 테이블을 사용 하 여 작업 트리거를 지정 합니다.

**추가 JobTrigger** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 예약 된 작업에 작업 트리거 추가

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

이 명령은 TestJob 예약된 작업에 Daily 작업 트리거를 추가합니다.

첫 번째 명령은 New-JobTrigger cmdlet을 사용 하 여 매일 오전 3:00에 예약 된 작업을 시작 하는 작업 트리거를 만듭니다.
이 명령은 $Daily 변수에 작업 트리거를 저장 합니다.

두 번째 명령은 **Add-JobTrigger** cmdlet을 사용하여 $Startup 변수의 작업 트리거를 TestJob 예약된 작업에 추가합니다.

### 예제 2: 몇 개의 예약 된 작업에 작업 트리거 추가

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

이 명령은 로컬 컴퓨터에 있는 모든 예약된 작업에 AtStartup 작업 트리거를 추가합니다.
Get-ScheduledJob를 사용 하 여 컴퓨터에 있는 모든 예약 된 작업을 가져옵니다.
파이프라인 연산자(|)를 사용하여 작업을 **Add-JobTrigger** cmdlet으로 보내면 이 cmdlet이 각 예약된 작업에 작업 트리거를 추가합니다.
*Trigger* 매개 변수 값은 atstartup 작업 트리거를 만드는 New-JobTrigger 명령입니다.

### 예제 3: 작업 트리거 복사

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

이 명령은 BackupArchives 예약된 작업에서 작업 트리거를 복사하여 TestBackup 및 BackupLogs 예약된 작업에 추가합니다.

첫 번째 명령은 Get-JobTrigger cmdlet을 사용 하 여 명령은 backuparchives 예약 된 작업의 작업 트리거를 가져옵니다.
트리거를 $t 변수에 저장합니다.

두 번째 명령은 **Add-JobTrigger** cmdlet을 사용하여 $t 변수의 작업 트리거를 TestBackup 및 BackupLogs 예약된 작업에 추가합니다.

## PARAMETERS

### -Id
예약된 작업의 ID 번호를 지정합니다.
**Add-JobTrigger** 는 지정한 예약된 작업에 작업 트리거를 추가합니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 id 번호를 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.

```yaml
Type: System.Int32[]
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
**Set-scheduledjob** 개체를 **추가 jobtrigger** 로 파이프 할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
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
**Add-JobTrigger** 는 지정한 예약된 작업에 작업 트리거를 추가합니다.
와일드카드가 지원됩니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 예약 된 작업의 이름을 가져오려면 Get-ScheduledJob cmdlet을 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -트리거
추가할 작업 트리거를 지정 합니다.
**ScheduledJobTrigger** 개체가 포함 된 작업 트리거 또는 변수를 지정 하는 해시 테이블을 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.
**ScheduledJobTrigger** 개체를 **추가 jobtrigger** 로 파이프 할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Set-scheduledjob. ScheduledJobTrigger, Set-scheduledjob. ScheduledJobDefinition.
작업 트리거 또는 예약된 작업을 **Add-JobTrigger** 로 파이프할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 반환되지 않습니다.

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
