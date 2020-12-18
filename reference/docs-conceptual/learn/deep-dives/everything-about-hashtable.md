---
title: 해시 테이블에 대해 알고 싶은 모든 것
description: 해시 테이블은 PowerShell에서 대단히 중요하기 때문에 확실하게 이해해야 합니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1539cf6444cab718c1108384c640193d66c85daf
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "93354425"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a><span data-ttu-id="51ce1-103">해시 테이블에 대해 알고 싶은 모든 것</span><span class="sxs-lookup"><span data-stu-id="51ce1-103">Everything you wanted to know about hashtables</span></span>

<span data-ttu-id="51ce1-104">잠시 뒤로 돌아가 [해시 테이블][]을 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-104">I want to take a step back and talk about [hashtables][].</span></span> <span data-ttu-id="51ce1-105">현재 해시 테이블을 항상 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-105">I use them all the time now.</span></span> <span data-ttu-id="51ce1-106">어젯밤 사용자 그룹 모임이 끝나고 관련 내용을 가르치다가 저 역시 학생과 똑같은 혼란을 겪고 있음을 알게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-106">I was teaching someone about them after our user group meeting last night and I realized I had the same confusion about them as he had.</span></span> <span data-ttu-id="51ce1-107">해시 테이블은 PowerShell에서 대단히 중요하기 때문에 확실하게 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-107">Hashtables are really important in PowerShell so it's good to have a solid understanding of them.</span></span>

