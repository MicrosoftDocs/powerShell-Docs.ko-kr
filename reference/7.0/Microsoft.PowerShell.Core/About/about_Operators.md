---
description: PowerShell에서 지 원하는 연산자에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: d442a64be77934cef4636e905c098d9630451b8f
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93225305"
---
# <a name="about-operators"></a>연산자 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 지 원하는 연산자에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

연산자는 명령 또는 식에서 사용할 수 있는 언어 요소입니다.
PowerShell은 값을 조작 하는 데 도움이 되는 여러 유형의 연산자를 지원 합니다.

### <a name="arithmetic-operators"></a>산술 연산자

산술 연산자 ( `+` ,, `-` `*` , `/` , `%` )를 사용 하 여 명령 또는 식의 값을 계산할 수 있습니다. 이러한 연산자를 사용 하 여 값을 추가, 빼기, 곱하기 또는 나눈 다음 나누기 연산의 나머지 (모듈러스)를 계산할 수 있습니다.

더하기 연산자는 요소를 연결 합니다. 곱하기 연산자는 각 요소에 대해 지정 된 수의 복사본을 반환 합니다. ,,,, 등을 구현 하는 .net 형식에 산술 연산자를 사용할 수 있습니다 `Int` `String` `DateTime` `Hashtable` .

비트 연산자 ( `-band` , `-bor` , `-bxor` , `-bnot` , `-shl` , `-shr` )는 값의 비트 패턴을 조작 합니다.

자세한 내용은 [about_Arithmetic_Operators](about_Arithmetic_Operators.md)를 참조 하세요.

### <a name="assignment-operators"></a>할당 연산자

할당 연산자 ( `=` ,, `+=` , `-=` , `*=` `/=` , `%=` )를 사용 하 여 변수에 값을 할당, 변경 또는 추가할 수 있습니다. 산술 연산자를 할당과 결합 하 여 산술 연산 결과를 변수에 할당할 수 있습니다.

자세한 내용은 [about_Assignment_Operators](about_Assignment_Operators.md)를 참조 하세요.

### <a name="comparison-operators"></a>비교 연산자

비교 연산자 ( `-eq` ,, `-ne` , `-gt` , `-lt` `-le` , `-ge` )를 사용 하 여 값 및 테스트 조건을 비교할 수 있습니다. 예를 들어 두 문자열 값을 비교 하 여 같은지 여부를 확인할 수 있습니다.

비교 연산자에는 텍스트의 패턴을 찾거나 바꾸는 연산자도 포함 됩니다. (, `-match` `-notmatch` , `-replace` ) 연산자는 정규식을 사용 하 고 ( `-like` , `-notlike` )는 와일드 카드를 사용 `*` 합니다.

포함 비교 연산자는 테스트 값이 참조 집합 ( `-in` ,,,)에 표시 되는지 여부를 결정 `-notin` `-contains` `-notcontains` 합니다.

형식 비교 연산자 ( `-is` , `-isnot` )는 개체가 지정 된 형식 인지 여부를 확인 합니다.

자세한 내용은 [about_Comparison_Operators](about_Comparison_Operators.md)를 참조 하세요.

### <a name="logical-operators"></a>논리 연산자

논리 연산자 ( `-and` , `-or` , `-xor` , `-not` , `!` )를 사용 하 여 조건부 문을 단일 복합 조건에 연결 합니다. 예를 들어 논리 연산자를 사용 `-and` 하 여 두 가지 조건이 있는 개체 필터를 만들 수 있습니다.

자세한 내용은 [about_Logical_Operators](about_logical_operators.md)를 참조 하세요.

### <a name="redirection-operators"></a>리디렉션 연산자

리디렉션 연산자 ( `>` ,, `>>` `2>` , `2>>` 및 `2>&1` )를 사용 하 여 명령 또는 식의 출력을 텍스트 파일로 보냅니다. 리디렉션 연산자는 `Out-File` 매개 변수 없이 cmdlet 처럼 작동 하지만, 오류 출력을 지정 된 파일로 리디렉션할 수도 있습니다. Cmdlet을 사용 하 여 `Tee-Object` 출력을 리디렉션할 수도 있습니다.

자세한 내용은 [about_Redirection](about_Redirection.md) 를 참조 하세요.

### <a name="split-and-join-operators"></a>분할 및 조인 연산자

