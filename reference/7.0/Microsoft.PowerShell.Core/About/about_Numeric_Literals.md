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
# <a name="about-numeric-literals"></a><span data-ttu-id="627b9-103">숫자 리터럴 정보</span><span class="sxs-lookup"><span data-stu-id="627b9-103">About numeric literals</span></span>

<span data-ttu-id="627b9-104">숫자 리터럴에는 integer와 real의 두 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="627b9-105">둘 다 형식 및 승수 접미사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="627b9-106">정수 리터럴</span><span class="sxs-lookup"><span data-stu-id="627b9-106">Integer literals</span></span>

<span data-ttu-id="627b9-107">정수 리터럴은 10 진수, 16 진수 또는 이진 표기법으로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-107">Integer literals can be written in decimal, hexadecimal, or binary notation.</span></span>
<span data-ttu-id="627b9-108">16 진수 리터럴에는 접두사가 `0x` 있고, 이진 리터럴의 접두사는 `0b` 10 진수와 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-108">Hexadecimal literals are prefixed with `0x` and binary literals are prefixed with `0b` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="627b9-109">정수 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="627b9-110">접미사</span><span class="sxs-lookup"><span data-stu-id="627b9-110">Suffix</span></span> |            <span data-ttu-id="627b9-111">의미</span><span class="sxs-lookup"><span data-stu-id="627b9-111">Meaning</span></span>             |          <span data-ttu-id="627b9-112">참고</span><span class="sxs-lookup"><span data-stu-id="627b9-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="627b9-113">y</span><span class="sxs-lookup"><span data-stu-id="627b9-113">y</span></span>      | <span data-ttu-id="627b9-114">부호 있는 바이트 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-114">signed byte data type</span></span>          | <span data-ttu-id="627b9-115">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="627b9-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="627b9-116">uy</span><span class="sxs-lookup"><span data-stu-id="627b9-116">uy</span></span>     | <span data-ttu-id="627b9-117">unsigned byte 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-117">unsigned byte data type</span></span>        | <span data-ttu-id="627b9-118">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="627b9-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="627b9-119">초</span><span class="sxs-lookup"><span data-stu-id="627b9-119">s</span></span>      | <span data-ttu-id="627b9-120">short 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-120">short data type</span></span>                | <span data-ttu-id="627b9-121">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="627b9-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="627b9-122">us</span><span class="sxs-lookup"><span data-stu-id="627b9-122">us</span></span>     | <span data-ttu-id="627b9-123">unsigned short 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-123">unsigned short data type</span></span>       | <span data-ttu-id="627b9-124">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="627b9-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="627b9-125">l</span><span class="sxs-lookup"><span data-stu-id="627b9-125">l</span></span>      | <span data-ttu-id="627b9-126">long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-126">long data type</span></span>                 |                         |
| <span data-ttu-id="627b9-127">u</span><span class="sxs-lookup"><span data-stu-id="627b9-127">u</span></span>      | <span data-ttu-id="627b9-128">unsigned int 또는 long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-128">unsigned int or long data type</span></span> | <span data-ttu-id="627b9-129">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="627b9-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="627b9-130">ul</span><span class="sxs-lookup"><span data-stu-id="627b9-130">ul</span></span>     | <span data-ttu-id="627b9-131">unsigned long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-131">unsigned long data type</span></span>        | <span data-ttu-id="627b9-132">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="627b9-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="627b9-133">n</span><span class="sxs-lookup"><span data-stu-id="627b9-133">n</span></span>      | <span data-ttu-id="627b9-134">BigInteger 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-134">BigInteger data type</span></span>           | <span data-ttu-id="627b9-135">PowerShell 7.0에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="627b9-135">Added in PowerShell 7.0</span></span> |
| <span data-ttu-id="627b9-136">kb</span><span class="sxs-lookup"><span data-stu-id="627b9-136">kb</span></span>     | <span data-ttu-id="627b9-137">kb 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-137">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="627b9-138">mb</span><span class="sxs-lookup"><span data-stu-id="627b9-138">mb</span></span>     | <span data-ttu-id="627b9-139">메가바이트 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-139">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="627b9-140">35</span><span class="sxs-lookup"><span data-stu-id="627b9-140">gb</span></span>     | <span data-ttu-id="627b9-141">gb 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-141">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="627b9-142">1tb</span><span class="sxs-lookup"><span data-stu-id="627b9-142">tb</span></span>     | <span data-ttu-id="627b9-143">테라바이트 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-143">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="627b9-144">pb</span><span class="sxs-lookup"><span data-stu-id="627b9-144">pb</span></span>     | <span data-ttu-id="627b9-145">페타바이트 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-145">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="627b9-146">정수 리터럴의 형식은 해당 값, 형식 접미사 및 숫자 승수 접미사로 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-146">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="627b9-147">형식 접미사가 없는 정수 리터럴의 경우:</span><span class="sxs-lookup"><span data-stu-id="627b9-147">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="627b9-148">값을 형식으로 나타낼 수 있으면 해당 `[int]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-148">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="627b9-149">그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[long]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-149">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="627b9-150">그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[decimal]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-150">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="627b9-151">그렇지 않으면 형식으로 표현 됩니다 `[double]` .</span><span class="sxs-lookup"><span data-stu-id="627b9-151">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="627b9-152">형식 접미사가 있는 정수 리터럴의 경우:</span><span class="sxs-lookup"><span data-stu-id="627b9-152">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="627b9-153">형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[uint]` 해당 형식은 `[uint]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-153">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="627b9-154">형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[ulong]` 해당 형식은 `[ulong]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-154">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="627b9-155">해당 값을 지정 된 형식으로 나타낼 수 있으면 해당 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-155">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="627b9-156">그렇지 않으면 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-156">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="627b9-157">real 리터럴</span><span class="sxs-lookup"><span data-stu-id="627b9-157">Real literals</span></span>

<span data-ttu-id="627b9-158">실수 리터럴은 소수 표기법 으로만 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-158">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="627b9-159">이 표기법은 지 수 부분을 사용 하 여 소수점이 나 과학적 표기법 뒤에 소수 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-159">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="627b9-160">지 수 부분에는 ' e ' 뒤에 선택적 기호 (+/-)와 지 수를 나타내는 숫자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-160">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="627b9-161">예를 들어 리터럴 값은 `1e2` 숫자 값 100와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-161">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="627b9-162">실제 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-162">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="627b9-163">접미사</span><span class="sxs-lookup"><span data-stu-id="627b9-163">Suffix</span></span> |       <span data-ttu-id="627b9-164">의미</span><span class="sxs-lookup"><span data-stu-id="627b9-164">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="627b9-165">일</span><span class="sxs-lookup"><span data-stu-id="627b9-165">d</span></span>      | <span data-ttu-id="627b9-166">decimal 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="627b9-166">decimal data type</span></span>   |
| <span data-ttu-id="627b9-167">kb</span><span class="sxs-lookup"><span data-stu-id="627b9-167">kb</span></span>     | <span data-ttu-id="627b9-168">kb 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-168">kilobyte multiplier</span></span> |
| <span data-ttu-id="627b9-169">mb</span><span class="sxs-lookup"><span data-stu-id="627b9-169">mb</span></span>     | <span data-ttu-id="627b9-170">메가바이트 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-170">megabyte multiplier</span></span> |
| <span data-ttu-id="627b9-171">35</span><span class="sxs-lookup"><span data-stu-id="627b9-171">gb</span></span>     | <span data-ttu-id="627b9-172">gb 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-172">gigabyte multiplier</span></span> |
| <span data-ttu-id="627b9-173">1tb</span><span class="sxs-lookup"><span data-stu-id="627b9-173">tb</span></span>     | <span data-ttu-id="627b9-174">테라바이트 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-174">terabyte multiplier</span></span> |
| <span data-ttu-id="627b9-175">pb</span><span class="sxs-lookup"><span data-stu-id="627b9-175">pb</span></span>     | <span data-ttu-id="627b9-176">페타바이트 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-176">petabyte multiplier</span></span> |

<span data-ttu-id="627b9-177">실수 리터럴의 두 가지 종류는 double과 decimal입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-177">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="627b9-178">이러한 숫자는 각각 decimal 형식 접미사의 유무에 따라 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-178">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="627b9-179">PowerShell은 값의 리터럴 표현을 지원 하지 않습니다 `[float]` .</span><span class="sxs-lookup"><span data-stu-id="627b9-179">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="627b9-180">Double 실수 리터럴의 형식은 `[double]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-180">A double real literal has type `[double]`.</span></span> <span data-ttu-id="627b9-181">Decimal 실수 리터럴의 형식은 `[decimal]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-181">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="627b9-182">Decimal 실수 리터럴의 소수 부분에 있는 뒤에 오는 0은 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-182">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="627b9-183">실제 리터럴의 지 수-부분 숫자 값 `[double]` 이 지원 되는 최소값 보다 작은 경우 해당 `[double]` 실수 리터럴의 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-183">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="627b9-184">실제 리터럴의 지 수-부분 숫자 값 `[decimal]` 이 지원 되는 최소값 보다 작은 경우 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-184">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="627b9-185">또는 실제 리터럴의 지 수-부분 숫자 값 `[double]` `[decimal]` 이 지원 되는 최대값 보다 큰 경우 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-185">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="627b9-186">구문을 사용 하 여 이중 실제 리터럴에 long 형식 접미사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-186">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="627b9-187">PowerShell은이 사례를 값이 형식으로 표현 되는 정수 리터럴로 처리 `[long]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-187">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="627b9-188">이 기능은 이전 버전의 PowerShell과의 호환성을 위해 유지 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-188">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="627b9-189">그러나 프로그래머는이 형식의 정수 리터럴을 사용 하지 않는 것이 좋습니다 .이는 리터럴의 실제 값을 쉽게 모호 하 게 만들 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-189">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="627b9-190">예를 들어에는 값 `1.2L` 이 1이 고 값이 `1.2345e1L` 12이 고 `1.2345e-5L` 값이 0 이면 해당 값 중 어느 것도 명확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-190">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="627b9-191">숫자 승수</span><span class="sxs-lookup"><span data-stu-id="627b9-191">Numeric multipliers</span></span>