> [!NOTE]
> <span data-ttu-id="51ce1-108">이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="51ce1-109">PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="51ce1-110">[PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="51ce1-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="hashtable-as-a-collection-of-things"></a><span data-ttu-id="51ce1-111">해시 테이블은 다양한 요소의 컬렉션입니다</span><span class="sxs-lookup"><span data-stu-id="51ce1-111">Hashtable as a collection of things</span></span>

<span data-ttu-id="51ce1-112">먼저 기본적으로 **해시 테이블** 은 컬렉션으로 정의된다는 사실을 아셔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-112">I want you to first see a **Hashtable** as a collection in the traditional definition of a hashtable.</span></span> <span data-ttu-id="51ce1-113">이 정의를 알아야 나중에 고급 작업에서 사용할 때 해시 테이블의 기본적인 작동 방식을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-113">This definition gives you a fundamental understanding of how they work when they get used for more advanced stuff later.</span></span> <span data-ttu-id="51ce1-114">이를 이해하지 않으면 혼란을 겪게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-114">Skipping this understanding is often a source of confusion.</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="51ce1-115">배열이란 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="51ce1-115">What is an array?</span></span>

<span data-ttu-id="51ce1-116">**해시 테이블** 이 무엇인지 살펴보기 전에 먼저 [배열][]을 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-116">Before I jump into what a **Hashtable** is, I need to mention [arrays][] first.</span></span> <span data-ttu-id="51ce1-117">여기서 말하는 배열은 값 또는 개체의 목록 또는 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-117">For the purpose of this discussion, an array is a list or collection of values or objects.</span></span>

```powershell
$array = @(1,2,3,5,7,11)
```

<span data-ttu-id="51ce1-118">항목을 배열 안에 배치하면 `foreach`를 사용하여 목록 전체에서 반복하거나 인덱스를 사용하여 배열 내 개별 요소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-118">Once you have your items into an array, you can either use `foreach` to iterate over the list or use an index to access individual elements in the array.</span></span>

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

<span data-ttu-id="51ce1-119">같은 방식으로 인덱스를 사용하여 값을 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-119">You can also update values using an index in the same way.</span></span>

```powershell
$array[2] = 13
```

<span data-ttu-id="51ce1-120">배열에 대한 아주 기초적인 내용만 설명했지만 이 내용을 알아야 해시 테이블을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-120">I just scratched the surface on arrays but that should put them into the right context as I move onto hashtables.</span></span>

## <a name="what-is-a-hashtable"></a><span data-ttu-id="51ce1-121">해시 테이블이란 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="51ce1-121">What is a hashtable?</span></span>

<span data-ttu-id="51ce1-122">해시 테이블의 기본적인 기술적 정의를 일반적인 관점에서 살펴본 다음 PowerShell에서 사용하는 다른 방법을 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-122">I'm going to start with a basic technical description of what hashtables are, in the general sense, before I shift into the other ways PowerShell uses them.</span></span>

<span data-ttu-id="51ce1-123">해시 테이블은 배열과 대단히 유사한 데이터 구조지만 키를 사용하는 각 값(개체)을 저장한다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-123">A hashtable is a data structure, much like an array, except you store each value (object) using a key.</span></span> <span data-ttu-id="51ce1-124">해시 테이블은 기본 키/값 저장소입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-124">It's a basic key/value store.</span></span> <span data-ttu-id="51ce1-125">먼저 빈 해시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-125">First, we create an empty hashtable.</span></span>

```powershell
$ageList = @{}
```

<span data-ttu-id="51ce1-126">해시 테이블을 정의할 때는 괄호 대신 중괄호를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-126">Notice that braces, instead of parentheses, are used to define a hashtable.</span></span> <span data-ttu-id="51ce1-127">그런 다음 이런 키를 사용하여 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-127">Then we add an item using a key like this:</span></span>

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

<span data-ttu-id="51ce1-128">사용자 이름이 키이며 나이는 저장할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-128">The person's name is the key and their age is the value that I want to save.</span></span>

## <a name="using-the-brackets-for-access"></a><span data-ttu-id="51ce1-129">액세스에 대괄호 사용</span><span class="sxs-lookup"><span data-stu-id="51ce1-129">Using the brackets for access</span></span>

<span data-ttu-id="51ce1-130">해시 테이블에 값을 추가하면 (배열에서처럼 숫자 인덱스를 사용하는 대신) 같은 키를 사용하여 다시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-130">Once you add your values to the hashtable, you can pull them back out using that same key (instead of using a numeric index like you would have for an array).</span></span>

```powershell
$ageList['Kevin']
$ageList['Alex']
```

<span data-ttu-id="51ce1-131">Kevin의 나이를 알고 싶다면 그의 이름을 사용하여 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-131">When I want Kevin's age, I use his name to access it.</span></span> <span data-ttu-id="51ce1-132">이 방법을 사용하면 해시 테이블에 값을 추가하거나 업데이트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-132">We can use this approach to add or update values into the hashtable too.</span></span> <span data-ttu-id="51ce1-133">위의 `add()` 함수 사용과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-133">This is just like using the `add()` function above.</span></span>

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

<span data-ttu-id="51ce1-134">값에 액세스하고 업데이트하는 데 사용할 수 있는 다른 구문이 있습니다. 관련 내용은 이후 섹션에서 다루겠습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-134">There's another syntax you can use for accessing and updating values that I'll cover in a later section.</span></span> <span data-ttu-id="51ce1-135">다른 언어로 PowerShell을 이용한다면 이러한 예제는 이제까지의 해시 테이블 사용 방법에도 잘 어울릴 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-135">If you're coming to PowerShell from another language, these examples should fit in with how you may have used hashtables before.</span></span>

### <a name="creating-hashtables-with-values"></a><span data-ttu-id="51ce1-136">값을 사용하여 해시 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="51ce1-136">Creating hashtables with values</span></span>

<span data-ttu-id="51ce1-137">지금까지 이러한 예제를 위한 빈 해시 테이블을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-137">So far I've created an empty hashtable for these examples.</span></span> <span data-ttu-id="51ce1-138">생성 시 키와 값을 미리 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-138">You can pre-populate the keys and values when you create them.</span></span>

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a><span data-ttu-id="51ce1-139">조회 테이블로 사용</span><span class="sxs-lookup"><span data-stu-id="51ce1-139">As a lookup table</span></span>

<span data-ttu-id="51ce1-140">이 형식의 해시 테이블이 제공하는 진정한 가치는 조회 테이블로 사용할 수 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-140">The real value of this type of a hashtable is that you can use them as a lookup table.</span></span> <span data-ttu-id="51ce1-141">다음은 간단한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-141">Here is a simple example.</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

<span data-ttu-id="51ce1-142">이 예제에서는 `$env` 변수의 환경을 지정하며 그러면 변수가 올바른 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-142">In this example, you specify an environment for the `$env` variable and it will pick the correct server.</span></span> <span data-ttu-id="51ce1-143">이런 선택에는 `switch($env){...}`를 사용할 수 있지만 해시 테이블도 좋은 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-143">You could use a `switch($env){...}` for a selection like this but a hashtable is a nice option.</span></span>

<span data-ttu-id="51ce1-144">나중에 사용하기 위해 조회 테이블을 동적으로 작성할 때는 더욱 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-144">This gets even better when you dynamically build the lookup table to use it later.</span></span> <span data-ttu-id="51ce1-145">따라서 무언가를 교차 참조해야 할 때는 이 방법을 고려해봐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-145">So think about using this approach when you need to cross reference something.</span></span> <span data-ttu-id="51ce1-146">PowerShell이 `Where-Object`를 이용한 파이프에서의 필터링에 부적합했다며 이 방법을 더 자주 활용했을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-146">I think we would see this even more if PowerShell wasn't so good at filtering on the pipe with `Where-Object`.</span></span> <span data-ttu-id="51ce1-147">성능이 중요한 상황이라면 이 접근 방식을 고려해 봐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-147">If you're ever in a situation where performance matters, this approach needs to be considered.</span></span>

<span data-ttu-id="51ce1-148">속도가 더 빠르지는 않지만 [성능이 중요하다면 테스트하라][]라는 규칙을 지킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-148">I won't say that it's faster, but it does fit into the rule of [If performance matters, test it][].</span></span>

#### <a name="multiselection"></a><span data-ttu-id="51ce1-149">다중 선택</span><span class="sxs-lookup"><span data-stu-id="51ce1-149">Multiselection</span></span>

<span data-ttu-id="51ce1-150">일반적으로 해시 테이블은 키 하나를 제공하여 값 하나를 얻는 키/값 쌍으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-150">Generally, you think of a hashtable as a key/value pair, where you provide one key and get one value.</span></span> <span data-ttu-id="51ce1-151">PowerShell을 사용하면 여러 값을 가져오는 키 배열을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-151">PowerShell allows you to provide an array of keys to get multiple values.</span></span>

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

<span data-ttu-id="51ce1-152">이 예제에서 위에서 설명한 것과 같은 조회 해시 테이블을 사용하고 세 가지 배열 스타일을 제공하여 일치 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-152">In this example, I use the same lookup hashtable from above and provide three different array styles to get the matches.</span></span> <span data-ttu-id="51ce1-153">대부분의 사람들이 모르는 PowerShell의 숨겨진 보석 같은 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-153">This is a hidden gem in PowerShell that most people aren't aware of.</span></span>

## <a name="iterating-hashtables"></a><span data-ttu-id="51ce1-154">해시 테이블 반복</span><span class="sxs-lookup"><span data-stu-id="51ce1-154">Iterating hashtables</span></span>

<span data-ttu-id="51ce1-155">해시 테이블은 키/값 쌍의 컬렉션이므로 배열이나 항목의 일반 목록과는 다른 방식으로 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-155">Because a hashtable is a collection of key/value pairs, you iterate over it differently than you do for an array or a normal list of items.</span></span>

<span data-ttu-id="51ce1-156">가장 먼저 주목해야 할 점은 해시 테이블을 파이프하면 파이프는 해시 테이블을 개체처럼 처리한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-156">The first thing to notice is that if you pipe your hashtable, the pipe treats it like one object.</span></span>

```powershell
PS> $ageList | Measure-Object
count : 1
```

<span data-ttu-id="51ce1-157">`.count` 속성에서 속성에 포함된 값 수를 알려준다고 해도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-157">Even though the `.count` property tells you how many values it contains.</span></span>

```powershell
PS> $ageList.count
2
```

<span data-ttu-id="51ce1-158">값만 필요하다면 `.values` 속성을 사용 하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-158">You get around this issue by using the `.values` property if all you need is just the values.</span></span>

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

<span data-ttu-id="51ce1-159">키를 열거하고 이러한 키를 사용하여 값에 액세스하는 방법이 더 효과적일 때도 잦습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-159">It's often more useful to enumerate the keys and use them to access the values.</span></span>

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

<span data-ttu-id="51ce1-160">다음은 `foreach(){...}` 루프를 이용하는 동일한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-160">Here is the same example with a `foreach(){...}` loop.</span></span>

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

<span data-ttu-id="51ce1-161">해시 테이블에서 각 키를 탐색한 다음 이 키를 사용하여 값에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-161">We are walking each key in the hashtable and then using it to access the value.</span></span> <span data-ttu-id="51ce1-162">해시 테이블을 컬렉션으로 사용할 때 자주 쓰는 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-162">This is a common pattern when working with hashtables as a collection.</span></span>

### <a name="getenumerator"></a><span data-ttu-id="51ce1-163">GetEnumerator()</span><span class="sxs-lookup"><span data-stu-id="51ce1-163">GetEnumerator()</span></span>

<span data-ttu-id="51ce1-164">이제 `GetEnumerator()`를 이용해 해시 테이블을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-164">That brings us to `GetEnumerator()` for iterating over our hashtable.</span></span>

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

<span data-ttu-id="51ce1-165">열거자는 각 키/값 쌍을 하나씩 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-165">The enumerator gives you each key/value pair one after another.</span></span> <span data-ttu-id="51ce1-166">이 사용 사례에 맞게 특별 제작한 열거자입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-166">It was designed specifically for this use case.</span></span> <span data-ttu-id="51ce1-167">이 사실을 알려준 [Mark Kraus](https://get-PowerShellblog.blogspot.com)에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-167">Thank you to [Mark Kraus](https://get-PowerShellblog.blogspot.com) for reminding me of this one.</span></span>

### <a name="badenumeration"></a><span data-ttu-id="51ce1-168">BadEnumeration</span><span class="sxs-lookup"><span data-stu-id="51ce1-168">BadEnumeration</span></span>

<span data-ttu-id="51ce1-169">열거 중인 해시 테이블을 수정할 수 없다는 점을 명심해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-169">One important detail is that you can't modify a hashtable while it's being enumerated.</span></span> <span data-ttu-id="51ce1-170">기본 `$environments` 예제부터 사용했다면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-170">If we start with our basic `$environments` example:</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

<span data-ttu-id="51ce1-171">또한 모든 키를 같은 서버 값으로 설정하면 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-171">And trying to set every key to the same server value fails.</span></span>

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

<span data-ttu-id="51ce1-172">겉보기에는 아무 문제 없어 보이더라도 결국에는 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-172">This will also fail even though it looks like it should also be fine:</span></span>

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

<span data-ttu-id="51ce1-173">이런 상황에서 중요한 점은 열거를 수행하기 전에 키를 복제하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-173">The trick to this situation is to clone the keys before doing the enumeration.</span></span>

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a><span data-ttu-id="51ce1-174">해시 테이블은 속성의 컬렉션입니다</span><span class="sxs-lookup"><span data-stu-id="51ce1-174">Hashtable as a collection of properties</span></span>

<span data-ttu-id="51ce1-175">지금까지 해시 테이블에 배치한 개체의 형식은 모두 동일한 개체 형식이었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-175">So far the type of objects we placed in our hashtable were all the same type of object.</span></span> <span data-ttu-id="51ce1-176">모든 예제에서 나이를 사용했고 키는 개인의 이름이었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-176">I used ages in all those examples and the key was the person's name.</span></span> <span data-ttu-id="51ce1-177">컬렉션의 각 개체에 이름이 있을 때 이를 확인하는 탁월한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-177">This is a great way to look at it when your collection of objects each have a name.</span></span> <span data-ttu-id="51ce1-178">PowerShell에서 해시 테이블을 사용하는 또 다른 일반적인 방법은 키가 속성의 이름인 속성 컬렉션을 보유하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-178">Another common way to use hashtables in PowerShell is to hold a collection of properties where the key is the name of the property.</span></span> <span data-ttu-id="51ce1-179">다음 예제를 통해 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-179">I'll step into that idea in this next example.</span></span>

### <a name="property-based-access"></a><span data-ttu-id="51ce1-180">속성 기반 액세스</span><span class="sxs-lookup"><span data-stu-id="51ce1-180">Property-based access</span></span>

<span data-ttu-id="51ce1-181">속성 기반 액세스를 사용하면 해시 테이블의 작동 방식과 PowerShell에서의 사용 방법이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-181">The use of property-based access changes the dynamics of hashtables and how you can use them in PowerShell.</span></span> <span data-ttu-id="51ce1-182">다음은 위에서처럼 속성을 키로 취급하는 일반적인 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-182">Here is our usual example from above treating the keys as properties.</span></span>

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

<span data-ttu-id="51ce1-183">위의 예제에서처럼 이번 예제에서도 해시 테이블에 없는 키는 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-183">Just like the examples above, this example adds those keys if they don't exist in the hashtable already.</span></span> <span data-ttu-id="51ce1-184">키를 정의하는 방법과 값에 따라 이 방법은 조금 이상할 수도 있고 완벽하게 어울릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-184">Depending on how you defined your keys and what your values are, this is either a little strange or a perfect fit.</span></span> <span data-ttu-id="51ce1-185">나이 목록 예제는 이 지점까지는 완벽하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-185">The age list example has worked great up until this point.</span></span> <span data-ttu-id="51ce1-186">다음 단계로 진행하려면 새로운 예제를 이용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-186">We need a new example for this to feel right going forward.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="51ce1-187">그리고 다음과 같은 `$person`에 특성을 추가하고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-187">And we can add and access attributes on the `$person` like this.</span></span>

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

<span data-ttu-id="51ce1-188">이 해시 테이블이 갑자기 개체처럼 보이고 개체처럼 작동할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-188">All of a sudden this hashtable starts to feel and act like an object.</span></span> <span data-ttu-id="51ce1-189">하지만 엄연히 항목 모음이므로 위의 모든 예제는 여전히 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-189">It's still a collection of things, so all the examples above still apply.</span></span> <span data-ttu-id="51ce1-190">우리는 다른 관점에서 살펴보았을 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-190">We just approach it from a different point of view.</span></span>

### <a name="checking-for-keys-and-values"></a><span data-ttu-id="51ce1-191">키 및 값 확인</span><span class="sxs-lookup"><span data-stu-id="51ce1-191">Checking for keys and values</span></span>

<span data-ttu-id="51ce1-192">대부분의 경우 다음과 같은 항목을 사용하여 값을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-192">In most cases, you can just test for the value with something like this:</span></span>

```powershell
if( $person.age ){...}
```

<span data-ttu-id="51ce1-193">단순하지만 제게는 수많은 버그의 원인이었는데, 논리에서 중요한 세부 사항 하나를 간과했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-193">It's simple but has been the source of many bugs for me because I was overlooking one important detail in my logic.</span></span> <span data-ttu-id="51ce1-194">처음에는 키가 존재했는지 테스트하는 용도로 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-194">I started to use it to test if a key was present.</span></span> <span data-ttu-id="51ce1-195">값이 `$false` 또는 0이라면 이 문은 예상과는 달리 `$false`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-195">When the value was `$false` or zero, that statement would return `$false` unexpectedly.</span></span>

```powershell
if( $person.age -ne $null ){...}
```

<span data-ttu-id="51ce1-196">이것은 0 값 관련 문제는 해결하지만 $null 대 존재하지 않는 키 관련 문제는 해결하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-196">This works around that issue for zero values but not $null vs non-existent keys.</span></span> <span data-ttu-id="51ce1-197">대부분의 경우에는 이를 구분하지 않아도 되지만 구분해야 할 때는 특정 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-197">Most of the time you don't need to make that distinction but there are functions for when you do.</span></span>

```powershell
if( $person.ContainsKey('age') ){...}
```

<span data-ttu-id="51ce1-198">또한 값을 테스트하고 싶지만 키를 모르거나 전체 컬렉션을 반복하고 싶지 않다면 `ContainsValue()`를 이용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-198">We also have a `ContainsValue()` for the situation where you need to test for a value without knowing the key or iterating the whole collection.</span></span>

### <a name="removing-and-clearing-keys"></a><span data-ttu-id="51ce1-199">키 제거 및 지우기</span><span class="sxs-lookup"><span data-stu-id="51ce1-199">Removing and clearing keys</span></span>

<span data-ttu-id="51ce1-200">`.Remove()` 함수를 사용하여 키를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-200">You can remove keys with the `.Remove()` function.</span></span>

```powershell
$person.remove('age')
```

<span data-ttu-id="51ce1-201">키에 `$null` 값을 할당하면 `$null` 값이 있는 키만 남습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-201">Assigning them a `$null` value just leaves you with a key that has a `$null` value.</span></span>

<span data-ttu-id="51ce1-202">해시 테이블을 지우는 일반적인 방법은 빈 해시 테이블로 초기화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-202">A common way to clear a hashtable is to just initialize it to an empty hashtable.</span></span>

```powershell
$person = @{}
```

<span data-ttu-id="51ce1-203">이 작업을 수행하는 동안 `clear()` 함수를 대신 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="51ce1-203">While that does work, try to use the `clear()` function instead.</span></span>

```powershell
$person.clear()
```

<span data-ttu-id="51ce1-204">함수를 사용하면 자체 문서화 코드를 만들고 코드의 의도가 대단히 명확하게 드러나는 인스턴스 예시입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-204">This is one of those instances where using the function creates self-documenting code and it makes the intentions of the code very clean.</span></span>

## <a name="all-the-fun-stuff"></a><span data-ttu-id="51ce1-205">흥미로운 요소</span><span class="sxs-lookup"><span data-stu-id="51ce1-205">All the fun stuff</span></span>

### <a name="ordered-hashtables"></a><span data-ttu-id="51ce1-206">순서 지정된 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="51ce1-206">Ordered hashtables</span></span>

<span data-ttu-id="51ce1-207">기본적으로 해시 테이블은 순서가 지정되지(또는 정렬되지) 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-207">By default, hashtables aren't ordered (or sorted).</span></span> <span data-ttu-id="51ce1-208">기존 환경에서는 항상 키를 사용하여 값에 액세스할 때는 순서가 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-208">In the traditional context, the order doesn't matter when you always use a key to access values.</span></span> <span data-ttu-id="51ce1-209">속성을 정의한 순서대로 유지하고 싶을 때가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-209">You may find that you want the properties to stay in the order that you define them.</span></span> <span data-ttu-id="51ce1-210">다행히 `ordered` 키워드를 사용하면 이 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-210">Thankfully, there's a way to do that with the `ordered` keyword.</span></span>

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="51ce1-211">이제 키와 값을 열거할 때 이 순서대로 열거됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-211">Now when you enumerate the keys and values, they stay in that order.</span></span>

### <a name="inline-hashtables"></a><span data-ttu-id="51ce1-212">인라인 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="51ce1-212">Inline hashtables</span></span>

<span data-ttu-id="51ce1-213">해시 테이블을 한 줄에 정의할 때는 세미콜론을 이용해 키/값 쌍을 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-213">When you're defining a hashtable on one line, you can separate the key/value pairs with a semicolon.</span></span>

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

<span data-ttu-id="51ce1-214">파이프에서 만들 때는 특히 더 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-214">This will come in handy if you're creating them on the pipe.</span></span>

### <a name="custom-expressions-in-common-pipeline-commands"></a><span data-ttu-id="51ce1-215">공통 파이프라인 명령에서의 사용자 지정 식</span><span class="sxs-lookup"><span data-stu-id="51ce1-215">Custom expressions in common pipeline commands</span></span>

<span data-ttu-id="51ce1-216">해시 테이블을 이용한 사용자 지정 또는 계산된 속성 생성을 지원하는 몇 가지 cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-216">There are a few cmdlets that support the use of hashtables to create custom or calculated properties.</span></span> <span data-ttu-id="51ce1-217">`Select-Object` 및 `Format-Table`과 함께 자주 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-217">You commonly see this with `Select-Object` and `Format-Table`.</span></span> <span data-ttu-id="51ce1-218">해시 테이블에는 완전히 펼치면 이런 식으로 보이는 특수 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-218">The hashtables have a special syntax that looks like this when fully expanded.</span></span>

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

<span data-ttu-id="51ce1-219">`name`은 cmdlet이 해당 열에 지정하는 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-219">The `name` is what the cmdlet would label that column.</span></span> <span data-ttu-id="51ce1-220">`expression`은 `$_`가 파이프 상의 개체 값을 때 실행되는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-220">The `expression` is a script block that is executed where `$_` is the value of the object on the pipe.</span></span> <span data-ttu-id="51ce1-221">다음은 실제로 작동하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-221">Here is that script in action:</span></span>

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

<span data-ttu-id="51ce1-222">변수에 배치했지만 인라인으로 쉽게 정의할 수 있으며 정의 중에 `name`을 `n`으로, `expression`을 `e`로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-222">I placed that in a variable but it could easily be defined inline and you can shorten `name` to `n` and `expression` to `e` while you're at it.</span></span>

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

<span data-ttu-id="51ce1-223">개인적으로 명령이 길어지는 것을 좋아하지 않으며, 제가 관여하지 않는 일부 잘못된 동작을 승격하곤 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-223">I personally don't like how long that makes commands and it often promotes some bad behaviors that I won't get into.</span></span> <span data-ttu-id="51ce1-224">스크립트에서 이 방법을 사용하는 대신 원하는 필드와 속성을 모두 사용하여 새 해시 테이블이나 `pscustomobject`를 만드는 방법을 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-224">I'm more likely to create a new hashtable or `pscustomobject` with all the fields and properties that I want instead of using this approach in scripts.</span></span> <span data-ttu-id="51ce1-225">하지만 이 작업은 수행하는 코드는 아주 많으니 이 방법을 알려드리고 싶었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-225">But there's a lot of code out there that does this so I wanted you to be aware of it.</span></span> <span data-ttu-id="51ce1-226">`pscustomobject` 생성 방법은 나중에 말씀드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-226">I talk about creating a `pscustomobject` later on.</span></span>

### <a name="custom-sort-expression"></a><span data-ttu-id="51ce1-227">사용자 지정 정렬 식</span><span class="sxs-lookup"><span data-stu-id="51ce1-227">Custom sort expression</span></span>

<span data-ttu-id="51ce1-228">정렬하려는 데이터가 개체에 있다면 컬렉션을 쉽게 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-228">It's easy to sort a collection if the objects have the data that you want to sort on.</span></span> <span data-ttu-id="51ce1-229">개체에 데이터를 추가하면 컬렉션을 정렬하거나 `Sort-Object`에 대한 사용자 지정 식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-229">You can either add the data to the object before you sort it or create a custom expression for `Sort-Object`.</span></span>

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

<span data-ttu-id="51ce1-230">이 예제에서는 사용자 목록을 가져오고 사용자 지정 cmdlet을 사용하여 정렬에 관한 추가 정보만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-230">In this example I'm taking a list of users and using some custom cmdlet to get additional information just for the sort.</span></span>

#### <a name="sort-a-list-of-hashtables"></a><span data-ttu-id="51ce1-231">해시 테이블 목록 정렬</span><span class="sxs-lookup"><span data-stu-id="51ce1-231">Sort a list of Hashtables</span></span>

<span data-ttu-id="51ce1-232">정렬하려는 해시 테이블 목록이 있다면 `Sort-Object`에서는 키를 속성으로 처리하지 않음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-232">If you have a list of hashtables that you want to sort, you'll find that the `Sort-Object` doesn't treat your keys as properties.</span></span> <span data-ttu-id="51ce1-233">사용자 지정 정렬 식을 사용하면 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-233">We can get a round that by using a custom sort expression.</span></span>

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a><span data-ttu-id="51ce1-234">cmdlet에서 해시 테이블 스플래팅</span><span class="sxs-lookup"><span data-stu-id="51ce1-234">Splatting hashtables at cmdlets</span></span>

<span data-ttu-id="51ce1-235">이것은 많은 사람들이 빨리 알아차리지 못하는, 해시 테이블에서 가장 좋아하는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-235">This is one of my favorite things about hashtables that many people don't discover early on.</span></span>
<span data-ttu-id="51ce1-236">이 작업은 모든 속성을 한 줄에 있는 cmdlet에 제공하는 대신 먼저 해시 테이블에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-236">The idea is that instead of providing all the properties to a cmdlet on one line, you can instead pack them into a hashtable first.</span></span> <span data-ttu-id="51ce1-237">그러면 특수한 방법을 이용해 해시 테이블을 함수에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-237">Then you can give the hashtable to the function in a special way.</span></span>
<span data-ttu-id="51ce1-238">다음은 DHCP 범위를 일반적인 방법으로 만드는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-238">Here is an example of creating a DHCP scope the normal way.</span></span>

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

<span data-ttu-id="51ce1-239">[스플래팅][]을 사용하지 않으면 모든 요소를 한 줄에 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-239">Without using [splatting][], all those things need to be defined on a single line.</span></span> <span data-ttu-id="51ce1-240">이 기능은 화면 밖으로 스크롤하거나 원하는 위치에서 줄을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-240">It either scrolls off the screen or will wrap where ever it feels like.</span></span> <span data-ttu-id="51ce1-241">이제 이것을 스플래팅을 사용하는 명령과 비교해보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-241">Now compare that to a command that uses splatting.</span></span>

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

<span data-ttu-id="51ce1-242">`$` 대신 `@` 부호를 사용하면 스플랫 작업이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-242">The use of the `@` sign instead of the `$` is what invokes the splat operation.</span></span>

<span data-ttu-id="51ce1-243">이 예제를 얼마나 쉽게 읽을 수 있는지 잠시 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="51ce1-243">Just take a moment to appreciate how easy that example is to read.</span></span> <span data-ttu-id="51ce1-244">동일한 값을 가진 완전히 동일한 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-244">They are the exact same command with all the same values.</span></span> <span data-ttu-id="51ce1-245">두 번째 명령이 더 이해하기 쉽고 향후 유지 관리도 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-245">The second one is easier to understand and maintain going forward.</span></span>

<span data-ttu-id="51ce1-246">명령이 너무 길어지면 언제든 스플래팅을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-246">I use splatting anytime the command gets too long.</span></span> <span data-ttu-id="51ce1-247">정의가 너무 길어 창을 오른쪽으로 스크롤해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-247">I define too long as causing my window to scroll right.</span></span> <span data-ttu-id="51ce1-248">함수에 속성 3개가 적중한다면 대부분의 경우 스플래팅한 해시 테이블을 이용해 함수를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-248">If I hit three properties for a function, odds are that I'll rewrite it using a splatted hashtable.</span></span>

### <a name="splatting-for-optional-parameters"></a><span data-ttu-id="51ce1-249">선택적 매개 변수 스플래팅</span><span class="sxs-lookup"><span data-stu-id="51ce1-249">Splatting for optional parameters</span></span>

<span data-ttu-id="51ce1-250">스플래팅을 사용하는 가장 일반적인 방법은 스크립트의 다른 부분에서 제공하는 선택적 매개 변수를 처리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-250">One of the most common ways I use splatting is to deal with optional parameters that come from some place else in my script.</span></span> <span data-ttu-id="51ce1-251">선택적 `$Credential` 인수가 있는 `Get-CIMInstance` 호출을 래핑하는 함수가 있다고 합시다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-251">Let's say I have a function that wraps a `Get-CIMInstance` call that has an optional `$Credential` argument.</span></span>

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

<span data-ttu-id="51ce1-252">먼저 일반 매개 변수를 사용하여 해시 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-252">I start by creating my hashtable with common parameters.</span></span> <span data-ttu-id="51ce1-253">그런 다음 `$Credential`이 존재한다면 이를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-253">Then I add the `$Credential` if it exists.</span></span>
<span data-ttu-id="51ce1-254">여기서는 스플래팅을 사용하고 있으니 코드에서 `Get-CIMInstance`를 한 번만 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-254">Because I'm using splatting here, I only need to have the call to `Get-CIMInstance` in my code once.</span></span> <span data-ttu-id="51ce1-255">이 디자인 패턴은 대단히 깔끔하며 많은 선택적 매개 변수를 쉽게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-255">This design pattern is very clean and can handle lots of optional parameters easily.</span></span>

<span data-ttu-id="51ce1-256">불공평하지 않도록 매개 변수에 `$null` 값을 허용하는 명령을 작성하셔도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-256">To be fair, you could write your commands to allow `$null` values for parameters.</span></span> <span data-ttu-id="51ce1-257">호출하는 다른 명령을 제어할 수 없을 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-257">You just don't always have control over the other commands you're calling.</span></span>

### <a name="multiple-splats"></a><span data-ttu-id="51ce1-258">여러 스플랫</span><span class="sxs-lookup"><span data-stu-id="51ce1-258">Multiple splats</span></span>

<span data-ttu-id="51ce1-259">여러 해시 테이블을 동일한 cmdlet으로 스플랫할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-259">You can splat multiple hashtables to the same cmdlet.</span></span> <span data-ttu-id="51ce1-260">처음 스플래팅 예제를 다시 확인하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-260">If we revisit our original splatting example:</span></span>

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

<span data-ttu-id="51ce1-261">많은 명령에 전달하는 공통 매개 변수 집합이 있을 때 이 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-261">I'll use this method when I have a common set of parameters that I'm passing to lots of commands.</span></span>

### <a name="splatting-for-clean-code"></a><span data-ttu-id="51ce1-262">깔끔한 코드의 스플래팅</span><span class="sxs-lookup"><span data-stu-id="51ce1-262">Splatting for clean code</span></span>

<span data-ttu-id="51ce1-263">코드를 더 깔끔하게 만들 수 있다면 단일 매개 변수로 스플래팅을 수행해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-263">There's nothing wrong with splatting a single parameter if makes you code cleaner.</span></span>

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a><span data-ttu-id="51ce1-264">실행 파일 스플래팅</span><span class="sxs-lookup"><span data-stu-id="51ce1-264">Splatting executables</span></span>

<span data-ttu-id="51ce1-265">스플래팅은 `/param:value` 구문을 사용하는 일부 실행 파일에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-265">Splatting also works on some executables that use a `/param:value` syntax.</span></span> <span data-ttu-id="51ce1-266">예를 들어 `Robocopy.exe`에는 이와 비슷한 몇 가지 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-266">`Robocopy.exe`, for example, has some parameters like this.</span></span>

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

<span data-ttu-id="51ce1-267">모든 매개 변수가 유용한지는 모르겠지만 흥미로운 요소이기는 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-267">I don't know that this is all that useful, but I found it interesting.</span></span>

## <a name="adding-hashtables"></a><span data-ttu-id="51ce1-268">해시 테이블 추가</span><span class="sxs-lookup"><span data-stu-id="51ce1-268">Adding hashtables</span></span>

<span data-ttu-id="51ce1-269">해시 테이블은 더하기 연산자를 이용하여 두 해시 테이블을 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-269">Hashtables support the addition operator to combine two hashtables.</span></span>

```powershell
$person += @{Zip = '78701'}
```

<span data-ttu-id="51ce1-270">두 해시 테이블이 키를 공유하지 않을 때만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-270">This only works if the two hashtables don't share a key.</span></span>

## <a name="nested-hashtables"></a><span data-ttu-id="51ce1-271">중첩된 해시 테이블</span><span class="sxs-lookup"><span data-stu-id="51ce1-271">Nested hashtables</span></span>

<span data-ttu-id="51ce1-272">해시 테이블 내에서 다른 해시 테이블을 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-272">We can use hashtables as values inside a hashtable.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

<span data-ttu-id="51ce1-273">먼저 키 두 개가 있는 기본 해시 테이블을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-273">I started with a basic hashtable containing two keys.</span></span> <span data-ttu-id="51ce1-274">빈 해시 테이블이 있는 `location`이라는 키를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-274">I added a key called `location` with an empty hashtable.</span></span> <span data-ttu-id="51ce1-275">그런 다음 이 `location` 해시 테이블에 마지막 항목 두 개를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-275">Then I added the last two items to that `location` hashtable.</span></span> <span data-ttu-id="51ce1-276">이상의 작업을 인라인으로 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-276">We can do this all inline too.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

<span data-ttu-id="51ce1-277">위에서 확인한 것과 동일한 해시 테이블을 만들며 속성에도 동일한 방식으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-277">This creates the same hashtable that we saw above and can access the properties the same way.</span></span>

```powershell
$person.location.city
Austin
```

<span data-ttu-id="51ce1-278">개체의 구조체에 접근하는 방법은 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-278">There are many ways to approach the structure of your objects.</span></span> <span data-ttu-id="51ce1-279">다음은 중첩된 해시 테이블을 확인하는 두 번째 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-279">Here is a second way to look at a nested hashtable.</span></span>

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

<span data-ttu-id="51ce1-280">해시 테이블을 개체 컬렉션으로 사용하는 방식과 속성 컬렉션으로 사용하는 방식을 결합하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-280">This mixes the concept of using hashtables as a collection of objects and a collection of properties.</span></span> <span data-ttu-id="51ce1-281">원하는 방법을 사용하여 중첩하더라도 값에 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-281">The values are still easy to access even when they're nested using whatever approach you prefer.</span></span>

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

<span data-ttu-id="51ce1-282">속성처럼 처리할 때는 점 속성을 사용하는 편입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-282">I tend to use the dot property when I'm treating it like a property.</span></span> <span data-ttu-id="51ce1-283">이것은 코드에서 정적으로 정의하는 일반적인 항목으로, 생각나는 대로 적은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-283">Those are generally things I've defined statically in my code and I know them off the top of my head.</span></span> <span data-ttu-id="51ce1-284">목록을 탐색하거나 프로그래밍 방식으로 키에 액세스해야 한다면 대괄호를 사용하여 키 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-284">If I need to walk the list or programmatically access the keys, I use the brackets to provide the key name.</span></span>

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

<span data-ttu-id="51ce1-285">해시 테이블을 중첩하는 기능은 뛰어난 유연과 많은 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-285">Having the ability to nest hashtables gives you a lot of flexibility and options.</span></span>

### <a name="looking-at-nested-hashtables"></a><span data-ttu-id="51ce1-286">중첩된 해시 테이블 확인</span><span class="sxs-lookup"><span data-stu-id="51ce1-286">Looking at nested hashtables</span></span>

<span data-ttu-id="51ce1-287">해시 테이블 중첩을 시작하면 콘솔에서 이를 쉽게 확인할 방법이 필요하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-287">As soon as you start nesting hashtables, you're going to need an easy way to look at them from the console.</span></span> <span data-ttu-id="51ce1-288">마지막 해시 테이블을 사용하면 다음과 비슷한 출력을 얻게 되며 이 출력은 아래쪽으로만 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-288">If I take that last hashtable, I get an output that looks like this and it only goes so deep:</span></span>

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

<span data-ttu-id="51ce1-289">이러한 요소를 확인할 때 사용하는 go to 명령은 `ConvertTo-JSON`입니다. 아주 깔끔한 데다 JSON을 특히 자주 사용하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-289">My go to command for looking at these things is `ConvertTo-JSON` because it's very clean and I frequently use JSON on other things.</span></span>

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

<span data-ttu-id="51ce1-290">JSON을 모르는 분도 원하는 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-290">Even if you don't know JSON, you should be able to see what you're looking for.</span></span> <span data-ttu-id="51ce1-291">이런 류의 구조화된 데이터를 위한 `Format-Custom` 명령도 있지만 저는 여전히 JSON 보기를 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-291">There's a `Format-Custom` command for structured data like this but I still like the JSON view better.</span></span>

## <a name="creating-objects"></a><span data-ttu-id="51ce1-292">개체 만들기</span><span class="sxs-lookup"><span data-stu-id="51ce1-292">Creating objects</span></span>

<span data-ttu-id="51ce1-293">개체만 필요하며 해시 테이블을 사용하여 속성을 보유하는 것만으로는 작업을 완료할 수 없을 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-293">Sometimes you just need to have an object and using a hashtable to hold properties just isn't getting the job done.</span></span> <span data-ttu-id="51ce1-294">대부분의 경우 사람들은 키를 열 이름으로 표시하고 싶어 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-294">Most commonly you want to see the keys as column names.</span></span> <span data-ttu-id="51ce1-295">`pscustomobject`를 사용하면 이 작업을 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-295">A `pscustomobject` makes that easy.</span></span>

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="51ce1-296">처음에 이것을 `pscustomobject`로 만들지 않았다 하더라도 필요하다면 언제든 캐스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-296">Even if you don't create it as a `pscustomobject` initially, you can always cast it later when needed.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="51ce1-297">이 문서 다음에 읽게 될 [pscustomobject][]에 자세한 내용을 기록해두었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-297">I already have detailed write-up for [pscustomobject][] that you should go read after this one.</span></span> <span data-ttu-id="51ce1-298">이 문서는 여기서 배운 많은 내용을 바탕으로 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-298">It builds on a lot of the things learned here.</span></span>

## <a name="reading-and-writing-hashtables-to-file"></a><span data-ttu-id="51ce1-299">해시 테이블을 읽고 파일에 쓰기</span><span class="sxs-lookup"><span data-stu-id="51ce1-299">Reading and writing hashtables to file</span></span>

### <a name="saving-to-csv"></a><span data-ttu-id="51ce1-300">CSV에 저장</span><span class="sxs-lookup"><span data-stu-id="51ce1-300">Saving to CSV</span></span>

<span data-ttu-id="51ce1-301">해시 테이블을 가져와 CSV에 저장하는 작업은 위에서 언급한 문제이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-301">Struggling with getting a hashtable to save to a CSV is one of the difficulties that I was referring to above.</span></span> <span data-ttu-id="51ce1-302">해시 테이블을 `pscustomobject`로 변환하면 CSV에 올바르게 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-302">Convert your hashtable to a `pscustomobject` and it will save correctly to CSV.</span></span> <span data-ttu-id="51ce1-303">`pscustomobject`로 시작하면 열 순서가 유지되기 때문에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-303">It helps if you start with a `pscustomobject` so the column order is preserved.</span></span> <span data-ttu-id="51ce1-304">그러나 필요하다면 `pscustomobject`를 인라인에 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-304">But you can cast it to a `pscustomobject` inline if needed.</span></span>

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

<span data-ttu-id="51ce1-305">[pscustomobject][] 이용에 관한 제 문서에서는 이 주제도 다루고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-305">Again, check out my write-up on using a [pscustomobject][].</span></span>

### <a name="saving-a-nested-hashtable-to-file"></a><span data-ttu-id="51ce1-306">중첩된 해시 테이블을 파일에 저장</span><span class="sxs-lookup"><span data-stu-id="51ce1-306">Saving a nested hashtable to file</span></span>

<span data-ttu-id="51ce1-307">중첩된 해시 테이블을 파일에 저장한 다음 다시 읽어야 한다면, JSON cmdlet을 사용하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-307">If I need to save a nested hashtable to a file and then read it back in again, I use the JSON cmdlets to do it.</span></span>

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

<span data-ttu-id="51ce1-308">이 방법에는 두 가지 중요한 점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-308">There are two important points about this method.</span></span> <span data-ttu-id="51ce1-309">첫 번째는 JSON은 여러 줄로 작성되므로 `-Raw` 옵션을 사용하여 다시 단일 문자열로 읽어야 한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-309">First is that the JSON is written out multiline so I need to use the `-Raw` option to read it back into a single string.</span></span> <span data-ttu-id="51ce1-310">두 번째는 가져온 개체는 더 이상 `[hashtable]`이 아니라는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-310">The Second is that the imported object is no longer a `[hashtable]`.</span></span> <span data-ttu-id="51ce1-311">가져온 개체는 `[pscustomobject]`가 되며 이를 예상하지 못하면 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-311">It's now a `[pscustomobject]` and that can cause issues if you don't expect it.</span></span>

<span data-ttu-id="51ce1-312">많이 중첩된 해시 테이블을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-312">Watch for deeply-nested hashtables.</span></span> <span data-ttu-id="51ce1-313">많이 중첩된 해시 테이블을 JSON으로 변환하면 원하는 결과를 얻지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-313">When you convert it to JSON you might not get the results you expect.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

<span data-ttu-id="51ce1-314">**Depth** 매개 변수를 사용하여 중첩된 모든 해시 테이블을 확장하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-314">Use **Depth** parameter to ensure that you have expanded all the nested hashtables.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

<span data-ttu-id="51ce1-315">가져올 때 이것이 `[hashtable]`이어야 한다면 `Export-CliXml`과 `Import-CliXml` 명령을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-315">If you need it to be a `[hashtable]` on import, then you need to use the `Export-CliXml` and `Import-CliXml` commands.</span></span>

### <a name="converting-json-to-hashtable"></a><span data-ttu-id="51ce1-316">JSON을 해시 테이블로 변환</span><span class="sxs-lookup"><span data-stu-id="51ce1-316">Converting JSON to Hashtable</span></span>

<span data-ttu-id="51ce1-317">JSON을 `[hashtable]`로 변환해야 한다면 제가 아는 한 가지 방법은 .NET에서 [JavaScriptSerializer][]를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-317">If you need to convert JSON to a `[hashtable]`, there's one way that I know of to do it with the [JavaScriptSerializer][] in .NET.</span></span>

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

<span data-ttu-id="51ce1-318">PowerShell v6부터 JSON 지원에서는 NewtonSoft JSON.NET가 사용되고 해시 테이블 지원이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-318">Beginning in PowerShell v6, JSON support uses the NewtonSoft JSON.NET and adds hashtable support.</span></span>

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

<span data-ttu-id="51ce1-319">PowerShell 6.2에서 **Depth** 매개 변수가 `ConvertFrom-Json`에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-319">PowerShell 6.2 added the **Depth** parameter to `ConvertFrom-Json`.</span></span> <span data-ttu-id="51ce1-320">기본 **Depth** 는 1024입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-320">The default **Depth** is 1024.</span></span>

### <a name="reading-directly-from-a-file"></a><span data-ttu-id="51ce1-321">파일에서 직접 읽기</span><span class="sxs-lookup"><span data-stu-id="51ce1-321">Reading directly from a file</span></span>

<span data-ttu-id="51ce1-322">PowerShell 구문을 사용하는 해시 테이블을 있는 파일을 사용한다면 파일에서 바로 가져오는 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-322">If you have a file that contains a hashtable using PowerShell syntax, there's a way to import it directly.</span></span>

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

<span data-ttu-id="51ce1-323">이 방법은 파일 콘텐츠를 `scriptblock`으로 가져온 다음 다른 PowerShell 명령이 없는 지 확인한 후에 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-323">It imports the contents of the file into a `scriptblock`, then checks to make sure it doesn't have any other PowerShell commands in it before it executes it.</span></span>

<span data-ttu-id="51ce1-324">그러고 보니, 모듈 매니페스트(psd1 파일)가 단순한 해시 테이블이라는 사실을 아셨나요?</span><span class="sxs-lookup"><span data-stu-id="51ce1-324">On that note, did you know that a module manifest (the psd1 file) is just a hashtable?</span></span>

## <a name="keys-can-be-any-object"></a><span data-ttu-id="51ce1-325">키는 모든 개체가 될 수 있음</span><span class="sxs-lookup"><span data-stu-id="51ce1-325">Keys can be any object</span></span>

<span data-ttu-id="51ce1-326">대부분의 경우 키는 단순히 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-326">Most of the time, the keys are just strings.</span></span> <span data-ttu-id="51ce1-327">따라서 어느 부분이든 따옴표를 붙이면 키로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-327">So we can put quotes around anything and make it a key.</span></span>

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

<span data-ttu-id="51ce1-328">여러분이 상상하지도 못했던 놀라운 일을 실현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-328">You can do some odd things that you may not have realized you could do.</span></span>

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

<span data-ttu-id="51ce1-329">하지만 할 수 있다고 해서 반드시 해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-329">Just because you can do something, it doesn't mean that you should.</span></span> <span data-ttu-id="51ce1-330">마지막 항목은 일어나기를 기다리는 버그처럼 보이며 코드를 읽는 사람이라면 누구나 오해하게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-330">That last one just looks like a bug waiting to happen and would be easily misunderstood by anyone reading your code.</span></span>

<span data-ttu-id="51ce1-331">엄밀히 말하면 키는 문자열이 아니어도 되지만 사람들은 문자열만 사용했다고 생각하곤 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-331">Technically your key doesn't have to be a string but they're easier to think about if you only use strings.</span></span> <span data-ttu-id="51ce1-332">그러나 인덱싱은 복잡한 키에서는 제대로 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-332">However, indexing doesn't work well with the complex keys.</span></span>

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

<span data-ttu-id="51ce1-333">키를 사용하여 해시 테이블의 값에 액세스하는 것은 항상 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-333">Accessing a value in the hashtable by its key doesn't always work.</span></span> <span data-ttu-id="51ce1-334">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-334">For example:</span></span>

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

<span data-ttu-id="51ce1-335">키가 배열인 경우 멤버 액세스(`.`) 표기법으로 사용할 수 있도록 `$key` 변수를 하위 식으로 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-335">When the key is an array, you must wrap the `$key` variable in a subexpression so that it can be used with member access (`.`) notation.</span></span> <span data-ttu-id="51ce1-336">또는 배열 인덱스(`[]`) 표기법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-336">Or, you can use array index (`[]`) notation.</span></span>

## <a name="use-in-automatic-variables"></a><span data-ttu-id="51ce1-337">자동 변수에서 사용</span><span class="sxs-lookup"><span data-stu-id="51ce1-337">Use in automatic variables</span></span>

### <a name="psboundparameters"></a><span data-ttu-id="51ce1-338">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="51ce1-338">$PSBoundParameters</span></span>

<span data-ttu-id="51ce1-339">[$PSBoundParameters][]는 함수의 컨텍스트 내에만 존재하는 자동 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-339">[$PSBoundParameters][] is an automatic variable that only exists inside the context of a function.</span></span>
<span data-ttu-id="51ce1-340">함수를 호출한 모든 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-340">It contains all the parameters that the function was called with.</span></span> <span data-ttu-id="51ce1-341">해시 테이블은 아니지만 해시 테이블처럼 처리해도 될 정도로 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-341">This isn't exactly a hashtable but close enough that you can treat it like one.</span></span>

<span data-ttu-id="51ce1-342">키 제거 및 다른 함수에 스플래팅 같은 작업도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-342">That includes removing keys and splatting it to other functions.</span></span> <span data-ttu-id="51ce1-343">프록시 함수를 작성한다면 이 내용을 더 자세히 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="51ce1-343">If you find yourself writing proxy functions, take a closer look at this one.</span></span>

<span data-ttu-id="51ce1-344">자세한 내용은 [about_Automatic_Variables][]를 참조하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-344">See [about_Automatic_Variables][] for more details.</span></span>

### <a name="psboundparameters-gotcha"></a><span data-ttu-id="51ce1-345">PSBoundParameters 알려진 문제</span><span class="sxs-lookup"><span data-stu-id="51ce1-345">PSBoundParameters gotcha</span></span>

<span data-ttu-id="51ce1-346">이것은 매개 변수로 전달되는 값만 포함한다는 사실을 명심해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-346">One important thing to remember is that this only includes the values that are passed in as parameters.</span></span> <span data-ttu-id="51ce1-347">기본값이 있지만 호출자가 전달하지 않은 매개 변수를 이용한다면, `$PSBoundParameters`에는 이러한 값이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-347">If you also have parameters with default values but aren't passed in by the caller, `$PSBoundParameters` doesn't contain those values.</span></span> <span data-ttu-id="51ce1-348">자주 간과되는 사실입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-348">This is commonly overlooked.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="51ce1-349">$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="51ce1-349">$PSDefaultParameterValues</span></span>

<span data-ttu-id="51ce1-350">이 자동 변수를 사용하면 cmdlet을 변경하지 않고도 모든 cmdlet에 기본값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-350">This automatic variable lets you assign default values to any cmdlet without changing the cmdlet.</span></span>
<span data-ttu-id="51ce1-351">이 예제를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="51ce1-351">Take a look at this example.</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

<span data-ttu-id="51ce1-352">`UTF8`을 `Out-File -Encoding` 매개 변수의 기본값으로 설정하는 `$PSDefaultParameterValues` 해시 테이블에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-352">This adds an entry to the `$PSDefaultParameterValues` hashtable that sets `UTF8` as the default value for the `Out-File -Encoding` parameter.</span></span> <span data-ttu-id="51ce1-353">세션별로 추가되므로 `$profile`에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-353">This is session-specific so you should place it in your `$profile`.</span></span>

<span data-ttu-id="51ce1-354">주로 자주 입력하는 값을 미리 할당하는 용도로 이 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-354">I use this often to pre-assign values that I type quite often.</span></span>

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

<span data-ttu-id="51ce1-355">와일드 카드를 허용하기 때문에 값을 대량으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-355">This also accepts wildcards so you can set values in bulk.</span></span> <span data-ttu-id="51ce1-356">다음은 대표적인 사용 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-356">Here are some ways you can use that:</span></span>

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

<span data-ttu-id="51ce1-357">자세한 내용을 알고 싶다면 [Michael Sorens][]가 작성한 이 훌륭한 [자동 기본값][] 관련 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51ce1-357">For a more in-depth breakdown, see this great article on [Automatic Defaults][] by [Michael Sorens][].</span></span>

## <a name="regex-matches"></a><span data-ttu-id="51ce1-358">정규식 $Matches</span><span class="sxs-lookup"><span data-stu-id="51ce1-358">Regex $Matches</span></span>

<span data-ttu-id="51ce1-359">`-match` 연산자를 사용하면 `$matches`라는 자동 변수가 일치 항목의 결과와 함께 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-359">When you use the `-match` operator, an automatic variable called `$matches` is created with the results of the match.</span></span> <span data-ttu-id="51ce1-360">정규식에 하위 식이 있다면 하위 항목도 함께 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-360">If you have any sub expressions in your regex, those sub matches are also listed.</span></span>

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a><span data-ttu-id="51ce1-361">명명된 일치 항목</span><span class="sxs-lookup"><span data-stu-id="51ce1-361">Named matches</span></span>

<span data-ttu-id="51ce1-362">대부분의 사람은 모르지만 제가 제일 좋아하는 기능에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-362">This is one of my favorite features that most people don't know about.</span></span> <span data-ttu-id="51ce1-363">명명된 정규식 일치를 사용하면 일치 항목의 이름을 기준으로 일치 항목에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-363">If you use a named regex match, then you can access that match by name on the matches.</span></span>

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

<span data-ttu-id="51ce1-364">위의 예제에서는 `(?<Name>.*)`이 명명된 하위 식입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-364">In the example above, the `(?<Name>.*)` is a named sub expression.</span></span> <span data-ttu-id="51ce1-365">이 값은 `$Matches.Name` 속성에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-365">This value is then placed in the `$Matches.Name` property.</span></span>

## <a name="group-object--ashashtable"></a><span data-ttu-id="51ce1-366">Group-Object -AsHashtable</span><span class="sxs-lookup"><span data-stu-id="51ce1-366">Group-Object -AsHashtable</span></span>

<span data-ttu-id="51ce1-367">`Group-Object`의 잘 알려지지 않은 기능 중 하나는 일부 데이터 집합을 해시 테이블로 전환하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-367">One little known feature of `Group-Object` is that it can turn some datasets into a hashtable for you.</span></span>

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

<span data-ttu-id="51ce1-368">이렇게 하면 각 행을 해시 테이블에 추가하고 지정 된 속성을 키로 사용하여 각 행에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-368">This will add each row into a hashtable and use the specified property as the key to access it.</span></span>

## <a name="copying-hashtables"></a><span data-ttu-id="51ce1-369">해시 테이블 복사</span><span class="sxs-lookup"><span data-stu-id="51ce1-369">Copying Hashtables</span></span>

<span data-ttu-id="51ce1-370">한 가지 명심해야 할 점은 해시 테이블은 개체라는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-370">One important thing to know is that hashtables are objects.</span></span> <span data-ttu-id="51ce1-371">그리고 각 변수는 개체에 대한 참조일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-371">And each variable is just a reference to an object.</span></span> <span data-ttu-id="51ce1-372">따라서 해시 테이블의 유효한 복사본을 만들려면 더 많은 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-372">This means that it takes more work to make a valid copy of a hashtable.</span></span>

### <a name="assigning-reference-types"></a><span data-ttu-id="51ce1-373">참조 형식 할당</span><span class="sxs-lookup"><span data-stu-id="51ce1-373">Assigning reference types</span></span>

<span data-ttu-id="51ce1-374">해시 테이블이 하나 있으며 두 번째 변수에 이를 할당하면, 두 변수는 같은 해시 테이블을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-374">When you have one hashtable and assign it to a second variable, both variables point to the same hashtable.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="51ce1-375">한쪽의 값을 변경하면 다른 쪽의 값도 변경되기 때문에 두 항목이 같음을 더욱 확실하게 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-375">This highlights that they're the same because altering the values in one will also alter the values in the other.</span></span> <span data-ttu-id="51ce1-376">다른 함수에 해시 테이블을 전달할 때도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-376">This also applies when passing hashtables into other functions.</span></span> <span data-ttu-id="51ce1-377">함수가 해시 테이블을 변경한다면 원본도 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-377">If those functions make changes to that hashtable, your original is also altered.</span></span>

### <a name="shallow-copies-single-level"></a><span data-ttu-id="51ce1-378">단순 복사본, 단일 수준</span><span class="sxs-lookup"><span data-stu-id="51ce1-378">Shallow copies, single level</span></span>

<span data-ttu-id="51ce1-379">위의 예제에서처럼 간단한 해시 테이블이 있다면 `.Clone()`를 사용하여 단순 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-379">If we have a simple hashtable like our example above, we can use `.Clone()` to make a shallow copy.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

<span data-ttu-id="51ce1-380">이렇게 하면 한쪽 해시 테이블의 기본 테이블을 변경해도 다른 해시 테이블은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-380">This will allow us to make some basic changes to one that don't impact the other.</span></span>

### <a name="shallow-copies-nested"></a><span data-ttu-id="51ce1-381">단순 복사본, 중첩</span><span class="sxs-lookup"><span data-stu-id="51ce1-381">Shallow copies, nested</span></span>

<span data-ttu-id="51ce1-382">단순 복사본이라고 하는 이유는 기본 수준 속성만 복사하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-382">The reason why it's called a shallow copy is because it only copies the base level properties.</span></span> <span data-ttu-id="51ce1-383">속성 중 하나가 참조 형식(예: 다른 해시 테이블)이어도 중첩된 개체는 계속해서 서로를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-383">If one of those properties is a reference type (like another hashtable), then those nested objects will still point to each other.</span></span>

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="51ce1-384">따라서 해시 테이블을 복제했더라도 `person`에 대한 참조는 복제되지 않음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-384">So you can see that even though I cloned the hashtable, the reference to `person` wasn't cloned.</span></span> <span data-ttu-id="51ce1-385">첫 번째 해시 테이블에 연결되지 않은 두 번째 해시 테이블을 얻으려면 전체 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-385">We need to make a deep copy to truly have a second hashtable that isn't linked to the first.</span></span>

### <a name="deep-copies"></a><span data-ttu-id="51ce1-386">전체 복사본</span><span class="sxs-lookup"><span data-stu-id="51ce1-386">Deep copies</span></span>

<span data-ttu-id="51ce1-387">이 문서를 작성하는 지금 해시 테이블의 전체 복사본을 만드는(그리고 이것을 해시 테이블로 유지하는) 방법보다 좋은 방법을 알지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-387">At the time of writing this, I'm not aware of any clever ways to just make a deep copy of a hashtable (and keep it as a hashtable).</span></span> <span data-ttu-id="51ce1-388">그런 방법은 다른 누군가가 작성할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-388">That's just one of those things that someone needs to write.</span></span>
<span data-ttu-id="51ce1-389">이 방법을 이용하면 작업을 빠르게 수행하는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-389">Here is a quick method to do that.</span></span>

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

<span data-ttu-id="51ce1-390">다른 참조 형식이나 배열을 처리하지는 않지만 좋은 출발점이 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-390">It doesn't handle any other reference types or arrays, but it's a good starting point.</span></span>

## <a name="anything-else"></a><span data-ttu-id="51ce1-391">다른 내용을 알고 싶으신가요?</span><span class="sxs-lookup"><span data-stu-id="51ce1-391">Anything else?</span></span>

<span data-ttu-id="51ce1-392">지금까지 많은 내용을 빠르게 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-392">I covered a lot of ground quickly.</span></span> <span data-ttu-id="51ce1-393">이 문서를 읽을 때마다 새로운 내용을 배우거나 기존 지식이 깊어지길 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-393">My hope is that you walk away leaning something new or understanding it better every time you read this.</span></span> <span data-ttu-id="51ce1-394">이 기능의 모든 특징을 살펴보았기 때문에 지금 당장은 적용되지 않는 측면이 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-394">Because I covered the full spectrum of this feature, there are aspects that just may not apply to you right now.</span></span> <span data-ttu-id="51ce1-395">지극히 정상적인 현상이며 PowerShell을 많이 이용한다면 필연적인 일이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ce1-395">That is perfectly OK and is kind of expected depending on how much you work with PowerShell.</span></span>

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[original version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[해시 테이블]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[hashtables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[배열]: /powershell/module/microsoft.powershell.core/about/about_arrays
[arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[성능이 중요하다면 테스트하라]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[If performance matters, test it]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[스플래팅]: /powershell/module/microsoft.powershell.core/about/about_splatting
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[자동 기본값]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Automatic Defaults]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
