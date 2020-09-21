---
title: if 문 관련 세부 사항
description: 다른 많은 언어와 마찬가지로 PowerShell에는 스크립트에서 조건부로 코드를 실행하기 위한 문이 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b6bafb99bfb8ecd0152bae841e5c58d4c27ccd3e
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469755"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a><span data-ttu-id="0de7c-103">`if` 문 관련 세부 사항</span><span class="sxs-lookup"><span data-stu-id="0de7c-103">Everything you wanted to know about the `if` statement</span></span>

<span data-ttu-id="0de7c-104">다른 많은 언어와 마찬가지로 PowerShell에는 스크립트에서 조건부로 코드를 실행하기 위한 문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-104">Like many other languages, PowerShell has statements for conditionally executing code in your scripts.</span></span> <span data-ttu-id="0de7c-105">해당 문 중 하나가 [If][] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-105">One of those statements is the [If][] statement.</span></span> <span data-ttu-id="0de7c-106">오늘은 PowerShell에서 가장 기본적인 명령 중 하나를 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-106">Today we will take a deep dive into one of the most fundamental commands in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="0de7c-107">현재 문서의 [원본 버전][]은 [@KevinMarquette][]가 작성한 블로그에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="0de7c-108">PowerShell 팀은 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="0de7c-109">[PowerShellExplained.com][]에 있는 해당 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="conditional-execution"></a><span data-ttu-id="0de7c-110">조건부 실행</span><span class="sxs-lookup"><span data-stu-id="0de7c-110">Conditional execution</span></span>

<span data-ttu-id="0de7c-111">스크립트에서는 결정을 내리고 이러한 결정에 따라 다른 논리를 실행해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-111">Your scripts often need to make decisions and perform different logic based on those decisions.</span></span>
<span data-ttu-id="0de7c-112">이것은 조건부 실행을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-112">This is what I mean by conditional execution.</span></span> <span data-ttu-id="0de7c-113">평가할 문이나 값이 하나 있으면 해당 평가에 따라 코드의 다른 섹션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-113">You have one statement or value to evaluate, then execute a different section of code based on that evaluation.</span></span> <span data-ttu-id="0de7c-114">이것은 정확히 `if` 문이 수행하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-114">This is exactly what the `if` statement does.</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="0de7c-115">`if` 문</span><span class="sxs-lookup"><span data-stu-id="0de7c-115">The `if` statement</span></span>

<span data-ttu-id="0de7c-116">`if` 문의 기본 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-116">Here is a basic example of the `if` statement:</span></span>

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

<span data-ttu-id="0de7c-117">`if` 문은 가장 먼저 괄호 안의 식을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-117">The first thing the `if` statement does is evaluate the expression in parentheses.</span></span> <span data-ttu-id="0de7c-118">`$true`인 것으로 계산되면 중괄호에서 `scriptblock`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-118">If it evaluates to `$true`, then it executes the `scriptblock` in the braces.</span></span> <span data-ttu-id="0de7c-119">값이 `$false`였다면 해당 scriptblock은 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-119">If the value was `$false`, then it would skip over that scriptblock.</span></span>

<span data-ttu-id="0de7c-120">이전 예제에서는 `if` 문이 `$condition` 변수만 계산했습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-120">In the previous example, the `if` statement was just evaluating the `$condition` variable.</span></span> <span data-ttu-id="0de7c-121">`$true`였으며 scriptblock 내부에서 `Write-Output` 명령을 실행했을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-121">It was `$true` and would have executed the `Write-Output` command inside the scriptblock.</span></span>

<span data-ttu-id="0de7c-122">일부 언어에서는 `if` 문 뒤에 한 줄의 코드를 배치하여 실행할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="0de7c-122">In some languages, you can place a single line of code after the `if` statement and it gets executed.</span></span> <span data-ttu-id="0de7c-123">PowerShell에는 해당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-123">That isn't the case in PowerShell.</span></span> <span data-ttu-id="0de7c-124">제대로 작동하게 하려면 중괄호를 포함한 전체 `scriptblock`를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-124">You must provide a full `scriptblock` with braces for it to work correctly.</span></span>

## <a name="comparison-operators"></a><span data-ttu-id="0de7c-125">비교 연산자</span><span class="sxs-lookup"><span data-stu-id="0de7c-125">Comparison operators</span></span>

<span data-ttu-id="0de7c-126">`if` 문의 가장 일반적인 용도는 두 항목을 서로 비교하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-126">The most common use of the `if` statement for is comparing two items with each other.</span></span> <span data-ttu-id="0de7c-127">PowerShell에는 다양한 비교 시나리오에 대한 특수 연산자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-127">PowerShell has special operators for different comparison scenarios.</span></span> <span data-ttu-id="0de7c-128">비교 연산자를 사용하면 왼쪽에 있는 값이 오른쪽에 있는 값과 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-128">When you use a comparison operator, the value on the left-hand side is compared to the value on the right-hand side.</span></span>

### <a name="-eq-for-equality"></a><span data-ttu-id="0de7c-129">같음에 대한 -eq</span><span class="sxs-lookup"><span data-stu-id="0de7c-129">-eq for equality</span></span>

<span data-ttu-id="0de7c-130">`-eq`는 두 값이 서로 같은지 확인하기 위해 같음 검사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-130">The `-eq` does an equality check between two values to make sure they're equal to each other.</span></span>

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

<span data-ttu-id="0de7c-131">이 예제에서는 알려진 값인 `5`를 가져오고 이를 내 `$value`와 비교하여 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-131">In this example, I'm taking a known value of `5` and comparing it to my `$value` to see if they match.</span></span>

<span data-ttu-id="0de7c-132">한 가지 사용 사례는 작업을 수행하기 전에 값의 상태를 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-132">One possible use case is to check the status of a value before you take an action on it.</span></span> <span data-ttu-id="0de7c-133">`Restart-Service`를 호출하기 전에 서비스를 가져와 상태를 실행하고 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-133">You could get a service and check that the status was running before you called `Restart-Service` on it.</span></span>

<span data-ttu-id="0de7c-134">C#과 같은 다른 언어에서 같음을 위해 `==`을 사용하는 경우(예: `5 == $value`)가 많지만 PowerShell에서는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-134">It's common in other languages like C# to use `==` for equality (ex: `5 == $value`) but that doesn't work with PowerShell.</span></span> <span data-ttu-id="0de7c-135">사용자가 하는 또 다른 흔한 실수는 변수에 값을 할당하는 데만 사용해야 하는 등호(예: `5 = $value`)를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-135">Another common mistake that people make is to use the equals sign (ex: `5 = $value`) that is reserved for assigning values to variables.</span></span> <span data-ttu-id="0de7c-136">왼쪽에 알려진 값을 배치하면 상황이 더 복잡해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-136">By placing your known value on the left, it makes that mistake more awkward to make.</span></span>

<span data-ttu-id="0de7c-137">해당 연산자(및 기타 연산자)에는 몇 가지 변형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-137">This operator (and others) has a few variations.</span></span>

