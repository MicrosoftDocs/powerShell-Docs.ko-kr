---
title: Switch 문에 대해 알고 싶은 모든 것
description: PowerShell의 switch 문은 다른 언어에서 찾을 수 없는 기능을 제공합니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 685a5691599408a0d54ca99bf383bcd7702322a6
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469721"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a>Switch 문에 대해 알고 싶은 모든 것

다른 많은 언어처럼 PowerShell에도 스크립트 내의 실행 흐름을 제어하는 명령이 있습니다. 이러한 문 중 하나가 [switch][] 문이며, PowerShell에서 이 문은 다른 언어에는 없는 기능을 제공합니다. 오늘은 PowerShell `switch` 이용 방법을 자세히 살펴보겠습니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

## <a name="the-if-statement"></a>`if` 문

`if` 문은 가장 먼저 배우는 문에 속합니다. 문이 `$true`라면 스크립트 블록을 실행할 수 있습니다.

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

`elseif` 및 `else` 문을 사용하면 훨씬 더 복잡한 논리를 만들 수 있습니다. 다음은 요일에 대한 숫자 값이 있고 이름을 문자열로 가져오는 예제입니다.

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

이것은 일반적인 패턴이며 처리하는 방법은 대단히 다양합니다. 그중 하나가 `switch`를 이용하는 것입니다.

## <a name="switch-statement"></a>Switch 문

`switch` 문을 사용하면 변수와 가능한 값 목록을 제공할 수 있습니다. 값이 변수와 일치하면 관련 scriptblock이 실행됩니다.

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

이 예제에서는 `$day` 값이 숫자 값 중 하 나와 일치하면 `$result`에 올바른 이름이 할당됩니다. 이 예제에서는 변수 할당만 수행하지만 이러한 스크립트 블록에서는 어떤 PowerShell도 실행할 수 있습니다.

### <a name="assign-to-a-variable"></a>변수에 할당

마지막 예제를 다른 방식으로 작성할 수 있습니다.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

지금은 PowerShell 파이프라인에 값을 배치하고 이 값을 `$result`에 할당합니다. `if` 및 `foreach` 문을 사용하여 같은 작업을 수행할 수도 있습니다.

### <a name="default"></a>기본값

`default` 키워드를 사용하면 일치하는 항목이 없을 때 수행할 동작을 식별할 수 있습니다.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

여기서는 기본 사례에서 `Unknown` 값을 반환합니다.

### <a name="strings"></a>문자열

이전 예제 모음에서는 숫자를 일치시켰지만 문자열을 일치시킬 수도 있습니다.

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

선택사항임을 강조하기 위해 `Component`,`Role` 및 `Location` 매치를 따옴표로 래핑하지는 않았습니다. 대부분의 경우 `switch`는 이를 문자열로 처리합니다.

## <a name="arrays"></a>배열

PowerShell `switch`의 대표적인 멋진 기능은 배열 처리 방식입니다. `switch`에 배열을 제공하면 관련 컬렉션의 각 요소를 처리합니다.

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

배열에 반복된 항목이 있다면 관련 섹션에서 여러 번 일치됩니다.

### <a name="psitem"></a>PSItem

`$PSItem` 또는 `$_`를 사용하면 처리된 현재 항목을 참조할 수 있습니다. 간단한 일치를 수행할 때는 `$PSItem`이 우리가 일치하는 값이 됩니다. 이 변수를 사용하는 다음 섹션에서 몇 가지 고급 일치를 수행하겠습니다.

## <a name="parameters"></a>매개 변수

PowerShell `switch`의 고유한 기능은 다양한 [switch 매개 변수][]로 작동 방식을 변경하는 것입니다.

### <a name="-casesensitive"></a>-CaseSensitive

기본적으로 일치는 대/소문자를 구분하지 않습니다. 대/소문자를 구분해야 한다면 `-CaseSensitive`를 사용하면 됩니다. 다른 switch 매개 변수와 함께 사용할 수 있습니다.

### <a name="-wildcard"></a>-Wildcard

`-wildcard` switch를 사용하면 와일드카드 지원을 사용하도록 설정할 수 있습니다. `-like` 연산자로 각 일치를 수행할 때와 같은 와일드카드 논리를 사용합니다.

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

여기서는 메시지를 처리한 다음 내용에 따라 서로 다른 스트림에 출력합니다.

### <a name="-regex"></a>-Regex

Switch 문은 와일드카드처럼 정규식 일치도 지원합니다.

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

제가 작성한 다른 문서에서 정규식을 사용하는 추가 예제를 확인할 수 있습니다. [정규식을 사용하는 다양한 방법][]

