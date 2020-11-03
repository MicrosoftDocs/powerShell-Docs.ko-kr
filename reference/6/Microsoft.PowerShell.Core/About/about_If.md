---
description: 하나 이상의 조건부 테스트의 결과에 따라 문 목록을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 7f63b6f12743390608e0da72adb4098ce0583751
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221561"
---
# <a name="about-if"></a>If 정보

## <a name="short-description"></a>간단한 설명
하나 이상의 조건부 테스트의 결과에 따라 문 목록을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.

## <a name="long-description"></a>자세한 설명

`If`지정 된 조건 테스트가 true로 평가 되는 경우 문을 사용 하 여 코드 블록을 실행할 수 있습니다. 모든 이전 테스트가 false로 평가 되는 경우 실행할 하나 이상의 추가 조건부 테스트를 지정할 수도 있습니다. 마지막으로, 다른 이전 조건 테스트가 true로 평가 되지 않으면 실행 되는 추가 코드 블록을 지정할 수 있습니다.

### <a name="syntax"></a>구문

다음 예에서는 `If` 문 구문을 보여 줍니다.

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

문을 실행 하면 `If` PowerShell은 `<test1>` 조건식을 true 또는 false로 평가 합니다. `<test1>`이 true 이면를 `<statement list 1>` 실행 하 고 PowerShell은 `If` 문을 종료 합니다. `<test1>`가 false 인 경우 PowerShell은 조건문에 지정 된 조건을 평가 합니다 `<test2>` .

`<test2>`이 true 이면를 `<statement list 2>` 실행 하 고 PowerShell은 `If` 문을 종료 합니다. 및가 `<test1>` 모두 `<test2>` false로 평가 되 면 `<statement list 3`> 코드 블록이 실행 되 고 PowerShell에서 if 문을 종료 합니다.

여러 Elseif 문을 사용 하 여 일련의 조건부 테스트를 연결할 수 있습니다. 따라서 각 테스트는 이전 테스트가 모두 false 인 경우에만 실행 됩니다.
`If`여러 Elseif 문을 포함 하는 문을 만들어야 하는 경우 Switch 문을 대신 사용 하는 것이 좋습니다.

예제:

가장 간단한 `If` 문에는 단일 명령이 포함 되 고 Elseif 문이나 Else 문은 포함 되지 않습니다. 다음 예에서는 문의 가장 간단한 형식을 보여 줍니다 `If` .

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

이 예에서는 $a 변수가 2 보다 크면 조건이 true로 평가 되 고 문 목록이 실행 됩니다. 그러나 $a이 2 보다 작거나 같거나 기존 변수가 아니면 `If` 문에 메시지가 표시 되지 않습니다.

Else 문을 추가 하면 $a이 2 보다 작거나 같은 경우 메시지가 표시 됩니다. 다음 예제와 같이 표시 됩니다.

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

이 예를 추가로 구체화 하려면 $a 값이 2 인 경우 Elseif 문을 사용 하 여 메시지를 표시할 수 있습니다. 다음 예제와 같이 표시 됩니다.

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

## <a name="see-also"></a>참고 항목

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Switch](about_Switch.md)
