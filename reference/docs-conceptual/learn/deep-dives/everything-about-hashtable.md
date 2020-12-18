---
title: 해시 테이블에 대해 알고 싶은 모든 것
description: 해시 테이블은 PowerShell에서 대단히 중요하기 때문에 확실하게 이해해야 합니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1539cf6444cab718c1108384c640193d66c85daf
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "93354425"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a>해시 테이블에 대해 알고 싶은 모든 것

잠시 뒤로 돌아가 [해시 테이블][]을 설명하겠습니다. 현재 해시 테이블을 항상 사용합니다. 어젯밤 사용자 그룹 모임이 끝나고 관련 내용을 가르치다가 저 역시 학생과 똑같은 혼란을 겪고 있음을 알게 되었습니다. 해시 테이블은 PowerShell에서 대단히 중요하기 때문에 확실하게 이해해야 합니다.

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다. [PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.

## <a name="hashtable-as-a-collection-of-things"></a>해시 테이블은 다양한 요소의 컬렉션입니다

먼저 기본적으로 **해시 테이블** 은 컬렉션으로 정의된다는 사실을 아셔야 합니다. 이 정의를 알아야 나중에 고급 작업에서 사용할 때 해시 테이블의 기본적인 작동 방식을 이해할 수 있습니다. 이를 이해하지 않으면 혼란을 겪게 됩니다.

## <a name="what-is-an-array"></a>배열이란 무엇일까요?

**해시 테이블** 이 무엇인지 살펴보기 전에 먼저 [배열][]을 설명해야 합니다. 여기서 말하는 배열은 값 또는 개체의 목록 또는 컬렉션입니다.

```powershell
$array = @(1,2,3,5,7,11)
```

항목을 배열 안에 배치하면 `foreach`를 사용하여 목록 전체에서 반복하거나 인덱스를 사용하여 배열 내 개별 요소에 액세스할 수 있습니다.

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

같은 방식으로 인덱스를 사용하여 값을 업데이트할 수도 있습니다.

```powershell
$array[2] = 13
```

배열에 대한 아주 기초적인 내용만 설명했지만 이 내용을 알아야 해시 테이블을 이해할 수 있습니다.

## <a name="what-is-a-hashtable"></a>해시 테이블이란 무엇일까요?

해시 테이블의 기본적인 기술적 정의를 일반적인 관점에서 살펴본 다음 PowerShell에서 사용하는 다른 방법을 설명하겠습니다.

해시 테이블은 배열과 대단히 유사한 데이터 구조지만 키를 사용하는 각 값(개체)을 저장한다는 점만 다릅니다. 해시 테이블은 기본 키/값 저장소입니다. 먼저 빈 해시 테이블을 만듭니다.

```powershell
$ageList = @{}
```

해시 테이블을 정의할 때는 괄호 대신 중괄호를 사용해야 합니다. 그런 다음 이런 키를 사용하여 항목을 추가합니다.

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

사용자 이름이 키이며 나이는 저장할 값입니다.

## <a name="using-the-brackets-for-access"></a>액세스에 대괄호 사용

해시 테이블에 값을 추가하면 (배열에서처럼 숫자 인덱스를 사용하는 대신) 같은 키를 사용하여 다시 가져올 수 있습니다.

```powershell
$ageList['Kevin']
$ageList['Alex']
```

Kevin의 나이를 알고 싶다면 그의 이름을 사용하여 액세스합니다. 이 방법을 사용하면 해시 테이블에 값을 추가하거나 업데이트할 수도 있습니다. 위의 `add()` 함수 사용과 비슷합니다.

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

값에 액세스하고 업데이트하는 데 사용할 수 있는 다른 구문이 있습니다. 관련 내용은 이후 섹션에서 다루겠습니다. 다른 언어로 PowerShell을 이용한다면 이러한 예제는 이제까지의 해시 테이블 사용 방법에도 잘 어울릴 것입니다.

### <a name="creating-hashtables-with-values"></a>값을 사용하여 해시 테이블 만들기

지금까지 이러한 예제를 위한 빈 해시 테이블을 만들었습니다. 생성 시 키와 값을 미리 채울 수 있습니다.

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a>조회 테이블로 사용

이 형식의 해시 테이블이 제공하는 진정한 가치는 조회 테이블로 사용할 수 있다는 점입니다. 다음은 간단한 예제입니다.

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

이 예제에서는 `$env` 변수의 환경을 지정하며 그러면 변수가 올바른 서버를 선택합니다. 이런 선택에는 `switch($env){...}`를 사용할 수 있지만 해시 테이블도 좋은 옵션입니다.

나중에 사용하기 위해 조회 테이블을 동적으로 작성할 때는 더욱 효과적입니다. 따라서 무언가를 교차 참조해야 할 때는 이 방법을 고려해봐야 합니다. PowerShell이 `Where-Object`를 이용한 파이프에서의 필터링에 부적합했다며 이 방법을 더 자주 활용했을 것입니다. 성능이 중요한 상황이라면 이 접근 방식을 고려해 봐야 합니다.

속도가 더 빠르지는 않지만 [성능이 중요하다면 테스트하라][]라는 규칙을 지킬 수 있습니다.

#### <a name="multiselection"></a>다중 선택

일반적으로 해시 테이블은 키 하나를 제공하여 값 하나를 얻는 키/값 쌍으로 간주됩니다. PowerShell을 사용하면 여러 값을 가져오는 키 배열을 제공할 수 있습니다.

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

이 예제에서 위에서 설명한 것과 같은 조회 해시 테이블을 사용하고 세 가지 배열 스타일을 제공하여 일치 항목을 가져옵니다. 대부분의 사람들이 모르는 PowerShell의 숨겨진 보석 같은 기능입니다.

## <a name="iterating-hashtables"></a>해시 테이블 반복

해시 테이블은 키/값 쌍의 컬렉션이므로 배열이나 항목의 일반 목록과는 다른 방식으로 반복됩니다.

가장 먼저 주목해야 할 점은 해시 테이블을 파이프하면 파이프는 해시 테이블을 개체처럼 처리한다는 것입니다.

```powershell
PS> $ageList | Measure-Object
count : 1
```

`.count` 속성에서 속성에 포함된 값 수를 알려준다고 해도 마찬가지입니다.

```powershell
PS> $ageList.count
2
```

값만 필요하다면 `.values` 속성을 사용 하여 이 문제를 해결할 수 있습니다.

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

키를 열거하고 이러한 키를 사용하여 값에 액세스하는 방법이 더 효과적일 때도 잦습니다.

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

다음은 `foreach(){...}` 루프를 이용하는 동일한 예제입니다.

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

해시 테이블에서 각 키를 탐색한 다음 이 키를 사용하여 값에 액세스합니다. 해시 테이블을 컬렉션으로 사용할 때 자주 쓰는 패턴입니다.

### <a name="getenumerator"></a>GetEnumerator()

이제 `GetEnumerator()`를 이용해 해시 테이블을 반복합니다.

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

열거자는 각 키/값 쌍을 하나씩 제공합니다. 이 사용 사례에 맞게 특별 제작한 열거자입니다. 이 사실을 알려준 [Mark Kraus](https://get-PowerShellblog.blogspot.com)에게 감사의 말을 전합니다.

### <a name="badenumeration"></a>BadEnumeration

열거 중인 해시 테이블을 수정할 수 없다는 점을 명심해야 합니다. 기본 `$environments` 예제부터 사용했다면 다음과 같습니다.

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

또한 모든 키를 같은 서버 값으로 설정하면 실패하게 됩니다.

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

겉보기에는 아무 문제 없어 보이더라도 결국에는 실패하게 됩니다.

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

이런 상황에서 중요한 점은 열거를 수행하기 전에 키를 복제하는 것입니다.

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a>해시 테이블은 속성의 컬렉션입니다

지금까지 해시 테이블에 배치한 개체의 형식은 모두 동일한 개체 형식이었습니다. 모든 예제에서 나이를 사용했고 키는 개인의 이름이었습니다. 컬렉션의 각 개체에 이름이 있을 때 이를 확인하는 탁월한 방법입니다. PowerShell에서 해시 테이블을 사용하는 또 다른 일반적인 방법은 키가 속성의 이름인 속성 컬렉션을 보유하는 것입니다. 다음 예제를 통해 자세히 살펴보겠습니다.

### <a name="property-based-access"></a>속성 기반 액세스

속성 기반 액세스를 사용하면 해시 테이블의 작동 방식과 PowerShell에서의 사용 방법이 변경됩니다. 다음은 위에서처럼 속성을 키로 취급하는 일반적인 예제입니다.

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

위의 예제에서처럼 이번 예제에서도 해시 테이블에 없는 키는 추가합니다. 키를 정의하는 방법과 값에 따라 이 방법은 조금 이상할 수도 있고 완벽하게 어울릴 수도 있습니다. 나이 목록 예제는 이 지점까지는 완벽하게 작동합니다. 다음 단계로 진행하려면 새로운 예제를 이용해야 합니다.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

그리고 다음과 같은 `$person`에 특성을 추가하고 액세스할 수 있습니다.

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

이 해시 테이블이 갑자기 개체처럼 보이고 개체처럼 작동할 것입니다. 하지만 엄연히 항목 모음이므로 위의 모든 예제는 여전히 적용됩니다. 우리는 다른 관점에서 살펴보았을 뿐입니다.

### <a name="checking-for-keys-and-values"></a>키 및 값 확인

대부분의 경우 다음과 같은 항목을 사용하여 값을 테스트할 수 있습니다.

```powershell
if( $person.age ){...}
```

단순하지만 제게는 수많은 버그의 원인이었는데, 논리에서 중요한 세부 사항 하나를 간과했기 때문입니다. 처음에는 키가 존재했는지 테스트하는 용도로 사용했습니다. 값이 `$false` 또는 0이라면 이 문은 예상과는 달리 `$false`를 반환합니다.

```powershell
if( $person.age -ne $null ){...}
```

이것은 0 값 관련 문제는 해결하지만 $null 대 존재하지 않는 키 관련 문제는 해결하지 못합니다. 대부분의 경우에는 이를 구분하지 않아도 되지만 구분해야 할 때는 특정 함수를 사용할 수 있습니다.

```powershell
if( $person.ContainsKey('age') ){...}
```

또한 값을 테스트하고 싶지만 키를 모르거나 전체 컬렉션을 반복하고 싶지 않다면 `ContainsValue()`를 이용하면 됩니다.

### <a name="removing-and-clearing-keys"></a>키 제거 및 지우기

`.Remove()` 함수를 사용하여 키를 제거할 수 있습니다.

```powershell
$person.remove('age')
```

키에 `$null` 값을 할당하면 `$null` 값이 있는 키만 남습니다.

해시 테이블을 지우는 일반적인 방법은 빈 해시 테이블로 초기화하는 것입니다.

```powershell
$person = @{}
```

이 작업을 수행하는 동안 `clear()` 함수를 대신 사용해 보세요.

```powershell
$person.clear()
```

함수를 사용하면 자체 문서화 코드를 만들고 코드의 의도가 대단히 명확하게 드러나는 인스턴스 예시입니다.

## <a name="all-the-fun-stuff"></a>흥미로운 요소

### <a name="ordered-hashtables"></a>순서 지정된 해시 테이블

기본적으로 해시 테이블은 순서가 지정되지(또는 정렬되지) 않습니다. 기존 환경에서는 항상 키를 사용하여 값에 액세스할 때는 순서가 중요하지 않습니다. 속성을 정의한 순서대로 유지하고 싶을 때가 있습니다. 다행히 `ordered` 키워드를 사용하면 이 작업을 할 수 있습니다.

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

이제 키와 값을 열거할 때 이 순서대로 열거됩니다.

### <a name="inline-hashtables"></a>인라인 해시 테이블

해시 테이블을 한 줄에 정의할 때는 세미콜론을 이용해 키/값 쌍을 구분할 수 있습니다.

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

파이프에서 만들 때는 특히 더 유용합니다.

### <a name="custom-expressions-in-common-pipeline-commands"></a>공통 파이프라인 명령에서의 사용자 지정 식

해시 테이블을 이용한 사용자 지정 또는 계산된 속성 생성을 지원하는 몇 가지 cmdlet이 있습니다. `Select-Object` 및 `Format-Table`과 함께 자주 사용합니다. 해시 테이블에는 완전히 펼치면 이런 식으로 보이는 특수 구문이 있습니다.

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

`name`은 cmdlet이 해당 열에 지정하는 레이블입니다. `expression`은 `$_`가 파이프 상의 개체 값을 때 실행되는 스크립트 블록입니다. 다음은 실제로 작동하는 스크립트입니다.

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

변수에 배치했지만 인라인으로 쉽게 정의할 수 있으며 정의 중에 `name`을 `n`으로, `expression`을 `e`로 줄일 수 있습니다.

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

개인적으로 명령이 길어지는 것을 좋아하지 않으며, 제가 관여하지 않는 일부 잘못된 동작을 승격하곤 합니다. 스크립트에서 이 방법을 사용하는 대신 원하는 필드와 속성을 모두 사용하여 새 해시 테이블이나 `pscustomobject`를 만드는 방법을 선호합니다. 하지만 이 작업은 수행하는 코드는 아주 많으니 이 방법을 알려드리고 싶었습니다. `pscustomobject` 생성 방법은 나중에 말씀드리겠습니다.

### <a name="custom-sort-expression"></a>사용자 지정 정렬 식

정렬하려는 데이터가 개체에 있다면 컬렉션을 쉽게 정렬할 수 있습니다. 개체에 데이터를 추가하면 컬렉션을 정렬하거나 `Sort-Object`에 대한 사용자 지정 식을 만들 수 있습니다.

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

이 예제에서는 사용자 목록을 가져오고 사용자 지정 cmdlet을 사용하여 정렬에 관한 추가 정보만 가져옵니다.

#### <a name="sort-a-list-of-hashtables"></a>해시 테이블 목록 정렬

정렬하려는 해시 테이블 목록이 있다면 `Sort-Object`에서는 키를 속성으로 처리하지 않음을 알 수 있습니다. 사용자 지정 정렬 식을 사용하면 이 문제를 해결할 수 있습니다.

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a>cmdlet에서 해시 테이블 스플래팅

이것은 많은 사람들이 빨리 알아차리지 못하는, 해시 테이블에서 가장 좋아하는 점입니다.
이 작업은 모든 속성을 한 줄에 있는 cmdlet에 제공하는 대신 먼저 해시 테이블에 넣습니다. 그러면 특수한 방법을 이용해 해시 테이블을 함수에 제공할 수 있습니다.
다음은 DHCP 범위를 일반적인 방법으로 만드는 예제입니다.

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

[스플래팅][]을 사용하지 않으면 모든 요소를 한 줄에 정의해야 합니다. 이 기능은 화면 밖으로 스크롤하거나 원하는 위치에서 줄을 바꿉니다. 이제 이것을 스플래팅을 사용하는 명령과 비교해보겠습니다.

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

`$` 대신 `@` 부호를 사용하면 스플랫 작업이 호출됩니다.

이 예제를 얼마나 쉽게 읽을 수 있는지 잠시 확인해 보세요. 동일한 값을 가진 완전히 동일한 명령입니다. 두 번째 명령이 더 이해하기 쉽고 향후 유지 관리도 쉽습니다.

명령이 너무 길어지면 언제든 스플래팅을 사용합니다. 정의가 너무 길어 창을 오른쪽으로 스크롤해야 합니다. 함수에 속성 3개가 적중한다면 대부분의 경우 스플래팅한 해시 테이블을 이용해 함수를 다시 작성합니다.

### <a name="splatting-for-optional-parameters"></a>선택적 매개 변수 스플래팅

스플래팅을 사용하는 가장 일반적인 방법은 스크립트의 다른 부분에서 제공하는 선택적 매개 변수를 처리하는 것입니다. 선택적 `$Credential` 인수가 있는 `Get-CIMInstance` 호출을 래핑하는 함수가 있다고 합시다.

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

먼저 일반 매개 변수를 사용하여 해시 테이블을 만듭니다. 그런 다음 `$Credential`이 존재한다면 이를 추가합니다.
여기서는 스플래팅을 사용하고 있으니 코드에서 `Get-CIMInstance`를 한 번만 호출하면 됩니다. 이 디자인 패턴은 대단히 깔끔하며 많은 선택적 매개 변수를 쉽게 처리할 수 있습니다.

불공평하지 않도록 매개 변수에 `$null` 값을 허용하는 명령을 작성하셔도 됩니다. 호출하는 다른 명령을 제어할 수 없을 때도 있습니다.

### <a name="multiple-splats"></a>여러 스플랫

여러 해시 테이블을 동일한 cmdlet으로 스플랫할 수 있습니다. 처음 스플래팅 예제를 다시 확인하겠습니다.

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

많은 명령에 전달하는 공통 매개 변수 집합이 있을 때 이 메서드를 사용합니다.

### <a name="splatting-for-clean-code"></a>깔끔한 코드의 스플래팅

코드를 더 깔끔하게 만들 수 있다면 단일 매개 변수로 스플래팅을 수행해도 됩니다.

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a>실행 파일 스플래팅

스플래팅은 `/param:value` 구문을 사용하는 일부 실행 파일에도 적용됩니다. 예를 들어 `Robocopy.exe`에는 이와 비슷한 몇 가지 매개 변수가 있습니다.

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

모든 매개 변수가 유용한지는 모르겠지만 흥미로운 요소이기는 합니다.

## <a name="adding-hashtables"></a>해시 테이블 추가

해시 테이블은 더하기 연산자를 이용하여 두 해시 테이블을 결합합니다.

```powershell
$person += @{Zip = '78701'}
```

두 해시 테이블이 키를 공유하지 않을 때만 가능합니다.

## <a name="nested-hashtables"></a>중첩된 해시 테이블

해시 테이블 내에서 다른 해시 테이블을 값으로 사용할 수 있습니다.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

먼저 키 두 개가 있는 기본 해시 테이블을 사용했습니다. 빈 해시 테이블이 있는 `location`이라는 키를 추가했습니다. 그런 다음 이 `location` 해시 테이블에 마지막 항목 두 개를 추가했습니다. 이상의 작업을 인라인으로 할 수도 있습니다.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

위에서 확인한 것과 동일한 해시 테이블을 만들며 속성에도 동일한 방식으로 액세스할 수 있습니다.

```powershell
$person.location.city
Austin
```

개체의 구조체에 접근하는 방법은 여러 가지가 있습니다. 다음은 중첩된 해시 테이블을 확인하는 두 번째 방법입니다.

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

해시 테이블을 개체 컬렉션으로 사용하는 방식과 속성 컬렉션으로 사용하는 방식을 결합하는 것입니다. 원하는 방법을 사용하여 중첩하더라도 값에 쉽게 액세스할 수 있습니다.

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

속성처럼 처리할 때는 점 속성을 사용하는 편입니다. 이것은 코드에서 정적으로 정의하는 일반적인 항목으로, 생각나는 대로 적은 것입니다. 목록을 탐색하거나 프로그래밍 방식으로 키에 액세스해야 한다면 대괄호를 사용하여 키 이름을 제공합니다.

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

해시 테이블을 중첩하는 기능은 뛰어난 유연과 많은 옵션을 제공합니다.

### <a name="looking-at-nested-hashtables"></a>중첩된 해시 테이블 확인

해시 테이블 중첩을 시작하면 콘솔에서 이를 쉽게 확인할 방법이 필요하게 됩니다. 마지막 해시 테이블을 사용하면 다음과 비슷한 출력을 얻게 되며 이 출력은 아래쪽으로만 진행됩니다.

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

이러한 요소를 확인할 때 사용하는 go to 명령은 `ConvertTo-JSON`입니다. 아주 깔끔한 데다 JSON을 특히 자주 사용하기 때문입니다.

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

JSON을 모르는 분도 원하는 항목을 볼 수 있습니다. 이런 류의 구조화된 데이터를 위한 `Format-Custom` 명령도 있지만 저는 여전히 JSON 보기를 선호합니다.

## <a name="creating-objects"></a>개체 만들기

개체만 필요하며 해시 테이블을 사용하여 속성을 보유하는 것만으로는 작업을 완료할 수 없을 때도 있습니다. 대부분의 경우 사람들은 키를 열 이름으로 표시하고 싶어 합니다. `pscustomobject`를 사용하면 이 작업을 쉽게 수행할 수 있습니다.

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

처음에 이것을 `pscustomobject`로 만들지 않았다 하더라도 필요하다면 언제든 캐스트할 수 있습니다.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

이 문서 다음에 읽게 될 [pscustomobject][]에 자세한 내용을 기록해두었습니다. 이 문서는 여기서 배운 많은 내용을 바탕으로 작성되었습니다.

## <a name="reading-and-writing-hashtables-to-file"></a>해시 테이블을 읽고 파일에 쓰기

### <a name="saving-to-csv"></a>CSV에 저장

해시 테이블을 가져와 CSV에 저장하는 작업은 위에서 언급한 문제이기도 합니다. 해시 테이블을 `pscustomobject`로 변환하면 CSV에 올바르게 저장됩니다. `pscustomobject`로 시작하면 열 순서가 유지되기 때문에 도움이 됩니다. 그러나 필요하다면 `pscustomobject`를 인라인에 캐스팅할 수 있습니다.

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

[pscustomobject][] 이용에 관한 제 문서에서는 이 주제도 다루고 있습니다.

### <a name="saving-a-nested-hashtable-to-file"></a>중첩된 해시 테이블을 파일에 저장

중첩된 해시 테이블을 파일에 저장한 다음 다시 읽어야 한다면, JSON cmdlet을 사용하여 이 작업을 수행합니다.

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

이 방법에는 두 가지 중요한 점이 있습니다. 첫 번째는 JSON은 여러 줄로 작성되므로 `-Raw` 옵션을 사용하여 다시 단일 문자열로 읽어야 한다는 점입니다. 두 번째는 가져온 개체는 더 이상 `[hashtable]`이 아니라는 점입니다. 가져온 개체는 `[pscustomobject]`가 되며 이를 예상하지 못하면 문제가 발생할 수 있습니다.

많이 중첩된 해시 테이블을 살펴봅니다. 많이 중첩된 해시 테이블을 JSON으로 변환하면 원하는 결과를 얻지 못할 수 있습니다.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

**Depth** 매개 변수를 사용하여 중첩된 모든 해시 테이블을 확장하도록 합니다.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

가져올 때 이것이 `[hashtable]`이어야 한다면 `Export-CliXml`과 `Import-CliXml` 명령을 사용해야 합니다.

### <a name="converting-json-to-hashtable"></a>JSON을 해시 테이블로 변환

JSON을 `[hashtable]`로 변환해야 한다면 제가 아는 한 가지 방법은 .NET에서 [JavaScriptSerializer][]를 사용하는 것입니다.

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

PowerShell v6부터 JSON 지원에서는 NewtonSoft JSON.NET가 사용되고 해시 테이블 지원이 추가됩니다.

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

PowerShell 6.2에서 **Depth** 매개 변수가 `ConvertFrom-Json`에 추가되었습니다. 기본 **Depth** 는 1024입니다.

### <a name="reading-directly-from-a-file"></a>파일에서 직접 읽기

PowerShell 구문을 사용하는 해시 테이블을 있는 파일을 사용한다면 파일에서 바로 가져오는 방법이 있습니다.

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

이 방법은 파일 콘텐츠를 `scriptblock`으로 가져온 다음 다른 PowerShell 명령이 없는 지 확인한 후에 실행합니다.

그러고 보니, 모듈 매니페스트(psd1 파일)가 단순한 해시 테이블이라는 사실을 아셨나요?

## <a name="keys-can-be-any-object"></a>키는 모든 개체가 될 수 있음

대부분의 경우 키는 단순히 문자열입니다. 따라서 어느 부분이든 따옴표를 붙이면 키로 만들 수 있습니다.

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

여러분이 상상하지도 못했던 놀라운 일을 실현할 수 있습니다.

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

하지만 할 수 있다고 해서 반드시 해야 하는 것은 아닙니다. 마지막 항목은 일어나기를 기다리는 버그처럼 보이며 코드를 읽는 사람이라면 누구나 오해하게 될 것입니다.

엄밀히 말하면 키는 문자열이 아니어도 되지만 사람들은 문자열만 사용했다고 생각하곤 합니다. 그러나 인덱싱은 복잡한 키에서는 제대로 작동하지 않습니다.

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

키를 사용하여 해시 테이블의 값에 액세스하는 것은 항상 작동하지 않습니다. 예를 들면 다음과 같습니다.

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

키가 배열인 경우 멤버 액세스(`.`) 표기법으로 사용할 수 있도록 `$key` 변수를 하위 식으로 래핑해야 합니다. 또는 배열 인덱스(`[]`) 표기법을 사용할 수 있습니다.

## <a name="use-in-automatic-variables"></a>자동 변수에서 사용

### <a name="psboundparameters"></a>$PSBoundParameters

[$PSBoundParameters][]는 함수의 컨텍스트 내에만 존재하는 자동 변수입니다.
함수를 호출한 모든 매개 변수를 포함합니다. 해시 테이블은 아니지만 해시 테이블처럼 처리해도 될 정도로 비슷합니다.

키 제거 및 다른 함수에 스플래팅 같은 작업도 마찬가지입니다. 프록시 함수를 작성한다면 이 내용을 더 자세히 살펴보세요.

자세한 내용은 [about_Automatic_Variables][]를 참조하시기 바랍니다.

### <a name="psboundparameters-gotcha"></a>PSBoundParameters 알려진 문제

이것은 매개 변수로 전달되는 값만 포함한다는 사실을 명심해야 합니다. 기본값이 있지만 호출자가 전달하지 않은 매개 변수를 이용한다면, `$PSBoundParameters`에는 이러한 값이 포함되지 않습니다. 자주 간과되는 사실입니다.

### <a name="psdefaultparametervalues"></a>$PSDefaultParameterValues

이 자동 변수를 사용하면 cmdlet을 변경하지 않고도 모든 cmdlet에 기본값을 할당할 수 있습니다.
이 예제를 살펴보세요.

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

`UTF8`을 `Out-File -Encoding` 매개 변수의 기본값으로 설정하는 `$PSDefaultParameterValues` 해시 테이블에 항목을 추가합니다. 세션별로 추가되므로 `$profile`에 배치해야 합니다.

주로 자주 입력하는 값을 미리 할당하는 용도로 이 기능을 사용합니다.

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

와일드 카드를 허용하기 때문에 값을 대량으로 설정할 수도 있습니다. 다음은 대표적인 사용 방법입니다.

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

자세한 내용을 알고 싶다면 [Michael Sorens][]가 작성한 이 훌륭한 [자동 기본값][] 관련 문서를 참조하세요.

## <a name="regex-matches"></a>정규식 $Matches

`-match` 연산자를 사용하면 `$matches`라는 자동 변수가 일치 항목의 결과와 함께 생성됩니다. 정규식에 하위 식이 있다면 하위 항목도 함께 나열됩니다.

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a>명명된 일치 항목

대부분의 사람은 모르지만 제가 제일 좋아하는 기능에 속합니다. 명명된 정규식 일치를 사용하면 일치 항목의 이름을 기준으로 일치 항목에 액세스할 수 있습니다.

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

위의 예제에서는 `(?<Name>.*)`이 명명된 하위 식입니다. 이 값은 `$Matches.Name` 속성에 배치됩니다.

## <a name="group-object--ashashtable"></a>Group-Object -AsHashtable

`Group-Object`의 잘 알려지지 않은 기능 중 하나는 일부 데이터 집합을 해시 테이블로 전환하는 것입니다.

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

이렇게 하면 각 행을 해시 테이블에 추가하고 지정 된 속성을 키로 사용하여 각 행에 액세스합니다.

## <a name="copying-hashtables"></a>해시 테이블 복사

한 가지 명심해야 할 점은 해시 테이블은 개체라는 점입니다. 그리고 각 변수는 개체에 대한 참조일 뿐입니다. 따라서 해시 테이블의 유효한 복사본을 만들려면 더 많은 작업을 수행해야 합니다.

### <a name="assigning-reference-types"></a>참조 형식 할당

해시 테이블이 하나 있으며 두 번째 변수에 이를 할당하면, 두 변수는 같은 해시 테이블을 가리킵니다.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

한쪽의 값을 변경하면 다른 쪽의 값도 변경되기 때문에 두 항목이 같음을 더욱 확실하게 알 수 있습니다. 다른 함수에 해시 테이블을 전달할 때도 마찬가지입니다. 함수가 해시 테이블을 변경한다면 원본도 변경됩니다.

### <a name="shallow-copies-single-level"></a>단순 복사본, 단일 수준

위의 예제에서처럼 간단한 해시 테이블이 있다면 `.Clone()`를 사용하여 단순 복사본을 만들 수 있습니다.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

이렇게 하면 한쪽 해시 테이블의 기본 테이블을 변경해도 다른 해시 테이블은 영향을 받지 않습니다.

### <a name="shallow-copies-nested"></a>단순 복사본, 중첩

단순 복사본이라고 하는 이유는 기본 수준 속성만 복사하기 때문입니다. 속성 중 하나가 참조 형식(예: 다른 해시 테이블)이어도 중첩된 개체는 계속해서 서로를 가리킵니다.

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

따라서 해시 테이블을 복제했더라도 `person`에 대한 참조는 복제되지 않음을 알 수 있습니다. 첫 번째 해시 테이블에 연결되지 않은 두 번째 해시 테이블을 얻으려면 전체 복사본을 만들어야 합니다.

### <a name="deep-copies"></a>전체 복사본

이 문서를 작성하는 지금 해시 테이블의 전체 복사본을 만드는(그리고 이것을 해시 테이블로 유지하는) 방법보다 좋은 방법을 알지 못합니다. 그런 방법은 다른 누군가가 작성할 것입니다.
이 방법을 이용하면 작업을 빠르게 수행하는 있습니다.

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

다른 참조 형식이나 배열을 처리하지는 않지만 좋은 출발점이 될 것입니다.

## <a name="anything-else"></a>다른 내용을 알고 싶으신가요?

지금까지 많은 내용을 빠르게 살펴보았습니다. 이 문서를 읽을 때마다 새로운 내용을 배우거나 기존 지식이 깊어지길 바랍니다. 이 기능의 모든 특징을 살펴보았기 때문에 지금 당장은 적용되지 않는 측면이 있을 것입니다. 지극히 정상적인 현상이며 PowerShell을 많이 이용한다면 필연적인 일이기도 합니다.

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[해시 테이블]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[배열]: /powershell/module/microsoft.powershell.core/about/about_arrays
[성능이 중요하다면 테스트하라]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[스플래팅]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[자동 기본값]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