<span data-ttu-id="627b9-192">편의를 위해 정수 및 실수 리터럴은 숫자 승수를 포함할 수 있으며이는 일반적으로 사용 되는 2의 거듭제곱 집합 중 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-192">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="627b9-193">숫자 승수는 대 문자와 소문자를 조합 하 여 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-193">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="627b9-194">승수 접미사는 형식 접미사와 함께 사용할 수 있지만 형식 접미사 뒤에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-194">The multiplier suffixes can be used in combination with any type suffixes, but must be present after the type suffix.</span></span> <span data-ttu-id="627b9-195">예를 들어 리터럴의 `100gbL` 형식이 잘못 되었지만 리터럴이 `100Lgb` 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-195">For example, the literal `100gbL` is malformed, but the literal `100Lgb` is valid.</span></span>

<span data-ttu-id="627b9-196">승수에서 지정 하는 숫자 형식에 사용할 수 있는 값을 초과 하는 값을 만드는 경우 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-196">If a multiplier creates a value that exceeds the possible values for the numeric type that the suffix specifies, the literal is malformed.</span></span> <span data-ttu-id="627b9-197">예를 들어, `1usgb` 값 `1gb` 이 접미사로 지정 된 형식에 허용 되는 값 보다 크므로 리터럴의 형식이 잘못 되었습니다 `[ushort]` `us` .</span><span class="sxs-lookup"><span data-stu-id="627b9-197">For example, the literal `1usgb` is malformed, because the value `1gb` is larger than what is permitted for the `[ushort]` type specified by the `us` suffix.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="627b9-198">승수 예</span><span class="sxs-lookup"><span data-stu-id="627b9-198">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="627b9-199">숫자 형식 액셀러레이터</span><span class="sxs-lookup"><span data-stu-id="627b9-199">Numeric type accelerators</span></span>

