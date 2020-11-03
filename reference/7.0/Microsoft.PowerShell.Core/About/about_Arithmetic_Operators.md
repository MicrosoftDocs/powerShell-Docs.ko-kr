---
description: PowerShell에서 산술 연산을 수행 하는 연산자에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_arithmetic_operators
ms.openlocfilehash: 5c9118eaa166beffc9d7a24f77a730d637a36a00
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222426"
---
# <a name="about-arithmetic-operators"></a>산술 연산자 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 산술 연산을 수행 하는 연산자에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

산술 연산자는 숫자 값을 계산 합니다. 하나 이상의 산술 연산자를 사용 하 여 값을 추가, 빼기, 곱하기 및 나누기 하 고 나누기 연산의 나머지 (모듈러스)를 계산할 수 있습니다.

또한 더하기 연산자 ( `+` ) 및 곱하기 연산자 ( `*` )는 문자열, 배열 및 해시 테이블 에서도 작동 합니다. 더하기 연산자는 입력을 연결 합니다. 곱하기 연산자는 입력의 여러 복사본을 반환 합니다. 산술 문에서 개체 형식을 혼합할 수도 있습니다. 문을 계산 하는 데 사용 되는 메서드는 식에서 가장 왼쪽에 있는 개체의 형식에 따라 결정 됩니다.

PowerShell 2.0부터 모든 산술 연산자는 64 비트 숫자에 대해 작동 합니다.

PowerShell 3.0부터 `-shr` `-shl` powershell에서 비트 산술 연산을 지원 하기 위해 (shift 오른쪽) 및 (왼쪽 시프트)가 추가 되었습니다.

PowerShell은 다음과 같은 산술 연산자를 지원 합니다.

|연산자|Description                       |예제                      |
|--------|----------------------------------|-----------------------------|
| +      |정수를 추가 합니다. 서로       |`6 + 2`                      |
|        |문자열, 배열 및 해시 테이블 |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |다른 값에서 하나의 값을 뺍니다.  |`6 - 2`                      |
|        |값                             |                             |
| -      |숫자를 음수 값으로 만듭니다.  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |숫자 곱하기 또는 문자열 복사  |`6 * 2`                      |
|        |지정 된 숫자의 및 배열   |`@("!") * 4`                 |
|        |횟수.                         |`"!" * 3`                    |
| /      |두 값을 나눕니다.               |`6 / 2`                      |
| %      |모듈러스-다음의 나머지를 반환 합니다.|`7 % 2`                      |
|        |나누기 연산입니다.             |                             |
|-대역   |비트 AND                       |`5 -band 3`                  |
|-bnot   |비트 NOT                       |`-bnot 5`                    |
|-bor    |비트 OR                        |`5 -bor 0x03`                |
|-bxor   |비트 XOR                       |`5 -bxor 3`                  |
|-shl    |비트를 왼쪽으로 이동 합니다.           |`102 -shl 2`                 |
|-shr    |비트를 오른쪽으로 이동 합니다.          |`102 -shr 2`                 |

비트 연산자는 정수 형식 에서만 작동 합니다.

## <a name="operator-precedence"></a>연산자 우선 순위

PowerShell은 다음과 같은 순서로 산술 연산자를 처리 합니다.

|우선 순위|연산자          |Description                            |
|----------|------------------|---------------------------------------|
|1         | `()`             |괄호                            |
|2         | `-`              |음수 또는 단항 연산자의 경우|
|3         | `*`, `/`, `%`    |곱하기 및 나누기의 경우        |
|4         | `+`, `-`         |더하기 및 빼기           |
|5         | `-band`, `-bnot` |비트 연산                 |
|5         | `-bor`, `-bxor`  |비트 연산                 |
|5         | `-shr`, `-shl`   |비트 연산                 |

PowerShell은 우선 순위 규칙에 따라 왼쪽에서 오른쪽으로 식을 처리 합니다. 다음 예에서는 우선 순위 규칙의 영향을 보여 줍니다.

|식 |결과|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

