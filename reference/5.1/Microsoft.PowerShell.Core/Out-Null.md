---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 5a949629cdf0f0822866863822e82e70fc38d8c2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212842"
---
# Out-Null

## 개요
파이프라인으로 보내거나 표시 하지 않고 출력을 숨깁니다.

## SYNTAX

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명
**Out-null** cmdlet은 결과를 null로 보내 파이프라인에서 제거 하 고 출력이 화면에 표시 되는 것을 방지 합니다. 표준 출력 스트림에만 영향을 줍니다.
오류 스트림과 같은 다른 출력 스트림은 영향을 받지 않습니다. 예외가 표시 됩니다. 이렇게 하면 오류에 대 한 명령을 더 쉽게 테스트할 수 있습니다.

## 예제

### 예제 1: 출력 삭제

```
PS C:\> Get-ChildItem | Out-Null
```

이 명령은 현재 위치/디렉터리에 있는 항목을 가져오지만 출력은 파이프라인을 통해 전달 되거나 명령줄에 표시 되지 않습니다.
이는 필요 하지 않은 출력을 숨기는 데 유용 합니다.

## PARAMETERS

### -InputObject
NULL로 보낼 개체를 지정 합니다 (파이프라인에서 제거 됨).
개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject
모든 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음
이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

* **Out** 동사를 포함 하는 Cmdlet ( **out** cmdlet)에는 이름이 나 파일 경로에 대 한 매개 변수가 없습니다. 데이터를 **Out** cmdlet으로 보내려면 파이프라인 연산자(|)를 사용하여 Windows PowerShell 명령의 출력을 cmdlet으로 보냅니다. 데이터를 변수에 저장하고 *InputObject* 매개 변수를 사용하여 데이터를 cmdlet으로 전달할 수도 있습니다. 자세한 내용은 예제를 참조하세요.
* **Out-Null** 은 출력 개체를 반환 하지 않습니다. **Out-Null** 출력을 Get-Member cmdlet에 파이프 하면 개체가 지정 되지 않은 것 **으로 보고 됩니다** .

## 관련 링크

[Out-Default](Out-Default.md)

[Out-Host](Out-Host.md)
