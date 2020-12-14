---
description: PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_comparison_operators
ms.openlocfilehash: ba671ae51d458a2e0074a85d4de859795c20a3d5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97069906"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="3daf7-103">비교 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="3daf7-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="3daf7-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="3daf7-104">Short description</span></span>
<span data-ttu-id="3daf7-105">PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-105">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3daf7-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-106">Long description</span></span>

<span data-ttu-id="3daf7-107">비교 연산자를 사용 하 여 값을 비교 하 고 지정 된 패턴과 일치 하는 값을 찾는 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-107">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="3daf7-108">비교 연산자를 사용 하려면 이러한 값을 구분 하는 연산자와 비교할 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-108">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="3daf7-109">PowerShell에는 다음과 같은 비교 연산자가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-109">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="3daf7-110">형식</span><span class="sxs-lookup"><span data-stu-id="3daf7-110">Type</span></span>        | <span data-ttu-id="3daf7-111">연산자</span><span class="sxs-lookup"><span data-stu-id="3daf7-111">Operators</span></span>    | <span data-ttu-id="3daf7-112">설명</span><span class="sxs-lookup"><span data-stu-id="3daf7-112">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="3daf7-113">같음</span><span class="sxs-lookup"><span data-stu-id="3daf7-113">Equality</span></span>    | <span data-ttu-id="3daf7-114">-eq</span><span class="sxs-lookup"><span data-stu-id="3daf7-114">-eq</span></span>          | <span data-ttu-id="3daf7-115">equals</span><span class="sxs-lookup"><span data-stu-id="3daf7-115">equals</span></span>                                      |
|             | <span data-ttu-id="3daf7-116">-ne</span><span class="sxs-lookup"><span data-stu-id="3daf7-116">-ne</span></span>          | <span data-ttu-id="3daf7-117">같지 않음</span><span class="sxs-lookup"><span data-stu-id="3daf7-117">not equals</span></span>                                  |
|             | <span data-ttu-id="3daf7-118">-gt</span><span class="sxs-lookup"><span data-stu-id="3daf7-118">-gt</span></span>          | <span data-ttu-id="3daf7-119">보다 큼</span><span class="sxs-lookup"><span data-stu-id="3daf7-119">greater than</span></span>                                |
|             | <span data-ttu-id="3daf7-120">-ge</span><span class="sxs-lookup"><span data-stu-id="3daf7-120">-ge</span></span>          | <span data-ttu-id="3daf7-121">크거나 같음</span><span class="sxs-lookup"><span data-stu-id="3daf7-121">greater than or equal</span></span>                       |
|             | <span data-ttu-id="3daf7-122">-lt</span><span class="sxs-lookup"><span data-stu-id="3daf7-122">-lt</span></span>          | <span data-ttu-id="3daf7-123">다음보다 작음</span><span class="sxs-lookup"><span data-stu-id="3daf7-123">less than</span></span>                                   |
|             | <span data-ttu-id="3daf7-124">-le</span><span class="sxs-lookup"><span data-stu-id="3daf7-124">-le</span></span>          | <span data-ttu-id="3daf7-125">작거나 같음</span><span class="sxs-lookup"><span data-stu-id="3daf7-125">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="3daf7-126">Matching</span><span class="sxs-lookup"><span data-stu-id="3daf7-126">Matching</span></span>    | <span data-ttu-id="3daf7-127">-like</span><span class="sxs-lookup"><span data-stu-id="3daf7-127">-like</span></span>        | <span data-ttu-id="3daf7-128">문자열이 와일드 카드와 일치할 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-128">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="3daf7-129">pattern</span><span class="sxs-lookup"><span data-stu-id="3daf7-129">pattern</span></span>                                     |
|             | <span data-ttu-id="3daf7-130">-notlike</span><span class="sxs-lookup"><span data-stu-id="3daf7-130">-notlike</span></span>     | <span data-ttu-id="3daf7-131">문자열이 일치 하지 않으면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-131">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="3daf7-132">와일드 카드 패턴</span><span class="sxs-lookup"><span data-stu-id="3daf7-132">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="3daf7-133">-match</span><span class="sxs-lookup"><span data-stu-id="3daf7-133">-match</span></span>       | <span data-ttu-id="3daf7-134">문자열이 regex와 일치 하면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-134">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="3daf7-135">되풀이 $matches에 일치 하는 문자열이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-135">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="3daf7-136">-notmatch</span><span class="sxs-lookup"><span data-stu-id="3daf7-136">-notmatch</span></span>    | <span data-ttu-id="3daf7-137">문자열이 일치 하지 않으면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-137">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="3daf7-138">regex 패턴; 일치 항목 포함 $matches</span><span class="sxs-lookup"><span data-stu-id="3daf7-138">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="3daf7-139">문자열</span><span class="sxs-lookup"><span data-stu-id="3daf7-139">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="3daf7-140">Containment</span><span class="sxs-lookup"><span data-stu-id="3daf7-140">Containment</span></span> | <span data-ttu-id="3daf7-141">-contains</span><span class="sxs-lookup"><span data-stu-id="3daf7-141">-contains</span></span>    | <span data-ttu-id="3daf7-142">참조 값이 포함 된 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-142">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="3daf7-143">컬렉션에서</span><span class="sxs-lookup"><span data-stu-id="3daf7-143">in a collection</span></span>                             |
|             | <span data-ttu-id="3daf7-144">-notcontains</span><span class="sxs-lookup"><span data-stu-id="3daf7-144">-notcontains</span></span> | <span data-ttu-id="3daf7-145">참조 값이이 아닌 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-145">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="3daf7-146">컬렉션에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-146">contained in a collection</span></span>                   |
|             | <span data-ttu-id="3daf7-147">-in</span><span class="sxs-lookup"><span data-stu-id="3daf7-147">-in</span></span>          | <span data-ttu-id="3daf7-148">에 포함 된 테스트 값이 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-148">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="3daf7-149">collection</span><span class="sxs-lookup"><span data-stu-id="3daf7-149">collection</span></span>                                  |
|             | <span data-ttu-id="3daf7-150">-notin</span><span class="sxs-lookup"><span data-stu-id="3daf7-150">-notin</span></span>       | <span data-ttu-id="3daf7-151">테스트 값이 포함 되지 않은 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-151">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="3daf7-152">컬렉션에서</span><span class="sxs-lookup"><span data-stu-id="3daf7-152">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="3daf7-153">Replacement</span><span class="sxs-lookup"><span data-stu-id="3daf7-153">Replacement</span></span> | <span data-ttu-id="3daf7-154">-replace</span><span class="sxs-lookup"><span data-stu-id="3daf7-154">-replace</span></span>     | <span data-ttu-id="3daf7-155">문자열 패턴을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-155">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="3daf7-156">형식</span><span class="sxs-lookup"><span data-stu-id="3daf7-156">Type</span></span>        | <span data-ttu-id="3daf7-157">-is</span><span class="sxs-lookup"><span data-stu-id="3daf7-157">-is</span></span>          | <span data-ttu-id="3daf7-158">두 개체가 같을 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-158">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="3daf7-159">형식</span><span class="sxs-lookup"><span data-stu-id="3daf7-159">type</span></span>                                        |
|             | <span data-ttu-id="3daf7-160">-isnot</span><span class="sxs-lookup"><span data-stu-id="3daf7-160">-isnot</span></span>       | <span data-ttu-id="3daf7-161">개체가 같지 않으면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-161">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="3daf7-162">형식</span><span class="sxs-lookup"><span data-stu-id="3daf7-162">type</span></span>                                        |

