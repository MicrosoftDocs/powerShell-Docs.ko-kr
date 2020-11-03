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
# <a name="about-arithmetic-operators"></a><span data-ttu-id="39b73-104">산술 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="39b73-104">About Arithmetic Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="39b73-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="39b73-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="39b73-106">PowerShell에서 산술 연산을 수행 하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-106">Describes the operators that perform arithmetic in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="39b73-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="39b73-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="39b73-108">산술 연산자는 숫자 값을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-108">Arithmetic operators calculate numeric values.</span></span> <span data-ttu-id="39b73-109">하나 이상의 산술 연산자를 사용 하 여 값을 추가, 빼기, 곱하기 및 나누기 하 고 나누기 연산의 나머지 (모듈러스)를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-109">You can use one or more arithmetic operators to add, subtract, multiply, and divide values, and to calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="39b73-110">또한 더하기 연산자 ( `+` ) 및 곱하기 연산자 ( `*` )는 문자열, 배열 및 해시 테이블 에서도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-110">In addition, the addition operator (`+`) and multiplication operator (`*`) also operate on strings, arrays, and hash tables.</span></span> <span data-ttu-id="39b73-111">더하기 연산자는 입력을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-111">The addition operator concatenates the input.</span></span> <span data-ttu-id="39b73-112">곱하기 연산자는 입력의 여러 복사본을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-112">The multiplication operator returns multiple copies of the input.</span></span> <span data-ttu-id="39b73-113">산술 문에서 개체 형식을 혼합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-113">You can even mix object types in an arithmetic statement.</span></span> <span data-ttu-id="39b73-114">문을 계산 하는 데 사용 되는 메서드는 식에서 가장 왼쪽에 있는 개체의 형식에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-114">The method that is used to evaluate the statement is determined by the type of the leftmost object in the expression.</span></span>

<span data-ttu-id="39b73-115">PowerShell 2.0부터 모든 산술 연산자는 64 비트 숫자에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-115">Beginning in PowerShell 2.0, all arithmetic operators work on 64-bit numbers.</span></span>

<span data-ttu-id="39b73-116">PowerShell 3.0부터 `-shr` `-shl` powershell에서 비트 산술 연산을 지원 하기 위해 (shift 오른쪽) 및 (왼쪽 시프트)가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-116">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are added to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="39b73-117">PowerShell은 다음과 같은 산술 연산자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-117">PowerShell supports the following arithmetic operators:</span></span>

|<span data-ttu-id="39b73-118">연산자</span><span class="sxs-lookup"><span data-stu-id="39b73-118">Operator</span></span>|<span data-ttu-id="39b73-119">Description</span><span class="sxs-lookup"><span data-stu-id="39b73-119">Description</span></span>                       |<span data-ttu-id="39b73-120">예제</span><span class="sxs-lookup"><span data-stu-id="39b73-120">Example</span></span>                      |
|--------|----------------------------------|-----------------------------|
| +      |<span data-ttu-id="39b73-121">정수를 추가 합니다. 서로</span><span class="sxs-lookup"><span data-stu-id="39b73-121">Adds integers; concatenates</span></span>       |`6 + 2`                      |
|        |<span data-ttu-id="39b73-122">문자열, 배열 및 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="39b73-122">strings, arrays, and hash tables.</span></span> |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |<span data-ttu-id="39b73-123">다른 값에서 하나의 값을 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-123">Subtracts one value from another</span></span>  |`6 - 2`                      |
|        |<span data-ttu-id="39b73-124">값</span><span class="sxs-lookup"><span data-stu-id="39b73-124">value</span></span>                             |                             |
| -      |<span data-ttu-id="39b73-125">숫자를 음수 값으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-125">Makes a number a negative number</span></span>  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |<span data-ttu-id="39b73-126">숫자 곱하기 또는 문자열 복사</span><span class="sxs-lookup"><span data-stu-id="39b73-126">Multiply numbers or copy strings</span></span>  |`6 * 2`                      |
|        |<span data-ttu-id="39b73-127">지정 된 숫자의 및 배열</span><span class="sxs-lookup"><span data-stu-id="39b73-127">and arrays the specified number</span></span>   |`@("!") * 4`                 |
|        |<span data-ttu-id="39b73-128">횟수.</span><span class="sxs-lookup"><span data-stu-id="39b73-128">of times.</span></span>                         |`"!" * 3`                    |
| /      |<span data-ttu-id="39b73-129">두 값을 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-129">Divides two values.</span></span>               |`6 / 2`                      |
| %      |<span data-ttu-id="39b73-130">모듈러스-다음의 나머지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-130">Modulus - returns the remainder of</span></span>|`7 % 2`                      |
|        |<span data-ttu-id="39b73-131">나누기 연산입니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-131">a division operation.</span></span>             |                             |
|<span data-ttu-id="39b73-132">-대역</span><span class="sxs-lookup"><span data-stu-id="39b73-132">-band</span></span>   |<span data-ttu-id="39b73-133">비트 AND</span><span class="sxs-lookup"><span data-stu-id="39b73-133">Bitwise AND</span></span>                       |`5 -band 3`                  |
|<span data-ttu-id="39b73-134">-bnot</span><span class="sxs-lookup"><span data-stu-id="39b73-134">-bnot</span></span>   |<span data-ttu-id="39b73-135">비트 NOT</span><span class="sxs-lookup"><span data-stu-id="39b73-135">Bitwise NOT</span></span>                       |`-bnot 5`                    |
|<span data-ttu-id="39b73-136">-bor</span><span class="sxs-lookup"><span data-stu-id="39b73-136">-bor</span></span>    |<span data-ttu-id="39b73-137">비트 OR</span><span class="sxs-lookup"><span data-stu-id="39b73-137">Bitwise OR</span></span>                        |`5 -bor 0x03`                |
|<span data-ttu-id="39b73-138">-bxor</span><span class="sxs-lookup"><span data-stu-id="39b73-138">-bxor</span></span>   |<span data-ttu-id="39b73-139">비트 XOR</span><span class="sxs-lookup"><span data-stu-id="39b73-139">Bitwise XOR</span></span>                       |`5 -bxor 3`                  |
|<span data-ttu-id="39b73-140">-shl</span><span class="sxs-lookup"><span data-stu-id="39b73-140">-shl</span></span>    |<span data-ttu-id="39b73-141">비트를 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-141">Shifts bits to the left</span></span>           |`102 -shl 2`                 |
|<span data-ttu-id="39b73-142">-shr</span><span class="sxs-lookup"><span data-stu-id="39b73-142">-shr</span></span>    |<span data-ttu-id="39b73-143">비트를 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-143">Shifts bits to the right</span></span>          |`102 -shr 2`                 |

