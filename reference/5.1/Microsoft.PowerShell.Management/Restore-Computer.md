---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214474"
---
# Restore-Computer

## 개요
로컬 컴퓨터에서 시스템 복원을 시작합니다.

## SYNTAX

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Restore-computer** cmdlet은 로컬 컴퓨터를 지정한 시스템 복원 지점으로 복원 합니다.

**복원-** 컴퓨터를 다시 시작 합니다.
다시 시작 작업 중 복원이 완료됩니다.

시스템 복원 지점과 **복원-컴퓨터** 는 windows 7, windows Vista 및 windows XP와 같은 클라이언트 운영 체제 에서만 지원 됩니다.

## 예제

### 예 1: 로컬 컴퓨터 복원

```
PS C:\> Restore-Computer -RestorePoint 253
```

이 명령은 로컬 컴퓨터를 시퀀스 번호가 253 인 복원 지점으로 복원 합니다.

### 예 2: 확인을 사용 하 여 로컬 컴퓨터 복원

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

이 명령은 로컬 컴퓨터를 시퀀스 번호가 255 인 복원 지점으로 복원 합니다.
*Confirm* 매개 변수를 사용 하 여 실제로 작업을 수행 하기 전에 사용자에 게 메시지를 표시 합니다.

### 예 3: 컴퓨터 복원 및 상태 확인

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

이 명령은 시스템 복원을 실행한 다음 상태를 확인합니다.

첫 번째 명령은 **get-computerrestorepoint** 를 사용 하 여 로컬 컴퓨터의 복원 위치를 가져옵니다.

두 번째 명령은 시퀀스 번호가 255 인 복원 지점으로 컴퓨터를 복원 합니다.

세 번째 명령은 *get-computerrestorepoint* Cmdlet의 *LastStatus* 매개 변수를 사용 하 여 복원 작업의 상태를 확인 합니다.
**복원 컴퓨터** 는 강제로 다시 시작 되기 때문에 컴퓨터가 다시 시작 된 후이 명령이 입력 됩니다.

## PARAMETERS

### -RestorePoint
복원 지점의 시퀀스 번호를 지정합니다.
시퀀스 번호를 찾으려면 Get-ComputerRestorePoint cmdlet을 사용 합니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

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

### 없음
이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* Windows Vista 이상 버전의 windows 운영 체제에서 Restore-Computer 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 엽니다.
* 이 cmdlet은 WMI(Windows Management Instrumentation) (WMI) **SystemRestore** 클래스를 사용 합니다.

## 관련 링크

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)
