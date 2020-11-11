---
description: PowerShell 연산자를 우선 순위 대로 나열 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 62b49476760192386ae2c583fd9b7699e893134c
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483063"
---
# <a name="about-operator-precedence"></a>연산자 우선 순위 정보

## <a name="short-description"></a>간단한 설명
PowerShell 연산자를 우선 순위 대로 나열 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell 연산자를 사용 하 여 간단 하지만 강력한 식을 생성할 수 있습니다. 이 항목에서는 연산자를 우선 순위 대로 나열 합니다. 우선 순위는 동일한 식에 여러 개의 연산자가 나타날 때 PowerShell에서 연산자를 평가 하는 순서입니다.

연산자의 우선 순위가 같으면 PowerShell은 식에 표시 된 대로 왼쪽에서 오른쪽으로 계산 합니다. 예외는 오른쪽에서 왼쪽으로 계산 되는 할당 연산자, 캐스트 연산자 및 부정 연산자 ( `!` , `-not` , `-bnot` )입니다.

괄호와 같은 인클로저를 사용 하 여 표준 우선 순위를 재정의 하 고 PowerShell에서 식에 포함 되지 않은 부분을 계산 하도록 강제할 수 있습니다.

다음 목록에서는 연산자가 평가 되는 순서 대로 나열 되어 있습니다. 같은 줄 또는 같은 그룹에 있는 연산자는 우선 순위가 같습니다.

연산자 열에 연산자가 나열 됩니다. 참조 열에는 연산자가 설명 된 PowerShell 도움말 항목이 나열 됩니다. 항목을 표시 하려면를 입력 `get-help <topic-name>` 합니다.

|         OPERATOR         |           참조            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | [about_Operators][]            |
| `.` (멤버 액세스)      | [about_Operators][]            |
| `::` 정적인            | [about_Operators][]            |
| `[0]` (인덱스 연산자)   | [about_Operators][]            |
| `[int]` (캐스트 연산자) | [about_Operators][]            |
| `-split` 플러스         | [about_Split][]                |
| `-join` 플러스          | [about_join][]                 |
| `,` (쉼표 연산자)     | [about_Operators][]            |
| `++ --`                  | [about_assignment_operators][] |
| `! -not`                 | [about_Logical_Operators][]    |
| `..` (범위 연산자)    | [about_Operators][]            |
| `-f` (format 연산자)   | [about_Operators][]            |
| `-` (단항/부정)     | [about_arithmetic_operators][] |
| `* / %`                  | [about_arithmetic_operators][] |
| `+ -`                    | [about_arithmetic_operators][] |

다음 연산자 그룹의 우선 순위가 동일 합니다. 대/소문자를 구분 하 고 명시적으로 대/소문자를 구분 하지 않는 변형은 동일한 우선 순위를 갖습니다.

|         OPERATOR          |           참조            |
| ------------------------- | ------------------------------ |
| `-split` 바이너리         | [about_Split][]                |
| `-join` 바이너리          | [about_join][]                 |
| `-is -isnot -as`          | [about_Type_Operators][]       |
| `-eq -ne -gt -gt -lt -le` | [about_Comparison_Operators][] |
| `-like -notlike`          | [about_Comparison_Operators][] |
| `-match -notmatch`        | [about_Comparison_Operators][] |
| `-in -notIn`              | [about_Comparison_Operators][] |
| `-contains -notContains`  | [about_Comparison_Operators][] |
| `-replace`                | [about_Comparison_Operators][] |

다음 연산자가 우선 순위 대로 나열 됩니다.

|                OPERATOR                 |           참조            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | [about_arithmetic_operators][] |
| `-and -or -xor`                         | [about_Logical_Operators][]    |

다음 항목은 진정한 연산자가 아닙니다. 이러한 구문은 식 구문이 아니라 PowerShell의 명령 구문에 포함 되어 있습니다. 할당은 항상 마지막으로 발생 하는 동작입니다.

|                SYNTAX                   |           참조            |
| --------------------------------------- | ------------------------------ |
| `.` (점 소스)                        | [about_Operators][]            |
| `&` 전화할                              | [about_Operators][]            |
| <code>&#124;</code> (파이프라인 연산자) | [about_Operators][]            |
| `> >> 2> 2>> 2>&1`                      | [about_Redirection][]          |
| `= += -= *= /= %=`                      | [about_assignment_operators][] |

## <a name="examples"></a>예제

다음 두 명령은 산술 연산자와 괄호를 사용 하 여 PowerShell이 식의 포함 된 부분을 먼저 평가 하도록 하는 결과를 보여 줍니다.

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

다음 예에서는 로컬 디렉터리에서 읽기 전용 텍스트 파일을 가져와서 변수에 저장 합니다 `$read_only` .

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

다음 예제와 동일 합니다.

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

파이프라인 연산자 ()는 `|` 대입 연산자 () 보다 우선 순위가 높기 때문에 `=` cmdlet이 가져오는 파일을 `Get-ChildItem` `Where-Object` 변수에 할당 하기 전에 필터링 하기 위해 cmdlet으로 보냅니다 `$read_only` .

다음 예에서는 index 연산자가 cast 연산자 보다 우선적으로 적용 되는 것을 보여 줍니다.

이 식은 세 문자열의 배열을 만듭니다. 그런 다음 값이 0 인 index 연산자를 사용 하 여 첫 번째 문자열인 배열의 첫 번째 개체를 선택 합니다. 마지막으로, 선택한 개체를 문자열로 캐스팅 합니다. 이 경우 캐스트는 영향을 주지 않습니다.

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

이 식은 괄호를 사용 하 여 인덱스를 선택 하기 전에 캐스트 연산을 강제로 수행 합니다. 결과적으로 전체 배열은 (단일) 문자열로 캐스팅 됩니다. 그런 다음 index 연산자는 첫 번째 문자인 문자열 배열의 첫 번째 항목을 선택 합니다.

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

다음 예에서는 ( `-gt` 보다 큼) 연산자가 (LOGICAL AND) 연산자 보다 높은 우선 순위를 가지 므로 `-and` 식의 결과는 FALSE입니다.

```powershell
PS> 2 -gt 4 -and 1
False
```

다음 식과 같습니다.

```powershell
PS> (2 -gt 4) -and 1
False
```

-And 연산자의 우선 순위가 더 높은 경우 답은 TRUE가 됩니다.

```powershell
PS> 2 -gt (4 -and 1)
True
```

그러나이 예에서는 연산자 우선 순위를 관리 하는 중요 한 원칙을 보여 줍니다. 사용자가 해석 하기 어려운 식의 경우 기본 연산자 우선 순위를 강제로 적용 하는 경우에도 괄호를 사용 하 여 계산 순서를 적용 합니다. 괄호를 사용 하면 스크립트를 읽고 유지 관리 하는 사용자가 원하는 대로 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Operators][]

[about_assignment_operators][]

[about_Comparison_Operators][]

[about_arithmetic_operators][]

[about_join][]

[about_Redirection][]

[about_Scopes][]

[about_Split][]

[about_Type_Operators][]

<!-- reference links -->
[about_arithmetic_operators]: about_Arithmetic_Operators.md
[about_assignment_operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
