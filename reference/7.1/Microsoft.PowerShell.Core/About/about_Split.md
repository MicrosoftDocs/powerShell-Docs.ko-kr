---
description: Split 연산자를 사용 하 여 하나 이상의 문자열을 부분 문자열로 분할 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: 3ea193fe0706e2a15d9f7ef64f37e29a19186648
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220465"
---
# <a name="about-split"></a>분할 정보

## <a name="short-description"></a>간단한 설명
Split 연산자를 사용 하 여 하나 이상의 문자열을 부분 문자열로 분할 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

Split 연산자는 하나 이상의 문자열을 부분 문자열로 분할 합니다. 분할 작업의 다음 요소를 변경할 수 있습니다.

- 문자가. 기본값은 공백 이지만 구분 기호를 지정 하는 문자, 문자열, 패턴 또는 스크립트 블록을 지정할 수 있습니다. PowerShell의 Split 연산자는 간단한 문자 대신 구분 기호에서 정규식을 사용 합니다.
- 최대 부분 문자열 수입니다. 기본값은 모든 부분 문자열을 반환 하는 것입니다. 하위 문자열 수보다 작은 숫자를 지정 하면 나머지 부분 문자열이 마지막 부분 문자열에 연결 됩니다.
- SimpleMatch 및 Multiline와 같이 구분 기호가 일치 하는 조건을 지정 하는 옵션입니다.

## <a name="syntax"></a>SYNTAX

다음 다이어그램에서는-split 연산자의 구문을 보여 줍니다.

명령에는 매개 변수 이름이 표시 되지 않습니다. 매개 변수 값만 포함 합니다. 값은 구문 다이어그램에 지정 된 순서 대로 표시 되어야 합니다.

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

`-iSplit` `-cSplit` `-split` 모든 이진 분할 문 (구분 기호 또는 스크립트 블록을 포함 하는 Split 문)에서 또는를 대체할 수 있습니다. `-iSplit`및 `-split` 연산자는 대/소문자를 구분 하지 않습니다. `-cSplit`연산자는 대/소문자를 구분 합니다. 즉, 구분 기호 규칙이 적용 될 때 대/소문자가 고려 됩니다.

## <a name="parameters"></a>PARAMETERS

### <a name="string-or-string"></a>\<String\> 또는 \<String[]\>

분할할 문자열을 하나 이상 지정 합니다. 여러 문자열을 전송 하는 경우 모든 문자열이 동일한 구분 기호 규칙을 사용 하 여 분할 됩니다.

예제:

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

