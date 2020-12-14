---
description: PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_comparison_operators
ms.openlocfilehash: ba671ae51d458a2e0074a85d4de859795c20a3d5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97069906"
---
# <a name="about-comparison-operators"></a>비교 연산자 정보

## <a name="short-description"></a>간단한 설명
PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

비교 연산자를 사용 하 여 값을 비교 하 고 지정 된 패턴과 일치 하는 값을 찾는 조건을 지정할 수 있습니다. 비교 연산자를 사용 하려면 이러한 값을 구분 하는 연산자와 비교할 값을 지정 합니다.

PowerShell에는 다음과 같은 비교 연산자가 포함 되어 있습니다.

| 형식        | 연산자    | 설명                                 |
| ----------- | ------------ | --------------------------------------------|
| 같음    | -eq          | equals                                      |
|             | -ne          | 같지 않음                                  |
|             | -gt          | 보다 큼                                |
|             | -ge          | 크거나 같음                       |
|             | -lt          | 다음보다 작음                                   |
|             | -le          | 작거나 같음                          |
|             |              |                                             |
| Matching    | -like        | 문자열이 와일드 카드와 일치할 경우 true를 반환 합니다.   |
|             |              | pattern                                     |
|             | -notlike     | 문자열이 일치 하지 않으면 true를 반환 합니다.     |
|             |              | 와일드 카드 패턴                            |
|             | -match       | 문자열이 regex와 일치 하면 true를 반환 합니다.      |
|             |              | 되풀이 $matches에 일치 하는 문자열이 포함 되어 있습니다. |
|             | -notmatch    | 문자열이 일치 하지 않으면 true를 반환 합니다.     |
|             |              | regex 패턴; 일치 항목 포함 $matches   |
|             |              | 문자열                                     |
|             |              |                                             |
| Containment | -contains    | 참조 값이 포함 된 경우 true를 반환 합니다. |
|             |              | 컬렉션에서                             |
|             | -notcontains | 참조 값이이 아닌 경우 true를 반환 합니다.       |
|             |              | 컬렉션에 포함 되어 있습니다.                   |
|             | -in          | 에 포함 된 테스트 값이 true를 반환 합니다. |
|             |              | collection                                  |
|             | -notin       | 테스트 값이 포함 되지 않은 경우 true를 반환 합니다.  |
|             |              | 컬렉션에서                             |
|             |              |                                             |
| Replacement | -replace     | 문자열 패턴을 바꿉니다.                   |
|             |              |                                             |
| 형식        | -is          | 두 개체가 같을 경우 true를 반환 합니다.    |
|             |              | 형식                                        |
|             | -isnot       | 개체가 같지 않으면 true를 반환 합니다.|
|             |              | 형식                                        |

기본적으로 모든 비교 연산자는 대/소문자를 구분 하지 않습니다. 대/소문자를 구분 하는 비교 연산자를 만들려면 연산자 이름 앞에을 붙입니다 `c` . 예를 들어 대/소문자를 구분 하는 버전 `-eq` 은 `-ceq` 입니다. 대/소문자를 구분 하지 않도록 명시적으로 지정 하려면 연산자 앞에을 붙입니다 `i` . 예를 들어의 명시적 대/소문자를 구분 하지 않는 버전은 `-eq` `-ieq` 입니다.

연산자에 대 한 입력이 스칼라 값인 경우 비교 연산자는 부울 값을 반환 합니다. 입력이 값 컬렉션인 경우 비교 연산자는 일치 하는 값을 반환 합니다. 컬렉션에 일치 하는 항목이 없는 경우 비교 연산자는 빈 배열을 반환 합니다.

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

예외는 포함 연산자, In 연산자 및 형식 연산자 이며 항상 **부울** 값을 반환 합니다.

> [!NOTE]
> 값을 비교 해야 하는 경우 `$null` `$null` 비교의 왼쪽에를 넣어야 합니다. `$null` **개체 []** 와 비교할 때 비교 개체가 배열 이기 때문에 결과가 **False** 입니다. 배열을와 비교할 때 `$null` 비교는 `$null` 배열에 저장 된 모든 값을 필터링 합니다. 예를 들어:
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a>같음 연산자

같음 연산자 ( `-eq` , `-ne` )는 하나 이상의 입력 값이 지정 된 패턴과 동일한 경우 TRUE 또는 일치 항목의 값을 반환 합니다. 전체 패턴이 전체 값과 일치 해야 합니다.

예제:

### <a name="-eq"></a>-eq

설명:가와 같습니다. 에 동일한 값이 포함 된 경우

예제:

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

### <a name="-ne"></a>-ne