- <span data-ttu-id="0de7c-138">`-eq` 대/소문자를 구분하지 않는 같음</span><span class="sxs-lookup"><span data-stu-id="0de7c-138">`-eq` case-insensitive equality</span></span>
- <span data-ttu-id="0de7c-139">`-ieq` 대/소문자를 구분하지 않는 같음</span><span class="sxs-lookup"><span data-stu-id="0de7c-139">`-ieq` case-insensitive equality</span></span>
- <span data-ttu-id="0de7c-140">`-ceq` 대/소문자를 구분하는 같음</span><span class="sxs-lookup"><span data-stu-id="0de7c-140">`-ceq` case-sensitive equality</span></span>

### <a name="-ne-not-equal"></a><span data-ttu-id="0de7c-141">-ne 같지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-141">-ne not equal</span></span>

<span data-ttu-id="0de7c-142">여러 연산자에 반대인 결과를 확인하는 관련 연산자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-142">Many operators have a related operator that is checking for the opposite result.</span></span> <span data-ttu-id="0de7c-143">`-ne`는 값이 서로 같지 않음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-143">`-ne` verifies that the values don't equal each other.</span></span>

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

<span data-ttu-id="0de7c-144">이것을 사용하여 값이 `5`가 아닌 경우에만 작업이 실행되도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-144">Use this to make sure that the action only executes if the value isn't `5`.</span></span> <span data-ttu-id="0de7c-145">시작하기 전에 서비스가 실행 중인 상태에 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-145">A good use-cases where would be to check if a service was in the running state before you try to start it.</span></span>

<span data-ttu-id="0de7c-146">**변형:**</span><span class="sxs-lookup"><span data-stu-id="0de7c-146">**Variations:**</span></span>

- <span data-ttu-id="0de7c-147">`-ne` 대/소문자를 구분하지 않는 같지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-147">`-ne` case-insensitive not equal</span></span>
- <span data-ttu-id="0de7c-148">`-ine` 대/소문자를 구분하지 않는 같지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-148">`-ine` case-insensitive not equal</span></span>
- <span data-ttu-id="0de7c-149">`-cne` 대/소문자를 구분하는 같지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-149">`-cne` case-sensitive not equal</span></span>

<span data-ttu-id="0de7c-150">이것은 `-eq`의 역 변형입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-150">These are inverse variations of `-eq`.</span></span> <span data-ttu-id="0de7c-151">다른 연산자의 변형을 나열하는 경우 이러한 형식을 함께 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-151">I'll group these types together when I list variations for other operators.</span></span>

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a><span data-ttu-id="0de7c-152">초과 또는 미만을 위한 -gt -ge -lt -le</span><span class="sxs-lookup"><span data-stu-id="0de7c-152">-gt -ge -lt -le for greater than or less than</span></span>

<span data-ttu-id="0de7c-153">이러한 연산자는 값이 다른 값보다 크거나 작은지 확인하는 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-153">These operators are used when checking to see if a value is larger or smaller than another value.</span></span>
<span data-ttu-id="0de7c-154">`-gt -ge -lt -le`는 GreaterThan, GreaterThanOrEqual, LessThan 및 LessThanOrEqual을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-154">The `-gt -ge -lt -le` stand for GreaterThan, GreaterThanOrEqual, LessThan, and LessThanOrEqual.</span></span>

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

<span data-ttu-id="0de7c-155">**변형:**</span><span class="sxs-lookup"><span data-stu-id="0de7c-155">**Variations:**</span></span>

- <span data-ttu-id="0de7c-156">`-gt` 보다 큼</span><span class="sxs-lookup"><span data-stu-id="0de7c-156">`-gt` greater than</span></span>
- <span data-ttu-id="0de7c-157">`-igt` 보다 큼, 대/소문자를 구분하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-157">`-igt` greater than, case-insensitive</span></span>
- <span data-ttu-id="0de7c-158">`-cgt` 보다 큼, 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="0de7c-158">`-cgt` greater than, case-sensitive</span></span>
- <span data-ttu-id="0de7c-159">`-ge` 크거나 같음</span><span class="sxs-lookup"><span data-stu-id="0de7c-159">`-ge` greater than or equal</span></span>
- <span data-ttu-id="0de7c-160">`-ige` 크거나 같음, 대/소문자를 구분하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-160">`-ige` greater than or equal, case-insensitive</span></span>
- <span data-ttu-id="0de7c-161">`-cge` 크거나 같음, 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="0de7c-161">`-cge` greater than or equal, case-sensitive</span></span>
- <span data-ttu-id="0de7c-162">`-lt` 보다 작음</span><span class="sxs-lookup"><span data-stu-id="0de7c-162">`-lt` less than</span></span>
- <span data-ttu-id="0de7c-163">`-ilt` 보다 작음, 대/소문자를 구분하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-163">`-ilt` less than, case-insensitive</span></span>
- <span data-ttu-id="0de7c-164">`-clt` 보다 작음, 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="0de7c-164">`-clt` less than, case-sensitive</span></span>
- <span data-ttu-id="0de7c-165">`-le` 작거나 같음</span><span class="sxs-lookup"><span data-stu-id="0de7c-165">`-le` less than or equal</span></span>
- <span data-ttu-id="0de7c-166">`-ile` 작거나 같음, 대/소문자를 구분하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-166">`-ile` less than or equal, case-insensitive</span></span>
- <span data-ttu-id="0de7c-167">`-cle` 작거나 같음, 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="0de7c-167">`-cle` less than or equal, case-sensitive</span></span>

<span data-ttu-id="0de7c-168">이러한 연산자에 대/소문자를 구분하거나 구분하지 않는 옵션을 사용하는 이유는 모릅니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-168">I don't know why you would use case-sensitive and insensitive options for these operators.</span></span>

### <a name="-like-wildcard-matches"></a><span data-ttu-id="0de7c-169">-like 와일드카드 일치</span><span class="sxs-lookup"><span data-stu-id="0de7c-169">-like wildcard matches</span></span>

<span data-ttu-id="0de7c-170">PowerShell에는 고유한 와일드카드 기반 패턴 일치 구문이 있으므로 `-like` 연산자와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-170">PowerShell has its own wildcard-based pattern matching syntax and you can use it with the `-like` operator.</span></span> <span data-ttu-id="0de7c-171">이러한 와일드카드 패턴은 상당히 기본적입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-171">These wildcard patterns are fairly basic.</span></span>

- <span data-ttu-id="0de7c-172">`?` 임의의 문자 하나에 대응</span><span class="sxs-lookup"><span data-stu-id="0de7c-172">`?` matches any single character</span></span>
- <span data-ttu-id="0de7c-173">`*` 임의의 수의 문자에 대응</span><span class="sxs-lookup"><span data-stu-id="0de7c-173">`*` matches any number of characters</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

<span data-ttu-id="0de7c-174">패턴이 전체 문자열과 일치하는지 확인하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-174">It's important to point out that the pattern matches the whole string.</span></span> <span data-ttu-id="0de7c-175">문자열의 중간에 있는 항목을 일치시켜야 하는 경우 문자열의 양쪽 끝에 `*`를 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-175">If you need to match something in the middle of the string, you need to place the `*` on both ends of the string.</span></span>

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

<span data-ttu-id="0de7c-176">**변형:**</span><span class="sxs-lookup"><span data-stu-id="0de7c-176">**Variations:**</span></span>

