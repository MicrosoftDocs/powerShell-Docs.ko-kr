---
description: PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 03/15/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_comparison_operators
ms.openlocfilehash: 739639f87628a59e781252b6a6c024a09262dcfd
ms.sourcegitcommit: 080c8b05a1242348c365fe1684457e873325f11e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483371"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="130e0-103">비교 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="130e0-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="130e0-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="130e0-104">Short description</span></span>

<span data-ttu-id="130e0-105">PowerShell의 비교 연산자는 입력 값에 대해 두 값 또는 컬렉션의 필터 요소를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-105">The comparison operators in PowerShell can either compare two values or filter elements of a collection against an input value.</span></span>

## <a name="long-description"></a><span data-ttu-id="130e0-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-106">Long description</span></span>

<span data-ttu-id="130e0-107">비교 연산자를 사용 하 여 값을 비교 하거나 지정 된 패턴과 일치 하는 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-107">Comparison operators let you compare values or finding values that match specified patterns.</span></span> <span data-ttu-id="130e0-108">PowerShell에는 다음과 같은 비교 연산자가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-108">PowerShell includes the following comparison operators:</span></span>

|    <span data-ttu-id="130e0-109">유형</span><span class="sxs-lookup"><span data-stu-id="130e0-109">Type</span></span>     |   <span data-ttu-id="130e0-110">연산자</span><span class="sxs-lookup"><span data-stu-id="130e0-110">Operator</span></span>   |              <span data-ttu-id="130e0-111">비교 테스트</span><span class="sxs-lookup"><span data-stu-id="130e0-111">Comparison test</span></span>              |
| ----------- | ------------ | ----------------------------------------- |
| <span data-ttu-id="130e0-112">등호</span><span class="sxs-lookup"><span data-stu-id="130e0-112">Equality</span></span>    | <span data-ttu-id="130e0-113">-eq</span><span class="sxs-lookup"><span data-stu-id="130e0-113">-eq</span></span>          | <span data-ttu-id="130e0-114">equals</span><span class="sxs-lookup"><span data-stu-id="130e0-114">equals</span></span>                                    |
|             | <span data-ttu-id="130e0-115">-ne</span><span class="sxs-lookup"><span data-stu-id="130e0-115">-ne</span></span>          | <span data-ttu-id="130e0-116">같지 않음</span><span class="sxs-lookup"><span data-stu-id="130e0-116">not equals</span></span>                                |
|             | <span data-ttu-id="130e0-117">-gt</span><span class="sxs-lookup"><span data-stu-id="130e0-117">-gt</span></span>          | <span data-ttu-id="130e0-118">보다 큼</span><span class="sxs-lookup"><span data-stu-id="130e0-118">greater than</span></span>                              |
|             | <span data-ttu-id="130e0-119">-ge</span><span class="sxs-lookup"><span data-stu-id="130e0-119">-ge</span></span>          | <span data-ttu-id="130e0-120">크거나 같음</span><span class="sxs-lookup"><span data-stu-id="130e0-120">greater than or equal</span></span>                     |
|             | <span data-ttu-id="130e0-121">-lt</span><span class="sxs-lookup"><span data-stu-id="130e0-121">-lt</span></span>          | <span data-ttu-id="130e0-122">다음보다 작음</span><span class="sxs-lookup"><span data-stu-id="130e0-122">less than</span></span>                                 |
|             | <span data-ttu-id="130e0-123">-le</span><span class="sxs-lookup"><span data-stu-id="130e0-123">-le</span></span>          | <span data-ttu-id="130e0-124">작거나 같음</span><span class="sxs-lookup"><span data-stu-id="130e0-124">less than or equal</span></span>                        |
| <span data-ttu-id="130e0-125">Matching</span><span class="sxs-lookup"><span data-stu-id="130e0-125">Matching</span></span>    | <span data-ttu-id="130e0-126">-like</span><span class="sxs-lookup"><span data-stu-id="130e0-126">-like</span></span>        | <span data-ttu-id="130e0-127">문자열이 와일드 카드 패턴과 일치</span><span class="sxs-lookup"><span data-stu-id="130e0-127">string matches wildcard pattern</span></span>           |
|             | <span data-ttu-id="130e0-128">-notlike</span><span class="sxs-lookup"><span data-stu-id="130e0-128">-notlike</span></span>     | <span data-ttu-id="130e0-129">문자열이 와일드 카드 패턴과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-129">string does not match wildcard pattern</span></span>    |
|             | <span data-ttu-id="130e0-130">-match</span><span class="sxs-lookup"><span data-stu-id="130e0-130">-match</span></span>       | <span data-ttu-id="130e0-131">문자열이 regex 패턴과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-131">string matches regex pattern</span></span>              |
|             | <span data-ttu-id="130e0-132">-notmatch</span><span class="sxs-lookup"><span data-stu-id="130e0-132">-notmatch</span></span>    | <span data-ttu-id="130e0-133">문자열이 regex 패턴과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-133">string does not match regex pattern</span></span>       |
| <span data-ttu-id="130e0-134">대체 기능</span><span class="sxs-lookup"><span data-stu-id="130e0-134">Replacement</span></span> | <span data-ttu-id="130e0-135">-replace</span><span class="sxs-lookup"><span data-stu-id="130e0-135">-replace</span></span>     | <span data-ttu-id="130e0-136">regex 패턴과 일치 하는 문자열을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-136">replaces strings matching a regex pattern</span></span> |
| <span data-ttu-id="130e0-137">Containment</span><span class="sxs-lookup"><span data-stu-id="130e0-137">Containment</span></span> | <span data-ttu-id="130e0-138">-contains</span><span class="sxs-lookup"><span data-stu-id="130e0-138">-contains</span></span>    | <span data-ttu-id="130e0-139">컬렉션에 값이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-139">collection contains a value</span></span>               |
|             | <span data-ttu-id="130e0-140">-notcontains</span><span class="sxs-lookup"><span data-stu-id="130e0-140">-notcontains</span></span> | <span data-ttu-id="130e0-141">컬렉션에 값이 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-141">collection does not contain a value</span></span>       |
|             | <span data-ttu-id="130e0-142">-in</span><span class="sxs-lookup"><span data-stu-id="130e0-142">-in</span></span>          | <span data-ttu-id="130e0-143">값이 컬렉션에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-143">value is in a collection</span></span>                  |
|             | <span data-ttu-id="130e0-144">-notin</span><span class="sxs-lookup"><span data-stu-id="130e0-144">-notin</span></span>       | <span data-ttu-id="130e0-145">값이 컬렉션에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-145">value is not in a collection</span></span>              |
| <span data-ttu-id="130e0-146">유형</span><span class="sxs-lookup"><span data-stu-id="130e0-146">Type</span></span>        | <span data-ttu-id="130e0-147">-is</span><span class="sxs-lookup"><span data-stu-id="130e0-147">-is</span></span>          | <span data-ttu-id="130e0-148">두 개체의 형식이 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-148">both objects are the same type</span></span>            |
|             | <span data-ttu-id="130e0-149">-isnot</span><span class="sxs-lookup"><span data-stu-id="130e0-149">-isnot</span></span>       | <span data-ttu-id="130e0-150">개체의 형식이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-150">the objects are not the same type</span></span>         |

