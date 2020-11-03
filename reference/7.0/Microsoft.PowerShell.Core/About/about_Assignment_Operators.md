---
description: 연산자를 사용 하 여 변수에 값을 할당 하는 방법에 대해 설명 합니다.
keywords: powershell,cmdlet
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_assignment_operators
ms.openlocfilehash: fba0c5f5e5263af15eb3d56f1c42a881057afc46
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222978"
---
# <a name="about-assignment-operators"></a>할당 연산자 정보

## <a name="short-description"></a>간단한 설명
연산자를 사용 하 여 변수에 값을 할당 하는 방법에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

할당 연산자는 변수에 하나 이상의 값을 할당 합니다. 할당 하기 전에 값에 대해 숫자 연산을 수행할 수 있습니다.

PowerShell은 다음과 같은 할당 연산자를 지원 합니다.

|연산자|Description                                                  |
|--------|-------------------------------------------------------------|
|=       |변수의 값을 지정 된 값으로 설정 합니다.         |
|+=      |변수의 값을 지정 된 값 만큼 늘립니다. 또는 |
|        |지정 된 값을 기존 값에 추가 합니다.           |
|-=      |지정 된 값에 따라 변수 값을 줄입니다.    |
|*=      |변수의 값을 지정 된 값과 곱합니다. 또는|
|        |지정 된 값을 기존 값에 추가 합니다.           |
|/=      |변수의 값을 지정 된 값으로 나눕니다.      |
|%=      |변수의 값을 지정 된 값으로 나눕니다.   |
|        |그런 다음는 나머지 (모듈러스)를 변수에 할당 합니다.        |
|++      |변수 또는 할당 가능한 속성의 값을 늘립니다.   |
|        |1의 배열 요소입니다.                                          |
|--      |변수 또는 할당 가능한 속성의 값을 줄입니다.   |
|        |1의 배열 요소입니다.                                          |

## <a name="syntax"></a>구문

할당 연산자의 구문은 다음과 같습니다.

`<assignable-expression>` `<assignment-operator>` `<value>`

할당 가능한 식에는 변수 및 속성이 포함 됩니다. 값은 단일 값, 값 배열 또는 명령, 식 또는 문이 될 수 있습니다.

증가 및 감소 연산자는 단항 연산자입니다. 각에는 접두사 및 후 위 버전이 있습니다.

`<assignable-expression><operator>`
`<operator><assignable-expression>`

할당 가능한 식은 숫자 여야 하며 숫자로 변환할 수 있어야 합니다.

## <a name="assigning-values"></a>값 할당

변수는 값을 저장 하는 메모리 공간 이라고 합니다. 할당 연산자를 사용 하 여 변수에 값을 저장 `=` 합니다. 새 값은 변수의 기존 값을 대체 하거나 기존 값에 새 값을 추가할 수 있습니다.

기본 할당 연산자는 등호 `=` `(ASCII 61)` 입니다. 예를 들어 다음 문은 변수에 값 PowerShell을 할당 합니다 `$MyShell` .

```powershell
$MyShell = "PowerShell"
```

PowerShell에서 변수에 값을 할당 하는 경우 변수가 아직 없는 경우 생성 됩니다. 예를 들어 다음 두 대입문 중 첫 번째 문은 변수를 만들고 `$a` 값으로 6을 할당 `$a` 합니다. 두 번째 대입문은 값 12를에 할당 합니다 `$a` . 첫 번째 문은 새 변수를 만듭니다. 두 번째 문은 해당 값만 변경 합니다.

```powershell
$a = 6
$a = 12
```

변환 하지 않는 한 PowerShell의 변수는 특정 데이터 형식이 아닙니다.
변수에 하나의 개체만 포함 된 경우 변수는 해당 개체의 데이터 형식을 사용 합니다. 변수에 개체 컬렉션이 포함 된 경우 변수는 System.object 데이터 형식입니다. 따라서 모든 형식의 개체를 컬렉션에 할당할 수 있습니다. 다음 예제에서는 오류를 생성 하지 않고 프로세스 개체, 서비스 개체, 문자열 및 정수를 변수에 추가할 수 있음을 보여 줍니다.

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

할당 연산자는 `=` 파이프라인 연산자 보다 우선 순위가 낮으므로 `|` 명령 파이프라인의 결과를 변수에 할당 하는 데는 괄호가 필요 하지 않습니다. 예를 들어 다음 명령은 컴퓨터의 서비스를 정렬 한 다음 정렬 된 서비스를 변수에 할당 합니다 `$a` .

