---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: d136dd46eaceb65b5c512e3ff5c98e13d685d45e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216634"
---
# Get-TraceSource

## 개요
추적을 위해 계측 된 PowerShell 구성 요소를 가져옵니다.

## SYNTAX

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## 설명

**TraceSource** cmdlet은 현재 사용 중인 PowerShell 구성 요소의 추적 원본을 가져옵니다.
데이터를 사용 하 여 추적할 수 있는 PowerShell 구성 요소를 확인할 수 있습니다.
추적할 때 구성 요소가 내부 처리의 각 단계에 대한 상세 메시지를 생성합니다.
개발자는 추적 데이터를 사용하여 데이터 흐름, 프로그램 실행 및 오류를 모니터링합니다.

추적 cmdlet은 PowerShell 개발자 용으로 만들어졌지만 모든 사용자가 사용할 수 있습니다.

## 예제

### 예제 1: 이름별로 추적 소스 가져오기

```
PS C:\> Get-TraceSource -Name "*provider*"
```

이 명령은 공급자가 포함 된 이름이 있는 추적 원본을 모두 가져옵니다.

### 예제 2: 모든 추적 원본 가져오기

```
PS C:\> Get-TraceSource
```

이 명령은 추적할 수 있는 모든 PowerShell 구성 요소를 가져옵니다.

## PARAMETERS

### -Name

가져올 추적 소스를 지정 합니다.
와일드카드가 지원됩니다.
매개 변수 이름 *이름은* 선택 사항입니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

추적 소스의 이름을 포함 하는 문자열을 **TraceSource** 로 파이프 할 수 있습니다.

## 출력

### 시스템 관리..

**TraceSource** 는 추적 원본을 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

[Set-TraceSource](Set-TraceSource.md)

[Trace-Command](Trace-Command.md)
