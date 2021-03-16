---
description: PowerShell의 값을 비교 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 03/15/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_comparison_operators
ms.openlocfilehash: ec8ce1a241676911795e76f0934d40fd8ad18bd8
ms.sourcegitcommit: 080c8b05a1242348c365fe1684457e873325f11e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483405"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="a6d7a-103">비교 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="a6d7a-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="a6d7a-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="a6d7a-104">Short description</span></span>

<span data-ttu-id="a6d7a-105">PowerShell의 비교 연산자는 입력 값에 대해 두 값 또는 컬렉션의 필터 요소를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-105">The comparison operators in PowerShell can either compare two values or filter elements of a collection against an input value.</span></span>

## <a name="long-description"></a><span data-ttu-id="a6d7a-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-106">Long description</span></span>

<span data-ttu-id="a6d7a-107">비교 연산자를 사용 하 여 값을 비교 하거나 지정 된 패턴과 일치 하는 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-107">Comparison operators let you compare values or finding values that match specified patterns.</span></span> <span data-ttu-id="a6d7a-108">PowerShell에는 다음과 같은 비교 연산자가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-108">PowerShell includes the following comparison operators:</span></span>

|    <span data-ttu-id="a6d7a-109">유형</span><span class="sxs-lookup"><span data-stu-id="a6d7a-109">Type</span></span>     |   <span data-ttu-id="a6d7a-110">연산자</span><span class="sxs-lookup"><span data-stu-id="a6d7a-110">Operator</span></span>   |              <span data-ttu-id="a6d7a-111">비교 테스트</span><span class="sxs-lookup"><span data-stu-id="a6d7a-111">Comparison test</span></span>              |
| ----------- | ------------ | ----------------------------------------- |
| <span data-ttu-id="a6d7a-112">등호</span><span class="sxs-lookup"><span data-stu-id="a6d7a-112">Equality</span></span>    | <span data-ttu-id="a6d7a-113">-eq</span><span class="sxs-lookup"><span data-stu-id="a6d7a-113">-eq</span></span>          | <span data-ttu-id="a6d7a-114">equals</span><span class="sxs-lookup"><span data-stu-id="a6d7a-114">equals</span></span>                                    |
|             | <span data-ttu-id="a6d7a-115">-ne</span><span class="sxs-lookup"><span data-stu-id="a6d7a-115">-ne</span></span>          | <span data-ttu-id="a6d7a-116">같지 않음</span><span class="sxs-lookup"><span data-stu-id="a6d7a-116">not equals</span></span>                                |
|             | <span data-ttu-id="a6d7a-117">-gt</span><span class="sxs-lookup"><span data-stu-id="a6d7a-117">-gt</span></span>          | <span data-ttu-id="a6d7a-118">보다 큼</span><span class="sxs-lookup"><span data-stu-id="a6d7a-118">greater than</span></span>                              |
|             | <span data-ttu-id="a6d7a-119">-ge</span><span class="sxs-lookup"><span data-stu-id="a6d7a-119">-ge</span></span>          | <span data-ttu-id="a6d7a-120">크거나 같음</span><span class="sxs-lookup"><span data-stu-id="a6d7a-120">greater than or equal</span></span>                     |
|             | <span data-ttu-id="a6d7a-121">-lt</span><span class="sxs-lookup"><span data-stu-id="a6d7a-121">-lt</span></span>          | <span data-ttu-id="a6d7a-122">다음보다 작음</span><span class="sxs-lookup"><span data-stu-id="a6d7a-122">less than</span></span>                                 |
|             | <span data-ttu-id="a6d7a-123">-le</span><span class="sxs-lookup"><span data-stu-id="a6d7a-123">-le</span></span>          | <span data-ttu-id="a6d7a-124">작거나 같음</span><span class="sxs-lookup"><span data-stu-id="a6d7a-124">less than or equal</span></span>                        |
| <span data-ttu-id="a6d7a-125">Matching</span><span class="sxs-lookup"><span data-stu-id="a6d7a-125">Matching</span></span>    | <span data-ttu-id="a6d7a-126">-like</span><span class="sxs-lookup"><span data-stu-id="a6d7a-126">-like</span></span>        | <span data-ttu-id="a6d7a-127">문자열이 와일드 카드 패턴과 일치</span><span class="sxs-lookup"><span data-stu-id="a6d7a-127">string matches wildcard pattern</span></span>           |
|             | <span data-ttu-id="a6d7a-128">-notlike</span><span class="sxs-lookup"><span data-stu-id="a6d7a-128">-notlike</span></span>     | <span data-ttu-id="a6d7a-129">문자열이 와일드 카드 패턴과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-129">string does not match wildcard pattern</span></span>    |
|             | <span data-ttu-id="a6d7a-130">-match</span><span class="sxs-lookup"><span data-stu-id="a6d7a-130">-match</span></span>       | <span data-ttu-id="a6d7a-131">문자열이 regex 패턴과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-131">string matches regex pattern</span></span>              |
|             | <span data-ttu-id="a6d7a-132">-notmatch</span><span class="sxs-lookup"><span data-stu-id="a6d7a-132">-notmatch</span></span>    | <span data-ttu-id="a6d7a-133">문자열이 regex 패턴과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-133">string does not match regex pattern</span></span>       |
| <span data-ttu-id="a6d7a-134">대체 기능</span><span class="sxs-lookup"><span data-stu-id="a6d7a-134">Replacement</span></span> | <span data-ttu-id="a6d7a-135">-replace</span><span class="sxs-lookup"><span data-stu-id="a6d7a-135">-replace</span></span>     | <span data-ttu-id="a6d7a-136">regex 패턴과 일치 하는 문자열을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-136">replaces strings matching a regex pattern</span></span> |
| <span data-ttu-id="a6d7a-137">Containment</span><span class="sxs-lookup"><span data-stu-id="a6d7a-137">Containment</span></span> | <span data-ttu-id="a6d7a-138">-contains</span><span class="sxs-lookup"><span data-stu-id="a6d7a-138">-contains</span></span>    | <span data-ttu-id="a6d7a-139">컬렉션에 값이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-139">collection contains a value</span></span>               |
|             | <span data-ttu-id="a6d7a-140">-notcontains</span><span class="sxs-lookup"><span data-stu-id="a6d7a-140">-notcontains</span></span> | <span data-ttu-id="a6d7a-141">컬렉션에 값이 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-141">collection does not contain a value</span></span>       |
|             | <span data-ttu-id="a6d7a-142">-in</span><span class="sxs-lookup"><span data-stu-id="a6d7a-142">-in</span></span>          | <span data-ttu-id="a6d7a-143">값이 컬렉션에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-143">value is in a collection</span></span>                  |
|             | <span data-ttu-id="a6d7a-144">-notin</span><span class="sxs-lookup"><span data-stu-id="a6d7a-144">-notin</span></span>       | <span data-ttu-id="a6d7a-145">값이 컬렉션에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-145">value is not in a collection</span></span>              |
| <span data-ttu-id="a6d7a-146">유형</span><span class="sxs-lookup"><span data-stu-id="a6d7a-146">Type</span></span>        | <span data-ttu-id="a6d7a-147">-is</span><span class="sxs-lookup"><span data-stu-id="a6d7a-147">-is</span></span>          | <span data-ttu-id="a6d7a-148">두 개체의 형식이 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-148">both objects are the same type</span></span>            |
|             | <span data-ttu-id="a6d7a-149">-isnot</span><span class="sxs-lookup"><span data-stu-id="a6d7a-149">-isnot</span></span>       | <span data-ttu-id="a6d7a-150">개체의 형식이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-150">the objects are not the same type</span></span>         |

