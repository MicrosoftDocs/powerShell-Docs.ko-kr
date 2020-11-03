---
description: PowerShell의 정규식에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: d4a01d183290f31202471a221b24859d556e7e3d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220969"
---
# <a name="about-regular-expressions"></a>정규식 정보

## <a name="short-description"></a>간단한 설명
PowerShell의 정규식에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

> [!NOTE]
> 이 문서에서는 PowerShell에서 정규식을 사용 하기 위한 구문과 메서드를 보여 줍니다. 모든 구문에 대해서는 설명 하지 않습니다. 자세한 참조는 [정규식 언어-빠른 참조](/dotnet/standard/base-types/regular-expression-language-quick-reference)를 참조 하세요.

정규식은 텍스트를 일치 시키는 데 사용 되는 패턴입니다. 리터럴 문자, 연산자 및 기타 구문으로 구성 될 수 있습니다.

이 문서에서는 PowerShell의 정규식 구문을 보여 줍니다. PowerShell에는 정규식을 사용 하는 몇 가지 연산자와 cmdlet이 있습니다. 구문 및 사용법에 대 한 자세한 내용은 아래 링크를 참조 하세요.

- [Select-String](xref:Microsoft.PowerShell.Utility.Select-String)
- [-match 및-replace 연산자](about_Comparison_Operators.md)
- [-분할](about_Split.md)
- [-regex 옵션을 사용 하는 switch 문](about_Switch.md)

PowerShell 정규식은 기본적으로 대/소문자를 구분 하지 않습니다. 위에 표시 된 각 방법에는 대/소문자 구분을 적용 하는 다른 방법이 있습니다.

|       메서드       |                      대/소문자 구분                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | `-CaseSensitive`스위치 사용                                |
| `switch` 문 | 옵션 사용 `-casesensitive`                            |
| 연산자          | **' c '** ( `-cmatch` , `-csplit` 또는 `-creplace` )를 사용 하는 접두사 |

### <a name="character-literals"></a>문자 리터럴

정규식은 리터럴 문자 또는 문자열일 수 있습니다. 식이 지정 된 텍스트와 정확히 일치 하도록 엔진을 설정 합니다.

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a>문자 클래스

문자 리터럴은 정확한 패턴을 알고 있는 경우에만 작동 하지만 문자 클래스를 사용 하면 더 구체적으로 지정할 수 있습니다.

#### <a name="character-groups"></a>문자 그룹

`[character group]` 를 사용 하면 한 번의 문자를 한 번만 일치 시킬 수 있으며 `[^character group]` 그룹에 없는 문자만 일치 시킬 수 있습니다.

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

일치 시킬 문자 목록에 하이픈 문자 ()가 포함 되어 있으면 `-` 문자 범위 식과 구분 하기 위해 목록의 시작 부분 또는 끝 부분에 있어야 합니다.

#### <a name="character-ranges"></a>문자 범위

패턴은 문자 범위가 될 수도 있습니다. 문자는 영문자 `[A-Z]` , 숫자 `[0-9]` 또는 ASCII 기반 `[ -~]` (모든 인쇄 가능한 문자) 일 수 있습니다.

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a>숫자

`\d`문자 클래스는 10 진수를 찾습니다. 반대로 `\D` 는 10 진수가 아닌 모든 숫자를 찾습니다.

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a>단어 문자

`\w`문자 클래스는 단어 문자를 찾습니다 `[a-zA-Z_0-9]` . 비단어 문자를 찾으려면를 사용 `\W` 합니다.

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a>와일드카드

마침표 ( `.` )는 정규식의 와일드 카드 문자입니다. 줄 바꿈 ()을 제외한 모든 문자를 찾습니다 `\n` .

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a>공백

문자 클래스를 사용 하 여 공백을 일치 시킵니다 `\s` . 공백이 아닌 문자는를 사용 하 여 일치 시킵니다 `\S` . 리터럴 공백 문자 `' '` 를 사용할 수도 있습니다.

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a>수량자

수량자는 입력 문자열에 있는 각 요소의 인스턴스 수를 제어 합니다.

PowerShell에서 사용할 수 있는 수량자 중 몇 가지는 다음과 같습니다.

