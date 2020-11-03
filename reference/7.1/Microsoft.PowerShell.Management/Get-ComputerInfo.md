---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: c8f24d7b020a75bae121c054550c8aed2c55074f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217650"
---
# Get-ComputerInfo

## 개요
시스템 및 운영 체제 속성의 통합 개체를 가져옵니다.

## SYNTAX

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## 설명

`Get-ComputerInfo`Cmdlet은 시스템 및 운영 체제 속성의 통합 개체를 가져옵니다.
이 cmdlet은 Windows PowerShell 5.1에서 도입 되었습니다.

## 예제

### 예제 1: 모든 컴퓨터 속성 가져오기

```powershell
Get-ComputerInfo
```

이 명령은 컴퓨터에서 모든 시스템 및 운영 체제 속성을 가져옵니다.

### 예제 2: 모든 컴퓨터 운영 체제 속성 가져오기

```powershell
Get-ComputerInfo -Property "os*"
```

이 명령은 컴퓨터에서 모든 운영 체제 속성을 가져옵니다.

## PARAMETERS

### -속성

이 cmdlet이 표시 되는 컴퓨터 속성을 문자열 배열로 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String[]

## 출력

### Microsoft. PowerShell. 관리 정보

## 참고

## 관련 링크

