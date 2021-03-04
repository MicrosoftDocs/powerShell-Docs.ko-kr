---
description: PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 02/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_comparison_operators
ms.openlocfilehash: 73a83e1cd93c3467857d5eded8ad6c384e548937
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685306"
---
# <a name="about-comparison-operators"></a>비교 연산자 정보

## <a name="short-description"></a>간단한 설명

PowerShell의 비교 연산자는 입력 값에 대해 두 값 또는 컬렉션의 필터 요소를 비교할 수 있습니다.

## <a name="long-description"></a>자세한 설명입니다.

비교 연산자를 사용 하 여 값을 비교 하거나 지정 된 패턴과 일치 하는 값을 찾을 수 있습니다. PowerShell에는 다음과 같은 비교 연산자가 포함 되어 있습니다.

|    유형     |   연산자   |              비교 테스트              |
| ----------- | ------------ | ----------------------------------------- |
| 등호    | -eq          | equals                                    |
|             | -ne          | 같지 않음                                |
|             | -gt          | 보다 큼                              |
|             | -ge          | 크거나 같음                     |
|             | -lt          | 다음보다 작음                                 |
|             | -le          | 작거나 같음                        |
| Matching    | -like        | 문자열이 와일드 카드 패턴과 일치           |
|             | -notlike     | 문자열이 와일드 카드 패턴과 일치 하지 않습니다.    |
|             | -match       | 문자열이 regex 패턴과 일치 합니다.              |
|             | -notmatch    | 문자열이 regex 패턴과 일치 하지 않습니다.       |
| 대체 기능 | -replace     | regex 패턴과 일치 하는 문자열을 바꿉니다. |
| Containment | -contains    | 컬렉션에 값이 포함 되어 있습니다.               |
|             | -notcontains | 컬렉션에 값이 포함 되어 있지 않습니다.       |
|             | -in          | 값이 컬렉션에 있습니다.                  |
|             | -notin       | 값이 컬렉션에 없습니다.              |
| Type        | -is          | 두 개체의 형식이 동일 합니다.            |
|             | -isnot       | 개체의 형식이 다릅니다.         |

## <a name="common-features"></a>일반 기능

기본적으로 모든 비교 연산자는 대/소문자를 구분 하지 않습니다. 대/소문자를 구분 하는 비교 연산자를 만들려면 뒤에를 추가 합니다 `c` `-` . 예를 들어 `-ceq` 은 대/소문자를 구분 하는 버전입니다 `-eq` . 대/소문자를 구분 하지 않도록 명시적으로 지정 하려면 앞에를 추가 `i` `-` 합니다. 예를 들어 `-ieq` 는의 명시적 대/소문자를 구분 하지 않는 버전입니다 `-eq` .

연산자의 입력이 스칼라 값 이면 연산자는 **부울** 값을 반환 합니다. 입력이 컬렉션인 경우 연산자는 식의 오른쪽 값과 일치 하는 컬렉션의 요소를 반환 합니다.
컬렉션에 일치 하는 항목이 없는 경우 비교 연산자는 빈 배열을 반환 합니다. 다음은 그 예입니다. 

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

몇 가지 예외도 있습니다.

- 포함 및 형식 연산자는 항상 **부울** 값을 반환 합니다.
- `-replace`연산자는 대체 결과를 반환 합니다.
- `-match`또한 및 `-notmatch` 연산자는 `$Matches` 자동 변수를 채웁니다.

## <a name="equality-operators"></a>같음 연산자

### <a name="-eq-and--ne"></a>-eq 및 -ne

왼쪽이 스칼라 인 경우 오른쪽이 정확 하 게 일치 하면 True를 반환 하 고, `-eq` 그렇지 않으면 False를 반환  `-eq` 합니다.  `-ne` 는 반대입니다. 양쪽이 일치할 경우 **false** 를 반환 합니다. 그렇지 않으면 `-ne` True를 반환 합니다.

예제:

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

