---
description: PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_comparison_operators
ms.openlocfilehash: d6096de14d0bb8c7ba86c0585806b86cf3bb921a
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224538"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="46af7-104">비교 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="46af7-104">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="46af7-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="46af7-105">Short description</span></span>
<span data-ttu-id="46af7-106">PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-106">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="46af7-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-107">Long description</span></span>

<span data-ttu-id="46af7-108">비교 연산자를 사용 하 여 값을 비교 하 고 지정 된 패턴과 일치 하는 값을 찾는 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-108">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="46af7-109">비교 연산자를 사용 하려면 이러한 값을 구분 하는 연산자와 비교할 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-109">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="46af7-110">PowerShell에는 다음과 같은 비교 연산자가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-110">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="46af7-111">유형</span><span class="sxs-lookup"><span data-stu-id="46af7-111">Type</span></span>        | <span data-ttu-id="46af7-112">연산자</span><span class="sxs-lookup"><span data-stu-id="46af7-112">Operators</span></span>    | <span data-ttu-id="46af7-113">설명</span><span class="sxs-lookup"><span data-stu-id="46af7-113">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="46af7-114">등호</span><span class="sxs-lookup"><span data-stu-id="46af7-114">Equality</span></span>    | <span data-ttu-id="46af7-115">-eq</span><span class="sxs-lookup"><span data-stu-id="46af7-115">-eq</span></span>          | <span data-ttu-id="46af7-116">같음</span><span class="sxs-lookup"><span data-stu-id="46af7-116">equals</span></span>                                      |
|             | <span data-ttu-id="46af7-117">-ne</span><span class="sxs-lookup"><span data-stu-id="46af7-117">-ne</span></span>          | <span data-ttu-id="46af7-118">같지 않음</span><span class="sxs-lookup"><span data-stu-id="46af7-118">not equals</span></span>                                  |
|             | <span data-ttu-id="46af7-119">-gt</span><span class="sxs-lookup"><span data-stu-id="46af7-119">-gt</span></span>          | <span data-ttu-id="46af7-120">보다 큼</span><span class="sxs-lookup"><span data-stu-id="46af7-120">greater than</span></span>                                |
|             | <span data-ttu-id="46af7-121">-ge</span><span class="sxs-lookup"><span data-stu-id="46af7-121">-ge</span></span>          | <span data-ttu-id="46af7-122">크거나 같음</span><span class="sxs-lookup"><span data-stu-id="46af7-122">greater than or equal</span></span>                       |
|             | <span data-ttu-id="46af7-123">-lt</span><span class="sxs-lookup"><span data-stu-id="46af7-123">-lt</span></span>          | <span data-ttu-id="46af7-124">다음보다 작음</span><span class="sxs-lookup"><span data-stu-id="46af7-124">less than</span></span>                                   |
|             | <span data-ttu-id="46af7-125">-le</span><span class="sxs-lookup"><span data-stu-id="46af7-125">-le</span></span>          | <span data-ttu-id="46af7-126">작거나 같음</span><span class="sxs-lookup"><span data-stu-id="46af7-126">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="46af7-127">Matching</span><span class="sxs-lookup"><span data-stu-id="46af7-127">Matching</span></span>    | <span data-ttu-id="46af7-128">-like</span><span class="sxs-lookup"><span data-stu-id="46af7-128">-like</span></span>        | <span data-ttu-id="46af7-129">문자열이 와일드 카드와 일치할 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-129">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="46af7-130">pattern</span><span class="sxs-lookup"><span data-stu-id="46af7-130">pattern</span></span>                                     |
|             | <span data-ttu-id="46af7-131">-notlike</span><span class="sxs-lookup"><span data-stu-id="46af7-131">-notlike</span></span>     | <span data-ttu-id="46af7-132">문자열이 일치 하지 않으면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-132">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="46af7-133">와일드 카드 패턴</span><span class="sxs-lookup"><span data-stu-id="46af7-133">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="46af7-134">-match</span><span class="sxs-lookup"><span data-stu-id="46af7-134">-match</span></span>       | <span data-ttu-id="46af7-135">문자열이 regex와 일치 하면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-135">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="46af7-136">되풀이 $matches에 일치 하는 문자열이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-136">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="46af7-137">-notmatch</span><span class="sxs-lookup"><span data-stu-id="46af7-137">-notmatch</span></span>    | <span data-ttu-id="46af7-138">문자열이 일치 하지 않으면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-138">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="46af7-139">regex 패턴; 일치 항목 포함 $matches</span><span class="sxs-lookup"><span data-stu-id="46af7-139">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="46af7-140">문자열</span><span class="sxs-lookup"><span data-stu-id="46af7-140">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="46af7-141">Containment</span><span class="sxs-lookup"><span data-stu-id="46af7-141">Containment</span></span> | <span data-ttu-id="46af7-142">-contains</span><span class="sxs-lookup"><span data-stu-id="46af7-142">-contains</span></span>    | <span data-ttu-id="46af7-143">참조 값이 포함 된 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-143">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="46af7-144">컬렉션에서</span><span class="sxs-lookup"><span data-stu-id="46af7-144">in a collection</span></span>                             |
|             | <span data-ttu-id="46af7-145">-notcontains</span><span class="sxs-lookup"><span data-stu-id="46af7-145">-notcontains</span></span> | <span data-ttu-id="46af7-146">참조 값이이 아닌 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-146">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="46af7-147">컬렉션에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-147">contained in a collection</span></span>                   |
|             | <span data-ttu-id="46af7-148">-in</span><span class="sxs-lookup"><span data-stu-id="46af7-148">-in</span></span>          | <span data-ttu-id="46af7-149">에 포함 된 테스트 값이 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-149">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="46af7-150">collection</span><span class="sxs-lookup"><span data-stu-id="46af7-150">collection</span></span>                                  |
|             | <span data-ttu-id="46af7-151">-notin</span><span class="sxs-lookup"><span data-stu-id="46af7-151">-notin</span></span>       | <span data-ttu-id="46af7-152">테스트 값이 포함 되지 않은 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-152">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="46af7-153">컬렉션에서</span><span class="sxs-lookup"><span data-stu-id="46af7-153">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="46af7-154">Replacement</span><span class="sxs-lookup"><span data-stu-id="46af7-154">Replacement</span></span> | <span data-ttu-id="46af7-155">-replace</span><span class="sxs-lookup"><span data-stu-id="46af7-155">-replace</span></span>     | <span data-ttu-id="46af7-156">문자열 패턴을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-156">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="46af7-157">유형</span><span class="sxs-lookup"><span data-stu-id="46af7-157">Type</span></span>        | <span data-ttu-id="46af7-158">-is</span><span class="sxs-lookup"><span data-stu-id="46af7-158">-is</span></span>          | <span data-ttu-id="46af7-159">두 개체가 같을 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-159">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="46af7-160">type</span><span class="sxs-lookup"><span data-stu-id="46af7-160">type</span></span>                                        |
|             | <span data-ttu-id="46af7-161">-isnot</span><span class="sxs-lookup"><span data-stu-id="46af7-161">-isnot</span></span>       | <span data-ttu-id="46af7-162">개체가 같지 않으면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-162">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="46af7-163">type</span><span class="sxs-lookup"><span data-stu-id="46af7-163">type</span></span>                                        |