## <a name="common-features"></a><span data-ttu-id="a6d7a-151">일반 기능</span><span class="sxs-lookup"><span data-stu-id="a6d7a-151">Common features</span></span>

<span data-ttu-id="a6d7a-152">기본적으로 모든 비교 연산자는 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-152">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="a6d7a-153">대/소문자를 구분 하는 비교 연산자를 만들려면 뒤에를 추가 합니다 `c` `-` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-153">To make a comparison operator case-sensitive, add a `c` after the `-`.</span></span> <span data-ttu-id="a6d7a-154">예를 들어 `-ceq` 은 대/소문자를 구분 하는 버전입니다 `-eq` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-154">For example, `-ceq` is the case-sensitive version of `-eq`.</span></span> <span data-ttu-id="a6d7a-155">대/소문자를 구분 하지 않도록 명시적으로 지정 하려면 앞에를 추가 `i` `-` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-155">To make the case-insensitivity explicit, add an `i` before `-`.</span></span> <span data-ttu-id="a6d7a-156">예를 들어 `-ieq` 는의 명시적 대/소문자를 구분 하지 않는 버전입니다 `-eq` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-156">For example, `-ieq` is the explicitly case-insensitive version of `-eq`.</span></span>

<span data-ttu-id="a6d7a-157">연산자의 입력이 스칼라 값 이면 연산자는 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-157">When the input of an operator is a scalar value, the operator returns a **Boolean** value.</span></span> <span data-ttu-id="a6d7a-158">입력이 컬렉션인 경우 연산자는 식의 오른쪽 값과 일치 하는 컬렉션의 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-158">When the input is a collection, the operator returns the elements of the collection that match the right-hand value of the expression.</span></span>
<span data-ttu-id="a6d7a-159">컬렉션에 일치 하는 항목이 없는 경우 비교 연산자는 빈 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-159">If there are no matches in the collection, comparison operators return an empty array.</span></span> <span data-ttu-id="a6d7a-160">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-160">For example:</span></span>

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