- <span data-ttu-id="0de7c-177">`-like` 대/소문자를 구분하지 않는 와일드카드</span><span class="sxs-lookup"><span data-stu-id="0de7c-177">`-like` case-insensitive wildcard</span></span>
- <span data-ttu-id="0de7c-178">`-ilike` 대/소문자를 구분하지 않는 와일드카드</span><span class="sxs-lookup"><span data-stu-id="0de7c-178">`-ilike` case-insensitive wildcard</span></span>
- <span data-ttu-id="0de7c-179">`-clike` 대/소문자 구분 와일드카드</span><span class="sxs-lookup"><span data-stu-id="0de7c-179">`-clike` case-sensitive wildcard</span></span>
- <span data-ttu-id="0de7c-180">`-notlike` 대/소문자를 구분하지 않는 와일드카드가 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-180">`-notlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="0de7c-181">`-inotlike` 대/소문자를 구분하지 않는 와일드카드가 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-181">`-inotlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="0de7c-182">`-cnotlike` 대/소문자 구분 와일드카드가 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-182">`-cnotlike` case-sensitive wildcard not matched</span></span>

### <a name="-match-regular-expression"></a><span data-ttu-id="0de7c-183">-match 정규식</span><span class="sxs-lookup"><span data-stu-id="0de7c-183">-match regular expression</span></span>

<span data-ttu-id="0de7c-184">`-match` 연산자를 사용하면 정규식 기반 일치 항목에 대한 문자열을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-184">The `-match` operator allows you to check a string for a regular-expression-based match.</span></span> <span data-ttu-id="0de7c-185">와일드카드 패턴이 유연하지 않을 경우 연산자를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-185">Use this when the wildcard patterns aren't flexible enough for you.</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

<span data-ttu-id="0de7c-186">regex 패턴은 기본적으로 문자열의 어디에서든 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-186">A regex pattern matches anywhere in the string by default.</span></span> <span data-ttu-id="0de7c-187">따라서 다음과 같이 일치하게 하려는 substring을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-187">So you can specify a substring that you want matched like this:</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

<span data-ttu-id="0de7c-188">regex는 그 자체로 복잡한 언어이며 살펴볼 가치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-188">Regex is a complex language of its own and worth looking into.</span></span> <span data-ttu-id="0de7c-189">`-match`에 대해 자세히 설명하고 다른 문서에서 [regex를 사용하는 여러 방법][]을 다루겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-189">I talk more about `-match` and [the many ways to use regex][] in another article.</span></span>

<span data-ttu-id="0de7c-190">**변형:**</span><span class="sxs-lookup"><span data-stu-id="0de7c-190">**Variations:**</span></span>

- <span data-ttu-id="0de7c-191">`-match` 대/소문자를 구분하지 않는 regex</span><span class="sxs-lookup"><span data-stu-id="0de7c-191">`-match` case-insensitive regex</span></span>
- <span data-ttu-id="0de7c-192">`-imatch` 대/소문자를 구분하지 않는 regex</span><span class="sxs-lookup"><span data-stu-id="0de7c-192">`-imatch` case-insensitive regex</span></span>
- <span data-ttu-id="0de7c-193">`-cmatch` 대/소문자 구분 regex</span><span class="sxs-lookup"><span data-stu-id="0de7c-193">`-cmatch` case-sensitive regex</span></span>
- <span data-ttu-id="0de7c-194">`-notmatch` 대/소문자를 구분하지 않는 regex가 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-194">`-notmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="0de7c-195">`-inotmatch` 대/소문자를 구분하지 않는 regex가 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-195">`-inotmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="0de7c-196">`-cnotmatch` 대/소문자 구분 regex가 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-196">`-cnotmatch` case-sensitive regex not matched</span></span>

### <a name="-is-of-type"></a><span data-ttu-id="0de7c-197">형식의 -is</span><span class="sxs-lookup"><span data-stu-id="0de7c-197">-is of type</span></span>

<span data-ttu-id="0de7c-198">`-is` 연산자를 사용하여 값의 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-198">You can check a value's type with the `-is` operator.</span></span>

```powershell
if ( $value -is [string] )
{
    # do something
}
```

<span data-ttu-id="0de7c-199">클래스로 작업하거나 파이프라인을 통해 다양한 개체를 허용하는 경우 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-199">You may use this if you're working with classes or accepting various objects over the pipeline.</span></span> <span data-ttu-id="0de7c-200">서비스 또는 서비스 이름을 입력으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-200">You could have either a service or a service name as your input.</span></span> <span data-ttu-id="0de7c-201">그런 다음 서비스가 있는지 확인하고 이름만 있는 경우 해당 서비스를 페치합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-201">Then check to see if you have a service and fetch the service if you only have the name.</span></span>

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

<span data-ttu-id="0de7c-202">**변형:**</span><span class="sxs-lookup"><span data-stu-id="0de7c-202">**Variations:**</span></span>

- <span data-ttu-id="0de7c-203">`-is` 형식의</span><span class="sxs-lookup"><span data-stu-id="0de7c-203">`-is` of type</span></span>
- <span data-ttu-id="0de7c-204">`-isnot` 형식이 아닌</span><span class="sxs-lookup"><span data-stu-id="0de7c-204">`-isnot` not of type</span></span>

## <a name="collection-operators"></a><span data-ttu-id="0de7c-205">컬렉션 연산자</span><span class="sxs-lookup"><span data-stu-id="0de7c-205">Collection operators</span></span>

<span data-ttu-id="0de7c-206">단일 값으로 이전 연산자를 사용하는 경우 결과는 `$true` 또는 `$false`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-206">When you use the previous operators with a single value, the result is `$true` or `$false`.</span></span> <span data-ttu-id="0de7c-207">이것은 컬렉션을 사용하는 약간 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-207">This is handled slightly differently when working with a collection.</span></span> <span data-ttu-id="0de7c-208">컬렉션의 각 항목이 평가되고 연산자는 `$true`로 계산되는 모든 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-208">Each item in the collection gets evaluated and the operator returns every value that evaluates to `$true`.</span></span>

```powershell
PS> 1,2,3,4 -eq 3
3
```

<span data-ttu-id="0de7c-209">이것은 `if` 문에서 계속 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-209">This still works correctly in a `if` statement.</span></span> <span data-ttu-id="0de7c-210">따라서 연산자가 값을 반환하면 전체 문이 `$true`입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-210">So a value is returned by your operator, then the whole statement is `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

<span data-ttu-id="0de7c-211">여기에서 세부 정보에 숨겨진 작은 문제를 언급하려고 합니다. 이러한 방식으로 `-ne` 연산자를 사용하면 실수로 논리를 거꾸로 보게 될 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-211">There's one small trap hiding in the details here that I need to point out. When using the `-ne` operator this way, it's easy to mistakenly look at the logic backwards.</span></span> <span data-ttu-id="0de7c-212">컬렉션의 항목이 사용자의 값과 일치하지 않는 경우 컬렉션과 함께 `-ne`를 사용하면 `$true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-212">Using `-ne` with a collection returns `$true` if any item in the collection doesn't match your value.</span></span>

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