<span data-ttu-id="46af7-164">기본적으로 모든 비교 연산자는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-164">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="46af7-165">대/소문자를 구분 하는 비교 연산자를 만들려면 연산자 이름 앞에을 붙입니다 `c` .</span><span class="sxs-lookup"><span data-stu-id="46af7-165">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="46af7-166">예를 들어 대/소문자를 구분 하는 버전 `-eq` 은 `-ceq` 입니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-166">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="46af7-167">대/소문자를 구분 하지 않도록 명시적으로 지정 하려면 연산자 앞에을 붙입니다 `i` .</span><span class="sxs-lookup"><span data-stu-id="46af7-167">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="46af7-168">예를 들어의 명시적 대/소문자를 구분 하지 않는 버전은 `-eq` `-ieq` 입니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-168">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="46af7-169">연산자에 대 한 입력이 스칼라 값인 경우 비교 연산자는 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-169">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="46af7-170">입력이 값 컬렉션인 경우 비교 연산자는 일치 하는 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-170">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="46af7-171">컬렉션에 일치 하는 항목이 없는 경우 비교 연산자는 빈 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-171">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="46af7-172">예외는 포함 연산자, In 연산자 및 형식 연산자 이며 항상 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-172">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="46af7-173">값을 비교 해야 하는 경우 `$null` `$null` 비교의 왼쪽에를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-173">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="46af7-174">`$null` **개체 []** 와 비교할 때 비교 개체가 배열 이기 때문에 결과가 **False** 입니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-174">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="46af7-175">배열을와 비교할 때 `$null` 비교는 `$null` 배열에 저장 된 모든 값을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-175">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="46af7-176">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="46af7-176">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