<span data-ttu-id="3daf7-163">기본적으로 모든 비교 연산자는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-163">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="3daf7-164">대/소문자를 구분 하는 비교 연산자를 만들려면 연산자 이름 앞에을 붙입니다 `c` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-164">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="3daf7-165">예를 들어 대/소문자를 구분 하는 버전 `-eq` 은 `-ceq` 입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-165">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="3daf7-166">대/소문자를 구분 하지 않도록 명시적으로 지정 하려면 연산자 앞에을 붙입니다 `i` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-166">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="3daf7-167">예를 들어의 명시적 대/소문자를 구분 하지 않는 버전은 `-eq` `-ieq` 입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-167">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="3daf7-168">연산자에 대 한 입력이 스칼라 값인 경우 비교 연산자는 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-168">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="3daf7-169">입력이 값 컬렉션인 경우 비교 연산자는 일치 하는 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-169">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="3daf7-170">컬렉션에 일치 하는 항목이 없는 경우 비교 연산자는 빈 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-170">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="3daf7-171">예외는 포함 연산자, In 연산자 및 형식 연산자 이며 항상 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-171">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="3daf7-172">값을 비교 해야 하는 경우 `$null` `$null` 비교의 왼쪽에를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-172">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="3daf7-173">`$null` **개체 []** 와 비교할 때 비교 개체가 배열 이기 때문에 결과가 **False** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-173">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="3daf7-174">배열을와 비교할 때 `$null` 비교는 `$null` 배열에 저장 된 모든 값을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-174">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="3daf7-175">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="3daf7-175">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a><span data-ttu-id="3daf7-176">같음 연산자</span><span class="sxs-lookup"><span data-stu-id="3daf7-176">Equality operators</span></span>