`-split`및 `-join` 연산자는 부분 문자열을 나누고 결합 합니다. `-split`연산자는 문자열을 부분 문자열로 분할 합니다. `-join`연산자는 여러 문자열을 단일 문자열로 연결 합니다.

자세한 내용은 [about_Split](about_Split.md) 및 [about_Join](about_Join.md)를 참조 하세요.

### <a name="type-operators"></a>형식 연산자

형식 연산자 ( `-is` , `-isnot` , `-as` )를 사용 하 여 개체의 .NET Framework 유형을 찾거나 변경할 수 있습니다.

자세한 내용은 [about_Type_Operators](about_Type_Operators.md)를 참조 하세요.

### <a name="unary-operators"></a>단항 연산자

단항 연산자를 사용 하 여 변수 또는 개체 속성을 증가 또는 감소 시키고 정수를 양수 또는 음수로 설정 합니다. 예를 들어 변수를에서로 증가 시키려면를 `$a` `9` `10` 입력 `$a++` 합니다.

### <a name="special-operators"></a>특수 연산자

특수 연산자에는 다른 운영자 그룹에 맞지 않는 특정 사용 사례가 있습니다. 예를 들어 특수 연산자를 사용 하 여 명령을 실행 하거나, 값의 데이터 형식을 변경 하거나, 배열에서 요소를 검색할 수 있습니다.

#### <a name="grouping-operator--"></a>그룹화 연산자 `( )`

다른 언어와 마찬가지로에서는 `(...)` 식의 연산자 우선 순위를 재정의 합니다. `(1 + 2) / 3`

그러나 PowerShell에는 추가 동작이 있습니다.

- `(...)`_명령의_ 출력이 식에 참여할 수 있도록 합니다. 다음은 그 예입니다. 

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- 파이프라인의 첫 번째 세그먼트로 사용 되는 경우 괄호를 사용 하 여 명령 또는 식을 항상 식 결과를 _열거_ 합니다. 괄호가 _명령을_ 래핑하는 경우 파이프라인을 통해 결과가 전송 되기 전에 _메모리에 수집_ 된 모든 출력을 사용 하 여 완료 될 때까지 실행 됩니다.

#### <a name="subexpression-operator--"></a>하위 식 연산자 `$( )`

하나 이상의 문 결과를 반환 합니다. 단일 결과의 경우 스칼라를 반환 합니다. 여러 결과에 대해는 배열을 반환 합니다. 다른 식 내에서 식을 사용 하려는 경우이를 사용 합니다. 예를 들어 명령 결과를 문자열 식에 포함 하려면

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a>Array 하위 식 연산자 `@( )`

하나 이상의 문 결과를 배열로 반환 합니다. 항목이 하나만 있는 경우 배열에는 하나의 멤버만 있습니다.

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a>Call 연산자 `&`

명령, 스크립트 또는 스크립트 블록을 실행 합니다. "호출 연산자" 라고도 하는 call 연산자를 사용 하면 변수에 저장 되 고 문자열 또는 스크립트 블록으로 표시 되는 명령을 실행할 수 있습니다. 호출 연산자는 자식 범위에서 실행 됩니다. 범위에 대 한 자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.

이 예제에서는 명령을 문자열에 저장 하 고 call 연산자를 사용 하 여 실행 합니다.

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

