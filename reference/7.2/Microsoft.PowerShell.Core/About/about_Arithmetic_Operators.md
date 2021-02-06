---
description: PowerShell에서 산술 연산을 수행 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_arithmetic_operators
ms.openlocfilehash: 174b3cb72f6b5eb1cc39c4974613d9b9c8dd81a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600863"
---
# <a name="about-arithmetic-operators"></a><span data-ttu-id="37369-103">산술 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="37369-103">About Arithmetic Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="37369-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="37369-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="37369-105">PowerShell에서 산술 연산을 수행 하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-105">Describes the operators that perform arithmetic in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="37369-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="37369-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="37369-107">산술 연산자는 숫자 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-107">Arithmetic operators calculate numeric values.</span></span> <span data-ttu-id="37369-108">하나 이상의 산술 연산자를 사용 하 여 값을 추가, 빼기, 곱하기 및 나누기 하 고 나누기 연산의 나머지 (모듈러스)를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-108">You can use one or more arithmetic operators to add, subtract, multiply, and divide values, and to calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="37369-109">또한 더하기 연산자 ( `+` ) 및 곱하기 연산자 ( `*` )는 문자열, 배열 및 해시 테이블 에서도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-109">In addition, the addition operator (`+`) and multiplication operator (`*`) also operate on strings, arrays, and hash tables.</span></span> <span data-ttu-id="37369-110">더하기 연산자는 입력을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-110">The addition operator concatenates the input.</span></span> <span data-ttu-id="37369-111">곱하기 연산자는 입력의 여러 복사본을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-111">The multiplication operator returns multiple copies of the input.</span></span> <span data-ttu-id="37369-112">산술 문에서 개체 형식을 혼합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-112">You can even mix object types in an arithmetic statement.</span></span> <span data-ttu-id="37369-113">문을 계산 하는 데 사용 되는 메서드는 식에서 가장 왼쪽에 있는 개체의 형식에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-113">The method that is used to evaluate the statement is determined by the type of the leftmost object in the expression.</span></span>

<span data-ttu-id="37369-114">PowerShell 2.0부터 모든 산술 연산자는 64 비트 숫자에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-114">Beginning in PowerShell 2.0, all arithmetic operators work on 64-bit numbers.</span></span>

<span data-ttu-id="37369-115">PowerShell 3.0부터 `-shr` `-shl` powershell에서 비트 산술 연산을 지원 하기 위해 (shift 오른쪽) 및 (왼쪽 시프트)가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-115">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are added to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="37369-116">PowerShell은 다음과 같은 산술 연산자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-116">PowerShell supports the following arithmetic operators:</span></span>

|<span data-ttu-id="37369-117">연산자</span><span class="sxs-lookup"><span data-stu-id="37369-117">Operator</span></span>|<span data-ttu-id="37369-118">설명</span><span class="sxs-lookup"><span data-stu-id="37369-118">Description</span></span>                       |<span data-ttu-id="37369-119">예제</span><span class="sxs-lookup"><span data-stu-id="37369-119">Example</span></span>                      |
|--------|----------------------------------|-----------------------------|
| +      |<span data-ttu-id="37369-120">정수를 추가 합니다. 서로</span><span class="sxs-lookup"><span data-stu-id="37369-120">Adds integers; concatenates</span></span>       |`6 + 2`                      |
|        |<span data-ttu-id="37369-121">문자열, 배열 및 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="37369-121">strings, arrays, and hash tables.</span></span> |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |<span data-ttu-id="37369-122">다른 값에서 하나의 값을 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-122">Subtracts one value from another</span></span>  |`6 - 2`                      |
|        |<span data-ttu-id="37369-123">값</span><span class="sxs-lookup"><span data-stu-id="37369-123">value</span></span>                             |                             |
| -      |<span data-ttu-id="37369-124">숫자를 음수 값으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37369-124">Makes a number a negative number</span></span>  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |<span data-ttu-id="37369-125">숫자 곱하기 또는 문자열 복사</span><span class="sxs-lookup"><span data-stu-id="37369-125">Multiply numbers or copy strings</span></span>  |`6 * 2`                      |
|        |<span data-ttu-id="37369-126">지정 된 숫자의 및 배열</span><span class="sxs-lookup"><span data-stu-id="37369-126">and arrays the specified number</span></span>   |`@("!") * 4`                 |
|        |<span data-ttu-id="37369-127">횟수.</span><span class="sxs-lookup"><span data-stu-id="37369-127">of times.</span></span>                         |`"!" * 3`                    |
| /      |<span data-ttu-id="37369-128">두 값을 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="37369-128">Divides two values.</span></span>               |`6 / 2`                      |
| %      |<span data-ttu-id="37369-129">모듈러스-다음의 나머지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-129">Modulus - returns the remainder of</span></span>|`7 % 2`                      |
|        |<span data-ttu-id="37369-130">나누기 연산입니다.</span><span class="sxs-lookup"><span data-stu-id="37369-130">a division operation.</span></span>             |                             |
|<span data-ttu-id="37369-131">-대역</span><span class="sxs-lookup"><span data-stu-id="37369-131">-band</span></span>   |<span data-ttu-id="37369-132">비트 AND</span><span class="sxs-lookup"><span data-stu-id="37369-132">Bitwise AND</span></span>                       |`5 -band 3`                  |
|<span data-ttu-id="37369-133">-bnot</span><span class="sxs-lookup"><span data-stu-id="37369-133">-bnot</span></span>   |<span data-ttu-id="37369-134">비트 NOT</span><span class="sxs-lookup"><span data-stu-id="37369-134">Bitwise NOT</span></span>                       |`-bnot 5`                    |
|<span data-ttu-id="37369-135">-bor</span><span class="sxs-lookup"><span data-stu-id="37369-135">-bor</span></span>    |<span data-ttu-id="37369-136">비트 OR</span><span class="sxs-lookup"><span data-stu-id="37369-136">Bitwise OR</span></span>                        |`5 -bor 0x03`                |
|<span data-ttu-id="37369-137">-bxor</span><span class="sxs-lookup"><span data-stu-id="37369-137">-bxor</span></span>   |<span data-ttu-id="37369-138">비트 XOR</span><span class="sxs-lookup"><span data-stu-id="37369-138">Bitwise XOR</span></span>                       |`5 -bxor 3`                  |
|<span data-ttu-id="37369-139">-shl</span><span class="sxs-lookup"><span data-stu-id="37369-139">-shl</span></span>    |<span data-ttu-id="37369-140">비트를 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-140">Shifts bits to the left</span></span>           |`102 -shl 2`                 |
|<span data-ttu-id="37369-141">-shr</span><span class="sxs-lookup"><span data-stu-id="37369-141">-shr</span></span>    |<span data-ttu-id="37369-142">비트를 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-142">Shifts bits to the right</span></span>          |`102 -shr 2`                 |