<span data-ttu-id="3daf7-177">같음 연산자 ( `-eq` , `-ne` )는 하나 이상의 입력 값이 지정 된 패턴과 동일한 경우 TRUE 또는 일치 항목의 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-177">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="3daf7-178">전체 패턴이 전체 값과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-178">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="3daf7-179">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-179">Example:</span></span>

### <a name="-eq"></a><span data-ttu-id="3daf7-180">-eq</span><span class="sxs-lookup"><span data-stu-id="3daf7-180">-eq</span></span>

<span data-ttu-id="3daf7-181">설명:가와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-181">Description: Equal to.</span></span> <span data-ttu-id="3daf7-182">에 동일한 값이 포함 된 경우</span><span class="sxs-lookup"><span data-stu-id="3daf7-182">Includes an identical value.</span></span>

<span data-ttu-id="3daf7-183">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-183">Example:</span></span>

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

### <a name="-ne"></a><span data-ttu-id="3daf7-184">-ne</span><span class="sxs-lookup"><span data-stu-id="3daf7-184">-ne</span></span>

<span data-ttu-id="3daf7-185">설명: 같지 않음</span><span class="sxs-lookup"><span data-stu-id="3daf7-185">Description: Not equal to.</span></span> <span data-ttu-id="3daf7-186">에 다른 값이 포함 된 경우</span><span class="sxs-lookup"><span data-stu-id="3daf7-186">Includes a different value.</span></span>

<span data-ttu-id="3daf7-187">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-187">Example:</span></span>

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

### <a name="-gt"></a><span data-ttu-id="3daf7-188">-gt</span><span class="sxs-lookup"><span data-stu-id="3daf7-188">-gt</span></span>

<span data-ttu-id="3daf7-189">설명: 보다 큼</span><span class="sxs-lookup"><span data-stu-id="3daf7-189">Description: Greater-than.</span></span>

<span data-ttu-id="3daf7-190">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-190">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="3daf7-191">`>`다른 많은 프로그래밍 언어의 보다 큼 연산자와 혼동 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-191">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="3daf7-192">PowerShell에서 `>` 는 리디렉션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-192">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="3daf7-193">자세한 내용은 [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3daf7-193">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

### <a name="-ge"></a><span data-ttu-id="3daf7-194">-ge</span><span class="sxs-lookup"><span data-stu-id="3daf7-194">-ge</span></span>

