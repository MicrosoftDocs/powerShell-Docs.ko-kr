---
title: if 문 관련 세부 사항
description: 다른 많은 언어와 마찬가지로 PowerShell에는 스크립트에서 조건부로 코드를 실행하기 위한 문이 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b6bafb99bfb8ecd0152bae841e5c58d4c27ccd3e
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469755"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a>`if` 문 관련 세부 사항

다른 많은 언어와 마찬가지로 PowerShell에는 스크립트에서 조건부로 코드를 실행하기 위한 문이 있습니다. 해당 문 중 하나가 [If][] 문입니다. 오늘은 PowerShell에서 가장 기본적인 명령 중 하나를 자세히 살펴보겠습니다.

> [!NOTE]
> 현재 문서의 [원본 버전][]은 [@KevinMarquette][]가 작성한 블로그에 있습니다. PowerShell 팀은 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 해당 블로그를 확인하세요.

## <a name="conditional-execution"></a>조건부 실행

스크립트에서는 결정을 내리고 이러한 결정에 따라 다른 논리를 실행해야 하는 경우가 많습니다.
이것은 조건부 실행을 의미합니다. 평가할 문이나 값이 하나 있으면 해당 평가에 따라 코드의 다른 섹션을 실행합니다. 이것은 정확히 `if` 문이 수행하는 작업입니다.

## <a name="the-if-statement"></a>`if` 문

`if` 문의 기본 예는 다음과 같습니다.

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

`if` 문은 가장 먼저 괄호 안의 식을 계산합니다. `$true`인 것으로 계산되면 중괄호에서 `scriptblock`을 실행합니다. 값이 `$false`였다면 해당 scriptblock은 건너뜁니다.

이전 예제에서는 `if` 문이 `$condition` 변수만 계산했습니다. `$true`였으며 scriptblock 내부에서 `Write-Output` 명령을 실행했을 것입니다.

일부 언어에서는 `if` 문 뒤에 한 줄의 코드를 배치하여 실행할 수 있지만 PowerShell에는 해당되지 않습니다. 제대로 작동하게 하려면 중괄호를 포함한 전체 `scriptblock`를 제공해야 합니다.

## <a name="comparison-operators"></a>비교 연산자

`if` 문의 가장 일반적인 용도는 두 항목을 서로 비교하는 것입니다. PowerShell에는 다양한 비교 시나리오에 대한 특수 연산자가 있습니다. 비교 연산자를 사용하면 왼쪽에 있는 값이 오른쪽에 있는 값과 비교됩니다.

### <a name="-eq-for-equality"></a>같음에 대한 -eq

`-eq`는 두 값이 서로 같은지 확인하기 위해 같음 검사를 실행합니다.

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

이 예제에서는 알려진 값인 `5`를 가져오고 이를 내 `$value`와 비교하여 일치하는지 확인합니다.

한 가지 사용 사례는 작업을 수행하기 전에 값의 상태를 확인하는 것입니다. `Restart-Service`를 호출하기 전에 서비스를 가져와 상태를 실행하고 있는지 확인할 수 있습니다.

C#과 같은 다른 언어에서 같음을 위해 `==`을 사용하는 경우(예: `5 == $value`)가 많지만 PowerShell에서는 작동하지 않습니다. 사용자가 하는 또 다른 흔한 실수는 변수에 값을 할당하는 데만 사용해야 하는 등호(예: `5 = $value`)를 사용하는 것입니다. 왼쪽에 알려진 값을 배치하면 상황이 더 복잡해질 수 있습니다.

해당 연산자(및 기타 연산자)에는 몇 가지 변형이 있습니다.

- `-eq` 대/소문자를 구분하지 않는 같음
- `-ieq` 대/소문자를 구분하지 않는 같음
- `-ceq` 대/소문자를 구분하는 같음

### <a name="-ne-not-equal"></a>-ne 같지 않음

여러 연산자에 반대인 결과를 확인하는 관련 연산자가 있습니다. `-ne`는 값이 서로 같지 않음을 확인합니다.

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

이것을 사용하여 값이 `5`가 아닌 경우에만 작업이 실행되도록 하세요. 시작하기 전에 서비스가 실행 중인 상태에 있는지 확인하는 것이 좋습니다.

**변형:**

- `-ne` 대/소문자를 구분하지 않는 같지 않음
- `-ine` 대/소문자를 구분하지 않는 같지 않음
- `-cne` 대/소문자를 구분하는 같지 않음

