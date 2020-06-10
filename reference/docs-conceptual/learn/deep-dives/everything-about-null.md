---
title: $null 관련 세부 사항
description: PowerShell $null은 대개 단순해 보이지만 신경 써야 할 세부 사항이 많이 있습니다. 예기치 않게 Null 값을 실행하는 경우 발생하는 상황을 알아보기 위해 $null에 대해 자세히 살펴보겠습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149476"
---
# <a name="everything-you-wanted-to-know-about-null"></a>$null 관련 세부 사항

PowerShell `$null`은 대개 단순해 보이지만 신경 써야 할 세부 사항이 많이 있습니다. 예기치 않게 `$null` 값을 실행하는 경우 발생하는 상황을 알아보기 위해 `$null`을 자세히 살펴보겠습니다.

> [!NOTE]
> 현재 문서의 [원본 버전][]은 [@KevinMarquette][]가 작성한 블로그에 있습니다. PowerShell 팀은 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 해당 블로그를 확인하세요.

## <a name="what-is-null"></a>NULL이란?

NULL은 알려지지 않았거나 비어 있는 값으로 간주할 수 있습니다. 값이나 개체가 할당되기 전의 변수는 NULL입니다. 이는 특정한 값이 필요한데 해당 값이 NULL인 경우 오류를 생성하는 일부 명령이 있으므로 중요할 수 있습니다.

### <a name="powershell-null"></a>PowerShell $null

`$null`은 NULL을 나타내는 데 사용되는 PowerShell의 자동 변수입니다. 변수에 할당하거나 비교 시 사용하거나 컬렉션에서 NULL의 자리 표시자로 사용할 수 있습니다.

PowerShell은 `$null`을 NULL 값이 있는 개체로 처리합니다. 다른 언어를 사용하는 경우에는 이와 다르게 처리될 수 있습니다.

## <a name="examples-of-null"></a>$null의 예

초기화하지 않은 변수를 사용하려고 할 때마다 값은 `$null`이 됩니다. 대개 이와 같은 방식으로 `$null` 값이 코드에 표시됩니다.

```powershell
PS> $null -eq $undefinedVariable
True
```

변수 이름을 잘못 입력한 경우 PowerShell은 다른 변수로 인식하고 값은 `$null`이 됩니다.

`$null` 값을 알아내는 또 다른 방법은 해당 값을 결과를 제공하지 않는 다른 명령에서 가져오는 것입니다.

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a>$null의 영향

`$null` 값은 표시되는 위치에 따라 코드에 미치는 영향이 다릅니다.

### <a name="in-strings"></a>문자열에서

문자열에서 `$null`을 사용하는 경우 $null은 빈 값(또는 빈 문자열)입니다.

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

로그 메시지에서 사용할 때 변수 주위에 괄호를 사용하는 이유 중 하나입니다. 값이 문자열의 끝에 있는 경우 변수 값의 가장자리를 식별하는 것이 더 중요합니다.

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

이를 통해 빈 문자열과 `$null` 값을 쉽게 찾을 수 있습니다.

### <a name="in-numeric-equation"></a>숫자 수식에서

`$null` 값을 숫자 수식에 사용하는 경우 오류가 발생하지 않으면 결과가 유효하지 않습니다. 경우에 따라 `$null`이 `0`으로 계산되기도 하고 전체 결과를 `$null`로 만들기도 합니다.
다음은 값의 순서에 따라 0 또는 `$null`을 제공하는 곱셈의 예입니다.

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a>컬렉션 대신

컬렉션을 사용하면 인덱스를 사용하여 값에 액세스할 수 있습니다. 실제로 `null`인 컬렉션에 대해 인덱싱하려고 하면 `Cannot index into a null array` 오류가 발생합니다.

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

컬렉션을 가지고 있지만 해당 컬렉션에 없는 요소에 액세스하려고 하면 `$null` 결과를 얻게 됩니다.

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a>개체 대신

