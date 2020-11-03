---
description: 정수 및 실수 리터럴은 모두 형식 및 승수 접미사를 사용할 수 있습니다.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 숫자 리터럴 정보
ms.openlocfilehash: 62f00ae9f3643724808146134fd03b6f01c29bce
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224689"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="2b8ea-103">숫자 리터럴 정보</span><span class="sxs-lookup"><span data-stu-id="2b8ea-103">About numeric literals</span></span>

<span data-ttu-id="2b8ea-104">숫자 리터럴에는 integer와 real의 두 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="2b8ea-105">둘 다 형식 및 승수 접미사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="2b8ea-106">정수 리터럴</span><span class="sxs-lookup"><span data-stu-id="2b8ea-106">Integer literals</span></span>

<span data-ttu-id="2b8ea-107">정수 리터럴은 10 진수 또는 16 진수 표기법으로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="2b8ea-108">16 진수 리터럴의 접두사는 `0x` 10 진수와 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="2b8ea-109">정수 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="2b8ea-110">접미사</span><span class="sxs-lookup"><span data-stu-id="2b8ea-110">Suffix</span></span> |            <span data-ttu-id="2b8ea-111">의미</span><span class="sxs-lookup"><span data-stu-id="2b8ea-111">Meaning</span></span>             |          <span data-ttu-id="2b8ea-112">참고</span><span class="sxs-lookup"><span data-stu-id="2b8ea-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="2b8ea-113">y</span><span class="sxs-lookup"><span data-stu-id="2b8ea-113">y</span></span>      | <span data-ttu-id="2b8ea-114">부호 있는 바이트 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-114">signed byte data type</span></span>          | <span data-ttu-id="2b8ea-115">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="2b8ea-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="2b8ea-116">uy</span><span class="sxs-lookup"><span data-stu-id="2b8ea-116">uy</span></span>     | <span data-ttu-id="2b8ea-117">unsigned byte 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-117">unsigned byte data type</span></span>        | <span data-ttu-id="2b8ea-118">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="2b8ea-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="2b8ea-119">초</span><span class="sxs-lookup"><span data-stu-id="2b8ea-119">s</span></span>      | <span data-ttu-id="2b8ea-120">short 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-120">short data type</span></span>                | <span data-ttu-id="2b8ea-121">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="2b8ea-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="2b8ea-122">us</span><span class="sxs-lookup"><span data-stu-id="2b8ea-122">us</span></span>     | <span data-ttu-id="2b8ea-123">unsigned short 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-123">unsigned short data type</span></span>       | <span data-ttu-id="2b8ea-124">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="2b8ea-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="2b8ea-125">l</span><span class="sxs-lookup"><span data-stu-id="2b8ea-125">l</span></span>      | <span data-ttu-id="2b8ea-126">long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-126">long data type</span></span>                 |                         |
| <span data-ttu-id="2b8ea-127">u</span><span class="sxs-lookup"><span data-stu-id="2b8ea-127">u</span></span>      | <span data-ttu-id="2b8ea-128">unsigned int 또는 long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-128">unsigned int or long data type</span></span> | <span data-ttu-id="2b8ea-129">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="2b8ea-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="2b8ea-130">ul</span><span class="sxs-lookup"><span data-stu-id="2b8ea-130">ul</span></span>     | <span data-ttu-id="2b8ea-131">unsigned long 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-131">unsigned long data type</span></span>        | <span data-ttu-id="2b8ea-132">PowerShell 6.2에 추가 됨</span><span class="sxs-lookup"><span data-stu-id="2b8ea-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="2b8ea-133">kb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-133">kb</span></span>     | <span data-ttu-id="2b8ea-134">kb 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-134">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="2b8ea-135">mb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-135">mb</span></span>     | <span data-ttu-id="2b8ea-136">메가바이트 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-136">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="2b8ea-137">35</span><span class="sxs-lookup"><span data-stu-id="2b8ea-137">gb</span></span>     | <span data-ttu-id="2b8ea-138">gb 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-138">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="2b8ea-139">1tb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-139">tb</span></span>     | <span data-ttu-id="2b8ea-140">테라바이트 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-140">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="2b8ea-141">pb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-141">pb</span></span>     | <span data-ttu-id="2b8ea-142">페타바이트 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-142">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="2b8ea-143">정수 리터럴의 형식은 해당 값, 형식 접미사 및 숫자 승수 접미사로 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-143">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="2b8ea-144">형식 접미사가 없는 정수 리터럴의 경우:</span><span class="sxs-lookup"><span data-stu-id="2b8ea-144">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="2b8ea-145">값을 형식으로 나타낼 수 있으면 해당 `[int]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-145">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="2b8ea-146">그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[long]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-146">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="2b8ea-147">그렇지 않고 값이 형식으로 표현 될 수 있는 경우 해당 `[decimal]` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-147">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="2b8ea-148">그렇지 않으면 형식으로 표현 됩니다 `[double]` .</span><span class="sxs-lookup"><span data-stu-id="2b8ea-148">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="2b8ea-149">형식 접미사가 있는 정수 리터럴의 경우:</span><span class="sxs-lookup"><span data-stu-id="2b8ea-149">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="2b8ea-150">형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[uint]` 해당 형식은 `[uint]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-150">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="2b8ea-151">형식 접미사가이 `u` 고 값을 형식으로 표시할 수 있는 경우 `[ulong]` 해당 형식은 `[ulong]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-151">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="2b8ea-152">해당 값을 지정 된 형식으로 나타낼 수 있으면 해당 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-152">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="2b8ea-153">그렇지 않으면 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-153">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="2b8ea-154">real 리터럴</span><span class="sxs-lookup"><span data-stu-id="2b8ea-154">Real literals</span></span>