## <a name="common-features"></a><span data-ttu-id="130e0-151">일반 기능</span><span class="sxs-lookup"><span data-stu-id="130e0-151">Common features</span></span>

<span data-ttu-id="130e0-152">기본적으로 모든 비교 연산자는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-152">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="130e0-153">대/소문자를 구분 하는 비교 연산자를 만들려면 뒤에를 추가 합니다 `c` `-` .</span><span class="sxs-lookup"><span data-stu-id="130e0-153">To make a comparison operator case-sensitive, add a `c` after the `-`.</span></span> <span data-ttu-id="130e0-154">예를 들어 `-ceq` 은 대/소문자를 구분 하는 버전입니다 `-eq` .</span><span class="sxs-lookup"><span data-stu-id="130e0-154">For example, `-ceq` is the case-sensitive version of `-eq`.</span></span> <span data-ttu-id="130e0-155">대/소문자를 구분 하지 않도록 명시적으로 지정 하려면 앞에를 추가 `i` `-` 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-155">To make the case-insensitivity explicit, add an `i` before `-`.</span></span> <span data-ttu-id="130e0-156">예를 들어 `-ieq` 는의 명시적 대/소문자를 구분 하지 않는 버전입니다 `-eq` .</span><span class="sxs-lookup"><span data-stu-id="130e0-156">For example, `-ieq` is the explicitly case-insensitive version of `-eq`.</span></span>

<span data-ttu-id="130e0-157">연산자의 입력이 스칼라 값 이면 연산자는 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-157">When the input of an operator is a scalar value, the operator returns a **Boolean** value.</span></span> <span data-ttu-id="130e0-158">입력이 컬렉션인 경우 연산자는 식의 오른쪽 값과 일치 하는 컬렉션의 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-158">When the input is a collection, the operator returns the elements of the collection that match the right-hand value of the expression.</span></span>
<span data-ttu-id="130e0-159">컬렉션에 일치 하는 항목이 없는 경우 비교 연산자는 빈 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-159">If there are no matches in the collection, comparison operators return an empty array.</span></span> <span data-ttu-id="130e0-160">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-160">For example:</span></span>

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