<span data-ttu-id="a6d7a-161">몇 가지 예외도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-161">There are a few exceptions:</span></span>

- <span data-ttu-id="a6d7a-162">포함 및 형식 연산자는 항상 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-162">The containment and type operators always return a **Boolean** value</span></span>
- <span data-ttu-id="a6d7a-163">`-replace`연산자는 대체 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-163">The `-replace` operator returns the replacement result</span></span>
- <span data-ttu-id="a6d7a-164">`-match` `-notmatch` 또한 `$Matches` 식의 왼쪽이 컬렉션인 경우를 제외 하 고 및 연산자는 자동 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-164">The `-match` and `-notmatch` operators also populate the `$Matches` automatic variable unless the left-hand side of the expression is a collection.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="a6d7a-165">같음 연산자</span><span class="sxs-lookup"><span data-stu-id="a6d7a-165">Equality operators</span></span>

### <a name="-eq-and--ne"></a><span data-ttu-id="a6d7a-166">-eq 및 -ne</span><span class="sxs-lookup"><span data-stu-id="a6d7a-166">-eq and -ne</span></span>

<span data-ttu-id="a6d7a-167">왼쪽이 스칼라 인 경우 오른쪽이 정확 하 게 일치 하면 True를 반환 하 고, `-eq` 그렇지 않으면 False를 반환  `-eq` 합니다. </span><span class="sxs-lookup"><span data-stu-id="a6d7a-167">When the left-hand side is scalar, `-eq` returns **True** if the right-hand side is an exact match, otherwise, `-eq` returns **False**.</span></span> <span data-ttu-id="a6d7a-168">`-ne` 는 반대입니다. 양쪽이 일치할 경우 **false** 를 반환 합니다. 그렇지 않으면 `-ne` True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-168">`-ne` does the opposite; it returns **False** when both sides match; otherwise, `-ne` returns True.</span></span>

<span data-ttu-id="a6d7a-169">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-169">Example:</span></span>

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

<span data-ttu-id="a6d7a-170">왼쪽이 컬렉션인 경우 `-eq` 오른쪽에 일치 하는 멤버를 반환 하는 반면는 해당 멤버를 `-ne` 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-170">When the left-hand side is a collection, `-eq` returns those members that match the right-hand side, while `-ne` filters them out.</span></span>

<span data-ttu-id="a6d7a-171">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-171">Example:</span></span>

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

<span data-ttu-id="a6d7a-172">이러한 연산자는 컬렉션의 모든 요소를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-172">These operators process all elements of the collection.</span></span> <span data-ttu-id="a6d7a-173">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-173">Example:</span></span>

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

<span data-ttu-id="a6d7a-174">같음 연산자는 스칼라 또는 컬렉션 뿐 아니라 모든 두 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-174">The equality operators accept any two objects, not just a scalar or collection.</span></span>
<span data-ttu-id="a6d7a-175">그러나 비교 결과는 최종 사용자에 게 의미가 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-175">But the comparison result is not guaranteed to be meaningful for the end-user.</span></span>
<span data-ttu-id="a6d7a-176">다음 예제에서는이 문제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-176">The following example demonstrates the issue.</span></span>

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

