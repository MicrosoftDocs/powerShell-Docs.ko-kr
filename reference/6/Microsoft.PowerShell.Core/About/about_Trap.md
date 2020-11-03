---
description: 종료 오류를 처리 하는 키워드에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 88c16066b96912faf38fd48a3bd2f84572707e4c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221098"
---
# <a name="about-trap"></a>트랩 정보

## <a name="short-description"></a>간단한 설명

종료 오류를 처리 하는 키워드에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

종료 오류가 발생 하면 문이 실행 되지 않습니다. PowerShell에서 어떤 방식으로든 종료 오류를 처리 하지 않는 경우에도 PowerShell은 현재 파이프라인에서 함수 또는 스크립트의 실행을 중지 합니다. C #과 같은 다른 언어에서 종료 오류는 예외 라고 합니다.

`trap`키워드는 종료 오류가 발생할 때 실행할 문의 목록을 지정 합니다. `trap` 문은 다음과 같은 방법으로 종료 오류를 처리 합니다.

- 문 블록을 처리 한 후 오류를 표시 `trap` 하 고가 포함 된 스크립트나 함수를 계속 실행 합니다 `trap` . 기본 동작입니다.

- 문에서 using을 포함 하는 스크립트 또는 함수의 실행을 중단 하 고 오류를 표시 `trap` `break` `trap` 합니다.

- 오류가 발생 하지만 문에서를 사용 하 여를 포함 하는 스크립트 또는 함수를 계속 실행 합니다 `trap` `continue` `trap` .

의 문 목록에는 `trap` 여러 조건 또는 함수 호출이 포함 될 수 있습니다. 는 `trap` 로그 나 테스트 조건을 쓰거나 다른 프로그램을 실행할 수도 있습니다.

### <a name="syntax"></a>구문

`trap`문에는 다음 구문이 있습니다.

```powershell
trap [[<error type>]] {<statement list>}
```

`trap`문에는 종료 오류가 발생할 때 실행할 문의 목록이 포함 되어 있습니다. `trap`문은 `trap` 키워드, 선택적으로 형식 식으로 구성 되 고, 오류가 트랩 될 때 실행할 문 목록을 포함 하는 문 블록으로 구성 됩니다. 형식 식은에서 catch 하는 오류 유형을 구체화 합니다 `trap` .

스크립트나 명령에는 여러 개의 문이 있을 수 있습니다 `trap` . `trap` 문은 스크립트나 명령의 어디에 나 나타날 수 있습니다.

### <a name="trapping-all-terminating-errors"></a>모든 종료 오류 트래핑

스크립트나 명령에서 다른 방식으로 처리 되지 않는 종료 오류가 발생 하면 PowerShell은 `trap` 오류를 처리 하는 문을 확인 합니다. `trap`문이 있는 경우 PowerShell은 문에서 스크립트나 명령을 계속 실행 `trap` 합니다.

다음 예는 매우 간단한 문입니다 `trap` .

```powershell
trap {"Error found."}
```

이 `trap` 문은 종료 오류를 트래핑 합니다.

다음 예제에서 함수는 런타임 오류를 발생 시키는 의미 없는 문자열을 포함 합니다.

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

이 함수를 실행 하면 다음이 반환 됩니다.

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

다음 예에는 `trap` 자동 변수를 사용 하 여 오류를 표시 하는 문이 포함 되어 있습니다 `$_` .

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

이 버전의 함수를 실행 하면 다음이 반환 됩니다.

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> `trap` 문은 지정 된 범위 내의 모든 위치에서 정의 될 수 있지만 항상 해당 범위의 모든 문에 적용 됩니다. 런타임에 `trap` 블록의 문은 다른 문이 실행 되기 전에 정의 됩니다. JavaScript에서이를 [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)라고 합니다. 즉, `trap` 실행이 정의 된 지점을 지난 후에도 문은 해당 블록의 모든 문에 적용 됩니다. 예를 들어 `trap` 스크립트의 끝에을 정의 하 고 첫 번째 문에서 오류를 throw 하는 것은 여전히 트리거됩니다 `trap` .

### <a name="trapping-specific-errors"></a>특정 오류 트래핑

스크립트나 명령에는 여러 개의 문이 있을 수 있습니다 `trap` . `trap`특정 오류를 처리 하도록를 정의할 수 있습니다.

다음 예는 `trap` 특정 오류 **CommandNotFoundException** 을 트래핑 하는 문입니다.

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

함수 또는 스크립트에서 알려진 명령과 일치 하지 않는 문자열이 발견 되 면이 `trap` 문은 "명령 오류 트랩" 문자열을 표시 합니다.
문 목록을 실행 한 후 PowerShell은 오류 `trap` 개체를 오류 스트림에 쓴 다음 스크립트를 계속 합니다.

PowerShell은 .NET 예외 유형을 사용 합니다. 다음 예에서는 **System.object 예외** 오류 유형을 지정 합니다.

```powershell
trap [System.Exception] {"An error trapped"}
```

**CommandNotFoundException** 오류 형식은 **system.object** 형식에서 상속 됩니다. 이 문은 알 수 없는 명령에 의해 생성 된 오류를 트래핑 합니다. 또한 다른 오류 유형도 트래핑 합니다.

