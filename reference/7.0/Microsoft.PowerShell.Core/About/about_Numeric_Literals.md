---
description: 정수 및 실수 리터럴은 모두 형식 및 승수 접미사를 사용할 수 있습니다.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 숫자 리터럴 정보
ms.openlocfilehash: f9d23a37c06c8285c23328ea8ddcebf8d6caae9e
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354731"
---
# <a name="about-numeric-literals"></a>숫자 리터럴 정보

숫자 리터럴에는 integer와 real의 두 종류가 있습니다. 둘 다 형식 및 승수 접미사를 사용할 수 있습니다.

## <a name="integer-literals"></a>정수 리터럴

정수 리터럴은 10 진수, 16 진수 또는 이진 표기법으로 작성할 수 있습니다.
16 진수 리터럴에는 접두사가 `0x` 있고, 이진 리터럴의 접두사는 `0b` 10 진수와 구분 됩니다.

정수 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.

| 접미사 |            의미             |          참고           |
| ------ | ------------------------------ | ----------------------- |
| y      | 부호 있는 바이트 데이터 형식          | PowerShell 6.2에 추가 됨 |
| uy     | unsigned byte 데이터 형식        | PowerShell 6.2에 추가 됨 |
| 초      | short 데이터 형식                | PowerShell 6.2에 추가 됨 |
| us     | unsigned short 데이터 형식       | PowerShell 6.2에 추가 됨 |
| l      | long 데이터 형식                 |                         |
| u      | unsigned int 또는 long 데이터 형식 | PowerShell 6.2에 추가 됨 |
| ul     | unsigned long 데이터 형식        | PowerShell 6.2에 추가 됨 |
| n      | BigInteger 데이터 형식           | PowerShell 7.0에 추가 됨 |
| kb     | kb 승수            |                         |
| mb     | 메가바이트 승수            |                         |
| 35     | gb 승수            |                         |
| 1tb     | 테라바이트 승수            |                         |
| pb     | 페타바이트 승수            |                         |

정수 리터럴의 형식은 해당 값, 형식 접미사 및 숫자 승수 접미사로 결정 됩니다.

형식 접미사가 없는 정수 리터럴의 경우:

- 값을 형식으로 나타낼 수 있으면 해당 `[int]` 형식입니다.
- 그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[long]` 형식입니다.
- 그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[decimal]` 형식입니다.
- 그렇지 않으면 형식으로 표현 됩니다 `[double]` .

형식 접미사가 있는 정수 리터럴의 경우:

- 형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[uint]` 해당 형식은 `[uint]` 입니다.
- 형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[ulong]` 해당 형식은 `[ulong]` 입니다.
- 해당 값을 지정 된 형식으로 나타낼 수 있으면 해당 형식입니다.
- 그렇지 않으면 리터럴의 형식이 잘못 됩니다.

## <a name="real-literals"></a>real 리터럴

실수 리터럴은 소수 표기법 으로만 쓸 수 있습니다. 이 표기법은 지 수 부분을 사용 하 여 소수점이 나 과학적 표기법 뒤에 소수 값을 포함할 수 있습니다.

지 수 부분에는 ' e ' 뒤에 선택적 기호 (+/-)와 지 수를 나타내는 숫자가 포함 됩니다. 예를 들어 리터럴 값은 `1e2` 숫자 값 100와 같습니다.

실제 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.

| 접미사 |       의미       |
| ------ | ------------------- |
| 일      | decimal 데이터 형식   |
| kb     | kb 승수 |
| mb     | 메가바이트 승수 |
| 35     | gb 승수 |
| 1tb     | 테라바이트 승수 |
| pb     | 페타바이트 승수 |

실수 리터럴의 두 가지 종류는 double과 decimal입니다. 이러한 숫자는 각각 decimal 형식 접미사의 유무에 따라 표시 됩니다. PowerShell은 값의 리터럴 표현을 지원 하지 않습니다 `[float]` . Double 실수 리터럴의 형식은 `[double]` 입니다. Decimal 실수 리터럴의 형식은 `[decimal]` 입니다.
Decimal 실수 리터럴의 소수 부분에 있는 뒤에 오는 0은 중요 합니다.