<span data-ttu-id="a6d7a-177">이 예제에서는 동일한 속성을 사용 하 여 두 개의 개체를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-177">In this example, we created two objects with identical properties.</span></span> <span data-ttu-id="a6d7a-178">그러나 같음 테스트 결과는 서로 다른 개체 이기 때문에 **False** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-178">Yet, the equality test result is **False** because they are different objects.</span></span> <span data-ttu-id="a6d7a-179">비교 가능한 클래스를 만들려면 클래스에서 [IEquatable \<T> ][2] 을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-179">To create comparable classes, you need to implement [System.IEquatable\<T>][2] in your class.</span></span> <span data-ttu-id="a6d7a-180">다음 예제에서는 [IEquatable \<T>][2] 를 구현 하 고 **파일** 및 **크기** 의 두 속성을 포함 하는 **MyFileInfoSet** 클래스의 부분 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-180">The following example demonstrates the partial implementation of a **MyFileInfoSet** class that implements [System.IEquatable\<T>][2] and has two properties, **File** and **Size**.</span></span> <span data-ttu-id="a6d7a-181">`Equals()`두 **MyFileInfoSet** 개체의 파일 및 크기 속성이 같으면이 메서드는 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-181">The `Equals()` method returns True if the File and Size properties of two **MyFileInfoSet** objects are the same.</span></span>

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

<span data-ttu-id="a6d7a-182">임의의 개체를 비교 하는 중요 한 예는 null 인지 여부를 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-182">A prominent example of comparing arbitrary objects is to find out if they are null.</span></span> <span data-ttu-id="a6d7a-183">하지만 변수가 인지 여부를 확인 해야 하는 경우 `$null` `$null` 같음 연산자의 왼쪽에를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-183">But if you need to determine whether a variable is `$null`, you must put `$null` on the left-hand side of the equality operator.</span></span> <span data-ttu-id="a6d7a-184">오른쪽에 배치 하는 것은 원하는 작업을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-184">Putting it on the right-hand side does not do what you expect.</span></span>

<span data-ttu-id="a6d7a-185">예를 `$a` 들어 다음과 같이 null 요소가 포함 된 배열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-185">For example, let `$a` be an array containing null elements:</span></span>

```powershell
$a = 1, 2, $null, 4, $null, 6
```

<span data-ttu-id="a6d7a-186">다음 테스트는 `$a` null이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-186">The following tests that `$a` is not null.</span></span>

```powershell
$null -ne $a
```

```output
True
```

<span data-ttu-id="a6d7a-187">그러나 다음은에서 null 요소를 모두 제외 하는 것입니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-187">The following, however, filers out all null elements from `$a`:</span></span>

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a><span data-ttu-id="a6d7a-188">-gt,-ge,-lt 및-le</span><span class="sxs-lookup"><span data-stu-id="a6d7a-188">-gt, -ge, -lt, and -le</span></span>

<span data-ttu-id="a6d7a-189">`-gt`, `-ge` , `-lt` 및는 `-le` 매우 유사 하 게 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-189">`-gt`, `-ge`, `-lt`, and `-le` behave very similarly.</span></span> <span data-ttu-id="a6d7a-190">두 측면이 모두 스칼라 인 경우 두 변의 비교 방식에 따라 **True** 또는 **False** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-190">When both sides are scalar they return **True** or **False** depending on how the two sides compare:</span></span>

| <span data-ttu-id="a6d7a-191">연산자</span><span class="sxs-lookup"><span data-stu-id="a6d7a-191">Operator</span></span> | <span data-ttu-id="a6d7a-192">다음의 경우 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-192">Returns True when...</span></span>                   |
| -------- | -------------------------------------- |
| <span data-ttu-id="a6d7a-193">-gt</span><span class="sxs-lookup"><span data-stu-id="a6d7a-193">-gt</span></span>      | <span data-ttu-id="a6d7a-194">왼쪽이 더 큽니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-194">The left-hand side is greater</span></span>          |
| <span data-ttu-id="a6d7a-195">-ge</span><span class="sxs-lookup"><span data-stu-id="a6d7a-195">-ge</span></span>      | <span data-ttu-id="a6d7a-196">왼쪽이 크거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-196">The left-hand side is greater or equal</span></span> |
| <span data-ttu-id="a6d7a-197">-lt</span><span class="sxs-lookup"><span data-stu-id="a6d7a-197">-lt</span></span>      | <span data-ttu-id="a6d7a-198">왼쪽이 더 작습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-198">The left-hand side is smaller</span></span>          |
| <span data-ttu-id="a6d7a-199">-le</span><span class="sxs-lookup"><span data-stu-id="a6d7a-199">-le</span></span>      | <span data-ttu-id="a6d7a-200">왼쪽이 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-200">The left-hand side is smaller or equal</span></span> |

