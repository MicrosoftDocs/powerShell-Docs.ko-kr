---
title: 문자열의 변수 대체에 대해 알고 싶은 모든 것
description: 문자열에서 다양한 방법으로 변수를 사용하여 서식 있는 텍스트를 만들 수 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 786526fb98dbf1b3ec7c5c6c985ac95b85a96259
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301321"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a>문자열의 변수 대체에 대해 알고 싶은 모든 것

문자열에서는 다양한 방법으로 변수를 사용할 수 있습니다. 지금은 이 변수 대체를 호출하지만 변수의 값을 포함하도록 문자열의 서식을 지정하고 싶다면 언제든 참조할 것입니다. 이것은 신입 스크립터에게 자주 설명하는 내용이기도 합니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

## <a name="concatenation"></a>연결

메서드의 첫 번째 클래스를 연결이라고 합니다. 기본적으로 여러 문자열을 가져와 조인합니다. 연결은 아주 오랫동안 서식이 지정된 문자열을 작성하는 용도로 사용했습니다.

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

추가할 값이 몇 개 없어도 연결은 정상적으로 작동합니다. 하지만 이렇게 되면 머지않아 복잡해질 것입니다.

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

이 간단한 예제조차 벌써 읽기가 어려워졌습니다.

## <a name="variable-substitution"></a>변수 대체

PowerShell에는 쉽게 읽을 수 있는 다른 선택지가 있습니다. 문자열에서 변수를 직접 지정하는 것입니다.

```powershell
$message = "Hello, $first $last."
```

문자열 앞뒤에 사용하는 따옴표 유형에 따라 결과가 달라집니다. 큰따옴표로 묶은 문자열은 대체를 허용하지만 따옴표로 묶은 단일 문자열은 허용하지 않습니다. 상황에 맞는 적합한 방법을 사용하면 됩니다.

## <a name="command-substitution"></a>명령 대체

속성 값을 문자열로 가져오는 작업을 시작하면 상황이 좀 더 복잡해집니다. 많은 초보자가 실수하는 부분입니다. 먼저 초보자가 생각하는 작동 방식을 보여드리겠습니다(실제로도 정상적으로 작동하는 것처럼 보일 것입니다).

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

`$directory`에서 `CreationTime`을 가져와야 할 것 같지만 실제로는 이 `Time: c:\windows.CreationTime`을 값으로 가져옵니다. 이 유형의 대체는 기본 변수만 확인하기 때문입니다. 마침표를 문자열의 일부로 간주하기 때문에 더 깊은 값의 확인을 중지합니다.

이 개체는 문자열에 배치될 때 문자열을 기본값으로 제공합니다.
일부 개체는 대신 `System.Collections.Hashtable` 같은 형식 이름을 제공합니다. 주의해야 할 사항입니다.

PowerShell을 사용하면 특수 구문을 사용하여 문자열 내에서 명령을 실행할 수 있습니다. 이렇게 하면 이러한 개체의 속성을 가져오고 다른 명령을 실행하여 값을 가져올 수 있습니다.

```powershell
$message = "Time: $($directory.CreationTime)"
```

일부 상황에서는 유용하지만 변수가 몇 개 없다면 연결을 이용할 때만큼 복잡해질 것입니다.

### <a name="command-execution"></a>명령 실행

문자열 내에서 명령을 실행할 수 있습니다. 저도 이 옵션을 이용할 수 있지만 좋아하지는 않습니다. 식간에 복잡해지고 디버그하기도 어렵기 때문입니다. 명령을 실행하여 변수에 저장하거나 서식 문자열을 사용합니다.

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a>형식 문자열

.NET에서는 대단히 쉬운 방식으로 문자열의 형식을 지정할 수 있습니다. 먼저 이를 위한 정적 메서드를 보여드린 다음 같은 작업을 수행하는 PowerShell 단축 방법을 보여드리겠습니다.

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

여기서는 `{0}` 및 `{1}` 토큰에 대해 문자열을 구문 분석한 다음 이 숫자를 사용하여 제공된 값 중에서 적절한 값을 선택합니다. 문자열의 특정 위치에서 같은 값을 반복하고 싶다면 해당 값을 다시 사용하면 됩니다.

이 접근법은 문자열이 복잡할수록 더 많은 값을 얻을 수 있습니다.

### <a name="format-values-as-arrays"></a>값을 배열로 형식 지정

형식 줄이 너무 길면 먼저 배열에 값을 입력해도 됩니다.

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

전체 배열을 전달하므로 스플래팅 작업은 아니지만 개념은 비슷합니다.

## <a name="advanced-formatting"></a>고급 서식 지정

의도적으로 이들을 .NET에서 호출했는데, 이미 수많은 서식 지정 옵션이 [문서화][]되어 있기 때문입니다. 다양한 데이터 형식의 서식을 지정하는 기본 제공 방법이 있습니다.

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

여기서 살펴보지는 않겠지만 필요하다면 대단히 강력한 서식 지정 엔진으로 사용할 수 있습니다.

## <a name="joining-strings"></a>문자열 조인

값 목록을 함께 연결해야 할 때도 있습니다. 이 작업은 `-join` 연산자로 수행합니다. 문자열 사이에 조인할 문자를 지정할 수도 있습니다.

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