<span data-ttu-id="0de7c-213">영리한 기법처럼 보일 수 있지만 이 문제를 보다 효율적으로 처리하는 연산자인 `-contains` 및 `-in`이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-213">This may look like a clever trick, but we have operators `-contains` and `-in` that handle this more efficiently.</span></span> <span data-ttu-id="0de7c-214">그리고 원하는 것을 `-notcontains`가 제공할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-214">And `-notcontains` does what you expect.</span></span>

### <a name="-contains"></a><span data-ttu-id="0de7c-215">-contains</span><span class="sxs-lookup"><span data-stu-id="0de7c-215">-contains</span></span>

<span data-ttu-id="0de7c-216">`-contains` 연산자는 컬렉션에서 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-216">The `-contains` operator checks the collection for your value.</span></span> <span data-ttu-id="0de7c-217">일치 항목을 찾으면 `$true`는 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-217">As soon as it finds a match, it returns `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

<span data-ttu-id="0de7c-218">컬렉션에 값이 포함되어 있는지 여부를 확인하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-218">This is the preferred way to see if a collection contains your value.</span></span> <span data-ttu-id="0de7c-219">`Where-Object`(또는 `-eq`)를 사용하면 매번 전체 목록을 표시하고 속도가 훨씬 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-219">Using `Where-Object` (or `-eq`) walks the entire list every time and is significantly slower.</span></span>

<span data-ttu-id="0de7c-220">**변형:**</span><span class="sxs-lookup"><span data-stu-id="0de7c-220">**Variations:**</span></span>

- <span data-ttu-id="0de7c-221">`-contains` 대/소문자를 구분하지 않는 일치</span><span class="sxs-lookup"><span data-stu-id="0de7c-221">`-contains` case-insensitive match</span></span>
- <span data-ttu-id="0de7c-222">`-icontains` 대/소문자를 구분하지 않는 일치</span><span class="sxs-lookup"><span data-stu-id="0de7c-222">`-icontains` case-insensitive match</span></span>
- <span data-ttu-id="0de7c-223">`-ccontains` 대/소문자를 구분하고 일치</span><span class="sxs-lookup"><span data-stu-id="0de7c-223">`-ccontains` case-sensitive match</span></span>
- <span data-ttu-id="0de7c-224">`-notcontains` 대/소문자를 구분하지 않고 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-224">`-notcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="0de7c-225">`-inotcontains` 대/소문자를 구분하지 않고 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-225">`-inotcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="0de7c-226">`-cnotcontains` 대/소문자를 구분하고 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-226">`-cnotcontains` case-sensitive not matched</span></span>

### <a name="-in"></a><span data-ttu-id="0de7c-227">-in</span><span class="sxs-lookup"><span data-stu-id="0de7c-227">-in</span></span>

<span data-ttu-id="0de7c-228">`-in` 연산자는 컬렉션이 오른쪽에 있는 점만 제외하면 `-contains` 연산자와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-228">The `-in` operator is just like the `-contains` operator except the collection is on the right-hand side.</span></span>

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

<span data-ttu-id="0de7c-229">**변형:**</span><span class="sxs-lookup"><span data-stu-id="0de7c-229">**Variations:**</span></span>

- <span data-ttu-id="0de7c-230">`-in` 대/소문자를 구분하지 않는 일치</span><span class="sxs-lookup"><span data-stu-id="0de7c-230">`-in` case-insensitive match</span></span>
- <span data-ttu-id="0de7c-231">`-iin` 대/소문자를 구분하지 않는 일치</span><span class="sxs-lookup"><span data-stu-id="0de7c-231">`-iin` case-insensitive match</span></span>
- <span data-ttu-id="0de7c-232">`-cin` 대/소문자를 구분하고 일치</span><span class="sxs-lookup"><span data-stu-id="0de7c-232">`-cin` case-sensitive match</span></span>
- <span data-ttu-id="0de7c-233">`-notin` 대/소문자를 구분하지 않고 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-233">`-notin` case-insensitive not matched</span></span>
- <span data-ttu-id="0de7c-234">`-inotin` 대/소문자를 구분하지 않고 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-234">`-inotin` case-insensitive not matched</span></span>
- <span data-ttu-id="0de7c-235">`-cnotin` 대/소문자를 구분하고 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="0de7c-235">`-cnotin` case-sensitive not matched</span></span>

## <a name="logical-operators"></a><span data-ttu-id="0de7c-236">논리 연산자</span><span class="sxs-lookup"><span data-stu-id="0de7c-236">Logical operators</span></span>

<span data-ttu-id="0de7c-237">논리 연산자는 다른 식을 반전하거나 결합하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-237">Logical operators are used to invert or combine other expressions.</span></span>

### <a name="-not"></a><span data-ttu-id="0de7c-238">-not</span><span class="sxs-lookup"><span data-stu-id="0de7c-238">-not</span></span>

<span data-ttu-id="0de7c-239">`-not` 연산자는 식을 `$false`에서 `$true` 또는 `$true`에서 `$false`로 대칭 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-239">The `-not` operator flips an expression from `$false` to `$true` or from `$true` to `$false`.</span></span> <span data-ttu-id="0de7c-240">다음은 `Test-Path` `$false`일 때 작업을 수행하려는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-240">Here is an example where we want to perform an action when `Test-Path` is `$false`.</span></span>

```powershell
if ( -not ( Test-Path -Path $path ) )
```

<span data-ttu-id="0de7c-241">설명한 대부분의 연산자에는 `-not` 연산자를 사용하지 않아도 되는 변형이 있지만</span><span class="sxs-lookup"><span data-stu-id="0de7c-241">Most of the operators we talked about do have a variation where you do not need to use the `-not` operator.</span></span> <span data-ttu-id="0de7c-242">여전히 유용한 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-242">But there are still times it is useful.</span></span>

### <a name="-operator"></a><span data-ttu-id="0de7c-243">!</span><span class="sxs-lookup"><span data-stu-id="0de7c-243">!</span></span> <span data-ttu-id="0de7c-244">operator</span><span class="sxs-lookup"><span data-stu-id="0de7c-244">operator</span></span>

<span data-ttu-id="0de7c-245">`!`를 `-not`의 별칭으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-245">You can use `!` as an alias for `-not`.</span></span>

```powershell
if ( -not $value ){}
if ( !$value ){}
```

<span data-ttu-id="0de7c-246">C#과 같은 다른 언어를 사용하는 사람들이 `!`를 더 많이 사용하는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-246">You may see `!` used more by people that come from another languages like C#.</span></span> <span data-ttu-id="0de7c-247">스크립트를 빨리 살펴볼 때 확인하기가 어려워서 입력하는 편을 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-247">I prefer to type it out because I find it hard to see when quickly looking at my scripts.</span></span>

### <a name="-and"></a><span data-ttu-id="0de7c-248">-and</span><span class="sxs-lookup"><span data-stu-id="0de7c-248">-and</span></span>

<span data-ttu-id="0de7c-249">식을 `-and` 연산자와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-249">You can combine expressions with the `-and` operator.</span></span> <span data-ttu-id="0de7c-250">이 작업을 수행하는 경우 전체 식이 `$true`가 되려면 양쪽 모두 `$true`여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-250">When you do that, both sides need to be `$true` for the whole expression to be `$true`.</span></span>

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