<span data-ttu-id="3daf7-195">설명: 크거나 같음.</span><span class="sxs-lookup"><span data-stu-id="3daf7-195">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="3daf7-196">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-196">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a><span data-ttu-id="3daf7-197">-lt</span><span class="sxs-lookup"><span data-stu-id="3daf7-197">-lt</span></span>

<span data-ttu-id="3daf7-198">설명: 보다 작음</span><span class="sxs-lookup"><span data-stu-id="3daf7-198">Description: Less-than.</span></span>

<span data-ttu-id="3daf7-199">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-199">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a><span data-ttu-id="3daf7-200">-le</span><span class="sxs-lookup"><span data-stu-id="3daf7-200">-le</span></span>

<span data-ttu-id="3daf7-201">설명: 보다 작거나 같음입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-201">Description: Less-than or equal to.</span></span>

<span data-ttu-id="3daf7-202">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-202">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a><span data-ttu-id="3daf7-203">일치 연산자</span><span class="sxs-lookup"><span data-stu-id="3daf7-203">Matching operators</span></span>

<span data-ttu-id="3daf7-204">Like 연산자 ( `-like` 및 `-notlike` )는 와일드 카드 식을 사용 하 여 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-204">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="3daf7-205">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-205">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="3daf7-206">일치 연산자 ( `-match` 및 `-notmatch` )가 정규식을 사용 하 여 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-206">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="3daf7-207">`$Matches`연산자에 대 한 입력 (왼쪽 인수)이 단일 스칼라 개체인 경우 match 연산자는 자동 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-207">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="3daf7-208">입력이 스칼라 인 경우 `-match` 및 연산자는 `-notmatch` 부울 값을 반환 하 고 `$Matches` 자동 변수 값을 인수의 일치 하는 구성 요소로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-208">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="3daf7-209">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-209">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a><span data-ttu-id="3daf7-210">-like</span><span class="sxs-lookup"><span data-stu-id="3daf7-210">-like</span></span>

<span data-ttu-id="3daf7-211">설명: 와일드 카드 문자 ()를 사용 하 여 찾습니다 \* .</span><span class="sxs-lookup"><span data-stu-id="3daf7-211">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="3daf7-212">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-212">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a><span data-ttu-id="3daf7-213">-notlike</span><span class="sxs-lookup"><span data-stu-id="3daf7-213">-notlike</span></span>

<span data-ttu-id="3daf7-214">설명: 와일드 카드 문자 ()를 사용 하 여 일치 하지 않습니다 \* .</span><span class="sxs-lookup"><span data-stu-id="3daf7-214">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="3daf7-215">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-215">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="3daf7-216">-match</span><span class="sxs-lookup"><span data-stu-id="3daf7-216">-match</span></span>

<span data-ttu-id="3daf7-217">설명: 정규식을 사용 하 여 문자열을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-217">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="3daf7-218">입력이 스칼라 인 경우 자동 변수를 채웁니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-218">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="3daf7-219">입력이 컬렉션인 경우 `-match` 및 `-notmatch` 연산자는 해당 컬렉션의 일치 하는 멤버를 반환 하지만이 연산자는 변수를 채우지 않습니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-219">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="3daf7-220">예를 들어 다음 명령은 연산자에 문자열 컬렉션을 전송 합니다 `-match` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-220">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="3daf7-221">`-match`연산자는 컬렉션에서 일치 하는 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-221">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="3daf7-222">자동 변수를 채우지 않습니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-222">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="3daf7-223">반면, 다음 명령은 단일 문자열을 운영자에 게 전송 합니다 `-match` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-223">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="3daf7-224">`-match`연산자는 부울 값을 반환 하 고 `$Matches` 자동 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-224">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="3daf7-225">`$Matches`자동 변수는 **해시 테이블** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-225">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="3daf7-226">그룹화 또는 캡처가 사용 되지 않으면 하나의 키만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-226">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="3daf7-227">`0`키는 일치 된 모든 텍스트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-227">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="3daf7-228">정규식을 사용한 그룹화 및 캡처에 대 한 자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3daf7-228">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="3daf7-229">해시 테이블에는 일치 하는 `$Matches` 패턴이 처음 나타나는 경우만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-229">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="3daf7-230">`0`키가 **정수** 입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-230">The `0` key is an **Integer**.</span></span> <span data-ttu-id="3daf7-231">모든 **Hashtable** 메서드를 사용 하 여 저장 된 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-231">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```powershell
> PS> "Good Dog" -match "Dog"
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

