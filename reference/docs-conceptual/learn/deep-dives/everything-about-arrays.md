---
title: 배열에 대해 알고 싶은 모든 것
description: 배열은 대부분의 프로그래밍 언어가 제공하는 기본적인 언어 기능입니다.
ms.date: 10/08/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b26aa11aadbeea1984b2754cfcad061c7fa3ff1e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "91852564"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a>배열에 대해 알고 싶은 모든 것

[배열][]은 대부분의 프로그래밍 언어가 제공하는 기본적인 언어 기능입니다. 사용하지 않기가 어려운 값 또는 개체 컬렉션입니다. 배열과 배열이 제공해야 하는 모든 혜택을 자세히 살펴보겠습니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

## <a name="what-is-an-array"></a>배열이란 무엇일까요?

먼저 배열에 관한 기본적인 기술적 설명과 대부분의 프로그래밍 언어에서 배열을 사용하는 방법을 살펴본 다음 PowerShell에서 배열을 사용하는 다른 방법을 설명하겠습니다.

배열은 여러 항목의 컬렉션 역할을 하는 데이터 구조입니다. 배열 전체를 반복하거나 인덱스를 사용하여 개별 항목에 액세스할 수 있습니다. 배열은 순차적인 메모리 청크 형태로 생성되며 각 값은 다른 값 옆에 저장됩니다.

수업을 진행하면서 각 항목을 자세히 살펴보겠습니다.

## <a name="basic-usage"></a>기본 사용법

배열은 PowerShell의 기본 기능이므로 간단한 구문을 이용하면 PowerShell에서 사용할 수 있습니다.

### <a name="create-an-array"></a>배열 만들기

`@()`을 이용하면 빈 배열을 만들 수 있습니다.

```powershell
PS> $data = @()
PS> $data.count
0
```

배열을 만들고 `@()` 괄호 안에 넣기만 하면 초기값을 지정할 수 있습니다.

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

이 배열에는 4가지 항목이 있습니다. `$data` 변수를 호출하면 항목 목록이 표시됩니다. 문자열 배열이라면 문자열마다 한 줄씩 가져옵니다.

여러 줄에 배열을 선언할 수도 있습니다. 이 경우 쉼표는 선택 사항이며 대부분의 경우 제거됩니다.

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

이처럼 여러 줄에 배열을 선언하는 방식을 선호합니다. 여러 항목이 있으면 읽기도 쉽지만 소스 제어를 사용할 때 이전 버전과 쉽게 비교할 수도 있습니다.

#### <a name="other-syntax"></a>기타 구문

일반적으로 `@()`가 배열을 만드는 구문으로 간주되지만 대부분의 경우 쉼표로 구분된 목록을 사용합니다.

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a>Write-Output으로 배열 만들기

아주 유용한 방법이 있는데 `Write-Output`을 사용하면 콘솔에서 문자열을 빠르게 만들 수 있다는 것입니다.

```powershell
$data = Write-Output Zero One Two Three
```

매개 변수가 문자열을 허용한다면 문자열 주위에 따옴표를 붙일 필요가 없어 편리합니다. 스크립트에서는 이 작업을 수행하지 않지만 콘솔에서는 유용한 기능입니다.

### <a name="accessing-items"></a>항목 액세스

이제 항목이 포함된 배열이 있으니 배열에 액세스하고 항목을 업데이트하고 싶을 것입니다.

#### <a name="offset"></a>Offset

개별 항목에 액세스할 때는 0부터 시작하는 오프셋 값과 함께 대괄호 `[]`를 사용합니다. 다음은 배열의 첫 번째 항목을 가져오는 방법입니다.

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

여기서 0을 사용하는 이유는 첫 번째 항목이 목록 시작 부분에 있어 오프셋 0개 항목을 이용해 가져와야 하기 때문입니다. 두 번째 항목을 가져오려면 오프셋 1을 이용해 첫 번째 항목을 건너뛰어야 합니다.

```powershell
PS> $data[1]
One
```