```powershell
$a = Get-Service | Sort-Object -Property name
```

다음 예제와 같이 문에 의해 생성 된 값을 변수에 할당할 수도 있습니다.

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

이 예에서는 `$a` 의 값이 0 보다 작은 경우 변수에 0을 할당 `$b` 합니다. `$b` `$a` 의 값 `$b` 이 0 보다 작지 않으면의 값을에 할당 합니다.

### <a name="the-assignment-operator"></a>할당 연산자

대입 연산자는 `=` 변수에 값을 할당 합니다. 변수에 이미 값이 있으면 대입 연산자는 `=` 경고 없이 값을 대체 합니다.

다음 문은 정수 값 6을 변수에 할당 합니다 `$a` .

```powershell
$a = 6
```

변수에 문자열 값을 할당 하려면 다음과 같이 문자열 값을 따옴표로 묶습니다.

```powershell
$a = "baseball"
```

변수에 배열 (다중 값)을 할당 하려면 다음과 같이 값을 쉼표로 구분 합니다.

```powershell
$a = "apple", "orange", "lemon", "grape"
```

변수에 해시 테이블을 할당 하려면 PowerShell에서 표준 해시 테이블 표기법을 사용 합니다. `@`세미콜론으로 구분 되 고 중괄호로 묶인 키/값 쌍이 뒤에 오도록 기호를 입력 `;` `{ }` 합니다. 예를 들어 변수에 해시 테이블을 할당 하려면 `$a` 다음을 입력 합니다.

```powershell
$a = @{one=1; two=2; three=3}
```

16 진수 값을 변수에 할당 하려면 값 앞에을 붙입니다 `0x` .
PowerShell에서는 16 진수 값 (0x10)을 10 진수 값 (이 경우 16)으로 변환 하 고 해당 값을 `$a` 변수에 할당 합니다. 예를 들어 변수에 0x10 값을 할당 하려면 `$a` 다음을 입력 합니다.

```powershell
$a = 0x10
```

변수에 지 수 값을 할당 하려면 루트 번호, 문자 `e` 및 10의 배수를 나타내는 숫자를 입력 합니다. 예를 들어 1000의 거듭제곱 3.1415 값을 변수에 할당 하려면 다음을 입력 합니다 `$a` .

```powershell
$a = 3.1415e3
```

또한 PowerShell `KB` 에서는 킬로바이트, 메가바이트 `MB` 및 기가바이트를 `GB` 바이트로 변환할 수 있습니다. 예를 들어 변수에 10kb 값을 할당 하려면 `$a` 다음을 입력 합니다.

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a>더하기 연산자 별 할당

더하기 연산자 대입 연산자는 `+=` 변수의 값을 증가 시키거나 지정 된 값을 기존 값에 추가 합니다. 작업은 변수에 숫자 또는 문자열 형식이 있는지 여부와 변수에 단일 값 (스칼라) 또는 여러 값 (컬렉션)이 포함 되어 있는지 여부에 따라 달라 집니다.

`+=`연산자는 두 개의 작업을 결합 합니다. 먼저,을 추가 하 고 할당 합니다.
따라서 다음 문은 동일 합니다.

```powershell
$a += 2
$a = ($a + 2)
```

변수에 단일 숫자 값이 포함 된 경우 연산자는 `+=` 연산자의 우변에 있는 양만큼 기존 값을 증가 시킵니다. 그런 다음 연산자는 결과 값을 변수에 할당 합니다. 다음 예에서는 연산자를 사용 하 여 `+=` 변수 값을 늘리는 방법을 보여 줍니다.

```powershell
$a = 4
$a += 2
$a
```

```
6
```

변수의 값이 문자열인 경우 연산자의 오른쪽에 있는 값은 다음과 같이 문자열에 추가 됩니다.

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

변수의 값이 배열인 경우 `+=` 연산자는 연산자의 오른쪽에 있는 값을 배열에 추가 합니다. 캐스팅을 통해 배열이 명시적으로 형식화 되지 않은 경우 다음과 같이 모든 형식의 값을 배열에 추가할 수 있습니다.

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

를 갖는

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

변수 값이 해시 테이블인 경우 연산자는 `+=` 연산자의 오른쪽에 있는 값을 해시 테이블에 추가 합니다. 그러나 해시 테이블에 추가할 수 있는 유일한 형식은 다른 해시 테이블 이기 때문에 다른 모든 할당은 실패 합니다.