<span data-ttu-id="39b73-144">비트 연산자는 정수 형식 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-144">The bitwise operators only work on integer types.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="39b73-145">연산자 우선 순위</span><span class="sxs-lookup"><span data-stu-id="39b73-145">OPERATOR PRECEDENCE</span></span>

<span data-ttu-id="39b73-146">PowerShell은 다음과 같은 순서로 산술 연산자를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-146">PowerShell processes arithmetic operators in the following order:</span></span>

|<span data-ttu-id="39b73-147">우선 순위</span><span class="sxs-lookup"><span data-stu-id="39b73-147">Precedence</span></span>|<span data-ttu-id="39b73-148">연산자</span><span class="sxs-lookup"><span data-stu-id="39b73-148">Operator</span></span>          |<span data-ttu-id="39b73-149">Description</span><span class="sxs-lookup"><span data-stu-id="39b73-149">Description</span></span>                            |
|----------|------------------|---------------------------------------|
|<span data-ttu-id="39b73-150">1</span><span class="sxs-lookup"><span data-stu-id="39b73-150">1</span></span>         | `()`             |<span data-ttu-id="39b73-151">괄호</span><span class="sxs-lookup"><span data-stu-id="39b73-151">Parentheses</span></span>                            |
|<span data-ttu-id="39b73-152">2</span><span class="sxs-lookup"><span data-stu-id="39b73-152">2</span></span>         | `-`              |<span data-ttu-id="39b73-153">음수 또는 단항 연산자의 경우</span><span class="sxs-lookup"><span data-stu-id="39b73-153">For a negative number or unary operator</span></span>|
|<span data-ttu-id="39b73-154">3</span><span class="sxs-lookup"><span data-stu-id="39b73-154">3</span></span>         | <span data-ttu-id="39b73-155">`*`, `/`, `%`</span><span class="sxs-lookup"><span data-stu-id="39b73-155">`*`, `/`, `%`</span></span>    |<span data-ttu-id="39b73-156">곱하기 및 나누기의 경우</span><span class="sxs-lookup"><span data-stu-id="39b73-156">For multiplication and division</span></span>        |
|<span data-ttu-id="39b73-157">4</span><span class="sxs-lookup"><span data-stu-id="39b73-157">4</span></span>         | <span data-ttu-id="39b73-158">`+`, `-`</span><span class="sxs-lookup"><span data-stu-id="39b73-158">`+`, `-`</span></span>         |<span data-ttu-id="39b73-159">더하기 및 빼기</span><span class="sxs-lookup"><span data-stu-id="39b73-159">For addition and subtraction</span></span>           |
|<span data-ttu-id="39b73-160">5</span><span class="sxs-lookup"><span data-stu-id="39b73-160">5</span></span>         | <span data-ttu-id="39b73-161">`-band`, `-bnot`</span><span class="sxs-lookup"><span data-stu-id="39b73-161">`-band`, `-bnot`</span></span> |<span data-ttu-id="39b73-162">비트 연산</span><span class="sxs-lookup"><span data-stu-id="39b73-162">For bitwise operations</span></span>                 |
|<span data-ttu-id="39b73-163">5</span><span class="sxs-lookup"><span data-stu-id="39b73-163">5</span></span>         | <span data-ttu-id="39b73-164">`-bor`, `-bxor`</span><span class="sxs-lookup"><span data-stu-id="39b73-164">`-bor`, `-bxor`</span></span>  |<span data-ttu-id="39b73-165">비트 연산</span><span class="sxs-lookup"><span data-stu-id="39b73-165">For bitwise operations</span></span>                 |
|<span data-ttu-id="39b73-166">5</span><span class="sxs-lookup"><span data-stu-id="39b73-166">5</span></span>         | <span data-ttu-id="39b73-167">`-shr`, `-shl`</span><span class="sxs-lookup"><span data-stu-id="39b73-167">`-shr`, `-shl`</span></span>   |<span data-ttu-id="39b73-168">비트 연산</span><span class="sxs-lookup"><span data-stu-id="39b73-168">For bitwise operations</span></span>                 |