구분 기호 없이 일부 문자열을 `-join`하려면 빈 문자열 `''`를 지정해야 합니다.
하지만 이 작업만 해야 한다면 더 빠른 선택지가 있습니다.

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

`-split` 문자열을 사용할 수 있다는 사실도 알면 도움이 될 겁니다.

## <a name="join-path"></a>Join-Path

자주 간과되지만 파일 경로를 빌드할 때 아주 유용한 cmdlet입니다.

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

장점은 여러 값을 함께 넣어도 백슬래시가 올바르게 작동한다는 것입니다. 사용자나 구성 파일에서 값을 가져올 때는 이 사실이 특히 중요합니다.

`Split-Path` 및 `Test-Path`에서도 아주 잘 작동합니다. [파일 읽기 및 쓰기][]에 관한 제 포스트에서도 관련 내용을 확인할 수 있습니다.

## <a name="strings-are-arrays"></a>문자열은 배열입니다

계속하기 전에 문자열 추가를 설명하겠습니다. 문자열은 단순한 문자 배열임을 잊지 마세요. 여러 문자열을 함께 추가하면 매번 새 배열이 생성됩니다.

이 예제를 확인하세요.

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

아주 기본적인 작업 같지만 문자열을 `$message`에 추가할 때마다 완전히 새로운 문자열이 생성된다는 사실은 모르셨을 겁니다. 메모리를 할당하고 데이터를 복사한 다음 이전 데이터를 삭제합니다.
몇 번만 수행할 때는 큰 문제가 아니지만 이런 식의 루프는 문제를 유발합니다.

### <a name="stringbuilder"></a>StringBuilder

StringBuilder는 수많은 작은 문자열로 큰 문자열을 작성하는 용도로도 자주 사용합니다. 사용자가 추가한 문자열만 수집하며 사용자가 값을 검색할 때만 모든 문자열을 연결하기 때문입니다.

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

이 역시 .NET에서 사용하는 기능입니다. 개인적으로 지금은 잘 사용하지 않지만 알고 있으면 도움이 될 겁니다.

## <a name="delineation-with-braces"></a>중괄호를 이용한 경계 지정

문자열 내에서 접미사를 연결할 때 사용합니다. 변수에 명확한 단어 경계가 없을 때도 있습니다.

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

이 사실을 알려 주신 [/u/real_parbold][] 님께 감사드립니다.

다음 방법을 사용해도 됩니다.

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

개인적으로는 서식 문자열을 사용하지만 알고 있으면 실제 현장에서 도움이 될 것입니다.

## <a name="find-and-replace-tokens"></a>토큰 찾기 및 바꾸기

이러한 기능 대부분은 자체 솔루션을 마련할 필요가 없게 하지만, 많은 템플릿 파일에서 내부 문자열을 바꿔야 할 때도 있습니다.

많은 텍스트가 있는 파일에서 템플릿을 끌어낸다고 가정하겠습니다.

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

많은 토큰을 교체해야 할 것입니다. 여기서 중요한 점은 쉽게 찾고 바꿀 수 있는 고유한 토큰을 사용하는 것입니다. 쉽게 구분할 수 있도록 양쪽 끝에 특수 문자를 사용하곤 합니다.

하지만 얼마 전 새로운 방법을 알게 되었습니다. 자주 사용하는 패턴이므로 이 부분은 여기에 남겨 놓기로 했습니다.

### <a name="replace-multiple-tokens"></a>여러 토큰 바꾸기

토큰 목록을 바꾸고 싶을 때 일반적인 방법을 사용합니다. 해시 테이블 안에 배치한 다음 반복 실행하여 바꾸기 작업을 수행합니다.

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

이러한 토큰은 필요하다면 JSON 또는 CSV에서 로드할 수 있습니다.

### <a name="executioncontext-expandstring"></a>ExecutionContext ExpandString

작은따옴표를 사용하여 대체 문자열을 정의하고 나중에 변수를 확장한다는 기발한 방법이 있습니다. 이 예제를 확인하세요.

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

현재 실행 컨텍스트에 대한 `.InvokeCommand.ExpandString` 호출은 현재 범위에 속하는 변수를 대체에 사용합니다. 여기서 중요한 점은 `$message`는 아주 초기에, 심지어 변수가 존재하기 전에도 정의할 수 있다는 것입니다.

조금만 확장하면 다른 값을 이용해 이 대체를 반복 수행할 수 있습니다.

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

이 작업을 하려면 텍스트 파일에서 대형 이메일 템플릿을 가져오면 됩니다. 이 [제안][]을 해 준 [Mark Kraus][]에게 감사의 말을 전합니다.

## <a name="whatever-works-the-best-for-you"></a>자신의 가장 적합한 작업

저는 서식 문자열 방법을 정말 좋아합니다. 문자열이 복잡하거나 여러 변수가 있을 때 사용합니다. 아주 짧은 요소에는 다음 중 하나를 사용합니다.

## <a name="anything-else"></a>다른 내용을 알고 싶으신가요?

지금까지 많은 내용을 설명했습니다. 이제 새로운 내용을 배워 보시기 바랍니다.

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[제안]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[파일 읽기 및 쓰기]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[문서화]: /dotnet/api/system.string.format#overloads