### <a name="equality-operators"></a><span data-ttu-id="46af7-177">같음 연산자</span><span class="sxs-lookup"><span data-stu-id="46af7-177">Equality Operators</span></span>

<span data-ttu-id="46af7-178">같음 연산자 ( `-eq` , `-ne` )는 하나 이상의 입력 값이 지정 된 패턴과 동일한 경우 TRUE 또는 일치 항목의 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-178">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="46af7-179">전체 패턴이 전체 값과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-179">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="46af7-180">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-180">Example:</span></span>

#### <a name="-eq"></a><span data-ttu-id="46af7-181">-eq</span><span class="sxs-lookup"><span data-stu-id="46af7-181">-eq</span></span>

<span data-ttu-id="46af7-182">설명:가와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-182">Description: Equal to.</span></span> <span data-ttu-id="46af7-183">에 동일한 값이 포함 된 경우</span><span class="sxs-lookup"><span data-stu-id="46af7-183">Includes an identical value.</span></span>

<span data-ttu-id="46af7-184">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-184">Example:</span></span>

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

#### <a name="-ne"></a><span data-ttu-id="46af7-185">-ne</span><span class="sxs-lookup"><span data-stu-id="46af7-185">-ne</span></span>

<span data-ttu-id="46af7-186">설명: 같지 않음</span><span class="sxs-lookup"><span data-stu-id="46af7-186">Description: Not equal to.</span></span> <span data-ttu-id="46af7-187">에 다른 값이 포함 된 경우</span><span class="sxs-lookup"><span data-stu-id="46af7-187">Includes a different value.</span></span>

<span data-ttu-id="46af7-188">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-188">Example:</span></span>

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

#### <a name="-gt"></a><span data-ttu-id="46af7-189">-gt</span><span class="sxs-lookup"><span data-stu-id="46af7-189">-gt</span></span>

<span data-ttu-id="46af7-190">설명: 보다 큼</span><span class="sxs-lookup"><span data-stu-id="46af7-190">Description: Greater-than.</span></span>

<span data-ttu-id="46af7-191">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-191">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="46af7-192">`>`다른 많은 프로그래밍 언어의 보다 큼 연산자와 혼동 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-192">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="46af7-193">PowerShell에서 `>` 는 리디렉션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-193">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="46af7-194">자세한 내용은 [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46af7-194">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

#### <a name="-ge"></a><span data-ttu-id="46af7-195">-ge</span><span class="sxs-lookup"><span data-stu-id="46af7-195">-ge</span></span>

<span data-ttu-id="46af7-196">설명: 크거나 같음.</span><span class="sxs-lookup"><span data-stu-id="46af7-196">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="46af7-197">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-197">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

#### <a name="-lt"></a><span data-ttu-id="46af7-198">-lt</span><span class="sxs-lookup"><span data-stu-id="46af7-198">-lt</span></span>

<span data-ttu-id="46af7-199">설명: 보다 작음</span><span class="sxs-lookup"><span data-stu-id="46af7-199">Description: Less-than.</span></span>

<span data-ttu-id="46af7-200">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-200">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

#### <a name="-le"></a><span data-ttu-id="46af7-201">-le</span><span class="sxs-lookup"><span data-stu-id="46af7-201">-le</span></span>

<span data-ttu-id="46af7-202">설명: 보다 작거나 같음입니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-202">Description: Less-than or equal to.</span></span>

<span data-ttu-id="46af7-203">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-203">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

### <a name="matching-operators"></a><span data-ttu-id="46af7-204">일치 연산자</span><span class="sxs-lookup"><span data-stu-id="46af7-204">Matching Operators</span></span>

<span data-ttu-id="46af7-205">Like 연산자 ( `-like` 및 `-notlike` )는 와일드 카드 식을 사용 하 여 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-205">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="46af7-206">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-206">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="46af7-207">일치 연산자 ( `-match` 및 `-notmatch` )가 정규식을 사용 하 여 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-207">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="46af7-208">`$Matches`연산자에 대 한 입력 (왼쪽 인수)이 단일 스칼라 개체인 경우 match 연산자는 자동 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-208">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="46af7-209">입력이 스칼라 인 경우 `-match` 및 연산자는 `-notmatch` 부울 값을 반환 하 고 `$Matches` 자동 변수 값을 인수의 일치 하는 구성 요소로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-209">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="46af7-210">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-210">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