실제 리터럴의 지 수-부분 숫자 값 `[double]` 이 지원 되는 최소값 보다 작은 경우 해당 `[double]` 실수 리터럴의 값은 0입니다. 실제 리터럴의 지 수-부분 숫자 값 `[decimal]` 이 지원 되는 최소값 보다 작은 경우 리터럴의 형식이 잘못 됩니다. 또는 실제 리터럴의 지 수-부분 숫자 값 `[double]` `[decimal]` 이 지원 되는 최대값 보다 큰 경우 리터럴의 형식이 잘못 됩니다.

> [!NOTE]
> 구문을 사용 하 여 이중 실제 리터럴에 long 형식 접미사를 사용할 수 있습니다.
> PowerShell은이 사례를 값이 형식으로 표현 되는 정수 리터럴로 처리 `[long]` 합니다. 이 기능은 이전 버전의 PowerShell과의 호환성을 위해 유지 되었습니다. 그러나 프로그래머는이 형식의 정수 리터럴을 사용 하지 않는 것이 좋습니다 .이는 리터럴의 실제 값을 쉽게 모호 하 게 만들 수 있기 때문입니다. 예를 들어에는 값 `1.2L` 이 1이 고 값이 `1.2345e1L` 12이 고 `1.2345e-5L` 값이 0 이면 해당 값 중 어느 것도 명확 하지 않습니다.

## <a name="numeric-multipliers"></a>숫자 승수

편의를 위해 정수 및 실수 리터럴은 숫자 승수를 포함할 수 있으며이는 일반적으로 사용 되는 2의 거듭제곱 집합 중 하나를 나타냅니다. 숫자 승수는 대 문자와 소문자를 조합 하 여 쓸 수 있습니다.

승수 접미사는 형식 접미사와 함께 사용할 수 있지만 형식 접미사 뒤에 있어야 합니다. 예를 들어 리터럴의 `100gbL` 형식이 잘못 되었지만 리터럴이 `100Lgb` 유효 합니다.

승수에서 지정 하는 숫자 형식에 사용할 수 있는 값을 초과 하는 값을 만드는 경우 리터럴의 형식이 잘못 됩니다. 예를 들어, `1usgb` 값 `1gb` 이 접미사로 지정 된 형식에 허용 되는 값 보다 크므로 리터럴의 형식이 잘못 되었습니다 `[ushort]` `us` .

### <a name="multiplier-examples"></a>승수 예

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a>숫자 형식 액셀러레이터

PowerShell은 다음과 같은 유형 가속기를 지원 합니다.

| 액셀러레이터 |         참고         |           Description            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | 바이트 (부호 없음)                  |
| `[sbyte]`   |                      | 바이트 (부호 있음)                    |
| `[Int16]`   |                      | 16 비트 정수                   |
| `[short]`   | 별칭 `[int16]`  | 16 비트 정수                   |
| `[UInt16]`  |                      | 16 비트 정수 (부호 없음)        |
| `[ushort]`  | 별칭 `[uint16]` | 16 비트 정수 (부호 없음)        |
| `[Int32]`   |                      | 32비트 정수                   |
| `[int]`     | 별칭 `[int32]`  | 32비트 정수                   |
| `[UInt32]`  |                      | 32 비트 정수 (부호 없음)        |
| `[uint]`    | 별칭 `[uint32]` | 32 비트 정수 (부호 없음)        |
| `[Int64]`   |                      | 64비트 정수                   |
| `[long]`    | 별칭 `[int64]`  | 64비트 정수                   |
| `[UInt64]`  |                      | 64 비트 정수 (부호 없음)        |
| `[ulong]`   | 별칭 `[uint64]` | 64 비트 정수 (부호 없음)        |
| `[bigint]`  |                      | [BigInteger 구조체][bigint] 를 참조 하세요.  |
| `[single]`  |                      | 단일 정밀도 부동 소수점  |
| `[float]`   | 별칭 `[single]` | 단일 정밀도 부동 소수점  |
| `[double]`  |                      | 배정밀도 부동 소수점  |
| `[decimal]` |                      | 128 비트 부동 소수점           |

> [!NOTE]
> PowerShell 6.2에 추가 된 형식 액셀러레이터는 `[short]` , `[ushort]` , `[uint]` , `[ulong]` 입니다.

