---
description: 정수 및 실수 리터럴은 모두 형식 및 승수 접미사를 사용할 수 있습니다.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 숫자 리터럴 정보
ms.openlocfilehash: dc1a55dbec1f0de99e06011645e6884b37480233
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354832"
---
# <a name="about-numeric-literals"></a>숫자 리터럴 정보

숫자 리터럴에는 integer와 real의 두 종류가 있습니다. 둘 다 형식 및 승수 접미사를 사용할 수 있습니다.

## <a name="integer-literals"></a>정수 리터럴

정수 리터럴은 10 진수 또는 16 진수 표기법으로 작성할 수 있습니다. 16 진수 리터럴의 접두사는 `0x` 10 진수와 구분 됩니다.

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

승수 접미사는 `u` , `ul` 및 형식 접미사와 함께 사용할 수 있습니다 `l` .

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

### <a name="working-with-other-numeric-types"></a>다른 숫자 형식 작업

다른 숫자 형식으로 작업 하려면 일부 문제가 없는 형식 액셀러레이터를 사용 해야 합니다. 예를 들어, 상위 정수 값은 다른 형식으로 캐스팅 되기 전에 항상 double로 구문 분석 됩니다.

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

값은 double로 구문 분석 되 고 더 높은 범위의 전체 자릿수가 손실 됩니다.
이 문제를 방지 하려면 값을 문자열로 입력 하 고 변환 합니다.

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a>예제

다음 표에서는 숫자 리터럴의 몇 가지 예를 포함 하 고 해당 형식 및 값을 나열 합니다.

|  번호  |  Type   |    값     |
| -------: | ------- | -----------: |
|      100 | Int32   |          100 |
|     100D | Decimal |          100 |
|     100l | Int64   |          100 |
|    100uL | UInt64  |          100 |
|    100us | UInt16  |          100 |
|    100uy | Byte    |          100 |
|     100y | SByte   |          100 |
|      1e2 | Double  |          100 |
|     1. e2 | Double  |          100 |
|    0x1e2 | Int32   |          482 |
|   0x1e2L | Int64   |          482 |
|   0x1e2D | Int32   |         7725 |
|     482D | Decimal |          482 |
|    482gb | Int64   | 517543559168 |
| 0x1e2lgb | Int64   | 517543559168 |

### <a name="commands-that-look-like-numeric-literals"></a>숫자 리터럴과 같은 명령

숫자 리터럴 처럼 보이는 명령은 호출 연산자 ()를 사용 하 여 실행 해야 합니다 `&` . 그렇지 않으면 연결 된 형식의 숫자로 해석 됩니다.

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

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