#### <a name="-like"></a><span data-ttu-id="46af7-211">-like</span><span class="sxs-lookup"><span data-stu-id="46af7-211">-like</span></span>

<span data-ttu-id="46af7-212">설명: 와일드 카드 문자 ()를 사용 하 여 찾습니다 \* .</span><span class="sxs-lookup"><span data-stu-id="46af7-212">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="46af7-213">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-213">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

#### <a name="-notlike"></a><span data-ttu-id="46af7-214">-notlike</span><span class="sxs-lookup"><span data-stu-id="46af7-214">-notlike</span></span>

<span data-ttu-id="46af7-215">설명: 와일드 카드 문자 ()를 사용 하 여 일치 하지 않습니다 \* .</span><span class="sxs-lookup"><span data-stu-id="46af7-215">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="46af7-216">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-216">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="46af7-217">-match</span><span class="sxs-lookup"><span data-stu-id="46af7-217">-match</span></span>

<span data-ttu-id="46af7-218">설명: 정규식을 사용 하 여 문자열을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-218">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="46af7-219">입력이 스칼라 인 경우 자동 변수를 채웁니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="46af7-219">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="46af7-220">입력이 컬렉션인 경우 `-match` 및 `-notmatch` 연산자는 해당 컬렉션의 일치 하는 멤버를 반환 하지만이 연산자는 변수를 채우지 않습니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="46af7-220">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="46af7-221">예를 들어 다음 명령은 연산자에 문자열 컬렉션을 전송 합니다 `-match` .</span><span class="sxs-lookup"><span data-stu-id="46af7-221">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="46af7-222">`-match`연산자는 컬렉션에서 일치 하는 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-222">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="46af7-223">자동 변수를 채우지 않습니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="46af7-223">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="46af7-224">반면, 다음 명령은 단일 문자열을 운영자에 게 전송 합니다 `-match` .</span><span class="sxs-lookup"><span data-stu-id="46af7-224">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="46af7-225">`-match`연산자는 부울 값을 반환 하 고 `$Matches` 자동 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-225">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="46af7-226">`$Matches`자동 변수는 **해시 테이블** 입니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-226">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="46af7-227">그룹화 또는 캡처가 사용 되지 않으면 하나의 키만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-227">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="46af7-228">`0`키는 일치 된 모든 텍스트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-228">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="46af7-229">정규식을 사용한 그룹화 및 캡처에 대 한 자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46af7-229">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="46af7-230">해시 테이블에는 일치 하는 `$Matches` 패턴이 처음 나타나는 경우만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-230">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="46af7-231">`0`키가 **정수** 입니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-231">The `0` key is an **Integer**.</span></span> <span data-ttu-id="46af7-232">모든 **Hashtable** 메서드를 사용 하 여 저장 된 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-232">You can use any **Hashtable** method to access the value stored.</span></span>
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

<span data-ttu-id="46af7-233">`-notmatch`연산자는 입력이 `$Matches` 스칼라 인 경우 자동 변수를 채우고 결과가 False 이면 일치 하는 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-233">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

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

#### <a name="-notmatch"></a><span data-ttu-id="46af7-234">-notmatch</span><span class="sxs-lookup"><span data-stu-id="46af7-234">-notmatch</span></span>