이것은 `-eq`의 역 변형입니다. 다른 연산자의 변형을 나열하는 경우 이러한 형식을 함께 그룹화합니다.

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a>초과 또는 미만을 위한 -gt -ge -lt -le

이러한 연산자는 값이 다른 값보다 크거나 작은지 확인하는 경우 사용됩니다.
`-gt -ge -lt -le`는 GreaterThan, GreaterThanOrEqual, LessThan 및 LessThanOrEqual을 의미합니다.

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

**변형:**

- `-gt` 보다 큼
- `-igt` 보다 큼, 대/소문자를 구분하지 않음
- `-cgt` 보다 큼, 대/소문자 구분
- `-ge` 크거나 같음
- `-ige` 크거나 같음, 대/소문자를 구분하지 않음
- `-cge` 크거나 같음, 대/소문자 구분
- `-lt` 보다 작음
- `-ilt` 보다 작음, 대/소문자를 구분하지 않음
- `-clt` 보다 작음, 대/소문자 구분
- `-le` 작거나 같음
- `-ile` 작거나 같음, 대/소문자를 구분하지 않음
- `-cle` 작거나 같음, 대/소문자 구분

이러한 연산자에 대/소문자를 구분하거나 구분하지 않는 옵션을 사용하는 이유는 모릅니다.

### <a name="-like-wildcard-matches"></a>-like 와일드카드 일치

PowerShell에는 고유한 와일드카드 기반 패턴 일치 구문이 있으므로 `-like` 연산자와 함께 사용할 수 있습니다. 이러한 와일드카드 패턴은 상당히 기본적입니다.

- `?` 임의의 문자 하나에 대응
- `*` 임의의 수의 문자에 대응

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

패턴이 전체 문자열과 일치하는지 확인하는 것이 중요합니다. 문자열의 중간에 있는 항목을 일치시켜야 하는 경우 문자열의 양쪽 끝에 `*`를 배치해야 합니다.

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

**변형:**

- `-like` 대/소문자를 구분하지 않는 와일드카드
- `-ilike` 대/소문자를 구분하지 않는 와일드카드
- `-clike` 대/소문자 구분 와일드카드
- `-notlike` 대/소문자를 구분하지 않는 와일드카드가 일치하지 않음
- `-inotlike` 대/소문자를 구분하지 않는 와일드카드가 일치하지 않음
- `-cnotlike` 대/소문자 구분 와일드카드가 일치하지 않음

### <a name="-match-regular-expression"></a>-match 정규식

`-match` 연산자를 사용하면 정규식 기반 일치 항목에 대한 문자열을 확인할 수 있습니다. 와일드카드 패턴이 유연하지 않을 경우 연산자를 사용하세요.

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

regex 패턴은 기본적으로 문자열의 어디에서든 일치합니다. 따라서 다음과 같이 일치하게 하려는 substring을 지정할 수 있습니다.

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

regex는 그 자체로 복잡한 언어이며 살펴볼 가치가 있습니다. `-match`에 대해 자세히 설명하고 다른 문서에서 [regex를 사용하는 여러 방법][]을 다루겠습니다.

**변형:**

- `-match` 대/소문자를 구분하지 않는 regex
- `-imatch` 대/소문자를 구분하지 않는 regex
- `-cmatch` 대/소문자 구분 regex
- `-notmatch` 대/소문자를 구분하지 않는 regex가 일치하지 않음
- `-inotmatch` 대/소문자를 구분하지 않는 regex가 일치하지 않음
- `-cnotmatch` 대/소문자 구분 regex가 일치하지 않음

### <a name="-is-of-type"></a>형식의 -is

`-is` 연산자를 사용하여 값의 형식을 확인할 수 있습니다.

```powershell
if ( $value -is [string] )
{
    # do something
}
```

클래스로 작업하거나 파이프라인을 통해 다양한 개체를 허용하는 경우 연산자를 사용할 수 있습니다. 서비스 또는 서비스 이름을 입력으로 사용할 수 있습니다. 그런 다음 서비스가 있는지 확인하고 이름만 있는 경우 해당 서비스를 페치합니다.

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

**변형:**

- `-is` 형식의
- `-isnot` 형식이 아닌

## <a name="collection-operators"></a>컬렉션 연산자

