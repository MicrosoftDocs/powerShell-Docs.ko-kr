---
description: 스위치를 사용 하 여 여러 문을 처리 하는 방법을 설명 합니다 `If` .
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 5ca12fe1d5052c1589c5dfecca8cf08cf68901e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599772"
---
# <a name="about-switch"></a>스위치 정보

## <a name="short-description"></a>간단한 설명
스위치를 사용 하 여 여러 문을 처리 하는 방법을 설명 합니다 `If` .

## <a name="long-description"></a>자세한 설명입니다.

스크립트나 함수에서 조건을 확인 하려면 `If` 문을 사용 합니다. `If`문은 변수의 값과 개체의 속성을 포함 하 여 다양 한 유형의 조건을 확인할 수 있습니다.

여러 조건을 확인 하려면 `Switch` 문을 사용 합니다. `Switch`문은 일련의 `If` 문과 동일 하지만 더 간단 합니다. `Switch`문은 각 조건과 선택적 동작을 나열 합니다. 조건이 가져오는 경우 작업이 수행 됩니다.

`Switch`문은 `$_` 및 자동 변수를 사용할 수 있습니다 `$switch` . 자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.

기본 `Switch` 문의 형식은 다음과 같습니다.

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

예를 들어 다음 `Switch` 문은 테스트 값 3을 각 조건과 비교 합니다. 테스트 값이 조건과 일치 하면 작업이 수행 됩니다.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

이 간단한 예제에서는 값 3과 일치 하는 경우에도 값이 목록의 각 조건과 비교 됩니다. 다음 `Switch` 문에는 값이 3 인 두 개의 조건이 있습니다. 기본적으로 모든 조건이 테스트 됨을 보여 줍니다.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

`Switch`일치 항목 뒤의 비교를 중지 하려면 문을 사용 합니다 `Break` . 문은 `Break` `Switch` 문을 종료 합니다.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

테스트 값이 배열과 같은 컬렉션인 경우 컬렉션의 각 항목이 표시 되는 순서 대로 평가 됩니다. 다음 예에서는 4와 2를 계산 합니다.

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

`Break`다음 예제와 같이 모든 문은 컬렉션에 적용 되 고 각 값에는 적용 되지 않습니다. `Switch`문은 `Break` 값 4 조건의 문으로 종료 됩니다.

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a>Syntax

전체 `Switch` 문 구문은 다음과 같습니다.

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

or

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

매개 변수를 사용 하지 않는 경우는 `Switch` **정확한** 매개 변수를 사용 하는 것과 동일 하 게 동작 합니다. 값에 대해 대/소문자를 구분 하지 않는 일치를 수행 합니다. 값이 컬렉션인 경우 각 요소는 표시 된 순서 대로 평가 됩니다.

`Switch`문에는 하나 이상의 condition 문이 포함 되어야 합니다.

`Default`값이 조건과 일치 하지 않는 경우 절이 트리거됩니다. `Else`문의 절과 동일 `If` 합니다. `Default`각 문에는 하나의 절만 사용할 수 `Switch` 있습니다.

`Switch` 에는 다음 매개 변수가 있습니다.

- **와일드 카드** -조건이 와일드 카드 문자열 임을 나타냅니다. Match 절이 문자열이 아니면 매개 변수는 무시 됩니다. 비교는 대/소문자를 구분합니다.
- **Exact** -match 절 (문자열 인 경우)이 정확 하 게 일치 해야 함을 나타냅니다. Match 절이 문자열이 아니면이 매개 변수는 무시 됩니다. 비교는 대/소문자를 구분합니다.
- **CaseSensitive** -대/소문자를 구분 하는 일치를 수행 합니다. Match 절이 문자열이 아니면이 매개 변수는 무시 됩니다.
- **파일**-값 문이 아닌 파일에서 입력을 가져옵니다. 여러 **파일** 매개 변수가 포함 된 경우에는 마지막 매개 변수만 사용 됩니다. 파일의 각 줄은 문에 의해 읽고 평가 됩니다 `Switch` . 비교는 대/소문자를 구분합니다.
- **Regex** -조건에 대 한 값의 정규식 일치를 수행 합니다. Match 절이 문자열이 아니면이 매개 변수는 무시 됩니다.
  비교는 대/소문자를 구분합니다. `$matches`자동 변수는 일치 하는 문 블록 내에서 사용할 수 있습니다.

> [!NOTE]
> **Regex** 및 **와일드 카드** 와 같이 충돌 하는 값을 지정 하는 경우 마지막으로 지정 된 매개 변수가 우선적으로 적용 되며 충돌 하는 모든 매개 변수는 무시 됩니다. 여러 매개 변수 인스턴스도 사용할 수 있습니다. 그러나 마지막으로 사용한 매개 변수만 유효 합니다.

이 예제에서 문자열이 나 숫자 데이터가 아닌 개체는에 전달 됩니다 `Switch` . 는 `Switch` 개체에 대해 문자열 강제 변환을 수행 하 고 결과를 평가 합니다.

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

이 예제에서는 일치 하는 대/소문자가 없으므로 출력이 없습니다.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

절을 추가 하 여 `Default` 다른 조건이 충족 되지 않을 때 작업을 수행할 수 있습니다.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

Case와 일치 하는 단어 "14"의 경우 `-Wildcard` 또는 매개 변수를 사용 해야 합니다 `-Regex` .

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

다음 예제에서는 매개 변수를 사용 합니다 `-Regex` .

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

Switch 문 조건은 다음 중 하나일 수 있습니다.

- 값이 입력 값과 비교 되는 식입니다.
- 조건을 충족 하는 경우를 반환 해야 하는 스크립트 블록입니다 `$true` .

`$_`자동 변수는 switch 문에 전달 되는 값을 포함 하며 조건문의 범위 내에서 평가 하 고 사용할 수 있습니다.

각 조건에 대 한 작업은 다른 조건의 작업과는 독립적입니다.

다음 예에서는 문 조건으로 스크립트 블록을 사용 하는 방법을 보여 줍니다 `Switch` .

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

값이 여러 조건과 일치 하면 각 조건에 대 한 동작이 실행 됩니다. 이 동작을 변경 하려면 `Break` 또는 키워드를 사용 `Continue` 합니다.

`Break`키워드는 처리를 중지 하 고 `Switch` 문을 종료 합니다.

`Continue`키워드는 현재 값의 처리를 중지 하지만 후속 값의 처리를 계속 합니다.

다음 예제에서는 숫자 배열을 처리 하 고 홀수 또는 짝수 인지 여부를 표시 합니다. 음수는 키워드를 사용 하 여 건너뜁니다 `Continue` . 숫자가 아닌 값이 발견 되 면 실행이 키워드를 사용 하 여 종료 됩니다 `Break` .

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a>참고 항목

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)