지정된 속성이 없는 개체의 속성 또는 하위 속성에 액세스하려고 하면 정의되지 않은 변수를 사용하는 것과 같은 `$null` 값을 얻게 됩니다. 이때 변수가 `$null`인지 실제 개체인지는 중요하지 않습니다.

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a>Null 값 식에 대한 메서드

`$null` 개체에서 메서드를 호출하면 `RuntimeException`이 throw됩니다.

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

`You cannot call a method on a null-valued expression` 구가 표시될 때마다 `$null`에 대해 확인하지 않고 먼저 찾는 것은 변수에 대한 메서드를 호출하는 위치입니다.

## <a name="checking-for-null"></a>$null 확인

예제에서 `$null`을 확인하면 항상 `$null`을 왼쪽에 두는 것을 알 수 있습니다. $null을 왼쪽에 두는 것은 의도적인 것으로 PowerShell 모범 사례로 인정됩니다. 일부 시나리오에서는 $null을 오른쪽에 두면 예상 결과를 얻을 수 없습니다.

다음 예제를 확인하고 결과를 예측해 보세요.

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

`$value`를 정의하지 않으면 첫 번째는 `$true`로 계산되고 메시지는 `The array is $null`이 됩니다. 여기에서 문제는 두 가지가 모두 `$false`가 되도록 허용하는 `$value`를 만들 수 있다는 점입니다.

```powershell
$value = @( $null )
```

이때 `$value`는 `$null`을 포함하는 배열입니다. `-eq`는 배열의 모든 값을 확인하고 일치하는 `$null`을 반환되고 `$false`로 계산됩니다. `-ne`는 `$null`과 일치하지 않는 모든 항목을 반환하며 이 경우에는 결과가 없습니다(이 또한 `$false`로 계산됨). 둘 중 하나가 true가 되어야 할 것 같지만 모두 `$true`가 아닙니다.

두 값을 모두 `$false`로 계산하는 값을 만들 수 있을 뿐 아니라 둘 다 `$true`로 계산되는 값을 만들 수도 있습니다. Mathias Jessen(@IISResetMe)은 해당 시나리오에 대해 자세히 설명하는 [유익한 게시물][]을 제공합니다.

### <a name="psscriptanalyzer-and-vscode"></a>PSScriptAnalyzer 및 VSCode

[PSScriptAnalyzer][] 모듈에는 `PSPossibleIncorrectComparisonWithNull`이라고 불리는 문제를 확인하는 규칙이 있습니다.

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

VS Code는 PSScriptAnalyser 규칙도 함께 사용하므로 스크립트에서 문제를 식별하거나 강조 표시합니다.

### <a name="simple-if-check"></a>간단한 If 확인

사용자가 $null이 아닌 값을 확인하는 일반적인 방법은 비교하지 않고 간단한 `if()` 문을 사용하는 것입니다.

```powershell
if ( $value )
{
    Do-Something
}
```

값이 `$null`이면 해당 값은 `$false`로 계산됩니다. 이러면 쉽게 읽을 수 있지만 찾고 있는 것을 정확히 찾고 있는지 주의해야 합니다. 해당 코드 줄은 다음과 같이 읽습니다.

> `$value`에 값이 있는 경우입니다.

그러나 이것이 전부를 설명하지 않습니다. 해당 줄은 실제로 다음을 의미합니다.

> `$value`가 `$null`, `0`, `$false` 또는 `empty string`이 아닌 경우

다음은 해당 문의 전체 샘플입니다.

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

변수가 값을 가진다는 점뿐만 아니라 다른 값이 `if`로 계산된다는 점을 기억한다면 기본적인 `$false` 확인을 사용해도 괜찮습니다.

며칠 전 몇 가지 코드를 리팩터링할 때 이러한 문제가 발생했습니다. 여기에는 다음과 같은 기본적인 속성 검사가 포함되어 있습니다.

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