<span data-ttu-id="37369-143">비트 연산자는 정수 형식 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-143">The bitwise operators only work on integer types.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="37369-144">연산자 우선 순위</span><span class="sxs-lookup"><span data-stu-id="37369-144">OPERATOR PRECEDENCE</span></span>

<span data-ttu-id="37369-145">PowerShell은 다음과 같은 순서로 산술 연산자를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-145">PowerShell processes arithmetic operators in the following order:</span></span>

|<span data-ttu-id="37369-146">우선 순위</span><span class="sxs-lookup"><span data-stu-id="37369-146">Precedence</span></span>|<span data-ttu-id="37369-147">연산자</span><span class="sxs-lookup"><span data-stu-id="37369-147">Operator</span></span>          |<span data-ttu-id="37369-148">설명</span><span class="sxs-lookup"><span data-stu-id="37369-148">Description</span></span>                            |
|----------|------------------|---------------------------------------|
|<span data-ttu-id="37369-149">1</span><span class="sxs-lookup"><span data-stu-id="37369-149">1</span></span>         | `()`             |<span data-ttu-id="37369-150">괄호</span><span class="sxs-lookup"><span data-stu-id="37369-150">Parentheses</span></span>                            |
|<span data-ttu-id="37369-151">2</span><span class="sxs-lookup"><span data-stu-id="37369-151">2</span></span>         | `-`              |<span data-ttu-id="37369-152">음수 또는 단항 연산자의 경우</span><span class="sxs-lookup"><span data-stu-id="37369-152">For a negative number or unary operator</span></span>|
|<span data-ttu-id="37369-153">3</span><span class="sxs-lookup"><span data-stu-id="37369-153">3</span></span>         | <span data-ttu-id="37369-154">`*`, `/`, `%`</span><span class="sxs-lookup"><span data-stu-id="37369-154">`*`, `/`, `%`</span></span>    |<span data-ttu-id="37369-155">곱하기 및 나누기의 경우</span><span class="sxs-lookup"><span data-stu-id="37369-155">For multiplication and division</span></span>        |
|<span data-ttu-id="37369-156">4</span><span class="sxs-lookup"><span data-stu-id="37369-156">4</span></span>         | <span data-ttu-id="37369-157">`+`, `-`</span><span class="sxs-lookup"><span data-stu-id="37369-157">`+`, `-`</span></span>         |<span data-ttu-id="37369-158">더하기 및 빼기</span><span class="sxs-lookup"><span data-stu-id="37369-158">For addition and subtraction</span></span>           |
|<span data-ttu-id="37369-159">5</span><span class="sxs-lookup"><span data-stu-id="37369-159">5</span></span>         | <span data-ttu-id="37369-160">`-band`, `-bnot`</span><span class="sxs-lookup"><span data-stu-id="37369-160">`-band`, `-bnot`</span></span> |<span data-ttu-id="37369-161">비트 연산</span><span class="sxs-lookup"><span data-stu-id="37369-161">For bitwise operations</span></span>                 |
|<span data-ttu-id="37369-162">5</span><span class="sxs-lookup"><span data-stu-id="37369-162">5</span></span>         | <span data-ttu-id="37369-163">`-bor`, `-bxor`</span><span class="sxs-lookup"><span data-stu-id="37369-163">`-bor`, `-bxor`</span></span>  |<span data-ttu-id="37369-164">비트 연산</span><span class="sxs-lookup"><span data-stu-id="37369-164">For bitwise operations</span></span>                 |
|<span data-ttu-id="37369-165">5</span><span class="sxs-lookup"><span data-stu-id="37369-165">5</span></span>         | <span data-ttu-id="37369-166">`-shr`, `-shl`</span><span class="sxs-lookup"><span data-stu-id="37369-166">`-shr`, `-shl`</span></span>   |<span data-ttu-id="37369-167">비트 연산</span><span class="sxs-lookup"><span data-stu-id="37369-167">For bitwise operations</span></span>                 |

