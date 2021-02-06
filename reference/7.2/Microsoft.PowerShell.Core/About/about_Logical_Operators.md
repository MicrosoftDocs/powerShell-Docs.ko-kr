---
description: PowerShell에서 문을 연결 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 8602551f3ecf74027b59715e1f47aab1b10bea92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601433"
---
# <a name="about_logical_operators"></a>about_Logical_Operators

## <a name="short-description"></a>간단한 설명
PowerShell에서 문을 연결 하는 연산자에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell 논리 연산자는 식과 문을 연결 하 여 여러 조건을 테스트할 단일 식을 사용할 수 있도록 합니다.

예를 들어 다음 문에서는 and 연산자와 or 연산자를 사용 하 여 세 개의 조건문을 연결 합니다. $A 값이 $b 값 보다 크고 $a 또는 $b가 보다 작은 경우에만 문은 true입니다.
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

PowerShell은 다음과 같은 논리 연산자를 지원 합니다.

|연산자|설명                        |예제                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |논리 AND. 둘 다        |`(1 -eq 1) -and (1 -eq 2)`|
|        |문은 TRUE입니다.               |`False`                   |
|`-or`   |논리 OR. 다음 중 하나에 해당 하는 경우 TRUE       |`(1 -eq 1) -or (1 -eq 2)` |
|        |문은 TRUE입니다.                 |`True`                    |
|`-xor`  |논리적 배타적 OR입니다. 다음의 경우 TRUE    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |문은 하나 뿐입니다.         |`False`                   |
|`-not`  |논리적 not. 문을 부정 합니다. |`-not (1 -eq 1)`          |
|        |이는 다음과 같습니다.                      |`False`                   |
|`!`     |`-not`과 동일                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 참고:

이전 예제에서는 같음 비교 연산자를 사용 합니다 `-eq` . 자세한 내용은 [about_Comparison_Operators](about_Comparison_Operators.md)를 참조 하세요. 또한이 예제에서는 정수의 부울 값을 사용 합니다. 정수 0의 값은 FALSE입니다. 다른 모든 정수의 값은 TRUE입니다.

논리 연산자의 구문은 다음과 같습니다.

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

논리 연산자를 사용 하는 문은 부울 값 (TRUE 또는 FALSE)을 반환 합니다.

PowerShell 논리 연산자는 문의 참 값을 확인 하는 데 필요한 문만 계산 합니다. And 연산자를 포함 하는 문의 왼쪽 피연산자가 FALSE 이면 오른쪽 피연산자가 계산 되지 않습니다.
또는 문이 포함 된 문의 왼쪽 피연산자가 TRUE 이면 오른쪽 피연산자가 계산 되지 않습니다. 따라서 문을 사용 하는 것과 같은 방법으로 이러한 문을 사용할 수 있습니다 `If` .

## <a name="see-also"></a>참고 항목

[about_Operators](about_Operators.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[about_Comparison_operators](about_Comparison_Operators.md)

[about_If](about_If.md)