저는 존재하는 경우에만 개체 속성에 값을 할당하려고 했습니다. 대부분의 경우 원본 개체에는 `if` 문에서 `$true`로 평가되는 값이 있었습니다. 그러나 가끔 값이 설정되지 않는 문제가 발생했습니다. 코드를 디버그했는데 속성이 있지만 빈 문자열 값인 개체를 발견했습니다. 이로 인해 이전 논리를 사용한 업데이트가 전혀 진행되지 않았습니다. 그래서 적절한 `$null` 확인을 추가했고 모든 작업이 문제없이 진행되었습니다.

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

이러한 버그는 발견하기가 어려우며 `$null`에 대한 값을 적극적으로 확인하게 합니다.

## <a name="nullcount"></a>$null.Count

`$null` 값의 속성에 액세스하려고 하는 경우 해당 속성도 `$null`이 됩니다. `count` 속성은 해당 규칙의 예외입니다.

```powershell
PS> $value = $null
PS> $value.count
0
```

`$null` 값이 있으면 `count`도 `0`이 됩니다. 이 특수 속성은 PowerShell을 통해 추가됩니다.

### <a name="pscustomobject-count"></a>[PSCustomObject] 수

PowerShell의 거의 모든 개체에는 해당 수 속성이 있습니다. 한 가지 중요한 예외는 Windows PowerShell 5.1의 `[PSCustomObject]`입니다(PowerShell 6.0에서 수정됨). 수 속성이 없으므로 해당 값을 사용하려고 하면 `$null` 값을 얻게 됩니다. 사용자가 `$null` 확인 대신 `.Count`를 사용하려고 시도하지 않도록 하기 위해 여기에서 설명합니다.

Windows PowerShell 5.1 및 PowerShell 6.0에서 해당 예제를 실행하면 다른 결과를 얻게 됩니다.

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a>빈 null

서로 다르게 작동하는 특수 형식의 `$null`이 있습니다. 빈 `$null`을 호출하려고 하는데 이것은 사실 [System.Management.Automation.Internal.AutomationNull][]입니다. 빈 `$null`은 아무것도 반환하지 않는 함수 또는 스크립트 블록의 결과로 얻게 됩니다(무효 결과).

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

`$null`과 비교하면 `$null` 값을 얻게 됩니다. 값이 필요한 평가에서 사용되는 경우 값은 항상 `$null`입니다. 하지만 배열 내부에 배치하면 빈 배열과 동일하게 처리됩니다.

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

`$null` 값이 한 개 포함되어 있고 해당 `count`가 `1`인 배열을 가질 수 있습니다. 하지만 배열 내부에 빈 결과를 배치하면 항목으로 계산되지 않습니다. 수는 `0`입니다.

컬렉션처럼 빈 `$null`을 처리하면 이것이 비어 있습니다.

### <a name="pipeline"></a>파이프라인

차이점은 파이프라인을 사용할 때 가장 잘 드러납니다. `$null` 값을 파이프하지만 빈 `$null` 값은 파이프하지 않을 수 있습니다.

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

코드에 따라 논리에서 `$null`을 고려해야 합니다.

먼저 `$null`을 확인하세요.

- 파이프라인에서 Null을 필터링(`... | Where {$null -ne $_} | ...`)
- 파이프라인 함수에서 처리

## <a name="foreach"></a>foreach

`foreach`에서 제가 가장 좋아하는 기능 중 하나는 Foreach가 `$null` 컬렉션에 대해 열거하지 않는다는 점입니다.

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

이로 인해 컬렉션을 열거하기 전에 컬렉션에서 `$null` 확인을 하지 않아도 됩니다. `$null` 값의 컬렉션이 있더라도 `$node`는 여전히 `$null`일 수 있습니다.

Foreach는 PowerShell 3.0을 사용하여 이러한 방식으로 작업하기 시작했습니다. 이전 버전을 사용하는 경우 해당되지 않습니다. 2\.0 호환성을 위한 백포팅 코드를 사용하는 경우 알아야 할 주요 변경 사항 중 하나입니다.

## <a name="value-types"></a>값 형식