<span data-ttu-id="37369-168">PowerShell은 우선 순위 규칙에 따라 왼쪽에서 오른쪽으로 식을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-168">PowerShell processes the expressions from left to right according to the precedence rules.</span></span> <span data-ttu-id="37369-169">다음 예에서는 우선 순위 규칙의 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-169">The following examples show the effect of the precedence rules:</span></span>

|<span data-ttu-id="37369-170">식</span><span class="sxs-lookup"><span data-stu-id="37369-170">Expression</span></span> |<span data-ttu-id="37369-171">결과</span><span class="sxs-lookup"><span data-stu-id="37369-171">Result</span></span>|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

<span data-ttu-id="37369-172">PowerShell에서 식을 평가 하는 순서는 사용자가 사용한 다른 프로그래밍 및 스크립트 언어와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-172">The order in which PowerShell evaluates expressions might differ from other programming and scripting languages that you have used.</span></span> <span data-ttu-id="37369-173">다음 예에서는 복잡 한 대입문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-173">The following example shows a complicated assignment statement.</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

<span data-ttu-id="37369-174">이 예제에서 식은 이전에 `$a++` 계산 됩니다 `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="37369-174">In this example, the expression `$a++` is evaluated before `$b[$a]`.</span></span>
<span data-ttu-id="37369-175">`$a++`문은 문에서 사용 된 후의 값을 변경 `$a` `$c[$a++]` 하지만에서 사용 되기 전에를 변경 합니다 `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="37369-175">Evaluating `$a++` changes the value of `$a` after it is used in the statement `$c[$a++]`; but, before it is used in `$b[$a]`.</span></span> <span data-ttu-id="37369-176">의 변수 `$a` 는 `$b[$a]` `1` 가 아니라 equals입니다 `0` . 따라서 문은가 아닌에 값을 할당 `$b[1]` `$b[0]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-176">The variable `$a` in `$b[$a]` equals `1`, not `0`; so, the statement assigns a value to `$b[1]`, not `$b[0]`.</span></span>

<span data-ttu-id="37369-177">위의 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-177">The above code is equivalent to:</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a><span data-ttu-id="37369-178">나누기 및 반올림</span><span class="sxs-lookup"><span data-stu-id="37369-178">DIVISION AND ROUNDING</span></span>

<span data-ttu-id="37369-179">나누기 연산의 몫이 정수인 경우 PowerShell은 값을 가장 가까운 정수로 반올림 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-179">When the quotient of a division operation is an integer, PowerShell rounds the value to the nearest integer.</span></span> <span data-ttu-id="37369-180">값이 이면 `.5` 가장 가까운 짝수로 반올림 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-180">When the value is `.5`, it rounds to the nearest even integer.</span></span>

<span data-ttu-id="37369-181">다음 예제에서는 가장 가까운 짝수 정수로 반올림 한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-181">The following example shows the effect of rounding to the nearest even integer.</span></span>

|<span data-ttu-id="37369-182">식</span><span class="sxs-lookup"><span data-stu-id="37369-182">Expression</span></span>      |<span data-ttu-id="37369-183">결과</span><span class="sxs-lookup"><span data-stu-id="37369-183">Result</span></span>|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

<span data-ttu-id="37369-184">**_5/2_ = 2.5** 은 **2** 로 반올림 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-184">Notice how **_5/2_ = 2.5** gets rounded to **2**.</span></span> <span data-ttu-id="37369-185">그러나 **_7/2_ = 3.5** 은 **4** 로 반올림 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-185">But, **_7/2_ = 3.5** gets rounded to **4**.</span></span>

<span data-ttu-id="37369-186">클래스를 사용 `[Math]` 하 여 다른 반올림 동작을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-186">You can use the `[Math]` class to get different rounding behavior.</span></span>

|                          <span data-ttu-id="37369-187">식</span><span class="sxs-lookup"><span data-stu-id="37369-187">Expression</span></span>                          | <span data-ttu-id="37369-188">결과</span><span class="sxs-lookup"><span data-stu-id="37369-188">Result</span></span> |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

<span data-ttu-id="37369-189">자세한 내용은 [Math](/dotnet/api/system.math.round) 메서드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="37369-189">For more information, see the [Math.Round](/dotnet/api/system.math.round) method.</span></span>

## <a name="adding-and-multiplying-non-numeric-types"></a><span data-ttu-id="37369-190">숫자가 아닌 형식 추가 및 곱하기</span><span class="sxs-lookup"><span data-stu-id="37369-190">ADDING AND MULTIPLYING NON-NUMERIC TYPES</span></span>

<span data-ttu-id="37369-191">숫자, 문자열, 배열 및 해시 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-191">You can add numbers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="37369-192">숫자, 문자열 및 배열을 곱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-192">And, you can multiply numbers, strings, and arrays.</span></span> <span data-ttu-id="37369-193">그러나 해시 테이블은 곱할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-193">However, you cannot multiply hash tables.</span></span>

<span data-ttu-id="37369-194">문자열, 배열 또는 해시 테이블을 추가 하면 요소가 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-194">When you add strings, arrays, or hash tables, the elements are concatenated.</span></span> <span data-ttu-id="37369-195">배열 또는 해시 테이블과 같은 컬렉션을 연결 하면 두 컬렉션의 개체를 포함 하는 새 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="37369-195">When you concatenate collections, such as arrays or hash tables, a new object is created that contains the objects from both collections.</span></span> <span data-ttu-id="37369-196">동일한 키가 있는 해시 테이블을 연결 하려고 하면 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-196">If you try to concatenate hash tables that have the same key, the operation fails.</span></span>

<span data-ttu-id="37369-197">예를 들어 다음 명령은 두 개의 배열을 만든 후 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-197">For example, the following commands create two arrays and then add them:</span></span>

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

<span data-ttu-id="37369-198">다른 형식의 개체에 대해 산술 연산을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-198">You can also perform arithmetic operations on objects of different types.</span></span>
<span data-ttu-id="37369-199">PowerShell에서 수행 하는 작업은 작업에서 가장 왼쪽에 있는 개체의 Microsoft .NET Framework 형식에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-199">The operation that PowerShell performs is determined by the Microsoft .NET Framework type of the leftmost object in the operation.</span></span> <span data-ttu-id="37369-200">PowerShell은 작업의 모든 개체를 첫 번째 개체의 .NET Framework 형식으로 변환 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-200">PowerShell tries to convert all the objects in the operation to the .NET Framework type of the first object.</span></span> <span data-ttu-id="37369-201">개체를 변환 하는 데 성공 하면 첫 번째 개체의 .NET Framework 형식에 적절 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-201">If it succeeds in converting the objects, it performs the operation appropriate to the .NET Framework type of the first object.</span></span> <span data-ttu-id="37369-202">개체를 변환 하는 데 실패 하면 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-202">If it fails to convert any of the objects, the operation fails.</span></span>

<span data-ttu-id="37369-203">다음 예에서는 더하기 및 곱하기 연산자를 사용 하는 방법을 보여 줍니다. 다른 개체 유형을 포함 하는 작업</span><span class="sxs-lookup"><span data-stu-id="37369-203">The following examples demonstrate the use of the addition and multiplication operators; in operations that include different object types.</span></span> <span data-ttu-id="37369-204">다음을 가정 합니다 `$array = 1,2,3` .</span><span class="sxs-lookup"><span data-stu-id="37369-204">Assume `$array = 1,2,3`:</span></span>

|<span data-ttu-id="37369-205">식</span><span class="sxs-lookup"><span data-stu-id="37369-205">Expression</span></span>       |<span data-ttu-id="37369-206">결과</span><span class="sxs-lookup"><span data-stu-id="37369-206">Result</span></span>                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |<span data-ttu-id="37369-207">`1`,`2`,`3`,`16`</span><span class="sxs-lookup"><span data-stu-id="37369-207">`1`,`2`,`3`,`16`</span></span>       |
|`$array + "file"`|<span data-ttu-id="37369-208">`1`,`2`,`3`,`file`</span><span class="sxs-lookup"><span data-stu-id="37369-208">`1`,`2`,`3`,`file`</span></span>     |
|`$array * 2`     |<span data-ttu-id="37369-209">`1`,`2`,`3`,`1`,`2`,`3`</span><span class="sxs-lookup"><span data-stu-id="37369-209">`1`,`2`,`3`,`1`,`2`,`3`</span></span>|
|`"file" * 3`     |`filefilefile`         |

<span data-ttu-id="37369-210">문을 계산 하는 데 사용 되는 메서드는 맨 왼쪽 개체에 의해 결정 되므로 PowerShell에서 더하기 및 곱하기는 엄격 하 게 교환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-210">Because the method that is used to evaluate statements is determined by the leftmost object, addition and multiplication in PowerShell are not strictly commutative.</span></span> <span data-ttu-id="37369-211">예를 들어는 `(a + b)` 항상 같지는 않으며 `(b + a)` 항상 같지는 않습니다 `(ab)` `(ba)` .</span><span class="sxs-lookup"><span data-stu-id="37369-211">For example, `(a + b)` does not always equal `(b + a)`, and `(ab)` does not always equal `(ba)`.</span></span>

<span data-ttu-id="37369-212">다음 예에서는이 원칙을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-212">The following examples demonstrate this principle:</span></span>

|<span data-ttu-id="37369-213">식</span><span class="sxs-lookup"><span data-stu-id="37369-213">Expression</span></span>   |<span data-ttu-id="37369-214">결과</span><span class="sxs-lookup"><span data-stu-id="37369-214">Result</span></span>                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |<span data-ttu-id="37369-215">+ 16 + "파일" '</span><span class="sxs-lookup"><span data-stu-id="37369-215">+ 16 + "file"\`</span></span>                                       |

<span data-ttu-id="37369-216">해시 테이블은 경우에 따라 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="37369-216">Hash tables are a slightly different case.</span></span> <span data-ttu-id="37369-217">추가 된 해시 테이블에 중복 키가 없는 경우에는 해시 테이블을 다른 해시 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-217">You can add hash tables to another hash table, as long as, the added hash tables don't have duplicate keys.</span></span>

<span data-ttu-id="37369-218">다음 예제에서는 해시 테이블을 서로 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-218">The following example show how to add hash tables to each other.</span></span>

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

<span data-ttu-id="37369-219">다음 예에서는 두 해시 테이블에서 키 중 하나가 중복 되기 때문에 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-219">The following example throws an error because one of the keys is duplicated in both hash tables.</span></span>

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

<span data-ttu-id="37369-220">또한 배열에 해시 테이블을 추가할 수 있습니다. 전체 해시 테이블은 배열의 항목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-220">Also, you can add a hash table to an array; and, the entire hash table becomes an item in the array.</span></span>

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

<span data-ttu-id="37369-221">그러나 해시 테이블에 다른 형식을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-221">However, you cannot add any other type to a hash table.</span></span>

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

<span data-ttu-id="37369-222">더하기 연산자가 매우 유용 하지만 할당 연산자를 사용 하 여 해시 테이블 및 배열에 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-222">Although the addition operators are very useful, use the assignment operators to add elements to hash tables and arrays.</span></span> <span data-ttu-id="37369-223">자세한 내용은 [about_assignment_operators](about_Assignment_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="37369-223">For more information see [about_assignment_operators](about_Assignment_Operators.md).</span></span> <span data-ttu-id="37369-224">다음 예에서는 `+=` 대입 연산자를 사용 하 여 배열에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-224">The following examples use the `+=` assignment operator to add items to an array:</span></span>

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

## <a name="type-conversion-to-accommodate-result"></a><span data-ttu-id="37369-225">결과를 수용할 형식 변환</span><span class="sxs-lookup"><span data-stu-id="37369-225">TYPE CONVERSION TO ACCOMMODATE RESULT</span></span>

<span data-ttu-id="37369-226">PowerShell은 전체 자릿수를 잃지 않고 결과를 가장 잘 표현 하는 .NET Framework 숫자 형식을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-226">PowerShell automatically selects the .NET Framework numeric type that best expresses the result without losing precision.</span></span> <span data-ttu-id="37369-227">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="37369-227">For example:</span></span>

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

<span data-ttu-id="37369-228">작업 결과가 형식에 맞지 않는 경우 다음 예제와 같이 결과의 형식이 결과에 맞게 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-228">If the result of an operation is too large for the type, the type of the result is widened to accommodate the result, as in the following example:</span></span>

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

<span data-ttu-id="37369-229">결과의 형식은 피연산자 중 하 나와 동일할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-229">The type of the result will not necessarily be the same as one of the operands.</span></span> <span data-ttu-id="37369-230">다음 예제에서는 음수 값을 부호 없는 정수로 캐스팅할 수 없으며, 부호 없는 정수가 너무 커서를 캐스팅할 수 없습니다 `Int32` .</span><span class="sxs-lookup"><span data-stu-id="37369-230">In the following example, the negative value cannot be cast to an unsigned integer, and the unsigned integer is too large to be cast to `Int32`:</span></span>

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

<span data-ttu-id="37369-231">이 예제에서는 `Int64` 두 형식을 모두 수용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-231">In this example, `Int64` can accommodate both types.</span></span>

<span data-ttu-id="37369-232">`System.Decimal`예외 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="37369-232">The `System.Decimal` type is an exception.</span></span> <span data-ttu-id="37369-233">피연산자 중 하나가 Decimal 형식이 면 결과는 Decimal 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-233">If either operand has the Decimal type, the result will be of the Decimal type.</span></span> <span data-ttu-id="37369-234">Decimal 형식에 대해 결과가 너무 크면 Double로 캐스팅 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-234">If the result is too large for the Decimal type, it will not be cast to Double.</span></span> <span data-ttu-id="37369-235">대신 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-235">Instead, an error results.</span></span>

|<span data-ttu-id="37369-236">식</span><span class="sxs-lookup"><span data-stu-id="37369-236">Expression</span></span>               |<span data-ttu-id="37369-237">결과</span><span class="sxs-lookup"><span data-stu-id="37369-237">Result</span></span>                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a><span data-ttu-id="37369-238">산술 연산자 및 변수</span><span class="sxs-lookup"><span data-stu-id="37369-238">ARITHMETIC OPERATORS AND VARIABLES</span></span>

<span data-ttu-id="37369-239">변수에 산술 연산자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-239">You can also use arithmetic operators with variables.</span></span> <span data-ttu-id="37369-240">연산자는 변수의 값에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-240">The operators act on the values of the variables.</span></span> <span data-ttu-id="37369-241">다음 예에서는 변수를 사용 하 여 산술 연산자를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-241">The following examples demonstrate the use of arithmetic operators with variables:</span></span>

| <span data-ttu-id="37369-242">식</span><span class="sxs-lookup"><span data-stu-id="37369-242">Expression</span></span>                                    |<span data-ttu-id="37369-243">결과</span><span class="sxs-lookup"><span data-stu-id="37369-243">Result</span></span>      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a><span data-ttu-id="37369-244">산술 연산자 및 명령</span><span class="sxs-lookup"><span data-stu-id="37369-244">ARITHMETIC OPERATORS AND COMMANDS</span></span>

<span data-ttu-id="37369-245">일반적으로 숫자, 문자열 및 배열을 사용 하 여 식에서 산술 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-245">Typically, you use the arithmetic operators in expressions with numbers, strings, and arrays.</span></span> <span data-ttu-id="37369-246">그러나 명령에서 반환 하는 개체 및 해당 개체의 속성을 사용 하 여 산술 연산자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-246">However, you can also use arithmetic operators with the objects that commands return and with the properties of those objects.</span></span>

<span data-ttu-id="37369-247">다음 예에서는 PowerShell 명령을 사용 하 여 식에서 산술 연산자를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="37369-247">The following examples show how to use the arithmetic operators in expressions with PowerShell commands:</span></span>

```powershell
(get-date) + (new-timespan -day 1)
```

<span data-ttu-id="37369-248">괄호 연산자를 통해 `get-date` cmdlet 및 cmdlet 식의 계산을 순서 대로 실행 합니다 `new-timespan -day 1` .</span><span class="sxs-lookup"><span data-stu-id="37369-248">The parenthesis operator forces the evaluation of the `get-date` cmdlet and the evaluation of the `new-timespan -day 1` cmdlet expression, in that order.</span></span> <span data-ttu-id="37369-249">그런 다음 연산자를 사용 하 여 두 결과를 추가 `+` 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-249">Both results are then added using the `+` operator.</span></span>

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

<span data-ttu-id="37369-250">위의 식에서 각 프로세스 작업 공간 ()에를 곱하고 그 결과와 비교 하 여 `$_.ws` `2` `50mb` 보다 큰지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-250">In the above expression, each process working space (`$_.ws`) is multiplied by `2`; and, the result, compared against `50mb` to see if it is greater than that.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="37369-251">비트 연산자</span><span class="sxs-lookup"><span data-stu-id="37369-251">Bitwise Operators</span></span>

<span data-ttu-id="37369-252">PowerShell은 비트 and ( `-bAnd` ), 포괄적 비트 or 연산자 ( `-bOr` 및 `-bXor` ), 비트 not ()을 비롯 한 표준 비트 연산자를 지원 `-bNot` 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-252">PowerShell supports the standard bitwise operators, including bitwise-AND (`-bAnd`), the inclusive and exclusive bitwise-OR operators (`-bOr` and `-bXor`), and bitwise-NOT (`-bNot`).</span></span>

<span data-ttu-id="37369-253">PowerShell 2.0부터 모든 비트 연산자는 64 비트 정수와 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-253">Beginning in PowerShell 2.0, all bitwise operators work with 64-bit integers.</span></span>

<span data-ttu-id="37369-254">PowerShell 3.0부터 `-shr` `-shl` powershell에서 비트 산술 연산을 지원 하기 위해 (shift 오른쪽) 및 (왼쪽 시프트)가 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-254">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are introduced to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="37369-255">PowerShell에서 지 원하는 비트 연산자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="37369-255">PowerShell supports the following bitwise operators.</span></span>

| <span data-ttu-id="37369-256">연산자</span><span class="sxs-lookup"><span data-stu-id="37369-256">Operator</span></span> | <span data-ttu-id="37369-257">Description</span><span class="sxs-lookup"><span data-stu-id="37369-257">Description</span></span>            | <span data-ttu-id="37369-258">식</span><span class="sxs-lookup"><span data-stu-id="37369-258">Expression</span></span>   | <span data-ttu-id="37369-259">결과</span><span class="sxs-lookup"><span data-stu-id="37369-259">Result</span></span> |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | <span data-ttu-id="37369-260">비트 AND</span><span class="sxs-lookup"><span data-stu-id="37369-260">Bitwise AND</span></span>            | `10 -band 3` | <span data-ttu-id="37369-261">2</span><span class="sxs-lookup"><span data-stu-id="37369-261">2</span></span>      |
| `-bor`   | <span data-ttu-id="37369-262">비트 OR (포함)</span><span class="sxs-lookup"><span data-stu-id="37369-262">Bitwise OR (inclusive)</span></span> | `10 -bor 3`  | <span data-ttu-id="37369-263">11</span><span class="sxs-lookup"><span data-stu-id="37369-263">11</span></span>     |
| `-bxor`  | <span data-ttu-id="37369-264">비트 or (제외)</span><span class="sxs-lookup"><span data-stu-id="37369-264">Bitwise OR (exclusive)</span></span> | `10 -bxor 3` | <span data-ttu-id="37369-265">9</span><span class="sxs-lookup"><span data-stu-id="37369-265">9</span></span>      |
| `-bnot`  | <span data-ttu-id="37369-266">비트 NOT</span><span class="sxs-lookup"><span data-stu-id="37369-266">Bitwise NOT</span></span>            | `-bNot 10`   | <span data-ttu-id="37369-267">-11</span><span class="sxs-lookup"><span data-stu-id="37369-267">-11</span></span>    |
| `-shl`   | <span data-ttu-id="37369-268">왼쪽으로 이동</span><span class="sxs-lookup"><span data-stu-id="37369-268">Shift-left</span></span>             | `102 -shl 2` | <span data-ttu-id="37369-269">408</span><span class="sxs-lookup"><span data-stu-id="37369-269">408</span></span>    |
| `-shr`   | <span data-ttu-id="37369-270">Shift + 오른쪽</span><span class="sxs-lookup"><span data-stu-id="37369-270">Shift-right</span></span>            | `102 -shr 1` | <span data-ttu-id="37369-271">51</span><span class="sxs-lookup"><span data-stu-id="37369-271">51</span></span>     |

<span data-ttu-id="37369-272">비트 연산자는 값의 이진 형식에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-272">Bitwise operators act on the binary format of a value.</span></span> <span data-ttu-id="37369-273">예를 들어 숫자 10의 비트 구조는 00001010 (1 바이트 기준)이 고 숫자 3의 비트 구조는 00000011입니다.</span><span class="sxs-lookup"><span data-stu-id="37369-273">For example, the bit structure for the number 10 is 00001010 (based on 1 byte), and the bit structure for the number 3 is 00000011.</span></span> <span data-ttu-id="37369-274">비트 연산자를 사용 하 여 10과 3을 비교 하는 경우 각 바이트의 개별 비트가 비교 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-274">When you use a bitwise operator to compare 10 to 3, the individual bits in each byte are compared.</span></span>

<span data-ttu-id="37369-275">비트 AND 연산에서는 두 입력 비트가 모두 1 인 경우에만 결과 비트가 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-275">In a bitwise AND operation, the resulting bit is set to 1 only when both input bits are 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

<span data-ttu-id="37369-276">비트 or (포함) 연산에서 입력 비트 중 하나 또는 둘 다가 1 이면 결과 비트는 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-276">In a bitwise OR (inclusive) operation, the resulting bit is set to 1 when either or both input bits are 1.</span></span> <span data-ttu-id="37369-277">두 입력 비트가 모두 0으로 설정 된 경우에만 결과 비트가 0으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-277">The resulting bit is set to 0 only when both input bits are set to 0.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

<span data-ttu-id="37369-278">비트 OR (배타) 연산에서 결과 비트는 1로 설정 됩니다. 한 입력 비트가 1 인 경우에만 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-278">In a bitwise OR (exclusive) operation, the resulting bit is set to 1 only when one input bit is 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

<span data-ttu-id="37369-279">비트 NOT 연산자는 값의 이진 보수를 생성 하는 단항 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="37369-279">The bitwise NOT operator is a unary operator that produces the binary complement of the value.</span></span> <span data-ttu-id="37369-280">1은 0으로 설정 되 고 비트 0은 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-280">A bit of 1 is set to 0 and a bit of 0 is set to 1.</span></span>

<span data-ttu-id="37369-281">예를 들어, 0의 이진 보수는-1, 부호 없는 최대 정수 (0xffffffff) 및-1의 이진 보수는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="37369-281">For example, the binary complement of 0 is -1, the maximum unsigned integer (0xffffffff), and the binary complement of -1 is 0.</span></span>

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

<span data-ttu-id="37369-282">비트 시프트 왼쪽 작업에서 모든 비트는 "n"이 왼쪽으로 이동 합니다. 여기서 "n"은 오른쪽 피연산자의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="37369-282">In a bitwise shift-left operation, all bits are moved "n" places to the left, where "n" is the value of the right operand.</span></span> <span data-ttu-id="37369-283">0은 한 자리에 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-283">A zero is inserted in the ones place.</span></span>

<span data-ttu-id="37369-284">왼쪽 피연산자가 정수 (32 비트) 값인 경우 오른쪽 피연산자의 하위 5 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-284">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="37369-285">왼쪽 피연산자가 Long (64 비트) 값인 경우 오른쪽 피연산자의 하위 6 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-285">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="37369-286">식</span><span class="sxs-lookup"><span data-stu-id="37369-286">Expression</span></span> |<span data-ttu-id="37369-287">결과</span><span class="sxs-lookup"><span data-stu-id="37369-287">Result</span></span>|<span data-ttu-id="37369-288">이진 결과</span><span class="sxs-lookup"><span data-stu-id="37369-288">Binary Result</span></span>|
|-----------|------|-------------|
|`21 -shl 0`|<span data-ttu-id="37369-289">21</span><span class="sxs-lookup"><span data-stu-id="37369-289">21</span></span>    |<span data-ttu-id="37369-290">0001 0101</span><span class="sxs-lookup"><span data-stu-id="37369-290">0001 0101</span></span>    |
|`21 -shl 1`|<span data-ttu-id="37369-291">42</span><span class="sxs-lookup"><span data-stu-id="37369-291">42</span></span>    |<span data-ttu-id="37369-292">0010 1010</span><span class="sxs-lookup"><span data-stu-id="37369-292">0010 1010</span></span>    |
|`21 -shl 2`|<span data-ttu-id="37369-293">84</span><span class="sxs-lookup"><span data-stu-id="37369-293">84</span></span>    |<span data-ttu-id="37369-294">0101 0100</span><span class="sxs-lookup"><span data-stu-id="37369-294">0101 0100</span></span>    |

<span data-ttu-id="37369-295">비트 시프트 오른쪽 작업에서는 모든 비트가 오른쪽으로 "n"을 이동 합니다. 여기서 "n"은 오른쪽 피연산자로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37369-295">In a bitwise shift-right operation, all bits are moved "n" places to the right, where "n" is specified by the right operand.</span></span> <span data-ttu-id="37369-296">오른쪽 시프트 연산자 (-shr)는 양수 또는 부호 없는 값을 오른쪽으로 이동할 때 왼쪽 맨 위에 0을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-296">The shift-right operator (-shr) inserts a zero in the left-most place when shifting a positive or unsigned value to the right.</span></span>

<span data-ttu-id="37369-297">왼쪽 피연산자가 정수 (32 비트) 값인 경우 오른쪽 피연산자의 하위 5 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-297">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="37369-298">왼쪽 피연산자가 Long (64 비트) 값인 경우 오른쪽 피연산자의 하위 6 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37369-298">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="37369-299">식</span><span class="sxs-lookup"><span data-stu-id="37369-299">Expression</span></span>              |<span data-ttu-id="37369-300">결과</span><span class="sxs-lookup"><span data-stu-id="37369-300">Result</span></span>      |<span data-ttu-id="37369-301">이진</span><span class="sxs-lookup"><span data-stu-id="37369-301">Binary</span></span>     |<span data-ttu-id="37369-302">Hex</span><span class="sxs-lookup"><span data-stu-id="37369-302">Hex</span></span>         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | <span data-ttu-id="37369-303">21</span><span class="sxs-lookup"><span data-stu-id="37369-303">21</span></span>         | <span data-ttu-id="37369-304">0001 0101</span><span class="sxs-lookup"><span data-stu-id="37369-304">0001 0101</span></span> | <span data-ttu-id="37369-305">0x15</span><span class="sxs-lookup"><span data-stu-id="37369-305">0x15</span></span>       |
|`21 -shr 1`             | <span data-ttu-id="37369-306">10</span><span class="sxs-lookup"><span data-stu-id="37369-306">10</span></span>         | <span data-ttu-id="37369-307">0000 1010</span><span class="sxs-lookup"><span data-stu-id="37369-307">0000 1010</span></span> | <span data-ttu-id="37369-308">0x0A</span><span class="sxs-lookup"><span data-stu-id="37369-308">0x0A</span></span>       |
|`21 -shr 2`             | <span data-ttu-id="37369-309">5</span><span class="sxs-lookup"><span data-stu-id="37369-309">5</span></span>          | <span data-ttu-id="37369-310">0000 0101</span><span class="sxs-lookup"><span data-stu-id="37369-310">0000 0101</span></span> | <span data-ttu-id="37369-311">0x05</span><span class="sxs-lookup"><span data-stu-id="37369-311">0x05</span></span>       |
|`21 -shr 31`            | <span data-ttu-id="37369-312">0</span><span class="sxs-lookup"><span data-stu-id="37369-312">0</span></span>          | <span data-ttu-id="37369-313">0000 0000</span><span class="sxs-lookup"><span data-stu-id="37369-313">0000 0000</span></span> | <span data-ttu-id="37369-314">0x00</span><span class="sxs-lookup"><span data-stu-id="37369-314">0x00</span></span>       |
|`21 -shr 32`            | <span data-ttu-id="37369-315">21</span><span class="sxs-lookup"><span data-stu-id="37369-315">21</span></span>         | <span data-ttu-id="37369-316">0001 0101</span><span class="sxs-lookup"><span data-stu-id="37369-316">0001 0101</span></span> | <span data-ttu-id="37369-317">0x15</span><span class="sxs-lookup"><span data-stu-id="37369-317">0x15</span></span>       |
|`21 -shr 64`            | <span data-ttu-id="37369-318">21</span><span class="sxs-lookup"><span data-stu-id="37369-318">21</span></span>         | <span data-ttu-id="37369-319">0001 0101</span><span class="sxs-lookup"><span data-stu-id="37369-319">0001 0101</span></span> | <span data-ttu-id="37369-320">0x15</span><span class="sxs-lookup"><span data-stu-id="37369-320">0x15</span></span>       |
|`21 -shr 65`            | <span data-ttu-id="37369-321">10</span><span class="sxs-lookup"><span data-stu-id="37369-321">10</span></span>         | <span data-ttu-id="37369-322">0000 1010</span><span class="sxs-lookup"><span data-stu-id="37369-322">0000 1010</span></span> | <span data-ttu-id="37369-323">0x0A</span><span class="sxs-lookup"><span data-stu-id="37369-323">0x0A</span></span>       |
|`21 -shr 66`            | <span data-ttu-id="37369-324">5</span><span class="sxs-lookup"><span data-stu-id="37369-324">5</span></span>          | <span data-ttu-id="37369-325">0000 0101</span><span class="sxs-lookup"><span data-stu-id="37369-325">0000 0101</span></span> | <span data-ttu-id="37369-326">0x05</span><span class="sxs-lookup"><span data-stu-id="37369-326">0x05</span></span>       |
|`[int]::MaxValue -shr 1`| <span data-ttu-id="37369-327">1073741823</span><span class="sxs-lookup"><span data-stu-id="37369-327">1073741823</span></span> |           | <span data-ttu-id="37369-328">0x3FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="37369-328">0x3FFFFFFF</span></span> |
|`[int]::MinValue -shr 1`| <span data-ttu-id="37369-329">-1073741824</span><span class="sxs-lookup"><span data-stu-id="37369-329">-1073741824</span></span>|           | <span data-ttu-id="37369-330">0xC0000000</span><span class="sxs-lookup"><span data-stu-id="37369-330">0xC0000000</span></span> |
|`-1 -shr 1`             | <span data-ttu-id="37369-331">-1</span><span class="sxs-lookup"><span data-stu-id="37369-331">-1</span></span>         |           | <span data-ttu-id="37369-332">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="37369-332">0xFFFFFFFF</span></span> |

## <a name="see-also"></a><span data-ttu-id="37369-333">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37369-333">SEE ALSO</span></span>

- [<span data-ttu-id="37369-334">about_arrays</span><span class="sxs-lookup"><span data-stu-id="37369-334">about_arrays</span></span>](about_Arrays.md)
- [<span data-ttu-id="37369-335">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="37369-335">about_assignment_operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="37369-336">about_comparison_operators</span><span class="sxs-lookup"><span data-stu-id="37369-336">about_comparison_operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="37369-337">about_hash_tables</span><span class="sxs-lookup"><span data-stu-id="37369-337">about_hash_tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="37369-338">about_operators</span><span class="sxs-lookup"><span data-stu-id="37369-338">about_operators</span></span>](about_Operators.md)
- [<span data-ttu-id="37369-339">about_variables</span><span class="sxs-lookup"><span data-stu-id="37369-339">about_variables</span></span>](about_Variables.md)
- [<span data-ttu-id="37369-340">가져오기-날짜</span><span class="sxs-lookup"><span data-stu-id="37369-340">Get-Date</span></span>](xref:Microsoft.PowerShell.Utility.Get-Date)
- [<span data-ttu-id="37369-341">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="37369-341">New-TimeSpan</span></span>](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