단일 값으로 이전 연산자를 사용하는 경우 결과는 `$true` 또는 `$false`가 됩니다. 이것은 컬렉션을 사용하는 약간 다르게 처리됩니다. 컬렉션의 각 항목이 평가되고 연산자는 `$true`로 계산되는 모든 값을 반환합니다.

```powershell
PS> 1,2,3,4 -eq 3
3
```

이것은 `if` 문에서 계속 제대로 작동합니다. 따라서 연산자가 값을 반환하면 전체 문이 `$true`입니다.

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

여기에서 세부 정보에 숨겨진 작은 문제를 언급하려고 합니다. 이러한 방식으로 `-ne` 연산자를 사용하면 실수로 논리를 거꾸로 보게 될 위험이 있습니다. 컬렉션의 항목이 사용자의 값과 일치하지 않는 경우 컬렉션과 함께 `-ne`를 사용하면 `$true`를 반환합니다.

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

영리한 기법처럼 보일 수 있지만 이 문제를 보다 효율적으로 처리하는 연산자인 `-contains` 및 `-in`이 있습니다. 그리고 원하는 것을 `-notcontains`가 제공할 것입니다.

### <a name="-contains"></a>-contains

`-contains` 연산자는 컬렉션에서 값을 확인합니다. 일치 항목을 찾으면 `$true`는 반환됩니다.

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

컬렉션에 값이 포함되어 있는지 여부를 확인하는 기본 방법입니다. `Where-Object`(또는 `-eq`)를 사용하면 매번 전체 목록을 표시하고 속도가 훨씬 느려집니다.

**변형:**

- `-contains` 대/소문자를 구분하지 않는 일치
- `-icontains` 대/소문자를 구분하지 않는 일치
- `-ccontains` 대/소문자를 구분하고 일치
- `-notcontains` 대/소문자를 구분하지 않고 일치하지 않음
- `-inotcontains` 대/소문자를 구분하지 않고 일치하지 않음
- `-cnotcontains` 대/소문자를 구분하고 일치하지 않음

### <a name="-in"></a>-in

`-in` 연산자는 컬렉션이 오른쪽에 있는 점만 제외하면 `-contains` 연산자와 동일합니다.

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

**변형:**

- `-in` 대/소문자를 구분하지 않는 일치
- `-iin` 대/소문자를 구분하지 않는 일치
- `-cin` 대/소문자를 구분하고 일치
- `-notin` 대/소문자를 구분하지 않고 일치하지 않음
- `-inotin` 대/소문자를 구분하지 않고 일치하지 않음
- `-cnotin` 대/소문자를 구분하고 일치하지 않음

## <a name="logical-operators"></a>논리 연산자

논리 연산자는 다른 식을 반전하거나 결합하는 데 사용됩니다.

### <a name="-not"></a>-not

`-not` 연산자는 식을 `$false`에서 `$true` 또는 `$true`에서 `$false`로 대칭 이동합니다. 다음은 `Test-Path` `$false`일 때 작업을 수행하려는 예제입니다.

```powershell
if ( -not ( Test-Path -Path $path ) )
```

설명한 대부분의 연산자에는 `-not` 연산자를 사용하지 않아도 되는 변형이 있지만 여전히 유용한 경우도 있습니다.

### <a name="-operator"></a>! operator

`!`를 `-not`의 별칭으로 사용할 수 있습니다.

```powershell
if ( -not $value ){}
if ( !$value ){}
```

C#과 같은 다른 언어를 사용하는 사람들이 `!`를 더 많이 사용하는 것을 볼 수 있습니다. 스크립트를 빨리 살펴볼 때 확인하기가 어려워서 입력하는 편을 선호합니다.

### <a name="-and"></a>-and

식을 `-and` 연산자와 결합할 수 있습니다. 이 작업을 수행하는 경우 전체 식이 `$true`가 되려면 양쪽 모두 `$true`여야 합니다.

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

이 예제에서는 `$age`가 왼쪽에서는 13세 이상 오른쪽에서는 55세 미만이어야 합니다. 이 예제에서는 더 명확하게 하기 위해 괄호를 추가했지만 식이 단순하다면 괄호는 선택 사항입니다. 다음은 괄호를 제외하고는 동일한 예제입니다.

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