이것은 마지막 항목은 오프셋 3이라는 뜻입니다.

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a>인덱스

이제 이 예제에서 이러한 값을 선택한 이유를 아실 겁니다. 실제로 오프셋이기 때문에 오프셋이라 소개했지만 일반적으로는 인덱스라고 합니다. `0`에서 시작하는 인덱스입니다. 이 문서의 나머지 부분에서는 오프셋을 인덱스라고 하겠습니다.

#### <a name="special-index-tricks"></a>특수 인덱스 기술

대부분의 언어에서는 단일 숫자만 인덱스로 지정하고 단일 항목만 다시 가져올 수 있습니다.
PowerShell은 훨씬 더 유연합니다. 여러 인덱스를 동시에 사용할 수 있습니다. 인덱스 목록을 제공하면 여러 항목을 선택할 수 있습니다.

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

제공된 인덱스의 순서에 따라 항목이 반환됩니다. 인덱스를 복제하면 항목을 두 번 가져옵니다.

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

기본 제공 `..` 연산자를 사용하여 일련의 숫자를 지정할 수 있습니다.

```powershell
PS> $data[1..3]
One
Two
Three
```

반대 경우에도 마찬가지입니다.

```powershell
PS> $data[3..1]
Three
Two
One
```

음수 인덱스 값을 사용하면 끝에서부터 오프셋할 수 있습니다. 따라서 목록의 마지막 항목이 필요하다면 `-1`을 사용하면 됩니다.

```powershell
PS> $data[-1]
Three
```

여기서 주의해야 할 항목은 `..` 연산자입니다. `0..-1` 및 `-1..0` 시퀀스는 `0,-1` 및 `-1,0`까지의 값을 평가합니다. 이 사실을 잊으면 `$data[0..-1]`을 이용하고 이것이 모든 항목을 열거한다고 생각하기 쉽습니다. `$data[0..-1]`은 배열의 첫 번째 항목과 마지막 항목을 제공하여 `$data[0,-1]`과 같은 값을 제공합니다(다른 값은 제공하지 않습니다).

#### <a name="out-of-bounds"></a>범위 초과

대부분의 언어에서 배열 끝을 벗어나는 항목의 인덱스에 액세스하려 하면 오류나 예외가 발생합니다. PowerShell은 어떤 것도 자동으로 반환하지 않습니다.

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a>Null 배열로 인덱싱할 수도 없습니다.

변수가 `$null`이며 배열처럼 인덱싱하려 하면 `Cannot index into a null array` 메시지와 함께 `System.Management.Automation.RuntimeException` 예외가 발생합니다.

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

따라서 내부 요소에 액세스하기 전에 배열이 `$null`이 아닌지 확인해야 합니다.

#### <a name="count"></a>개수

배열 및 기타 컬렉션에는 배열에 있는 항목 수를 알려 주는 count 속성이 있습니다.

```powershell
PS> $data.count
4
```

PowerShell 3.0에서는 대부분의 개체에 count 속성이 추가되었습니다. 단일 개체를 가질 수 있으며 이 경우 카운트는 `1`이 됩니다.

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

`0`을 반환하지 않는다면 `$null`도 count 속성을 가집니다.

```powershell
PS> $null.count
0
```

여기에는 몇 가지 함정이 있는데, 이 문서 후반부에서 `$null` 또는 빈 배열을 다룰 때 말씀드리겠습니다.

#### <a name="off-by-one-errors"></a>OBO(off-by-one) 오류

대표적인 프로그래밍 오류는 배열이 인덱스 0에서 시작되기 때문에 발생합니다. OBO(off-by-one) 오류는 주로 두 가지 방법으로 발생합니다.

첫 번째 방법은 두 번째 항목을 원한다고 생각하여 `2` 인덱스를 사용했는데 실제로는 세 번째 항목을 얻는 것입니다. 혹은 항목 4개가 있고 마지막 항목을 원하기 때문에 count를 이용해 마지막 항목에 액세스하는 경우도 있습니다.