| 수량자 |                설명                |
| ---------- | ----------------------------------------- |
| `*`        | 0 회 이상                       |
| `+`        | 한 번 이상                        |
| `?`        | 0 번 또는 1 번.                         |
| `{n,m}`    | 적어도 `n` 한 `m` 번 이상. |

별표 ( `*` )는 이전 요소를 0 번 이상 찾습니다. 따라서 요소가 없는 입력 문자열도 일치 하는 항목이 됩니다.

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

더하기 기호 ( `+` )는 이전 요소를 1 번 이상 일치 시킵니다.

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

물음표는 `?` 이전 요소를 0 번 또는 한 번 일치 시킵니다. 별표와 마찬가지로 `*` 요소가 없는 문자열도 일치 시킵니다.

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

`{n, m}`수량자를 사용 하 여 수량자를 세부적으로 제어할 수 있는 여러 가지 방법을 사용할 수 있습니다. 두 번째 요소 `m` 와 쉼표는 `,` 선택 사항입니다.

| 수량자 |                설명                 |
| ---------- | ------------------------------------------ |
| `{n}`      | 정확히 일치 하 `n` 는 횟수입니다.         |
| `{n,}`     | 최소 횟수를 찾습니다 `n` .        |
| `{n,m}`    | `n`와 횟수를 일치 시킵니다 `m` . |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a>앵커

앵커를 사용 하면 입력 문자열 내의 일치 위치에 따라 일치가 성공 하거나 실패할 수 있습니다.

일반적으로 사용 되는 두 앵커는 `^` 및 `$` 입니다. 캐럿은 문자열의 `^` 시작과 일치 하며 `$` 문자열의 끝과 일치 합니다. 앵커를 사용 하면 원치 않는 문자를 삭제 하는 동시에 특정 위치에 있는 텍스트를 찾을 수 있습니다.

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> 앵커를 포함 하는 regex를 정의할 때 큰따옴표 `$` () 대신 작은따옴표 ()를 사용 하 여 regex를 묶어야 합니다 `'` `"` . 그렇지 않으면 PowerShell에서 식을 변수로 확장 합니다.

PowerShell에서 앵커를 사용 하는 경우 **regexoptions.singleline** 및 **Multiline** 정규식 옵션의 차이점을 이해 해야 합니다.

- **여러** 줄 모드: 여러 줄 모드는 `^` `$` 입력 문자열의 시작 및 끝이 아니라 모든 줄의 시작 부분을 일치 시킵니다.
- **Regexoptions.singleline** : regexoptions.singleline 모드는 입력 문자열을 **regexoptions.singleline** 로 처리 합니다.
  `.`줄 바꿈 문자를 제외한 모든 문자와 일치 하는 대신 문자를 모든 문자 (줄바꿈 포함)와 일치 하도록 강제 합니다 `\n` .

이러한 옵션 및 사용 방법에 대 한 자세한 내용은 [정규식 언어-빠른 참조](/dotnet/standard/base-types/regular-expression-language-quick-reference)를 참조 하세요.

### <a name="escaping-characters"></a>문자 이스케이프