### <a name="-file"></a>-File

Switch 문은 `-File` 매개 변수로 파일을 처리한다는 잘 알려지지 않은 기능이 있습니다. 변수 식을 제공하는 대신 `-file`을 파일 경로와 함께 사용합니다.

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

배열 처리와 비슷한 방식으로 작동합니다. 이 예제에서는 이를 와일드카드와 일치와 결합하고 `$PSItem`을 활용합니다. 그러면 로그 파일을 처리하고 정규식 일치에 따라 경고 및 오류 메시지로 변환합니다.

## <a name="advanced-details"></a>고급 정보

문서화된 기능을 모두 확인했으니 이제 더 복잡한 처리 컨텍스트에서 이러한 기능을 활용할 수 있습니다.

### <a name="expressions"></a>식

`switch`는 변수 대신 식에 넣을 수 있습니다.

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

식의 평가 대상은 일치에 사용한 값이 됩니다.

### <a name="multiple-matches"></a>다중 일치

이 기능은 이미 알고 계실지도 모르지만, `switch`는 여러 조건에 일치시킬 수 있습니다. `-wildcard` 또는 `-regex` 일치를 사용할 때는 더욱더 그렇습니다. 동일한 조건을 여러 번 추가할 수 있으며 이 경우 모든 조건이 트리거됩니다.

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

다음 문 3가지는 모두 실행됩니다. 모든 조건이 (순서대로) 확인됨을 알 수 있습니다. 이것은 각 항목이 각 조건을 확인하는 배열을 처리하는 경우에 적용됩니다.

### <a name="continue"></a>계속

보통은 이 시점에서 `break` 문을 소개하지만 `continue` 사용 방법을 먼저 확인하면 도움이 됩니다. `foreach` 루프처럼 `continue`는 컬렉션의 다음 항목으로 계속 진행하거나 남은 항목이 없다면 `switch`를 종료합니다. 마지막 예제를 continue 문으로 다시 작성하면 문을 하나만 실행할 수 있습니다.

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

3가지 항목을 모두 일치시키는 대신 첫 번째 항목을 일치시키며 switch는 다음 값으로 계속 진행됩니다. 처리할 값이 없기 때문에 switch는 종료됩니다. 다음 예제에서는 와일드카드로 여러 항목을 일치시키는 방법을 알 수 있습니다.

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

입력 파일의 줄에 `Error`와 `Warning` 단어가 모두 포함될 수 있어 첫 번째 항목만 실행하고 파일을 계속 처리하려 합니다.

### <a name="break"></a>중단

`break` 문은 switch를 종료합니다. `continue`가 단일 값에 대해 제공하는 동작과 동일합니다. 차이점은 배열을 처리할 때 드러납니다. `break`는 switch의 모든 처리를 중지하며 `continue`는 다음 항목으로 이동합니다.

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

이 경우 `Error`로 시작하는 줄에 도달하면 오류가 발생하고 switch가 중단됩니다.
`break` 문이 수행하는 작업과 동일합니다. 문자열 내에 `Error`가 있고 시작 부분이 아니라면 이를 경고라고 작성합니다. `Warning`에서도 같은 작업을 수행합니다. 한 줄에 `Error`와 `Warning` 단어가 모두 포함될 수 있지만 하나만 처리하면 됩니다. `continue` 문은 바로 이 작업을 수행합니다.

### <a name="break-labels"></a>Break 레이블

`switch` 문은 `foreach`처럼 `break/continue` 레이블을 지원합니다.

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

개인적으로는 break 레이블을 사용하지 않지만 이 레이블을 처음 보신다면 혼란스러울 수 있으니 설명해드리겠습니다. 여러 `switch`나 `foreach` 문이 중첩되어 있다면 가장 안쪽에 있는 항목 이외의 항목도 중단해야 할 것입니다. `break`의 대상이 될 수 있는 `switch`에 레이블을 배치하면 됩니다.

### <a name="enum"></a>열거형

PowerShell 5.0에서 열거형이 도입되었고 이를 switch에서 사용할 수 있습니다.

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

모든 항목을 강력한 형식의 열거형으로 유지하고 싶다면 괄호 안에 배치하면 됩니다.

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

괄호가 필요한 이유는 switch가 `[Context]::Location` 값을 리터럴 문자열로 처리하면 안 되기 때문입니다.

### <a name="scriptblock"></a>ScriptBlock

필요하다면 scriptblock을 사용하여 일치 항목 평가를 수행할 수 있습니다.

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