왼쪽이 컬렉션인 경우 `-eq` 오른쪽에 일치 하는 멤버를 반환 하는 반면는 해당 멤버를 `-ne` 필터링 합니다.

예제:

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

이러한 연산자는 컬렉션의 모든 요소를 처리 합니다. 예제:

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

같음 연산자는 스칼라 또는 컬렉션 뿐 아니라 모든 두 개체를 허용 합니다.
그러나 비교 결과는 최종 사용자에 게 의미가 없을 수도 있습니다.
다음 예제에서는이 문제를 보여 줍니다.

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

이 예제에서는 동일한 속성을 사용 하 여 두 개의 개체를 만들었습니다. 그러나 같음 테스트 결과는 서로 다른 개체 이기 때문에 **False** 입니다. 비교 가능한 클래스를 만들려면 클래스에서 [IEquatable \<T> ][2] 을 구현 해야 합니다. 다음 예제에서는 [IEquatable \<T>][2] 를 구현 하 고 **파일** 및 **크기** 의 두 속성을 포함 하는 **MyFileInfoSet** 클래스의 부분 구현을 보여 줍니다. `Equals()`두 **MyFileInfoSet** 개체의 파일 및 크기 속성이 같으면이 메서드는 True를 반환 합니다.

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

임의의 개체를 비교 하는 중요 한 예는 null 인지 여부를 확인 하는 것입니다. 하지만 변수가 인지 여부를 확인 해야 하는 경우 `$null` `$null` 같음 연산자의 왼쪽에를 넣어야 합니다. 오른쪽에 배치 하는 것은 원하는 작업을 수행 하지 않습니다.

예를 `$a` 들어 다음과 같이 null 요소가 포함 된 배열을 사용할 수 있습니다.

```powershell
$a = 1, 2, $null, 4, $null, 6
```

다음 테스트는 `$a` null이 아닙니다.

```powershell
$null -ne $a
```

```output
True
```

그러나 다음은에서 null 요소를 모두 제외 하는 것입니다 `$a` .

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a>-gt,-ge,-lt 및-le

`-gt`, `-ge` , `-lt` 및는 `-le` 매우 유사 하 게 동작 합니다. 두 측면이 모두 스칼라 인 경우 두 변의 비교 방식에 따라 **True** 또는 **False** 를 반환 합니다.

| 연산자 | 다음의 경우 True를 반환 합니다.                   |
| -------- | -------------------------------------- |
| -gt      | 왼쪽이 더 큽니다.          |
| -ge      | 왼쪽이 크거나 같습니다. |
| -lt      | 왼쪽이 더 작습니다.          |
| -le      | 왼쪽이 작거나 같습니다. |

다음 예에서는 모든 문이 True를 반환 합니다.

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> 대부분의 프로그래밍 언어에서 보다 큼 연산자는 `>` 입니다. PowerShell에서이 문자는 리디렉션에 사용 됩니다. 자세한 내용은 [about_Redirection][3]를 참조 하세요.

왼쪽이 컬렉션인 경우 이러한 연산자는 컬렉션의 각 멤버를 오른쪽과 비교 합니다. 논리에 따라 멤버를 유지 하거나 삭제 합니다.

예제:

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

이러한 연산자는 [system.object][1]를 구현 하는 모든 클래스에서 작동 합니다.

예:

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

다음 예제에서는 ' a ' 뒤에 정렬 되는 미국 QWERTY 키보드에 기호가 없음을 보여 줍니다. 연산자에 이러한 기호를 모두 포함 하는 집합을 공급 `-gt` 하 여 ' a '와 비교 합니다. 출력은 빈 배열입니다.

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

연산자의 양쪽이 매우 비교할 수 없는 경우 이러한 연산자는 종료 되지 않는 오류를 발생 시킵니다.

## <a name="matching-operators"></a>일치 연산자