<span data-ttu-id="a6d7a-201">다음 예에서는 모든 문이 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-201">In the following examples, all statements return True.</span></span>

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> <span data-ttu-id="a6d7a-202">대부분의 프로그래밍 언어에서 보다 큼 연산자는 `>` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-202">In most programming languages the greater-than operator is `>`.</span></span> <span data-ttu-id="a6d7a-203">PowerShell에서이 문자는 리디렉션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-203">In PowerShell, this character is used for redirection.</span></span> <span data-ttu-id="a6d7a-204">자세한 내용은 [about_Redirection][3]를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-204">For details, see [about_Redirection][3].</span></span>

<span data-ttu-id="a6d7a-205">왼쪽이 컬렉션인 경우 이러한 연산자는 컬렉션의 각 멤버를 오른쪽과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-205">When the left-hand side is a collection, these operators compare each member of the collection with the right-hand side.</span></span> <span data-ttu-id="a6d7a-206">논리에 따라 멤버를 유지 하거나 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-206">Depending on their logic, they either keep or discard the member.</span></span>

<span data-ttu-id="a6d7a-207">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-207">Example:</span></span>

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

<span data-ttu-id="a6d7a-208">이러한 연산자는 [system.object][1]를 구현 하는 모든 클래스에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-208">These operators work with any class that implements [System.IComparable][1].</span></span>

<span data-ttu-id="a6d7a-209">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-209">Examples:</span></span>

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

<span data-ttu-id="a6d7a-210">다음 예제에서는 ' a ' 뒤에 정렬 되는 미국 QWERTY 키보드에 기호가 없음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-210">The following example demonstrates that there is no symbol on an American QWERTY keyboard that gets sorted after 'a'.</span></span> <span data-ttu-id="a6d7a-211">연산자에 이러한 기호를 모두 포함 하는 집합을 공급 `-gt` 하 여 ' a '와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-211">It feeds a set containing all such symbols to the `-gt` operator to compare them against 'a'.</span></span> <span data-ttu-id="a6d7a-212">출력은 빈 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-212">The output is an empty array.</span></span>

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

<span data-ttu-id="a6d7a-213">연산자의 양쪽이 매우 비교할 수 없는 경우 이러한 연산자는 종료 되지 않는 오류를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-213">If the two sides of the operators are not reasonably comparable, these operators raise a non-terminating error.</span></span>

## <a name="matching-operators"></a><span data-ttu-id="a6d7a-214">일치 연산자</span><span class="sxs-lookup"><span data-stu-id="a6d7a-214">Matching operators</span></span>

<span data-ttu-id="a6d7a-215">일치 하는 연산자 ( `-like` , `-notlike` , `-match` 및 `-notmatch` )가 지정 된 패턴과 일치 하거나 일치 하지 않는 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-215">The matching operators (`-like`, `-notlike`, `-match`, and `-notmatch`) find elements that match or do not match a specified pattern.</span></span> <span data-ttu-id="a6d7a-216">및의 패턴 `-like` 은 `-notlike` , 및를 포함 하는 와일드 카드 식 이며 `*` `?` `[ ]` `-match` `-notmatch` 정규식 (Regex)을 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-216">The pattern for `-like` and `-notlike` is a wildcard expression (containing `*`, `?`, and `[ ]`), while `-match` and `-notmatch` accept a regular expression (Regex).</span></span>

<span data-ttu-id="a6d7a-217">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-217">The syntax is:</span></span>

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

<span data-ttu-id="a6d7a-218">이러한 연산자의 입력이 스칼라 값 이면 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-218">When the input of these operators is a scalar value, they return a **Boolean** value.</span></span> <span data-ttu-id="a6d7a-219">입력이 값 컬렉션인 경우 연산자는 일치 하는 멤버를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-219">When the input is a collection of values, the operators return any matching members.</span></span> <span data-ttu-id="a6d7a-220">컬렉션에 일치 하는 항목이 없는 경우이 연산자는 빈 배열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-220">If there are no matches in a collection, the operators return an empty array.</span></span>

### <a name="-like-and--notlike"></a><span data-ttu-id="a6d7a-221">유사 및-notlike</span><span class="sxs-lookup"><span data-stu-id="a6d7a-221">-like and -notlike</span></span>

<span data-ttu-id="a6d7a-222">`-like` 및 `-notlike` 는 및와 유사 하 게 동작 `-eq` `-ne` 하지만 오른쪽은 [와일드 카드](about_Wildcards.md)를 포함 하는 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-222">`-like` and `-notlike` behave similarly to `-eq` and `-ne`, but the right-hand side could be a string containing [wildcards](about_Wildcards.md).</span></span>

<span data-ttu-id="a6d7a-223">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-223">Example:</span></span>

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

