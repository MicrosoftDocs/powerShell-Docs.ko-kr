---
description: 정수 및 실수 리터럴은 모두 형식 및 승수 접미사를 사용할 수 있습니다.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 숫자 리터럴 정보
ms.openlocfilehash: 99fa8c1a751551d028fe6df0b0cec94e07f19c59
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224961"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="d0ce8-103">숫자 리터럴 정보</span><span class="sxs-lookup"><span data-stu-id="d0ce8-103">About numeric literals</span></span>

<span data-ttu-id="d0ce8-104">숫자 리터럴에는 integer와 real의 두 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="d0ce8-105">둘 다 형식 및 승수 접미사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="d0ce8-106">정수 리터럴</span><span class="sxs-lookup"><span data-stu-id="d0ce8-106">Integer literals</span></span>

<span data-ttu-id="d0ce8-107">정수 리터럴은 10 진수 또는 16 진수 표기법으로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="d0ce8-108">16 진수 리터럴의 접두사는 `0x` 10 진수와 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="d0ce8-109">정수 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="d0ce8-110">접미사</span><span class="sxs-lookup"><span data-stu-id="d0ce8-110">Suffix</span></span> |       <span data-ttu-id="d0ce8-111">의미</span><span class="sxs-lookup"><span data-stu-id="d0ce8-111">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="d0ce8-112">l</span><span class="sxs-lookup"><span data-stu-id="d0ce8-112">l</span></span>      | <span data-ttu-id="d0ce8-113">long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d0ce8-113">long data type</span></span>      |
| <span data-ttu-id="d0ce8-114">kb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-114">kb</span></span>     | <span data-ttu-id="d0ce8-115">kb 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-115">kilobyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-116">mb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-116">mb</span></span>     | <span data-ttu-id="d0ce8-117">메가바이트 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-117">megabyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-118">35</span><span class="sxs-lookup"><span data-stu-id="d0ce8-118">gb</span></span>     | <span data-ttu-id="d0ce8-119">gb 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-119">gigabyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-120">1tb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-120">tb</span></span>     | <span data-ttu-id="d0ce8-121">테라바이트 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-121">terabyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-122">pb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-122">pb</span></span>     | <span data-ttu-id="d0ce8-123">페타바이트 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-123">petabyte multiplier</span></span> |

<span data-ttu-id="d0ce8-124">정수 리터럴의 형식은 해당 값, 형식 접미사 및 숫자 승수 접미사로 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-124">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="d0ce8-125">형식 접미사가 없는 정수 리터럴의 경우:</span><span class="sxs-lookup"><span data-stu-id="d0ce8-125">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="d0ce8-126">값을 형식으로 나타낼 수 있으면 해당 `[int]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-126">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="d0ce8-127">그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[long]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-127">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="d0ce8-128">그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[decimal]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-128">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="d0ce8-129">그렇지 않으면 형식으로 표현 됩니다 `[double]` .</span><span class="sxs-lookup"><span data-stu-id="d0ce8-129">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="d0ce8-130">형식 접미사가 있는 정수 리터럴의 경우:</span><span class="sxs-lookup"><span data-stu-id="d0ce8-130">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="d0ce8-131">형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[int]` 해당 형식은 `[int]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-131">If the type suffix is `u` and the value can be represented by type `[int]` then its type is `[int]`.</span></span>
- <span data-ttu-id="d0ce8-132">형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[long]` 해당 형식은 `[long]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-132">If the type suffix is `u` and the value can be represented by type `[long]` then its type is `[long]`.</span></span>
- <span data-ttu-id="d0ce8-133">해당 값을 지정 된 형식으로 나타낼 수 있으면 해당 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-133">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="d0ce8-134">그렇지 않으면 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-134">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="d0ce8-135">real 리터럴</span><span class="sxs-lookup"><span data-stu-id="d0ce8-135">Real literals</span></span>