평가는 왼쪽에서 오른쪽으로 수행됩니다. 첫 번째 항목이 `$false`로 평가되면 일찍 종료되고 비교가 올바르게 수행되지 않습니다. 이러한 방법은 사용하기 전에 값이 존재하는지 확인해야 하는 경우에 유용합니다. 예를 들어 `$null` 경로를 지정하는 경우 `Test-Path`가 오류를 throw합니다.

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a>-or

`-or`을 사용하여 두 식을 지정하고 둘 중 하나가 `$true`인 경우 `$true`를 반환할 수 있습니다.

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

`-and` 연산자와 마찬가지로 평가는 왼쪽에서 오른쪽으로 수행됩니다. 첫 번째 부분이 `$true`인 경우 전체 문이 `$true`가 되며 식의 나머지 부분을 처리하지 않습니다.

또한 이러한 연산자에서 구문이 작동하는 방식에 주목하세요. 두 개의 별도 식이 필요합니다. 실수를 인식하지 못한 채 이러한 `$value -eq 5 -or 6`과 같은 작업을 수행하려는 사용자를 본 적이 있습니다.

### <a name="-xor-exclusive-or"></a>-xor 배타적 OR

이것은 약간 특이한 방법입니다. `-xor`은 식 하나만 `$true`인지 계산하도록 허용합니다. 따라서 두 항목 모두 `$false`거나 두 항목 모두 `$true`인 경우 전체 식이 `$false`가 됩니다. 이것을 살펴보는 또 다른 방법은 식의 결과가 다른 경우에만 식이 `$true`라는 것입니다.

사용자가 해당 논리 연산자를 사용하는 경우는 거의 없으며 이것을 사용하는 이유에 대해 설명하기가 어렵습니다.

## <a name="bitwise-operators"></a>비트 연산자

비트 연산자는 값 내부의 비트에 대해 계산하고 그 결과로 새 값을 생성합니다. [비트 연산자][]에 대한 교육은 본 문서의 범위를 벗어나며 여기에서는 그 목록만을 소개합니다.

- `-band` 이진 AND
- `-bor` 이진 OR
- `-bxor` 이진 배타적 OR
- `-bnot` 이진 NOT
- `-shl` 왼쪽으로 이동
- `-shr` 오른쪽으로 이동

## <a name="powershell-expressions"></a>PowerShell 식

조건문 내부에서 일반 PowerShell을 사용할 수 있습니다.

```powershell
if ( Test-Path -Path $Path )
```

이것이 실행될 때 `Test-Path`는 `$true` 또는 `$false`를 반환합니다. 이것은 다른 값을 반환하는 명령에도 적용됩니다.

```powershell
if ( Get-Process Notepad* )
```

반환된 프로세스가 있는 경우 `$true`로 계산하고 아무것도 없는 경우 `$false`로 계산합니다. 파이프라인 식 또는 다음과 같은 기타 PowerShell 문을 사용할 수 있습니다.

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

이러한 식은 `-and` 및 `-or` 연산자를 사용하여 서로 결합할 수 있지만 하위 식으로 구분하려면 괄호를 사용해야 할 수도 있습니다.

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a>$null 확인

`if` 문에서는 결과가 없거나 `$null` 값이 `$false`로 계산됩니다. 특히 `$null`을 확인하는 경우 `$null`을 왼쪽에 배치하는 것이 권장됩니다.

```powershell
if ( $null -eq $value )
```

PowerShell에서 `$null` 값을 처리하는 경우 신경 써야 할 사항이 매우 많습니다. 좀 더 자세히 알아보려면 [$null 관련 세부 사항][] 문서를 참조하세요.

### <a name="variable-assignment"></a>변수 할당

[Prasoon Karunan V][]가 알려주기 전까지 변수 할당 항목을 추가하는 것을 잊어버릴 뻔했습니다.

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

일반적으로 변수에 값을 할당하는 경우 값이 파이프라인 또는 콘솔로 전달되지 않습니다. 하위 식에서 변수를 할당하는 경우에는 파이프라인으로 전달됩니다.

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

`$first` 할당에 출력이 없고 `$second` 할당에는 있는 경우에는 어떻게 되는지 확인해 보세요. `if` 문에서 할당을 완료한 경우 위의 `$second` 할당과 마찬가지로 실행됩니다. 다음은 변수 할당을 사용하는 방법에 대한 명확한 예제입니다.

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

`$process`에 값이 할당되면 문이 `$true`가 되고 `$process`가 중단됩니다.