<span data-ttu-id="627b9-200">PowerShell은 다음과 같은 유형 가속기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-200">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="627b9-201">액셀러레이터</span><span class="sxs-lookup"><span data-stu-id="627b9-201">Accelerator</span></span> |         <span data-ttu-id="627b9-202">참고</span><span class="sxs-lookup"><span data-stu-id="627b9-202">Note</span></span>         |           <span data-ttu-id="627b9-203">Description</span><span class="sxs-lookup"><span data-stu-id="627b9-203">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="627b9-204">바이트 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="627b9-204">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="627b9-205">바이트 (부호 있음)</span><span class="sxs-lookup"><span data-stu-id="627b9-205">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="627b9-206">16 비트 정수</span><span class="sxs-lookup"><span data-stu-id="627b9-206">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="627b9-207">별칭 `[int16]`</span><span class="sxs-lookup"><span data-stu-id="627b9-207">alias for `[int16]`</span></span>  | <span data-ttu-id="627b9-208">16 비트 정수</span><span class="sxs-lookup"><span data-stu-id="627b9-208">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="627b9-209">16 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="627b9-209">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="627b9-210">별칭 `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="627b9-210">alias for `[uint16]`</span></span> | <span data-ttu-id="627b9-211">16 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="627b9-211">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="627b9-212">32비트 정수</span><span class="sxs-lookup"><span data-stu-id="627b9-212">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="627b9-213">별칭 `[int32]`</span><span class="sxs-lookup"><span data-stu-id="627b9-213">alias for `[int32]`</span></span>  | <span data-ttu-id="627b9-214">32비트 정수</span><span class="sxs-lookup"><span data-stu-id="627b9-214">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="627b9-215">32 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="627b9-215">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="627b9-216">별칭 `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="627b9-216">alias for `[uint32]`</span></span> | <span data-ttu-id="627b9-217">32 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="627b9-217">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="627b9-218">64비트 정수</span><span class="sxs-lookup"><span data-stu-id="627b9-218">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="627b9-219">별칭 `[int64]`</span><span class="sxs-lookup"><span data-stu-id="627b9-219">alias for `[int64]`</span></span>  | <span data-ttu-id="627b9-220">64비트 정수</span><span class="sxs-lookup"><span data-stu-id="627b9-220">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="627b9-221">64 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="627b9-221">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="627b9-222">별칭 `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="627b9-222">alias for `[uint64]`</span></span> | <span data-ttu-id="627b9-223">64 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="627b9-223">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="627b9-224">[BigInteger 구조체][bigint] 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="627b9-224">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="627b9-225">단일 정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="627b9-225">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="627b9-226">별칭 `[single]`</span><span class="sxs-lookup"><span data-stu-id="627b9-226">alias for `[single]`</span></span> | <span data-ttu-id="627b9-227">단일 정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="627b9-227">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="627b9-228">배정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="627b9-228">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="627b9-229">128 비트 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="627b9-229">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="627b9-230">PowerShell 6.2에 추가 된 형식 액셀러레이터는 `[short]` , `[ushort]` , `[uint]` , `[ulong]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-230">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