예를 들어 다음 명령은 변수에 해시 테이블을 할당 `$a` 합니다.
그런 다음 연산자를 사용 하 여 기존 해시 테이블 `+=` 에 다른 해시 테이블을 추가 하 여 기존 해시 테이블에 새 키/값 쌍을 효과적으로 추가 합니다.
출력에 표시 된 것 처럼이 명령은 성공 합니다.

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

다음 명령은 변수의 해시 테이블에 "1" 정수를 추가 하려고 시도 합니다 `$a` . 이 명령은 실패 합니다.

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a>빼기 연산자로 할당

빼기로 할당 연산자는 `-=` 연산자의 우변에 지정 된 값으로 변수 값을 감소 시킵니다. 이 연산자는 문자열 변수와 함께 사용할 수 없으며 컬렉션에서 요소를 제거 하는 데 사용할 수 없습니다.

`-=`연산자는 두 개의 작업을 결합 합니다. 먼저를 빼고를 할당 합니다. 따라서 다음 문은 동일 합니다.

```powershell
$a -= 2
$a = ($a - 2)
```

다음 예에서는 연산자를 사용 하 여 변수 값을 줄이는 방법을 보여 줍니다 `-=` .

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

`-=`할당 연산자를 사용 하 여 숫자 배열의 멤버 값을 줄일 수도 있습니다. 이렇게 하려면 변경 하려는 배열 요소의 인덱스를 지정 합니다. 다음 예제에서는 배열의 세 번째 요소 (요소 2)의 값이 1 씩 감소 합니다.

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

연산자를 사용 하 여 변수 값을 삭제할 수는 없습니다 `-=` . 변수에 할당 된 모든 값을 삭제 하려면 [Clear 항목](xref:Microsoft.PowerShell.Management.Clear-Item) 또는 [clear-variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) cmdlet을 사용 하 여 또는 값을 `$null` 변수에 할당 `""` 합니다.

```powershell
$a = $null
```

배열에서 특정 값을 삭제 하려면 배열 표기법을 사용 하 여 값을 `$null` 특정 항목에 할당 합니다. 예를 들어 다음 문은 배열에서 두 번째 값 (인덱스 위치 1)을 삭제 합니다.

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

변수를 삭제 하려면 [제거-변수](xref:Microsoft.PowerShell.Utility.Remove-Variable) cmdlet을 사용 합니다. 이 메서드는 변수가 특정 데이터 형식으로 명시적으로 캐스팅 되 고 형식화 되지 않은 변수를 원하는 경우에 유용 합니다. 다음 명령은 변수를 삭제 합니다 `$a` .

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a>곱하기 연산자에의 한 할당

곱하기 연산자에의 한 할당은 `*=` 숫자 값을 곱하고 변수의 문자열 값에 대 한 지정 된 수의 복사본을 추가 합니다.

변수에 단일 숫자 값이 포함 된 경우 해당 값은 연산자의 우변에 있는 값을 곱합니다. 예를 들어 다음 예제에서는 연산자를 사용 하 여 `*=` 변수 값을 곱하는 방법을 보여 줍니다.

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

이 경우 `*=` 연산자는 두 개의 작업을 결합 합니다. 먼저를 곱한 다음 할당 합니다. 따라서 다음 문은 동일 합니다.

```powershell
$a *= 2
$a = ($a * 2)
```

변수에 문자열 값이 포함 된 경우 PowerShell은 다음과 같이 지정 된 수의 문자열을 값에 추가 합니다.

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

배열의 요소를 곱하려면 인덱스를 사용 하 여 곱할 요소를 식별 합니다. 예를 들어 다음 명령은 배열 (인덱스 위치 0)의 첫 번째 요소를 2로 곱합니다.

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a>나누기 연산자에의 한 할당

나누기 별 대입 연산자는 `/=` 숫자 값을 연산자의 우변에 지정 된 값으로 나눕니다. 연산자는 문자열 변수와 함께 사용할 수 없습니다.

`/=`연산자는 두 개의 작업을 결합 합니다. 첫째,이를 나누고 할당 합니다. 따라서 다음 두 문은 동일 합니다.

```powershell
$a /= 2
$a = ($a / 2)
```

예를 들어 다음 명령은 연산자를 사용 하 여 `/=` 변수 값을 나눕니다.

```powershell
$a = 8
$a /=2
$a
```

```
4
```

배열의 요소를 나누려면 인덱스를 사용 하 여 변경 하려는 요소를 식별 합니다. 예를 들어 다음 명령은 배열의 두 번째 요소 (인덱스 위치 1)를 2로 나눕니다.

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a>모듈러스 연산자에의 한 할당