스크립트에 문이 둘 이상 있을 수 있습니다 `trap` . 각 오류 유형은 하나의 문으로만 트래핑할 수 있습니다 `trap` . 종료 오류가 발생 하면 PowerShell은 `trap` 현재 실행 범위에서 시작 하 여 가장 구체적인 일치 항목을 가진를 검색 합니다.

다음 스크립트 예제에는 오류가 포함 되어 있습니다. 스크립트에는 `trap` 종료 오류를 트래핑 하는 일반 문과 `trap` **CommandNotFoundException** 형식을 지정 하는 특정 문이 포함 되어 있습니다.

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

이 스크립트를 실행 하면 다음과 같은 결과가 생성 됩니다.

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

PowerShell에서 cmdlet 또는 다른 항목으로 "nonsenseString"을 인식 하지 못하기 때문에 **CommandNotFoundException** 오류가 반환 됩니다. 이 종료 오류는 특정 문으로 트래핑 됩니다 `trap` .

다음 스크립트 예제에는 `trap` 다른 오류가 있는 동일한 문이 포함 되어 있습니다.

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

이 스크립트를 실행 하면 다음과 같은 결과가 생성 됩니다.

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

0으로 나누려고 하면 **CommandNotFoundException** 오류가 생성 되지 않습니다. 대신,이 오류는 종료 오류를 트래핑 하는 다른 문에 의해 트래핑 됩니다 `trap` .

### <a name="trapping-errors-and-scope"></a>오류 및 범위 트래핑

문과 동일한 범위에서 종료 오류가 발생 하는 경우 `trap` PowerShell은에서 정의한 문 목록을 실행 합니다 `trap` . 오류가 발생 한 후 문에서 실행이 계속 됩니다. `trap`문이 오류와 다른 범위에 있으면 문과 동일한 범위에 있는 다음 문에서 실행이 계속 됩니다 `trap` .

예를 들어 함수에서 오류가 발생 하 고 `trap` 문이 함수에 있는 경우 스크립트는 다음 문에서 계속 됩니다. 다음 스크립트에는 오류와 문이 포함 되어 있습니다 `trap` .

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

이 스크립트를 실행 하면 다음과 같은 결과가 생성 됩니다.

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

`trap`함수의 문은 오류를 트래핑 합니다. 메시지를 표시 한 후 PowerShell은 함수 실행을 다시 시작 합니다. `Function1`가 완료 되었습니다.

같은 오류 및 문이 있는 다음 예제와 비교 `trap` 합니다. 이 예제에서 `trap` 문은 함수 외부에서 발생 합니다.

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

함수를 실행 하면 `Function2` 다음과 같은 결과가 생성 됩니다.

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

이 예에서는 "function2가 완료 되었습니다." 명령이 실행 되지 않았습니다. 두 예제에서 종료 오류는 함수 내에서 발생 합니다. 그러나이 예제에서 `trap` 문은 함수 외부에 있습니다. 문이 실행 된 후에는 PowerShell이 함수로 다시 이동 하지 않습니다 `trap` .

> [!CAUTION]
> 동일한 오류 조건에 대해 여러 개의 트랩이 정의 되 면 첫 번째로 `trap` 정의 된 어휘를 사용 합니다 (범위에서 가장 높음).

다음 예제에서는 `trap` "같습니다. 1"이 있는만 실행 됩니다.

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> Trap 문은 컴파일되는 위치로 범위가 지정 됩니다. 함수 또는 점 원본 스크립트 내에 문이 있는 경우 `trap` 함수 또는 점 원본 스크립트가 종료 되 면 `trap` 내부의 모든 문이 제거 됩니다.

### <a name="using-the-break-and-continue-keywords"></a>Break 및 continue 키워드 사용

문에 및 키워드를 사용 하 여 `break` `continue` `trap` 종료 오류 후 스크립트나 명령을 계속 실행할지 여부를 결정할 수 있습니다.

문 목록에 문을 포함 하는 경우 `break` `trap` PowerShell은 함수 또는 스크립트를 중지 합니다. 다음 샘플 함수는 `break` 문에서 키워드를 사용 합니다 `trap` .

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

문은 키워드를 포함 하기 때문에 `trap` `break` 함수는 계속 실행 되지 않으며 "함수 완료 됨" 줄은 실행 되지 않습니다.

문에 키워드를 포함 하는 경우에는 `continue` `trap` 또는 없이 오류가 발생 한 문 뒤에 PowerShell이 다시 시작 됩니다 `break` `continue` . 그러나 키워드를 사용 하면 `continue` PowerShell에서 오류 스트림에 오류를 쓰지 않습니다.

다음 샘플 함수는 `continue` 문에서 키워드를 사용 합니다 `trap` .

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

이 함수는 오류가 트래핑 된 후 다시 시작 되 고 "Function completed" 문이 실행 됩니다. 오류 스트림에 오류가 기록 되지 않습니다.

## <a name="notes"></a>메모

`trap` 문은 범위 내의 모든 종료 오류를 처리 하는 간단한 방법을 제공 합니다. 보다 세부적인 오류 처리에 대해서는 `try` / `catch` 문을 사용 하 여 트랩이 정의 된 블록을 사용 `catch` 합니다. `catch`문은 연결 된 문 내부의 코드에만 적용 `try` 됩니다. 자세한 내용은 [about_Try_Catch_Finally](about_Try_Catch_Finally.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
