---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213442"
---
# Enable-JobTrigger

## 개요
예약된 작업의 작업 트리거를 사용하도록 설정합니다.

## SYNTAX

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**JobTrigger** cmdlet은 Disable-JobTrigger cmdlet을 사용 하 여 사용 하지 않도록 설정한 것과 같은 예약 된 작업의 작업 트리거를 다시 사용 하도록 설정 합니다.
사용되는 작업 트리거 및 다시 사용하도록 설정된 작업 트리거는 예약된 작업을 즉시 시작할 수 있으므로 Windows 또는 Windows PowerShell을 다시 시작하지 않아도 됩니다.

이 cmdlet을 사용 하려면 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.
그런 다음 작업 트리거를 **-JobTrigger** 를 사용 하도록 파이프 하거나 *InputObject* 매개 변수를 사용 합니다.

작업 트리거를 사용 하도록 설정 하기 위해 **-jobtrigger** cmdlet은 작업 트리거의 Enabled 속성을 $True 설정 합니다.

**Set-scheduledjob** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 작업 트리거를 사용 하도록 설정

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

이 명령은 로컬 컴퓨터에 있는 Backup-Archives 예약된 작업의 첫 번째 트리거(ID=1)를 사용하도록 설정합니다.

이 명령은 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.
파이프라인 연산자가 작업 트리거를 **Enable-JobTrigger** cmdlet으로 보내면 이 cmdlet이 작업 트리거를 사용하도록 설정합니다.

### 예제 2: 모든 작업 트리거를 사용 하도록 설정

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.
파이프라인 연산자 (|)가 예약 된 작업의 모든 작업 트리거를 가져오는 Get-JobTrigger cmdlet으로 예약 된 작업을 보냅니다.
다른 파이프라인 연산자가 작업 트리거를 **Enable-JobTrigger** cmdlet으로 보내면 이 cmdlet이 작업 트리거를 사용하도록 설정합니다.

### 예 3: 원격 컴퓨터에서 예약 된 작업의 작업 트리거를 사용 하도록 설정

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

이 명령은 Server01 원격 컴퓨터에 있는 DeployPackage 예약된 작업의 AtLogon 작업 트리거를 다시 사용하도록 설정합니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.
원격 명령은 Get-JobTrigger cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 트리거를 가져옵니다.
파이프라인 연산자는 AtLogon 작업 트리거도 반환 하는 Where-Object cmdlet으로 작업 트리거를 보냅니다.
파이프라인 연산자가 AtLogon 작업 트리거를 사용 하도록 설정 하는 **jobtrigger** cmdlet으로 보냅니다.

### 예 4: 비활성화 된 작업 트리거 표시

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

이 명령은 모든 예약된 작업의 사용되지 않는 모든 작업 트리거를 테이블로 표시합니다.
이러한 명령을 통해 사용하도록 설정해야 하는 작업 트리거를 검색할 수 있습니다.

이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 예약 된 작업을 가져옵니다.
파이프라인 연산자 (|)가 예약 된 작업의 모든 작업 트리거를 가져오는 Get-JobTrigger cmdlet으로 예약 된 작업을 보냅니다.
다른 파이프라인 연산자가 작업 트리거를 Where-Object cmdlet으로 보냅니다 .이 cmdlet은 비활성화 된 작업 트리거만 반환 합니다. 즉, 작업 트리거의 Enabled 속성 값이 (!) true가 아닙니다.

다른 파이프라인 연산자는 사용 하지 않도록 설정 된 작업 트리거를 Format-Table cmdlet으로 보냅니다 .이 cmdlet은 테이블에서 작업 트리거의 선택 된 속성을 표시 합니다.
속성에는 작업 트리거의 JobDefinition 속성에 있는 예약된 작업의 이름을 표시하는 새 JobName 속성이 포함됩니다.

## PARAMETERS

### -InputObject
사용 하도록 설정할 작업 트리거를 지정 합니다.
**ScheduledJobTrigger** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.
**ScheduledJobTrigger** 개체를 파이프 하 여 **-Jobtrigger를 사용 하도록 설정할** 수도 있습니다.

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

### Set-scheduledjob. ScheduledJobTrigger
작업 트리거를 사용 하도록 설정 하 여 **JobTrigger를 설정할** 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 이미 사용 하도록 설정 된 작업 트리거를 사용 하도록 설정 하는 경우 **-JobTrigger** 는 오류 또는 경고를 생성 하지 않습니다.

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