```powershell
$data[ $data.count ]
```

PowerShell에서 같은 작업을 수행하면 인덱스 4에 있는 실제 항목인 `$null`을 얻게 됩니다. 앞에서 배운 `$data.count - 1`이나 `-1`을 사용해야 합니다.

```powershell
PS> $data[ $data.count - 1 ]
Three
```

여기서 `-1` 인덱스를 사용하면 마지막 요소를 가져올 수 있습니다.

```powershell
PS> $data[ -1 ]
Three
```

Lee Dailey는 `$data.GetUpperBound(0)`를 사용하면 최대 인덱스 번호를 가져올 수 있다고 알려주었습니다.

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

두 번째 일반적인 방법은 목록을 반복하면서 적절한 시간에 중지하지 않는 것입니다. `for` 루프 사용을 다룰 때 자세히 설명하겠습니다.

### <a name="updating-items"></a>항목 업데이트

동일한 인덱스를 사용하여 배열의 기존 항목을 업데이트할 수 있습니다. 이 방법을 이용하면 직접 액세스하여 개별 항목을 업데이트할 수 있습니다.

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

마지막 요소 밖에 있는 항목을 업데이트하려고 하면 `Index was outside the bounds of the array.` 오류가 발생합니다.

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

여기에 대해서는 배열 확대 방법을 다룰 때 자세히 설명하겠습니다.

### <a name="iteration"></a>반복

특정 시점에서 전체 목록을 탐색하거나 반복하고 배열의 각 항목에 특정 작업을 수행해야 할 수도 있습니다.

#### <a name="pipeline"></a>파이프라인

배열과 PowerShell 파이프라인은 대단히 효율적인 조합입니다. 이러한 값을 처리하는 가장 간단한 방법입니다. 배열을 파이프라인에 전달하면 배열 내 각 항목은 개별적으로 처리됩니다.

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

`$PSItem`을 처음 본다면 `$_`와 같다고 생각하시면 됩니다. 둘 다 파이프라인의 현재 개체를 나타내기 때문에 어느 쪽을 사용해도 됩니다.

#### <a name="foreach-loop"></a>ForEach 루프

`ForEach` 루프는 컬렉션과 아주 잘 어울립니다. `foreach ( <variable> in <collection> )` 구문을 사용합니다.

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a>ForEach 메서드

잊어버릴 때가 잦지만 단순한 작업에 어울리는 메서드입니다. PowerShell을 사용하면 컬렉션에서 `.ForEach()`를 호출할 수 있습니다.

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

`.foreach()`는 스크립트 블록인 매개 변수를 사용합니다. 괄호를 삭제하고 스크립트 블록만 제공하면 됩니다.

```powershell
$data.foreach{"Item [$PSItem]"}
```

잘 알려지지 않은 구문이지만 효과는 동일합니다. 이 `foreach` 메서드는 PowerShell 4.0에서 추가되었습니다.

#### <a name="for-loop"></a>For 루프

`for` 루프는 대부분의 다른 언어에서는 자주 사용하지만 PowerShell에서는 보기 어렵습니다. 대부분의 경우 배열을 탐색하는 컨텍스트에서 등장합니다.

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

가장 먼저 할 일은 `0``$index`를 초기화하는 것입니다. 그런 다음 `$index`가 `$data.count`보다 작아야 한다는 조건을 추가합니다. 마지막으로, 루프할 때마다 인덱스를 `1`씩 늘리도록 지정합니다. 이 경우 `$index++`는 `$index = $index + 1`의 축약형입니다.

`for` 루프를 사용할 때는 항상 조건을 주의 깊게 확인해야 합니다. 여기서는 `$index -lt $data.count`를 사용했습니다. 논리가 조금만 잘못돼도 논리에서 OBO(off-by-one) 오류가 발생하기 쉽습니다. `$index -le $data.count` 또는 `$index -lt ($data.count - 1)`을 사용하는 것은 아주 약한 잘못에 속합니다. 너무 많거나 적은 항목을 처리한 결과가 발생하게 됩니다. 이것은 전형적인 OBO(off-by-one) 오류에 속합니다.