부분 문자열의 끝을 식별 하는 문자입니다. 기본 구분 기호는 공백 및 인쇄할 수 없는 문자 (예: 줄 바꿈 ( \` n) 및 tab (t))를 포함 하는 공백입니다 \` . 문자열이 분할 되 면 모든 부분 문자열에서 구분 기호가 생략 됩니다. 예제:

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

기본적으로 구분 기호는 결과에서 생략 됩니다. 구분 기호의 전체 또는 일부를 유지 하려면 유지 하려는 부분을 괄호로 묶습니다.
\<Max-substrings\>매개 변수가 추가 되 면 명령이 컬렉션을 분할 하는 경우이 매개 변수가 우선적으로 적용 됩니다. 출력의 일부로 구분 기호를 포함 하도록 선택 하는 경우 명령은 출력의 일부로 구분 기호를 반환 합니다. 그러나 출력의 일부로 구분 기호를 반환 하도록 문자열을 분할 하는 것은 분할으로 계산 되지 않습니다.

예제:

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

다음 예제에서 \<Max-substrings\> 은 3으로 설정 됩니다. 이로 인해 문자열 값의 세 분할이 발생 하지만 결과 출력에 총 5 개의 문자열이 있습니다. 구분 기호는 분할 후에 포함 되며, 최대 세 부분 문자열에 도달할 때까지 포함 됩니다. 최종 부분 문자열의 추가 구분 기호는 부분 문자열의 일부가 됩니다.

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

문자열이 분할 되는 최대 횟수를 지정 합니다. 기본값은 구분 기호로 분할 된 모든 부분 문자열입니다. 부분 문자열이 더 있으면 최종 부분 문자열에 연결 됩니다. 부분 문자열이 더 적으면 모든 부분 문자열이 반환 됩니다. 값 0은 모든 부분 문자열을 반환 합니다. 음수 값은 입력 문자열의 끝부터 시작 하 여 요청 된 부분 문자열의 크기를 반환 합니다.

> [!NOTE]
> PowerShell 7에 음수 값에 대 한 지원이 추가 되었습니다.

**Max-하위 문자열** 은 반환 되는 최대 개체 수를 지정 하지 않습니다. 해당 값은 문자열이 분할 되는 최대 횟수와 같습니다.
연산자에 둘 이상의 문자열 (문자열 배열)을 전송 하는 경우 `-split` **최대 부분** 문자열 한도가 각 문자열에 개별적으로 적용 됩니다.

예제:

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

구분 기호를 적용 하는 규칙을 지정 하는 식입니다. 식은 $true 또는 $false로 계산 되어야 합니다. 스크립트 블록을 중괄호로 묶습니다.

예제:

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

옵션 이름을 따옴표로 묶습니다. 옵션은 \<Max-substrings\> 매개 변수가 문에 사용 되는 경우에만 유효 합니다.

Options 매개 변수에 대 한 구문은 다음과 같습니다.

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

SimpleMatch 옵션은 다음과 같습니다.

- **SimpleMatch** : 구분 기호를 계산할 때 간단한 문자열 비교를 사용 합니다. RegexMatch와 함께 사용할 수 없습니다.
- **IgnoreCase** :-csplit 연산자가 지정 된 경우에도 대/소문자를 구분 하지 않는 일치를 수행 합니다.

RegexMatch 옵션은 다음과 같습니다.

- **RegexMatch** : 정규식 일치를 사용 하 여 구분 기호를 평가 합니다. 기본 동작입니다. SimpleMatch와 함께 사용할 수 없습니다.
- **IgnoreCase** :-csplit 연산자가 지정 된 경우에도 대/소문자를 구분 하지 않는 일치를 수행 합니다.
- **Regexoptions.cultureinvariant** : 구분 기호를 evaluting 때 언어의 문화권 차이를 무시 합니다. RegexMatch에만 유효 합니다.
- **Regexoptions.ignorepatternwhitespace** : 숫자 기호 (#)로 표시 된 이스케이프 되지 않은 공백과 주석을 무시 합니다. RegexMatch에만 유효 합니다.
- **여러** 줄 모드: 여러 줄 모드는 `^` `$` 입력 문자열의 시작 및 끝이 아니라 모든 줄의 시작 부분을 일치 시킵니다.
- **Regexoptions.singleline** : regexoptions.singleline 모드는 입력 문자열을 *regexoptions.singleline* 로 처리 합니다.
  `.`줄 바꿈 문자를 제외한 모든 문자와 일치 하는 대신 문자를 모든 문자 (줄바꿈 포함)와 일치 하도록 강제 합니다 `\n` .
- **Regexoptions.explicitcapture** : 명시적 캡처 그룹만 결과 목록에 반환 되도록 명명 되지 않은 일치 그룹을 무시 합니다. RegexMatch에만 유효 합니다.

## <a name="unary-and-binary-split-operators"></a>단항 및 이항 분할 연산자

단항 분할 연산자 ( `-split <string>` )의 우선 순위는 쉼표 보다 높습니다. 결과적으로, 쉼표로 구분 된 문자열 목록을 단항 분할 연산자에 제출 하면 첫 번째 쉼표 앞의 첫 번째 문자열만 분할 됩니다.

다음 패턴 중 하나를 사용 하 여 둘 이상의 문자열을 분할 합니다.

- 이진 분할 연산자 ( \<string[]\> -split) 사용 \<delimiter\>
- 모든 문자열을 괄호로 묶습니다.
- 변수에 문자열을 저장 한 다음 split 연산자에 변수를 제출 합니다.

다음 예제를 참조하세요.

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a>예제

다음 문은 공백에서 문자열을 분할 합니다.

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

다음 문은 임의의 쉼표에서 문자열을 분할 합니다.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

다음 문은 "er" 패턴에서 문자열을 분할 합니다.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

다음 문은 "N" 문자에서 대/소문자를 구분 하는 분할을 수행 합니다.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

다음 문은 "e" 및 "t"에서 문자열을 분할 합니다.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

다음 문은 "e"와 "r"에서 문자열을 분할 하지만 결과 부분 문자열을 6 개의 부분 문자열로 제한 합니다.

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

다음 문은 문자열을 세 개의 부분 문자열로 분할 합니다.

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

다음 문은 문자열의 끝에서 시작 하 여 문자열을 세 개의 부분 문자열로 분할 합니다.

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

다음 문은 두 문자열을 세 부분 문자열로 분할 합니다.
한도는 각 문자열에 독립적으로 적용 됩니다.

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

다음 문은 여기에서 문자열의 각 줄을 첫 번째 자릿수로 분할 합니다. 여러 줄 옵션을 사용 하 여 각 줄과 문자열의 시작 부분을 인식 합니다.

0은 Max 부분 문자열 매개 변수의 "모두 반환" 값을 나타냅니다. 최대 부분 문자열 값이 지정 된 경우에만 여러 줄 등의 옵션을 사용할 수 있습니다.

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

다음 문에서는 백슬래시 문자를 사용 하 여 점 (.) 구분 기호를 이스케이프 합니다.

기본 RegexMatch를 사용 하면 따옴표 (".")로 묶인 점이 줄 바꿈 문자를 제외한 모든 문자와 일치 하는 것으로 해석 됩니다. 결과적으로 Split 문은 줄 바꿈 문자를 제외한 모든 문자에 대해 빈 줄을 반환 합니다.

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

다음 문은 SimpleMatch 옵션을 사용 하 여-split 연산자를 지시 하 여 점 (.) 구분 기호를 리터럴로 해석 합니다.

0은 Max 부분 문자열 매개 변수의 "모두 반환" 값을 나타냅니다. SimpleMatch와 같은 옵션을 사용할 수 있습니다 .이 옵션은 Max-하위 문자열 값이 지정 된 경우에만 사용할 수 있습니다.

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

다음 문은 변수 값에 따라 두 구분 기호 중 하나에서 문자열을 분할 합니다.

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a>참고 항목

[Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_join](about_Join.md)