## <a name="examples"></a><span data-ttu-id="627b9-231">예제</span><span class="sxs-lookup"><span data-stu-id="627b9-231">Examples</span></span>

<span data-ttu-id="627b9-232">다음 표에서는 숫자 리터럴의 몇 가지 예를 포함 하 고 해당 형식 및 값을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-232">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|   <span data-ttu-id="627b9-233">번호</span><span class="sxs-lookup"><span data-stu-id="627b9-233">Number</span></span>     |  <span data-ttu-id="627b9-234">Type</span><span class="sxs-lookup"><span data-stu-id="627b9-234">Type</span></span>      |    <span data-ttu-id="627b9-235">값</span><span class="sxs-lookup"><span data-stu-id="627b9-235">Value</span></span>     |
| -----------: | ---------- | -----------: |
|         <span data-ttu-id="627b9-236">100</span><span class="sxs-lookup"><span data-stu-id="627b9-236">100</span></span>  | <span data-ttu-id="627b9-237">Int32</span><span class="sxs-lookup"><span data-stu-id="627b9-237">Int32</span></span>      |          <span data-ttu-id="627b9-238">100</span><span class="sxs-lookup"><span data-stu-id="627b9-238">100</span></span> |
|        <span data-ttu-id="627b9-239">100u</span><span class="sxs-lookup"><span data-stu-id="627b9-239">100u</span></span>  | <span data-ttu-id="627b9-240">UInt32</span><span class="sxs-lookup"><span data-stu-id="627b9-240">UInt32</span></span>     |          <span data-ttu-id="627b9-241">100</span><span class="sxs-lookup"><span data-stu-id="627b9-241">100</span></span> |
|        <span data-ttu-id="627b9-242">100D</span><span class="sxs-lookup"><span data-stu-id="627b9-242">100D</span></span>  | <span data-ttu-id="627b9-243">Decimal</span><span class="sxs-lookup"><span data-stu-id="627b9-243">Decimal</span></span>    |          <span data-ttu-id="627b9-244">100</span><span class="sxs-lookup"><span data-stu-id="627b9-244">100</span></span> |
|        <span data-ttu-id="627b9-245">100l</span><span class="sxs-lookup"><span data-stu-id="627b9-245">100l</span></span>  | <span data-ttu-id="627b9-246">Int64</span><span class="sxs-lookup"><span data-stu-id="627b9-246">Int64</span></span>      |          <span data-ttu-id="627b9-247">100</span><span class="sxs-lookup"><span data-stu-id="627b9-247">100</span></span> |
|       <span data-ttu-id="627b9-248">100uL</span><span class="sxs-lookup"><span data-stu-id="627b9-248">100uL</span></span>  | <span data-ttu-id="627b9-249">UInt64</span><span class="sxs-lookup"><span data-stu-id="627b9-249">UInt64</span></span>     |          <span data-ttu-id="627b9-250">100</span><span class="sxs-lookup"><span data-stu-id="627b9-250">100</span></span> |
|       <span data-ttu-id="627b9-251">100us</span><span class="sxs-lookup"><span data-stu-id="627b9-251">100us</span></span>  | <span data-ttu-id="627b9-252">UInt16</span><span class="sxs-lookup"><span data-stu-id="627b9-252">UInt16</span></span>     |          <span data-ttu-id="627b9-253">100</span><span class="sxs-lookup"><span data-stu-id="627b9-253">100</span></span> |
|       <span data-ttu-id="627b9-254">100uy</span><span class="sxs-lookup"><span data-stu-id="627b9-254">100uy</span></span>  | <span data-ttu-id="627b9-255">Byte</span><span class="sxs-lookup"><span data-stu-id="627b9-255">Byte</span></span>       |          <span data-ttu-id="627b9-256">100</span><span class="sxs-lookup"><span data-stu-id="627b9-256">100</span></span> |
|        <span data-ttu-id="627b9-257">100y</span><span class="sxs-lookup"><span data-stu-id="627b9-257">100y</span></span>  | <span data-ttu-id="627b9-258">SByte</span><span class="sxs-lookup"><span data-stu-id="627b9-258">SByte</span></span>      |          <span data-ttu-id="627b9-259">100</span><span class="sxs-lookup"><span data-stu-id="627b9-259">100</span></span> |
|         <span data-ttu-id="627b9-260">1e2</span><span class="sxs-lookup"><span data-stu-id="627b9-260">1e2</span></span>  | <span data-ttu-id="627b9-261">Double</span><span class="sxs-lookup"><span data-stu-id="627b9-261">Double</span></span>     |          <span data-ttu-id="627b9-262">100</span><span class="sxs-lookup"><span data-stu-id="627b9-262">100</span></span> |
|        <span data-ttu-id="627b9-263">1. e2</span><span class="sxs-lookup"><span data-stu-id="627b9-263">1.e2</span></span>  | <span data-ttu-id="627b9-264">Double</span><span class="sxs-lookup"><span data-stu-id="627b9-264">Double</span></span>     |          <span data-ttu-id="627b9-265">100</span><span class="sxs-lookup"><span data-stu-id="627b9-265">100</span></span> |
|       <span data-ttu-id="627b9-266">0x1e2</span><span class="sxs-lookup"><span data-stu-id="627b9-266">0x1e2</span></span>  | <span data-ttu-id="627b9-267">Int32</span><span class="sxs-lookup"><span data-stu-id="627b9-267">Int32</span></span>      |          <span data-ttu-id="627b9-268">482</span><span class="sxs-lookup"><span data-stu-id="627b9-268">482</span></span> |
|      <span data-ttu-id="627b9-269">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="627b9-269">0x1e2L</span></span>  | <span data-ttu-id="627b9-270">Int64</span><span class="sxs-lookup"><span data-stu-id="627b9-270">Int64</span></span>      |          <span data-ttu-id="627b9-271">482</span><span class="sxs-lookup"><span data-stu-id="627b9-271">482</span></span> |
|      <span data-ttu-id="627b9-272">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="627b9-272">0x1e2D</span></span>  | <span data-ttu-id="627b9-273">Int32</span><span class="sxs-lookup"><span data-stu-id="627b9-273">Int32</span></span>      |         <span data-ttu-id="627b9-274">7725</span><span class="sxs-lookup"><span data-stu-id="627b9-274">7725</span></span> |
|        <span data-ttu-id="627b9-275">482D</span><span class="sxs-lookup"><span data-stu-id="627b9-275">482D</span></span>  | <span data-ttu-id="627b9-276">Decimal</span><span class="sxs-lookup"><span data-stu-id="627b9-276">Decimal</span></span>    |          <span data-ttu-id="627b9-277">482</span><span class="sxs-lookup"><span data-stu-id="627b9-277">482</span></span> |
|       <span data-ttu-id="627b9-278">482gb</span><span class="sxs-lookup"><span data-stu-id="627b9-278">482gb</span></span>  | <span data-ttu-id="627b9-279">Int64</span><span class="sxs-lookup"><span data-stu-id="627b9-279">Int64</span></span>      | <span data-ttu-id="627b9-280">517543559168</span><span class="sxs-lookup"><span data-stu-id="627b9-280">517543559168</span></span> |
|       <span data-ttu-id="627b9-281">482ngb</span><span class="sxs-lookup"><span data-stu-id="627b9-281">482ngb</span></span> | <span data-ttu-id="627b9-282">BigInteger</span><span class="sxs-lookup"><span data-stu-id="627b9-282">BigInteger</span></span> | <span data-ttu-id="627b9-283">517543559168</span><span class="sxs-lookup"><span data-stu-id="627b9-283">517543559168</span></span> |
|    <span data-ttu-id="627b9-284">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="627b9-284">0x1e2lgb</span></span>  | <span data-ttu-id="627b9-285">Int64</span><span class="sxs-lookup"><span data-stu-id="627b9-285">Int64</span></span>      | <span data-ttu-id="627b9-286">517543559168</span><span class="sxs-lookup"><span data-stu-id="627b9-286">517543559168</span></span> |
|   <span data-ttu-id="627b9-287">0b1011011</span><span class="sxs-lookup"><span data-stu-id="627b9-287">0b1011011</span></span>  | <span data-ttu-id="627b9-288">Int32</span><span class="sxs-lookup"><span data-stu-id="627b9-288">Int32</span></span>      |           <span data-ttu-id="627b9-289">91</span><span class="sxs-lookup"><span data-stu-id="627b9-289">91</span></span> |
|  <span data-ttu-id="627b9-290">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="627b9-290">0xFFFFFFFF</span></span>  | <span data-ttu-id="627b9-291">Int32</span><span class="sxs-lookup"><span data-stu-id="627b9-291">Int32</span></span>      |           <span data-ttu-id="627b9-292">-1</span><span class="sxs-lookup"><span data-stu-id="627b9-292">-1</span></span> |
| <span data-ttu-id="627b9-293">-0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="627b9-293">-0xFFFFFFFF</span></span>  | <span data-ttu-id="627b9-294">Int32</span><span class="sxs-lookup"><span data-stu-id="627b9-294">Int32</span></span>      |            <span data-ttu-id="627b9-295">1</span><span class="sxs-lookup"><span data-stu-id="627b9-295">1</span></span> |
| <span data-ttu-id="627b9-296">0xFFFFFFFFu</span><span class="sxs-lookup"><span data-stu-id="627b9-296">0xFFFFFFFFu</span></span>  | <span data-ttu-id="627b9-297">UInt32</span><span class="sxs-lookup"><span data-stu-id="627b9-297">UInt32</span></span>     |   <span data-ttu-id="627b9-298">4294967295</span><span class="sxs-lookup"><span data-stu-id="627b9-298">4294967295</span></span> |