<span data-ttu-id="3daf7-232">`-notmatch`연산자는 입력이 `$Matches` 스칼라 인 경우 자동 변수를 채우고 결과가 False 이면 일치 하는 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-232">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

### <a name="-notmatch"></a><span data-ttu-id="3daf7-233">-notmatch</span><span class="sxs-lookup"><span data-stu-id="3daf7-233">-notmatch</span></span>

<span data-ttu-id="3daf7-234">설명:가 문자열과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-234">Description: Does not match a string.</span></span> <span data-ttu-id="3daf7-235">정규식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-235">Uses regular expressions.</span></span> <span data-ttu-id="3daf7-236">입력이 스칼라 인 경우 자동 변수를 채웁니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-236">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="3daf7-237">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-237">Example:</span></span>

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

## <a name="containment-operators"></a><span data-ttu-id="3daf7-238">포함 연산자</span><span class="sxs-lookup"><span data-stu-id="3daf7-238">Containment operators</span></span>

<span data-ttu-id="3daf7-239">포함 연산자 ( `-contains` 및 `-notcontains` )는 같음 연산자와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-239">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="3daf7-240">그러나 포함 연산자는 입력이 컬렉션인 경우에도 항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-240">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="3daf7-241">또한 같음 연산자와 달리 포함 연산자는 첫 번째 일치 항목을 검색 하는 즉시 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-241">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="3daf7-242">같음 연산자는 모든 입력을 평가한 다음 컬렉션에서 일치 하는 항목을 모두 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-242">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

### <a name="-contains"></a><span data-ttu-id="3daf7-243">-contains</span><span class="sxs-lookup"><span data-stu-id="3daf7-243">-contains</span></span>

<span data-ttu-id="3daf7-244">설명: 포함 연산자.</span><span class="sxs-lookup"><span data-stu-id="3daf7-244">Description: Containment operator.</span></span> <span data-ttu-id="3daf7-245">참조 값의 컬렉션에 단일 테스트 값이 포함 되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-245">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="3daf7-246">항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-246">Always returns a Boolean value.</span></span> <span data-ttu-id="3daf7-247">테스트 값이 하나 이상의 참조 값과 정확 하 게 일치 하는 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-247">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="3daf7-248">테스트 값이 컬렉션인 경우 Contains 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-248">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="3daf7-249">참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-249">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="3daf7-250">매우 큰 컬렉션에서 `-contains` 연산자는 같음 연산자 보다 더 빠른 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-250">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="3daf7-251">구문</span><span class="sxs-lookup"><span data-stu-id="3daf7-251">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="3daf7-252">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-252">Examples:</span></span>

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

### <a name="-notcontains"></a><span data-ttu-id="3daf7-253">-notcontains</span><span class="sxs-lookup"><span data-stu-id="3daf7-253">-notcontains</span></span>