<span data-ttu-id="0de7c-251">이 예제에서는 `$age`가 왼쪽에서는 13세 이상 오른쪽에서는 55세 미만이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-251">In that example, `$age` must be 13 or older for the left side and less than 55 for the right side.</span></span> <span data-ttu-id="0de7c-252">이 예제에서는 더 명확하게 하기 위해 괄호를 추가했지만 식이 단순하다면 괄호는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-252">I added extra parentheses to make it clearer in that example but they're optional as long as the expression is simple.</span></span> <span data-ttu-id="0de7c-253">다음은 괄호를 제외하고는 동일한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-253">Here is the same example without them.</span></span>

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

<span data-ttu-id="0de7c-254">평가는 왼쪽에서 오른쪽으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-254">Evaluation happens from left to right.</span></span> <span data-ttu-id="0de7c-255">첫 번째 항목이 `$false`로 평가되면 일찍 종료되고 비교가 올바르게 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-255">If the first item evaluates to `$false`, it exits early and doesn't perform the right comparison.</span></span> <span data-ttu-id="0de7c-256">이러한 방법은 사용하기 전에 값이 존재하는지 확인해야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-256">This is handy when you need to make sure a value exists before you use it.</span></span> <span data-ttu-id="0de7c-257">예를 들어 `$null` 경로를 지정하는 경우 `Test-Path`가 오류를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-257">For example, `Test-Path` throws an error if you give it a `$null` path.</span></span>

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a><span data-ttu-id="0de7c-258">-or</span><span class="sxs-lookup"><span data-stu-id="0de7c-258">-or</span></span>

<span data-ttu-id="0de7c-259">`-or`을 사용하여 두 식을 지정하고 둘 중 하나가 `$true`인 경우 `$true`를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-259">The `-or` allows for you to specify two expressions and returns `$true` if either one of them is `$true`.</span></span>

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

<span data-ttu-id="0de7c-260">`-and` 연산자와 마찬가지로 평가는 왼쪽에서 오른쪽으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-260">Just like with the `-and` operator, the evaluation happens from left to right.</span></span> <span data-ttu-id="0de7c-261">첫 번째 부분이 `$true`인 경우 전체 문이 `$true`가 되며 식의 나머지 부분을 처리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-261">Except that if the first part is `$true`, then the whole statement is `$true` and it doesn't process the rest of the expression.</span></span>

<span data-ttu-id="0de7c-262">또한 이러한 연산자에서 구문이 작동하는 방식에 주목하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-262">Also make note of how the syntax works for these operators.</span></span> <span data-ttu-id="0de7c-263">두 개의 별도 식이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-263">You need two separate expressions.</span></span> <span data-ttu-id="0de7c-264">실수를 인식하지 못한 채 이러한 `$value -eq 5 -or 6`과 같은 작업을 수행하려는 사용자를 본 적이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-264">I have seen users try to do something like this `$value -eq 5 -or 6` without realizing their mistake.</span></span>

### <a name="-xor-exclusive-or"></a><span data-ttu-id="0de7c-265">-xor 배타적 OR</span><span class="sxs-lookup"><span data-stu-id="0de7c-265">-xor exclusive or</span></span>

<span data-ttu-id="0de7c-266">이것은 약간 특이한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-266">This one is a little unusual.</span></span> <span data-ttu-id="0de7c-267">`-xor`은 식 하나만 `$true`인지 계산하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-267">`-xor` allows only one expression to evaluate to `$true`.</span></span> <span data-ttu-id="0de7c-268">따라서 두 항목 모두 `$false`거나 두 항목 모두 `$true`인 경우 전체 식이 `$false`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-268">So if both items are `$false` or both items are `$true`, then the whole expression is `$false`.</span></span> <span data-ttu-id="0de7c-269">이것을 살펴보는 또 다른 방법은 식의 결과가 다른 경우에만 식이 `$true`라는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-269">Another way to look at this is the expression is only `$true` when the results of the expression are different.</span></span>

<span data-ttu-id="0de7c-270">사용자가 해당 논리 연산자를 사용하는 경우는 거의 없으며 이것을 사용하는 이유에 대해 설명하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-270">It's rare that anyone would ever use this logical operator and I can't think up a good example as to why I would ever use it.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="0de7c-271">비트 연산자</span><span class="sxs-lookup"><span data-stu-id="0de7c-271">Bitwise operators</span></span>

<span data-ttu-id="0de7c-272">비트 연산자는 값 내부의 비트에 대해 계산하고 그 결과로 새 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-272">Bitwise operators perform calculations on the bits within the values and produce a new value as the result.</span></span> <span data-ttu-id="0de7c-273">[비트 연산자][]에 대한 교육은 본 문서의 범위를 벗어나며 여기에서는 그 목록만을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-273">Teaching [bitwise operators][] is beyond the scope of this article, but here is the list the them.</span></span>

- <span data-ttu-id="0de7c-274">`-band` 이진 AND</span><span class="sxs-lookup"><span data-stu-id="0de7c-274">`-band` binary AND</span></span>
- <span data-ttu-id="0de7c-275">`-bor` 이진 OR</span><span class="sxs-lookup"><span data-stu-id="0de7c-275">`-bor` binary OR</span></span>
- <span data-ttu-id="0de7c-276">`-bxor` 이진 배타적 OR</span><span class="sxs-lookup"><span data-stu-id="0de7c-276">`-bxor` binary exclusive OR</span></span>
- <span data-ttu-id="0de7c-277">`-bnot` 이진 NOT</span><span class="sxs-lookup"><span data-stu-id="0de7c-277">`-bnot` binary NOT</span></span>
- <span data-ttu-id="0de7c-278">`-shl` 왼쪽으로 이동</span><span class="sxs-lookup"><span data-stu-id="0de7c-278">`-shl` shift left</span></span>
- <span data-ttu-id="0de7c-279">`-shr` 오른쪽으로 이동</span><span class="sxs-lookup"><span data-stu-id="0de7c-279">`-shr` shift right</span></span>

## <a name="powershell-expressions"></a><span data-ttu-id="0de7c-280">PowerShell 식</span><span class="sxs-lookup"><span data-stu-id="0de7c-280">PowerShell expressions</span></span>

<span data-ttu-id="0de7c-281">조건문 내부에서 일반 PowerShell을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-281">We can use normal PowerShell inside the condition statement.</span></span>

```powershell
if ( Test-Path -Path $Path )
```

<span data-ttu-id="0de7c-282">이것이 실행될 때 `Test-Path`는 `$true` 또는 `$false`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-282">`Test-Path` returns `$true` or `$false` when it executes.</span></span> <span data-ttu-id="0de7c-283">이것은 다른 값을 반환하는 명령에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-283">This also applies to commands that return other values.</span></span>

```powershell
if ( Get-Process Notepad* )
```

<span data-ttu-id="0de7c-284">반환된 프로세스가 있는 경우 `$true`로 계산하고 아무것도 없는 경우 `$false`로 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-284">It evaluates to `$true` if there's a returned process and `$false` if there'sn'thing.</span></span> <span data-ttu-id="0de7c-285">파이프라인 식 또는 다음과 같은 기타 PowerShell 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-285">It's perfectly valid to use pipeline expressions or other PowerShell statements like this:</span></span>

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