모듈러스 연산자의 대입 연산자는 `%=` 변수의 값을 연산자의 우변에 있는 값으로 나눕니다. 그런 다음 `%=` 연산자는 나머지 (모듈러스 라고 함)를 변수에 할당 합니다. 변수에 단일 숫자 값이 포함 된 경우에만이 연산자를 사용할 수 있습니다. 변수에 문자열 변수나 배열이 포함 된 경우에는이 연산자를 사용할 수 없습니다.

`%=`연산자는 두 개의 작업을 결합 합니다. 먼저 나머지를 나누고 결정 한 다음 나머지를 변수에 할당 합니다. 따라서 다음 문은 동일 합니다.

```powershell
$a %= 2
$a = ($a % 2)
```

다음 예제에서는 연산자를 사용 하 여 몫의 모듈러스를 저장 하는 방법을 보여 줍니다 `%=` .

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a>증가 및 감소 연산자

증가 연산자는 `++` 변수의 값을 1 씩 늘립니다. 단순 문에서 increment 연산자를 사용 하면 값이 반환 되지 않습니다. 결과를 보려면 다음과 같이 변수 값을 표시 합니다.

```powershell
$a = 7
++$a
$a
```

```
8
```

값을 강제로 반환 하려면 다음과 같이 변수와 연산자를 괄호로 묶습니다.

```powershell
$a = 7
(++$a)
```

```
8
```

증가 연산자는 변수 앞 (접두사) 이나 뒤 (후)에 배치할 수 있습니다. 연산자의 전위 버전은 다음과 같이 문에 값이 사용 되기 전에 변수를 증가 시킵니다.

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

연산자의 후 위 버전은 해당 값이 문에서 사용 된 후 변수를 증가 시킵니다. 다음 예에서는 `$c` `$a` 값이 변경 전에에 할당 되기 때문에 및 변수의 값이 다릅니다 `$c` `$a` .

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

감소 연산자는 `--` 변수의 값을 1만 큼 줄입니다. 증가 연산자와 마찬가지로 간단한 문에서 연산자를 사용 하는 경우 값이 반환 되지 않습니다. 다음과 같이 괄호를 사용 하 여 값을 반환 합니다.

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

연산자의 전위 버전은 다음과 같이 문에 값이 사용 되기 전에 변수를 감소 시킵니다.

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

연산자의 후 위 버전은 해당 값이 문에 사용 된 후 변수를 감소 시킵니다. 다음 예에서는 `$d` `$a` 값이 변경 전에에 할당 되기 때문에 및 변수의 값이 다릅니다 `$d` `$a` .

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a>Microsoft .NET Framework 형식

기본적으로 변수에 값이 하나만 있는 경우 변수에 할당 된 값은 변수의 데이터 형식을 결정 합니다. 예를 들어 다음 명령은 "Integer" (system.string) 형식의 변수를 만듭니다.

```powershell
$a = 6
```

변수의 .NET Framework 형식을 찾으려면 다음과 같이 **GetType** 메서드와 해당 **FullName** 속성을 사용 합니다. 메서드 호출에 인수가 없더라도 **GetType** 메서드 이름 뒤에 괄호를 포함 해야 합니다.

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

문자열을 포함 하는 변수를 만들려면 변수에 문자열 값을 할당 합니다. 값이 문자열 임을 나타내려면 다음과 같이 따옴표로 묶으십시오.

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

변수에 할당 된 첫 번째 값이 문자열인 경우 PowerShell은 모든 작업을 문자열 작업으로 처리 하 고 새 값을 문자열에 캐스팅 합니다.
이는 다음 예제에서 발생 합니다.

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

첫 번째 값이 정수인 경우 PowerShell은 모든 작업을 정수 연산으로 처리 하 고 새 값을 정수로 캐스팅 합니다. 이는 다음 예제에서 발생 합니다.

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

변수 이름이 나 첫 번째 할당 값 앞에 있는 대괄호 안에 형식 이름을 배치 하 여 새 스칼라 변수를 .NET Framework 형식으로 캐스팅할 수 있습니다. 변수를 캐스팅할 때 변수에 저장할 수 있는 데이터 형식을 결정할 수 있습니다. 또한 변수를 조작할 때 변수의 동작 방식을 결정할 수 있습니다.

예를 들어 다음 명령은 변수를 문자열 형식으로 캐스팅 합니다.

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

다음 예에서는 변수를 캐스팅 하는 대신 첫 번째 값을 캐스팅 합니다.

```powershell
$a = [string]27
```