### <a name="-match-and--notmatch"></a><span data-ttu-id="a6d7a-224">-match 및-notmatch</span><span class="sxs-lookup"><span data-stu-id="a6d7a-224">-match and -notmatch</span></span>

<span data-ttu-id="a6d7a-225">`-match``-notmatch`정규식을 사용 하 여 왼쪽 값에서 패턴을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-225">`-match` and `-notmatch` use regular expressions to search for pattern in the left-hand side values.</span></span> <span data-ttu-id="a6d7a-226">정규식은 전자 메일 주소, UNC 경로 또는 형식이 지정 된 전화 번호와 같은 복잡 한 패턴을 일치 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-226">Regular expressions can match complex patterns like email addresses, UNC paths, or formatted phone numbers.</span></span> <span data-ttu-id="a6d7a-227">오른쪽 문자열은 [정규식](about_Regular_Expressions.md) 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-227">The right-hand side string must adhere to the [regular expressions](about_Regular_Expressions.md) rules.</span></span>

<span data-ttu-id="a6d7a-228">스칼라 예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-228">Scalar examples:</span></span>

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

<span data-ttu-id="a6d7a-229">입력이 컬렉션인 경우 연산자는 해당 컬렉션의 일치 하는 멤버를 반환 하 고 `$Matches` 자동 변수는 `$null` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-229">If the input is a collection, the operators return the matching members of that collection and the `$Matches` automatic variable is `$null`.</span></span>

<span data-ttu-id="a6d7a-230">컬렉션 예:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-230">Collection examples:</span></span>

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

<span data-ttu-id="a6d7a-231">`-match` 및는 `-notmatch` regex 캡처 그룹을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-231">`-match` and `-notmatch` support regex capture groups.</span></span> <span data-ttu-id="a6d7a-232">실행 될 때마다 `$Matches` 자동 변수를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-232">Each time they run, they overwrite the `$Matches` automatic variable.</span></span> <span data-ttu-id="a6d7a-233">`<input>`이 컬렉션이 면 변수가입니다 `$Matches` `$null` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-233">When `<input>` is a collection the `$Matches` variable is `$null`.</span></span> <span data-ttu-id="a6d7a-234">`$Matches` 는 항상 전체 일치 항목을 저장 하는 ' 0 ' 이라는 키가 있는 **해시 테이블** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-234">`$Matches` is a **Hashtable** that always has a key named '0', which stores the entire match.</span></span> <span data-ttu-id="a6d7a-235">정규식에 캡처 그룹이 포함 된 경우에는 `$Matches` 각 그룹에 대 한 추가 키가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-235">If the regular expression contains capture groups, the `$Matches` contains additional keys for each group.</span></span>

<span data-ttu-id="a6d7a-236">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-236">Example:</span></span>

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

<span data-ttu-id="a6d7a-237">자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-237">For details, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

## <a name="replacement-operator"></a><span data-ttu-id="a6d7a-238">대체 연산자</span><span class="sxs-lookup"><span data-stu-id="a6d7a-238">Replacement operator</span></span>

### <a name="replacement-with-regular-expressions"></a><span data-ttu-id="a6d7a-239">정규식으로 대체</span><span class="sxs-lookup"><span data-stu-id="a6d7a-239">Replacement with regular expressions</span></span>

<span data-ttu-id="a6d7a-240">Like와 같이 `-match` 연산자는 정규식을 사용 하 여 `-replace` 지정 된 패턴을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-240">Like `-match`, the `-replace` operator uses regular expressions to find the specified pattern.</span></span> <span data-ttu-id="a6d7a-241">그러나와 `-match` 는 달리 일치 항목을 지정 된 다른 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-241">But unlike `-match`, it replaces the matches with another specified value.</span></span>

<span data-ttu-id="a6d7a-242">구문</span><span class="sxs-lookup"><span data-stu-id="a6d7a-242">Syntax:</span></span>

```
<input> -replace <regular-expression>, <substitute>
```

<span data-ttu-id="a6d7a-243">연산자는 정규식을 사용 하 여 값의 일부 또는 전체를 지정 된 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-243">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="a6d7a-244">파일 이름 바꾸기와 같은 많은 관리 작업에 대해 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-244">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="a6d7a-245">예를 들어 다음 명령은 모든 파일의 파일 이름 확장명 `.txt` 을로 변경 합니다 `.log` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-245">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="a6d7a-246">기본적으로 연산자는 `-replace` 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-246">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="a6d7a-247">대/소문자를 구분 하려면를 사용 `-creplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-247">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="a6d7a-248">명시적으로 대/소문자를 구분 하지 않도록 하려면를 사용 `-ireplace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-248">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="a6d7a-249">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-249">Examples:</span></span>

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a><span data-ttu-id="a6d7a-250">정규식 대체</span><span class="sxs-lookup"><span data-stu-id="a6d7a-250">Regular expressions substitutions</span></span>