<span data-ttu-id="0de7c-286">이러한 식은 `-and` 및 `-or` 연산자를 사용하여 서로 결합할 수 있지만 하위 식으로 구분하려면 괄호를 사용해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-286">These expressions can be combined with each other with the `-and` and `-or` operators, but you may have to use parenthesis to break them into subexpressions.</span></span>

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a><span data-ttu-id="0de7c-287">$null 확인</span><span class="sxs-lookup"><span data-stu-id="0de7c-287">Checking for $null</span></span>

<span data-ttu-id="0de7c-288">`if` 문에서는 결과가 없거나 `$null` 값이 `$false`로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-288">Having a no result or a `$null` value evaluates to `$false` in the `if` statement.</span></span> <span data-ttu-id="0de7c-289">특히 `$null`을 확인하는 경우 `$null`을 왼쪽에 배치하는 것이 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-289">When checking specifically for `$null`, it's a best practice to place the `$null` on the left-hand side.</span></span>

```powershell
if ( $null -eq $value )
```

<span data-ttu-id="0de7c-290">PowerShell에서 `$null` 값을 처리하는 경우 신경 써야 할 사항이 매우 많습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-290">There are quite a few nuances when dealing with `$null` values in PowerShell.</span></span> <span data-ttu-id="0de7c-291">좀 더 자세히 알아보려면 [$null 관련 세부 사항][] 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-291">If you're interested in diving deeper, I have an article about [everything you wanted to know about $null][].</span></span>

### <a name="variable-assignment"></a><span data-ttu-id="0de7c-292">변수 할당</span><span class="sxs-lookup"><span data-stu-id="0de7c-292">Variable assignment</span></span>

<span data-ttu-id="0de7c-293">[Prasoon Karunan V][]가 알려주기 전까지 변수 할당 항목을 추가하는 것을 잊어버릴 뻔했습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-293">I almost forgot to add this one until [Prasoon Karunan V][] reminded me of it.</span></span>

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

<span data-ttu-id="0de7c-294">일반적으로 변수에 값을 할당하는 경우 값이 파이프라인 또는 콘솔로 전달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-294">Normally when you assign a value to a variable, the value isn't passed onto the pipeline or console.</span></span> <span data-ttu-id="0de7c-295">하위 식에서 변수를 할당하는 경우에는 파이프라인으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-295">When you do a variable assignment in a sub expression, it does get passed on to the pipeline.</span></span>

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

<span data-ttu-id="0de7c-296">`$first` 할당에 출력이 없고 `$second` 할당에는 있는 경우에는 어떻게 되는지 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-296">See how the `$first` assignment has no output and the `$second` assignment does?</span></span> <span data-ttu-id="0de7c-297">`if` 문에서 할당을 완료한 경우 위의 `$second` 할당과 마찬가지로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-297">When an assignment is done in an `if` statement, it executes just like the `$second` assignment above.</span></span> <span data-ttu-id="0de7c-298">다음은 변수 할당을 사용하는 방법에 대한 명확한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-298">Here is a clean example on how you could use it:</span></span>

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

<span data-ttu-id="0de7c-299">`$process`에 값이 할당되면 문이 `$true`가 되고 `$process`가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-299">If `$process` gets assigned a value, then the statement is `$true` and `$process` gets stopped.</span></span>

<span data-ttu-id="0de7c-300">이것은 같음 검사가 아니므로 `-eq`와 혼동하지 않도록 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-300">Make sure you don't confuse this with `-eq` because this isn't an equality check.</span></span> <span data-ttu-id="0de7c-301">이것은 더 모호한 기능이며 대부분의 사람들은 작업을 이러한 방식으로 인식하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-301">This is a more obscure feature that most people don't realize works this way.</span></span>

## <a name="alternate-execution-path"></a><span data-ttu-id="0de7c-302">대체 실행 경로</span><span class="sxs-lookup"><span data-stu-id="0de7c-302">Alternate execution path</span></span>

<span data-ttu-id="0de7c-303">`if` 문을 사용하면 문이 `$true`가 되는 경우뿐만 아니라 `$false`가 되는 경우에도 동작을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-303">The `if` statement allows you to specify an action for not only when the statement is `$true`, but also for when it's `$false`.</span></span> <span data-ttu-id="0de7c-304">여기에서 `else` 문이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-304">This is where the `else` statement comes into play.</span></span>

### <a name="else"></a><span data-ttu-id="0de7c-305">else</span><span class="sxs-lookup"><span data-stu-id="0de7c-305">else</span></span>

<span data-ttu-id="0de7c-306">`else` 문은 항상 `if` 문의 마지막 부분에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-306">The `else` statement is always the last part of the `if` statement when used.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

<span data-ttu-id="0de7c-307">이 예제에서는 이것이 파일인지 확인하기 위해 `$path`를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-307">In this example, we check the `$path` to make sure it's a file.</span></span> <span data-ttu-id="0de7c-308">파일을 찾았으면 해당 파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-308">If we find the file, we move it.</span></span> <span data-ttu-id="0de7c-309">그러지 않은 경우 경고를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-309">If not, we write a warning.</span></span> <span data-ttu-id="0de7c-310">이러한 분기 논리 형식은 매우 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-310">This type of branching logic is very common.</span></span>

### <a name="nested-if"></a><span data-ttu-id="0de7c-311">중첩된 If</span><span class="sxs-lookup"><span data-stu-id="0de7c-311">Nested if</span></span>

<span data-ttu-id="0de7c-312">`if` 및 `else` 문은 스크립트 블록을 사용하므로 기타 `if` 문을 포함한 모든 PowerShell 명령을 내부에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-312">The `if` and `else` statements take a script block, so we can place any PowerShell command inside them, including another `if` statement.</span></span> <span data-ttu-id="0de7c-313">이렇게 하면 훨씬 더 복잡한 논리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-313">This allows you to make use of much more complicated logic.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

<span data-ttu-id="0de7c-314">이 예제에서는 행복 경로를 먼저 테스트한 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-314">In this example, we test the happy path first and then take action on it.</span></span> <span data-ttu-id="0de7c-315">해당 작업이 실패한 경우 다른 검사를 수행하고 사용자에게 보다 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-315">If that fails, we do another check and to provide more detailed information to the user.</span></span>

### <a name="elseif"></a><span data-ttu-id="0de7c-316">Elseif</span><span class="sxs-lookup"><span data-stu-id="0de7c-316">elseif</span></span>

<span data-ttu-id="0de7c-317">단일 조건부 검사만 있는 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-317">We aren't limited to just a single conditional check.</span></span> <span data-ttu-id="0de7c-318">`elseif` 문을 사용하여 `if` 및 `else` 문을 중첩하는 대신 함께 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-318">We can chain `if` and `else` statements together instead of nesting them by using the `elseif` statement.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

<span data-ttu-id="0de7c-319">실행은 위쪽에서 아래쪽으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-319">The execution happens from the top to the bottom.</span></span> <span data-ttu-id="0de7c-320">위에 있는 `if` 문이 먼저 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-320">The top `if` statement is evaluated first.</span></span> <span data-ttu-id="0de7c-321">이것이 `$false`인 경우 목록에서 다음 `elseif` 또는 `else`로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-321">If that is `$false`, then it moves down to the next `elseif` or `else` in the list.</span></span> <span data-ttu-id="0de7c-322">마지막 `else`는 다른 것들이 `$true`를 반환하지 않는 경우 수행하는 기본 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-322">That last `else` is the default action to take if none of the others return `$true`.</span></span>