### <a name="working-with-binary-or-hexadecimal-numbers"></a><span data-ttu-id="627b9-299">이진 또는 16 진수를 사용 하 여 작업</span><span class="sxs-lookup"><span data-stu-id="627b9-299">Working with binary or hexadecimal numbers</span></span>

<span data-ttu-id="627b9-300">접미사가 지정 된 경우에만 너무 큼 이진 또는 16 진수 리터럴은 `[bigint]` 구문 분석에 실패 하는 것이 아니라로 반환 될 수 있습니다 `n` .</span><span class="sxs-lookup"><span data-stu-id="627b9-300">Overly large binary or hexadecimal literals can return as `[bigint]` rather than failing the parse, if and only if the `n` suffix is specified.</span></span> <span data-ttu-id="627b9-301">하지만 부호 비트는 여전히 범위 내 `[decimal]` 에서 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-301">Sign bits are still respected above even `[decimal]` ranges, however:</span></span>

- <span data-ttu-id="627b9-302">이진 문자열이 8 비트 long의 배수가 면 가장 높은 비트가 부호 비트로 취급 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-302">If a binary string is some multiple of 8 bits long, the highest bit is treated as the sign bit.</span></span>
- <span data-ttu-id="627b9-303">길이가 8 인 16 진수 문자열의 첫 번째 숫자가 8 이상인 경우 숫자는 음수로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-303">If a hex string, which has a length that is a multiple of 8, has the first digit with 8 or higher, the numeral is treated as negative.</span></span>