<span data-ttu-id="d0ce8-136">실수 리터럴은 소수 표기법 으로만 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-136">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="d0ce8-137">이 표기법은 지 수 부분을 사용 하 여 소수점이 나 과학적 표기법 뒤에 소수 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-137">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="d0ce8-138">지 수 부분에는 ' e ' 뒤에 선택적 기호 (+/-)와 지 수를 나타내는 숫자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-138">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="d0ce8-139">예를 들어 리터럴 값은 `1e2` 숫자 값 100와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-139">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="d0ce8-140">실제 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-140">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="d0ce8-141">접미사</span><span class="sxs-lookup"><span data-stu-id="d0ce8-141">Suffix</span></span> |       <span data-ttu-id="d0ce8-142">의미</span><span class="sxs-lookup"><span data-stu-id="d0ce8-142">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="d0ce8-143">일</span><span class="sxs-lookup"><span data-stu-id="d0ce8-143">d</span></span>      | <span data-ttu-id="d0ce8-144">decimal 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d0ce8-144">decimal data type</span></span>   |
| <span data-ttu-id="d0ce8-145">kb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-145">kb</span></span>     | <span data-ttu-id="d0ce8-146">kb 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-146">kilobyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-147">mb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-147">mb</span></span>     | <span data-ttu-id="d0ce8-148">메가바이트 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-148">megabyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-149">35</span><span class="sxs-lookup"><span data-stu-id="d0ce8-149">gb</span></span>     | <span data-ttu-id="d0ce8-150">gb 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-150">gigabyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-151">1tb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-151">tb</span></span>     | <span data-ttu-id="d0ce8-152">테라바이트 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-152">terabyte multiplier</span></span> |
| <span data-ttu-id="d0ce8-153">pb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-153">pb</span></span>     | <span data-ttu-id="d0ce8-154">페타바이트 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-154">petabyte multiplier</span></span> |