설명: 같지 않음 에 다른 값이 포함 된 경우

예제:

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

### <a name="-gt"></a>-gt

설명: 보다 큼

예제:

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> `>`다른 많은 프로그래밍 언어의 보다 큼 연산자와 혼동 해서는 안 됩니다. PowerShell에서 `>` 는 리디렉션에 사용 됩니다. 자세한 내용은 [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)를 참조 하세요.

### <a name="-ge"></a>-ge

설명: 크거나 같음.

예제:

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a>-lt

설명: 보다 작음

예제:

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a>-le

설명: 보다 작거나 같음입니다.

예제:

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a>일치 연산자

Like 연산자 ( `-like` 및 `-notlike` )는 와일드 카드 식을 사용 하 여 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.

구문은 다음과 같습니다.

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

일치 연산자 ( `-match` 및 `-notmatch` )가 정규식을 사용 하 여 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.

`$Matches`연산자에 대 한 입력 (왼쪽 인수)이 단일 스칼라 개체인 경우 match 연산자는 자동 변수를 채웁니다. 입력이 스칼라 인 경우 `-match` 및 연산자는 `-notmatch` 부울 값을 반환 하 고 `$Matches` 자동 변수 값을 인수의 일치 하는 구성 요소로 설정 합니다.

구문은 다음과 같습니다.

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a>-like

설명: 와일드 카드 문자 ()를 사용 하 여 찾습니다 \* .

예제:

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a>-notlike

설명: 와일드 카드 문자 ()를 사용 하 여 일치 하지 않습니다 \* .

예제:

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a>-match

설명: 정규식을 사용 하 여 문자열을 찾습니다. 입력이 스칼라 인 경우 자동 변수를 채웁니다 `$Matches` .

입력이 컬렉션인 경우 `-match` 및 `-notmatch` 연산자는 해당 컬렉션의 일치 하는 멤버를 반환 하지만이 연산자는 변수를 채우지 않습니다 `$Matches` .

예를 들어 다음 명령은 연산자에 문자열 컬렉션을 전송 합니다 `-match` . `-match`연산자는 컬렉션에서 일치 하는 항목을 반환 합니다. 자동 변수를 채우지 않습니다 `$Matches` .

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

반면, 다음 명령은 단일 문자열을 운영자에 게 전송 합니다 `-match` . `-match`연산자는 부울 값을 반환 하 고 `$Matches` 자동 변수를 채웁니다. `$Matches`자동 변수는 **해시 테이블** 입니다. 그룹화 또는 캡처가 사용 되지 않으면 하나의 키만 채워집니다.
`0`키는 일치 된 모든 텍스트를 나타냅니다. 정규식을 사용한 그룹화 및 캡처에 대 한 자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