### <a name="switch"></a><span data-ttu-id="0de7c-323">스위치</span><span class="sxs-lookup"><span data-stu-id="0de7c-323">switch</span></span>

<span data-ttu-id="0de7c-324">이제 `switch` 문에 대해 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-324">At this point, I need to mention the `switch` statement.</span></span> <span data-ttu-id="0de7c-325">이것은 값을 사용하여 여러 가지 비교를 수행하는 대체 구문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-325">It provides an alternate syntax for doing multiple comparisons with a value.</span></span> <span data-ttu-id="0de7c-326">`switch`를 사용하면 식을 지정하고 결과를 여러 다른 값과 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-326">With the `switch`, you specify an expression and that result gets compared with several different values.</span></span> <span data-ttu-id="0de7c-327">이러한 값 중 하나가 일치하면 일치 코드 블록이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-327">If one of those values match, the matching code block is executed.</span></span> <span data-ttu-id="0de7c-328">다음 예제를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-328">Take a look at this example:</span></span>

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

<span data-ttu-id="0de7c-329">`$itemType`과 일치할 수 있는 값은 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-329">There three possible values that can match the `$itemType`.</span></span> <span data-ttu-id="0de7c-330">여기에서는 `Role`과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-330">In this case, it matches with `Role`.</span></span> <span data-ttu-id="0de7c-331">간단한 예제를 사용하여 `switch` 연산자를 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-331">I used a simple example just to give you some exposure to the `switch` operator.</span></span> <span data-ttu-id="0de7c-332">[Switch 문 관련 설명][]에 대한 자세한 내용은 다른 문서에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-332">I talk more about [everything you ever wanted to know about the switch statement][] in another article.</span></span>

## <a name="pipeline"></a><span data-ttu-id="0de7c-333">파이프라인</span><span class="sxs-lookup"><span data-stu-id="0de7c-333">Pipeline</span></span>

<span data-ttu-id="0de7c-334">파이프라인은 PowerShell의 고유하고 중요한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-334">The pipeline is a unique and important feature of PowerShell.</span></span> <span data-ttu-id="0de7c-335">제거되지 않은 값 또는 변수에 할당되지 않은 값은 파이프라인에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-335">Any value that isn't suppressed or assigned to a variable gets placed in the pipeline.</span></span> <span data-ttu-id="0de7c-336">`if`를 사용하면 파이프라인을 이용할 수 있습니다. 이 이용 방식이 항상 명확하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-336">The `if` provides us a way to take advantage of the pipeline in a way that isn't always obvious.</span></span>

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

<span data-ttu-id="0de7c-337">각 스크립트 블록은 명령의 결과 또는 값을 파이프라인에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-337">Each script block is placing the results the commands or the value into the pipeline.</span></span> <span data-ttu-id="0de7c-338">그런 다음, `if` 문의 결과를 `$discount` 변수에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-338">Then we assign the result of the `if` statement to the `$discount` variable.</span></span> <span data-ttu-id="0de7c-339">이 예제에서는 각 scriptblock에서 직접 `$discount` 변수에 해당 값을 간편하게 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-339">That example could have just as easily assigned those values to the `$discount` variable directly in each scriptblock.</span></span> <span data-ttu-id="0de7c-340">이것을 `if` 문에 자주 사용한다고 말할 수 없지만 최근에 사용한 적이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-340">I can't say that I use this with the `if` statement often, but I do have an example where I used this recently.</span></span>

### <a name="array-inline"></a><span data-ttu-id="0de7c-341">배열 인라인</span><span class="sxs-lookup"><span data-stu-id="0de7c-341">Array inline</span></span>

<span data-ttu-id="0de7c-342">여러 명령줄 인수를 사용하여 실행 파일을 시작하는 [Invoke-SnowSql][]이라는 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-342">I have a function called [Invoke-SnowSql][] that launches an executable with several command-line arguments.</span></span> <span data-ttu-id="0de7c-343">다음은 인수 배열을 빌드하는 해당 함수의 클립입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-343">Here is a clip from that function where I build the array of arguments.</span></span>

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

<span data-ttu-id="0de7c-344">`$Debug` 및 `$Path` 변수는 최종 사용자가 제공하는 함수에 대한 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-344">The `$Debug` and `$Path` variables are parameters on the function that are provided by the end user.</span></span>
<span data-ttu-id="0de7c-345">배열의 초기화 내부에서 해당 변수를 인라인으로 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-345">I evaluate them inline inside the initialization of my array.</span></span> <span data-ttu-id="0de7c-346">`$Debug`가 true면 `$snowSqlParam`에 해당하는 값이 올바른 위치가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-346">If `$Debug` is true, then those values fall into the `$snowSqlParam` in the correct place.</span></span> <span data-ttu-id="0de7c-347">`$Path` 변수에 대해서도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-347">Same holds true for the `$Path` variable.</span></span>

## <a name="simplify-complex-operations"></a><span data-ttu-id="0de7c-348">복잡한 작업의 간소화</span><span class="sxs-lookup"><span data-stu-id="0de7c-348">Simplify complex operations</span></span>

<span data-ttu-id="0de7c-349">확인할 비교 사항이 너무 많고 `If` 문이 화면 오른쪽에서 멀리 스크롤되는 상황이 발생하는 것은 피하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-349">It's inevitable that you run into a situation that has way too many comparisons to check and your `If` statement scrolls way off the right side of the screen.</span></span>

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

<span data-ttu-id="0de7c-350">이러한 작업은 읽기 어려울 수 있으며 실수하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-350">They can be hard to read and that make you more prone to make mistakes.</span></span> <span data-ttu-id="0de7c-351">이러한 경우 몇 가지 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-351">There are a few things we can do about that.</span></span>

### <a name="line-continuation"></a><span data-ttu-id="0de7c-352">줄 연속</span><span class="sxs-lookup"><span data-stu-id="0de7c-352">Line continuation</span></span>

<span data-ttu-id="0de7c-353">PowerShell에는 명령을 다음 줄로 래핑할 수 있는 몇 가지 연산자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-353">There some operators in PowerShell that let you wrap you command to the next line.</span></span> <span data-ttu-id="0de7c-354">논리 연산자 `-and` 및 `-or`는 식을 여러 줄로 구분하려는 경우에 유용한 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-354">The logical operators `-and` and `-or` are good operators to use if you want to break your expression into multiple lines.</span></span>

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

<span data-ttu-id="0de7c-355">여전히 많은 일이 벌어지고 있지만 각 부분을 별도의 줄에 배치하면 큰 차이가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-355">There's still a lot going on there, but placing each piece on its own line makes a big difference.</span></span>
<span data-ttu-id="0de7c-356">세 개 이상의 비교를 하거나 논리를 읽기 위해 오른쪽으로 스크롤해야 하는 경우 일반적으로 이 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-356">I generally use this when I get more than two comparisons or if I have to scroll to the right to read any of the logic.</span></span>