<span data-ttu-id="39b73-169">PowerShell은 우선 순위 규칙에 따라 왼쪽에서 오른쪽으로 식을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-169">PowerShell processes the expressions from left to right according to the precedence rules.</span></span> <span data-ttu-id="39b73-170">다음 예에서는 우선 순위 규칙의 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-170">The following examples show the effect of the precedence rules:</span></span>

|<span data-ttu-id="39b73-171">식</span><span class="sxs-lookup"><span data-stu-id="39b73-171">Expression</span></span> |<span data-ttu-id="39b73-172">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-172">Result</span></span>|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

<span data-ttu-id="39b73-173">PowerShell에서 식을 평가 하는 순서는 사용자가 사용한 다른 프로그래밍 및 스크립트 언어와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-173">The order in which PowerShell evaluates expressions might differ from other programming and scripting languages that you have used.</span></span> <span data-ttu-id="39b73-174">다음 예에서는 복잡 한 대입문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-174">The following example shows a complicated assignment statement.</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

<span data-ttu-id="39b73-175">이 예제에서 식은 이전에 `$a++` 계산 됩니다 `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="39b73-175">In this example, the expression `$a++` is evaluated before `$b[$a]`.</span></span>
<span data-ttu-id="39b73-176">`$a++`문은 문에서 사용 된 후의 값을 변경 `$a` `$c[$a++]` 하지만에서 사용 되기 전에를 변경 합니다 `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="39b73-176">Evaluating `$a++` changes the value of `$a` after it is used in the statement `$c[$a++]`; but, before it is used in `$b[$a]`.</span></span> <span data-ttu-id="39b73-177">의 변수 `$a` 는 `$b[$a]` `1` 가 아니라 equals입니다 `0` . 따라서 문은가 아닌에 값을 할당 `$b[1]` `$b[0]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-177">The variable `$a` in `$b[$a]` equals `1`, not `0`; so, the statement assigns a value to `$b[1]`, not `$b[0]`.</span></span>

<span data-ttu-id="39b73-178">위의 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-178">The above code is equivalent to:</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a><span data-ttu-id="39b73-179">나누기 및 반올림</span><span class="sxs-lookup"><span data-stu-id="39b73-179">DIVISION AND ROUNDING</span></span>

<span data-ttu-id="39b73-180">나누기 연산의 몫이 정수인 경우 PowerShell은 값을 가장 가까운 정수로 반올림 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-180">When the quotient of a division operation is an integer, PowerShell rounds the value to the nearest integer.</span></span> <span data-ttu-id="39b73-181">값이 이면 `.5` 가장 가까운 짝수로 반올림 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-181">When the value is `.5`, it rounds to the nearest even integer.</span></span>

<span data-ttu-id="39b73-182">다음 예제에서는 가장 가까운 짝수 정수로 반올림 한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-182">The following example shows the effect of rounding to the nearest even integer.</span></span>

|<span data-ttu-id="39b73-183">식</span><span class="sxs-lookup"><span data-stu-id="39b73-183">Expression</span></span>      |<span data-ttu-id="39b73-184">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-184">Result</span></span>|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

<span data-ttu-id="39b73-185">**_5/2_ = 2.5** 은 **2** 로 반올림 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-185">Notice how **_5/2_ = 2.5** gets rounded to **2**.</span></span> <span data-ttu-id="39b73-186">그러나 **_7/2_ = 3.5** 은 **4** 로 반올림 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-186">But, **_7/2_ = 3.5** gets rounded to **4**.</span></span>

<span data-ttu-id="39b73-187">클래스를 사용 `[Math]` 하 여 다른 반올림 동작을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-187">You can use the `[Math]` class to get different rounding behavior.</span></span>

|                          <span data-ttu-id="39b73-188">식</span><span class="sxs-lookup"><span data-stu-id="39b73-188">Expression</span></span>                          | <span data-ttu-id="39b73-189">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-189">Result</span></span> |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

<span data-ttu-id="39b73-190">자세한 내용은 [Math](/dotnet/api/system.math.round) 메서드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="39b73-190">For more information, see the [Math.Round](/dotnet/api/system.math.round) method.</span></span>

## <a name="adding-and-multiplying-non-numeric-types"></a><span data-ttu-id="39b73-191">숫자가 아닌 형식 추가 및 곱하기</span><span class="sxs-lookup"><span data-stu-id="39b73-191">ADDING AND MULTIPLYING NON-NUMERIC TYPES</span></span>

<span data-ttu-id="39b73-192">숫자, 문자열, 배열 및 해시 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-192">You can add numbers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="39b73-193">숫자, 문자열 및 배열을 곱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-193">And, you can multiply numbers, strings, and arrays.</span></span> <span data-ttu-id="39b73-194">그러나 해시 테이블은 곱할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-194">However, you cannot multiply hash tables.</span></span>

<span data-ttu-id="39b73-195">문자열, 배열 또는 해시 테이블을 추가 하면 요소가 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-195">When you add strings, arrays, or hash tables, the elements are concatenated.</span></span> <span data-ttu-id="39b73-196">배열 또는 해시 테이블과 같은 컬렉션을 연결 하면 두 컬렉션의 개체를 포함 하는 새 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-196">When you concatenate collections, such as arrays or hash tables, a new object is created that contains the objects from both collections.</span></span> <span data-ttu-id="39b73-197">동일한 키가 있는 해시 테이블을 연결 하려고 하면 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-197">If you try to concatenate hash tables that have the same key, the operation fails.</span></span>

<span data-ttu-id="39b73-198">예를 들어 다음 명령은 두 개의 배열을 만든 후 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-198">For example, the following commands create two arrays and then add them:</span></span>

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

<span data-ttu-id="39b73-199">다른 형식의 개체에 대해 산술 연산을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-199">You can also perform arithmetic operations on objects of different types.</span></span>
<span data-ttu-id="39b73-200">PowerShell에서 수행 하는 작업은 작업에서 가장 왼쪽에 있는 개체의 Microsoft .NET Framework 형식에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-200">The operation that PowerShell performs is determined by the Microsoft .NET Framework type of the leftmost object in the operation.</span></span> <span data-ttu-id="39b73-201">PowerShell은 작업의 모든 개체를 첫 번째 개체의 .NET Framework 형식으로 변환 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-201">PowerShell tries to convert all the objects in the operation to the .NET Framework type of the first object.</span></span> <span data-ttu-id="39b73-202">개체를 변환 하는 데 성공 하면 첫 번째 개체의 .NET Framework 형식에 적절 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-202">If it succeeds in converting the objects, it performs the operation appropriate to the .NET Framework type of the first object.</span></span> <span data-ttu-id="39b73-203">개체를 변환 하는 데 실패 하면 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-203">If it fails to convert any of the objects, the operation fails.</span></span>

<span data-ttu-id="39b73-204">다음 예에서는 더하기 및 곱하기 연산자를 사용 하는 방법을 보여 줍니다. 다른 개체 유형을 포함 하는 작업</span><span class="sxs-lookup"><span data-stu-id="39b73-204">The following examples demonstrate the use of the addition and multiplication operators; in operations that include different object types.</span></span> <span data-ttu-id="39b73-205">다음을 가정 합니다 `$array = 1,2,3` .</span><span class="sxs-lookup"><span data-stu-id="39b73-205">Assume `$array = 1,2,3`:</span></span>

|<span data-ttu-id="39b73-206">식</span><span class="sxs-lookup"><span data-stu-id="39b73-206">Expression</span></span>       |<span data-ttu-id="39b73-207">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-207">Result</span></span>                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |<span data-ttu-id="39b73-208">`1`,`2`,`3`,`16`</span><span class="sxs-lookup"><span data-stu-id="39b73-208">`1`,`2`,`3`,`16`</span></span>       |
|`$array + "file"`|<span data-ttu-id="39b73-209">`1`,`2`,`3`,`file`</span><span class="sxs-lookup"><span data-stu-id="39b73-209">`1`,`2`,`3`,`file`</span></span>     |
|`$array * 2`     |<span data-ttu-id="39b73-210">`1`,`2`,`3`,`1`,`2`,`3`</span><span class="sxs-lookup"><span data-stu-id="39b73-210">`1`,`2`,`3`,`1`,`2`,`3`</span></span>|
|`"file" * 3`     |`filefilefile`         |

<span data-ttu-id="39b73-211">문을 계산 하는 데 사용 되는 메서드는 맨 왼쪽 개체에 의해 결정 되므로 PowerShell에서 더하기 및 곱하기는 엄격 하 게 교환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-211">Because the method that is used to evaluate statements is determined by the leftmost object, addition and multiplication in PowerShell are not strictly commutative.</span></span> <span data-ttu-id="39b73-212">예를 들어는 `(a + b)` 항상 같지는 않으며 `(b + a)` 항상 같지는 않습니다 `(ab)` `(ba)` .</span><span class="sxs-lookup"><span data-stu-id="39b73-212">For example, `(a + b)` does not always equal `(b + a)`, and `(ab)` does not always equal `(ba)`.</span></span>

<span data-ttu-id="39b73-213">다음 예에서는이 원칙을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-213">The following examples demonstrate this principle:</span></span>

|<span data-ttu-id="39b73-214">식</span><span class="sxs-lookup"><span data-stu-id="39b73-214">Expression</span></span>   |<span data-ttu-id="39b73-215">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-215">Result</span></span>                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |<span data-ttu-id="39b73-216">+ 16 + "파일" '</span><span class="sxs-lookup"><span data-stu-id="39b73-216">+ 16 + "file"\`</span></span>                                       |

<span data-ttu-id="39b73-217">해시 테이블은 경우에 따라 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-217">Hash tables are a slightly different case.</span></span> <span data-ttu-id="39b73-218">추가 된 해시 테이블에 중복 키가 없는 경우에는 해시 테이블을 다른 해시 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-218">You can add hash tables to another hash table, as long as, the added hash tables don't have duplicate keys.</span></span>

<span data-ttu-id="39b73-219">다음 예제에서는 해시 테이블을 서로 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-219">The following example show how to add hash tables to each other.</span></span>

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

<span data-ttu-id="39b73-220">다음 예에서는 두 해시 테이블에서 키 중 하나가 중복 되기 때문에 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-220">The following example throws an error because one of the keys is duplicated in both hash tables.</span></span>

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

<span data-ttu-id="39b73-221">또한 배열에 해시 테이블을 추가할 수 있습니다. 전체 해시 테이블은 배열의 항목이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-221">Also, you can add a hash table to an array; and, the entire hash table becomes an item in the array.</span></span>

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

<span data-ttu-id="39b73-222">그러나 해시 테이블에 다른 형식을 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-222">However, you cannot add any other type to a hash table.</span></span>

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

<span data-ttu-id="39b73-223">더하기 연산자가 매우 유용 하지만 할당 연산자를 사용 하 여 해시 테이블 및 배열에 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-223">Although the addition operators are very useful, use the assignment operators to add elements to hash tables and arrays.</span></span> <span data-ttu-id="39b73-224">자세한 내용은 [about_assignment_operators](about_Assignment_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="39b73-224">For more information see [about_assignment_operators](about_Assignment_Operators.md).</span></span> <span data-ttu-id="39b73-225">다음 예에서는 `+=` 대입 연산자를 사용 하 여 배열에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-225">The following examples use the `+=` assignment operator to add items to an array:</span></span>

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

## <a name="type-conversion-to-accommodate-result"></a><span data-ttu-id="39b73-226">결과를 수용할 형식 변환</span><span class="sxs-lookup"><span data-stu-id="39b73-226">TYPE CONVERSION TO ACCOMMODATE RESULT</span></span>

<span data-ttu-id="39b73-227">PowerShell은 전체 자릿수를 잃지 않고 결과를 가장 잘 표현 하는 .NET Framework 숫자 형식을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-227">PowerShell automatically selects the .NET Framework numeric type that best expresses the result without losing precision.</span></span> <span data-ttu-id="39b73-228">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="39b73-228">For example:</span></span>

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

<span data-ttu-id="39b73-229">작업 결과가 형식에 맞지 않는 경우 다음 예제와 같이 결과의 형식이 결과에 맞게 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-229">If the result of an operation is too large for the type, the type of the result is widened to accommodate the result, as in the following example:</span></span>

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

<span data-ttu-id="39b73-230">결과의 형식은 피연산자 중 하 나와 동일할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-230">The type of the result will not necessarily be the same as one of the operands.</span></span> <span data-ttu-id="39b73-231">다음 예제에서는 음수 값을 부호 없는 정수로 캐스팅할 수 없으며, 부호 없는 정수가 너무 커서를 캐스팅할 수 없습니다 `Int32` .</span><span class="sxs-lookup"><span data-stu-id="39b73-231">In the following example, the negative value cannot be cast to an unsigned integer, and the unsigned integer is too large to be cast to `Int32`:</span></span>

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

<span data-ttu-id="39b73-232">이 예제에서는 `Int64` 두 형식을 모두 수용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-232">In this example, `Int64` can accommodate both types.</span></span>

<span data-ttu-id="39b73-233">`System.Decimal`예외 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-233">The `System.Decimal` type is an exception.</span></span> <span data-ttu-id="39b73-234">피연산자 중 하나가 Decimal 형식이 면 결과는 Decimal 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-234">If either operand has the Decimal type, the result will be of the Decimal type.</span></span> <span data-ttu-id="39b73-235">Decimal 형식에 대해 결과가 너무 크면 Double로 캐스팅 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-235">If the result is too large for the Decimal type, it will not be cast to Double.</span></span> <span data-ttu-id="39b73-236">대신 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-236">Instead, an error results.</span></span>

|<span data-ttu-id="39b73-237">식</span><span class="sxs-lookup"><span data-stu-id="39b73-237">Expression</span></span>               |<span data-ttu-id="39b73-238">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-238">Result</span></span>                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a><span data-ttu-id="39b73-239">산술 연산자 및 변수</span><span class="sxs-lookup"><span data-stu-id="39b73-239">ARITHMETIC OPERATORS AND VARIABLES</span></span>

<span data-ttu-id="39b73-240">변수에 산술 연산자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-240">You can also use arithmetic operators with variables.</span></span> <span data-ttu-id="39b73-241">연산자는 변수의 값에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-241">The operators act on the values of the variables.</span></span> <span data-ttu-id="39b73-242">다음 예에서는 변수를 사용 하 여 산술 연산자를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-242">The following examples demonstrate the use of arithmetic operators with variables:</span></span>

| <span data-ttu-id="39b73-243">식</span><span class="sxs-lookup"><span data-stu-id="39b73-243">Expression</span></span>                                    |<span data-ttu-id="39b73-244">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-244">Result</span></span>      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a><span data-ttu-id="39b73-245">산술 연산자 및 명령</span><span class="sxs-lookup"><span data-stu-id="39b73-245">ARITHMETIC OPERATORS AND COMMANDS</span></span>

<span data-ttu-id="39b73-246">일반적으로 숫자, 문자열 및 배열을 사용 하 여 식에서 산술 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-246">Typically, you use the arithmetic operators in expressions with numbers, strings, and arrays.</span></span> <span data-ttu-id="39b73-247">그러나 명령에서 반환 하는 개체 및 해당 개체의 속성을 사용 하 여 산술 연산자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-247">However, you can also use arithmetic operators with the objects that commands return and with the properties of those objects.</span></span>

<span data-ttu-id="39b73-248">다음 예에서는 PowerShell 명령을 사용 하 여 식에서 산술 연산자를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-248">The following examples show how to use the arithmetic operators in expressions with PowerShell commands:</span></span>

```powershell
(get-date) + (new-timespan -day 1)
```

<span data-ttu-id="39b73-249">괄호 연산자를 통해 `get-date` cmdlet 및 cmdlet 식의 계산을 순서 대로 실행 합니다 `new-timespan -day 1` .</span><span class="sxs-lookup"><span data-stu-id="39b73-249">The parenthesis operator forces the evaluation of the `get-date` cmdlet and the evaluation of the `new-timespan -day 1` cmdlet expression, in that order.</span></span> <span data-ttu-id="39b73-250">그런 다음 연산자를 사용 하 여 두 결과를 추가 `+` 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-250">Both results are then added using the `+` operator.</span></span>

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

<span data-ttu-id="39b73-251">위의 식에서 각 프로세스 작업 공간 ()에를 곱하고 그 결과와 비교 하 여 `$_.ws` `2` `50mb` 보다 큰지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-251">In the above expression, each process working space (`$_.ws`) is multiplied by `2`; and, the result, compared against `50mb` to see if it is greater than that.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="39b73-252">비트 연산자</span><span class="sxs-lookup"><span data-stu-id="39b73-252">Bitwise Operators</span></span>

<span data-ttu-id="39b73-253">PowerShell은 비트 and ( `-bAnd` ), 포괄적 비트 or 연산자 ( `-bOr` 및 `-bXor` ), 비트 not ()을 비롯 한 표준 비트 연산자를 지원 `-bNot` 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-253">PowerShell supports the standard bitwise operators, including bitwise-AND (`-bAnd`), the inclusive and exclusive bitwise-OR operators (`-bOr` and `-bXor`), and bitwise-NOT (`-bNot`).</span></span>

<span data-ttu-id="39b73-254">PowerShell 2.0부터 모든 비트 연산자는 64 비트 정수와 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-254">Beginning in PowerShell 2.0, all bitwise operators work with 64-bit integers.</span></span>

<span data-ttu-id="39b73-255">PowerShell 3.0부터 `-shr` `-shl` powershell에서 비트 산술 연산을 지원 하기 위해 (shift 오른쪽) 및 (왼쪽 시프트)가 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-255">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are introduced to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="39b73-256">PowerShell에서 지 원하는 비트 연산자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-256">PowerShell supports the following bitwise operators.</span></span>

| <span data-ttu-id="39b73-257">연산자</span><span class="sxs-lookup"><span data-stu-id="39b73-257">Operator</span></span> | <span data-ttu-id="39b73-258">Description</span><span class="sxs-lookup"><span data-stu-id="39b73-258">Description</span></span>            | <span data-ttu-id="39b73-259">식</span><span class="sxs-lookup"><span data-stu-id="39b73-259">Expression</span></span>   | <span data-ttu-id="39b73-260">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-260">Result</span></span> |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | <span data-ttu-id="39b73-261">비트 AND</span><span class="sxs-lookup"><span data-stu-id="39b73-261">Bitwise AND</span></span>            | `10 -band 3` | <span data-ttu-id="39b73-262">2</span><span class="sxs-lookup"><span data-stu-id="39b73-262">2</span></span>      |
| `-bor`   | <span data-ttu-id="39b73-263">비트 OR (포함)</span><span class="sxs-lookup"><span data-stu-id="39b73-263">Bitwise OR (inclusive)</span></span> | `10 -bor 3`  | <span data-ttu-id="39b73-264">11</span><span class="sxs-lookup"><span data-stu-id="39b73-264">11</span></span>     |
| `-bxor`  | <span data-ttu-id="39b73-265">비트 or (제외)</span><span class="sxs-lookup"><span data-stu-id="39b73-265">Bitwise OR (exclusive)</span></span> | `10 -bxor 3` | <span data-ttu-id="39b73-266">9</span><span class="sxs-lookup"><span data-stu-id="39b73-266">9</span></span>      |
| `-bnot`  | <span data-ttu-id="39b73-267">비트 NOT</span><span class="sxs-lookup"><span data-stu-id="39b73-267">Bitwise NOT</span></span>            | `-bNot 10`   | <span data-ttu-id="39b73-268">-11</span><span class="sxs-lookup"><span data-stu-id="39b73-268">-11</span></span>    |
| `-shl`   | <span data-ttu-id="39b73-269">왼쪽으로 이동</span><span class="sxs-lookup"><span data-stu-id="39b73-269">Shift-left</span></span>             | `102 -shl 2` | <span data-ttu-id="39b73-270">408</span><span class="sxs-lookup"><span data-stu-id="39b73-270">408</span></span>    |
| `-shr`   | <span data-ttu-id="39b73-271">Shift + 오른쪽</span><span class="sxs-lookup"><span data-stu-id="39b73-271">Shift-right</span></span>            | `102 -shr 1` | <span data-ttu-id="39b73-272">51</span><span class="sxs-lookup"><span data-stu-id="39b73-272">51</span></span>     |

<span data-ttu-id="39b73-273">비트 연산자는 값의 이진 형식에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-273">Bitwise operators act on the binary format of a value.</span></span> <span data-ttu-id="39b73-274">예를 들어 숫자 10의 비트 구조는 00001010 (1 바이트 기준)이 고 숫자 3의 비트 구조는 00000011입니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-274">For example, the bit structure for the number 10 is 00001010 (based on 1 byte), and the bit structure for the number 3 is 00000011.</span></span> <span data-ttu-id="39b73-275">비트 연산자를 사용 하 여 10과 3을 비교 하는 경우 각 바이트의 개별 비트가 비교 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-275">When you use a bitwise operator to compare 10 to 3, the individual bits in each byte are compared.</span></span>

<span data-ttu-id="39b73-276">비트 AND 연산에서는 두 입력 비트가 모두 1 인 경우에만 결과 비트가 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-276">In a bitwise AND operation, the resulting bit is set to 1 only when both input bits are 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

<span data-ttu-id="39b73-277">비트 or (포함) 연산에서 입력 비트 중 하나 또는 둘 다가 1 이면 결과 비트는 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-277">In a bitwise OR (inclusive) operation, the resulting bit is set to 1 when either or both input bits are 1.</span></span> <span data-ttu-id="39b73-278">두 입력 비트가 모두 0으로 설정 된 경우에만 결과 비트가 0으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-278">The resulting bit is set to 0 only when both input bits are set to 0.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

<span data-ttu-id="39b73-279">비트 OR (배타) 연산에서 결과 비트는 1로 설정 됩니다. 한 입력 비트가 1 인 경우에만 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-279">In a bitwise OR (exclusive) operation, the resulting bit is set to 1 only when one input bit is 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

<span data-ttu-id="39b73-280">비트 NOT 연산자는 값의 이진 보수를 생성 하는 단항 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-280">The bitwise NOT operator is a unary operator that produces the binary complement of the value.</span></span> <span data-ttu-id="39b73-281">1은 0으로 설정 되 고 비트 0은 1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-281">A bit of 1 is set to 0 and a bit of 0 is set to 1.</span></span>

<span data-ttu-id="39b73-282">예를 들어, 0의 이진 보수는-1, 부호 없는 최대 정수 (0xffffffff) 및-1의 이진 보수는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-282">For example, the binary complement of 0 is -1, the maximum unsigned integer (0xffffffff), and the binary complement of -1 is 0.</span></span>

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

<span data-ttu-id="39b73-283">비트 시프트 왼쪽 작업에서 모든 비트는 "n"이 왼쪽으로 이동 합니다. 여기서 "n"은 오른쪽 피연산자의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-283">In a bitwise shift-left operation, all bits are moved "n" places to the left, where "n" is the value of the right operand.</span></span> <span data-ttu-id="39b73-284">0은 한 자리에 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-284">A zero is inserted in the ones place.</span></span>

<span data-ttu-id="39b73-285">왼쪽 피연산자가 정수 (32 비트) 값인 경우 오른쪽 피연산자의 하위 5 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-285">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="39b73-286">왼쪽 피연산자가 Long (64 비트) 값인 경우 오른쪽 피연산자의 하위 6 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-286">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="39b73-287">식</span><span class="sxs-lookup"><span data-stu-id="39b73-287">Expression</span></span> |<span data-ttu-id="39b73-288">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-288">Result</span></span>|<span data-ttu-id="39b73-289">이진 결과</span><span class="sxs-lookup"><span data-stu-id="39b73-289">Binary Result</span></span>|
|-----------|------|-------------|
|`21 -shl 0`|<span data-ttu-id="39b73-290">21</span><span class="sxs-lookup"><span data-stu-id="39b73-290">21</span></span>    |<span data-ttu-id="39b73-291">0001 0101</span><span class="sxs-lookup"><span data-stu-id="39b73-291">0001 0101</span></span>    |
|`21 -shl 1`|<span data-ttu-id="39b73-292">42</span><span class="sxs-lookup"><span data-stu-id="39b73-292">42</span></span>    |<span data-ttu-id="39b73-293">0010 1010</span><span class="sxs-lookup"><span data-stu-id="39b73-293">0010 1010</span></span>    |
|`21 -shl 2`|<span data-ttu-id="39b73-294">84</span><span class="sxs-lookup"><span data-stu-id="39b73-294">84</span></span>    |<span data-ttu-id="39b73-295">0101 0100</span><span class="sxs-lookup"><span data-stu-id="39b73-295">0101 0100</span></span>    |

<span data-ttu-id="39b73-296">비트 시프트 오른쪽 작업에서는 모든 비트가 오른쪽으로 "n"을 이동 합니다. 여기서 "n"은 오른쪽 피연산자로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-296">In a bitwise shift-right operation, all bits are moved "n" places to the right, where "n" is specified by the right operand.</span></span> <span data-ttu-id="39b73-297">오른쪽 시프트 연산자 (-shr)는 양수 또는 부호 없는 값을 오른쪽으로 이동할 때 왼쪽 맨 위에 0을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-297">The shift-right operator (-shr) inserts a zero in the left-most place when shifting a positive or unsigned value to the right.</span></span>

<span data-ttu-id="39b73-298">왼쪽 피연산자가 정수 (32 비트) 값인 경우 오른쪽 피연산자의 하위 5 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-298">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="39b73-299">왼쪽 피연산자가 Long (64 비트) 값인 경우 오른쪽 피연산자의 하위 6 비트는 이동 하는 왼쪽 피연산자의 비트 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="39b73-299">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="39b73-300">식</span><span class="sxs-lookup"><span data-stu-id="39b73-300">Expression</span></span>              |<span data-ttu-id="39b73-301">결과</span><span class="sxs-lookup"><span data-stu-id="39b73-301">Result</span></span>      |<span data-ttu-id="39b73-302">이진</span><span class="sxs-lookup"><span data-stu-id="39b73-302">Binary</span></span>     |<span data-ttu-id="39b73-303">Hex</span><span class="sxs-lookup"><span data-stu-id="39b73-303">Hex</span></span>         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | <span data-ttu-id="39b73-304">21</span><span class="sxs-lookup"><span data-stu-id="39b73-304">21</span></span>         | <span data-ttu-id="39b73-305">0001 0101</span><span class="sxs-lookup"><span data-stu-id="39b73-305">0001 0101</span></span> | <span data-ttu-id="39b73-306">0x15</span><span class="sxs-lookup"><span data-stu-id="39b73-306">0x15</span></span>       |
|`21 -shr 1`             | <span data-ttu-id="39b73-307">10</span><span class="sxs-lookup"><span data-stu-id="39b73-307">10</span></span>         | <span data-ttu-id="39b73-308">0000 1010</span><span class="sxs-lookup"><span data-stu-id="39b73-308">0000 1010</span></span> | <span data-ttu-id="39b73-309">0x0A</span><span class="sxs-lookup"><span data-stu-id="39b73-309">0x0A</span></span>       |
|`21 -shr 2`             | <span data-ttu-id="39b73-310">5</span><span class="sxs-lookup"><span data-stu-id="39b73-310">5</span></span>          | <span data-ttu-id="39b73-311">0000 0101</span><span class="sxs-lookup"><span data-stu-id="39b73-311">0000 0101</span></span> | <span data-ttu-id="39b73-312">0x05</span><span class="sxs-lookup"><span data-stu-id="39b73-312">0x05</span></span>       |
|`21 -shr 31`            | <span data-ttu-id="39b73-313">0</span><span class="sxs-lookup"><span data-stu-id="39b73-313">0</span></span>          | <span data-ttu-id="39b73-314">0000 0000</span><span class="sxs-lookup"><span data-stu-id="39b73-314">0000 0000</span></span> | <span data-ttu-id="39b73-315">0x00</span><span class="sxs-lookup"><span data-stu-id="39b73-315">0x00</span></span>       |
|`21 -shr 32`            | <span data-ttu-id="39b73-316">21</span><span class="sxs-lookup"><span data-stu-id="39b73-316">21</span></span>         | <span data-ttu-id="39b73-317">0001 0101</span><span class="sxs-lookup"><span data-stu-id="39b73-317">0001 0101</span></span> | <span data-ttu-id="39b73-318">0x15</span><span class="sxs-lookup"><span data-stu-id="39b73-318">0x15</span></span>       |
|`21 -shr 64`            | <span data-ttu-id="39b73-319">21</span><span class="sxs-lookup"><span data-stu-id="39b73-319">21</span></span>         | <span data-ttu-id="39b73-320">0001 0101</span><span class="sxs-lookup"><span data-stu-id="39b73-320">0001 0101</span></span> | <span data-ttu-id="39b73-321">0x15</span><span class="sxs-lookup"><span data-stu-id="39b73-321">0x15</span></span>       |
|`21 -shr 65`            | <span data-ttu-id="39b73-322">10</span><span class="sxs-lookup"><span data-stu-id="39b73-322">10</span></span>         | <span data-ttu-id="39b73-323">0000 1010</span><span class="sxs-lookup"><span data-stu-id="39b73-323">0000 1010</span></span> | <span data-ttu-id="39b73-324">0x0A</span><span class="sxs-lookup"><span data-stu-id="39b73-324">0x0A</span></span>       |
|`21 -shr 66`            | <span data-ttu-id="39b73-325">5</span><span class="sxs-lookup"><span data-stu-id="39b73-325">5</span></span>          | <span data-ttu-id="39b73-326">0000 0101</span><span class="sxs-lookup"><span data-stu-id="39b73-326">0000 0101</span></span> | <span data-ttu-id="39b73-327">0x05</span><span class="sxs-lookup"><span data-stu-id="39b73-327">0x05</span></span>       |
|`[int]::MaxValue -shr 1`| <span data-ttu-id="39b73-328">1073741823</span><span class="sxs-lookup"><span data-stu-id="39b73-328">1073741823</span></span> |           | <span data-ttu-id="39b73-329">0x3FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="39b73-329">0x3FFFFFFF</span></span> |
|`[int]::MinValue -shr 1`| <span data-ttu-id="39b73-330">-1073741824</span><span class="sxs-lookup"><span data-stu-id="39b73-330">-1073741824</span></span>|           | <span data-ttu-id="39b73-331">0xC0000000</span><span class="sxs-lookup"><span data-stu-id="39b73-331">0xC0000000</span></span> |
|`-1 -shr 1`             | <span data-ttu-id="39b73-332">-1</span><span class="sxs-lookup"><span data-stu-id="39b73-332">-1</span></span>         |           | <span data-ttu-id="39b73-333">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="39b73-333">0xFFFFFFFF</span></span> |

## <a name="see-also"></a><span data-ttu-id="39b73-334">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39b73-334">SEE ALSO</span></span>

- [<span data-ttu-id="39b73-335">about_arrays</span><span class="sxs-lookup"><span data-stu-id="39b73-335">about_arrays</span></span>](about_Arrays.md)
- [<span data-ttu-id="39b73-336">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="39b73-336">about_assignment_operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="39b73-337">about_comparison_operators</span><span class="sxs-lookup"><span data-stu-id="39b73-337">about_comparison_operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="39b73-338">about_hash_tables</span><span class="sxs-lookup"><span data-stu-id="39b73-338">about_hash_tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="39b73-339">about_operators</span><span class="sxs-lookup"><span data-stu-id="39b73-339">about_operators</span></span>](about_Operators.md)
- [<span data-ttu-id="39b73-340">about_variables</span><span class="sxs-lookup"><span data-stu-id="39b73-340">about_variables</span></span>](about_Variables.md)
- [<span data-ttu-id="39b73-341">가져오기-날짜</span><span class="sxs-lookup"><span data-stu-id="39b73-341">Get-Date</span></span>](xref:Microsoft.PowerShell.Utility.Get-Date)
- [<span data-ttu-id="39b73-342">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="39b73-342">New-TimeSpan</span></span>](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