일치 하는 연산자 ( `-like` , `-notlike` , `-match` 및 `-notmatch` )가 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다. 및의 패턴 `-like` 은 `-notlike` , 및를 포함 하는 와일드 카드 식 이며 `*` `?` `[ ]` `-match` `-notmatch` 정규식 (Regex)을 받아들입니다.

구문은 다음과 같습니다.

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

이러한 연산자의 입력이 스칼라 값 이면 **부울** 값을 반환 합니다. 입력이 값 컬렉션인 경우 연산자는 일치 하는 멤버를 반환 합니다. 컬렉션에 일치 하는 항목이 없는 경우이 연산자는 빈 배열을 반환 합니다.

### <a name="-like-and--notlike"></a>유사 및-notlike

`-like` 및 `-notlike` 는 및와 유사 하 게 동작 `-eq` `-ne` 하지만 오른쪽은 [와일드 카드](about_Wildcards.md)를 포함 하는 문자열일 수 있습니다.

예제:

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a>-match 및-notmatch

`-match``-notmatch`정규식을 사용 하 여 왼쪽 값에서 패턴을 검색 합니다. 정규식은 전자 메일 주소, UNC 경로 또는 형식이 지정 된 전화 번호와 같은 복잡 한 패턴을 일치 시킬 수 있습니다. 오른쪽 문자열은 [정규식](about_Regular_Expressions.md) 규칙을 따라야 합니다.

스칼라 예제:

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

입력이 컬렉션인 경우 연산자는 해당 컬렉션의 일치 하는 멤버를 반환 합니다.

컬렉션 예:

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

`-match` 및는 `-notmatch` regex 캡처 그룹을 지원 합니다. 실행 될 때마다 `$Matches` 자동 변수를 덮어씁니다. `<input>`이 컬렉션이 면 변수가입니다 `$Matches` `$null` . `$Matches` 는 항상 전체 일치 항목을 저장 하는 ' 0 ' 이라는 키가 있는 **해시 테이블** 입니다. 정규식에 캡처 그룹이 포함 된 경우에는 `$Matches` 각 그룹에 대 한 추가 키가 포함 됩니다.

예제:

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.

## <a name="replacement-operator"></a>대체 연산자

### <a name="replacement-with-regular-expressions"></a>정규식으로 대체

Like와 같이 `-match` 연산자는 정규식을 사용 하 여 `-replace` 지정 된 패턴을 찾습니다. 그러나와 `-match` 는 달리 일치 항목을 지정 된 다른 값으로 바꿉니다.

구문

```
<input> -replace <regular-expression>, <substitute>
```

연산자는 정규식을 사용 하 여 값의 일부 또는 전체를 지정 된 값으로 바꿉니다. 파일 이름 바꾸기와 같은 많은 관리 작업에 대해 연산자를 사용할 수 있습니다. 예를 들어 다음 명령은 모든 파일의 파일 이름 확장명 `.txt` 을로 변경 합니다 `.log` .

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

기본적으로 연산자는 `-replace` 대/소문자를 구분 하지 않습니다. 대/소문자를 구분 하려면를 사용 `-creplace` 합니다. 명시적으로 대/소문자를 구분 하지 않도록 하려면를 사용 `-ireplace` 합니다.

예:

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a>정규식 대체

또한 정규식을 사용 하 여 캡처링 그룹 및 대체를 사용 하 여 텍스트를 동적으로 바꿀 수 있습니다. `<substitute>`그룹 식별자 앞에 달러 기호 () 문자를 사용 하 여 문자열에서 캡처 그룹을 참조할 수 있습니다 `$` .