기술적으로는 참조 형식만 `$null`일 수 있습니다. 그러나 PowerShell은 매우 관대하며 변수를 모든 형식으로 지정할 수 있습니다. 값 형식을 강력한 형식으로 결정한 경우에는 `$null`이 될 수 없습니다.
PowerShell은 `$null`을 여러 형식의 기본값으로 변환합니다.

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

일부 형식은 `$null`에서 유효한 전환을 할 수 없습니다. 이러한 형식은 `Cannot convert null to type` 오류를 생성합니다.

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a>함수 매개 변수

함수 매개 변수에 강력한 형식의 값을 사용하는 경우가 많습니다. 일반적으로 스크립트에서 기타 변수의 형식을 정의하지 않는 경우에도 매개 변수의 형식을 정의하는 방법을 배웁니다. 함수에 강력한 형식의 변수가 이미 있지만 그것을 모르고 있을 수 있습니다.

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

매개 변수의 형식을 `string`으로 설정하는 즉시 값은 `$null`이 될 수 없습니다. 사용자가 값을 제공했는지 여부를 확인하기 위해 값이 `$null`인지 확인하는 경우가 많습니다.

```powershell
if ( $null -ne $Value ){...}
```

값을 제공하지 않는 경우 `$Value` 는 빈 문자열 `''`입니다. 대신 자동 변수 `$PSBoundParameters.Value`를 사용하세요.

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

해당 함수가 호출될 때 `$PSBoundParameters`는 지정된 매개 변수만 포함합니다.
속성을 확인하려면 `ContainsKey` 메서드도 사용할 수 있습니다.

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a>IsNotNullOrEmpty

값이 문자열인 경우 정적 문자열 함수를 사용하여 값이 `$null`이 되었는지 빈 문자열인지 동시에 확인할 수 있습니다.

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

값 형식이 문자열이어야 하는 경우 이것을 자주 사용하게 됩니다.

## <a name="when-i-null-check"></a>제가 $null 확인을 할 때

방어적인 스크립터가 됩니다. 함수를 호출하고 해당 함수에 변수를 할당할 때마다 저는 `$null`을 확인합니다.

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

`try/catch`를 사용하는 것보다 `if` 또는 `foreach`를 사용하는 것을 훨씬 선호합니다. `try/catch`도 여전히 많이 사용하긴 합니다. 하지만 오류 조건 또는 빈 결과 집합을 테스트할 수 있다면 예외 처리를 실제 예외에만 허용할 수 있습니다.

또한 개체에 대한 값을 인덱싱하거나 메서드를 호출하기 전에 `$null`을 확인하는 경향이 있습니다. 이러한 두 가지 작업은 `$null` 개체에 대해 실패하므로 먼저 유효성을 검사하는 것이 중요하다고 생각합니다. 게시물의 앞부분에서 이러한 시나리오에 대해 이미 설명했습니다.

### <a name="no-results-scenario"></a>결과 없음 시나리오

다른 함수 및 명령은 결과 없음 시나리오를 다르게 처리한다는 점을 알고 있어야 합니다. 많은 PowerShell 명령은 빈 `$null` 및 오류 스트림의 오류를 반환합니다. 그러나 다른 명령은 예외를 throw하거나 상태 개체를 제공합니다. 사용하는 명령이 결과 없음 및 오류 시나리오를 처리하는 방법을 알고 있어야 합니다.

## <a name="initializing-to-null"></a>$null로 초기화

저는 변수를 사용하기 전에 모든 변수를 초기화하는 습관을 가지게 되었습니다. 다른 언어에서는 이 작업을 반드시 수행해야 합니다. 함수 맨 위 또는 foreach 루프를 입력하는 경우 사용하는 모든 값을 정의합니다.

다음 시나리오를 자세히 살펴보세요. 이전에 추적해야 했던 버그의 한 예입니다.

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

여기에서는 `Get-Something`이 결과 또는 빈 `$null`을 반환할 거라고 예상합니다. 오류가 발생하면 로그에 기록합니다. 그런 다음 오류를 처리하기 전에 유효한 결과가 있는지 확인합니다.

