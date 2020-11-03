---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213490"
---
# Disable-JobTrigger

## 개요
예약된 작업의 작업 트리거를 사용하지 않도록 설정합니다.

## SYNTAX

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Disable-JobTrigger** cmdlet은 예약된 작업의 작업 트리거를 일시적으로 사용하지 않도록 설정합니다.
사용하지 않도록 설정할 경우 모든 작업 트리거 속성이 유지되지만 작업 트리거가 예약된 작업을 시작할 수 없습니다.

이 cmdlet을 사용 하려면 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.
작업 트리거를 **Disable-JobTrigger** 로 파이프하거나 해당 *InputObject* 매개 변수를 사용합니다.

작업 트리거를 사용 하지 않도록 설정 하기 위해 no **jobtrigger** cmdlet은 작업 트리거의 Enabled 속성을 $False 설정 합니다.
작업 트리거를 다시 사용 하도록 설정 하려면 Enable-JobTrigger cmdlet을 사용 합니다 .이 cmdlet은 작업 트리거의 **Enabled** 속성을 $True로 설정 합니다.
작업 트리거를 사용 하지 않도록 설정 해도 Disable-ScheduledJob cmdlet에서 수행 하는 것과 같이 예약 된 작업을 사용 하지 않도록 설정 하는 것은 아니지만 모든 작업 트리거를 사용 하지 않도록 설정 하는 경우 효과는 예약 된 작업을 사용 하지 않도록

예약 된 작업을 사용 하지 않도록 설정 하거나 예약 된 작업의 모든 작업 트리거를 사용 하지 않도록 설정 하는 경우에도 Start-Job cmdlet을 사용 하 여 작업을 시작 하거나 사용 되지 않는 예약 된 작업을 템플릿으로 사용할 수 있습니다.

**Set-scheduledjob** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 작업 트리거 사용 안 함

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

이 명령은 로컬 컴퓨터에 있는 Backup-Archives 예약된 작업의 첫 번째 트리거(ID=1)를 사용하지 않도록 설정합니다.

이 명령은 Get-JobTrigger cmdlet을 사용 하 여 작업 트리거를 가져옵니다.
파이프라인 연산자가 작업 트리거를 **Disable-JobTrigger** cmdlet으로 보내면 이 cmdlet이 작업 트리거를 사용하지 않도록 설정합니다.

### 예제 2: 모든 작업 트리거 사용 안 함

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

이 명령은 두 예약된 작업의 모든 작업 트리거를 사용하지 않도록 설정하고 결과를 표시합니다.

### 예 3: 원격 컴퓨터에서 예약 된 작업의 작업 트리거를 사용 하지 않도록 설정

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

이 명령은 Server01 원격 컴퓨터에 있는 DeployPackage 예약된 작업의 일별 작업 트리거를 사용하지 않도록 설정합니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 컴퓨터에서 명령을 실행 합니다.
원격 명령은 Get-JobTrigger cmdlet을 사용 하 여 있는 deploypackage 예약 된 작업의 작업 트리거를 가져옵니다.
파이프라인 연산자가 작업 트리거를 Where-Object cmdlet으로 보내면이 cmdlet이 일별 작업 트리거도 반환 합니다.
파이프라인 연산자는 일별 작업 트리거를 사용 하지 않도록 설정 하는 **jobtrigger** cmdlet으로 보냅니다.

## PARAMETERS

### -InputObject
사용하지 않도록 설정할 작업 트리거를 지정합니다.
**ScheduledJobTrigger** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobTrigger** 개체를 가져오는 명령 또는 식 (예: Get-JobTrigger 명령)을 입력 합니다.
**ScheduledJobTrigger** 개체를 파이프 하 여 **-Jobtrigger를 사용 하지 않도록 설정할** 수도 있습니다.

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
작업 트리거를 **Disable-JobTrigger** 로 파이프할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* 이미 사용 하지 않도록 설정 된 작업 트리거를 사용 하지 않도록 설정 하는 경우 **-JobTrigger** 는 오류 또는 경고를 생성 하지 않습니다.

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