백슬래시 ( `\` )는 문자를 이스케이프 하는 데 사용 되므로 정규식 엔진에서 구문 분석 되지 않습니다.

다음 문자는 예약 되어 `[]().\^$|?*+{}` 있습니다.

입력 문자열에서 이러한 문자를 일치 시키려면 패턴에서 이러한 문자를 이스케이프 해야 합니다.

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

텍스트를 이스케이프할 수 있는 정규식 클래스의 정적 메서드가 있습니다.

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> 문자 클래스에서 사용 되는 기존 백슬래시를 포함 하 여 모든 예약 된 정규식 문자를 이스케이프 합니다. 이스케이프 해야 하는 패턴 부분 에서만 사용 해야 합니다.

#### <a name="other-character-escapes"></a>기타 문자 이스케이프

특수 문자 형식을 일치 시키는 데 사용할 수 있는 예약 된 문자 이스케이프도 있습니다.

일반적으로 사용 되는 문자 이스케이프는 다음과 같습니다.

|문자 이스케이프  |Description  |
|---------|---------|
|`\t`|탭과 일치|
|`\n`|줄 바꿈 문자를 찾습니다.|
|`\r`|캐리지 리턴 문자를 찾습니다.|

### <a name="groups-captures-and-substitutions"></a>그룹, 캡처 및 대체

그룹화 구문은 입력 문자열을 캡처하거나 무시할 수 있는 부분 문자열로 구분 합니다. 그룹화 된 부분 문자열을 하위 식 이라고 합니다. 기본적으로 부분식은 번호 매기기 그룹에 캡처되고 이름을 지정할 수도 있습니다.

그룹화 구문은 괄호로 묶은 정규식입니다. 포함 된 정규식과 일치 하는 모든 텍스트가 캡처됩니다. 다음 예제에서는 입력 텍스트를 두 개의 캡처링 그룹으로 나눕니다.

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

`$Matches` **Hashtable** 자동 변수를 사용 하 여 캡처된 텍스트를 검색 합니다.
전체 일치 항목을 나타내는 텍스트는 키에 저장 됩니다 `0` .

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

캡처는 왼쪽에서 오른쪽으로 증가 하는 숫자 **정수** 키에 저장 됩니다. 캡처 `1` 는 사용자 이름, 캡처에 사용자 이름만 포함 될 때까지 모든 텍스트를 포함 합니다 `2` .

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> `0`키가 **정수** 입니다. 모든 **Hashtable** 메서드를 사용 하 여 저장 된 값에 액세스할 수 있습니다.
>
> ```
> PS> 'Good Dog' -match 'Dog'
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

#### <a name="named-captures"></a>명명 된 캡처

기본적으로 캡처는 왼쪽에서 오른쪽으로 오름차순으로 저장 됩니다.
캡처링 그룹에 **이름을** 할당할 수도 있습니다. 이 **이름은** `$Matches` **Hashtable** 자동 변수의 키가 됩니다.

캡처링 그룹 내에서를 사용 `?<keyname>` 하 여 캡처된 데이터를 명명 된 키 아래에 저장 합니다.

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

다음 예에서는 Windows 보안 로그에 최신 로그 항목을 저장 합니다.
제공 된 정규식은 메시지에서 사용자 이름과 도메인을 추출 하 여 키 아래에 저장 합니다. **N** 은 이름, 도메인의 경우 **D** 입니다.

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

자세한 내용은 [정규식의 그룹화 구문](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)을 참조 하세요.

#### <a name="substitutions-in-regular-expressions"></a>정규식의 대체

정규식을 연산자와 함께 사용 하면 `-replace` 캡처된 텍스트를 사용 하 여 동적으로 텍스트를 바꿀 수 있습니다.

`<input> -replace <original>, <substitute>`

- `<input>`: 검색할 문자열
- `<original>`: 입력 문자열을 검색 하는 데 사용 되는 정규식입니다.
- `<substitute>`: 입력 문자열에서 찾은 일치 항목을 대체할 정규식 대체 식입니다.

> [!NOTE]
> `<original>`및 `<substitute>` 피연산자는 문자 이스케이프와 같은 정규식 엔진의 규칙에 따라 결정 됩니다.

캡처링 그룹은 문자열에서 참조할 수 있습니다 `<substitute>` . 대체는 그룹 식별자 앞에 있는 문자를 사용 하 여 수행 됩니다 `$` .

캡처링 그룹을 참조 하는 두 가지 방법으로는 **번호** 및 **이름을** 기준으로 합니다.

- **번호** 캡처링 그룹은 왼쪽에서 오른쪽으로 번호가 매겨집니다.

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- 이름 **으로** 캡처링 그룹은 이름으로 참조할 수도 있습니다.

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

`$&`식은 일치 하는 모든 텍스트를 나타냅니다.

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> 문자는 `$` 문자열 확장에 사용 되므로 대체를 사용 하 여 리터럴 문자열을 사용 하거나 `$` 큰따옴표를 사용 하는 경우 문자를 이스케이프 해야 합니다.
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> 또한을 `$` 리터럴 문자로 사용 하려면 `$$` 일반 이스케이프 문자 대신을 사용 합니다. 큰따옴표를 사용 하는 경우에도의 모든 인스턴스를 이스케이프 `$` 하 여 잘못 된 대체가 발생 하지 않도록 합니다.
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

자세한 내용은 [정규식의 대체](/dotnet/standard/base-types/substitutions-in-regular-expressions)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Operators](about_Operators.md)