<span data-ttu-id="46af7-235">설명:가 문자열과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-235">Description: Does not match a string.</span></span> <span data-ttu-id="46af7-236">정규식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-236">Uses regular expressions.</span></span> <span data-ttu-id="46af7-237">입력이 스칼라 인 경우 자동 변수를 채웁니다 `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="46af7-237">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="46af7-238">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-238">Example:</span></span>

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

### <a name="containment-operators"></a><span data-ttu-id="46af7-239">포함 연산자</span><span class="sxs-lookup"><span data-stu-id="46af7-239">Containment Operators</span></span>

<span data-ttu-id="46af7-240">포함 연산자 ( `-contains` 및 `-notcontains` )는 같음 연산자와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-240">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="46af7-241">그러나 포함 연산자는 입력이 컬렉션인 경우에도 항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-241">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="46af7-242">또한 같음 연산자와 달리 포함 연산자는 첫 번째 일치 항목을 검색 하는 즉시 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-242">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="46af7-243">같음 연산자는 모든 입력을 평가한 다음 컬렉션에서 일치 하는 항목을 모두 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-243">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

#### <a name="-contains"></a><span data-ttu-id="46af7-244">-contains</span><span class="sxs-lookup"><span data-stu-id="46af7-244">-contains</span></span>

<span data-ttu-id="46af7-245">설명: 포함 연산자.</span><span class="sxs-lookup"><span data-stu-id="46af7-245">Description: Containment operator.</span></span> <span data-ttu-id="46af7-246">참조 값의 컬렉션에 단일 테스트 값이 포함 되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-246">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="46af7-247">항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-247">Always returns a Boolean value.</span></span> <span data-ttu-id="46af7-248">테스트 값이 하나 이상의 참조 값과 정확 하 게 일치 하는 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-248">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="46af7-249">테스트 값이 컬렉션인 경우 Contains 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-249">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="46af7-250">참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-250">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="46af7-251">매우 큰 컬렉션에서 `-contains` 연산자는 같음 연산자 보다 더 빠른 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-251">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="46af7-252">구문</span><span class="sxs-lookup"><span data-stu-id="46af7-252">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="46af7-253">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-253">Examples:</span></span>

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

#### <a name="-notcontains"></a><span data-ttu-id="46af7-254">-notcontains</span><span class="sxs-lookup"><span data-stu-id="46af7-254">-notcontains</span></span>

<span data-ttu-id="46af7-255">설명: 포함 연산자.</span><span class="sxs-lookup"><span data-stu-id="46af7-255">Description: Containment operator.</span></span> <span data-ttu-id="46af7-256">참조 값의 컬렉션에 단일 테스트 값이 포함 되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-256">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="46af7-257">항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-257">Always returns a Boolean value.</span></span> <span data-ttu-id="46af7-258">테스트 값이 하나 이상의 참조 값과 정확히 일치 하지 않는 경우 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-258">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="46af7-259">테스트 값이 컬렉션인 경우 NotContains 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-259">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="46af7-260">구문</span><span class="sxs-lookup"><span data-stu-id="46af7-260">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="46af7-261">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-261">Examples:</span></span>

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

#### <a name="-in"></a><span data-ttu-id="46af7-262">-in</span><span class="sxs-lookup"><span data-stu-id="46af7-262">-in</span></span>

<span data-ttu-id="46af7-263">설명: In 연산자</span><span class="sxs-lookup"><span data-stu-id="46af7-263">Description: In operator.</span></span> <span data-ttu-id="46af7-264">테스트 값이 참조 값의 컬렉션에 표시 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-264">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="46af7-265">항상 부울 값으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-265">Always return as Boolean value.</span></span> <span data-ttu-id="46af7-266">테스트 값이 하나 이상의 참조 값과 정확 하 게 일치 하는 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-266">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="46af7-267">테스트 값이 컬렉션인 경우 In 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-267">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="46af7-268">참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-268">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="46af7-269">`-in`연산자는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-269">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="46af7-270">구문</span><span class="sxs-lookup"><span data-stu-id="46af7-270">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="46af7-271">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-271">Examples:</span></span>

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

#### <a name="-notin"></a><span data-ttu-id="46af7-272">-notin</span><span class="sxs-lookup"><span data-stu-id="46af7-272">-notin</span></span>

<span data-ttu-id="46af7-273">Description: 테스트 값이 참조 값의 컬렉션에 나타나는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-273">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="46af7-274">항상 부울 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-274">Always returns a Boolean value.</span></span> <span data-ttu-id="46af7-275">테스트 값이 하나 이상의 참조 값과 정확히 일치 하지 않는 경우 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-275">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="46af7-276">테스트 값이 컬렉션인 경우 In 연산자는 참조 같음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-276">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="46af7-277">참조 값 중 하나가 테스트 값 개체의 동일한 인스턴스인 경우에만 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-277">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="46af7-278">`-notin`연산자는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-278">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="46af7-279">구문</span><span class="sxs-lookup"><span data-stu-id="46af7-279">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="46af7-280">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-280">Examples:</span></span>

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

### <a name="replacement-operator"></a><span data-ttu-id="46af7-281">대체 연산자</span><span class="sxs-lookup"><span data-stu-id="46af7-281">Replacement Operator</span></span>

<span data-ttu-id="46af7-282">`-replace`연산자는 정규식을 사용 하 여 값의 일부 또는 전체를 지정 된 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-282">The `-replace` operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="46af7-283">`-replace`파일 이름 바꾸기와 같은 많은 관리 작업에 대해 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-283">You can use the `-replace` operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="46af7-284">예를 들어 다음 명령은 모든 .txt 파일의 파일 이름 확장명을 .log로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-284">For example, the following command changes the file name extensions of all .txt files to .log:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="46af7-285">연산자의 구문은 `-replace` 다음과 같습니다 `<original>` . 여기서 자리 표시자는 바꿀 문자를 나타내고 `<substitute>` 자리 표시자는 바꿀 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-285">The syntax of the `-replace` operator is as follows, where the `<original>` placeholder represents the characters to be replaced, and the `<substitute>` placeholder represents the characters that will replace them:</span></span>

`<input> <operator> <original>, <substitute>`

<span data-ttu-id="46af7-286">기본적으로 연산자는 `-replace` 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-286">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="46af7-287">대/소문자를 구분 하려면를 사용 `-creplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-287">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="46af7-288">명시적으로 대/소문자를 구분 하지 않도록 하려면를 사용 `-ireplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-288">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="46af7-289">다음과 같은 예를 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-289">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
```

```Output
Cook
```

```powershell
"book" -ireplace "B", "C"
```

```Output
Cook
```

```powershell
"book" -creplace "B", "C"
```

```Output
book
```

<span data-ttu-id="46af7-290">또한 정규식을 사용 하 여 캡처링 그룹 및 대체를 사용 하 여 텍스트를 동적으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-290">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="46af7-291">자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46af7-291">For more information, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="scriptblock-substitutions"></a><span data-ttu-id="46af7-292">ScriptBlock 대체</span><span class="sxs-lookup"><span data-stu-id="46af7-292">ScriptBlock substitutions</span></span>

<span data-ttu-id="46af7-293">PowerShell 6부터 *대체* 텍스트에 대 한 **ScriptBlock** 인수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-293">Beginning in PowerShell 6, you can use a **ScriptBlock** argument for the *Substitution* text.</span></span> <span data-ttu-id="46af7-294">**ScriptBlock** 은 *입력* 문자열에서 찾은 각 일치 항목에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-294">The **ScriptBlock** will execute for each match found in the *input* string.</span></span>

<span data-ttu-id="46af7-295">**ScriptBlock** 내에서 `$_` 자동 변수를 사용 하 여 현재 **system.text.regularexpressions.regex>** 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-295">Within the **ScriptBlock** , use the `$_` automatic variable to refer to the current **System.Text.RegularExpressions.Match** object.</span></span> <span data-ttu-id="46af7-296">**Match** 개체를 사용 하면 대체 중인 현재 입력 텍스트 및 기타 유용한 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-296">The **Match** object gives you access to the current input text being replaced, as well as other useful information.</span></span>

<span data-ttu-id="46af7-297">이 예제에서는 세 개의 10 진수 시퀀스를 해당 하는 문자로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-297">This example replaces each sequence of three decimals with the character equivalent.</span></span> <span data-ttu-id="46af7-298">**ScriptBlock** 은 교체 해야 하는 세 개의 10 진수 집합에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-298">The **ScriptBlock** is run for each set of three decimals that needs to be replaced.</span></span>

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

### <a name="type-comparison"></a><span data-ttu-id="46af7-299">형식 비교</span><span class="sxs-lookup"><span data-stu-id="46af7-299">Type comparison</span></span>

<span data-ttu-id="46af7-300">형식 비교 연산자 ( `-is` 및 `-isnot` )는 개체가 특정 형식 인지 여부를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46af7-300">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

#### <a name="-is"></a><span data-ttu-id="46af7-301">-is</span><span class="sxs-lookup"><span data-stu-id="46af7-301">-is</span></span>

<span data-ttu-id="46af7-302">구문</span><span class="sxs-lookup"><span data-stu-id="46af7-302">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="46af7-303">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-303">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

#### <a name="-isnot"></a><span data-ttu-id="46af7-304">-isnot</span><span class="sxs-lookup"><span data-stu-id="46af7-304">-isnot</span></span>

<span data-ttu-id="46af7-305">구문</span><span class="sxs-lookup"><span data-stu-id="46af7-305">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="46af7-306">예제:</span><span class="sxs-lookup"><span data-stu-id="46af7-306">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="46af7-307">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46af7-307">SEE ALSO</span></span>

- [<span data-ttu-id="46af7-308">about_Operators</span><span class="sxs-lookup"><span data-stu-id="46af7-308">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="46af7-309">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="46af7-309">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="46af7-310">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="46af7-310">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="46af7-311">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="46af7-311">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="46af7-312">Foreach-개체</span><span class="sxs-lookup"><span data-stu-id="46af7-312">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="46af7-313">Where-Object</span><span class="sxs-lookup"><span data-stu-id="46af7-313">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