<span data-ttu-id="627b9-304">이진 및 16 진수 리터럴에 부호 없는 접미사를 지정 하면 부호 비트가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-304">Specifying an unsigned suffix on binary and hex literals ignores sign bits.</span></span> <span data-ttu-id="627b9-305">예를 들어 `0xFFFFFFFF` 는 `-1` 를 반환 하지만 `0xFFFFFFFFu` 4294967295의를 반환 합니다 `[uint]::MaxValue` .</span><span class="sxs-lookup"><span data-stu-id="627b9-305">For example, `0xFFFFFFFF` returns `-1`, but `0xFFFFFFFFu` returns the `[uint]::MaxValue` of 4294967295.</span></span>

<span data-ttu-id="627b9-306">을 사용 하 여 리터럴을 접두사로 사용 `0` 하면이를 무시 하 고 unsigned로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-306">Prefixing the literal with a `0` will bypass this and be treated as unsigned.</span></span>
<span data-ttu-id="627b9-307">예를 들면 `0b011111111`과 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-307">For example: `0b011111111`.</span></span> <span data-ttu-id="627b9-308">이는 범위의 리터럴을 사용할 때 `[bigint]` 와 접미사를 결합할 수 없기 때문에 필요할 수 있습니다 `u` `n` .</span><span class="sxs-lookup"><span data-stu-id="627b9-308">This can be necessary when working with literals in the `[bigint]` range, as the `u` and `n` suffixes cannot be combined.</span></span>

<span data-ttu-id="627b9-309">접두사를 사용 하 여 이진 및 16 진 리터럴을 부정할 수도 있습니다 `-` .</span><span class="sxs-lookup"><span data-stu-id="627b9-309">You can also negate binary and hex literals using the `-` prefix.</span></span> <span data-ttu-id="627b9-310">그러면 부호 비트가 허용 되므로 양수가 반환 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-310">This can result in a positive number since sign bits are permitted.</span></span>

<span data-ttu-id="627b9-311">BigInteger-접미사 숫자에는 부호 비트가 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-311">Sign bits are accepted for BigInteger-suffixed numerals:</span></span>