해당 코드에서 발생하는 버그는 `Get-Something`이 예외를 throw하고 `$result`에 값을 할당하지 않는 경우입니다. 할당하기 전에 실패했으므로 `$result` 변수에 `$null`을 할당하지 않습니다. `$result`에는 다른 반복에서 이전에 유효했던 `$result`가 계속 포함되어 있습니다.
이 시나리오에서는 `Update-Something`이 동일한 개체에서 여러 번 실행됩니다.

해당 문제를 완화하기 위해 사용 전 foreach 루프 내부에 `$result`를 `$null`로 설정합니다.

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a>범위 문제

범위 지정 문제를 완화하는 데도 도움이 됩니다. 해당 예제에서는 루프에서 값을 `$result`로 할당합니다. 그러나 PowerShell은 함수 외부의 변수 값이 현재 함수의 범위에 영향을 미치는 것을 허용하므로 함수 내부에서 이를 초기화하면 해당 방식으로 생길 수 있는 버그가 완화됩니다.

함수에서 초기화되지 않은 변수가 부모 범위의 값으로 설정된 경우 `$null`이 되지 않습니다.
부모 범위는 함수를 호출하고 동일한 변수 이름을 사용하는 또 다른 함수일 수 있습니다.

동일한 `Do-something` 예제를 사용하고 루프를 제거하면 다음 예제와 같이 표시될 수 있습니다.

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

`Get-Something` 호출이 예외를 throw하는 경우 내 `$null` 확인에서 `Invoke-Something`에서 `$result`를 찾습니다. 함수 내부의 값을 초기화하면 해당 문제가 완화됩니다.

변수에 이름을 붙이는 것은 어려우며 작성자가 여러 함수에서 동일한 변수 이름을 사용하는 것이 일반적입니다. 저는 `$node`, `$result`, `$data`를 항상 사용합니다. 따라서 다른 범위를 가진 값이 있어서는 안 될 장소에서 표시되는 경우가 많습니다.

## <a name="redirect-output-to-null"></a>출력을 $null로 리디렉션

전체 문서에서 `$null` 값에 대해 설명했고 이제 출력을 `$null`로 리디렉션하는 것에 대해서도 다루려고 합니다. 표시하지 않으려는 정보 또는 개체를 출력하는 명령이 있는 경우가 있습니다. 출력을 `$null`로 리디렉션하면 됩니다.

### <a name="out-null"></a>Out-Null

Out-Null 명령은 파이프라인 데이터를 `$null`로 리디렉션하는 기본 제공 방법입니다.

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a>$null에 할당

`Out-Null`을 사용하는 것과 동일한 효과를 위해 `$null`에 명령 결과를 할당할 수 있습니다.

```powershell
$null = New-Item -Type Directory -Path $path
```

`$null`은 상수 값이므로 덮어쓸 수 없습니다. 코드에서 표시되는 방식이 마음에 들진 않지만 `Out-Null`보다 빠르게 실행되는 경우가 많습니다.

### <a name="redirect-to-null"></a>$null로 리디렉션

리디렉션 연산자를 사용하여 출력을 `$null`로 보낼 수도 있습니다.

```powershell
New-Item -Type Directory -Path $path > $null
```

다른 스트림에서 출력되는 명령줄 실행 파일을 처리하는 경우 다음과 같이 모든 출력 스트림을 `$null`로 리디렉션할 수 있습니다.

```powershell
git status *> $null
```

## <a name="summary"></a>요약

해당 문서에서 여러 가지를 설명했고 이것이 다른 심층 분석보다 조각화되었다는 점을 알고 있습니다. 이것은 `$null` 값이 PowerShell의 여러 다른 위치에서 표시될 수 있고 발견되는 위치에 따라 미묘한 차이가 있기 때문입니다. `$null`에 대해 더 잘 이해하고 접할 가능성이 있는 더 모호한 시나리오에 대해 더 잘 알게 되셨길 바랍니다.

<!-- link references -->
[원본 버전]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[유익한 게시물]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