이렇게 하면 더 복잡해지고 `switch`를 읽기가 어려워질 수 있습니다. 이와 같은 요소를 사용하는 대부분의 경우에는 `if` 및 `elseif` 문을 사용하는 것이 좋습니다. 이미 많은 스위치가 있고 두 항목이 같은 평가 블록에 적중하게 해야 할 때 이것을 사용할 것입니다.

가독성을 높일 수 있는 한 가지 방법은 scriptblock을 괄호 안에 넣는 것입니다.

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

같은 방식으로 실행되지만 중단된 부분을 더 명확하게 확인할 수 있습니다.

### <a name="regex-matches"></a>정규식 $matches

아직 명확하지 않은 항목을 다룰 때는 정규식을 다시 확인해야 합니다. 정규식을 사용하면 `$matches` 변수가 입력됩니다. `$matches` 사용 방법은 [정규식을 사용하는 다양한 방법][]을 말할 때 자세하게 설명하겠습니다. 다음은 명명된 일치를 사용하여 실제로 작동하는 방식을 보여 주는 간단한 예입니다.

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a>$null

기본값이 아니어도 되는 `$null` 값을 일치시킬 수 있습니다.

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

빈 문자열에서도 마찬가집니다.

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a>상수 식

Lee Dailey가 상수 `$true` 식을 사용하여 `[bool]` 항목을 평가할 수 있다고 알려주었습니다.
몇 가지 부울 검사를 수행해야 한다고 상상해 보세요.

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

이 방법을 이용하면 쉽게 여러 부울 필드의 상태를 평가하고 조치를 취할 수 있습니다. 이 방법의 장점은 아직 평가되지 않은 값의 상태를 한 번 일치 대칭 이동할 수 있다는 것입니다.

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

이 예제에서 `$isEnabled`를 `$true`로 설정하면 `$isVisible`도 `$true`로 설정됩니다. 그리고 `$isVisible`이 평가되면 관련 scriptblock이 호출됩니다. 직관적이진 않지만 현명한 작동 방식 활용법입니다.

### <a name="switch-automatic-variable"></a>$switch 자동 변수

`switch`는 관련 값을 처리할 때 열거자를 만들고 `$switch`라고 부릅니다. 이것은 PowerShell에서 자동으로 생성되는 변수이며 사용자가 직접 조작할 수 있습니다.

이 방법은 [/u/frmadsen](https://www.reddit.com/user/frmadsen) 님이 알려주었습니다.

<div class="reddit-embed" data-embed-media="www.redditmedia.com" data-embed-parent="false" data-embed-live="false" data-embed-uuid="8f6edbf1-abc6-4513-971e-ccd1d202889d" data-embed-created="2018-12-25T22:05:33.986Z"><a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">(IT 학생인) 제가 PowerShell을 마스터하려면 무엇을 배워야 할까요?</a>라는 토론의 <a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">댓글</a>에서 알려준 사실입니다.</div><script async src="https://www.redditstatic.com/comment-embed.js"></script>

다음과 같은 결과가 도출됩니다.

```Output
2
4
```

열거자를 앞으로 옮기면 다음 항목은 `switch`에서 처리하지 않지만 사용자는 해당 값에 직접 액세스할 수 있습니다. 저는 이것을 광기라고 부릅니다.

## <a name="other-patterns"></a>기타 패턴

### <a name="hashtables"></a>해시 테이블

제 게시물 중 최고의 인기를 자랑하는 것은 [해시 테이블][] 관련 게시물입니다. `hashtable`의 대표적인 사용 사례는 조회 테이블입니다. `switch` 문이 자주 처리하는 일반적인 패턴에 대한 또 다른 접근 방식입니다.

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

`switch`를 조회로만 사용할 때는 주로 `hashtable`를 대신 사용합니다.

### <a name="enum"></a>열거형

PowerShell 5.0에서 도입된 `Enum`을 이 경우에도 사용할 수 있습니다.

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

이 문제를 해결하는 방법을 모두 살펴보려면 종일 해도 모자랄 것입니다. 여러분에게 이러한 선택지가 있음을 알려드리고 싶을 뿐입니다.

## <a name="final-words"></a>맺음말

Switch 문은 겉으로 보기엔 간단하지만 대부분의 사용자는 사용할 수 있음을 알지도 못하는 고급 기능을 제공합니다. Switch 문은 이러한 기능을 함께 사용할 때 강력한 효과를 발휘합니다. 이제까지 몰랐던 사실을 배우셨길 바랍니다.

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch 매개 변수]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[정규식을 사용하는 다양한 방법]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[해시 테이블]: everything-about-hashtable.md