- <span data-ttu-id="627b9-312">BigInteger hex는 부호 비트로 8 자의 길이가 배수 인 리터럴의 상위 비트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-312">BigInteger-suffixed hex treats the high bit of any literal with a length multiple of 8 characters as the sign bit.</span></span> <span data-ttu-id="627b9-313">길이는 접두사 또는 접미사를 포함 하지 않습니다 `0x` .</span><span class="sxs-lookup"><span data-stu-id="627b9-313">The length does not include the `0x` prefix or any suffixes.</span></span>
- <span data-ttu-id="627b9-314">BigInteger는 96 및 128 문자에서 부호 비트를 허용 하 고,은 8 자 마다 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-314">BigInteger-suffixed binary accepts sign bits at 96 and 128 characters, and at every 8 characters after.</span></span>

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="627b9-315">숫자 리터럴과 같은 명령</span><span class="sxs-lookup"><span data-stu-id="627b9-315">Commands that look like numeric literals</span></span>

<span data-ttu-id="627b9-316">유효한 숫자 리터럴 처럼 보이는 명령은 호출 연산자 ()를 사용 하 여 실행 해야 합니다 `&` . 그렇지 않으면 숫자로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-316">Any command that looks like a valid numeric literal must be executed using the call operator (`&`), otherwise it is interpreted as a number.</span></span> <span data-ttu-id="627b9-317">올바른 구문이 있는 형식이 잘못 된 리터럴은 `1usgb` 다음과 같은 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-317">Malformed literals with valid syntax like `1usgb` will result in the following error:</span></span>

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

<span data-ttu-id="627b9-318">그러나 잘못 된 구문을 사용 하는 잘못 된 형식의 리터럴은 `1gbus` 표준 기본 문자열로 해석 되 고 명령이 호출 될 수 있는 컨텍스트에서 유효한 명령 이름으로 해석 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-318">However, malformed literals with invalid syntax like `1gbus` will be interpreted as a standard bare string, and can be interpreted as a valid command name in contexts where commands may be called.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="627b9-319">숫자 개체의 속성 및 메서드 액세스</span><span class="sxs-lookup"><span data-stu-id="627b9-319">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="627b9-320">숫자 리터럴의 멤버에 액세스 하려면 리터럴을 괄호로 묶어야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-320">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="627b9-321">리터럴에 소수점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-321">The literal does not have a decimal point</span></span>
- <span data-ttu-id="627b9-322">리터럴의 소수점 뒤에 숫자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-322">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="627b9-323">리터럴에 접미사가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-323">The literal does not have a suffix</span></span>

<span data-ttu-id="627b9-324">예를 들어 다음 예제는 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-324">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="627b9-325">다음 예제가 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-325">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="627b9-326">PowerShell 파서는 숫자 리터럴이 끝나고 **GetType** 메서드가 시작 되는 위치를 결정할 수 있기 때문에 처음 두 예제는 괄호 안에 리터럴 값을 포함 하지 않고 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-326">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

## <a name="how-powershell-parses-numeric-literals"></a><span data-ttu-id="627b9-327">PowerShell에서 숫자 리터럴을 구문 분석 하는 방법</span><span class="sxs-lookup"><span data-stu-id="627b9-327">How PowerShell parses numeric literals</span></span>

<span data-ttu-id="627b9-328">PowerShell v 7.0은 새 기능을 사용할 수 있도록 숫자 리터럴이 구문 분석 되는 방식을 변경 했습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-328">PowerShell v7.0 changed the way numeric literals are parsed to enable the new features.</span></span>

### <a name="parsing-real-numeric-literals"></a><span data-ttu-id="627b9-329">실수 리터럴 구문 분석</span><span class="sxs-lookup"><span data-stu-id="627b9-329">Parsing real numeric literals</span></span>

<span data-ttu-id="627b9-330">리터럴에 소수점이 나 e 표기법이 포함 된 경우 리터럴 문자열은 실수를 구문 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-330">If the literal contains a decimal point or the e-notation, the literal string is parsed a real number.</span></span>

- <span data-ttu-id="627b9-331">10 진수 접미사가 있으면에 직접 표시 됩니다 `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="627b9-331">If the decimal-suffix is present then directly into `[decimal]`.</span></span>
- <span data-ttu-id="627b9-332">또는를로 구문 분석 하 `[Double]` 고 값에 승수를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-332">Else, parse as `[Double]` and apply multiplier to the value.</span></span> <span data-ttu-id="627b9-333">그런 다음 형식 접미사를 확인 하 고 적절 한 형식으로 캐스팅 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-333">Then check the type suffixes and attempt to cast into appropriate type.</span></span>
- <span data-ttu-id="627b9-334">문자열에 형식 접미사가 없으면로 구문 분석 `[Double]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-334">If the string has no type suffix, then parse as `[Double]`.</span></span>

### <a name="paring-integer-numeric-literals"></a><span data-ttu-id="627b9-335">Paring 정수 숫자 리터럴</span><span class="sxs-lookup"><span data-stu-id="627b9-335">Paring integer numeric literals</span></span>

<span data-ttu-id="627b9-336">정수 형식 리터럴은 다음 단계를 사용 하 여 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-336">Integer type literals are parsed using the following steps:</span></span>