<span data-ttu-id="3daf7-254">설명: 포함 연산자.</span><span class="sxs-lookup"><span data-stu-id="3daf7-254">Description: Containment operator.</span></span> <span data-ttu-id="3daf7-255">참조 값의 컬렉션에 단일 테스트 값이 포함 되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-255">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="3daf7-256">항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-256">Always returns a Boolean value.</span></span> <span data-ttu-id="3daf7-257">테스트 값이 하나 이상의 참조 값과 정확히 일치 하지 않는 경우 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-257">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="3daf7-258">테스트 값이 컬렉션인 경우 NotContains 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-258">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="3daf7-259">구문</span><span class="sxs-lookup"><span data-stu-id="3daf7-259">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="3daf7-260">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-260">Examples:</span></span>

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

### <a name="-in"></a><span data-ttu-id="3daf7-261">-in</span><span class="sxs-lookup"><span data-stu-id="3daf7-261">-in</span></span>

<span data-ttu-id="3daf7-262">설명: In 연산자</span><span class="sxs-lookup"><span data-stu-id="3daf7-262">Description: In operator.</span></span> <span data-ttu-id="3daf7-263">테스트 값이 참조 값의 컬렉션에 표시 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-263">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="3daf7-264">항상 부울 값으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-264">Always return as Boolean value.</span></span> <span data-ttu-id="3daf7-265">테스트 값이 하나 이상의 참조 값과 정확 하 게 일치 하는 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-265">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="3daf7-266">테스트 값이 컬렉션인 경우 In 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-266">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="3daf7-267">참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-267">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="3daf7-268">`-in`연산자는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-268">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="3daf7-269">구문</span><span class="sxs-lookup"><span data-stu-id="3daf7-269">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="3daf7-270">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-270">Examples:</span></span>

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

### <a name="-notin"></a><span data-ttu-id="3daf7-271">-notin</span><span class="sxs-lookup"><span data-stu-id="3daf7-271">-notin</span></span>

<span data-ttu-id="3daf7-272">Description: 테스트 값이 참조 값의 컬렉션에 나타나는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-272">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="3daf7-273">항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-273">Always returns a Boolean value.</span></span> <span data-ttu-id="3daf7-274">테스트 값이 하나 이상의 참조 값과 정확히 일치 하지 않는 경우 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-274">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="3daf7-275">테스트 값이 컬렉션인 경우 In 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-275">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="3daf7-276">참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-276">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="3daf7-277">`-notin`연산자는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-277">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="3daf7-278">구문</span><span class="sxs-lookup"><span data-stu-id="3daf7-278">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="3daf7-279">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-279">Examples:</span></span>

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

## <a name="replacement-operator"></a><span data-ttu-id="3daf7-280">대체 연산자</span><span class="sxs-lookup"><span data-stu-id="3daf7-280">Replacement Operator</span></span>

<span data-ttu-id="3daf7-281">`-replace`연산자의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-281">The `-replace` operator has the following syntax:</span></span>

`<input> -replace <original>, <substitute>`

<span data-ttu-id="3daf7-282">`<original>`자리 표시자는 바꿀 문자와 일치 하는 정규식입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-282">The `<original>` placeholder is a regular expression matching the characters to be replaced.</span></span> <span data-ttu-id="3daf7-283">`<substitute>`자리 표시자는이를 대체 하는 리터럴 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-283">The `<substitute>` placeholder is a literal string that replaces them.</span></span>

<span data-ttu-id="3daf7-284">연산자는 정규식을 사용 하 여 값의 일부 또는 전체를 지정 된 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-284">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="3daf7-285">파일 이름 바꾸기와 같은 많은 관리 작업에 대해 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-285">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="3daf7-286">예를 들어 다음 명령은 모든 파일의 파일 이름 확장명 `.txt` 을로 변경 합니다 `.log` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-286">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a><span data-ttu-id="3daf7-287">대/소문자 구분 일치</span><span class="sxs-lookup"><span data-stu-id="3daf7-287">Case-sensitive matches</span></span>