<span data-ttu-id="2b8ea-155">실수 리터럴은 소수 표기법 으로만 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-155">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="2b8ea-156">이 표기법은 지 수 부분을 사용 하 여 소수점이 나 과학적 표기법 뒤에 소수 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-156">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="2b8ea-157">지 수 부분에는 ' e ' 뒤에 선택적 기호 (+/-)와 지 수를 나타내는 숫자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-157">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="2b8ea-158">예를 들어 리터럴 값은 `1e2` 숫자 값 100와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-158">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="2b8ea-159">실제 리터럴에는 형식 접미사와 승수 접미사가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-159">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="2b8ea-160">접미사</span><span class="sxs-lookup"><span data-stu-id="2b8ea-160">Suffix</span></span> |       <span data-ttu-id="2b8ea-161">의미</span><span class="sxs-lookup"><span data-stu-id="2b8ea-161">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="2b8ea-162">일</span><span class="sxs-lookup"><span data-stu-id="2b8ea-162">d</span></span>      | <span data-ttu-id="2b8ea-163">decimal 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2b8ea-163">decimal data type</span></span>   |
| <span data-ttu-id="2b8ea-164">kb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-164">kb</span></span>     | <span data-ttu-id="2b8ea-165">kb 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-165">kilobyte multiplier</span></span> |
| <span data-ttu-id="2b8ea-166">mb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-166">mb</span></span>     | <span data-ttu-id="2b8ea-167">메가바이트 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-167">megabyte multiplier</span></span> |
| <span data-ttu-id="2b8ea-168">35</span><span class="sxs-lookup"><span data-stu-id="2b8ea-168">gb</span></span>     | <span data-ttu-id="2b8ea-169">gb 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-169">gigabyte multiplier</span></span> |
| <span data-ttu-id="2b8ea-170">1tb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-170">tb</span></span>     | <span data-ttu-id="2b8ea-171">테라바이트 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-171">terabyte multiplier</span></span> |
| <span data-ttu-id="2b8ea-172">pb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-172">pb</span></span>     | <span data-ttu-id="2b8ea-173">페타바이트 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-173">petabyte multiplier</span></span> |

<span data-ttu-id="2b8ea-174">실수 리터럴의 두 가지 종류는 double과 decimal입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-174">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="2b8ea-175">이러한 숫자는 각각 decimal 형식 접미사의 유무에 따라 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-175">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="2b8ea-176">PowerShell은 값의 리터럴 표현을 지원 하지 않습니다 `[float]` .</span><span class="sxs-lookup"><span data-stu-id="2b8ea-176">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="2b8ea-177">Double 실수 리터럴의 형식은 `[double]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-177">A double real literal has type `[double]`.</span></span> <span data-ttu-id="2b8ea-178">Decimal 실수 리터럴의 형식은 `[decimal]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-178">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="2b8ea-179">Decimal 실수 리터럴의 소수 부분에 있는 뒤에 오는 0은 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-179">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="2b8ea-180">실제 리터럴의 지 수-부분 숫자 값 `[double]` 이 지원 되는 최소값 보다 작은 경우 해당 `[double]` 실수 리터럴의 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-180">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="2b8ea-181">실제 리터럴의 지 수-부분 숫자 값 `[decimal]` 이 지원 되는 최소값 보다 작은 경우 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-181">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="2b8ea-182">또는 실제 리터럴의 지 수-부분 숫자 값 `[double]` `[decimal]` 이 지원 되는 최대값 보다 큰 경우 리터럴의 형식이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-182">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="2b8ea-183">구문을 사용 하 여 이중 실제 리터럴에 long 형식 접미사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-183">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="2b8ea-184">PowerShell은이 사례를 값이 형식으로 표현 되는 정수 리터럴로 처리 `[long]` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-184">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="2b8ea-185">이 기능은 이전 버전의 PowerShell과의 호환성을 위해 유지 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-185">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="2b8ea-186">그러나 프로그래머는이 형식의 정수 리터럴을 사용 하지 않는 것이 좋습니다 .이는 리터럴의 실제 값을 쉽게 모호 하 게 만들 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-186">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="2b8ea-187">예를 들어에는 값 `1.2L` 이 1이 고 값이 `1.2345e1L` 12이 고 `1.2345e-5L` 값이 0 이면 해당 값 중 어느 것도 명확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-187">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="2b8ea-188">숫자 승수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-188">Numeric multipliers</span></span>

