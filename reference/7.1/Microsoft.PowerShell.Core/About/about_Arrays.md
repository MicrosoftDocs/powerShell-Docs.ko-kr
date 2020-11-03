---
description: 항목 컬렉션을 저장 하도록 디자인 된 데이터 구조인 배열에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_arrays
ms.openlocfilehash: 96e3798d4ff0a737421bb6211b809b192afa96f0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222953"
---
# <a name="about-arrays"></a>배열 정보

## <a name="short-description"></a>간단한 설명
항목 컬렉션을 저장 하도록 디자인 된 데이터 구조인 배열에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

배열은 항목 컬렉션을 저장 하도록 디자인 된 데이터 구조입니다.
항목은 형식이 나 형식이 다를 수 있습니다.

Windows PowerShell 3.0부터 0 개 또는 한 개의 개체 컬렉션에 배열의 속성이 있습니다.

## <a name="creating-and-initializing-an-array"></a>배열 만들기 및 초기화

배열을 만들고 초기화 하려면 변수에 여러 값을 할당 합니다. 배열에 저장 된 값은 쉼표로 구분 되며 대입 연산자 ()로 변수 이름과 구분 됩니다 `=` .

예를 `$A` 들어 7 개의 숫자 (int) 값 22, 5, 10, 8, 12, 9, 80를 포함 하는 라는 배열을 만들려면 다음을 입력 합니다.

```powershell
$A = 22,5,10,8,12,9,80
```

쉼표는 단일 항목 앞에 쉼표를 추가 하 여 단일 항목 배열을 초기화 하는 데 사용할 수도 있습니다.

예를 `$B` 들어 단일 값 7을 포함 하는 라는 단일 항목 배열을 만들려면 다음과 같이 입력 합니다.

```powershell
$B = ,7
```

범위 연산자 ()를 사용 하 여 배열을 만들고 초기화할 수도 있습니다 `..` .
다음 예에서는 값 5 ~ 8을 포함 하는 배열을 만듭니다.

```powershell
$C = 5..8
```

따라서에는 `$C` 5, 6, 7 및 8의 네 가지 값이 포함 됩니다.

데이터 형식을 지정 하지 않으면 PowerShell에서 각 배열을 개체 배열 ( **system.object []** )로 만듭니다. 배열의 데이터 형식을 확인 하려면 **GetType ()** 메서드를 사용 합니다. 예를 들어 배열의 데이터 형식을 확인 하려면 다음을 `$A` 입력 합니다.

```powershell
$A.GetType()
```

특정 형식의 값만 포함할 수 있는 강력한 형식의 배열을 만들려면 변수를 **문자열 []** , **long []** 또는 **int32 []** 와 같은 배열 형식으로 캐스팅 합니다. 배열을 캐스팅 하려면 변수 이름 앞에 대괄호로 묶은 배열 형식을 사용 합니다. 예를 `$ia` 들어 4 개의 정수 (1500, 2230, 3350 및 4000)가 포함 된 32 비트 정수 배열을 만들려면 다음을 입력 합니다.

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

따라서 `$ia` 배열에 정수만 포함 될 수 있습니다.

Microsoft .NET 프레임 워크에서 지원 되는 형식으로 캐스팅 된 배열을 만들 수 있습니다. 예를 들어 `Get-Process` 프로세스를 나타내기 위해 검색 하는 개체는 **System.web. 프로세스** 형식입니다. 프로세스 개체의 강력한 형식의 배열을 만들려면 다음 명령을 입력 합니다.

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a>배열 하위 식 연산자

배열 하위 식 연산자는 내부에 있는 문에서 배열을 만듭니다. 연산자 내의 문이 생성 하는 것과 관계 없이 연산자는 배열에이를 추가 합니다. 개체가 0 개 또는 1 개 있는 경우에도 마찬가지입니다.

배열 연산자의 구문은 다음과 같습니다.

```syntax
@( ... )
```

배열 연산자를 사용 하 여 0 개 또는 한 개의 개체로 이루어진 배열을 만들 수 있습니다. 다음은 그 예입니다. 

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

Array 연산자는 개체를 가져올 때 스크립트에 유용 하지만, 얻을 수 있는 개체의 수를 알 수 없습니다. 다음은 그 예입니다. 

```powershell
$p = @(Get-Process Notepad)
```