#### <a name="switch-loop"></a>Switch 루프

이것은 간과하기 쉬운 항목입니다. [Switch 문][]에 배열을 제공하면 배열에 있는 각 항목을 확인합니다.

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

Switch 문을 이용하면 수많은 유용한 작업을 수행할 수 있습니다. 이 작업의 또 다른 전용 문서가 있습니다.

- [Switch 문에 대해 알고 싶은 모든 것][switch 문]

#### <a name="updating-values"></a>값 업데이트

배열이 문자열 또는 정수(값 형식) 컬렉션이라면 루프할 때 배열의 값을 업데이트해야 할 때가 있습니다. 위의 루프 대부분은 값의 복사본을 보유하는 루프 내 변수를 사용합니다. 이 변수를 업데이트하면 배열의 원래 값은 업데이트되지 않습니다.

이 문에 대한 예외는 `for` 루프입니다. 배열을 탐색하고 그 안에 있는 값을 업데이트하려면 `for` 루프를 이용하면 됩니다.

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

이 예제에서는 인덱스를 사용하여 값을 가져오고 몇 가지 사항을 변경한 다음 동일한 인덱스를 사용하여 다시 할당합니다.

## <a name="arrays-of-objects"></a>개체 배열

지금까지는 배열에 값 형식만 배치했지만 배열은 개체를 포함할 수도 있습니다.

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

많은 cmdlet은 변수에 할당될 때 개체의 컬렉션을 배열로 반환합니다.

```powershell
$processList = Get-Process
```

앞에서 언급한 모든 기본 기능은 여전히 개체 배열에 적용되지만 몇 가지 세부 사항을 확인해야 합니다.

### <a name="accessing-properties"></a>속성 액세스

인덱스를 사용하여 값 형식과 마찬가지로 컬렉션의 개별 항목에 액세스할 수 있습니다.

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

속성에 직접 액세스하여 속성을 업데이트할 수 있습니다.

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a>배열 속성

일반적으로 모든 속성에 액세스하려면 다음과 같이 전체 목록을 열거해야 합니다.

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

또는 `Select-Object -ExpandProperty` cmdlet을 사용해도 됩니다.

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

하지만 PowerShell은 `LastName`을 직접 요청하는 기능을 제공합니다. PowerShell은 사용자를 대신해 모든 항목을 열거하고 깔끔한 목록을 반환합니다.

```powershell
PS> $data.LastName

Marquette
Doe
```

열거는 계속 진행되지만 복잡해 보이지 않게 됩니다.

### <a name="where-object-filtering"></a>Where-Object 필터링

`Where-Object`를 이용해 개체 속성을 바탕으로 배열을 필터링하고 원하는 항목을 선택하는 기능입니다.

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

같은 쿼리를 작성하여 원하는 `FirstName`을 가져올 수 있습니다.

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a>Where()

배열에는 필터의 `scriptblock`을 지정할 수 있는 `Where()` 메서드가 있습니다.

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

이 기능은 PowerShell 4.0에서 추가되었습니다.

### <a name="updating-objects-in-loops"></a>루프에서 개체 업데이트

값 형식이 있는 배열을 업데이트하는 유일한 방법은 루프를 사용하는 것입니다. 값을 교체해야 하는 인덱스를 파악해야 하기 때문입니다. 개체는 참조 형식이므로 더 많은 선택지를 사용할 수 있습니다. 간단한 예제는 다음과 같습니다.

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

이 루프는 `$data` 배열의 모든 개체를 탐색합니다. 개체는 참조 형식이므로 `$person` 변수는 배열에 있는 것과 정확하게 같은 개체를 참조합니다. 따라서 속성을 업데이트하면 원본도 업데이트됩니다.

하지만 이 방법으로 전체 개체를 바꿀 수는 없습니다. 새 개체를 `$person` 변수에 할당하면 변수 참조 업데이트되어 배열 내 원래 개체를 가리키지 않게 됩니다. 예상했던 결과는 아닐 것입니다.

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a>연산자

