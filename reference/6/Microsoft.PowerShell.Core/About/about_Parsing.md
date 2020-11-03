---
description: PowerShell에서 명령을 구문 분석 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: 200a3aa7aac6477a2b2d3660167621132514c333
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221393"
---
# <a name="about-parsing"></a>구문 분석 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 명령을 구문 분석 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

명령 프롬프트에서 명령을 입력 하면 PowerShell에서 명령 텍스트를 _토큰_ 이라는 일련의 세그먼트로 분리 한 다음 각 토큰을 해석 하는 방법을 결정 합니다.

예를 들어 다음을 입력 합니다.

```powershell
Write-Host book
```

PowerShell은 명령을 두 개의 토큰으로 분리 `Write-Host` 하 `book` 고 두 가지 주요 구문 분석 모드 (식 모드 및 인수 모드) 중 하나를 사용 하 여 각 토큰을 독립적으로 해석 합니다.

> [!NOTE]
> PowerShell에서 명령 입력을 구문 분석 하면 cmdlet 또는 네이티브 실행 파일에 명령 이름을 확인 하려고 시도 합니다. 명령 이름에 정확히 일치 하는 항목이 없으면 PowerShell이 명령 앞 `Get-` 에 기본 동사로 필요 합니다. 예를 들어 PowerShell `Process` 은로 구문 분석 `Get-Process` 합니다. 다음과 같은 이유로이 기능을 사용 하지 않는 것이 좋습니다.
>
> - 비효율적입니다. 이렇게 하면 PowerShell에서 여러 번 검색 합니다.
> - 같은 이름의 외부 프로그램을 먼저 확인 하므로 의도 한 cmdlet을 실행할 수 없습니다.
> - `Get-Help` 및는 `Get-Command` 동사 없는 이름을 인식 하지 않습니다.

### <a name="expression-mode"></a>식 모드

식 모드는 스크립팅 언어의 값 조작에 필요한 식을 결합 하기 위한 것입니다. 식은 PowerShell 구문에서 값에 대 한 표현으로, 단순 또는 복합 일 수 있습니다. 예를 들면 다음과 같습니다.

리터럴 식은 해당 값을 직접 표현한 것입니다. 

```powershell
'hello', 32
```

변수 식은 참조 하는 변수의 값을 포함 합니다. 

```powershell
$x, $script:path
```
연산자는 평가를 위해 다른 식을 결합 합니다. 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- _문자열 리터럴은_ 따옴표 안에 포함 되어야 합니다.
- _숫자_ 는 일련의 문자가 아닌 숫자 값으로 처리 됩니다 (이스케이프 되지 않은 경우).
- _Operators_ And와 같은 단항 연산자 및 `-` `-not` 및와 같은 이항 연산자를 포함 하 `+` 는 연산자 `-gt` 는 연산자로 해석 되 고 해당 인수 (피연산자)에 대해 해당 작업을 적용 합니다.
- _특성 및 변환 식은_ 식으로 구문 분석 되 고 하위 식 (예:)에 적용 `[int] '7'` 됩니다.
- _변수 참조_ 는 값으로 계산 되지만 _스 플랫_ (즉, 미리 채워진 매개 변수 집합 붙여넣기)는 사용할 수 없으며 파서 오류가 발생 합니다.
- 다른 모든 항목은 호출할 명령으로 처리 됩니다.

### <a name="argument-mode"></a>인수 모드

구문 분석할 때 PowerShell은 먼저 입력을 식으로 해석 합니다. 그러나 명령 호출이 발생 하면 구문 분석은 인수 모드에서 계속 됩니다.

인수 모드는 셸 환경의 명령에 대 한 인수 및 매개 변수를 구문 분석 하기 위해 디자인 되었습니다. 모든 입력은 다음 구문 중 하나를 사용 하지 않는 한 확장 가능한 문자열로 처리 됩니다.

- 달러 기호 ( `$` )는 변수 참조를 시작 합니다 (뒤에 유효한 변수 이름이 오는 경우에만). 그렇지 않은 경우 확장 가능한 문자열의 일부로 해석 됩니다.
- 따옴표 ( `'` 및 `"` )는 문자열 값을 시작 합니다.
- 괄호 ( `(` 및 `)` )는 새 식을 구분 합니다.
- 하위 식 연산자 ( `$(` ... `)` ) 정하는 포함 식.
- 중괄호 ( `{` 및 `}` )는 새 스크립트 블록을 구분 합니다.
- 초기 at 기호 ( `@` )는 스 플랫 ( `@args` ), 배열 ( `@(1,2,3)` ) 및 해시 테이블 ()과 같은 식 구문을 시작 `@{a=1;b=2}` 합니다.
- 쉼표 ()는로 전달 되는 `,` 명령이 네이티브 응용 프로그램 일 경우를 제외 하 고 배열로 전달 되는 목록을 소개 합니다 .이 경우 확장 가능한 문자열의 일부로 해석 됩니다. 초기, 연속 또는 후행 쉼표는 지원 되지 않습니다.