배열 하위 식 연산자에 대 한 자세한 내용은 [about_Operators](about_Operators.md)를 참조 하세요.

## <a name="accessing-and-using-array-elements"></a>배열 요소 액세스 및 사용

### <a name="reading-an-array"></a>배열 읽기

변수 이름을 사용 하 여 배열을 참조할 수 있습니다. 배열의 모든 요소를 표시 하려면 배열 이름을 입력 합니다. 예를 들어, `$a` 가 9까지 정수 0, 1, 2를 포함 하는 배열인 경우 다음을 입력 합니다.

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

0 위치에서 시작 하 여 인덱스를 사용 하 여 배열의 요소를 참조할 수 있습니다. 인덱스 번호를 대괄호로 묶습니다. 예를 들어 배열의 첫 번째 요소를 표시 하려면 `$a` 다음을 입력 합니다.

```powershell
$a[0]
```

```Output
0
```

배열의 세 번째 요소를 표시 하려면 `$a` 다음을 입력 합니다.

```powershell
$a[2]
```

```Output
2
```

인덱스에 대해 범위 연산자를 사용 하 여 배열의 일부를 검색할 수 있습니다. 예를 들어 배열의 두 번째 요소와 다섯 번째 요소를 검색 하려면 다음을 입력 합니다.

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

배열의 끝부터 음수를 계산 합니다. 예를 들어 "-1"은 배열의 마지막 요소를 참조 합니다. 배열의 마지막 세 요소를 표시 하려면 인덱스 오름차순에서 다음을 입력 합니다.

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

음수 인덱스를 내림차순으로 입력 하면 출력이 변경 됩니다.

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

그러나이 표기법을 사용할 때는 주의 해야 합니다. 표기법은 끝 경계에서 배열의 시작 부분으로 순환 됩니다.

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

또한 일반적인 실수 중 하나는 `$a[0..-2]` 마지막 요소를 제외 하 고 배열의 모든 요소를 참조 하는 것입니다. 배열의 첫 번째, 마지막 및 초에서 마지막 요소를 참조 합니다.

더하기 연산자 ()를 사용 `+` 하 여 범위를 배열의 요소 목록과 결합할 수 있습니다. 예를 들어 인덱스 위치 0, 2 및 4-6에 요소를 표시 하려면 다음을 입력 합니다.

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

또한 여러 범위 및 개별 요소를 나열 하려면 더하기 연산자를 사용할 수 있습니다. 예를 들어 0 ~ 2, 4 ~ 6 개의 요소를 나열 하 고 여덟 번째 위치에 요소를 나열 하려면 다음을 입력 합니다.

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a>배열 요소 반복

ForEach, For, While 루프와 같은 루프 구문을 사용 하 여 배열의 요소를 참조할 수도 있습니다. 예를 들어 ForEach 루프를 사용 하 여 배열의 요소를 표시 하려면 `$a` 다음을 입력 합니다.

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

Foreach 루프는 배열을 반복 하 고 배열의 끝에 도달할 때까지 배열의 각 값을 반환 합니다.

For 루프는 배열의 요소를 검사 하는 동안 카운터를 증가 시키는 경우에 유용 합니다. 예를 들어 For 루프를 사용 하 여 배열의 다른 모든 값을 반환 하려면 다음을 입력 합니다.

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

While 루프를 사용 하 여 정의 된 조건이 더 이상 true가 될 때까지 배열의 요소를 표시할 수 있습니다. 예를 들어 배열 `$a` 인덱스가 4 보다 작은 동안 배열의 요소를 표시 하려면 다음을 입력 합니다.

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a>배열의 속성

### <a name="count-or-length-or-longlength"></a>개수 또는 길이 또는 고 길이

배열에 있는 항목 수를 확인 하려면 `Length` 속성 또는 해당 별칭을 사용 `Count` 합니다. `Longlength` 배열에 2147483647 개 이상의 요소가 포함 된 경우에 유용 합니다.

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a>순위

배열의 차원 수를 반환합니다. PowerShell의 대부분 배열에는 하나의 차원만 있습니다. 다차원 배열을 작성 한다고 생각 하는 경우에도 다음 예제와 같습니다.

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