이것은 같음 검사가 아니므로 `-eq`와 혼동하지 않도록 주의하세요. 이것은 더 모호한 기능이며 대부분의 사람들은 작업을 이러한 방식으로 인식하지 않습니다.

## <a name="alternate-execution-path"></a>대체 실행 경로

`if` 문을 사용하면 문이 `$true`가 되는 경우뿐만 아니라 `$false`가 되는 경우에도 동작을 지정할 수 있습니다. 여기에서 `else` 문이 필요합니다.

### <a name="else"></a>else

`else` 문은 항상 `if` 문의 마지막 부분에서 사용됩니다.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

이 예제에서는 이것이 파일인지 확인하기 위해 `$path`를 검사합니다. 파일을 찾았으면 해당 파일을 이동합니다. 그러지 않은 경우 경고를 작성합니다. 이러한 분기 논리 형식은 매우 일반적입니다.

### <a name="nested-if"></a>중첩된 If

`if` 및 `else` 문은 스크립트 블록을 사용하므로 기타 `if` 문을 포함한 모든 PowerShell 명령을 내부에 배치할 수 있습니다. 이렇게 하면 훨씬 더 복잡한 논리를 사용할 수 있습니다.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

이 예제에서는 행복 경로를 먼저 테스트한 다음 작업을 수행합니다. 해당 작업이 실패한 경우 다른 검사를 수행하고 사용자에게 보다 자세한 정보를 제공합니다.

### <a name="elseif"></a>Elseif

단일 조건부 검사만 있는 것이 아닙니다. `elseif` 문을 사용하여 `if` 및 `else` 문을 중첩하는 대신 함께 연결할 수 있습니다.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

실행은 위쪽에서 아래쪽으로 수행됩니다. 위에 있는 `if` 문이 먼저 평가됩니다. 이것이 `$false`인 경우 목록에서 다음 `elseif` 또는 `else`로 이동합니다. 마지막 `else`는 다른 것들이 `$true`를 반환하지 않는 경우 수행하는 기본 작업입니다.

### <a name="switch"></a>스위치

이제 `switch` 문에 대해 설명하겠습니다. 이것은 값을 사용하여 여러 가지 비교를 수행하는 대체 구문을 제공합니다. `switch`를 사용하면 식을 지정하고 결과를 여러 다른 값과 비교할 수 있습니다. 이러한 값 중 하나가 일치하면 일치 코드 블록이 실행됩니다. 다음 예제를 살펴보세요.

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

`$itemType`과 일치할 수 있는 값은 세 가지가 있습니다. 여기에서는 `Role`과 일치합니다. 간단한 예제를 사용하여 `switch` 연산자를 설명했습니다. [Switch 문 관련 설명][]에 대한 자세한 내용은 다른 문서에서 설명합니다.

## <a name="pipeline"></a>파이프라인

파이프라인은 PowerShell의 고유하고 중요한 기능입니다. 제거되지 않은 값 또는 변수에 할당되지 않은 값은 파이프라인에 배치됩니다. `if`를 사용하면 파이프라인을 이용할 수 있습니다. 이 이용 방식이 항상 명확하지는 않습니다.

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

각 스크립트 블록은 명령의 결과 또는 값을 파이프라인에 배치합니다. 그런 다음, `if` 문의 결과를 `$discount` 변수에 할당합니다. 이 예제에서는 각 scriptblock에서 직접 `$discount` 변수에 해당 값을 간편하게 할당할 수 있습니다. 이것을 `if` 문에 자주 사용한다고 말할 수 없지만 최근에 사용한 적이 있습니다.

### <a name="array-inline"></a>배열 인라인

여러 명령줄 인수를 사용하여 실행 파일을 시작하는 [Invoke-SnowSql][]이라는 함수가 있습니다. 다음은 인수 배열을 빌드하는 해당 함수의 클립입니다.

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

`$Debug` 및 `$Path` 변수는 최종 사용자가 제공하는 함수에 대한 매개 변수입니다.
배열의 초기화 내부에서 해당 변수를 인라인으로 계산합니다. `$Debug`가 true면 `$snowSqlParam`에 해당하는 값이 올바른 위치가 됩니다. `$Path` 변수에 대해서도 마찬가지입니다.

## <a name="simplify-complex-operations"></a>복잡한 작업의 간소화

확인할 비교 사항이 너무 많고 `If` 문이 화면 오른쪽에서 멀리 스크롤되는 상황이 발생하는 것은 피하기 어렵습니다.

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