PowerShell에서 식을 평가 하는 순서는 사용자가 사용한 다른 프로그래밍 및 스크립트 언어와 다를 수 있습니다. 다음 예에서는 복잡 한 대입문을 보여 줍니다.

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

이 예제에서 식은 이전에 `$a++` 계산 됩니다 `$b[$a]` .
`$a++`문은 문에서 사용 된 후의 값을 변경 `$a` `$c[$a++]` 하지만에서 사용 되기 전에를 변경 합니다 `$b[$a]` . 의 변수 `$a` 는 `$b[$a]` `1` 가 아니라 equals입니다 `0` . 따라서 문은가 아닌에 값을 할당 `$b[1]` `$b[0]` 합니다.

위의 코드는 다음과 같습니다.

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a>나누기 및 반올림

나누기 연산의 몫이 정수인 경우 PowerShell은 값을 가장 가까운 정수로 반올림 합니다. 값이 이면 `.5` 가장 가까운 짝수로 반올림 합니다.

다음 예제에서는 가장 가까운 짝수 정수로 반올림 한 결과를 보여 줍니다.

|식      |결과|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

**_5/2_ = 2.5** 은 **2** 로 반올림 됩니다. 그러나 **_7/2_ = 3.5** 은 **4** 로 반올림 됩니다.

클래스를 사용 `[Math]` 하 여 다른 반올림 동작을 가져올 수 있습니다.

|                          식                          | 결과 |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

자세한 내용은 [Math](/dotnet/api/system.math.round) 메서드를 참조 하세요.

## <a name="adding-and-multiplying-non-numeric-types"></a>숫자가 아닌 형식 추가 및 곱하기

숫자, 문자열, 배열 및 해시 테이블을 추가할 수 있습니다. 숫자, 문자열 및 배열을 곱할 수 있습니다. 그러나 해시 테이블은 곱할 수 없습니다.

문자열, 배열 또는 해시 테이블을 추가 하면 요소가 연결 됩니다. 배열 또는 해시 테이블과 같은 컬렉션을 연결 하면 두 컬렉션의 개체를 포함 하는 새 개체가 만들어집니다. 동일한 키가 있는 해시 테이블을 연결 하려고 하면 작업이 실패 합니다.

예를 들어 다음 명령은 두 개의 배열을 만든 후 추가 합니다.

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

다른 형식의 개체에 대해 산술 연산을 수행할 수도 있습니다.
PowerShell에서 수행 하는 작업은 작업에서 가장 왼쪽에 있는 개체의 Microsoft .NET Framework 형식에 의해 결정 됩니다. PowerShell은 작업의 모든 개체를 첫 번째 개체의 .NET Framework 형식으로 변환 하려고 합니다. 개체를 변환 하는 데 성공 하면 첫 번째 개체의 .NET Framework 형식에 적절 한 작업을 수행 합니다. 개체를 변환 하는 데 실패 하면 작업이 실패 합니다.

다음 예에서는 더하기 및 곱하기 연산자를 사용 하는 방법을 보여 줍니다. 다른 개체 유형을 포함 하는 작업 다음을 가정 합니다 `$array = 1,2,3` .

|식       |결과                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |`1`,`2`,`3`,`16`       |
|`$array + "file"`|`1`,`2`,`3`,`file`     |
|`$array * 2`     |`1`,`2`,`3`,`1`,`2`,`3`|
|`"file" * 3`     |`filefilefile`         |

문을 계산 하는 데 사용 되는 메서드는 맨 왼쪽 개체에 의해 결정 되므로 PowerShell에서 더하기 및 곱하기는 엄격 하 게 교환 되지 않습니다. 예를 들어는 `(a + b)` 항상 같지는 않으며 `(b + a)` 항상 같지는 않습니다 `(ab)` `(ba)` .

다음 예에서는이 원칙을 보여 줍니다.

|식   |결과                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |+ 16 + "파일" '                                       |

해시 테이블은 경우에 따라 약간 다릅니다. 추가 된 해시 테이블에 중복 키가 없는 경우에는 해시 테이블을 다른 해시 테이블에 추가할 수 있습니다.

다음 예제에서는 해시 테이블을 서로 추가 하는 방법을 보여 줍니다.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