<span data-ttu-id="130e0-161">몇 가지 예외도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-161">There are a few exceptions:</span></span>

- <span data-ttu-id="130e0-162">포함 및 형식 연산자는 항상 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-162">The containment and type operators always return a **Boolean** value</span></span>
- <span data-ttu-id="130e0-163">`-replace`연산자는 대체 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-163">The `-replace` operator returns the replacement result</span></span>
- <span data-ttu-id="130e0-164">`-match` `-notmatch` 또한 `$Matches` 식의 왼쪽이 컬렉션인 경우를 제외 하 고 및 연산자는 자동 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-164">The `-match` and `-notmatch` operators also populate the `$Matches` automatic variable unless the left-hand side of the expression is a collection.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="130e0-165">같음 연산자</span><span class="sxs-lookup"><span data-stu-id="130e0-165">Equality operators</span></span>

### <a name="-eq-and--ne"></a><span data-ttu-id="130e0-166">-eq 및 -ne</span><span class="sxs-lookup"><span data-stu-id="130e0-166">-eq and -ne</span></span>

<span data-ttu-id="130e0-167">왼쪽이 스칼라 인 경우 오른쪽이 정확 하 게 일치 하면 True를 반환 하 고, `-eq` 그렇지 않으면 False를 반환  `-eq` 합니다. </span><span class="sxs-lookup"><span data-stu-id="130e0-167">When the left-hand side is scalar, `-eq` returns **True** if the right-hand side is an exact match, otherwise, `-eq` returns **False**.</span></span> <span data-ttu-id="130e0-168">`-ne` 는 반대입니다. 양쪽이 일치할 경우 **false** 를 반환 합니다. 그렇지 않으면 `-ne` True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-168">`-ne` does the opposite; it returns **False** when both sides match; otherwise, `-ne` returns True.</span></span>

<span data-ttu-id="130e0-169">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-169">Example:</span></span>

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

<span data-ttu-id="130e0-170">왼쪽이 컬렉션인 경우 `-eq` 오른쪽에 일치 하는 멤버를 반환 하는 반면는 해당 멤버를 `-ne` 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-170">When the left-hand side is a collection, `-eq` returns those members that match the right-hand side, while `-ne` filters them out.</span></span>

<span data-ttu-id="130e0-171">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-171">Example:</span></span>

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

<span data-ttu-id="130e0-172">이러한 연산자는 컬렉션의 모든 요소를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-172">These operators process all elements of the collection.</span></span> <span data-ttu-id="130e0-173">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-173">Example:</span></span>

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

<span data-ttu-id="130e0-174">같음 연산자는 스칼라 또는 컬렉션 뿐 아니라 모든 두 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-174">The equality operators accept any two objects, not just a scalar or collection.</span></span>
<span data-ttu-id="130e0-175">그러나 비교 결과는 최종 사용자에 게 의미가 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-175">But the comparison result is not guaranteed to be meaningful for the end-user.</span></span>
<span data-ttu-id="130e0-176">다음 예제에서는이 문제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-176">The following example demonstrates the issue.</span></span>

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

<span data-ttu-id="130e0-177">이 예제에서는 동일한 속성을 사용 하 여 두 개의 개체를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-177">In this example, we created two objects with identical properties.</span></span> <span data-ttu-id="130e0-178">그러나 같음 테스트 결과는 서로 다른 개체 이기 때문에 **False** 입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-178">Yet, the equality test result is **False** because they are different objects.</span></span> <span data-ttu-id="130e0-179">비교 가능한 클래스를 만들려면 클래스에서 [IEquatable \<T> ][2] 을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-179">To create comparable classes, you need to implement [System.IEquatable\<T>][2] in your class.</span></span> <span data-ttu-id="130e0-180">다음 예제에서는 [IEquatable \<T>][2] 를 구현 하 고 **파일** 및 **크기** 의 두 속성을 포함 하는 **MyFileInfoSet** 클래스의 부분 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-180">The following example demonstrates the partial implementation of a **MyFileInfoSet** class that implements [System.IEquatable\<T>][2] and has two properties, **File** and **Size**.</span></span> <span data-ttu-id="130e0-181">`Equals()`두 **MyFileInfoSet** 개체의 파일 및 크기 속성이 같으면이 메서드는 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-181">The `Equals()` method returns True if the File and Size properties of two **MyFileInfoSet** objects are the same.</span></span>

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

