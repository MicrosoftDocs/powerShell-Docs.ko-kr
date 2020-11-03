---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213410"
---
# Remove-JobTrigger

## 개요
예약 된 작업에서 작업 트리거를 삭제 합니다.

## SYNTAX

### JobDefinition (기본값)

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### JobDefinitionId

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## 설명
**Remove JobTrigger** cmdlet은 예약 된 작업에서 작업 트리거를 삭제 합니다.

작업 트리거는 예약 된 작업을 시작 하기 위한 되풀이 일정 또는 조건을 정의 합니다.
작업 트리거를 관리 하려면 New-JobTrigger, Add JobTrigger, Set JobTrigger 및 Set-ScheduledJob cmdlet을 사용 합니다.

*Remove-JobTrigger* 의 *Name* , *ID* 또는 **InputObject** 매개 변수를 사용하여 트리거를 제거할 예약된 작업을 식별할 수 있습니다.
*TriggerID* 매개 변수를 사용 하 여 삭제할 작업 트리거를 식별 합니다.
기본적으로 **Remove-JobTrigger** 는 예약된 작업의 모든 작업 트리거를 삭제합니다.

**Remove JobTrigger** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 모든 작업 트리거 삭제

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

이 명령은 예약 된 작업에서 이름이 Test로 시작 하는 모든 작업 트리거를 삭제 합니다.

### 예 2: 선택한 작업 트리거 삭제

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

이 명령은 BackupArchive 예약된 작업에서 세 번째 트리거(ID = 3)만 삭제합니다.

### 예 3: 모든 예약 된 작업에서 AtStartup 작업 트리거 삭제

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

이 함수는 로컬 컴퓨터의 모든 작업에서 모든 AtStartup 작업 트리거를 삭제합니다.
함수를 사용 하려면 세션에서 함수를 실행 한 다음를 입력 `Delete-AtStartup` 합니다.

Delete-AtStartup 함수에는 하나의 명령이 포함되어 있습니다.
이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.
파이프라인 연산자 (|)가 예약 된 작업을 Get-JobTrigger cmdlet으로 보내면이 cmdlet이 각 예약 된 작업의 모든 작업 트리거를 가져옵니다.
파이프라인 연산자가 작업 트리거를 Where-Object cmdlet으로 보냅니다 .이 cmdlet은 작업 트리거의 Frequency 속성 값이 AtStartup과 같은 작업 트리거를 선택 합니다.

**Jobtrigger** 개체에는 트리거하는 예약 된 작업을 포함 하는 **JobDefinition** 속성이 있습니다.
명령의 나머지 부분에서는 이 유용한 기능을 사용합니다.

파이프라인 연산자는 AtStartup 작업 트리거를 ForEach-Object cmdlet으로 보냅니다 .이 cmdlet은 각 AtStartup 트리거에서 **Remove jobtrigger** 명령을 실행 합니다.
**JobTrigger** 의 *InputObject* 매개 변수 값은 작업 트리거의 JobDefinition 속성에 있는 예약 된 작업입니다.
*TriggerID* 매개 변수의 값은 작업 트리거의 ID 속성에 있는 식별자입니다.

### 예 4: 원격 예약 된 작업에서 작업 트리거 삭제

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

이 명령은 Server01 컴퓨터의 Inventory 작업에서 첫 번째 작업 트리거를 삭제합니다.

이 명령은 **Invoke 명령** cmdlet을 사용 하 여 Server01 컴퓨터에서 **Remove jobtrigger** cmdlet을 실행 합니다.
**Remove JobTrigger** Cmdlet은 *ID* 매개 변수를 사용 하 여 Inventory 예약 된 작업을 식별 하 고 *TriggerID* 매개 변수를 사용 하 여 첫 번째 트리거를 지정 합니다.
*ID* 매개 변수는 특히 여러 개의 예약 된 작업에서 이름이 같거나 비슷한 경우에 유용 합니다.

## PARAMETERS

### -Id
예약된 작업의 ID 번호를 지정합니다.
**Remove-JobTrigger** 는 지정한 예약된 작업에서 작업 트리거를 삭제합니다.

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
**Set-scheduledjob** 개체를 **제거-jobtrigger** 로 파이프 할 수도 있습니다.

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
**Remove-JobTrigger** 는 지정한 예약된 작업에서 작업 트리거를 삭제합니다.
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

### -TriggerId
지정한 작업 트리거만 삭제합니다.
기본적으로 **Remove-JobTrigger** 는 예약된 작업에서 모든 트리거를 삭제합니다.
예약된 작업에 여러 개의 작업 트리거가 있는 경우 이 매개 변수를 사용합니다.

예약된 작업의 하나 이상 작업 트리거에 대한 트리거 ID를 입력합니다.
여러 개의 예약 된 작업을 지정 하는 경우 **JobTrigger** 는 모든 예약 된 작업에서 지정 된 ID의 작업 트리거를 삭제 합니다.

```yaml
Type: System.Int32[]
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

### Set-scheduledjob. ScheduledJobDefinition
예약된 작업을 **Remove-JobTrigger** cmdlet으로 파이프할 수 있습니다.

## 출력

### 없음
이 cmdlet에서 어떠한 출력도 생성되지 않습니다.

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