다음 예에서는 `-replace` 연산자가 형식으로 사용자 이름을 받아 `DomainName\Username` 형식으로 변환 합니다 `Username@DomainName` .

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> `$`이 문자에는 PowerShell 및 정규식에서 syntatic 역할이 있습니다.
>
> - PowerShell에서 큰따옴표 사이에는 변수를 지정 하 고 하위 식 연산자로 작동 합니다.
> - Regex 검색 문자열에서 줄의 끝을 나타냅니다.
> - Regex 대체 문자열에서 캡처된 그룹을 나타냅니다. 정규식을 작은따옴표 사이에 배치 하거나 앞에 억음 () 문자를 삽입 해야 `` ` `` 합니다.

다음은 그 예입니다. 

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

`$$` Regex에서 리터럴을 나타냅니다 `$` . 대체 `$$` 문자열에서 결과 대체에 리터럴을 포함 하는 This `$` 입니다. 다음은 그 예입니다. 

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

자세히 알아보려면 [정규식의][4] [about_Regular_Expressions](about_Regular_Expressions.md) 및 대체를 참조 하세요.

### <a name="substituting-in-a-collection"></a>컬렉션에서 대체

`<input>` `-replace` 연산자가 컬렉션인 경우 PowerShell은 컬렉션의 모든 값에 대체를 적용 합니다. 다음은 그 예입니다. 

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a>스크립트 블록으로 바꾸기

PowerShell 6 이상에서 `-replace` 연산자는 대체를 수행 하는 스크립트 블록만 허용 합니다. 스크립트 블록은 모든 일치 항목에 대해 한 번씩 실행 됩니다.

구문

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

스크립트 블록 내에서 `$_` 자동 변수를 사용 하 여 대체 되는 입력 텍스트 및 기타 유용한 정보에 액세스 합니다. 이 변수의 클래스 형식은 [system.text.regularexpressions.regex>][2]입니다.

다음 예에서는 세 자리의 각 시퀀스를 해당 하는 문자로 바꿉니다. 스크립트 블록은 교체 해야 하는 3 자리 숫자의 각 집합에 대해 실행 됩니다.

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a>포함 연산자

포함 연산자 ( `-contains` , `-notcontains` , `-in` 및)는 `-notin` 입력이 컬렉션인 경우에도 항상 **부울** 값을 반환 한다는 점을 제외 하 고 같음 연산자와 유사 합니다. 이러한 연산자는 첫 번째 일치 항목을 검색 하는 즉시 비교를 중지 하는 반면 같음 연산자는 모든 입력 멤버를 평가 합니다. 매우 큰 컬렉션에서 이러한 연산자는 같음 연산자 보다 더 빠르게 반환 됩니다.

구문

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a>-contains 및-notcontains

이러한 연산자는 집합에 특정 요소가 포함 되는지 여부를 알려 줍니다. `-contains` 오른쪽 (테스트 개체)이 집합의 요소 중 하 나와 일치 하면 True를 반환 합니다. `-notcontains` 대신 False를 반환 합니다. 테스트 개체가 컬렉션인 경우 이러한 연산자는 참조 같음을 사용 합니다. 즉, 집합의 요소 중 하나가 테스트 개체의 동일한 인스턴스인지 여부를 확인 합니다.

예:

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

더 복잡 한 예제:

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a>-in 및-notin

`-in`및 연산자는 `notin` PowerShell 3에서 및 연산자의와 반대로 된 구문으로 도입 되었습니다 `contains` `-notcontain` . `-in`왼쪽  이 `<test-object>` 집합의 요소 중 하 나와 일치 하면 True를 반환 합니다. `-notin` 대신 **False** 를 반환 합니다. 테스트 개체가 집합인 경우 이러한 연산자는 참조 일치를 사용 하 여 집합의 요소 중 하나가 테스트 개체의 동일한 인스턴스인지 여부를 확인 합니다.

다음 예에서는 및에 대 한 예제와 동일한 작업 `-contain` `-notcontain` 을 수행 하지만 `-in` 및 대신 및를 사용 하 여 작성 됩니다 `-notin` .

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

더 복잡 한 예제:

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a>형식 비교

형식 비교 연산자 ( `-is` 및 `-isnot` )는 개체가 특정 형식 인지 여부를 확인 하는 데 사용 됩니다.

구문

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

예제:

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a>참고 항목

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [Foreach-개체](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