PowerShell의 연산자는 배열에서도 작동합니다. 일부 연산자는 작동 방식이 약간 다릅니다.

### <a name="-join"></a>-join

`-join` 연산자는 가장 알기 쉬운 연산자이므로 제일 먼저 설명하겠습니다. `-join` 연산자를 좋아해서 자주 사용합니다. 배열의 모든 요소를 지정한 문자 또는 문자열에 조인합니다.

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

제가 좋아하는 `-join` 연산자의 기능은 단일 항목 처리입니다.

```powershell
PS> 1 -join '-'
1
```

로깅 및 자세한 정보 메시지에서 이 연산자를 사용합니다.

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a>-join $array

다음은 Lee Dailey가 알려준 유용한 방법입니다. 구분 기호 없이 모든 항목을 조인하려면 대신 이 작업을 수행해야 합니다.

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

배열이 있는 `-join`을 접두사 없는 매개 변수로 사용할 수 있습니다. 이 예제를 살펴보면 무슨 말인지 확인하실 수 있습니다.

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a>-replace 및 -split

`-replace` 및 `-split` 같은 다른 연산자는 배열의 각 항목에 대해 실행됩니다. 이런 방식으로 사용해보지 않았지만 다음 예시에서 확인하실 수 있습니다.

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a>-contains

`-contains` 연산자를 사용하면 값의 배열에 지정한 값이 있는지를 확인할 수 있습니다.

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a>-in

단일 값이 여러 값 중 하나와 일치하는지 확인하고 싶다면 `-in` 연산자를 사용하면 됩니다. 값은 연산자 왼쪽에 있고 배열은 오른쪽에 있습니다.

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

이 방법은 목록이 길다면 비용이 많이 들 수 있습니다. 다수의 값을 확인할 때는 주로 정규식 패턴을 사용합니다.

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a>-eq 및 -ne

같음을 이용하면 배열이 복잡해질 수 있습니다. 배열이 왼쪽에 있으면 모든 항목을 비교합니다. `True`를 반환하는 대신 일치하는 개체를 반환합니다.

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

`-ne` 연산자를 사용하면 대상 값과 같지 않은 모든 값을 가져옵니다.

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

`if()` 문에서 이 연산자를 사용하면 반환되는 값은 `True` 값이 됩니다. 값이 반환되지 않는다면 `False` 값이라는 뜻입니다. 다음 두 문은 모두 `True`로 평가됩니다.

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

여기에 관해서는 `$null` 테스트를 다룰 때 다시 설명하겠습니다.

### <a name="-match"></a>-match

`-match` 연산자는 컬렉션의 각 항목을 일치시킵니다.

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

단일 값으로 `-match`를 사용하면 일치 정보에 특수 변수인 `$Matches`가 입력됩니다. 배열을 이 방식으로 처리할 때는 적용되지 않습니다.

`Select-String`과 동일한 방법을 사용할 수 있습니다.

```powershell
$servers | Select-String SQL
```

[을 사용하는 다양한 방법][]이라는 게시물에서 `Select-String`,`-match`,`$matches` 변수를 자세히 살펴보겠습니다.

### <a name="null-or-empty"></a>$null 또는 비어 있음

`$null` 또는 빈 배열에 대한 테스트는 쉽지가 않습니다. 다음을 배열에서 자주 발생하는 함정입니다.

얼핏 보면 이 문은 정상적으로 작동하는 것처럼 보입니다.

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

하지만 앞에서 `-eq`는 배열의 각 항목을 확인한다고 말씀드렸습니다. 따라서 배열이 단일 $null 값을 이용하는 여러 항목으로 구성될 수 있으며 이 배열은 `$true`로 평가됩니다.

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

그래서 `$null`은 되도록 연산자 왼쪽에 배치해야 합니다. 이렇게 하면 이 시나리오는 문제가 되지 않습니다.

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