이러한 작업은 읽기 어려울 수 있으며 실수하기 쉽습니다. 이러한 경우 몇 가지 작업을 수행할 수 있습니다.

### <a name="line-continuation"></a>줄 연속

PowerShell에는 명령을 다음 줄로 래핑할 수 있는 몇 가지 연산자가 있습니다. 논리 연산자 `-and` 및 `-or`는 식을 여러 줄로 구분하려는 경우에 유용한 연산자입니다.

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

여전히 많은 일이 벌어지고 있지만 각 부분을 별도의 줄에 배치하면 큰 차이가 발생합니다.
세 개 이상의 비교를 하거나 논리를 읽기 위해 오른쪽으로 스크롤해야 하는 경우 일반적으로 이 연산자를 사용합니다.

### <a name="pre-calculating-results"></a>결과 미리 계산

`if` 문에서 해당 문을 분리하고 결과만 확인할 수 있습니다.

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

이전 예제보다 훨씬 더 깔끔해 보일 것입니다. 또한 실제로 검사하려는 대상을 설명하는 변수 이름을 사용할 수도 있습니다. 이는 또한 불필요한 주석을 줄이는 자체 문서화 코드의 예제이기도 합니다.

### <a name="multiple-if-statements"></a>여러 If 문

여러 If 문을 여러 문으로 구분하고 한 번에 하나씩 검사할 수 있습니다. 이때 플래그 또는 추적 변수를 사용하여 결과를 결합합니다.

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

플래그 논리가 제대로 작동하도록 논리를 반전해야 했습니다. 각 평가는 개별 `if` 문입니다. 디버깅하는 경우 이를 통해 논리에서 수행하는 작업을 정확하게 알 수 있습니다. 또한 훨씬 더 자세한 정보를 추가할 수 있었습니다.

분명한 단점은 더 많은 코드를 작성해야 한다는 점입니다. 코드는 한 줄의 논리를 사용하여 25개 이상의 줄로 확대해야 하므로 훨씬 복잡합니다.

### <a name="using-functions"></a>함수 사용

모든 유효성 검사 논리를 함수로 이동할 수도 있습니다. 얼마나 깔끔한지 살펴보세요.

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

유효성 검사를 실행하는 함수를 만들어야 하지만 이를 통해 코드를 훨씬 더 쉽게 사용할 수 있습니다. 해당 코드를 더 쉽게 테스트할 수 있습니다. 테스트에서 `Test-ADDriveConfiguration`에 대한 호출을 모방할 수 있으며 해당 함수에 대해서는 두 가지 테스트만 하면 됩니다. 하나는 `$true`를 반환하는 것이고 다른 하나는 `$false`를 반환하는 것입니다. 크기가 작아서 다른 함수를 테스트하는 것은 더 간단합니다.

해당 함수의 본문은 아직 시작할 때의 한 줄이거나 지난 섹션에서 사용한 확대된 논리일 수 있습니다. 이 작업은 두 시나리오에서 모두 잘 작동하며 나중에 구현을 쉽게 변경할 수 있습니다.

## <a name="error-handling"></a>오류 처리

`if` 문의 한 가지 중요한 사용은 오류가 발생하기 전에 오류 조건을 검사하는 것입니다. 폴더를 만들기 전에 폴더가 이미 존재하는지 확인하는 것은 한 가지 좋은 예입니다.

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

예외가 발생할 것이라고 예상되면 그것은 사실 예외가 아니라고 말할 수 있습니다. 그러므로 값을 확인하고 가능한 경우 조건의 유효성을 검사하세요.

실제 예외 처리에 대해 좀 더 자세히 알아보려면 [Everything you ever wanted to know about exceptions(예외 관련 세부 사항)][]에 대한 문서를 참조하세요.

## <a name="final-words"></a>맺음말

`if` 문은 간단한 문이며 PowerShell의 중요한 부분입니다. 작성하는 거의 모든 스크립트에서 이 문을 여러 번 사용하게 될 것입니다. 이전보다 더 잘 이해하게 되셨길 바랍니다.

<!-- link references -->
[원본 버전]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[비트 연산자]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[regex를 사용하는 여러 방법]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[Everything you ever wanted to know about exceptions(예외 관련 세부 사항)]: everything-about-exceptions.md
[$null 관련 세부 사항]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Switch 문 관련 설명]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