<span data-ttu-id="130e0-182">임의의 개체를 비교 하는 중요 한 예는 null 인지 여부를 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-182">A prominent example of comparing arbitrary objects is to find out if they are null.</span></span> <span data-ttu-id="130e0-183">하지만 변수가 인지 여부를 확인 해야 하는 경우 `$null` `$null` 같음 연산자의 왼쪽에를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-183">But if you need to determine whether a variable is `$null`, you must put `$null` on the left-hand side of the equality operator.</span></span> <span data-ttu-id="130e0-184">오른쪽에 배치 하는 것은 원하는 작업을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-184">Putting it on the right-hand side does not do what you expect.</span></span>

<span data-ttu-id="130e0-185">예를 `$a` 들어 다음과 같이 null 요소가 포함 된 배열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-185">For example, let `$a` be an array containing null elements:</span></span>

```powershell
$a = 1, 2, $null, 4, $null, 6
```

<span data-ttu-id="130e0-186">다음 테스트는 `$a` null이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-186">The following tests that `$a` is not null.</span></span>

```powershell
$null -ne $a
```

```output
True
```

<span data-ttu-id="130e0-187">그러나 다음은에서 null 요소를 모두 제외 하는 것입니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="130e0-187">The following, however, filers out all null elements from `$a`:</span></span>

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a><span data-ttu-id="130e0-188">-gt,-ge,-lt 및-le</span><span class="sxs-lookup"><span data-stu-id="130e0-188">-gt, -ge, -lt, and -le</span></span>

<span data-ttu-id="130e0-189">`-gt`, `-ge` , `-lt` 및는 `-le` 매우 유사 하 게 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-189">`-gt`, `-ge`, `-lt`, and `-le` behave very similarly.</span></span> <span data-ttu-id="130e0-190">두 측면이 모두 스칼라 인 경우 두 변의 비교 방식에 따라 **True** 또는 **False** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-190">When both sides are scalar they return **True** or **False** depending on how the two sides compare:</span></span>

| <span data-ttu-id="130e0-191">연산자</span><span class="sxs-lookup"><span data-stu-id="130e0-191">Operator</span></span> | <span data-ttu-id="130e0-192">다음의 경우 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-192">Returns True when...</span></span>                   |
| -------- | -------------------------------------- |
| <span data-ttu-id="130e0-193">-gt</span><span class="sxs-lookup"><span data-stu-id="130e0-193">-gt</span></span>      | <span data-ttu-id="130e0-194">왼쪽이 더 큽니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-194">The left-hand side is greater</span></span>          |
| <span data-ttu-id="130e0-195">-ge</span><span class="sxs-lookup"><span data-stu-id="130e0-195">-ge</span></span>      | <span data-ttu-id="130e0-196">왼쪽이 크거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-196">The left-hand side is greater or equal</span></span> |
| <span data-ttu-id="130e0-197">-lt</span><span class="sxs-lookup"><span data-stu-id="130e0-197">-lt</span></span>      | <span data-ttu-id="130e0-198">왼쪽이 더 작습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-198">The left-hand side is smaller</span></span>          |
| <span data-ttu-id="130e0-199">-le</span><span class="sxs-lookup"><span data-stu-id="130e0-199">-le</span></span>      | <span data-ttu-id="130e0-200">왼쪽이 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-200">The left-hand side is smaller or equal</span></span> |

<span data-ttu-id="130e0-201">다음 예에서는 모든 문이 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-201">In the following examples, all statements return True.</span></span>

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> <span data-ttu-id="130e0-202">대부분의 프로그래밍 언어에서 보다 큼 연산자는 `>` 입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-202">In most programming languages the greater-than operator is `>`.</span></span> <span data-ttu-id="130e0-203">PowerShell에서이 문자는 리디렉션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-203">In PowerShell, this character is used for redirection.</span></span> <span data-ttu-id="130e0-204">자세한 내용은 [about_Redirection][3]를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="130e0-204">For details, see [about_Redirection][3].</span></span>

<span data-ttu-id="130e0-205">왼쪽이 컬렉션인 경우 이러한 연산자는 컬렉션의 각 멤버를 오른쪽과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-205">When the left-hand side is a collection, these operators compare each member of the collection with the right-hand side.</span></span> <span data-ttu-id="130e0-206">논리에 따라 멤버를 유지 하거나 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-206">Depending on their logic, they either keep or discard the member.</span></span>

<span data-ttu-id="130e0-207">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-207">Example:</span></span>

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