변수를 특정 형식으로 캐스팅 하는 경우 일반적인 규칙은 값이 아니라 변수를 캐스팅 하는 것입니다. 그러나 해당 값을 새 데이터 형식으로 변환할 수 없는 경우에는 기존 변수의 데이터 형식을 다시 캐스팅 수 없습니다. 데이터 형식을 변경 하려면 다음과 같이 값을 바꾸어야 합니다.

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

또한 변수 이름 앞에 데이터 형식을 사용 하는 경우 다른 데이터 형식을 지정 하 여 명시적으로 형식을 재정의 하지 않으면 해당 변수의 형식이 잠깁니다. 기존 형식과 호환 되지 않는 값을 할당 하려고 하는데 형식을 명시적으로 재정의 하지 않는 경우 PowerShell에서 다음 예제와 같이 오류를 표시 합니다.

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

PowerShell에서 배열의 여러 항목을 포함 하는 변수의 데이터 형식은 단일 항목을 포함 하는 변수의 데이터 형식과는 다르게 처리 됩니다. 데이터 형식이 배열 변수에 특별히 할당 되지 않은 경우 데이터 형식은 항상 `System.Object []` 입니다. 이 데이터 형식은 배열에만 적용 됩니다.

경우에 따라 다른 형식을 지정 하 여 기본 형식을 재정의할 수 있습니다. 예를 들어 다음 명령은 변수를 배열 형식으로 캐스팅 합니다 `string []` .

```powershell
[string []] $a = "one", "two", "three"
```

PowerShell 변수는 모든 .NET Framework 데이터 형식일 수 있습니다. 또한 현재 프로세스에서 사용할 수 있는 정규화 된 .NET Framework 데이터 형식을 할당할 수 있습니다. 예를 들어 다음 명령은 `System.DateTime` 데이터 형식을 지정 합니다.

```powershell
[System.DateTime]$a = "5/31/2005"
```

변수에는 데이터 형식에 맞는 값이 할당 됩니다 `System.DateTime` . 변수의 값은 `$a` 다음과 같습니다.

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a>여러 변수 할당

PowerShell에서 단일 명령을 사용 하 여 여러 변수에 값을 할당할 수 있습니다. 할당 값의 첫 번째 요소는 첫 번째 변수에 할당 되 고 두 번째 요소는 두 번째 변수에 할당 되며 세 번째 요소는 세 번째 변수에 할당 됩니다. 예를 들어 다음 명령은 변수에 값 1을 할당 하 고 값 2를 변수에 할당 `$a` 한 다음 `$b` 값 3을 변수에 할당 합니다 `$c` .

```powershell
$a, $b, $c = 1, 2, 3
```

할당 값에 변수 보다 많은 요소가 포함 된 경우 나머지 값은 모두 마지막 변수에 할당 됩니다. 예를 들어 다음 명령은 3 개의 변수와 5 개의 값을 포함 합니다.

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

따라서 PowerShell은 변수에 값 1을 할당 하 `$a` 고 값 2를 `$b` 변수에 할당 합니다. 값 3, 4 및 5를 `$c` 변수에 할당 합니다.
변수의 값을 `$c` 다른 세 변수에 할당 하려면 다음 형식을 사용 합니다.

```powershell
$d, $e, $f = $c
```

이 명령은 값 3을 변수에 할당 하 고, 값 4를 변수에 할당 하 `$d` `$e` 고, 값 5를 변수에 할당 `$f` 합니다.

할당 값에 변수 보다 더 작은 요소가 포함 된 경우 끝에 있는 나머지 모든 변수에는 값이 할당 되지 않습니다. 예를 들어 다음 명령에는 세 개의 변수와 두 개의 값이 있습니다.

```powershell
$a, $b, $c = 1, 2
```

따라서 PowerShell은 변수에 값 1을 할당 하 `$a` 고 값 2를 `$b` 변수에 할당 합니다. 변수에 값을 할당 하지 않습니다 `$c` .

변수를 연결 하 여 여러 변수에 단일 값을 할당할 수도 있습니다. 예를 들어 다음 명령은 네 가지 변수에 모두 "3" 값을 할당 합니다.

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a>변수 관련 cmdlet

할당 연산을 사용 하 여 변수 값을 설정 하는 것 외에도, [집합 변수](xref:Microsoft.PowerShell.Utility.Set-Variable) cmdlet을 사용할 수 있습니다. 예를 들어 다음 명령은를 사용 하 여 `Set-Variable` 1, 2, 3의 배열을 `$a` 변수에 할당 합니다.

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a>참고 항목

[about_Arrays](about_Arrays.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Variables](about_Variables.md)

[Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