## <a name="examples"></a>예제

다음 표에서는 숫자 리터럴의 몇 가지 예를 포함 하 고 해당 형식 및 값을 나열 합니다.

|   번호     |  Type      |    값     |
| -----------: | ---------- | -----------: |
|         100  | Int32      |          100 |
|        100u  | UInt32     |          100 |
|        100D  | Decimal    |          100 |
|        100l  | Int64      |          100 |
|       100uL  | UInt64     |          100 |
|       100us  | UInt16     |          100 |
|       100uy  | Byte       |          100 |
|        100y  | SByte      |          100 |
|         1e2  | Double     |          100 |
|        1. e2  | Double     |          100 |
|       0x1e2  | Int32      |          482 |
|      0x1e2L  | Int64      |          482 |
|      0x1e2D  | Int32      |         7725 |
|        482D  | Decimal    |          482 |
|       482gb  | Int64      | 517543559168 |
|       482ngb | BigInteger | 517543559168 |
|    0x1e2lgb  | Int64      | 517543559168 |
|   0b1011011  | Int32      |           91 |
|  0xFFFFFFFF  | Int32      |           -1 |
| -0xFFFFFFFF  | Int32      |            1 |
| 0xFFFFFFFFu  | UInt32     |   4294967295 |

### <a name="working-with-binary-or-hexadecimal-numbers"></a>이진 또는 16 진수를 사용 하 여 작업

접미사가 지정 된 경우에만 너무 큼 이진 또는 16 진수 리터럴은 `[bigint]` 구문 분석에 실패 하는 것이 아니라로 반환 될 수 있습니다 `n` . 하지만 부호 비트는 여전히 범위 내 `[decimal]` 에서 적용 됩니다.

- 이진 문자열이 8 비트 long의 배수가 면 가장 높은 비트가 부호 비트로 취급 됩니다.
- 길이가 8 인 16 진수 문자열의 첫 번째 숫자가 8 이상인 경우 숫자는 음수로 처리 됩니다.

이진 및 16 진수 리터럴에 부호 없는 접미사를 지정 하면 부호 비트가 무시 됩니다. 예를 들어 `0xFFFFFFFF` 는 `-1` 를 반환 하지만 `0xFFFFFFFFu` 4294967295의를 반환 합니다 `[uint]::MaxValue` .

을 사용 하 여 리터럴을 접두사로 사용 `0` 하면이를 무시 하 고 unsigned로 처리 됩니다.
예를 들면 `0b011111111`과 다음과 같습니다. 이는 범위의 리터럴을 사용할 때 `[bigint]` 와 접미사를 결합할 수 없기 때문에 필요할 수 있습니다 `u` `n` .

접두사를 사용 하 여 이진 및 16 진 리터럴을 부정할 수도 있습니다 `-` . 그러면 부호 비트가 허용 되므로 양수가 반환 될 수 있습니다.

BigInteger-접미사 숫자에는 부호 비트가 허용 됩니다.

- BigInteger hex는 부호 비트로 8 자의 길이가 배수 인 리터럴의 상위 비트를 처리 합니다. 길이는 접두사 또는 접미사를 포함 하지 않습니다 `0x` .
- BigInteger는 96 및 128 문자에서 부호 비트를 허용 하 고,은 8 자 마다 허용 합니다.

### <a name="commands-that-look-like-numeric-literals"></a>숫자 리터럴과 같은 명령

유효한 숫자 리터럴 처럼 보이는 명령은 호출 연산자 ()를 사용 하 여 실행 해야 합니다 `&` . 그렇지 않으면 숫자로 해석 됩니다. 올바른 구문이 있는 형식이 잘못 된 리터럴은 `1usgb` 다음과 같은 오류가 발생 합니다.

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

그러나 잘못 된 구문을 사용 하는 잘못 된 형식의 리터럴은 `1gbus` 표준 기본 문자열로 해석 되 고 명령이 호출 될 수 있는 컨텍스트에서 유효한 명령 이름으로 해석 될 수 있습니다.

### <a name="access-properties-and-methods-of-numeric-objects"></a>숫자 개체의 속성 및 메서드 액세스