다음 예에서는 두 해시 테이블에서 키 중 하나가 중복 되기 때문에 오류를 throw 합니다.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

또한 배열에 해시 테이블을 추가할 수 있습니다. 전체 해시 테이블은 배열의 항목이 됩니다.

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

그러나 해시 테이블에 다른 형식을 추가할 수는 없습니다.

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

더하기 연산자가 매우 유용 하지만 할당 연산자를 사용 하 여 해시 테이블 및 배열에 요소를 추가 합니다. 자세한 내용은 [about_assignment_operators](about_Assignment_Operators.md)를 참조 하세요. 다음 예에서는 `+=` 대입 연산자를 사용 하 여 배열에 항목을 추가 합니다.

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a>결과를 수용할 형식 변환

PowerShell은 전체 자릿수를 잃지 않고 결과를 가장 잘 표현 하는 .NET Framework 숫자 형식을 자동으로 선택 합니다. 다음은 그 예입니다. 

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

작업 결과가 형식에 맞지 않는 경우 다음 예제와 같이 결과의 형식이 결과에 맞게 확장 됩니다.

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

결과의 형식은 피연산자 중 하 나와 동일할 필요는 없습니다. 다음 예제에서는 음수 값을 부호 없는 정수로 캐스팅할 수 없으며, 부호 없는 정수가 너무 커서를 캐스팅할 수 없습니다 `Int32` .

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

이 예제에서는 `Int64` 두 형식을 모두 수용할 수 있습니다.

`System.Decimal`예외 형식입니다. 피연산자 중 하나가 Decimal 형식이 면 결과는 Decimal 형식이 됩니다. Decimal 형식에 대해 결과가 너무 크면 Double로 캐스팅 되지 않습니다. 대신 오류가 발생 합니다.

|식               |결과                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a>산술 연산자 및 변수

변수에 산술 연산자를 사용할 수도 있습니다. 연산자는 변수의 값에 대해 작동 합니다. 다음 예에서는 변수를 사용 하 여 산술 연산자를 사용 하는 방법을 보여 줍니다.

| 식                                    |결과      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a>산술 연산자 및 명령

일반적으로 숫자, 문자열 및 배열을 사용 하 여 식에서 산술 연산자를 사용 합니다. 그러나 명령에서 반환 하는 개체 및 해당 개체의 속성을 사용 하 여 산술 연산자를 사용할 수도 있습니다.

다음 예에서는 PowerShell 명령을 사용 하 여 식에서 산술 연산자를 사용 하는 방법을 보여 줍니다.

```powershell
(get-date) + (new-timespan -day 1)
```

괄호 연산자를 통해 `get-date` cmdlet 및 cmdlet 식의 계산을 순서 대로 실행 합니다 `new-timespan -day 1` . 그런 다음 연산자를 사용 하 여 두 결과를 추가 `+` 합니다.

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

위의 식에서 각 프로세스 작업 공간 ()에를 곱하고 그 결과와 비교 하 여 `$_.ws` `2` `50mb` 보다 큰지 확인 합니다.

## <a name="bitwise-operators"></a>비트 연산자

PowerShell은 비트 and ( `-bAnd` ), 포괄적 비트 or 연산자 ( `-bOr` 및 `-bXor` ), 비트 not ()을 비롯 한 표준 비트 연산자를 지원 `-bNot` 합니다.

PowerShell 2.0부터 모든 비트 연산자는 64 비트 정수와 함께 작동 합니다.

PowerShell 3.0부터 `-shr` `-shl` powershell에서 비트 산술 연산을 지원 하기 위해 (shift 오른쪽) 및 (왼쪽 시프트)가 도입 되었습니다.

PowerShell에서 지 원하는 비트 연산자는 다음과 같습니다.

| 연산자 | Description            | 식   | 결과 |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | 비트 AND            | `10 -band 3` | 2      |
| `-bor`   | 비트 OR (포함) | `10 -bor 3`  | 11     |
| `-bxor`  | 비트 or (제외) | `10 -bxor 3` | 9      |
| `-bnot`  | 비트 NOT            | `-bNot 10`   | -11    |
| `-shl`   | 왼쪽으로 이동             | `102 -shl 2` | 408    |
| `-shr`   | Shift + 오른쪽            | `102 -shr 1` | 51     |