<span data-ttu-id="a6d7a-251">또한 정규식을 사용 하 여 캡처링 그룹 및 대체를 사용 하 여 텍스트를 동적으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-251">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="a6d7a-252">`<substitute>`그룹 식별자 앞에 달러 기호 () 문자를 사용 하 여 문자열에서 캡처 그룹을 참조할 수 있습니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-252">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="a6d7a-253">다음 예에서는 `-replace` 연산자가 형식으로 사용자 이름을 받아 `DomainName\Username` 형식으로 변환 합니다 `Username@DomainName` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-253">In the following example, the `-replace` operator accepts a username in the form of `DomainName\Username` and converts to the `Username@DomainName` format:</span></span>

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> <span data-ttu-id="a6d7a-254">`$`이 문자에는 PowerShell 및 정규식에서 syntatic 역할이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-254">The `$` character has syntatic roles in both PowerShell and regular expressions:</span></span>
>
> - <span data-ttu-id="a6d7a-255">PowerShell에서 큰따옴표 사이에는 변수를 지정 하 고 하위 식 연산자로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-255">In PowerShell, between double quotation marks, it designates variables and acts as a subexpression operator.</span></span>
> - <span data-ttu-id="a6d7a-256">Regex 검색 문자열에서 줄의 끝을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-256">In Regex search strings, it denotes end of the line</span></span>
> - <span data-ttu-id="a6d7a-257">Regex 대체 문자열에서 캡처된 그룹을 나타냅니다. 정규식을 작은따옴표 사이에 배치 하거나 앞에 억음 () 문자를 삽입 해야 `` ` `` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-257">In Regex substitution strings, it denotes captured groups.Be sure to either put your regular expressions between single quotation marks or insert a backtick (`` ` ``) character before them.</span></span>

<span data-ttu-id="a6d7a-258">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-258">For example:</span></span>

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

<span data-ttu-id="a6d7a-259">`$$` Regex에서 리터럴을 나타냅니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-259">`$$` in Regex denotes a literal `$`.</span></span> <span data-ttu-id="a6d7a-260">대체 `$$` 문자열에서 결과 대체에 리터럴을 포함 하는 This `$` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-260">This `$$` in the substitution string to include a literal `$` in the resulting replacement.</span></span> <span data-ttu-id="a6d7a-261">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-261">For example:</span></span>

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

<span data-ttu-id="a6d7a-262">자세히 알아보려면 [정규식의][4] [about_Regular_Expressions](about_Regular_Expressions.md) 및 대체를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-262">To learn more, see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions][4].</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="a6d7a-263">컬렉션에서 대체</span><span class="sxs-lookup"><span data-stu-id="a6d7a-263">Substituting in a collection</span></span>

<span data-ttu-id="a6d7a-264">`<input>` `-replace` 연산자가 컬렉션인 경우 PowerShell은 컬렉션의 모든 값에 대체를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-264">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="a6d7a-265">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-265">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

## <a name="containment-operators"></a><span data-ttu-id="a6d7a-266">포함 연산자</span><span class="sxs-lookup"><span data-stu-id="a6d7a-266">Containment operators</span></span>

<span data-ttu-id="a6d7a-267">포함 연산자 ( `-contains` , `-notcontains` , `-in` 및)는 `-notin` 입력이 컬렉션인 경우에도 항상 **부울** 값을 반환 한다는 점을 제외 하 고 같음 연산자와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-267">The containment operators (`-contains`, `-notcontains`, `-in`, and `-notin`) are similar to the equality operators, except that they always return a **Boolean** value, even when the input is a collection.</span></span> <span data-ttu-id="a6d7a-268">이러한 연산자는 첫 번째 일치 항목을 검색 하는 즉시 비교를 중지 하는 반면 같음 연산자는 모든 입력 멤버를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-268">These operators stop comparing as soon as they detect the first match, whereas the equality operators evaluate all input members.</span></span> <span data-ttu-id="a6d7a-269">매우 큰 컬렉션에서 이러한 연산자는 같음 연산자 보다 더 빠르게 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-269">In a very large collection, these operators return quicker than the equality operators.</span></span>

