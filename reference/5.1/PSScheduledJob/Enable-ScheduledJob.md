---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213449"
---
# Enable-ScheduledJob

## 개요
예약된 작업을 사용하도록 설정합니다.

## SYNTAX

### 정의 (기본값)

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 인

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Build.definitionname

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Set-scheduledjob** cmdlet은 Disable-ScheduledJob cmdlet을 사용 하 여 비활성화 된 작업 등 사용 하지 않도록 설정 된 예약 된 작업을 다시 사용 하도록 설정 합니다.
사용되는 작업은 트리거 시 자동으로 실행됩니다.

예약 된 작업을 사용 하도록 설정 하기 위해 **set-scheduledjob** cmdlet은 예약 된 작업의 Enabled 속성을 $True 설정 합니다.

**Enabled-set-scheduledjob** 은 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.

예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.
PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예제 1: 예약 된 작업을 사용 하도록 설정

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

이 명령은 로컬 컴퓨터에서 ID가 2인 예약된 작업을 사용하도록 설정합니다.
출력은 명령의 결과를 보여 줍니다.

### 예 2: 모든 예약 된 작업을 사용 하도록 설정

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

이 명령은 로컬 컴퓨터에서 모든 예약된 작업을 사용하도록 설정합니다.
Get-ScheduledJob cmdlet을 사용 하 여 모든 예약 된 작업을 가져오고 **set-scheduledjob** cmdlet을 사용 하 여 사용 하도록 설정 합니다.

이미 사용 하도록 설정 된 예약 된 작업을 사용 하도록 설정 하는 경우 **set-scheduledjob** 는 경고 또는 오류를 생성 하지 않으므로 조건 없이 모든 예약 된 작업을 사용 하도록 설정할 수 있습니다.

### 예 3: 선택한 예약 된 작업 사용

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

이 명령은 네트워크 연결이 필요 없는 예약된 작업을 사용하도록 설정합니다.

이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 컴퓨터에 있는 모든 예약 된 작업을 가져옵니다.
파이프라인 연산자는 예약 된 작업을 Get-ScheduledJobOption cmdlet으로 보냅니다 .이 cmdlet은 예약 된 각 작업의 작업 옵션을 가져옵니다.
각 작업 옵션 개체에는 관련 예약된 작업을 포함하는 JobDefinition 속성이 있습니다.
JobDefinition 속성은 명령을 완료하는 데 사용됩니다.

이 명령은 파이프라인 연산자 (|)를 사용 하 여 작업 옵션을 Where-Object cmdlet으로 보냅니다 .이 cmdlet은 **RunWithoutNetwork** 속성 값이 True ($true) 인 예약 된 작업 옵션 개체를 선택 합니다.
다른 파이프라인 연산자는 선택한 예약 된 작업 옵션 개체를 ForEach-Object cmdlet으로 보냅니다 .이 cmdlet은 예약 된 작업에서 각 작업 옵션 개체의 JobDefinition 속성 값에 있는 **set-scheduledjob** 명령을 실행 합니다.

### 예 4: 원격 컴퓨터에서 예약 된 작업을 사용 하도록 설정

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

이 명령은 두 원격 컴퓨터 Srv01 및 Srv10에서 이름에 "test"가 포함된 예약된 작업을 사용하도록 설정합니다.

이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 및 Srv10 컴퓨터에서 **set-scheduledjob** 명령을 실행 합니다.
*Enable-ScheduledJob* 의 **Name** 매개 변수를 사용하여 각 컴퓨터에서 Inventory 예약된 작업을 사용하도록 설정합니다.

## PARAMETERS

### -Id
지정한 ID를 가진 예약된 작업을 사용하도록 설정합니다.
예약된 작업의 ID를 입력합니다.

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
사용할 예약 된 작업을 지정 합니다.
**ScheduledJobDefinition** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobDefinition** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.
**ScheduledJobDefinition** 개체를 **Enable-ScheduledJob** 으로 파이프할 수도 있습니다.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
지정한 이름을 가진 예약된 작업을 사용하도록 설정합니다.
예약된 작업의 이름을 입력합니다.
와일드카드가 지원됩니다.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
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
예약 된 작업을 Set-scheduledjob로 파이프 하 여 **설정할** 수 있습니다.

## 출력

### None 또는 Set-scheduledjob. ScheduledJobDefinition
**Passthru** 매개 변수를 사용할 경우 **Enable-ScheduledJob** 은 사용하도록 설정된 예약된 작업을 반환합니다.
그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

* 사용 하도록 설정 된 예약 된 작업을 사용 하도록 설정 하는 데 사용 하는 경우 **set-scheduledjob** 는 경고 또는 오류를 생성 하지 않습니다.

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