<span data-ttu-id="130e0-208">이러한 연산자는 [system.object][1]를 구현 하는 모든 클래스에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-208">These operators work with any class that implements [System.IComparable][1].</span></span>

<span data-ttu-id="130e0-209">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-209">Examples:</span></span>

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

<span data-ttu-id="130e0-210">다음 예제에서는 ' a ' 뒤에 정렬 되는 미국 QWERTY 키보드에 기호가 없음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-210">The following example demonstrates that there is no symbol on an American QWERTY keyboard that gets sorted after 'a'.</span></span> <span data-ttu-id="130e0-211">연산자에 이러한 기호를 모두 포함 하는 집합을 공급 `-gt` 하 여 ' a '와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-211">It feeds a set containing all such symbols to the `-gt` operator to compare them against 'a'.</span></span> <span data-ttu-id="130e0-212">출력은 빈 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-212">The output is an empty array.</span></span>

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

<span data-ttu-id="130e0-213">연산자의 양쪽이 매우 비교할 수 없는 경우 이러한 연산자는 종료 되지 않는 오류를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-213">If the two sides of the operators are not reasonably comparable, these operators raise a non-terminating error.</span></span>

## <a name="matching-operators"></a><span data-ttu-id="130e0-214">일치 연산자</span><span class="sxs-lookup"><span data-stu-id="130e0-214">Matching operators</span></span>

<span data-ttu-id="130e0-215">일치 하는 연산자 ( `-like` , `-notlike` , `-match` 및 `-notmatch` )가 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-215">The matching operators (`-like`, `-notlike`, `-match`, and `-notmatch`) find elements that match or do not match a specified pattern.</span></span> <span data-ttu-id="130e0-216">및의 패턴 `-like` 은 `-notlike` , 및를 포함 하는 와일드 카드 식 이며 `*` `?` `[ ]` `-match` `-notmatch` 정규식 (Regex)을 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-216">The pattern for `-like` and `-notlike` is a wildcard expression (containing `*`, `?`, and `[ ]`), while `-match` and `-notmatch` accept a regular expression (Regex).</span></span>

<span data-ttu-id="130e0-217">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-217">The syntax is:</span></span>

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

<span data-ttu-id="130e0-218">이러한 연산자의 입력이 스칼라 값 이면 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-218">When the input of these operators is a scalar value, they return a **Boolean** value.</span></span> <span data-ttu-id="130e0-219">입력이 값 컬렉션인 경우 연산자는 일치 하는 멤버를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-219">When the input is a collection of values, the operators return any matching members.</span></span> <span data-ttu-id="130e0-220">컬렉션에 일치 하는 항목이 없는 경우이 연산자는 빈 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-220">If there are no matches in a collection, the operators return an empty array.</span></span>

### <a name="-like-and--notlike"></a><span data-ttu-id="130e0-221">유사 및-notlike</span><span class="sxs-lookup"><span data-stu-id="130e0-221">-like and -notlike</span></span>

<span data-ttu-id="130e0-222">`-like` 및 `-notlike` 는 및와 유사 하 게 동작 `-eq` `-ne` 하지만 오른쪽은 [와일드 카드](about_Wildcards.md)를 포함 하는 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-222">`-like` and `-notlike` behave similarly to `-eq` and `-ne`, but the right-hand side could be a string containing [wildcards](about_Wildcards.md).</span></span>

<span data-ttu-id="130e0-223">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-223">Example:</span></span>

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a><span data-ttu-id="130e0-224">-match 및-notmatch</span><span class="sxs-lookup"><span data-stu-id="130e0-224">-match and -notmatch</span></span>

<span data-ttu-id="130e0-225">`-match``-notmatch`정규식을 사용 하 여 왼쪽 값에서 패턴을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-225">`-match` and `-notmatch` use regular expressions to search for pattern in the left-hand side values.</span></span> <span data-ttu-id="130e0-226">정규식은 전자 메일 주소, UNC 경로 또는 형식이 지정 된 전화 번호와 같은 복잡 한 패턴을 일치 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-226">Regular expressions can match complex patterns like email addresses, UNC paths, or formatted phone numbers.</span></span> <span data-ttu-id="130e0-227">오른쪽 문자열은 [정규식](about_Regular_Expressions.md) 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-227">The right-hand side string must adhere to the [regular expressions](about_Regular_Expressions.md) rules.</span></span>

<span data-ttu-id="130e0-228">스칼라 예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-228">Scalar examples:</span></span>

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