호출 연산자는 문자열을 구문 분석 하지 않습니다. 즉, call 연산자를 사용 하는 경우 문자열 내에서 명령 매개 변수를 사용할 수 없습니다.

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
```

호출 연산자를 사용할 때 구문 분석 오류가 발생 하는 코드를 [호출](xref:Microsoft.PowerShell.Utility.Invoke-Expression) 하는 코드를 실행할 수 있습니다.

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

Call 연산자를 사용 하 여 파일 이름을 사용 하 여 스크립트를 실행할 수 있습니다. 아래 예제에서는 공백이 포함 된 스크립트 파일 이름을 보여 줍니다. 스크립트를 실행 하려고 하면 PowerShell은 대신 파일 이름을 포함 하는 따옴표 붙은 문자열의 내용을 표시 합니다. Call 연산자를 사용 하 여 파일 이름을 포함 하는 문자열의 내용을 실행할 수 있습니다.

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

스크립트 블록에 대 한 자세한 내용은 [about_Script_Blocks](about_Script_Blocks.md)를 참조 하세요.

#### <a name="background-operator-"></a>Background 연산자 `&`

PowerShell 작업에서 백그라운드 이전에 파이프라인을 실행 합니다. 이 연산자는 `&` subshell에서 작업으로 비동기적으로 명령을 실행 하는 UNIX 제어 연산자 앰퍼샌드 ()와 유사 하 게 작동 합니다.

이 연산자는와 기능적으로 동일 `Start-Job` 합니다. 기본적으로 background 연산자는 병렬 작업을 시작 하는 호출자의 현재 작업 디렉터리에서 작업을 시작 합니다. 다음 예에서는 백그라운드 작업 연산자의 기본 사용법을 보여 줍니다.

```powershell
Get-Process -Name pwsh &
```

이 명령은 다음과 같은 기능을 사용 하는 것과 기능적으로 동일 합니다 `Start-Job` .

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

마찬가지로 `Start-Job` `&` background 연산자는 개체를 반환 합니다 `Job` . 이 개체는 `Receive-Job` `Remove-Job` 작업을 시작 하는 데 사용한 것 처럼 및와 함께 사용할 수 있습니다 `Start-Job` .

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

`&`또한 background 연산자는 UNIX 제어 연산자 앰퍼샌드 ()와 마찬가지로 문 종결자입니다 `&` . 이렇게 하면 백그라운드 연산자 다음에 추가 명령을 호출할 수 있습니다 `&` . 다음 예에서는 백그라운드 연산자 다음에 추가 명령을 호출 하는 방법을 보여 줍니다 `&` .

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

다음 스크립트와 동일 합니다.

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

각각의 백그라운드 프로세스에서 각 명령을 한 줄에 실행 하려는 경우 각 명령의 앞뒤에 있는 명령을 입력 `&` 합니다.

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

PowerShell 작업에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.

#### <a name="cast-operator--"></a>캐스트 연산자 `[ ]`

개체를 지정 된 형식으로 변환 하거나 제한 합니다. 개체를 변환할 수 없는 경우 PowerShell에서 오류를 생성 합니다.

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

캐스트 [표기법](about_Variables.md)을 사용 하 여 변수를 할당 하는 경우에도 캐스트를 수행할 수 있습니다.

#### <a name="comma-operator-"></a>쉼표 연산자 `,`

이항 연산자로 쉼표는 배열을 만들거나 생성 되는 배열에 추가 합니다. 식 모드에서 단항 연산자는 쉼표를 사용 하 여 하나의 멤버만 사용 하는 배열을 만듭니다. 멤버 앞에 쉼표를 놓습니다.

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

에 `Write-Object` 는 인수가 필요 하므로 식을 괄호 안에 넣어야 합니다.

#### <a name="dot-sourcing-operator-"></a>점 소싱 연산자 `.`

현재 범위에서 스크립트를 실행 하 여 스크립트에서 만드는 모든 함수, 별칭 및 변수가 현재 범위에 추가 되 고 기존 함수를 재정의 합니다. 스크립트에 의해 선언 된 매개 변수는 변수가 됩니다. 값이 지정 되지 않은 매개 변수는 값이 없는 변수가 됩니다. 그러나 자동 변수는 `$args` 유지 됩니다.

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> 점 소싱 연산자에는 공백이 있습니다. 공백을 사용 하 여 `.` 현재 디렉터리를 나타내는 점 () 기호와 점을 구분 합니다.
>
> 다음 예제에서는 현재 디렉터리의 Sample.ps1 스크립트가 현재 범위에서 실행 됩니다.
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a>Format 연산자 `-f`

문자열 개체의 format 메서드를 사용 하 여 문자열의 서식을 지정 합니다. 연산자의 좌 변에 있는 형식 문자열을 입력 하 고 연산자의 오른쪽에 서식을 지정할 개체를 입력 합니다.

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

서식이 지정 된 문자열에서 중괄호 ()를 유지 해야 하는 경우 중괄호 `{}` 를 두 배로 하 여 이스케이프할 수 있습니다.

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

자세한 내용은 [string.format](/dotnet/api/system.string.format) 메서드 및 [복합 서식 지정](/dotnet/standard/base-types/composite-formatting)을 참조 하세요.

#### <a name="index-operator--"></a>Index 연산자 `[ ]`

배열 및 해시 테이블과 같은 인덱싱된 컬렉션에서 개체를 선택 합니다. 배열 인덱스는 0부터 시작 하므로 첫 번째 개체는로 인덱싱됩니다 `[0]` . 배열의 경우에는 음수 인덱스만 사용 하 여 마지막 값을 가져올 수도 있습니다. 해시 테이블은 키 값으로 인덱싱됩니다.

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a>파이프라인 연산자 `|`

앞에 오는 명령의 출력 ("파이프")을 뒤에 오는 명령에 보냅니다. 출력에 둘 이상의 개체 ("컬렉션")가 포함 된 경우 파이프라인 연산자는 개체를 한 번에 하나씩 보냅니다.

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a>파이프라인 체인 연산자 `&&` 및 `||`

왼쪽 파이프라인의 성공 여부에 따라 오른쪽 파이프라인을 조건부로 실행 합니다.

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

자세한 내용은 [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md)를 참조 하세요.

#### <a name="range-operator-"></a>Range 연산자 `..`

지정 된 상한 및 하 한을 가진 정수 배열의 순차 정수를 나타냅니다.

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

또한 순서에 따라 범위를 만들 수 있습니다.

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

PowerShell 6부터 범위 연산자는 **정수** 뿐만 아니라 **문자와** 함께 작동 합니다.

문자 범위를 만들려면 경계 문자를 따옴표로 묶습니다.

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a>멤버 액세스 연산자 `.`

개체의 속성 및 메서드에 액세스 합니다. 멤버 이름은 식일 수 있습니다.

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a>정적 멤버 연산자 `::`

.NET Framework 클래스의 정적 속성 및 메서드를 호출 합니다. 개체의 정적 속성 및 메서드를 찾으려면 cmdlet의 정적 매개 변수를 사용 합니다 `Get-Member` .  멤버 이름은 식일 수 있습니다.

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a>삼항 연산자 `? <if-true> : <if-false>`

단순 조건부 사례의 문에 대 한 대체 항목으로 삼항 연산자를 사용할 수 있습니다 `if-else` .

자세한 내용은 [about_If](about_If.md)를 참조 하세요.

#### <a name="null-coalescing-operator-"></a>Null 병합 연산자 `??`

Null 병합 연산자 `??`는 null이 아닌 경우 왼쪽 피연산자의 값을 반환합니다. 그렇지 않으면 오른쪽 피연산자를 계산하고 그 결과를 반환합니다. `??` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

다음 예에서는 오른쪽 피연산자를 계산 하지 않습니다.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a>Null 병합 할당 연산자 `??=`

Null 병합 할당 연산자는 왼쪽 피연산자가 `??=` null로 계산 되는 경우에만 오른쪽 피연산자의 값을 왼쪽 피연산자에 할당 합니다. `??=` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

다음 예에서는 오른쪽 피연산자를 계산 하지 않습니다.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a>Null 조건부 연산자 `?.` 및 `?[]`

> [!NOTE]
> 이는 실험적인 기능입니다. 자세한 내용은 [about_Experimental_Features](about_Experimental_Features.md)를 참조 하세요.

Null 조건 연산자는 해당 `?.` `?[]` 피연산자가 null이 아닌 값으로 계산 되는 경우에만 해당 피연산자에 대 한 멤버 액세스, 또는 요소 액세스를 적용 합니다. 그렇지 않으면 null을 반환 합니다.

PowerShell을 사용하면 `?`를 변수 이름에 포함할 수 있으므로 이러한 연산자를 사용하려면 변수 이름의 공식적인 사양이 필요합니다. 따라서 `{}`를 `${a}`와 같이 변수 이름 주위에 사용하거나 `?`이 변수 이름의 일부인 경우(`${a?}`)에 사용해야 합니다.

다음 예에서는 **속성 속성** 의 값이 반환 됩니다.

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

다음 예에서는 멤버 이름 **속성** 이름에 액세스 하려고 하지 않고 null을 반환 합니다.

```powershell
$a = $null
${a}?.PropName
```

마찬가지로 요소 값이 반환 됩니다.

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

피연산자가 null 이면 요소에 액세스 되지 않고 null이 반환 됩니다.

```PowerShell
$a = $null
${a}?[0]
```

## <a name="see-also"></a>참고 항목

[about_arithmetic_operators](about_Arithmetic_Operators.md)

[about_assignment_operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Logical_Operators](about_logical_operators.md)

[about_Operator_Precedence](about_operator_precedence.md)

[about_Type_Operators](about_Type_Operators.md)

[about_Pipeline_Chain_Operators](about_Pipeline_Chain_Operators.md)

[about_Split](about_Split.md)

[about_join](about_Join.md)

[about_Redirection](about_Redirection.md)