숫자 리터럴의 멤버에 액세스 하려면 리터럴을 괄호로 묶어야 하는 경우가 있습니다.

- 리터럴에 소수점이 없습니다.
- 리터럴의 소수점 뒤에 숫자가 없습니다.
- 리터럴에 접미사가 없습니다.

예를 들어 다음 예제는 실패 합니다.

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

다음 예제가 작동 합니다.

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

PowerShell 파서는 숫자 리터럴이 끝나고 **GetType** 메서드가 시작 되는 위치를 결정할 수 있기 때문에 처음 두 예제는 괄호 안에 리터럴 값을 포함 하지 않고 작동 합니다.

## <a name="how-powershell-parses-numeric-literals"></a>PowerShell에서 숫자 리터럴을 구문 분석 하는 방법

PowerShell v 7.0은 새 기능을 사용할 수 있도록 숫자 리터럴이 구문 분석 되는 방식을 변경 했습니다.

### <a name="parsing-real-numeric-literals"></a>실수 리터럴 구문 분석

리터럴에 소수점이 나 e 표기법이 포함 된 경우 리터럴 문자열은 실수를 구문 분석 합니다.

- 10 진수 접미사가 있으면에 직접 표시 됩니다 `[decimal]` .
- 또는를로 구문 분석 하 `[Double]` 고 값에 승수를 적용 합니다. 그런 다음 형식 접미사를 확인 하 고 적절 한 형식으로 캐스팅 하려고 시도 합니다.
- 문자열에 형식 접미사가 없으면로 구문 분석 `[Double]` 합니다.

### <a name="paring-integer-numeric-literals"></a>Paring 정수 숫자 리터럴

정수 형식 리터럴은 다음 단계를 사용 하 여 구문 분석 됩니다.

1. 기 하 형식 결정
   - 이진 형식의 경우로 구문 분석 `[BigInteger]` 합니다.
   - 16 진수 형식의 경우 `[BigInteger]` 값이 또는 범위에 있을 때 원래 동작을 유지 하기 위해 특수 casies 사용 하 여로 구문 분석 `[int]` `[long]` 합니다.
   - Binary와 hex가 둘 다 없는 경우는 정상적으로로 구문 분석 `[BigInteger]` 됩니다.
2. 캐스트를 시도 하기 전에 승수 값을 적용 하 여 형식 범위를 오버플로 없이 적절히 확인할 수 있도록 합니다.
3. 유형 접미사를 확인 합니다.
   - 형식 범위를 확인 하 고 해당 형식으로 구문 분석을 시도 합니다.
   - 접미사를 사용 하지 않는 경우 값은 다음 순서로 범위가 결정 됩니다. 그러면 첫 번째 성공한 테스트가 숫자의 형식을 결정 합니다.
     - `[int]`
     - `[long]`
     - `[decimal]` (기본-10 리터럴 전용)
     - `[double]` (기본-10 리터럴 전용)
   - 값이 `[long]` 16 진수 및 이진 숫자 범위를 벗어나면 구문 분석이 실패 합니다.
   - 값이 `[double]` base 10 number의 범위를 벗어나면 구문 분석이 실패 합니다.
   - `n`리터럴을로 구문 분석 하려면 접미사를 사용 하 여 더 높은 값을 명시적으로 작성 해야 합니다 `BigInteger` .

### <a name="parsing-large-value-literals"></a>대량 값 리터럴 구문 분석

이전에는 더 높은 정수 값이 다른 형식으로 캐스팅 되기 전에 double로 구문 분석 되었습니다. 이로 인해 더 높은 범위의 전체 자릿수가 손실 됩니다. 예를 들면 다음과 같습니다.

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

이 문제를 방지 하려면 값을 문자열로 쓴 다음 변환 해야 합니다.

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

PowerShell 7.0에서는 접미사를 사용 해야 합니다 `N` .

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

또한 및 사이의 값은 `[ulong]::MaxValue` `[decimal]::MaxValue` `D` 정확도를 유지 하기 위해 10 진수 접미사를 사용 하 여 표시 되어야 합니다. 접미사가 없으면 이러한 값은 `[Double]` 실제 구문 분석 모드를 사용 하 여 구문 분석 됩니다.

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