<span data-ttu-id="a6d7a-270">구문</span><span class="sxs-lookup"><span data-stu-id="a6d7a-270">Syntax:</span></span>

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a><span data-ttu-id="a6d7a-271">-contains 및-notcontains</span><span class="sxs-lookup"><span data-stu-id="a6d7a-271">-contains and -notcontains</span></span>

<span data-ttu-id="a6d7a-272">이러한 연산자는 집합에 특정 요소가 포함 되는지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-272">These operators tell whether a set includes a certain element.</span></span> <span data-ttu-id="a6d7a-273">`-contains` 오른쪽 (테스트 개체)이 집합의 요소 중 하 나와 일치 하면 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-273">`-contains` returns True when the right-hand side (test object) matches one of the elements in the set.</span></span> <span data-ttu-id="a6d7a-274">`-notcontains` 대신 False를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-274">`-notcontains` returns False instead.</span></span> <span data-ttu-id="a6d7a-275">테스트 개체가 컬렉션인 경우 이러한 연산자는 참조 같음을 사용 합니다. 즉, 집합의 요소 중 하나가 테스트 개체의 동일한 인스턴스인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-275">When the test object is a collection, these operators use reference equality, i.e. they check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="a6d7a-276">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-276">Examples:</span></span>

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

<span data-ttu-id="a6d7a-277">더 복잡 한 예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-277">More complex examples:</span></span>

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

### <a name="-in-and--notin"></a><span data-ttu-id="a6d7a-278">-in 및-notin</span><span class="sxs-lookup"><span data-stu-id="a6d7a-278">-in and -notin</span></span>

<span data-ttu-id="a6d7a-279">`-in`및 연산자는 `notin` PowerShell 3에서 및 연산자의와 반대로 된 구문으로 도입 되었습니다 `contains` `-notcontain` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-279">The `-in` and -`notin` operators were introduced in PowerShell 3 as the syntactic reverse of the of `contains` and `-notcontain` operators.</span></span> <span data-ttu-id="a6d7a-280">`-in`왼쪽  이 `<test-object>` 집합의 요소 중 하 나와 일치 하면 True를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-280">`-in` returns **True** when the left-hand side `<test-object>` matches one of the elements in the set.</span></span> <span data-ttu-id="a6d7a-281">`-notin` 대신 **False** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-281">`-notin` returns **False** instead.</span></span> <span data-ttu-id="a6d7a-282">테스트 개체가 집합인 경우 이러한 연산자는 참조 일치를 사용 하 여 집합의 요소 중 하나가 테스트 개체의 동일한 인스턴스인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-282">When the test object is a set, these operators use reference equality to check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="a6d7a-283">다음 예에서는 및에 대 한 예제와 동일한 작업 `-contain` `-notcontain` 을 수행 하지만 `-in` 및 대신 및를 사용 하 여 작성 됩니다 `-notin` .</span><span class="sxs-lookup"><span data-stu-id="a6d7a-283">The following examples do the same thing that the examples for `-contain` and `-notcontain` do, but they are written with `-in` and `-notin` instead.</span></span>

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

<span data-ttu-id="a6d7a-284">더 복잡 한 예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-284">More complex examples:</span></span>

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

## <a name="type-comparison"></a><span data-ttu-id="a6d7a-285">형식 비교</span><span class="sxs-lookup"><span data-stu-id="a6d7a-285">Type comparison</span></span>

<span data-ttu-id="a6d7a-286">형식 비교 연산자 ( `-is` 및 `-isnot` )는 개체가 특정 형식 인지 여부를 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-286">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

<span data-ttu-id="a6d7a-287">구문</span><span class="sxs-lookup"><span data-stu-id="a6d7a-287">Syntax:</span></span>

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

<span data-ttu-id="a6d7a-288">예제:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-288">Example:</span></span>

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a><span data-ttu-id="a6d7a-289">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6d7a-289">SEE ALSO</span></span>

- [<span data-ttu-id="a6d7a-290">about_Operators</span><span class="sxs-lookup"><span data-stu-id="a6d7a-290">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="a6d7a-291">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="a6d7a-291">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="a6d7a-292">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="a6d7a-292">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="a6d7a-293">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="a6d7a-293">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="a6d7a-294">Foreach-개체</span><span class="sxs-lookup"><span data-stu-id="a6d7a-294">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="a6d7a-295">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a6d7a-295">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