비트 연산자는 값의 이진 형식에 대해 작동 합니다. 예를 들어 숫자 10의 비트 구조는 00001010 (1 바이트 기준)이 고 숫자 3의 비트 구조는 00000011입니다. 비트 연산자를 사용 하 여 10과 3을 비교 하는 경우 각 바이트의 개별 비트가 비교 됩니다.

비트 AND 연산에서는 두 입력 비트가 모두 1 인 경우에만 결과 비트가 1로 설정 됩니다.

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

비트 or (포함) 연산에서 입력 비트 중 하나 또는 둘 다가 1 이면 결과 비트는 1로 설정 됩니다. 두 입력 비트가 모두 0으로 설정 된 경우에만 결과 비트가 0으로 설정 됩니다.

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

비트 OR (배타) 연산에서 결과 비트는 1로 설정 됩니다. 한 입력 비트가 1 인 경우에만 1로 설정 됩니다.

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

비트 NOT 연산자는 값의 이진 보수를 생성 하는 단항 연산자입니다. 1은 0으로 설정 되 고 비트 0은 1로 설정 됩니다.

예를 들어, 0의 이진 보수는-1, 부호 없는 최대 정수 (0xffffffff) 및-1의 이진 보수는 0입니다.

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

비트 시프트 왼쪽 작업에서 모든 비트는 "n"이 왼쪽으로 이동 합니다. 여기서 "n"은 오른쪽 피연산자의 값입니다. 0은 한 자리에 삽입 됩니다.

왼쪽 피연산자가 정수 (32 비트) 값인 경우 오른쪽 피연산자의 하위 5 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.

왼쪽 피연산자가 Long (64 비트) 값인 경우 오른쪽 피연산자의 하위 6 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.

|식 |결과|이진 결과|
|-----------|------|-------------|
|`21 -shl 0`|21    |0001 0101    |
|`21 -shl 1`|42    |0010 1010    |
|`21 -shl 2`|84    |0101 0100    |

비트 시프트 오른쪽 작업에서는 모든 비트가 오른쪽으로 "n"을 이동 합니다. 여기서 "n"은 오른쪽 피연산자로 지정 됩니다. 오른쪽 시프트 연산자 (-shr)는 양수 또는 부호 없는 값을 오른쪽으로 이동할 때 왼쪽 맨 위에 0을 삽입 합니다.

왼쪽 피연산자가 정수 (32 비트) 값인 경우 오른쪽 피연산자의 하위 5 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.

왼쪽 피연산자가 Long (64 비트) 값인 경우 오른쪽 피연산자의 하위 6 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.

|식              |결과      |이진     |Hex         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | 21         | 0001 0101 | 0x15       |
|`21 -shr 1`             | 10         | 0000 1010 | 0x0A       |
|`21 -shr 2`             | 5          | 0000 0101 | 0x05       |
|`21 -shr 31`            | 0          | 0000 0000 | 0x00       |
|`21 -shr 32`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 64`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 65`            | 10         | 0000 1010 | 0x0A       |
|`21 -shr 66`            | 5          | 0000 0101 | 0x05       |
|`[int]::MaxValue -shr 1`| 1073741823 |           | 0x3FFFFFFF |
|`[int]::MinValue -shr 1`| -1073741824|           | 0xC0000000 |
|`-1 -shr 1`             | -1         |           | 0xFFFFFFFF |

## <a name="see-also"></a>참고 항목

- [about_arrays](about_Arrays.md)
- [about_assignment_operators](about_Assignment_Operators.md)
- [about_comparison_operators](about_Comparison_Operators.md)
- [about_hash_tables](about_Hash_Tables.md)
- [about_operators](about_Operators.md)
- [about_variables](about_Variables.md)
- [가져오기-날짜](xref:Microsoft.PowerShell.Utility.Get-Date)
- [New-TimeSpan](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