<span data-ttu-id="d0ce8-155">실수 리터럴의 두 가지 종류는 double과 decimal입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-155">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="d0ce8-156">이러한 숫자는 각각 decimal 형식 접미사의 유무에 따라 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-156">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="d0ce8-157">PowerShell은 값의 리터럴 표현을 지원 하지 않습니다 `[float]` .</span><span class="sxs-lookup"><span data-stu-id="d0ce8-157">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="d0ce8-158">Double 실수 리터럴의 형식은 `[double]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-158">A double real literal has type `[double]`.</span></span> <span data-ttu-id="d0ce8-159">Decimal 실수 리터럴의 형식은 `[decimal]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-159">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="d0ce8-160">Decimal 실수 리터럴의 소수 부분에 있는 뒤에 오는 0은 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-160">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="d0ce8-161">실제 리터럴의 지 수-부분 숫자 값 `[double]` 이 지원 되는 최소값 보다 작은 경우 해당 `[double]` 실수 리터럴의 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-161">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="d0ce8-162">실제 리터럴의 지 수-부분 숫자 값 `[decimal]` 이 지원 되는 최소값 보다 작은 경우 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-162">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="d0ce8-163">또는 실제 리터럴의 지 수-부분 숫자 값 `[double]` `[decimal]` 이 지원 되는 최대값 보다 큰 경우 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-163">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="d0ce8-164">구문을 사용 하 여 이중 실제 리터럴에 long 형식 접미사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-164">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="d0ce8-165">PowerShell은이 사례를 값이 형식으로 표현 되는 정수 리터럴로 처리 `[long]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-165">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="d0ce8-166">이 기능은 이전 버전의 PowerShell과의 호환성을 위해 유지 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-166">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="d0ce8-167">그러나 프로그래머는이 형식의 정수 리터럴을 사용 하지 않는 것이 좋습니다 .이는 리터럴의 실제 값을 쉽게 모호 하 게 만들 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-167">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="d0ce8-168">예를 들어에는 값 `1.2L` 이 1이 고 값이 `1.2345e1L` 12이 고 `1.2345e-5L` 값이 0 이면 해당 값 중 어느 것도 명확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-168">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="d0ce8-169">숫자 승수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-169">Numeric multipliers</span></span>

<span data-ttu-id="d0ce8-170">편의를 위해 정수 및 실수 리터럴은 숫자 승수를 포함할 수 있으며이는 일반적으로 사용 되는 2의 거듭제곱 집합 중 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-170">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="d0ce8-171">숫자 승수는 대 문자와 소문자를 조합 하 여 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-171">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="d0ce8-172">승수 접미사는 `u` , `ul` 및 형식 접미사와 함께 사용할 수 있습니다 `l` .</span><span class="sxs-lookup"><span data-stu-id="d0ce8-172">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="d0ce8-173">승수 예</span><span class="sxs-lookup"><span data-stu-id="d0ce8-173">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="d0ce8-174">숫자 형식 액셀러레이터</span><span class="sxs-lookup"><span data-stu-id="d0ce8-174">Numeric type accelerators</span></span>

<span data-ttu-id="d0ce8-175">PowerShell은 다음과 같은 유형 가속기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-175">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="d0ce8-176">액셀러레이터</span><span class="sxs-lookup"><span data-stu-id="d0ce8-176">Accelerator</span></span> |         <span data-ttu-id="d0ce8-177">참고</span><span class="sxs-lookup"><span data-stu-id="d0ce8-177">Note</span></span>         |           <span data-ttu-id="d0ce8-178">Description</span><span class="sxs-lookup"><span data-stu-id="d0ce8-178">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="d0ce8-179">바이트 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="d0ce8-179">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="d0ce8-180">바이트 (부호 있음)</span><span class="sxs-lookup"><span data-stu-id="d0ce8-180">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="d0ce8-181">16 비트 정수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-181">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="d0ce8-182">16 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="d0ce8-182">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="d0ce8-183">32비트 정수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-183">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="d0ce8-184">별칭 `[int32]`</span><span class="sxs-lookup"><span data-stu-id="d0ce8-184">alias for `[int32]`</span></span>  | <span data-ttu-id="d0ce8-185">32비트 정수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-185">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="d0ce8-186">32 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="d0ce8-186">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="d0ce8-187">64비트 정수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-187">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="d0ce8-188">별칭 `[int64]`</span><span class="sxs-lookup"><span data-stu-id="d0ce8-188">alias for `[int64]`</span></span>  | <span data-ttu-id="d0ce8-189">64비트 정수</span><span class="sxs-lookup"><span data-stu-id="d0ce8-189">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="d0ce8-190">64 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="d0ce8-190">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="d0ce8-191">[BigInteger 구조체][bigint] 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-191">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="d0ce8-192">단일 정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="d0ce8-192">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="d0ce8-193">별칭 `[single]`</span><span class="sxs-lookup"><span data-stu-id="d0ce8-193">alias for `[single]`</span></span> | <span data-ttu-id="d0ce8-194">단일 정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="d0ce8-194">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="d0ce8-195">배정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="d0ce8-195">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="d0ce8-196">128 비트 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="d0ce8-196">128-bit floating point</span></span>           |

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="d0ce8-197">다른 숫자 형식 작업</span><span class="sxs-lookup"><span data-stu-id="d0ce8-197">Working with other numeric types</span></span>

<span data-ttu-id="d0ce8-198">다른 숫자 형식으로 작업 하려면 일부 문제가 없는 형식 액셀러레이터를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-198">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="d0ce8-199">예를 들어, 상위 정수 값은 다른 형식으로 캐스팅 되기 전에 항상 double로 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-199">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="d0ce8-200">값은 double로 구문 분석 되 고 더 높은 범위의 전체 자릿수가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-200">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="d0ce8-201">이 문제를 방지 하려면 값을 문자열로 입력 하 고 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-201">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="d0ce8-202">예</span><span class="sxs-lookup"><span data-stu-id="d0ce8-202">Examples</span></span>

<span data-ttu-id="d0ce8-203">다음 표에서는 숫자 리터럴의 몇 가지 예를 포함 하 고 해당 형식 및 값을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-203">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="d0ce8-204">숫자</span><span class="sxs-lookup"><span data-stu-id="d0ce8-204">Number</span></span>  |  <span data-ttu-id="d0ce8-205">유형</span><span class="sxs-lookup"><span data-stu-id="d0ce8-205">Type</span></span>   |    <span data-ttu-id="d0ce8-206">값</span><span class="sxs-lookup"><span data-stu-id="d0ce8-206">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="d0ce8-207">100</span><span class="sxs-lookup"><span data-stu-id="d0ce8-207">100</span></span> | <span data-ttu-id="d0ce8-208">Int32</span><span class="sxs-lookup"><span data-stu-id="d0ce8-208">Int32</span></span>   |          <span data-ttu-id="d0ce8-209">100</span><span class="sxs-lookup"><span data-stu-id="d0ce8-209">100</span></span> |
|     <span data-ttu-id="d0ce8-210">100D</span><span class="sxs-lookup"><span data-stu-id="d0ce8-210">100D</span></span> | <span data-ttu-id="d0ce8-211">Decimal</span><span class="sxs-lookup"><span data-stu-id="d0ce8-211">Decimal</span></span> |          <span data-ttu-id="d0ce8-212">100</span><span class="sxs-lookup"><span data-stu-id="d0ce8-212">100</span></span> |
|     <span data-ttu-id="d0ce8-213">100l</span><span class="sxs-lookup"><span data-stu-id="d0ce8-213">100l</span></span> | <span data-ttu-id="d0ce8-214">Int64</span><span class="sxs-lookup"><span data-stu-id="d0ce8-214">Int64</span></span>   |          <span data-ttu-id="d0ce8-215">100</span><span class="sxs-lookup"><span data-stu-id="d0ce8-215">100</span></span> |
|      <span data-ttu-id="d0ce8-216">1e2</span><span class="sxs-lookup"><span data-stu-id="d0ce8-216">1e2</span></span> | <span data-ttu-id="d0ce8-217">Double</span><span class="sxs-lookup"><span data-stu-id="d0ce8-217">Double</span></span>  |          <span data-ttu-id="d0ce8-218">100</span><span class="sxs-lookup"><span data-stu-id="d0ce8-218">100</span></span> |
|     <span data-ttu-id="d0ce8-219">1. e2</span><span class="sxs-lookup"><span data-stu-id="d0ce8-219">1.e2</span></span> | <span data-ttu-id="d0ce8-220">Double</span><span class="sxs-lookup"><span data-stu-id="d0ce8-220">Double</span></span>  |          <span data-ttu-id="d0ce8-221">100</span><span class="sxs-lookup"><span data-stu-id="d0ce8-221">100</span></span> |
|    <span data-ttu-id="d0ce8-222">0x1e2</span><span class="sxs-lookup"><span data-stu-id="d0ce8-222">0x1e2</span></span> | <span data-ttu-id="d0ce8-223">Int32</span><span class="sxs-lookup"><span data-stu-id="d0ce8-223">Int32</span></span>   |          <span data-ttu-id="d0ce8-224">482</span><span class="sxs-lookup"><span data-stu-id="d0ce8-224">482</span></span> |
|   <span data-ttu-id="d0ce8-225">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="d0ce8-225">0x1e2L</span></span> | <span data-ttu-id="d0ce8-226">Int64</span><span class="sxs-lookup"><span data-stu-id="d0ce8-226">Int64</span></span>   |          <span data-ttu-id="d0ce8-227">482</span><span class="sxs-lookup"><span data-stu-id="d0ce8-227">482</span></span> |
|   <span data-ttu-id="d0ce8-228">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="d0ce8-228">0x1e2D</span></span> | <span data-ttu-id="d0ce8-229">Int32</span><span class="sxs-lookup"><span data-stu-id="d0ce8-229">Int32</span></span>   |         <span data-ttu-id="d0ce8-230">7725</span><span class="sxs-lookup"><span data-stu-id="d0ce8-230">7725</span></span> |
|     <span data-ttu-id="d0ce8-231">482D</span><span class="sxs-lookup"><span data-stu-id="d0ce8-231">482D</span></span> | <span data-ttu-id="d0ce8-232">Decimal</span><span class="sxs-lookup"><span data-stu-id="d0ce8-232">Decimal</span></span> |          <span data-ttu-id="d0ce8-233">482</span><span class="sxs-lookup"><span data-stu-id="d0ce8-233">482</span></span> |
|    <span data-ttu-id="d0ce8-234">482gb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-234">482gb</span></span> | <span data-ttu-id="d0ce8-235">Int64</span><span class="sxs-lookup"><span data-stu-id="d0ce8-235">Int64</span></span>   | <span data-ttu-id="d0ce8-236">517543559168</span><span class="sxs-lookup"><span data-stu-id="d0ce8-236">517543559168</span></span> |
| <span data-ttu-id="d0ce8-237">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="d0ce8-237">0x1e2lgb</span></span> | <span data-ttu-id="d0ce8-238">Int64</span><span class="sxs-lookup"><span data-stu-id="d0ce8-238">Int64</span></span>   | <span data-ttu-id="d0ce8-239">517543559168</span><span class="sxs-lookup"><span data-stu-id="d0ce8-239">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="d0ce8-240">숫자 리터럴과 같은 명령</span><span class="sxs-lookup"><span data-stu-id="d0ce8-240">Commands that look like numeric literals</span></span>

<span data-ttu-id="d0ce8-241">숫자 리터럴 처럼 보이는 명령은 호출 연산자 ()를 사용 하 여 실행 해야 합니다 `&` . 그렇지 않으면 연결 된 형식의 숫자로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-241">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="d0ce8-242">숫자 개체의 속성 및 메서드 액세스</span><span class="sxs-lookup"><span data-stu-id="d0ce8-242">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="d0ce8-243">숫자 리터럴의 멤버에 액세스 하려면 리터럴을 괄호로 묶어야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-243">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="d0ce8-244">리터럴에 소수점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-244">The literal does not have a decimal point</span></span>
- <span data-ttu-id="d0ce8-245">리터럴의 소수점 뒤에 숫자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-245">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="d0ce8-246">리터럴에 접미사가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-246">The literal does not have a suffix</span></span>

<span data-ttu-id="d0ce8-247">예를 들어 다음 예제는 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-247">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="d0ce8-248">다음 예제가 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-248">The following examples work:</span></span>

```
PS> 2L.GetType().Name
Int64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="d0ce8-249">PowerShell 파서는 숫자 리터럴이 끝나고 **GetType** 메서드가 시작 되는 위치를 결정할 수 있기 때문에 처음 두 예제는 괄호 안에 리터럴 값을 포함 하지 않고 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0ce8-249">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
