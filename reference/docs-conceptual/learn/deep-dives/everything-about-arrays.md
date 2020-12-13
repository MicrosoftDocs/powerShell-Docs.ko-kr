---
title: 배열에 대해 알고 싶은 모든 것
description: 배열은 대부분의 프로그래밍 언어가 제공하는 기본적인 언어 기능입니다.
ms.date: 10/08/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b26aa11aadbeea1984b2754cfcad061c7fa3ff1e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "91852564"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a><span data-ttu-id="b30d0-103">배열에 대해 알고 싶은 모든 것</span><span class="sxs-lookup"><span data-stu-id="b30d0-103">Everything you wanted to know about arrays</span></span>

<span data-ttu-id="b30d0-104">[배열][]은 대부분의 프로그래밍 언어가 제공하는 기본적인 언어 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-104">[Arrays][] are a fundamental language feature of most programming languages.</span></span> <span data-ttu-id="b30d0-105">사용하지 않기가 어려운 값 또는 개체 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-105">They're a collection of values or objects that are difficult to avoid.</span></span> <span data-ttu-id="b30d0-106">배열과 배열이 제공해야 하는 모든 혜택을 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-106">Let's take a close look at arrays and everything they have to offer.</span></span>

> [!NOTE]
> <span data-ttu-id="b30d0-107">이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="b30d0-108">PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="b30d0-109">[PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b30d0-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="b30d0-110">배열이란 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="b30d0-110">What is an array?</span></span>

<span data-ttu-id="b30d0-111">먼저 배열에 관한 기본적인 기술적 설명과 대부분의 프로그래밍 언어에서 배열을 사용하는 방법을 살펴본 다음 PowerShell에서 배열을 사용하는 다른 방법을 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-111">I'm going to start with a basic technical description of what arrays are and how they are used by most programming languages before I shift into the other ways PowerShell makes use of them.</span></span>

<span data-ttu-id="b30d0-112">배열은 여러 항목의 컬렉션 역할을 하는 데이터 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-112">An array is a data structure that serves as a collection of multiple items.</span></span> <span data-ttu-id="b30d0-113">배열 전체를 반복하거나 인덱스를 사용하여 개별 항목에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-113">You can iterate over the array or access individual items using an index.</span></span> <span data-ttu-id="b30d0-114">배열은 순차적인 메모리 청크 형태로 생성되며 각 값은 다른 값 옆에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-114">The array is created as a sequential chunk of memory where each value is stored right next to the other.</span></span>

<span data-ttu-id="b30d0-115">수업을 진행하면서 각 항목을 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-115">I'll touch on each of those details as we go.</span></span>

## <a name="basic-usage"></a><span data-ttu-id="b30d0-116">기본 사용법</span><span class="sxs-lookup"><span data-stu-id="b30d0-116">Basic usage</span></span>

<span data-ttu-id="b30d0-117">배열은 PowerShell의 기본 기능이므로 간단한 구문을 이용하면 PowerShell에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-117">Because arrays are such a basic feature of PowerShell, there is a simple syntax for working with them in PowerShell.</span></span>

### <a name="create-an-array"></a><span data-ttu-id="b30d0-118">배열 만들기</span><span class="sxs-lookup"><span data-stu-id="b30d0-118">Create an array</span></span>

<span data-ttu-id="b30d0-119">`@()`을 이용하면 빈 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-119">An empty array can be created by using `@()`</span></span>

```powershell
PS> $data = @()
PS> $data.count
0
```

<span data-ttu-id="b30d0-120">배열을 만들고 `@()` 괄호 안에 넣기만 하면 초기값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-120">We can create an array and seed it with values just by placing them in the `@()` parentheses.</span></span>

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

<span data-ttu-id="b30d0-121">이 배열에는 4가지 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-121">This array has 4 items.</span></span> <span data-ttu-id="b30d0-122">`$data` 변수를 호출하면 항목 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-122">When we call the `$data` variable, we see the list of our items.</span></span> <span data-ttu-id="b30d0-123">문자열 배열이라면 문자열마다 한 줄씩 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-123">If it's an array of strings, then we get one line per string.</span></span>

<span data-ttu-id="b30d0-124">여러 줄에 배열을 선언할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-124">We can declare an array on multiple lines.</span></span> <span data-ttu-id="b30d0-125">이 경우 쉼표는 선택 사항이며 대부분의 경우 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-125">The comma is optional in this case and generally left out.</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

<span data-ttu-id="b30d0-126">이처럼 여러 줄에 배열을 선언하는 방식을 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-126">I prefer to declare my arrays on multiple lines like that.</span></span> <span data-ttu-id="b30d0-127">여러 항목이 있으면 읽기도 쉽지만 소스 제어를 사용할 때 이전 버전과 쉽게 비교할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-127">Not only does it get easier to read when you have multiple items, it also makes it easier to compare to previous versions when using source control.</span></span>

#### <a name="other-syntax"></a><span data-ttu-id="b30d0-128">기타 구문</span><span class="sxs-lookup"><span data-stu-id="b30d0-128">Other syntax</span></span>

<span data-ttu-id="b30d0-129">일반적으로 `@()`가 배열을 만드는 구문으로 간주되지만 대부분의 경우 쉼표로 구분된 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-129">It's commonly understood that `@()` is the syntax for creating an array, but comma-separated lists work most of the time.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a><span data-ttu-id="b30d0-130">Write-Output으로 배열 만들기</span><span class="sxs-lookup"><span data-stu-id="b30d0-130">Write-Output to create arrays</span></span>

<span data-ttu-id="b30d0-131">아주 유용한 방법이 있는데 `Write-Output`을 사용하면 콘솔에서 문자열을 빠르게 만들 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-131">One cool little trick worth mentioning is that you can use `Write-Output` to quickly create strings at the console.</span></span>

```powershell
$data = Write-Output Zero One Two Three
```

<span data-ttu-id="b30d0-132">매개 변수가 문자열을 허용한다면 문자열 주위에 따옴표를 붙일 필요가 없어 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-132">This is handy because you don't have to put quotes around the strings when the parameter accepts strings.</span></span> <span data-ttu-id="b30d0-133">스크립트에서는 이 작업을 수행하지 않지만 콘솔에서는 유용한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-133">I would never do this in a script but it's fair game in the console.</span></span>

### <a name="accessing-items"></a><span data-ttu-id="b30d0-134">항목 액세스</span><span class="sxs-lookup"><span data-stu-id="b30d0-134">Accessing items</span></span>

<span data-ttu-id="b30d0-135">이제 항목이 포함된 배열이 있으니 배열에 액세스하고 항목을 업데이트하고 싶을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-135">Now that you have an array with items in it, you may want to access and update those items.</span></span>

#### <a name="offset"></a><span data-ttu-id="b30d0-136">Offset</span><span class="sxs-lookup"><span data-stu-id="b30d0-136">Offset</span></span>

<span data-ttu-id="b30d0-137">개별 항목에 액세스할 때는 0부터 시작하는 오프셋 값과 함께 대괄호 `[]`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-137">To access individual items, we use the brackets `[]` with an offset value starting at 0.</span></span> <span data-ttu-id="b30d0-138">다음은 배열의 첫 번째 항목을 가져오는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-138">This is how we get the first item in our array:</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

<span data-ttu-id="b30d0-139">여기서 0을 사용하는 이유는 첫 번째 항목이 목록 시작 부분에 있어 오프셋 0개 항목을 이용해 가져와야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-139">The reason why we use zero here is because the first item is at the beginning of the list so we use an offset of 0 items to get to it.</span></span> <span data-ttu-id="b30d0-140">두 번째 항목을 가져오려면 오프셋 1을 이용해 첫 번째 항목을 건너뛰어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-140">To get to the second item, we would need to use an offset of 1 to skip the first item.</span></span>

```powershell
PS> $data[1]
One
```

<span data-ttu-id="b30d0-141">이것은 마지막 항목은 오프셋 3이라는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-141">This would mean that the last item is at offset 3.</span></span>

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a><span data-ttu-id="b30d0-142">인덱스</span><span class="sxs-lookup"><span data-stu-id="b30d0-142">Index</span></span>

<span data-ttu-id="b30d0-143">이제 이 예제에서 이러한 값을 선택한 이유를 아실 겁니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-143">Now you can see why I picked the values that I did for this example.</span></span> <span data-ttu-id="b30d0-144">실제로 오프셋이기 때문에 오프셋이라 소개했지만 일반적으로는 인덱스라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-144">I introduced this as an offset because that is what it really is, but this offset is more commonly referred to as an index.</span></span> <span data-ttu-id="b30d0-145">`0`에서 시작하는 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-145">An index that starts at `0`.</span></span> <span data-ttu-id="b30d0-146">이 문서의 나머지 부분에서는 오프셋을 인덱스라고 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-146">For the rest of this article I will call the offset an index.</span></span>

#### <a name="special-index-tricks"></a><span data-ttu-id="b30d0-147">특수 인덱스 기술</span><span class="sxs-lookup"><span data-stu-id="b30d0-147">Special index tricks</span></span>

<span data-ttu-id="b30d0-148">대부분의 언어에서는 단일 숫자만 인덱스로 지정하고 단일 항목만 다시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-148">In most languages, you can only specify a single number as the index and you get a single item back.</span></span>
<span data-ttu-id="b30d0-149">PowerShell은 훨씬 더 유연합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-149">PowerShell is much more flexible.</span></span> <span data-ttu-id="b30d0-150">여러 인덱스를 동시에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-150">You can use multiple indexes at once.</span></span> <span data-ttu-id="b30d0-151">인덱스 목록을 제공하면 여러 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-151">By providing a list of indexes, we can select several items.</span></span>

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

<span data-ttu-id="b30d0-152">제공된 인덱스의 순서에 따라 항목이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-152">The items are returned based on the order of the indexes provided.</span></span> <span data-ttu-id="b30d0-153">인덱스를 복제하면 항목을 두 번 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-153">If you duplicate an index, you get that item both times.</span></span>

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

<span data-ttu-id="b30d0-154">기본 제공 `..` 연산자를 사용하여 일련의 숫자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-154">We can specify a sequence of numbers with the built-in `..` operator.</span></span>

```powershell
PS> $data[1..3]
One
Two
Three
```

<span data-ttu-id="b30d0-155">반대 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-155">This works in reverse too.</span></span>

```powershell
PS> $data[3..1]
Three
Two
One
```

<span data-ttu-id="b30d0-156">음수 인덱스 값을 사용하면 끝에서부터 오프셋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-156">You can use negative index values to offset from the end.</span></span> <span data-ttu-id="b30d0-157">따라서 목록의 마지막 항목이 필요하다면 `-1`을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-157">So if you need the last item in the list, you can use `-1`.</span></span>

```powershell
PS> $data[-1]
Three
```

<span data-ttu-id="b30d0-158">여기서 주의해야 할 항목은 `..` 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-158">One word of caution here with the `..` operator.</span></span> <span data-ttu-id="b30d0-159">`0..-1` 및 `-1..0` 시퀀스는 `0,-1` 및 `-1,0`까지의 값을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-159">The sequence `0..-1` and `-1..0` evaluate to the values `0,-1` and `-1,0`.</span></span> <span data-ttu-id="b30d0-160">이 사실을 잊으면 `$data[0..-1]`을 이용하고 이것이 모든 항목을 열거한다고 생각하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-160">It's easy to see `$data[0..-1]` and think it would enumerate all items if you forget this detail.</span></span> <span data-ttu-id="b30d0-161">`$data[0..-1]`은 배열의 첫 번째 항목과 마지막 항목을 제공하여 `$data[0,-1]`과 같은 값을 제공합니다(다른 값은 제공하지 않습니다).</span><span class="sxs-lookup"><span data-stu-id="b30d0-161">`$data[0..-1]` gives you the same value as `$data[0,-1]` by giving you the first and last item in the array (and none of the other values).</span></span>

#### <a name="out-of-bounds"></a><span data-ttu-id="b30d0-162">범위 초과</span><span class="sxs-lookup"><span data-stu-id="b30d0-162">Out of bounds</span></span>

<span data-ttu-id="b30d0-163">대부분의 언어에서 배열 끝을 벗어나는 항목의 인덱스에 액세스하려 하면 오류나 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-163">In most languages, if you try to access an index of an item that is past the end of the array, you would get some type of error or an exception.</span></span> <span data-ttu-id="b30d0-164">PowerShell은 어떤 것도 자동으로 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-164">PowerShell silently returns nothing.</span></span>

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a><span data-ttu-id="b30d0-165">Null 배열로 인덱싱할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-165">Cannot index into a null array</span></span>

<span data-ttu-id="b30d0-166">변수가 `$null`이며 배열처럼 인덱싱하려 하면 `Cannot index into a null array` 메시지와 함께 `System.Management.Automation.RuntimeException` 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-166">If your variable is `$null` and you try to index it like an array, you get a `System.Management.Automation.RuntimeException` exception with the message `Cannot index into a null array`.</span></span>

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

<span data-ttu-id="b30d0-167">따라서 내부 요소에 액세스하기 전에 배열이 `$null`이 아닌지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-167">So make sure your arrays are not `$null` before you try to access elements inside them.</span></span>

#### <a name="count"></a><span data-ttu-id="b30d0-168">개수</span><span class="sxs-lookup"><span data-stu-id="b30d0-168">Count</span></span>

<span data-ttu-id="b30d0-169">배열 및 기타 컬렉션에는 배열에 있는 항목 수를 알려 주는 count 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-169">Arrays and other collections have a count property that tells you how many items are in the array.</span></span>

```powershell
PS> $data.count
4
```

<span data-ttu-id="b30d0-170">PowerShell 3.0에서는 대부분의 개체에 count 속성이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-170">PowerShell 3.0 added a count property to most objects.</span></span> <span data-ttu-id="b30d0-171">단일 개체를 가질 수 있으며 이 경우 카운트는 `1`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-171">you can have a single object and it should give you a count of `1`.</span></span>

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

<span data-ttu-id="b30d0-172">`0`을 반환하지 않는다면 `$null`도 count 속성을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-172">Even `$null` has a count property except it returns `0`.</span></span>

```powershell
PS> $null.count
0
```

<span data-ttu-id="b30d0-173">여기에는 몇 가지 함정이 있는데, 이 문서 후반부에서 `$null` 또는 빈 배열을 다룰 때 말씀드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-173">There are some traps here that I will revisit when I cover checking for `$null` or empty arrays later on in this article.</span></span>

#### <a name="off-by-one-errors"></a><span data-ttu-id="b30d0-174">OBO(off-by-one) 오류</span><span class="sxs-lookup"><span data-stu-id="b30d0-174">Off-by-one errors</span></span>

<span data-ttu-id="b30d0-175">대표적인 프로그래밍 오류는 배열이 인덱스 0에서 시작되기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-175">A common programming error is created because arrays start at index 0.</span></span> <span data-ttu-id="b30d0-176">OBO(off-by-one) 오류는 주로 두 가지 방법으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-176">Off-by-one errors can be introduced in two ways.</span></span>

<span data-ttu-id="b30d0-177">첫 번째 방법은 두 번째 항목을 원한다고 생각하여 `2` 인덱스를 사용했는데 실제로는 세 번째 항목을 얻는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-177">The first is by mentally thinking you want the second item and using an index of `2` and really getting the third item.</span></span> <span data-ttu-id="b30d0-178">혹은 항목 4개가 있고 마지막 항목을 원하기 때문에 count를 이용해 마지막 항목에 액세스하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-178">Or by thinking that you have four items and you want last item, so you use the count to access the last item.</span></span>

```powershell
$data[ $data.count ]
```

<span data-ttu-id="b30d0-179">PowerShell에서 같은 작업을 수행하면 인덱스 4에 있는 실제 항목인 `$null`을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-179">PowerShell is perfectly happy to let you do that and give you exactly what item exists at index 4: `$null`.</span></span> <span data-ttu-id="b30d0-180">앞에서 배운 `$data.count - 1`이나 `-1`을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-180">You should be using `$data.count - 1` or the `-1` that we learned about above.</span></span>

```powershell
PS> $data[ $data.count - 1 ]
Three
```

<span data-ttu-id="b30d0-181">여기서 `-1` 인덱스를 사용하면 마지막 요소를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-181">This is where you can use the `-1` index to get the last element.</span></span>

```powershell
PS> $data[ -1 ]
Three
```

<span data-ttu-id="b30d0-182">Lee Dailey는 `$data.GetUpperBound(0)`를 사용하면 최대 인덱스 번호를 가져올 수 있다고 알려주었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-182">Lee Dailey also pointed out to me that we can use `$data.GetUpperBound(0)` to get the max index number.</span></span>

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

<span data-ttu-id="b30d0-183">두 번째 일반적인 방법은 목록을 반복하면서 적절한 시간에 중지하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-183">The second most common way is when iterating the list and not stopping at the right time.</span></span> <span data-ttu-id="b30d0-184">`for` 루프 사용을 다룰 때 자세히 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-184">I'll revisit this when we talk about using the `for` loop.</span></span>

### <a name="updating-items"></a><span data-ttu-id="b30d0-185">항목 업데이트</span><span class="sxs-lookup"><span data-stu-id="b30d0-185">Updating items</span></span>

<span data-ttu-id="b30d0-186">동일한 인덱스를 사용하여 배열의 기존 항목을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-186">We can use the same index to update existing items in the array.</span></span> <span data-ttu-id="b30d0-187">이 방법을 이용하면 직접 액세스하여 개별 항목을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-187">This gives us direct access to update individual items.</span></span>

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

<span data-ttu-id="b30d0-188">마지막 요소 밖에 있는 항목을 업데이트하려고 하면 `Index was outside the bounds of the array.` 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-188">If we try to update an item that is past the last element, then we get an `Index was outside the bounds of the array.` error.</span></span>

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

<span data-ttu-id="b30d0-189">여기에 대해서는 배열 확대 방법을 다룰 때 자세히 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-189">I'll revisit this later when I talk about how to make an array larger.</span></span>

### <a name="iteration"></a><span data-ttu-id="b30d0-190">반복</span><span class="sxs-lookup"><span data-stu-id="b30d0-190">Iteration</span></span>

<span data-ttu-id="b30d0-191">특정 시점에서 전체 목록을 탐색하거나 반복하고 배열의 각 항목에 특정 작업을 수행해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-191">At some point, you might need to walk or iterate the entire list and perform some action for each item in the array.</span></span>

#### <a name="pipeline"></a><span data-ttu-id="b30d0-192">파이프라인</span><span class="sxs-lookup"><span data-stu-id="b30d0-192">Pipeline</span></span>

<span data-ttu-id="b30d0-193">배열과 PowerShell 파이프라인은 대단히 효율적인 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-193">Arrays and the PowerShell pipeline are meant for each other.</span></span> <span data-ttu-id="b30d0-194">이러한 값을 처리하는 가장 간단한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-194">This is one of the simplest ways to process over those values.</span></span> <span data-ttu-id="b30d0-195">배열을 파이프라인에 전달하면 배열 내 각 항목은 개별적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-195">When you pass an array to a pipeline, each item inside the array is processed individually.</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

<span data-ttu-id="b30d0-196">`$PSItem`을 처음 본다면 `$_`와 같다고 생각하시면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-196">If you have not seen `$PSItem` before, just know that it's the same thing as `$_`.</span></span> <span data-ttu-id="b30d0-197">둘 다 파이프라인의 현재 개체를 나타내기 때문에 어느 쪽을 사용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-197">You can use either one because they both represent the current object in the pipeline.</span></span>

#### <a name="foreach-loop"></a><span data-ttu-id="b30d0-198">ForEach 루프</span><span class="sxs-lookup"><span data-stu-id="b30d0-198">ForEach loop</span></span>

<span data-ttu-id="b30d0-199">`ForEach` 루프는 컬렉션과 아주 잘 어울립니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-199">The `ForEach` loop works well with collections.</span></span> <span data-ttu-id="b30d0-200">`foreach ( <variable> in <collection> )` 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-200">Using the syntax: `foreach ( <variable> in <collection> )`</span></span>

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a><span data-ttu-id="b30d0-201">ForEach 메서드</span><span class="sxs-lookup"><span data-stu-id="b30d0-201">ForEach method</span></span>

<span data-ttu-id="b30d0-202">잊어버릴 때가 잦지만 단순한 작업에 어울리는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-202">I tend to forget about this one but it works well for simple operations.</span></span> <span data-ttu-id="b30d0-203">PowerShell을 사용하면 컬렉션에서 `.ForEach()`를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-203">PowerShell allows you to call `.ForEach()` on a collection.</span></span>

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

<span data-ttu-id="b30d0-204">`.foreach()`는 스크립트 블록인 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-204">The `.foreach()` takes a parameter that is a script block.</span></span> <span data-ttu-id="b30d0-205">괄호를 삭제하고 스크립트 블록만 제공하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-205">You can drop the parentheses and just provide the script block.</span></span>

```powershell
$data.foreach{"Item [$PSItem]"}
```

<span data-ttu-id="b30d0-206">잘 알려지지 않은 구문이지만 효과는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-206">This is a lesser known syntax but it works just the same.</span></span> <span data-ttu-id="b30d0-207">이 `foreach` 메서드는 PowerShell 4.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-207">This `foreach` method was added in PowerShell 4.0.</span></span>

#### <a name="for-loop"></a><span data-ttu-id="b30d0-208">For 루프</span><span class="sxs-lookup"><span data-stu-id="b30d0-208">For loop</span></span>

<span data-ttu-id="b30d0-209">`for` 루프는 대부분의 다른 언어에서는 자주 사용하지만 PowerShell에서는 보기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-209">The `for` loop is used heavily in most other languages but you don't see it much in PowerShell.</span></span> <span data-ttu-id="b30d0-210">대부분의 경우 배열을 탐색하는 컨텍스트에서 등장합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-210">When you do see it, it's often in the context of walking an array.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="b30d0-211">가장 먼저 할 일은 `0``$index`를 초기화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-211">The first thing we do is initialize an `$index` to `0`.</span></span> <span data-ttu-id="b30d0-212">그런 다음 `$index`가 `$data.count`보다 작아야 한다는 조건을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-212">Then we add the condition that `$index` must be less than `$data.count`.</span></span> <span data-ttu-id="b30d0-213">마지막으로, 루프할 때마다 인덱스를 `1`씩 늘리도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-213">Finally, we specify that every time we loop that me must increase the index by `1`.</span></span> <span data-ttu-id="b30d0-214">이 경우 `$index++`는 `$index = $index + 1`의 축약형입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-214">In this case `$index++` is short for `$index = $index + 1`.</span></span>

<span data-ttu-id="b30d0-215">`for` 루프를 사용할 때는 항상 조건을 주의 깊게 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-215">Whenever you're using a `for` loop, pay special attention to the condition.</span></span> <span data-ttu-id="b30d0-216">여기서는 `$index -lt $data.count`를 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-216">I used `$index -lt $data.count` here.</span></span> <span data-ttu-id="b30d0-217">논리가 조금만 잘못돼도 논리에서 OBO(off-by-one) 오류가 발생하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-217">It's easy to get the condition slightly wrong to get an off-by-one error in your logic.</span></span> <span data-ttu-id="b30d0-218">`$index -le $data.count` 또는 `$index -lt ($data.count - 1)`을 사용하는 것은 아주 약한 잘못에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-218">Using `$index -le $data.count` or `$index -lt ($data.count - 1)` are ever so slightly wrong.</span></span> <span data-ttu-id="b30d0-219">너무 많거나 적은 항목을 처리한 결과가 발생하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-219">That would cause your result to process too many or too few items.</span></span> <span data-ttu-id="b30d0-220">이것은 전형적인 OBO(off-by-one) 오류에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-220">This is the classic off-by-one error.</span></span>

#### <a name="switch-loop"></a><span data-ttu-id="b30d0-221">Switch 루프</span><span class="sxs-lookup"><span data-stu-id="b30d0-221">Switch loop</span></span>

<span data-ttu-id="b30d0-222">이것은 간과하기 쉬운 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-222">This is one that is easy to overlook.</span></span> <span data-ttu-id="b30d0-223">[Switch 문][]에 배열을 제공하면 배열에 있는 각 항목을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-223">If you provide an array to a [switch statement][], it checks each item in the array.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

<span data-ttu-id="b30d0-224">Switch 문을 이용하면 수많은 유용한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-224">There are a lot of cool things that we can do with the switch statement.</span></span> <span data-ttu-id="b30d0-225">이 작업의 또 다른 전용 문서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-225">I have another article dedicated to this.</span></span>

- <span data-ttu-id="b30d0-226">[Switch 문에 대해 알고 싶은 모든 것][switch 문]</span><span class="sxs-lookup"><span data-stu-id="b30d0-226">[Everything you ever wanted to know about the switch statement][switch statement]</span></span>

#### <a name="updating-values"></a><span data-ttu-id="b30d0-227">값 업데이트</span><span class="sxs-lookup"><span data-stu-id="b30d0-227">Updating values</span></span>

<span data-ttu-id="b30d0-228">배열이 문자열 또는 정수(값 형식) 컬렉션이라면 루프할 때 배열의 값을 업데이트해야 할 때가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-228">When your array is a collection of string or integers (value types), sometimes you may want to update the values in the array as you loop over them.</span></span> <span data-ttu-id="b30d0-229">위의 루프 대부분은 값의 복사본을 보유하는 루프 내 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-229">Most of the loops above use a variable in the loop that holds a copy of the value.</span></span> <span data-ttu-id="b30d0-230">이 변수를 업데이트하면 배열의 원래 값은 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-230">If you update that variable, the original value in the array is not updated.</span></span>

<span data-ttu-id="b30d0-231">이 문에 대한 예외는 `for` 루프입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-231">The exception to that statement is the `for` loop.</span></span> <span data-ttu-id="b30d0-232">배열을 탐색하고 그 안에 있는 값을 업데이트하려면 `for` 루프를 이용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-232">If you want to walk an array and update values inside it, then the `for` loop is what you're looking for.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="b30d0-233">이 예제에서는 인덱스를 사용하여 값을 가져오고 몇 가지 사항을 변경한 다음 동일한 인덱스를 사용하여 다시 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-233">This example takes a value by index, makes a few changes, and then uses that same index to assign it back.</span></span>

## <a name="arrays-of-objects"></a><span data-ttu-id="b30d0-234">개체 배열</span><span class="sxs-lookup"><span data-stu-id="b30d0-234">Arrays of Objects</span></span>

<span data-ttu-id="b30d0-235">지금까지는 배열에 값 형식만 배치했지만 배열은 개체를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-235">So far, the only thing we've placed in an array is a value type, but arrays can also contain objects.</span></span>

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

<span data-ttu-id="b30d0-236">많은 cmdlet은 변수에 할당될 때 개체의 컬렉션을 배열로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-236">Many cmdlets return collections of objects as arrays when you assign them to a variable.</span></span>

```powershell
$processList = Get-Process
```

<span data-ttu-id="b30d0-237">앞에서 언급한 모든 기본 기능은 여전히 개체 배열에 적용되지만 몇 가지 세부 사항을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-237">All of the basic features we already talked about still apply to arrays of objects with a few details worth pointing out.</span></span>

### <a name="accessing-properties"></a><span data-ttu-id="b30d0-238">속성 액세스</span><span class="sxs-lookup"><span data-stu-id="b30d0-238">Accessing properties</span></span>

<span data-ttu-id="b30d0-239">인덱스를 사용하여 값 형식과 마찬가지로 컬렉션의 개별 항목에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-239">We can use an index to access an individual item in a collection just like with value types.</span></span>

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="b30d0-240">속성에 직접 액세스하여 속성을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-240">We can access and update properties directly.</span></span>

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a><span data-ttu-id="b30d0-241">배열 속성</span><span class="sxs-lookup"><span data-stu-id="b30d0-241">Array properties</span></span>

<span data-ttu-id="b30d0-242">일반적으로 모든 속성에 액세스하려면 다음과 같이 전체 목록을 열거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-242">Normally you would have to enumerate the whole list like this to access all the properties:</span></span>

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

<span data-ttu-id="b30d0-243">또는 `Select-Object -ExpandProperty` cmdlet을 사용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-243">Or by using the `Select-Object -ExpandProperty` cmdlet.</span></span>

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

<span data-ttu-id="b30d0-244">하지만 PowerShell은 `LastName`을 직접 요청하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-244">But PowerShell offers us the ability to request `LastName` directly.</span></span> <span data-ttu-id="b30d0-245">PowerShell은 사용자를 대신해 모든 항목을 열거하고 깔끔한 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-245">PowerShell enumerates them all for us and returns a clean list.</span></span>

```powershell
PS> $data.LastName

Marquette
Doe
```

<span data-ttu-id="b30d0-246">열거는 계속 진행되지만 복잡해 보이지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-246">The enumeration still happens but we don't see the complexity behind it.</span></span>

### <a name="where-object-filtering"></a><span data-ttu-id="b30d0-247">Where-Object 필터링</span><span class="sxs-lookup"><span data-stu-id="b30d0-247">Where-Object filtering</span></span>

<span data-ttu-id="b30d0-248">`Where-Object`를 이용해 개체 속성을 바탕으로 배열을 필터링하고 원하는 항목을 선택하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-248">This is where `Where-Object` comes in so we can filter and select what we want out of the array based on the properties of the object.</span></span>

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="b30d0-249">같은 쿼리를 작성하여 원하는 `FirstName`을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-249">We can write that same query to get the `FirstName` we are looking for.</span></span>

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a><span data-ttu-id="b30d0-250">Where()</span><span class="sxs-lookup"><span data-stu-id="b30d0-250">Where()</span></span>

<span data-ttu-id="b30d0-251">배열에는 필터의 `scriptblock`을 지정할 수 있는 `Where()` 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-251">Arrays have a `Where()` method on them that allows you to specify a `scriptblock` for the filter.</span></span>

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

<span data-ttu-id="b30d0-252">이 기능은 PowerShell 4.0에서 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-252">This feature was added in PowerShell 4.0.</span></span>

### <a name="updating-objects-in-loops"></a><span data-ttu-id="b30d0-253">루프에서 개체 업데이트</span><span class="sxs-lookup"><span data-stu-id="b30d0-253">Updating objects in loops</span></span>

<span data-ttu-id="b30d0-254">값 형식이 있는 배열을 업데이트하는 유일한 방법은 루프를 사용하는 것입니다. 값을 교체해야 하는 인덱스를 파악해야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-254">With value types, the only way to update the array is to use a for loop because we need to know the index to replace the value.</span></span> <span data-ttu-id="b30d0-255">개체는 참조 형식이므로 더 많은 선택지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-255">We have more options with objects because they are reference types.</span></span> <span data-ttu-id="b30d0-256">간단한 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-256">Here is a quick example:</span></span>

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

<span data-ttu-id="b30d0-257">이 루프는 `$data` 배열의 모든 개체를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-257">This loop is walking every object in the `$data` array.</span></span> <span data-ttu-id="b30d0-258">개체는 참조 형식이므로 `$person` 변수는 배열에 있는 것과 정확하게 같은 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-258">Because objects are reference types, the `$person` variable references the exact same object that is in the array.</span></span> <span data-ttu-id="b30d0-259">따라서 속성을 업데이트하면 원본도 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-259">So updates to its properties do update the original.</span></span>

<span data-ttu-id="b30d0-260">하지만 이 방법으로 전체 개체를 바꿀 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-260">You still can't replace the whole object this way.</span></span> <span data-ttu-id="b30d0-261">새 개체를 `$person` 변수에 할당하면 변수 참조 업데이트되어 배열 내 원래 개체를 가리키지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-261">If you try to assign a new object to the `$person` variable, you're updating the variable reference to something else that no longer points to the original object in the array.</span></span> <span data-ttu-id="b30d0-262">예상했던 결과는 아닐 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-262">This doesn't work like you would expect:</span></span>

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a><span data-ttu-id="b30d0-263">연산자</span><span class="sxs-lookup"><span data-stu-id="b30d0-263">Operators</span></span>

<span data-ttu-id="b30d0-264">PowerShell의 연산자는 배열에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-264">The operators in PowerShell also work on arrays.</span></span> <span data-ttu-id="b30d0-265">일부 연산자는 작동 방식이 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-265">Some of them work slightly differently.</span></span>

### <a name="-join"></a><span data-ttu-id="b30d0-266">-join</span><span class="sxs-lookup"><span data-stu-id="b30d0-266">-join</span></span>

<span data-ttu-id="b30d0-267">`-join` 연산자는 가장 알기 쉬운 연산자이므로 제일 먼저 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-267">The `-join` operator is the most obvious one so let's look at it first.</span></span> <span data-ttu-id="b30d0-268">`-join` 연산자를 좋아해서 자주 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-268">I like the `-join` operator and use it often.</span></span> <span data-ttu-id="b30d0-269">배열의 모든 요소를 지정한 문자 또는 문자열에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-269">It joins all elements in the array with the character or string that you specify.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

<span data-ttu-id="b30d0-270">제가 좋아하는 `-join` 연산자의 기능은 단일 항목 처리입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-270">One of the features that I like about the `-join` operator is that it handles single items.</span></span>

```powershell
PS> 1 -join '-'
1
```

<span data-ttu-id="b30d0-271">로깅 및 자세한 정보 메시지에서 이 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-271">I use this inside logging and verbose messages.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a><span data-ttu-id="b30d0-272">-join $array</span><span class="sxs-lookup"><span data-stu-id="b30d0-272">-join $array</span></span>

<span data-ttu-id="b30d0-273">다음은 Lee Dailey가 알려준 유용한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-273">Here is a clever trick that Lee Dailey pointed out to me.</span></span> <span data-ttu-id="b30d0-274">구분 기호 없이 모든 항목을 조인하려면 대신 이 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-274">If you ever want to join everything without a delimiter, instead of doing this:</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

<span data-ttu-id="b30d0-275">배열이 있는 `-join`을 접두사 없는 매개 변수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-275">You can use `-join` with the array as the parameter with no prefix.</span></span> <span data-ttu-id="b30d0-276">이 예제를 살펴보면 무슨 말인지 확인하실 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-276">Take a look at this example to see that I'm talking about.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a><span data-ttu-id="b30d0-277">-replace 및 -split</span><span class="sxs-lookup"><span data-stu-id="b30d0-277">-replace and -split</span></span>

<span data-ttu-id="b30d0-278">`-replace` 및 `-split` 같은 다른 연산자는 배열의 각 항목에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-278">The other operators like `-replace` and `-split` execute on each item in the array.</span></span> <span data-ttu-id="b30d0-279">이런 방식으로 사용해보지 않았지만 다음 예시에서 확인하실 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-279">I can't say that I have ever used them this way but here is an example.</span></span>

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a><span data-ttu-id="b30d0-280">-contains</span><span class="sxs-lookup"><span data-stu-id="b30d0-280">-contains</span></span>

<span data-ttu-id="b30d0-281">`-contains` 연산자를 사용하면 값의 배열에 지정한 값이 있는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-281">The `-contains` operator allows you to check an array of values to see if it contains a specified value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a><span data-ttu-id="b30d0-282">-in</span><span class="sxs-lookup"><span data-stu-id="b30d0-282">-in</span></span>

<span data-ttu-id="b30d0-283">단일 값이 여러 값 중 하나와 일치하는지 확인하고 싶다면 `-in` 연산자를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-283">When you have a single value that you would like to verify matches one of several values, you can use the `-in` operator.</span></span> <span data-ttu-id="b30d0-284">값은 연산자 왼쪽에 있고 배열은 오른쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-284">The value would be on the left and the array on the right-hand side of the operator.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

<span data-ttu-id="b30d0-285">이 방법은 목록이 길다면 비용이 많이 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-285">This can get expensive if the list is large.</span></span> <span data-ttu-id="b30d0-286">다수의 값을 확인할 때는 주로 정규식 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-286">I often use a regex pattern if I'm checking more than a few values.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a><span data-ttu-id="b30d0-287">-eq 및 -ne</span><span class="sxs-lookup"><span data-stu-id="b30d0-287">-eq and -ne</span></span>

<span data-ttu-id="b30d0-288">같음을 이용하면 배열이 복잡해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-288">Equality and arrays can get complicated.</span></span> <span data-ttu-id="b30d0-289">배열이 왼쪽에 있으면 모든 항목을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-289">When the array is on the left side, every item gets compared.</span></span> <span data-ttu-id="b30d0-290">`True`를 반환하는 대신 일치하는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-290">Instead of returning `True`, it returns the object that matches.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

<span data-ttu-id="b30d0-291">`-ne` 연산자를 사용하면 대상 값과 같지 않은 모든 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-291">When you use the `-ne` operator, we get all the values that are not equal to our value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

<span data-ttu-id="b30d0-292">`if()` 문에서 이 연산자를 사용하면 반환되는 값은 `True` 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-292">When you use this in an `if()` statement, a value that is returned is a `True` value.</span></span> <span data-ttu-id="b30d0-293">값이 반환되지 않는다면 `False` 값이라는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-293">If no value is returned, then it's a `False` value.</span></span> <span data-ttu-id="b30d0-294">다음 두 문은 모두 `True`로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-294">Both of these next statements evaluate to `True`.</span></span>

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

<span data-ttu-id="b30d0-295">여기에 관해서는 `$null` 테스트를 다룰 때 다시 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-295">I'll revisit this in a moment when we talk about testing for `$null`.</span></span>

### <a name="-match"></a><span data-ttu-id="b30d0-296">-match</span><span class="sxs-lookup"><span data-stu-id="b30d0-296">-match</span></span>

<span data-ttu-id="b30d0-297">`-match` 연산자는 컬렉션의 각 항목을 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-297">The `-match` operator tries to match each item in the collection.</span></span>

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

<span data-ttu-id="b30d0-298">단일 값으로 `-match`를 사용하면 일치 정보에 특수 변수인 `$Matches`가 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-298">When you use `-match` with a single value, a special variable `$Matches` gets populated with match info.</span></span> <span data-ttu-id="b30d0-299">배열을 이 방식으로 처리할 때는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-299">This isn't the case when an array is processed this way.</span></span>

<span data-ttu-id="b30d0-300">`Select-String`과 동일한 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-300">We can take the same approach with `Select-String`.</span></span>

```powershell
$servers | Select-String SQL
```

<span data-ttu-id="b30d0-301">[을 사용하는 다양한 방법][]이라는 게시물에서 `Select-String`,`-match`,`$matches` 변수를 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-301">I take a closer look at `Select-String`,`-match` and the `$matches` variable in another post called [The many ways to use regex][].</span></span>

### <a name="null-or-empty"></a><span data-ttu-id="b30d0-302">$null 또는 비어 있음</span><span class="sxs-lookup"><span data-stu-id="b30d0-302">$null or empty</span></span>

<span data-ttu-id="b30d0-303">`$null` 또는 빈 배열에 대한 테스트는 쉽지가 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-303">Testing for `$null` or empty arrays can be tricky.</span></span> <span data-ttu-id="b30d0-304">다음을 배열에서 자주 발생하는 함정입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-304">Here are the common traps with arrays.</span></span>

<span data-ttu-id="b30d0-305">얼핏 보면 이 문은 정상적으로 작동하는 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-305">At a glance, this statement looks like it should work.</span></span>

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

<span data-ttu-id="b30d0-306">하지만 앞에서 `-eq`는 배열의 각 항목을 확인한다고 말씀드렸습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-306">But I just went over how `-eq` checks each item in the array.</span></span> <span data-ttu-id="b30d0-307">따라서 배열이 단일 $null 값을 이용하는 여러 항목으로 구성될 수 있으며 이 배열은 `$true`로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-307">So we can have an array of several items with a single $null value and it would evaluate to `$true`</span></span>

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

<span data-ttu-id="b30d0-308">그래서 `$null`은 되도록 연산자 왼쪽에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-308">This is why it's a best practice to place the `$null` on the left side of the operator.</span></span> <span data-ttu-id="b30d0-309">이렇게 하면 이 시나리오는 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-309">This makes this scenario a non-issue.</span></span>

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

<span data-ttu-id="b30d0-310">`$null` 배열은 빈 배열과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-310">A `$null` array isn't the same thing as an empty array.</span></span> <span data-ttu-id="b30d0-311">배열이 있다면 배열 안에 있는 개체 수를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b30d0-311">If you know you have an array, check the count of objects in it.</span></span> <span data-ttu-id="b30d0-312">배열이 `$null`이라면 수는 `0`입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-312">If the array is `$null`, the count is `0`.</span></span>

```powershell
if ( $array.count -gt 0 )
{
    "Array isn't empty"
}
```

<span data-ttu-id="b30d0-313">여기서는 한 가지 함정을 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-313">There is one more trap to watch out for here.</span></span> <span data-ttu-id="b30d0-314">개체가 하나뿐이더라도 `count`를 사용할 수 있지만 개체가 `PSCustomObject`일 때는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-314">You can use the `count` even if you have a single object, unless that object is a `PSCustomObject`.</span></span> <span data-ttu-id="b30d0-315">이것은 버그로 PowerShell 6.1에서 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-315">This is a bug that is fixed in PowerShell 6.1.</span></span>
<span data-ttu-id="b30d0-316">반가운 소식이지만 아직 많은 사용자가 5.1을 사용하고 있으니 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-316">That's good news, but a lot of people are still on 5.1 and need to watch out for it.</span></span>

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

<span data-ttu-id="b30d0-317">아직 PowerShell 5.1을 사용한다면 개체를 배열에 래핑한 다음 개수를 확인해야 정확한 수를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-317">If you're still on PowerShell 5.1, you can wrap the object in an array before checking the count to get an accurate count.</span></span>

```powershell
if ( @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

<span data-ttu-id="b30d0-318">안전하게 하려면 `$null`를 확인한 다음 개수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-318">To fully play it safe, check for `$null`, then check the count.</span></span>

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

### <a name="all--eq"></a><span data-ttu-id="b30d0-319">All -eq</span><span class="sxs-lookup"><span data-stu-id="b30d0-319">All -eq</span></span>

<span data-ttu-id="b30d0-320">얼마 전 어떤 분이 [배열의 모든 값이 지정된 값과 일치하는지 확인하는 방법][]을 물어보셨는데</span><span class="sxs-lookup"><span data-stu-id="b30d0-320">I recently saw someone ask [how to verify that every value in an array matches a given value][].</span></span>
<span data-ttu-id="b30d0-321">Reddit 사용자 **/u/bis** 님이 잘못된 값을 확인한 다음 결과를 대칭 이동하면 된다는 탁월한 [해결책][]을 알려주었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-321">Reddit user **/u/bis** had this clever [solution][] that checks for any incorrect values and then flips the result.</span></span>

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a><span data-ttu-id="b30d0-322">배열에 추가</span><span class="sxs-lookup"><span data-stu-id="b30d0-322">Adding to arrays</span></span>

<span data-ttu-id="b30d0-323">이제 배열에 항목을 추가하는 방법이 궁금하실 겁니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-323">At this point, you're starting to wonder how to add items to an array.</span></span> <span data-ttu-id="b30d0-324">결론부터 말하자면 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-324">The quick answer is that you can't.</span></span> <span data-ttu-id="b30d0-325">배열은 메모리에서 크기가 고정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-325">An array is a fixed size in memory.</span></span> <span data-ttu-id="b30d0-326">크기를 늘리거나 단일 항목을 추가하려면 새 배열을 만들고 기존 배열의 모든 값을 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-326">If you need to grow it or add a single item to it, then you need to create a new array and copy all the values over from the old array.</span></span> <span data-ttu-id="b30d0-327">이렇게 하면 작업량이 많을 것 같지만 PowerShell에서는 새 배열을 간단하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-327">This sounds like a lot of work, however, PowerShell hides the complexity of creating the new array.</span></span> <span data-ttu-id="b30d0-328">PowerShell은 배열에 대해 더하기 연산자(`+`)를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-328">PowerShell implements the addition operator (`+`) for arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="b30d0-329">PowerShell은 빼기 연산을 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-329">PowerShell does not implement a subtraction operation.</span></span> <span data-ttu-id="b30d0-330">배열을 유연하게 대체하려면 [일반 `List`](#generic-list) 개체를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-330">If you want a flexible alternative to an array, you need to use a [generic `List`](#generic-list) object.</span></span>

### <a name="array-addition"></a><span data-ttu-id="b30d0-331">배열 추가</span><span class="sxs-lookup"><span data-stu-id="b30d0-331">Array addition</span></span>

<span data-ttu-id="b30d0-332">더하기 연산자를 배열과 함께 사용하면 새 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-332">We can use the addition operator with arrays to create a new array.</span></span> <span data-ttu-id="b30d0-333">따라서 다음과 같은 두 배열이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-333">So given these two arrays:</span></span>

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

<span data-ttu-id="b30d0-334">두 배열을 모두 추가하면 새 배열을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-334">We can add them together to get a new array.</span></span>

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a><span data-ttu-id="b30d0-335">Plus equals +=</span><span class="sxs-lookup"><span data-stu-id="b30d0-335">Plus equals +=</span></span>

<span data-ttu-id="b30d0-336">현재 위치에서 새 배열을 만들고 다음과 같이 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-336">We can create a new array in place and add an item to it like this:</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

<span data-ttu-id="b30d0-337">`+=`을 사용할 때마다 복제하여 새 배열을 만든다는 사실만 기억하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-337">Just remember that every time you use `+=` that you're duplicating and creating a new array.</span></span> <span data-ttu-id="b30d0-338">작은 데이터 세트에서는 문제가 되지 않지만 크기가 커지면 효율이 극도로 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-338">This is a not an issue for small datasets but it scales extremely poorly.</span></span>

### <a name="pipeline-assignment"></a><span data-ttu-id="b30d0-339">파이프라인 할당</span><span class="sxs-lookup"><span data-stu-id="b30d0-339">Pipeline assignment</span></span>

<span data-ttu-id="b30d0-340">파이프라인의 결과를 변수에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-340">You can assign the results of any pipeline into a variable.</span></span> <span data-ttu-id="b30d0-341">여러 항목이 있다면 배열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-341">It's an array if it contains multiple items.</span></span>

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

<span data-ttu-id="b30d0-342">일반적으로 우리는 파이프라인 사용을 전형적인 PowerShell 일회성 사용이라고 생각합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-342">Normally when we think of using the pipeline, we think of the typical PowerShell one-liners.</span></span> <span data-ttu-id="b30d0-343">`foreach()` 문과 다른 루프를 이용해 파이프라인을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-343">We can leverage the pipeline with `foreach()` statements and other loops.</span></span> <span data-ttu-id="b30d0-344">따라서 여러 항목을 루프 내 배열에 추가하는 대신 파이프라인에 놓으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-344">So instead of adding items to an array in a loop, we can drop items onto the pipeline.</span></span>

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a><span data-ttu-id="b30d0-345">배열 유형</span><span class="sxs-lookup"><span data-stu-id="b30d0-345">Array Types</span></span>

<span data-ttu-id="b30d0-346">기본적으로 PowerShell의 배열은 `[PSObject[]]` 형식으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-346">By default, an array in PowerShell is created as a `[PSObject[]]` type.</span></span> <span data-ttu-id="b30d0-347">이렇게 하면 어떤 형식의 개체나 값도 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-347">This allows it to contain any type of object or value.</span></span> <span data-ttu-id="b30d0-348">모든 요소를 `PSObject` 형식에서 상속하기 때문에 가능한 일입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-348">This works because everything is inherited from the `PSObject` type.</span></span>

### <a name="strongly-typed-arrays"></a><span data-ttu-id="b30d0-349">강력한 형식의 배열</span><span class="sxs-lookup"><span data-stu-id="b30d0-349">Strongly typed arrays</span></span>

<span data-ttu-id="b30d0-350">비슷한 구문을 사용하여 어떤 형식의 배열도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-350">You can create an array of any type using a similar syntax.</span></span> <span data-ttu-id="b30d0-351">강력한 형식의 배열을 만들 때는 지정된 형식의 값이나 개체만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-351">When you create a strongly typed array, it can only contain values or objects the specified type.</span></span>

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a><span data-ttu-id="b30d0-352">ArrayList</span><span class="sxs-lookup"><span data-stu-id="b30d0-352">ArrayList</span></span>

<span data-ttu-id="b30d0-353">배열에 항목을 추가하는 일은 제한이 가장 심한 작업이지만 몇 가지 다른 컬렉션을 이용하면 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-353">Adding items to an array is one of its biggest limitations, but there are a few other collections that we can turn to that solve this problem.</span></span>

<span data-ttu-id="b30d0-354">`ArrayList`는 빠르게 작동하는 배열을 만들 때 가장 먼저 떠올리는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-354">The `ArrayList` is commonly one of the first things that we think of when we need an array that is faster to work with.</span></span> <span data-ttu-id="b30d0-355">필요한 모든 곳에서 개체 배열처럼 작동하지만 항목 추가를 빠르게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-355">It acts like an object array every place that we need it, but it handles adding items quickly.</span></span>

<span data-ttu-id="b30d0-356">다음은 `ArrayList`를 만들고 항목을 추가하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-356">Here is how we create an `ArrayList` and add items to it.</span></span>

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

<span data-ttu-id="b30d0-357">형식을 얻기 위해 .NET을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-357">We are calling into .NET to get this type.</span></span> <span data-ttu-id="b30d0-358">이 경우에는 기본 생성자를 사용하여 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-358">In this case, we are using the default constructor to create it.</span></span> <span data-ttu-id="b30d0-359">그런 다음 `Add` 메서드를 호출하여 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-359">Then we call the `Add` method to add an item to it.</span></span>

<span data-ttu-id="b30d0-360">줄 시작 부분에 `[void]`를 사용하는 이유는 반환 코드를 표시하지 않기 위함입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-360">The reason I'm using `[void]` at the beginning of the line is to suppress the return code.</span></span> <span data-ttu-id="b30d0-361">일부 .NET 호출로 이 작업을 수행할 수 있지만 예기치 않은 출력이 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-361">Some .NET calls do this and can create unexpected output.</span></span>

<span data-ttu-id="b30d0-362">배열에 있는 데이터가 문자열뿐이라면 [StringBuilder][] 사용도 검토해봐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-362">If the only data that you have in your array is strings, then also take a look at using [StringBuilder][].</span></span> <span data-ttu-id="b30d0-363">거의 동일하지만 문자열만 처리하는 몇 가지 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-363">It's almost the same thing but has some methods that are just for dealing with strings.</span></span> <span data-ttu-id="b30d0-364">`StringBuilder`는 성능을 위해 특별히 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-364">The `StringBuilder` is specially designed for performance.</span></span>

<span data-ttu-id="b30d0-365">많은 사람들이 배열에서 `ArrayList`로 전환하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-365">It's common to see people move to `ArrayList` from arrays.</span></span> <span data-ttu-id="b30d0-366">그러나 이 기능은 C#에서 일반 지원이 제공되지 않을 때 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-366">But it comes from a time where C# didn't have generic support.</span></span> <span data-ttu-id="b30d0-367">`ArrayList`는 일반 `List[]`가 지원되면서 사용이 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-367">The `ArrayList` is deprecated in support for the generic `List[]`</span></span>

### <a name="generic-list"></a><span data-ttu-id="b30d0-368">일반 링크</span><span class="sxs-lookup"><span data-stu-id="b30d0-368">Generic List</span></span>

<span data-ttu-id="b30d0-369">일반 형식은 일반화된 클래스를 정의하는 C#에서의 특수 형식으로 사용자는 생성 시 C#에서 사용하는 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-369">A generic type is a special type in C# that defines a generalized class and the user specifies the data types it uses when created.</span></span> <span data-ttu-id="b30d0-370">따라서 숫자 또는 문자열 목록이 필요하다면 `int` 또는 `string` 유형 목록을 원한다고 정의하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-370">So if you want a list of numbers or strings, you would define that you want list of `int` or `string` types.</span></span>

<span data-ttu-id="b30d0-371">문자열 목록을 만드는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-371">Here is how you create a List for strings.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

<span data-ttu-id="b30d0-372">숫자 목록을 만드는 방법이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-372">Or a list for numbers.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

<span data-ttu-id="b30d0-373">먼저 개체를 만드는 대신 기존 배열을 이런 식으로 목록에 캐스팅해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-373">We can cast an existing array to a list like this without creating the object first:</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

<span data-ttu-id="b30d0-374">PowerShell 5 이상에서는 `using namespace` 문을 이용해 구문을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-374">We can shorten the syntax with the `using namespace` statement in PowerShell 5 and newer.</span></span> <span data-ttu-id="b30d0-375">`using` 문은 스크립트의 첫 번째 줄이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-375">The `using` statement needs to be the first line of your script.</span></span> <span data-ttu-id="b30d0-376">PowerShell은 네임스페이스를 선언하여 사용자가 데이터 유형을 참조할 때 이 문을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-376">By declaring a namespace, PowerShell lets you leave it off of the data types when you reference them.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

<span data-ttu-id="b30d0-377">따라서 `List`가 훨씬 더 유용해집니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-377">This makes the `List` much more usable.</span></span>

<span data-ttu-id="b30d0-378">비슷한 `Add` 메서드를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-378">You have a similar `Add` method available to you.</span></span> <span data-ttu-id="b30d0-379">ArrayList와는 달리 `Add` 메서드에는 반환값이 없으므로 `void`하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-379">Unlike the ArrayList, there is no return value on the `Add` method so we don't have to `void` it.</span></span>

```powershell
$myList.Add(10)
```

<span data-ttu-id="b30d0-380">다른 배열 같은 요소에도 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-380">And we can still access the elements like other arrays.</span></span>

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a><span data-ttu-id="b30d0-381">List[PSObject]</span><span class="sxs-lookup"><span data-stu-id="b30d0-381">List[PSObject]</span></span>

<span data-ttu-id="b30d0-382">어떤 형식의 목록도 가질 수 있지만 개체 형식을 모른다면 `[List[PSObject]]`를 사용하여 해당 형식을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-382">You can have a list of any type, but when you don't know the type of objects, you can use `[List[PSObject]]` to contain them.</span></span>

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a><span data-ttu-id="b30d0-383">Remove()</span><span class="sxs-lookup"><span data-stu-id="b30d0-383">Remove()</span></span>

<span data-ttu-id="b30d0-384">`ArrayList` 및 일반 `List[]`는 모두 컬렉션의 항목 제거 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-384">The `ArrayList` and the generic `List[]` both support removing items from the collection.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

<span data-ttu-id="b30d0-385">값 형식을 작업할 때는 목록의 첫 번째 항목이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-385">When working with value types, it removes the first one from the list.</span></span> <span data-ttu-id="b30d0-386">반복 호출하면 값을 계속 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-386">You can call it over and over again to keep removing that value.</span></span> <span data-ttu-id="b30d0-387">참조 형식이 있다면 제거할 개체를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-387">If you have reference types, you have to provide the object that you want removed.</span></span>

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

<span data-ttu-id="b30d0-388">Remove 메서드는 컬렉션에서 항목을 찾아 제거할 수 있다면 `true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-388">The remove method returns `true` if it was able to find and remove the item from the collection.</span></span>

### <a name="more-collections"></a><span data-ttu-id="b30d0-389">추가 컬렉션</span><span class="sxs-lookup"><span data-stu-id="b30d0-389">More collections</span></span>

<span data-ttu-id="b30d0-390">다른 많은 컬렉션을 사용할 수 있지만 바람직한 일반 배열 대체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-390">There are many other collections that can be used but these are the good generic array replacements.</span></span>
<span data-ttu-id="b30d0-391">여기에 관해 자세히 알고 싶다면 [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html)가 정리한 이 [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b30d0-391">If you're interested in learning about more of these options, take a look at this [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) that [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) put together.</span></span>

## <a name="other-nuances"></a><span data-ttu-id="b30d0-392">기타 뉘앙스</span><span class="sxs-lookup"><span data-stu-id="b30d0-392">Other nuances</span></span>

<span data-ttu-id="b30d0-393">주요 기능은 모두 살펴보았으니 지금부터는 마무리하기 전에 몇 가지 추가 요소를 말씀드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-393">Now that I have covered all the major functionality, here are a few more things that I wanted to mention before I wrap this up.</span></span>

### <a name="pre-sized-arrays"></a><span data-ttu-id="b30d0-394">미리 크기가 지정된 배열</span><span class="sxs-lookup"><span data-stu-id="b30d0-394">Pre-sized arrays</span></span>

<span data-ttu-id="b30d0-395">배열을 만든 후에는 크기를 변경할 수 없다고 말씀드렸습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-395">I mentioned that you can't change the size of an array once it's created.</span></span> <span data-ttu-id="b30d0-396">`new($size)` 생성자로 호출하면 미리 정한 크기의 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-396">We can create an array of a pre-determined size by calling it with the `new($size)` constructor.</span></span>

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a><span data-ttu-id="b30d0-397">배열 곱하기</span><span class="sxs-lookup"><span data-stu-id="b30d0-397">Multiplying arrays</span></span>

<span data-ttu-id="b30d0-398">재미 있는 기법이 있는데 바로 배열을 정수로 곱하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-398">An interesting little trick is that you can multiply an array by an integer.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a><span data-ttu-id="b30d0-399">0으로 초기화</span><span class="sxs-lookup"><span data-stu-id="b30d0-399">Initialize with 0</span></span>

<span data-ttu-id="b30d0-400">모든 항목이 0인 배열을 만들어야 할 때가 자주 찾아옵니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-400">A common scenario is that you want to create an array with all zeros.</span></span> <span data-ttu-id="b30d0-401">정수만 이용할 계획이라면 정수의 강력한 형식 배열은 기본적으로 모두 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-401">If you're only going to have integers, a strongly typed array of integers defaults to all zeros.</span></span>

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

<span data-ttu-id="b30d0-402">곱하기 기법을 이용하여 이 작업을 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-402">We can use the multiplying trick to do this too.</span></span>

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

<span data-ttu-id="b30d0-403">곱하기 기술의 장점은 어떤 값도 사용할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-403">The nice thing about the multiplying trick is that you can use any value.</span></span> <span data-ttu-id="b30d0-404">따라서 기본값이 `255`라면 이 방법도 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-404">So if you would rather have `255` as your default value, this would be a good way to do it.</span></span>

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a><span data-ttu-id="b30d0-405">중첩된 배열</span><span class="sxs-lookup"><span data-stu-id="b30d0-405">Nested arrays</span></span>

<span data-ttu-id="b30d0-406">배열 안에 있는 배열을 중첩된 배열이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-406">An array inside an array is called a nested array.</span></span> <span data-ttu-id="b30d0-407">PowerShell에서는 중첩된 배열을 잘 사용하지 않지만 다른 언어에서는 자주 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-407">I don't use these much in PowerShell but I have used them more in other languages.</span></span> <span data-ttu-id="b30d0-408">데이터가 패턴 같은 그리드에 들어맞는다면 배열 내 배열을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-408">Consider using an array of arrays when your data fits in a grid like pattern.</span></span>

<span data-ttu-id="b30d0-409">2차원 배열은 두 가지 방법으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-409">Here are two ways we can create a two-dimensional array.</span></span>

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

<span data-ttu-id="b30d0-410">이러한 예제에서는 쉼표가 대단히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-410">The comma is very important in those examples.</span></span> <span data-ttu-id="b30d0-411">앞에서 여러 줄이 있으며 쉼표가 선택 사항인 일반 배열을 소개해드렸습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-411">I gave an earlier example of a normal array on multiple lines where the comma was optional.</span></span> <span data-ttu-id="b30d0-412">이것은 다차원 배열에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-412">That isn't the case with a multi-dimensional array.</span></span>

<span data-ttu-id="b30d0-413">지금은 중첩된 배열을 사용하기 때문에 인덱스 표기법 사용 방법이 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-413">The way we use the index notation changes slightly now that we've a nested array.</span></span> <span data-ttu-id="b30d0-414">위의 `$data`를 사용하여 값 3에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-414">Using the `$data` above, this is how we would access the value 3.</span></span>

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

<span data-ttu-id="b30d0-415">각 배열 중첩 수준에 대괄호 집합을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-415">Add a set of bracket for each level of array nesting.</span></span> <span data-ttu-id="b30d0-416">첫 번째 대괄호 집합은 가장 바깥쪽 배열에 사용하며 이곳에서 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-416">The first set of brackets is for the outer most array and then you work your way in from there.</span></span>

### <a name="write-output--noenumerate"></a><span data-ttu-id="b30d0-417">Write-Output -NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="b30d0-417">Write-Output -NoEnumerate</span></span>

<span data-ttu-id="b30d0-418">PowerShell은 배열 래핑 해제나 열거를 좋아합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-418">PowerShell likes to unwrap or enumerate arrays.</span></span> <span data-ttu-id="b30d0-419">PowerShell에서 파이프라인을 사용할 때의 핵심 요소지만 두 작업을 원치 않을 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-419">This is a core aspect of the way PowerShell uses the pipeline but there are times that you don't want that to happen.</span></span>

<span data-ttu-id="b30d0-420">자세한 정보를 확인하고자 자주 개체를 `Get-Member`에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-420">I commonly pipe objects to `Get-Member` to learn more about them.</span></span> <span data-ttu-id="b30d0-421">배열을 연결하면 래핑이 해제되며 Get-Member는 실제 배열이 아니 배열의 멤버를 보게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-421">When I pipe an array to it, it gets unwrapped and Get-Member sees the members of the array and not the actual array.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

<span data-ttu-id="b30d0-422">배열의 래핑 해제를 방지하려면 `Write-Object -NoEnumerate`를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-422">To prevent that unwrap of the array, you can use `Write-Object -NoEnumerate`.</span></span>

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

<span data-ttu-id="b30d0-423">두 번째 방법은 해킹에 가깝습니다(그리고 이런 식의 해킹은 지양합니다).</span><span class="sxs-lookup"><span data-stu-id="b30d0-423">I have a second way that's more of a hack (and I try to avoid hacks like this).</span></span> <span data-ttu-id="b30d0-424">연결하기 전에 배열 앞에 쉼표를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-424">You can place a comma in front of the array before you pipe it.</span></span>

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a><span data-ttu-id="b30d0-425">배열 반환</span><span class="sxs-lookup"><span data-stu-id="b30d0-425">Return an array</span></span>

<span data-ttu-id="b30d0-426">이러한 배열 래핑 해제는 함수에서 값을 출력하거나 반환하는 경우에도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-426">This unwrapping of arrays also happens when you output or return values from a function.</span></span> <span data-ttu-id="b30d0-427">출력을 변수에 할당하더라도 배열을 얻을 수 있기 때문에 일반적으로는 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-427">You can still get an array if you assign the output to a variable so this isn't commonly an issue.</span></span>

<span data-ttu-id="b30d0-428">중요한 것은 새 배열이 생성된다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-428">The catch is that you have a new array.</span></span> <span data-ttu-id="b30d0-429">이것이 문제가 된다면 `Write-Output -NoEnumerate $array`나 `return ,$array`로 해결하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-429">If that is ever a problem, you can use `Write-Output -NoEnumerate $array` or `return ,$array` to work around it.</span></span>

## <a name="anything-else"></a><span data-ttu-id="b30d0-430">다른 내용을 알고 싶으신가요?</span><span class="sxs-lookup"><span data-stu-id="b30d0-430">Anything else?</span></span>

<span data-ttu-id="b30d0-431">습득하기엔 많은 내용이라는 걸 잘 압니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-431">I know this is all a lot to take in.</span></span> <span data-ttu-id="b30d0-432">이 문서를 읽을 때마다 배움을 얻고 앞으로도 오랫동안 참조 자료로 사용하시길 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-432">My hope is that you learn something from this article every time you read it and that it turns out to be a good reference for you for a long time to come.</span></span> <span data-ttu-id="b30d0-433">이 문서가 도움이 되는 것 같다면 도움이 필요한 다른 사람에게도 알려 주세요.</span><span class="sxs-lookup"><span data-stu-id="b30d0-433">If you found this to be helpful, please share it with others you think may get value out of it.</span></span>

<span data-ttu-id="b30d0-434">제가 작성한 비슷한 [해시 테이블][] 관련 게시물도 참조하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="b30d0-434">From here, I would recommend you check out a similar post that I wrote about [hashtables][].</span></span>

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[배열]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch 문]: everything-about-switch.md
[switch statement]: everything-about-switch.md
[해시 테이블]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
[을 사용하는 다양한 방법]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[배열의 모든 값이 지정된 값과 일치하는지 확인하는 방법]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[how to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[해결책]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