### <a name="pre-calculating-results"></a><span data-ttu-id="0de7c-357">결과 미리 계산</span><span class="sxs-lookup"><span data-stu-id="0de7c-357">Pre-calculating results</span></span>

<span data-ttu-id="0de7c-358">`if` 문에서 해당 문을 분리하고 결과만 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-358">We can take that statement out of the `if` statement and only check the result.</span></span>

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

<span data-ttu-id="0de7c-359">이전 예제보다 훨씬 더 깔끔해 보일 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-359">This just feels much cleaner than the previous example.</span></span> <span data-ttu-id="0de7c-360">또한 실제로 검사하려는 대상을 설명하는 변수 이름을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-360">You also are given an opportunity to use a variable name that explains what it's that you're really checking.</span></span> <span data-ttu-id="0de7c-361">이는 또한 불필요한 주석을 줄이는 자체 문서화 코드의 예제이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-361">This is also and example of self-documenting code that saves unnecessary comments.</span></span>

### <a name="multiple-if-statements"></a><span data-ttu-id="0de7c-362">여러 If 문</span><span class="sxs-lookup"><span data-stu-id="0de7c-362">Multiple if statements</span></span>

<span data-ttu-id="0de7c-363">여러 If 문을 여러 문으로 구분하고 한 번에 하나씩 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-363">We can break this up into multiple statements and check them one at a time.</span></span> <span data-ttu-id="0de7c-364">이때 플래그 또는 추적 변수를 사용하여 결과를 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-364">In this case, we use a flag or a tracking variable to combine the results.</span></span>

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

<span data-ttu-id="0de7c-365">플래그 논리가 제대로 작동하도록 논리를 반전해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-365">I did have to invert the logic to make the flag logic work correctly.</span></span> <span data-ttu-id="0de7c-366">각 평가는 개별 `if` 문입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-366">Each evaluation is an individual `if` statement.</span></span> <span data-ttu-id="0de7c-367">디버깅하는 경우 이를 통해 논리에서 수행하는 작업을 정확하게 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-367">The advantage of this is that when you're debugging, you can tell exactly what the logic is doing.</span></span> <span data-ttu-id="0de7c-368">또한 훨씬 더 자세한 정보를 추가할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-368">I was able to add much better verbosity at the same time.</span></span>

<span data-ttu-id="0de7c-369">분명한 단점은 더 많은 코드를 작성해야 한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-369">The obvious downside is that it's so much more code to write.</span></span> <span data-ttu-id="0de7c-370">코드는 한 줄의 논리를 사용하여 25개 이상의 줄로 확대해야 하므로 훨씬 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-370">The code is more complex to look at as it takes a single line of logic and explodes it into 25 or more lines.</span></span>

### <a name="using-functions"></a><span data-ttu-id="0de7c-371">함수 사용</span><span class="sxs-lookup"><span data-stu-id="0de7c-371">Using functions</span></span>

<span data-ttu-id="0de7c-372">모든 유효성 검사 논리를 함수로 이동할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-372">We can also move all that validation logic into a function.</span></span> <span data-ttu-id="0de7c-373">얼마나 깔끔한지 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-373">Look at how clean this looks at a glance.</span></span>

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

<span data-ttu-id="0de7c-374">유효성 검사를 실행하는 함수를 만들어야 하지만 이를 통해 코드를 훨씬 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-374">You still have to create the function to do the validation, but it makes this code much easier to work with.</span></span> <span data-ttu-id="0de7c-375">해당 코드를 더 쉽게 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-375">It makes this code easier to test.</span></span> <span data-ttu-id="0de7c-376">테스트에서 `Test-ADDriveConfiguration`에 대한 호출을 모방할 수 있으며 해당 함수에 대해서는 두 가지 테스트만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-376">In your tests, you can mock the call to `Test-ADDriveConfiguration` and you only need two tests for this function.</span></span> <span data-ttu-id="0de7c-377">하나는 `$true`를 반환하는 것이고 다른 하나는 `$false`를 반환하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-377">One where it returns `$true` and one where it returns `$false`.</span></span> <span data-ttu-id="0de7c-378">크기가 작아서 다른 함수를 테스트하는 것은 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-378">Testing the other function is simpler because it's so small.</span></span>

<span data-ttu-id="0de7c-379">해당 함수의 본문은 아직 시작할 때의 한 줄이거나 지난 섹션에서 사용한 확대된 논리일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-379">The body of that function could still be that one-liner we started with or the exploded logic that we used in the last section.</span></span> <span data-ttu-id="0de7c-380">이 작업은 두 시나리오에서 모두 잘 작동하며 나중에 구현을 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-380">This works well for both scenarios and allows you to easily change that implementation later.</span></span>

## <a name="error-handling"></a><span data-ttu-id="0de7c-381">오류 처리</span><span class="sxs-lookup"><span data-stu-id="0de7c-381">Error handling</span></span>

<span data-ttu-id="0de7c-382">`if` 문의 한 가지 중요한 사용은 오류가 발생하기 전에 오류 조건을 검사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-382">One important use of the `if` statement is to check for error conditions before you run into errors.</span></span> <span data-ttu-id="0de7c-383">폴더를 만들기 전에 폴더가 이미 존재하는지 확인하는 것은 한 가지 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-383">A good example is to check if a folder already exists before you try to create it.</span></span>

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

<span data-ttu-id="0de7c-384">예외가 발생할 것이라고 예상되면 그것은 사실 예외가 아니라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-384">I like to say that if you expect an exception to happen, then it's not really an exception.</span></span> <span data-ttu-id="0de7c-385">그러므로 값을 확인하고 가능한 경우 조건의 유효성을 검사하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-385">So check your values and validate your conditions where you can.</span></span>

<span data-ttu-id="0de7c-386">실제 예외 처리에 대해 좀 더 자세히 알아보려면 [Everything you ever wanted to know about exceptions(예외 관련 세부 사항)][]에 대한 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0de7c-386">If you want to dive a little more into actual exception handling, I have an article on [everything you ever wanted to know about exceptions][].</span></span>

## <a name="final-words"></a><span data-ttu-id="0de7c-387">맺음말</span><span class="sxs-lookup"><span data-stu-id="0de7c-387">Final words</span></span>

<span data-ttu-id="0de7c-388">`if` 문은 간단한 문이며 PowerShell의 중요한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-388">The `if` statement is such a simple statement but is a fundamental piece of PowerShell.</span></span> <span data-ttu-id="0de7c-389">작성하는 거의 모든 스크립트에서 이 문을 여러 번 사용하게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-389">You will find yourself using this multiple times in almost every script you write.</span></span> <span data-ttu-id="0de7c-390">이전보다 더 잘 이해하게 되셨길 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="0de7c-390">I hope you have a better understanding than you had before.</span></span>

<!-- link references -->
[원본 버전]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[original version]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[비트 연산자]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[bitwise operators]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[regex를 사용하는 여러 방법]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[the many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[Everything you ever wanted to know about exceptions(예외 관련 세부 사항)]: everything-about-exceptions.md
[everything you ever wanted to know about exceptions]: everything-about-exceptions.md
[$null 관련 세부 사항]: everything-about-null.md
[everything you wanted to know about $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Switch 문 관련 설명]: everything-about-switch.md
[everything you ever wanted to know about the switch statement]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
