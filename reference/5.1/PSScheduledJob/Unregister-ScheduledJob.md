---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213370"
---
# Unregister-ScheduledJob

## 개요
로컬 컴퓨터에서 예약된 작업을 삭제합니다.

## SYNTAX

### 정의 (기본값)

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 인

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Build.definitionname

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Unregister-ScheduledJob** cmdlet은 로컬 컴퓨터에서 예약된 작업을 삭제합니다.

예약 된 작업을 삭제 하거나 등록 취소 하면 **set-scheduledjob** 는 예약 된 작업 ($home \appdata\local\microsoft\windows\powershell\scheduledjobs 디렉터리)에 대 한 디렉터리를 삭제 합니다. 여기에는 예약 된 작업, 작업 실행 기록 및 모든 작업 결과를 정의 하는 XML 파일이 포함 되어 있습니다.
이 작업은 작업 스케줄러에서 작업도 삭제합니다.

**Set-scheduledjob** 는 Register-ScheduledJob cmdlet을 사용 하 여 만든 예약 작업만 삭제 합니다.
작업 스케줄러에서 만들어진 예약된 작업은 삭제하지 않습니다.

**Set-scheduledjob** 의 매개 변수를 사용 하 여 ID 또는 이름으로 예약 된 작업을 삭제 하거나 Get-ScheduledJob에서 **set-scheduledjob** 로의 파이프 예약 된 작업을 수행할 수 있습니다.

**Set-scheduledjob** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 예약 된 작업 삭제

```
PS C:\> Unregister-ScheduledJob TestJob
```

이 명령은 로컬 컴퓨터에 있는 TestJob 예약된 작업을 삭제합니다.

### 예 2: 모든 예약 된 작업 삭제

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

이 예제에서는 로컬 컴퓨터에서 모든 예약 된 작업을 삭제 하는 두 가지 명령을 보여 줍니다.

첫 번째 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 모든 예약 된 작업을 가져옵니다.
파이프라인 연산자(|)가 예약된 작업을 **Unregister-ScheduleJob** 으로 보내면 이 cmdlet이 예약된 작업을 삭제합니다.

두 번째 명령은 *Unregister-ScheduledJob* 의 **Name** 매개 변수를 모두(*) 값으로 사용하여 모든 예약된 작업을 삭제합니다.

두 명령은 작업 인스턴스가 실행 중인 경우에도 예약된 작업을 삭제하는 *Force* 매개 변수를 사용합니다.

### 예 3: 원격 컴퓨터에서 예약 된 작업 삭제

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

이 명령은 이름이 Server01 원격 컴퓨터의 테스트로 시작 하는 예약 된 작업을 삭제 합니다.
이 명령은 Invoke-Command cmdlet을 사용 하 여 Server02 컴퓨터에서 **set-scheduledjob** 명령을 실행 합니다.

## PARAMETERS

### -Force
작업 인스턴스가 실행 중인 경우에도 예약된 작업을 삭제합니다.
기본적으로 **Unregister-ScheduledJob** 은 실행 중인 작업을 중단하지 않습니다.

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

### -Id
지정한 ID 번호(ID)를 가진 예약된 작업을 삭제합니다.
컴퓨터에 있는 예약된 작업의 ID를 입력합니다.

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
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
**Set-scheduledjob** 개체를 파이프 되지 않은 **jobtrigger** 로 파이프 할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
지정한 이름을 가진 예약된 작업을 삭제합니다.
컴퓨터에 있는 하나 이상 예약된 작업의 이름을 입력합니다.
와일드카드가 지원됩니다.

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

### -Confirm
cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Set-scheduledjob. ScheduledJobDefinition
예약된 작업을 Unregister-ScheduledJob으로 파이프할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

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