포함 식의 값은 문자열로 변환 됩니다.

다음 표에서는 식 모드 및 인수 모드에서 처리 된 값의 몇 가지 예제와 이러한 값의 평가를 제공 합니다. 변수의 값이 인 것으로 가정 `a` `4` 합니다.

|       예제        |    모드    |      결과       |
| -------------------- | ---------- | ----------------- |
| `2`                  | 식 | 2 (정수)       |
| `` `2``              | 식 | "2" (명령)     |
| `echo 2`             | 식 | 2 (정수)       |
| `2+2`                | 식 | 4 (정수)       |
| `echo 2+2`           | 인수   | "2 + 2" (문자열)    |
| `echo(2+2)`          | 식 | 4 (정수)       |
| `$a`                 | 식 | 4 (정수)       |
| `echo $a`            | 식 | 4 (정수)       |
| `$a+2`               | 식 | 6 (정수)       |
| `echo $a+2`          | 인수   | 4 + 2 (문자열)      |
| `$-`                 | 인수   | "$-" (명령)    |
| `echo $-`            | 인수   | "$-" (문자열)     |
| `a$a`                | 식 | "a $ a" (명령)   |
| `echo a$a`           | 인수   | "a4" (문자열)     |
| `a'$a'`              | 식 | "a $ a" (명령)   |
| `echo a'$a'`         | 인수   | "a $ a" (문자열)    |
| `a"$a"`              | 식 | "a $ a" (명령)   |
| `echo a"$a"`         | 인수   | "a4" (문자열)     |
| `a$(2)`              | 식 | "a $ (2)" (명령) |
| `echo a$(2)`         | 인수   | "a2" (문자열)     |

모든 토큰은 부울 또는 문자열과 같은 일종의 개체 형식으로 해석할 수 있습니다. PowerShell에서 식의 개체 유형을 확인 하려고 합니다.
개체 형식은 명령에 필요한 매개 변수의 형식과 PowerShell이 인수를 올바른 형식으로 변환 하는 방법을 인식 하는지 여부에 따라 달라 집니다. 다음 표에서는 식에서 반환 하는 값에 할당 된 형식의 몇 가지 예를 보여 줍니다.

|       예제          |    모드    |     결과      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | 인수   | "! 1" (문자열)   |
| `Write-Output (!1)`    | expression | False (부울) |
| `Write-Output (2)`     | expression | 2 (정수)     |
| `Set-Variable AB A,B`  | 인수   | ' A ', ' B ' (배열) |
| `CMD /CECHO A,B`       | 인수   | ' A, B ' (문자열)  |
| `CMD /CECHO $AB`       | expression | ' A ', ' B ' (배열) |
| `CMD /CECHO :$AB`      | 인수   | ': A B ' (문자열) |

PowerShell 3.0에 도입 된 중지 구문 분석 기호 ()는 powershell `--%` 명령 또는 식으로 입력을 해석 하지 않도록 powershell에 지시 합니다.

PowerShell에서 실행 프로그램을 호출 하는 경우 프로그램 인수 앞에 구문 분석 기호를 추가 합니다. 이 기법은 잘못 해석을 방지 하기 위해 이스케이프 문자를 사용 하는 것 보다 훨씬 쉽습니다.

중지 구문 분석 기호가 나타나면 PowerShell은 줄의 나머지 문자를 리터럴로 처리 합니다. 표준 Windows 표기법을 사용 하는 환경 변수 (예:)에 대 한 값을 대체 하는 해석을 수행 합니다 `%USERPROFILE%` .

중지 구문 분석 기호는 다음 줄 바꿈 문자 또는 파이프라인 문자 까지만 적용 됩니다. 연속 문자 ()를 사용 `` ` `` 하 여 효과를 확장 하거나 명령 구분 기호 ()를 사용 하 여 효과를 종료할 수 없습니다 `;` .

예를 들어 다음 명령은 **Icacls** 프로그램을 호출 합니다.

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell 2.0에서이 명령을 실행 하려면 이스케이프 문자를 사용 하 여 misinterpreting에서 괄호를 사용 하지 않도록 해야 합니다.

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

PowerShell 3.0 부터는 중지 구문 분석 기호를 사용할 수 있습니다.

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell은 다음 명령 문자열을 **Icacls** 프로그램으로 보냅니다.

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> 중지 구문 분석 기호는 Windows 플랫폼 에서만 사용 됩니다.

## <a name="see-also"></a>참고 항목

[about_Command_Syntax](about_Command_Syntax.md)