1. <span data-ttu-id="627b9-337">기 하 형식 결정</span><span class="sxs-lookup"><span data-stu-id="627b9-337">Determine the radix format</span></span>
   - <span data-ttu-id="627b9-338">이진 형식의 경우로 구문 분석 `[BigInteger]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-338">For binary formats, parse into `[BigInteger]`.</span></span>
   - <span data-ttu-id="627b9-339">16 진수 형식의 경우 `[BigInteger]` 값이 또는 범위에 있을 때 원래 동작을 유지 하기 위해 특수 casies 사용 하 여로 구문 분석 `[int]` `[long]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-339">For hexidecimal formats, parse into `[BigInteger]` using special casies to retain original behaviours when the value is in the `[int]` or `[long]` range.</span></span>
   - <span data-ttu-id="627b9-340">Binary와 hex가 둘 다 없는 경우는 정상적으로로 구문 분석 `[BigInteger]` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-340">If neither binary nor hex, parse normally as a `[BigInteger]`.</span></span>
2. <span data-ttu-id="627b9-341">캐스트를 시도 하기 전에 승수 값을 적용 하 여 형식 범위를 오버플로 없이 적절히 확인할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-341">Apply the multiplier value before attempting any casts to ensure type bounds can be appropriately checked without overflows.</span></span>
3. <span data-ttu-id="627b9-342">유형 접미사를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-342">Check type suffixes.</span></span>
   - <span data-ttu-id="627b9-343">형식 범위를 확인 하 고 해당 형식으로 구문 분석을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-343">Check type bounds and attempt to parse into that type.</span></span>
   - <span data-ttu-id="627b9-344">접미사를 사용 하지 않는 경우 값은 다음 순서로 범위가 결정 됩니다. 그러면 첫 번째 성공한 테스트가 숫자의 형식을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-344">If no suffix is used, then the value is bounds-checked in the following order, resulting in the first successful test determining the type of the number.</span></span>
     - `[int]`
     - `[long]`
     - <span data-ttu-id="627b9-345">`[decimal]` (기본-10 리터럴 전용)</span><span class="sxs-lookup"><span data-stu-id="627b9-345">`[decimal]` (base-10 literals only)</span></span>
     - <span data-ttu-id="627b9-346">`[double]` (기본-10 리터럴 전용)</span><span class="sxs-lookup"><span data-stu-id="627b9-346">`[double]` (base-10 literals only)</span></span>
   - <span data-ttu-id="627b9-347">값이 `[long]` 16 진수 및 이진 숫자 범위를 벗어나면 구문 분석이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-347">If the value is outside the `[long]` range for hex and binary numbers, the parse fails.</span></span>
   - <span data-ttu-id="627b9-348">값이 `[double]` base 10 number의 범위를 벗어나면 구문 분석이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-348">If the value is outside the `[double]` range for base 10 number, the parse fails.</span></span>
   - <span data-ttu-id="627b9-349">`n`리터럴을로 구문 분석 하려면 접미사를 사용 하 여 더 높은 값을 명시적으로 작성 해야 합니다 `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="627b9-349">Higher values must be explicitly written using the `n` suffix to parse the literal as a `BigInteger`.</span></span>

### <a name="parsing-large-value-literals"></a><span data-ttu-id="627b9-350">대량 값 리터럴 구문 분석</span><span class="sxs-lookup"><span data-stu-id="627b9-350">Parsing large value literals</span></span>

<span data-ttu-id="627b9-351">이전에는 더 높은 정수 값이 다른 형식으로 캐스팅 되기 전에 double로 구문 분석 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-351">Previously, higher integer values were parsed as double before being cast to any other type.</span></span> <span data-ttu-id="627b9-352">이로 인해 더 높은 범위의 전체 자릿수가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-352">This results in a loss of precision in the higher ranges.</span></span> <span data-ttu-id="627b9-353">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-353">For example:</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="627b9-354">이 문제를 방지 하려면 값을 문자열로 쓴 다음 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-354">To avoid this problem you had to write values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="627b9-355">PowerShell 7.0에서는 접미사를 사용 해야 합니다 `N` .</span><span class="sxs-lookup"><span data-stu-id="627b9-355">In PowerShell 7.0 you must use the `N` suffix.</span></span>

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="627b9-356">또한 및 사이의 값은 `[ulong]::MaxValue` `[decimal]::MaxValue` `D` 정확도를 유지 하기 위해 10 진수 접미사를 사용 하 여 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-356">Also values between `[ulong]::MaxValue` and `[decimal]::MaxValue` should be denoted using the decimal-suffix `D` to maintain accuracy.</span></span> <span data-ttu-id="627b9-357">접미사가 없으면 이러한 값은 `[Double]` 실제 구문 분석 모드를 사용 하 여 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="627b9-357">Without the suffix, these values are parsed as `[Double]` using the real-parsing mode.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