<span data-ttu-id="3daf7-288">기본적으로 연산자는 `-replace` 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-288">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="3daf7-289">대/소문자를 구분 하려면를 사용 `-creplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-289">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="3daf7-290">명시적으로 대/소문자를 구분 하지 않도록 하려면를 사용 `-ireplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-290">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="3daf7-291">다음 예제를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="3daf7-291">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="3daf7-292">정규식의 대체</span><span class="sxs-lookup"><span data-stu-id="3daf7-292">Substitutions in regular expressions</span></span>

<span data-ttu-id="3daf7-293">또한 정규식을 사용 하 여 캡처링 그룹 및 대체를 사용 하 여 텍스트를 동적으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-293">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="3daf7-294">`<substitute>`그룹 식별자 앞에 달러 기호 () 문자를 사용 하 여 문자열에서 캡처 그룹을 참조할 수 있습니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-294">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="3daf7-295">캡처 그룹은 **번호** 또는 **이름** 으로 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-295">Capture groups can be referenced by **Number** or **Name**</span></span>

- <span data-ttu-id="3daf7-296">**번호** 캡처링 그룹은 왼쪽에서 오른쪽으로 번호가 매겨집니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-296">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="3daf7-297">이름 **으로** 캡처링 그룹은 이름으로 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-297">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> <span data-ttu-id="3daf7-298">문자는 `$` 문자열 확장에 사용 되므로 리터럴 문자열을 사용 하거나 문자를 이스케이프 해야 합니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="3daf7-298">Since the `$` character is used in string expansion, you must use literal strings or escape the `$` character.</span></span>
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> <span data-ttu-id="3daf7-299">또한 `$` 문자가 대체에 사용 되므로 문자열의 모든 인스턴스를 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-299">Additionally, since the `$` character is used in substitution, you must escape any instances in your string.</span></span>
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

<span data-ttu-id="3daf7-300">자세히 알아보려면 정규식의 [about_Regular_Expressions](about_Regular_Expressions.md) 및 [대체](/dotnet/standard/base-types/substitutions-in-regular-expressions) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3daf7-300">To learn more see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="3daf7-301">컬렉션에서 대체</span><span class="sxs-lookup"><span data-stu-id="3daf7-301">Substituting in a collection</span></span>

<span data-ttu-id="3daf7-302">`<input>` `-replace` 연산자가 컬렉션인 경우 PowerShell은 컬렉션의 모든 값에 대체를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-302">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="3daf7-303">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="3daf7-303">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

## <a name="type-comparison"></a><span data-ttu-id="3daf7-304">형식 비교</span><span class="sxs-lookup"><span data-stu-id="3daf7-304">Type comparison</span></span>

<span data-ttu-id="3daf7-305">형식 비교 연산자 ( `-is` 및 `-isnot` )는 개체가 특정 형식 인지 여부를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3daf7-305">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

### <a name="-is"></a><span data-ttu-id="3daf7-306">-is</span><span class="sxs-lookup"><span data-stu-id="3daf7-306">-is</span></span>

<span data-ttu-id="3daf7-307">구문</span><span class="sxs-lookup"><span data-stu-id="3daf7-307">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="3daf7-308">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-308">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a><span data-ttu-id="3daf7-309">-isnot</span><span class="sxs-lookup"><span data-stu-id="3daf7-309">-isnot</span></span>

<span data-ttu-id="3daf7-310">구문</span><span class="sxs-lookup"><span data-stu-id="3daf7-310">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="3daf7-311">예제:</span><span class="sxs-lookup"><span data-stu-id="3daf7-311">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="3daf7-312">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3daf7-312">See also</span></span>

- [<span data-ttu-id="3daf7-313">about_Operators</span><span class="sxs-lookup"><span data-stu-id="3daf7-313">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="3daf7-314">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="3daf7-314">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="3daf7-315">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="3daf7-315">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="3daf7-316">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="3daf7-316">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="3daf7-317">Foreach-개체</span><span class="sxs-lookup"><span data-stu-id="3daf7-317">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="3daf7-318">Where-Object</span><span class="sxs-lookup"><span data-stu-id="3daf7-318">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