[int]$r = $a.Rank
"`$a rank: $r"
```

```Output
$a rank: 1
```

다음 예제에서는 .Net Framework를 사용 하 여 진정한 다차원 배열을 만드는 방법을 보여 줍니다.

```powershell
[int[,]]$rank2 = [int[,]]::new(5,5)
$rank2.rank
```

```Output
2
```

## <a name="methods-of-arrays"></a>배열의 메서드

### <a name="clear"></a>지우기

모든 요소 값을 배열의 요소 형식 _기본값으로_ 설정 합니다.
Clear () 메서드는 배열의 크기를 다시 설정 하지 않습니다.

다음 예제에서는 `$a` 개체의 배열입니다.

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

이 예제에서 `$intA` 는 정수를 포함 하도록 명시적으로 형식화 됩니다.

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a>ForEach

를 사용 하 여 배열의 모든 요소를 반복 하 고 배열의 각 요소에 대해 지정 된 작업을 수행할 수 있습니다.

ForEach 메서드에는 서로 다른 작업을 수행 하는 여러 오버 로드가 있습니다.

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a>ForEach (scriptblock 식)

#### <a name="foreachscriptblock-expression-object-arguments"></a>ForEach (scriptblock 식, object [] arguments)

이 메서드는 PowerShell v4에서 추가 되었습니다.

> [!NOTE]
> 구문에서는 스크립트 블록을 사용 해야 합니다. Scriptblock이 유일한 매개 변수인 경우 괄호는 선택 사항입니다. 또한 메서드와 여는 괄호 또는 중괄호 사이에 공백이 있어서는 안 됩니다.

다음 예제에서는 foreach 메서드를 사용 하는 방법을 보여 줍니다. 이 경우 배열의 요소에 대 한 제곱 값을 생성 하는 것이 의도입니다.

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

`-ArgumentList`의 매개 변수와 마찬가지로 `ForEach-Object` `arguments` 매개 변수를 사용 하면 인수 배열을 허용 하도록 구성 된 스크립트 블록에 인수 배열을 전달할 수 있습니다.

**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about_Splatting.md#splatting-with-arrays)를 참조 하세요.

#### <a name="foreachtype-converttotype"></a>ForEach (convertToType 형식)

`ForEach`메서드를 사용 하 여 요소를 다른 형식으로 빠르게 캐스팅할 수 있습니다. 다음 예제에서는 문자열 날짜 목록을 형식으로 변환 하는 방법을 보여 줍니다 `[DateTime]` .

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a>ForEach (문자열 propertyName)

#### <a name="foreachstring-propertyname-object-newvalue"></a>ForEach (string propertyName, object [] newValue)

`ForEach`메서드를 사용 하 여 컬렉션의 모든 항목에 대 한 속성 값을 신속 하 게 검색 하거나 설정할 수도 있습니다.

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a>ForEach (string methodName)

#### <a name="foreachstring-methodname-object-arguments"></a>ForEach (string methodName, object [] arguments)

마지막으로 `ForEach` 메서드를 사용 하 여 컬렉션의 모든 항목에 대해 메서드를 실행할 수 있습니다.

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

`-ArgumentList`의 매개 변수와 마찬가지로 `ForEach-Object` `arguments` 매개 변수를 사용 하면 인수 배열을 허용 하도록 구성 된 스크립트 블록에 인수 배열을 전달할 수 있습니다.

> [!NOTE]
> Windows PowerShell 3.0에서 시작 하 여 컬렉션의 각 항목에 대 한 속성 검색 및 메서드 실행은 "스칼라 개체 및 컬렉션의 메서드"를 사용 하 여 수행할 수도 있습니다. 여기 [about_methods](about_methods.md)여기에 대해 자세히 알아볼 수 있습니다.

### <a name="where"></a>Where

배열의 요소를 필터링 하거나 선택할 수 있습니다. 스크립트는 0 (0), 빈 문자열 `$false` 또는 `$null` 다음에 표시 되는 요소에 대해 다음과 다른 것으로 계산 되어야 합니다. `Where`

메서드에 대 한 정의가 하나 있습니다 `Where` .

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> 구문에서는 스크립트 블록을 사용 해야 합니다. Scriptblock이 유일한 매개 변수인 경우 괄호는 선택 사항입니다. 또한 메서드와 여는 괄호 또는 중괄호 사이에 공백이 있어서는 안 됩니다.

는 `Expression` 필터링에 필요한 scriptblock 이며 `mode` 선택적 인수는 추가 선택 기능을 허용 하 고 `numberToReturn` 선택적 인수는 필터에서 반환 되는 항목 수를 제한 하는 기능을 허용 합니다.

에 허용 되는 값은 `mode` 다음과 같습니다.

- Default (0)-모든 항목 반환
- First (1)-첫 번째 항목 반환
- Last (2)-마지막 항목 반환
- 다음까지 건너뛰기 (3)-조건이 true가 될 때까지 항목을 건너뛰고 나머지 항목을 반환 합니다.
- Until (4)-조건이 true가 될 때까지 모든 항목 반환
- Split (5)-두 요소의 배열을 반환 합니다.
  - 첫 번째 요소는 일치 하는 항목을 포함 합니다.
  - 두 번째 요소는 나머지 항목을 포함 합니다.

다음 예제에서는 배열에서 홀수인 모든 숫자를 선택 하는 방법을 보여 줍니다.

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

이 예에서는 비어 있지 않은 문자열을 선택 하는 방법을 보여 줍니다.

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a>기본값

이 `Default` 모드는 scriptblock을 사용 하 여 항목을 필터링 `Expression` 합니다.

`numberToReturn`가 제공 되는 경우 반환할 최대 항목 수를 지정 합니다.

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> `Default`모드와 모드는 모두 `First` 첫 번째 ( `numberToReturn` ) 항목을 반환 하며, 서로 바꿔 사용할 수 있습니다.

#### <a name="last"></a>마지막

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a>다음까지 건너뛰기

`SkipUntil`모드는 개체가 스크립트 블록 식 필터를 전달할 때까지 컬렉션의 모든 개체를 건너뜁니다. 그런 다음 나머지 컬렉션 항목을 테스트 하지 않고 **모두** 반환 합니다. _하나의 전달 항목만 테스트 됩니다_.

즉, 반환 된 컬렉션에는 테스트 되지 않은 _전달_ 및 _전달_ 되지 않는 항목이 모두 포함 됩니다.

값을 인수로 전달 하 여 반환 되는 항목 수를 제한할 수 있습니다 `numberToReturn` .

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a>발생할

모드는 `Until` 모드를 반전 `SkipUntil` 합니다.  항목이 스크립트 블록 식을 전달할 때까지 컬렉션의 **모든** 항목을 반환 합니다. 항목이 scriptblock 식을 _전달_ 하면 `Where` 메서드가 항목 처리를 중지 합니다.

즉, 메서드에서 _전달 되지 않는_ 첫 번째 항목 집합을 받습니다 `Where` . 한 항목이 전달 된 _후_ 나머지는 테스트 되거나 반환 되지 않습니다.

값을 인수로 전달 하 여 반환 되는 항목 수를 제한할 수 있습니다 `numberToReturn` .

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> 및는 모두 `Until` `SkipUntil` 항목의 일괄 처리를 테스트 하지 않고 온-프레미스로 작동 합니다.
>
> `Until`첫 번째 패스 **앞** 에 있는 _pass_ 항목을 반환 합니다.
>
> `SkipUntil`첫 번째 전달 항목을 포함 하 여 첫 번째 _패스_ **이후의** 모든 항목을 반환 합니다.

#### <a name="split"></a>분할

`Split`모드는 컬렉션 항목을 두 개의 개별 컬렉션으로 분할 하거나 그룹화 합니다. Scriptblock 식을 전달 하는 것과 그렇지 않은 식입니다.

을 지정 하는 경우 `numberToReturn` 첫 번째 컬렉션에는 지정 된 값을 초과 하지 않고 _전달_ 하는 항목이 포함 됩니다.

식 필터를 **전달** 하는 개체를 포함 하 여 나머지 개체는 두 번째 컬렉션에서 반환 됩니다.

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a>배열의 멤버 가져오기

Length 속성 및 **SetValue** 메서드와 같이 배열의 속성 및 메서드를 가져오려면 Cmdlet의 **InputObject** 매개 변수를 사용 합니다 `Get-Member` .

배열을로 파이프 하면 `Get-Member` PowerShell에서 한 번에 하나씩 항목을 보내고, `Get-Member` 배열의 각 항목에 대 한 형식을 반환 합니다 (중복 요소 무시).

**InputObject** 매개 변수를 사용 하는 경우는 `Get-Member` 배열의 멤버를 반환 합니다.

예를 들어 다음 명령은 배열 변수의 멤버를 가져옵니다 `$a` .

```powershell
Get-Member -InputObject $a
```

Cmdlet으로 파이프 되는 값 앞에 쉼표 (,)를 입력 하 여 배열의 멤버를 가져올 수도 있습니다 `Get-Member` . 쉼표를 사용 하면 배열이 배열 배열의 두 번째 항목으로 설정 됩니다. PowerShell은 한 번에 하나씩 배열을 파이프 하 고 `Get-Member` 배열의 멤버를 반환 합니다. 다음 두 예제와 같습니다.

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a>배열 조작

배열의 요소를 변경 하 고, 배열에 요소를 추가 하 고, 두 배열의 값을 세 번째 배열로 결합할 수 있습니다.

배열의 특정 요소에 대 한 값을 변경 하려면 변경할 요소의 배열 이름과 인덱스를 지정한 다음 할당 연산자 ()를 사용 `=` 하 여 요소에 대 한 새 값을 지정 합니다. 예를 들어 배열의 두 번째 항목 `$a` (인덱스 위치 1) 값을 10으로 변경 하려면 다음을 입력 합니다.

```powershell
$a[1] = 10
```

배열의 **SetValue** 메서드를 사용 하 여 값을 변경할 수도 있습니다. 다음 예에서는 배열의 두 번째 값 (인덱스 위치 1) `$a` 을 500로 변경 합니다.

```powershell
$a.SetValue(500,1)
```

연산자를 사용 `+=` 하 여 요소를 배열에 추가할 수 있습니다. 다음 예제에서는 배열에 요소를 추가 하는 방법을 보여 줍니다 `$a` .

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> 연산자를 사용 하는 경우 `+=` PowerShell은 실제로 원래 배열의 값과 추가 된 값을 사용 하 여 새 배열을 만듭니다. 이로 인해 작업이 여러 번 반복 되거나 배열의 크기가 너무 큰 경우 성능 문제가 발생할 수 있습니다.

배열에서 요소를 삭제 하는 것은 쉽지 않지만 기존 배열의 선택한 요소만 포함 하는 새 배열을 만들 수 있습니다. 예를 들어 `$t` 인덱스 위치 2의 값을 제외 하 고 배열의 모든 요소가 포함 된 배열을 만들려면 `$a` 다음과 같이 입력 합니다.

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

두 배열을 단일 배열로 결합 하려면 더하기 연산자 ()를 사용 `+` 합니다. 다음 예제에서는 두 개의 배열을 만들고이를 결합 한 다음 결과 결합 된 배열을 표시 합니다.

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

결과적으로 배열에는 `$z` 1, 3, 5, 9가 포함 됩니다.

배열을 삭제 하려면 값을 `$null` 배열에 할당 합니다. 다음 명령은 변수에서 배열을 삭제 합니다 `$a` .

`$a = $null`

`Remove-Item`Cmdlet을 사용할 수도 있지만, 값을 할당 하는 `$null` 것은 특히 많은 배열의 경우 더 빠릅니다.

## <a name="arrays-of-zero-or-one"></a>0 또는 1의 배열

Windows PowerShell 3.0부터 0 개 또는 한 개의 개체 컬렉션에 Count 및 Length 속성이 있습니다. 또한 한 개체의 배열에 대 한 인덱스를 만들 수 있습니다. 이 기능을 사용 하면 컬렉션을 필요로 하는 명령이 두 개 미만의 항목 보다 작은 경우 발생 하는 스크립팅 오류를 방지할 수 있습니다.

다음 예에서는이 기능을 보여 줍니다.

### <a name="zero-objects"></a>0 개 개체

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a>개체 하나

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a>System.string 개체에 대 한 인덱싱 지원

PowerShell 6.1에는 배열과 유사한 **튜플** 개체의 인덱싱된 액세스에 대 한 지원이 추가 되었습니다.
다음은 그 예입니다. 

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

배열 및 다른 컬렉션 개체와 달리 **튜플** 개체는 파이프라인을 통해 전달 될 때 또는 개체의 배열을 지 원하는 매개 변수를 통해 전달 될 때 단일 개체로 처리 됩니다.

자세한 내용은 [system.object](/dotnet/api/system.tuple)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [about_assignment_operators](about_Assignment_Operators.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Operators](about_Operators.md)
- [about_For](about_For.md)
- [about_Foreach](about_Foreach.md)
- [about_While](about_While.md)