<span data-ttu-id="2b8ea-189">편의를 위해 정수 및 실수 리터럴은 숫자 승수를 포함할 수 있으며이는 일반적으로 사용 되는 2의 거듭제곱 집합 중 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-189">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="2b8ea-190">숫자 승수는 대 문자와 소문자를 조합 하 여 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-190">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="2b8ea-191">승수 접미사는 `u` , `ul` 및 형식 접미사와 함께 사용할 수 있습니다 `l` .</span><span class="sxs-lookup"><span data-stu-id="2b8ea-191">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="2b8ea-192">승수 예</span><span class="sxs-lookup"><span data-stu-id="2b8ea-192">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="2b8ea-193">숫자 형식 액셀러레이터</span><span class="sxs-lookup"><span data-stu-id="2b8ea-193">Numeric type accelerators</span></span>

<span data-ttu-id="2b8ea-194">PowerShell은 다음과 같은 유형 가속기를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-194">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="2b8ea-195">액셀러레이터</span><span class="sxs-lookup"><span data-stu-id="2b8ea-195">Accelerator</span></span> |         <span data-ttu-id="2b8ea-196">참고</span><span class="sxs-lookup"><span data-stu-id="2b8ea-196">Note</span></span>         |           <span data-ttu-id="2b8ea-197">Description</span><span class="sxs-lookup"><span data-stu-id="2b8ea-197">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="2b8ea-198">바이트 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-198">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="2b8ea-199">바이트 (부호 있음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-199">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="2b8ea-200">16 비트 정수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-200">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="2b8ea-201">별칭 `[int16]`</span><span class="sxs-lookup"><span data-stu-id="2b8ea-201">alias for `[int16]`</span></span>  | <span data-ttu-id="2b8ea-202">16 비트 정수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-202">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="2b8ea-203">16 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-203">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="2b8ea-204">별칭 `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="2b8ea-204">alias for `[uint16]`</span></span> | <span data-ttu-id="2b8ea-205">16 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-205">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="2b8ea-206">32비트 정수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-206">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="2b8ea-207">별칭 `[int32]`</span><span class="sxs-lookup"><span data-stu-id="2b8ea-207">alias for `[int32]`</span></span>  | <span data-ttu-id="2b8ea-208">32비트 정수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-208">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="2b8ea-209">32 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-209">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="2b8ea-210">별칭 `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="2b8ea-210">alias for `[uint32]`</span></span> | <span data-ttu-id="2b8ea-211">32 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-211">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="2b8ea-212">64비트 정수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-212">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="2b8ea-213">별칭 `[int64]`</span><span class="sxs-lookup"><span data-stu-id="2b8ea-213">alias for `[int64]`</span></span>  | <span data-ttu-id="2b8ea-214">64비트 정수</span><span class="sxs-lookup"><span data-stu-id="2b8ea-214">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="2b8ea-215">64 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-215">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="2b8ea-216">별칭 `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="2b8ea-216">alias for `[uint64]`</span></span> | <span data-ttu-id="2b8ea-217">64 비트 정수 (부호 없음)</span><span class="sxs-lookup"><span data-stu-id="2b8ea-217">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="2b8ea-218">[BigInteger 구조체][bigint] 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-218">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="2b8ea-219">단일 정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="2b8ea-219">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="2b8ea-220">별칭 `[single]`</span><span class="sxs-lookup"><span data-stu-id="2b8ea-220">alias for `[single]`</span></span> | <span data-ttu-id="2b8ea-221">단일 정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="2b8ea-221">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="2b8ea-222">배정밀도 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="2b8ea-222">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="2b8ea-223">128 비트 부동 소수점</span><span class="sxs-lookup"><span data-stu-id="2b8ea-223">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="2b8ea-224">PowerShell 6.2에 추가 된 형식 액셀러레이터는 `[short]` , `[ushort]` , `[uint]` , `[ulong]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-224">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="2b8ea-225">다른 숫자 형식 작업</span><span class="sxs-lookup"><span data-stu-id="2b8ea-225">Working with other numeric types</span></span>

<span data-ttu-id="2b8ea-226">다른 숫자 형식으로 작업 하려면 일부 문제가 없는 형식 액셀러레이터를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-226">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="2b8ea-227">예를 들어, 상위 정수 값은 다른 형식으로 캐스팅 되기 전에 항상 double로 구문 분석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-227">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="2b8ea-228">값은 double로 구문 분석 되 고 더 높은 범위의 전체 자릿수가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-228">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="2b8ea-229">이 문제를 방지 하려면 값을 문자열로 입력 하 고 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-229">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="2b8ea-230">예</span><span class="sxs-lookup"><span data-stu-id="2b8ea-230">Examples</span></span>

<span data-ttu-id="2b8ea-231">다음 표에서는 숫자 리터럴의 몇 가지 예를 포함 하 고 해당 형식 및 값을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-231">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="2b8ea-232">숫자</span><span class="sxs-lookup"><span data-stu-id="2b8ea-232">Number</span></span>  |  <span data-ttu-id="2b8ea-233">유형</span><span class="sxs-lookup"><span data-stu-id="2b8ea-233">Type</span></span>   |    <span data-ttu-id="2b8ea-234">값</span><span class="sxs-lookup"><span data-stu-id="2b8ea-234">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="2b8ea-235">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-235">100</span></span> | <span data-ttu-id="2b8ea-236">Int32</span><span class="sxs-lookup"><span data-stu-id="2b8ea-236">Int32</span></span>   |          <span data-ttu-id="2b8ea-237">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-237">100</span></span> |
|     <span data-ttu-id="2b8ea-238">100D</span><span class="sxs-lookup"><span data-stu-id="2b8ea-238">100D</span></span> | <span data-ttu-id="2b8ea-239">Decimal</span><span class="sxs-lookup"><span data-stu-id="2b8ea-239">Decimal</span></span> |          <span data-ttu-id="2b8ea-240">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-240">100</span></span> |
|     <span data-ttu-id="2b8ea-241">100l</span><span class="sxs-lookup"><span data-stu-id="2b8ea-241">100l</span></span> | <span data-ttu-id="2b8ea-242">Int64</span><span class="sxs-lookup"><span data-stu-id="2b8ea-242">Int64</span></span>   |          <span data-ttu-id="2b8ea-243">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-243">100</span></span> |
|    <span data-ttu-id="2b8ea-244">100uL</span><span class="sxs-lookup"><span data-stu-id="2b8ea-244">100uL</span></span> | <span data-ttu-id="2b8ea-245">UInt64</span><span class="sxs-lookup"><span data-stu-id="2b8ea-245">UInt64</span></span>  |          <span data-ttu-id="2b8ea-246">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-246">100</span></span> |
|    <span data-ttu-id="2b8ea-247">100us</span><span class="sxs-lookup"><span data-stu-id="2b8ea-247">100us</span></span> | <span data-ttu-id="2b8ea-248">UInt16</span><span class="sxs-lookup"><span data-stu-id="2b8ea-248">UInt16</span></span>  |          <span data-ttu-id="2b8ea-249">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-249">100</span></span> |
|    <span data-ttu-id="2b8ea-250">100uy</span><span class="sxs-lookup"><span data-stu-id="2b8ea-250">100uy</span></span> | <span data-ttu-id="2b8ea-251">Byte</span><span class="sxs-lookup"><span data-stu-id="2b8ea-251">Byte</span></span>    |          <span data-ttu-id="2b8ea-252">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-252">100</span></span> |
|     <span data-ttu-id="2b8ea-253">100y</span><span class="sxs-lookup"><span data-stu-id="2b8ea-253">100y</span></span> | <span data-ttu-id="2b8ea-254">SByte</span><span class="sxs-lookup"><span data-stu-id="2b8ea-254">SByte</span></span>   |          <span data-ttu-id="2b8ea-255">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-255">100</span></span> |
|      <span data-ttu-id="2b8ea-256">1e2</span><span class="sxs-lookup"><span data-stu-id="2b8ea-256">1e2</span></span> | <span data-ttu-id="2b8ea-257">Double</span><span class="sxs-lookup"><span data-stu-id="2b8ea-257">Double</span></span>  |          <span data-ttu-id="2b8ea-258">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-258">100</span></span> |
|     <span data-ttu-id="2b8ea-259">1. e2</span><span class="sxs-lookup"><span data-stu-id="2b8ea-259">1.e2</span></span> | <span data-ttu-id="2b8ea-260">Double</span><span class="sxs-lookup"><span data-stu-id="2b8ea-260">Double</span></span>  |          <span data-ttu-id="2b8ea-261">100</span><span class="sxs-lookup"><span data-stu-id="2b8ea-261">100</span></span> |
|    <span data-ttu-id="2b8ea-262">0x1e2</span><span class="sxs-lookup"><span data-stu-id="2b8ea-262">0x1e2</span></span> | <span data-ttu-id="2b8ea-263">Int32</span><span class="sxs-lookup"><span data-stu-id="2b8ea-263">Int32</span></span>   |          <span data-ttu-id="2b8ea-264">482</span><span class="sxs-lookup"><span data-stu-id="2b8ea-264">482</span></span> |
|   <span data-ttu-id="2b8ea-265">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="2b8ea-265">0x1e2L</span></span> | <span data-ttu-id="2b8ea-266">Int64</span><span class="sxs-lookup"><span data-stu-id="2b8ea-266">Int64</span></span>   |          <span data-ttu-id="2b8ea-267">482</span><span class="sxs-lookup"><span data-stu-id="2b8ea-267">482</span></span> |
|   <span data-ttu-id="2b8ea-268">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="2b8ea-268">0x1e2D</span></span> | <span data-ttu-id="2b8ea-269">Int32</span><span class="sxs-lookup"><span data-stu-id="2b8ea-269">Int32</span></span>   |         <span data-ttu-id="2b8ea-270">7725</span><span class="sxs-lookup"><span data-stu-id="2b8ea-270">7725</span></span> |
|     <span data-ttu-id="2b8ea-271">482D</span><span class="sxs-lookup"><span data-stu-id="2b8ea-271">482D</span></span> | <span data-ttu-id="2b8ea-272">Decimal</span><span class="sxs-lookup"><span data-stu-id="2b8ea-272">Decimal</span></span> |          <span data-ttu-id="2b8ea-273">482</span><span class="sxs-lookup"><span data-stu-id="2b8ea-273">482</span></span> |
|    <span data-ttu-id="2b8ea-274">482gb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-274">482gb</span></span> | <span data-ttu-id="2b8ea-275">Int64</span><span class="sxs-lookup"><span data-stu-id="2b8ea-275">Int64</span></span>   | <span data-ttu-id="2b8ea-276">517543559168</span><span class="sxs-lookup"><span data-stu-id="2b8ea-276">517543559168</span></span> |
| <span data-ttu-id="2b8ea-277">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="2b8ea-277">0x1e2lgb</span></span> | <span data-ttu-id="2b8ea-278">Int64</span><span class="sxs-lookup"><span data-stu-id="2b8ea-278">Int64</span></span>   | <span data-ttu-id="2b8ea-279">517543559168</span><span class="sxs-lookup"><span data-stu-id="2b8ea-279">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="2b8ea-280">숫자 리터럴과 같은 명령</span><span class="sxs-lookup"><span data-stu-id="2b8ea-280">Commands that look like numeric literals</span></span>

<span data-ttu-id="2b8ea-281">숫자 리터럴 처럼 보이는 명령은 호출 연산자 ()를 사용 하 여 실행 해야 합니다 `&` . 그렇지 않으면 연결 된 형식의 숫자로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-281">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="2b8ea-282">숫자 개체의 속성 및 메서드 액세스</span><span class="sxs-lookup"><span data-stu-id="2b8ea-282">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="2b8ea-283">숫자 리터럴의 멤버에 액세스 하려면 리터럴을 괄호로 묶어야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-283">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="2b8ea-284">리터럴에 소수점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-284">The literal does not have a decimal point</span></span>
- <span data-ttu-id="2b8ea-285">리터럴의 소수점 뒤에 숫자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-285">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="2b8ea-286">리터럴에 접미사가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-286">The literal does not have a suffix</span></span>

<span data-ttu-id="2b8ea-287">예를 들어 다음 예제는 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-287">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="2b8ea-288">다음 예제가 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-288">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="2b8ea-289">PowerShell 파서는 숫자 리터럴이 끝나고 **GetType** 메서드가 시작 되는 위치를 결정할 수 있기 때문에 처음 두 예제는 괄호 안에 리터럴 값을 포함 하지 않고 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8ea-289">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger?view=netcore-2.2