`$null` 배열은 빈 배열과는 다릅니다. 배열이 있다면 배열 안에 있는 개체 수를 확인하세요. 배열이 `$null`이라면 수는 `0`입니다.

```powershell
if ( $array.count -gt 0 )
{
    "Array isn't empty"
}
```

여기서는 한 가지 함정을 주의해야 합니다. 개체가 하나뿐이더라도 `count`를 사용할 수 있지만 개체가 `PSCustomObject`일 때는 예외입니다. 이것은 버그로 PowerShell 6.1에서 수정되었습니다.
반가운 소식이지만 아직 많은 사용자가 5.1을 사용하고 있으니 주의해야 합니다.

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

아직 PowerShell 5.1을 사용한다면 개체를 배열에 래핑한 다음 개수를 확인해야 정확한 수를 알 수 있습니다.

```powershell
if ( @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

안전하게 하려면 `$null`를 확인한 다음 개수를 확인합니다.

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

### <a name="all--eq"></a>All -eq

얼마 전 어떤 분이 [배열의 모든 값이 지정된 값과 일치하는지 확인하는 방법][]을 물어보셨는데
Reddit 사용자 **/u/bis** 님이 잘못된 값을 확인한 다음 결과를 대칭 이동하면 된다는 탁월한 [해결책][]을 알려주었습니다.

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a>배열에 추가

이제 배열에 항목을 추가하는 방법이 궁금하실 겁니다. 결론부터 말하자면 불가능합니다. 배열은 메모리에서 크기가 고정되어 있습니다. 크기를 늘리거나 단일 항목을 추가하려면 새 배열을 만들고 기존 배열의 모든 값을 복사해야 합니다. 이렇게 하면 작업량이 많을 것 같지만 PowerShell에서는 새 배열을 간단하게 만들 수 있습니다. PowerShell은 배열에 대해 더하기 연산자(`+`)를 구현합니다.

> [!NOTE]
> PowerShell은 빼기 연산을 구현하지 않습니다. 배열을 유연하게 대체하려면 [일반 `List`](#generic-list) 개체를 사용해야 합니다.

### <a name="array-addition"></a>배열 추가

더하기 연산자를 배열과 함께 사용하면 새 배열을 만들 수 있습니다. 따라서 다음과 같은 두 배열이 제공됩니다.

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

두 배열을 모두 추가하면 새 배열을 얻을 수 있습니다.

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a>Plus equals +=

현재 위치에서 새 배열을 만들고 다음과 같이 항목을 추가할 수 있습니다.

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

`+=`을 사용할 때마다 복제하여 새 배열을 만든다는 사실만 기억하면 됩니다. 작은 데이터 세트에서는 문제가 되지 않지만 크기가 커지면 효율이 극도로 떨어집니다.

### <a name="pipeline-assignment"></a>파이프라인 할당

파이프라인의 결과를 변수에 할당할 수 있습니다. 여러 항목이 있다면 배열이 됩니다.

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

일반적으로 우리는 파이프라인 사용을 전형적인 PowerShell 일회성 사용이라고 생각합니다. `foreach()` 문과 다른 루프를 이용해 파이프라인을 활용할 수 있습니다. 따라서 여러 항목을 루프 내 배열에 추가하는 대신 파이프라인에 놓으면 됩니다.

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a>배열 유형

기본적으로 PowerShell의 배열은 `[PSObject[]]` 형식으로 생성됩니다. 이렇게 하면 어떤 형식의 개체나 값도 포함할 수 있습니다. 모든 요소를 `PSObject` 형식에서 상속하기 때문에 가능한 일입니다.

### <a name="strongly-typed-arrays"></a>강력한 형식의 배열

비슷한 구문을 사용하여 어떤 형식의 배열도 만들 수 있습니다. 강력한 형식의 배열을 만들 때는 지정된 형식의 값이나 개체만 포함할 수 있습니다.

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a>ArrayList

배열에 항목을 추가하는 일은 제한이 가장 심한 작업이지만 몇 가지 다른 컬렉션을 이용하면 이 문제를 해결할 수 있습니다.

`ArrayList`는 빠르게 작동하는 배열을 만들 때 가장 먼저 떠올리는 요소입니다. 필요한 모든 곳에서 개체 배열처럼 작동하지만 항목 추가를 빠르게 처리합니다.

다음은 `ArrayList`를 만들고 항목을 추가하는 방법입니다.

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

형식을 얻기 위해 .NET을 호출합니다. 이 경우에는 기본 생성자를 사용하여 형식을 만듭니다. 그런 다음 `Add` 메서드를 호출하여 항목을 추가합니다.

줄 시작 부분에 `[void]`를 사용하는 이유는 반환 코드를 표시하지 않기 위함입니다. 일부 .NET 호출로 이 작업을 수행할 수 있지만 예기치 않은 출력이 생성될 수 있습니다.

배열에 있는 데이터가 문자열뿐이라면 [StringBuilder][] 사용도 검토해봐야 합니다. 거의 동일하지만 문자열만 처리하는 몇 가지 메서드가 있습니다. `StringBuilder`는 성능을 위해 특별히 설계되었습니다.

많은 사람들이 배열에서 `ArrayList`로 전환하고 있습니다. 그러나 이 기능은 C#에서 일반 지원이 제공되지 않을 때 도입되었습니다. `ArrayList`는 일반 `List[]`가 지원되면서 사용이 중단되었습니다.

### <a name="generic-list"></a>일반 링크

일반 형식은 일반화된 클래스를 정의하는 C#에서의 특수 형식으로 사용자는 생성 시 C#에서 사용하는 데이터 형식을 지정합니다. 따라서 숫자 또는 문자열 목록이 필요하다면 `int` 또는 `string` 유형 목록을 원한다고 정의하면 됩니다.

문자열 목록을 만드는 방법은 다음과 같습니다.

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

숫자 목록을 만드는 방법이기도 합니다.

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

먼저 개체를 만드는 대신 기존 배열을 이런 식으로 목록에 캐스팅해도 됩니다.

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

PowerShell 5 이상에서는 `using namespace` 문을 이용해 구문을 줄일 수 있습니다. `using` 문은 스크립트의 첫 번째 줄이어야 합니다. PowerShell은 네임스페이스를 선언하여 사용자가 데이터 유형을 참조할 때 이 문을 그대로 둡니다.

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

따라서 `List`가 훨씬 더 유용해집니다.

비슷한 `Add` 메서드를 사용할 수도 있습니다. ArrayList와는 달리 `Add` 메서드에는 반환값이 없으므로 `void`하지 않아도 됩니다.

```powershell
$myList.Add(10)
```

다른 배열 같은 요소에도 계속 액세스할 수 있습니다.

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a>List[PSObject]

어떤 형식의 목록도 가질 수 있지만 개체 형식을 모른다면 `[List[PSObject]]`를 사용하여 해당 형식을 포함할 수 있습니다.

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a>Remove()

`ArrayList` 및 일반 `List[]`는 모두 컬렉션의 항목 제거 기능을 지원합니다.

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

값 형식을 작업할 때는 목록의 첫 번째 항목이 제거됩니다. 반복 호출하면 값을 계속 제거할 수 있습니다. 참조 형식이 있다면 제거할 개체를 제공해야 합니다.

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

Remove 메서드는 컬렉션에서 항목을 찾아 제거할 수 있다면 `true`를 반환합니다.

### <a name="more-collections"></a>추가 컬렉션

다른 많은 컬렉션을 사용할 수 있지만 바람직한 일반 배열 대체는 다음과 같습니다.
여기에 관해 자세히 알고 싶다면 [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html)가 정리한 이 [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c)를 참조하세요.

## <a name="other-nuances"></a>기타 뉘앙스

주요 기능은 모두 살펴보았으니 지금부터는 마무리하기 전에 몇 가지 추가 요소를 말씀드리겠습니다.

### <a name="pre-sized-arrays"></a>미리 크기가 지정된 배열

배열을 만든 후에는 크기를 변경할 수 없다고 말씀드렸습니다. `new($size)` 생성자로 호출하면 미리 정한 크기의 배열을 만들 수 있습니다.

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a>배열 곱하기

재미 있는 기법이 있는데 바로 배열을 정수로 곱하는 것입니다.

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a>0으로 초기화

모든 항목이 0인 배열을 만들어야 할 때가 자주 찾아옵니다. 정수만 이용할 계획이라면 정수의 강력한 형식 배열은 기본적으로 모두 0으로 설정됩니다.

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

곱하기 기법을 이용하여 이 작업을 할 수도 있습니다.

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

곱하기 기술의 장점은 어떤 값도 사용할 수 있다는 것입니다. 따라서 기본값이 `255`라면 이 방법도 도움이 됩니다.

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a>중첩된 배열

배열 안에 있는 배열을 중첩된 배열이라고 합니다. PowerShell에서는 중첩된 배열을 잘 사용하지 않지만 다른 언어에서는 자주 사용합니다. 데이터가 패턴 같은 그리드에 들어맞는다면 배열 내 배열을 사용하는 것이 좋습니다.

2차원 배열은 두 가지 방법으로 만들 수 있습니다.

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

이러한 예제에서는 쉼표가 대단히 중요합니다. 앞에서 여러 줄이 있으며 쉼표가 선택 사항인 일반 배열을 소개해드렸습니다. 이것은 다차원 배열에는 적용되지 않습니다.

지금은 중첩된 배열을 사용하기 때문에 인덱스 표기법 사용 방법이 약간 다릅니다. 위의 `$data`를 사용하여 값 3에 액세스합니다.

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

각 배열 중첩 수준에 대괄호 집합을 추가합니다. 첫 번째 대괄호 집합은 가장 바깥쪽 배열에 사용하며 이곳에서 작업을 수행합니다.

### <a name="write-output--noenumerate"></a>Write-Output -NoEnumerate

PowerShell은 배열 래핑 해제나 열거를 좋아합니다. PowerShell에서 파이프라인을 사용할 때의 핵심 요소지만 두 작업을 원치 않을 때도 있습니다.

자세한 정보를 확인하고자 자주 개체를 `Get-Member`에 연결합니다. 배열을 연결하면 래핑이 해제되며 Get-Member는 실제 배열이 아니 배열의 멤버를 보게 됩니다.

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

배열의 래핑 해제를 방지하려면 `Write-Object -NoEnumerate`를 사용하면 됩니다.

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

두 번째 방법은 해킹에 가깝습니다(그리고 이런 식의 해킹은 지양합니다). 연결하기 전에 배열 앞에 쉼표를 배치합니다.

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a>배열 반환

이러한 배열 래핑 해제는 함수에서 값을 출력하거나 반환하는 경우에도 발생합니다. 출력을 변수에 할당하더라도 배열을 얻을 수 있기 때문에 일반적으로는 문제가 되지 않습니다.

중요한 것은 새 배열이 생성된다는 점입니다. 이것이 문제가 된다면 `Write-Output -NoEnumerate $array`나 `return ,$array`로 해결하면 됩니다.

## <a name="anything-else"></a>다른 내용을 알고 싶으신가요?

습득하기엔 많은 내용이라는 걸 잘 압니다. 이 문서를 읽을 때마다 배움을 얻고 앞으로도 오랫동안 참조 자료로 사용하시길 바랍니다. 이 문서가 도움이 되는 것 같다면 도움이 필요한 다른 사람에게도 알려 주세요.

제가 작성한 비슷한 [해시 테이블][] 관련 게시물도 참조하시기 바랍니다.

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[배열]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch 문]: everything-about-switch.md
[해시 테이블]: everything-about-hashtable.md
[을 사용하는 다양한 방법]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[배열의 모든 값이 지정된 값과 일치하는지 확인하는 방법]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[해결책]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