해시 테이블에는 일치 하는 `$Matches` 패턴이 처음 나타나는 경우만 포함 됩니다.

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> `0`키가 **정수** 입니다. 모든 **Hashtable** 메서드를 사용 하 여 저장 된 값에 액세스할 수 있습니다.
>
> ```powershell
> PS> "Good Dog" -match "Dog"
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

`-notmatch`연산자는 입력이 `$Matches` 스칼라 인 경우 자동 변수를 채우고 결과가 False 이면 일치 하는 항목을 검색 합니다.

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

### <a name="-notmatch"></a>-notmatch

설명:가 문자열과 일치 하지 않습니다. 정규식을 사용 합니다. 입력이 스칼라 인 경우 자동 변수를 채웁니다 `$Matches` .

예제:

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

## <a name="containment-operators"></a>포함 연산자

포함 연산자 ( `-contains` 및 `-notcontains` )는 같음 연산자와 유사 합니다. 그러나 포함 연산자는 입력이 컬렉션인 경우에도 항상 부울 값을 반환 합니다.

또한 같음 연산자와 달리 포함 연산자는 첫 번째 일치 항목을 검색 하는 즉시 값을 반환 합니다. 같음 연산자는 모든 입력을 평가한 다음 컬렉션에서 일치 하는 항목을 모두 반환 합니다.

### <a name="-contains"></a>-contains

설명: 포함 연산자. 참조 값의 컬렉션에 단일 테스트 값이 포함 되어 있는지 여부를 나타냅니다. 항상 부울 값을 반환 합니다. 테스트 값이 하나 이상의 참조 값과 정확 하 게 일치 하는 경우에만 TRUE를 반환 합니다.

테스트 값이 컬렉션인 경우 Contains 연산자는 참조 같음을 사용 합니다. 참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.

매우 큰 컬렉션에서 `-contains` 연산자는 같음 연산자 보다 더 빠른 결과를 반환 합니다.

구문

`<Reference-values> -contains <Test-value>`

예제:

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

### <a name="-notcontains"></a>-notcontains

설명: 포함 연산자. 참조 값의 컬렉션에 단일 테스트 값이 포함 되어 있는지 여부를 나타냅니다. 항상 부울 값을 반환 합니다. 테스트 값이 하나 이상의 참조 값과 정확히 일치 하지 않는 경우 TRUE를 반환 합니다.

테스트 값이 컬렉션인 경우 NotContains 연산자는 참조 같음을 사용 합니다.

구문

`<Reference-values> -notcontains <Test-value>`

예제:

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

### <a name="-in"></a>-in

설명: In 연산자 테스트 값이 참조 값의 컬렉션에 표시 되는지 여부를 나타냅니다. 항상 부울 값으로 반환 합니다. 테스트 값이 하나 이상의 참조 값과 정확 하 게 일치 하는 경우에만 TRUE를 반환 합니다.

테스트 값이 컬렉션인 경우 In 연산자는 참조 같음을 사용 합니다.
참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.

`-in`연산자는 PowerShell 3.0에서 도입 되었습니다.

구문

`<Test-value> -in <Reference-values>`

예제:

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

### <a name="-notin"></a>-notin

Description: 테스트 값이 참조 값의 컬렉션에 나타나는지 여부를 알려 줍니다. 항상 부울 값을 반환 합니다. 테스트 값이 하나 이상의 참조 값과 정확히 일치 하지 않는 경우 TRUE를 반환 합니다.

테스트 값이 컬렉션인 경우 In 연산자는 참조 같음을 사용 합니다.
참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.

`-notin`연산자는 PowerShell 3.0에서 도입 되었습니다.

구문

`<Test-value> -notin <Reference-values>`

예제:

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

## <a name="replacement-operator"></a>대체 연산자

`-replace`연산자의 구문은 다음과 같습니다.

`<input> -replace <original>, <substitute>`

`<original>`자리 표시자는 바꿀 문자와 일치 하는 정규식입니다. `<substitute>`자리 표시자는이를 대체 하는 리터럴 문자열입니다.

연산자는 정규식을 사용 하 여 값의 일부 또는 전체를 지정 된 값으로 바꿉니다. 파일 이름 바꾸기와 같은 많은 관리 작업에 대해 연산자를 사용할 수 있습니다. 예를 들어 다음 명령은 모든 파일의 파일 이름 확장명 `.txt` 을로 변경 합니다 `.log` .

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a>대/소문자 구분 일치

기본적으로 연산자는 `-replace` 대/소문자를 구분 하지 않습니다. 대/소문자를 구분 하려면를 사용 `-creplace` 합니다. 명시적으로 대/소문자를 구분 하지 않도록 하려면를 사용 `-ireplace` 합니다.

다음 예제를 살펴보세요.

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a>정규식의 대체

또한 정규식을 사용 하 여 캡처링 그룹 및 대체를 사용 하 여 텍스트를 동적으로 바꿀 수 있습니다. `<substitute>`그룹 식별자 앞에 달러 기호 () 문자를 사용 하 여 문자열에서 캡처 그룹을 참조할 수 있습니다 `$` .

캡처 그룹은 **번호** 또는 **이름** 으로 참조할 수 있습니다.

- **번호** 캡처링 그룹은 왼쪽에서 오른쪽으로 번호가 매겨집니다.

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- 이름 **으로** 캡처링 그룹은 이름으로 참조할 수도 있습니다.

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> 문자는 `$` 문자열 확장에 사용 되므로 리터럴 문자열을 사용 하거나 문자를 이스케이프 해야 합니다 `$` .
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> 또한 `$` 문자가 대체에 사용 되므로 문자열의 모든 인스턴스를 이스케이프 해야 합니다.
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

자세히 알아보려면 정규식의 [about_Regular_Expressions](about_Regular_Expressions.md) 및 [대체](/dotnet/standard/base-types/substitutions-in-regular-expressions) 를 참조 하세요.

### <a name="substituting-in-a-collection"></a>컬렉션에서 대체

`<input>` `-replace` 연산자가 컬렉션인 경우 PowerShell은 컬렉션의 모든 값에 대체를 적용 합니다. 예를 들어:

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

## <a name="type-comparison"></a>형식 비교

형식 비교 연산자 ( `-is` 및 `-isnot` )는 개체가 특정 형식 인지 여부를 확인 하는 데 사용 됩니다.

### <a name="-is"></a>-is

구문

`<object> -is <type reference>`

예제:

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a>-isnot

구문

`<object> -isnot <type reference>`

예제:

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a>참고 항목

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [Foreach-개체](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)