<span data-ttu-id="130e0-229">입력이 컬렉션인 경우 연산자는 해당 컬렉션의 일치 하는 멤버를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-229">If the input is a collection, the operators return the matching members of that collection.</span></span>

<span data-ttu-id="130e0-230">컬렉션 예:</span><span class="sxs-lookup"><span data-stu-id="130e0-230">Collection examples:</span></span>

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

<span data-ttu-id="130e0-231">`-match` 및는 `-notmatch` regex 캡처 그룹을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-231">`-match` and `-notmatch` support regex capture groups.</span></span> <span data-ttu-id="130e0-232">실행 될 때마다 `$Matches` 자동 변수를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-232">Each time they run, they overwrite the `$Matches` automatic variable.</span></span> <span data-ttu-id="130e0-233">`<input>`이 컬렉션이 면 변수가입니다 `$Matches` `$null` .</span><span class="sxs-lookup"><span data-stu-id="130e0-233">When `<input>` is a collection the `$Matches` variable is `$null`.</span></span> <span data-ttu-id="130e0-234">`$Matches` 는 항상 전체 일치 항목을 저장 하는 ' 0 ' 이라는 키가 있는 **해시 테이블** 입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-234">`$Matches` is a **Hashtable** that always has a key named '0', which stores the entire match.</span></span> <span data-ttu-id="130e0-235">정규식에 캡처 그룹이 포함 된 경우에는 `$Matches` 각 그룹에 대 한 추가 키가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-235">If the regular expression contains capture groups, the `$Matches` contains additional keys for each group.</span></span>

<span data-ttu-id="130e0-236">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-236">Example:</span></span>

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

<span data-ttu-id="130e0-237">자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="130e0-237">For details, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

## <a name="replacement-operator"></a><span data-ttu-id="130e0-238">대체 연산자</span><span class="sxs-lookup"><span data-stu-id="130e0-238">Replacement operator</span></span>

### <a name="replacement-with-regular-expressions"></a><span data-ttu-id="130e0-239">정규식으로 대체</span><span class="sxs-lookup"><span data-stu-id="130e0-239">Replacement with regular expressions</span></span>

<span data-ttu-id="130e0-240">Like와 같이 `-match` 연산자는 정규식을 사용 하 여 `-replace` 지정 된 패턴을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-240">Like `-match`, the `-replace` operator uses regular expressions to find the specified pattern.</span></span> <span data-ttu-id="130e0-241">그러나와 `-match` 는 달리 일치 항목을 지정 된 다른 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-241">But unlike `-match`, it replaces the matches with another specified value.</span></span>

<span data-ttu-id="130e0-242">구문</span><span class="sxs-lookup"><span data-stu-id="130e0-242">Syntax:</span></span>

```
<input> -replace <regular-expression>, <substitute>
```

<span data-ttu-id="130e0-243">연산자는 정규식을 사용 하 여 값의 일부 또는 전체를 지정 된 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-243">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="130e0-244">파일 이름 바꾸기와 같은 많은 관리 작업에 대해 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-244">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="130e0-245">예를 들어 다음 명령은 모든 파일의 파일 이름 확장명 `.txt` 을로 변경 합니다 `.log` .</span><span class="sxs-lookup"><span data-stu-id="130e0-245">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="130e0-246">기본적으로 연산자는 `-replace` 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-246">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="130e0-247">대/소문자를 구분 하려면를 사용 `-creplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-247">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="130e0-248">명시적으로 대/소문자를 구분 하지 않도록 하려면를 사용 `-ireplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-248">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="130e0-249">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-249">Examples:</span></span>

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a><span data-ttu-id="130e0-250">정규식 대체</span><span class="sxs-lookup"><span data-stu-id="130e0-250">Regular expressions substitutions</span></span>

<span data-ttu-id="130e0-251">또한 정규식을 사용 하 여 캡처링 그룹 및 대체를 사용 하 여 텍스트를 동적으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-251">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="130e0-252">`<substitute>`그룹 식별자 앞에 달러 기호 () 문자를 사용 하 여 문자열에서 캡처 그룹을 참조할 수 있습니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="130e0-252">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="130e0-253">다음 예에서는 `-replace` 연산자가 형식으로 사용자 이름을 받아 `DomainName\Username` 형식으로 변환 합니다 `Username@DomainName` .</span><span class="sxs-lookup"><span data-stu-id="130e0-253">In the following example, the `-replace` operator accepts a username in the form of `DomainName\Username` and converts to the `Username@DomainName` format:</span></span>

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> <span data-ttu-id="130e0-254">`$`이 문자에는 PowerShell 및 정규식에서 syntatic 역할이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-254">The `$` character has syntatic roles in both PowerShell and regular expressions:</span></span>
>
> - <span data-ttu-id="130e0-255">PowerShell에서 큰따옴표 사이에는 변수를 지정 하 고 하위 식 연산자로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-255">In PowerShell, between double quotation marks, it designates variables and acts as a subexpression operator.</span></span>
> - <span data-ttu-id="130e0-256">Regex 검색 문자열에서 줄의 끝을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-256">In Regex search strings, it denotes end of the line</span></span>
> - <span data-ttu-id="130e0-257">Regex 대체 문자열에서 캡처된 그룹을 나타냅니다. 정규식을 작은따옴표 사이에 배치 하거나 앞에 억음 () 문자를 삽입 해야 `` ` `` 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-257">In Regex substitution strings, it denotes captured groups.Be sure to either put your regular expressions between single quotation marks or insert a backtick (`` ` ``) character before them.</span></span>

