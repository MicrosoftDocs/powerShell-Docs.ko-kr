---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215609"
---
# Checkpoint-Computer

## 개요
로컬 컴퓨터에 시스템 복원 지점을 만듭니다.

## SYNTAX

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## 설명

`Checkpoint-Computer`Cmdlet은 로컬 컴퓨터에 시스템 복원 지점을 만듭니다.

시스템 복원 지점과 `Checkpoint-Computer` cmdlet은 windows 8, windows 7, Windows Vista 및 WINDOWS XP와 같은 클라이언트 운영 체제 에서만 지원 됩니다.

Windows 8부터는 `Checkpoint-Computer` 매일 둘 이상의 검사점을 만들 수 없습니다.

## 예제

### 예 1: 시스템 복원 지점 만들기

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

이 명령은 Install MyApp 라는 시스템 복원 지점을 만듭니다.
"Install MyApp"라는 시스템 복원 지점을 만듭니다.

### 예 2: 시스템 MODIFY_SETTINGS 복원 지점 만들기

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

이 명령은 "ChangeNetSettings"라는 MODIFY_SETTINGS 시스템 복원 지점을 만듭니다.

## PARAMETERS

### -Description

복원 지점에 대한 설명이 포함된 이름을 지정합니다.
이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePointType

복원 지점의 유형을 지정합니다.
기본값은 APPLICATION_INSTALL입니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- APPLICATION_INSTALL
- APPLICATION_UNINSTALL
- DEVICE_DRIVER_INSTALL
- MODIFY_SETTINGS
- CANCELLED_OPERATION

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### 없음

개체를에 연결할 수 없습니다 `Checkpoint-Computer` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

- 이 cmdlet은 **BEGIN_SYSTEM_CHANGE** 이벤트와 함께 **SystemRestore** 클래스의 **CreateRestorePoint** 메서드를 사용 합니다.
- Windows 8부터는 `Checkpoint-Computer` 매일 둘 이상의 시스템 복원 지점을 만들 수 없습니다. 24시간이 지나기 전에 새 복원 지점을 만들려고 하면 Windows PowerShell에서 다음 오류를 생성합니다.

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## 관련 링크

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restore-Computer](Restore-Computer.md)
