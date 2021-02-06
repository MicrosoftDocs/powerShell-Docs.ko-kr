---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: fe28f52088a82b93799724de7a7a3f20ce42e36b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605015"
---
# Out-Null

## 개요
파이프라인으로 보내거나 표시 하지 않고 출력을 숨깁니다.

## SYNTAX

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명

**Out-null** cmdlet은 결과를 null로 보내 파이프라인에서 제거 하 고 출력이 화면에 표시 되는 것을 방지 합니다.

## 예제

### 예제 1: 출력 삭제

```powershell
Get-ChildItem | Out-Null
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

* **Out** 동사를 포함 하는 Cmdlet ( **out** cmdlet)에는 이름이 나 파일 경로에 대 한 매개 변수가 없습니다. **Out** cmdlet에 데이터를 보내려면 파이프라인 연산자 (|)를 사용 하 여 PowerShell 명령의 출력을 cmdlet으로 보냅니다. 데이터를 변수에 저장하고 *InputObject* 매개 변수를 사용하여 데이터를 cmdlet으로 전달할 수도 있습니다. 자세한 내용은 예제를 참조하세요.
* **Out-Null** 은 출력 개체를 반환 하지 않습니다. **Out-Null** 출력을 Get-Member cmdlet에 파이프 하면 개체가 지정 되지 않은 것 **으로 보고 됩니다** .

## 관련 링크

[Out-Default](Out-Default.md)

[Out-Host](Out-Host.md)