<span data-ttu-id="130e0-258">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-258">For example:</span></span>

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

<span data-ttu-id="130e0-259">`$$` Regex에서 리터럴을 나타냅니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="130e0-259">`$$` in Regex denotes a literal `$`.</span></span> <span data-ttu-id="130e0-260">대체 `$$` 문자열에서 결과 대체에 리터럴을 포함 하는 This `$` 입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-260">This `$$` in the substitution string to include a literal `$` in the resulting replacement.</span></span> <span data-ttu-id="130e0-261">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-261">For example:</span></span>

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

<span data-ttu-id="130e0-262">자세히 알아보려면 [정규식의][4] [about_Regular_Expressions](about_Regular_Expressions.md) 및 대체를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="130e0-262">To learn more, see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions][4].</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="130e0-263">컬렉션에서 대체</span><span class="sxs-lookup"><span data-stu-id="130e0-263">Substituting in a collection</span></span>

<span data-ttu-id="130e0-264">`<input>` `-replace` 연산자가 컬렉션인 경우 PowerShell은 컬렉션의 모든 값에 대체를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-264">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="130e0-265">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-265">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a><span data-ttu-id="130e0-266">스크립트 블록으로 바꾸기</span><span class="sxs-lookup"><span data-stu-id="130e0-266">Replacement with a script block</span></span>

<span data-ttu-id="130e0-267">PowerShell 6 이상에서 `-replace` 연산자는 대체를 수행 하는 스크립트 블록만 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-267">In PowerShell 6 and later, the `-replace` operator also accepts a script block that performs the replacement.</span></span> <span data-ttu-id="130e0-268">스크립트 블록은 모든 일치 항목에 대해 한 번씩 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-268">The script block runs once for every match.</span></span>

<span data-ttu-id="130e0-269">구문</span><span class="sxs-lookup"><span data-stu-id="130e0-269">Syntax:</span></span>

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

<span data-ttu-id="130e0-270">스크립트 블록 내에서 `$_` 자동 변수를 사용 하 여 대체 되는 입력 텍스트 및 기타 유용한 정보에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-270">Within the script block, use the `$_` automatic variable to access the input text being replaced and other useful information.</span></span> <span data-ttu-id="130e0-271">이 변수의 클래스 형식은 [system.text.regularexpressions.regex>][2]입니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-271">This variable's class type is [System.Text.RegularExpressions.Match][2].</span></span>

<span data-ttu-id="130e0-272">다음 예에서는 세 자리의 각 시퀀스를 해당 하는 문자로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-272">The following example replaces each sequence of three digits with the character equivalents.</span></span> <span data-ttu-id="130e0-273">스크립트 블록은 교체 해야 하는 3 자리 숫자의 각 집합에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-273">The script block runs for each set of three digits that needs to be replaced.</span></span>

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a><span data-ttu-id="130e0-274">포함 연산자</span><span class="sxs-lookup"><span data-stu-id="130e0-274">Containment operators</span></span>

<span data-ttu-id="130e0-275">포함 연산자 ( `-contains` , `-notcontains` , `-in` 및)는 `-notin` 입력이 컬렉션인 경우에도 항상 **부울** 값을 반환 한다는 점을 제외 하 고 같음 연산자와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-275">The containment operators (`-contains`, `-notcontains`, `-in`, and `-notin`) are similar to the equality operators, except that they always return a **Boolean** value, even when the input is a collection.</span></span> <span data-ttu-id="130e0-276">이러한 연산자는 첫 번째 일치 항목을 검색 하는 즉시 비교를 중지 하는 반면 같음 연산자는 모든 입력 멤버를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-276">These operators stop comparing as soon as they detect the first match, whereas the equality operators evaluate all input members.</span></span> <span data-ttu-id="130e0-277">매우 큰 컬렉션에서 이러한 연산자는 같음 연산자 보다 더 빠르게 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-277">In a very large collection, these operators return quicker than the equality operators.</span></span>

<span data-ttu-id="130e0-278">구문</span><span class="sxs-lookup"><span data-stu-id="130e0-278">Syntax:</span></span>

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a><span data-ttu-id="130e0-279">-contains 및-notcontains</span><span class="sxs-lookup"><span data-stu-id="130e0-279">-contains and -notcontains</span></span>

<span data-ttu-id="130e0-280">이러한 연산자는 집합에 특정 요소가 포함 되는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-280">These operators tell whether a set includes a certain element.</span></span> <span data-ttu-id="130e0-281">`-contains` 오른쪽 (테스트 개체)이 집합의 요소 중 하 나와 일치 하면 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-281">`-contains` returns True when the right-hand side (test object) matches one of the elements in the set.</span></span> <span data-ttu-id="130e0-282">`-notcontains` 대신 False를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-282">`-notcontains` returns False instead.</span></span> <span data-ttu-id="130e0-283">테스트 개체가 컬렉션인 경우 이러한 연산자는 참조 같음을 사용 합니다. 즉, 집합의 요소 중 하나가 테스트 개체의 동일한 인스턴스인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-283">When the test object is a collection, these operators use reference equality, i.e. they check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="130e0-284">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-284">Examples:</span></span>

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

<span data-ttu-id="130e0-285">더 복잡 한 예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-285">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a><span data-ttu-id="130e0-286">-in 및-notin</span><span class="sxs-lookup"><span data-stu-id="130e0-286">-in and -notin</span></span>

<span data-ttu-id="130e0-287">`-in`및 연산자는 `notin` PowerShell 3에서 및 연산자의와 반대로 된 구문으로 도입 되었습니다 `contains` `-notcontain` .</span><span class="sxs-lookup"><span data-stu-id="130e0-287">The `-in` and -`notin` operators were introduced in PowerShell 3 as the syntactic reverse of the of `contains` and `-notcontain` operators.</span></span> <span data-ttu-id="130e0-288">`-in`왼쪽  이 `<test-object>` 집합의 요소 중 하 나와 일치 하면 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-288">`-in` returns **True** when the left-hand side `<test-object>` matches one of the elements in the set.</span></span> <span data-ttu-id="130e0-289">`-notin` 대신 **False** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-289">`-notin` returns **False** instead.</span></span> <span data-ttu-id="130e0-290">테스트 개체가 집합인 경우 이러한 연산자는 참조 일치를 사용 하 여 집합의 요소 중 하나가 테스트 개체의 동일한 인스턴스인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-290">When the test object is a set, these operators use reference equality to check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="130e0-291">다음 예에서는 및에 대 한 예제와 동일한 작업 `-contain` `-notcontain` 을 수행 하지만 `-in` 및 대신 및를 사용 하 여 작성 됩니다 `-notin` .</span><span class="sxs-lookup"><span data-stu-id="130e0-291">The following examples do the same thing that the examples for `-contain` and `-notcontain` do, but they are written with `-in` and `-notin` instead.</span></span>

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

<span data-ttu-id="130e0-292">더 복잡 한 예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-292">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a><span data-ttu-id="130e0-293">형식 비교</span><span class="sxs-lookup"><span data-stu-id="130e0-293">Type comparison</span></span>

<span data-ttu-id="130e0-294">형식 비교 연산자 ( `-is` 및 `-isnot` )는 개체가 특정 형식 인지 여부를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="130e0-294">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

<span data-ttu-id="130e0-295">구문</span><span class="sxs-lookup"><span data-stu-id="130e0-295">Syntax:</span></span>

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

<span data-ttu-id="130e0-296">예제:</span><span class="sxs-lookup"><span data-stu-id="130e0-296">Example:</span></span>

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a><span data-ttu-id="130e0-297">참고 항목</span><span class="sxs-lookup"><span data-stu-id="130e0-297">SEE ALSO</span></span>

- [<span data-ttu-id="130e0-298">about_Operators</span><span class="sxs-lookup"><span data-stu-id="130e0-298">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="130e0-299">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="130e0-299">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="130e0-300">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="130e0-300">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="130e0-301">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="130e0-301">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="130e0-302">Foreach-개체</span><span class="sxs-lookup"><span data-stu-id="130e0-302">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="130e0-303">Where-Object</span><span class="sxs-lookup"><span data-stu-id="130e0-303">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
