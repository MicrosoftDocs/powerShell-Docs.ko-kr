---
title: $null 관련 세부 사항
description: PowerShell $null은 대개 단순해 보이지만 신경 써야 할 세부 사항이 많이 있습니다. 예기치 않게 Null 값을 실행하는 경우 발생하는 상황을 알아보기 위해 $null에 대해 자세히 살펴보겠습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149476"
---
# <a name="everything-you-wanted-to-know-about-null"></a><span data-ttu-id="d9273-104">$null 관련 세부 사항</span><span class="sxs-lookup"><span data-stu-id="d9273-104">Everything you wanted to know about $null</span></span>

<span data-ttu-id="d9273-105">PowerShell `$null`은 대개 단순해 보이지만 신경 써야 할 세부 사항이 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-105">The PowerShell `$null` often appears to be simple but it has a lot of nuances.</span></span> <span data-ttu-id="d9273-106">예기치 않게 `$null` 값을 실행하는 경우 발생하는 상황을 알아보기 위해 `$null`을 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-106">Let's take a close look at `$null` so you know what happens when you unexpectedly run into a `$null` value.</span></span>

> [!NOTE]
> <span data-ttu-id="d9273-107">현재 문서의 [원본 버전][]은 [@KevinMarquette][]가 작성한 블로그에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="d9273-108">PowerShell 팀은 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="d9273-109">[PowerShellExplained.com][]에 있는 해당 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d9273-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-null"></a><span data-ttu-id="d9273-110">NULL이란?</span><span class="sxs-lookup"><span data-stu-id="d9273-110">What is NULL?</span></span>

<span data-ttu-id="d9273-111">NULL은 알려지지 않았거나 비어 있는 값으로 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-111">You can think of NULL as an unknown or empty value.</span></span> <span data-ttu-id="d9273-112">값이나 개체가 할당되기 전의 변수는 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-112">A variable is NULL until you assign a value or an object to it.</span></span> <span data-ttu-id="d9273-113">이는 특정한 값이 필요한데 해당 값이 NULL인 경우 오류를 생성하는 일부 명령이 있으므로 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-113">This can be important because there are some commands that require a value and generate errors if the value is NULL.</span></span>

### <a name="powershell-null"></a><span data-ttu-id="d9273-114">PowerShell $null</span><span class="sxs-lookup"><span data-stu-id="d9273-114">PowerShell $null</span></span>

<span data-ttu-id="d9273-115">`$null`은 NULL을 나타내는 데 사용되는 PowerShell의 자동 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-115">`$null` is an automatic variable in PowerShell used to represent NULL.</span></span> <span data-ttu-id="d9273-116">변수에 할당하거나 비교 시 사용하거나 컬렉션에서 NULL의 자리 표시자로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-116">You can assign it to variables, use it in comparisons and use it as a place holder for NULL in a collection.</span></span>

<span data-ttu-id="d9273-117">PowerShell은 `$null`을 NULL 값이 있는 개체로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-117">PowerShell treats `$null` as an object with a value of NULL.</span></span> <span data-ttu-id="d9273-118">다른 언어를 사용하는 경우에는 이와 다르게 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-118">This is different than what you may expect if you come from another language.</span></span>

## <a name="examples-of-null"></a><span data-ttu-id="d9273-119">$null의 예</span><span class="sxs-lookup"><span data-stu-id="d9273-119">Examples of $null</span></span>

<span data-ttu-id="d9273-120">초기화하지 않은 변수를 사용하려고 할 때마다 값은 `$null`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-120">Anytime you try to use a variable that you have not initialized, the value is `$null`.</span></span> <span data-ttu-id="d9273-121">대개 이와 같은 방식으로 `$null` 값이 코드에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-121">This is one of the most common ways that `$null` values sneak into your code.</span></span>

```powershell
PS> $null -eq $undefinedVariable
True
```

<span data-ttu-id="d9273-122">변수 이름을 잘못 입력한 경우 PowerShell은 다른 변수로 인식하고 값은 `$null`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-122">If you happen to mistype a variable name then PowerShell sees it as a different variable and the value is `$null`.</span></span>

<span data-ttu-id="d9273-123">`$null` 값을 알아내는 또 다른 방법은 해당 값을 결과를 제공하지 않는 다른 명령에서 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-123">The other way you find `$null` values is when they come from other commands that don't give you any results.</span></span>

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a><span data-ttu-id="d9273-124">$null의 영향</span><span class="sxs-lookup"><span data-stu-id="d9273-124">Impact of $null</span></span>

<span data-ttu-id="d9273-125">`$null` 값은 표시되는 위치에 따라 코드에 미치는 영향이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-125">`$null` values impact your code differently depending on where they show up.</span></span>

### <a name="in-strings"></a><span data-ttu-id="d9273-126">문자열에서</span><span class="sxs-lookup"><span data-stu-id="d9273-126">In strings</span></span>

<span data-ttu-id="d9273-127">문자열에서 `$null`을 사용하는 경우 $null은 빈 값(또는 빈 문자열)입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-127">If you use `$null` in a string, then it's a blank value (or empty string).</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

<span data-ttu-id="d9273-128">로그 메시지에서 사용할 때 변수 주위에 괄호를 사용하는 이유 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-128">This is one of the reasons that I like to place brackets around variables when using them in log messages.</span></span> <span data-ttu-id="d9273-129">값이 문자열의 끝에 있는 경우 변수 값의 가장자리를 식별하는 것이 더 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-129">It's even more important to identify the edges of your variable values when the value is at the end of the string.</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

<span data-ttu-id="d9273-130">이를 통해 빈 문자열과 `$null` 값을 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-130">This makes empty strings and `$null` values easy to spot.</span></span>

### <a name="in-numeric-equation"></a><span data-ttu-id="d9273-131">숫자 수식에서</span><span class="sxs-lookup"><span data-stu-id="d9273-131">In numeric equation</span></span>

<span data-ttu-id="d9273-132">`$null` 값을 숫자 수식에 사용하는 경우 오류가 발생하지 않으면 결과가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-132">When a `$null` value is used in a numeric equation then your results are invalid if they don't give an error.</span></span> <span data-ttu-id="d9273-133">경우에 따라 `$null`이 `0`으로 계산되기도 하고 전체 결과를 `$null`로 만들기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-133">Sometimes the `$null` evaluates to `0` and other times it makes the whole result `$null`.</span></span>
<span data-ttu-id="d9273-134">다음은 값의 순서에 따라 0 또는 `$null`을 제공하는 곱셈의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-134">Here is an example with multiplication that gives 0 or `$null` depending on the order of the values.</span></span>

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a><span data-ttu-id="d9273-135">컬렉션 대신</span><span class="sxs-lookup"><span data-stu-id="d9273-135">In place of a collection</span></span>

<span data-ttu-id="d9273-136">컬렉션을 사용하면 인덱스를 사용하여 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-136">A collection allow you use an index to access values.</span></span> <span data-ttu-id="d9273-137">실제로 `null`인 컬렉션에 대해 인덱싱하려고 하면 `Cannot index into a null array` 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-137">If you try to index into a collection that is actually `null`, you get this error: `Cannot index into a null array`.</span></span>

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

<span data-ttu-id="d9273-138">컬렉션을 가지고 있지만 해당 컬렉션에 없는 요소에 액세스하려고 하면 `$null` 결과를 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-138">If you have a collection but try to access an element that is not in the collection, you get a `$null` result.</span></span>

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a><span data-ttu-id="d9273-139">개체 대신</span><span class="sxs-lookup"><span data-stu-id="d9273-139">In place of an object</span></span>

<span data-ttu-id="d9273-140">지정된 속성이 없는 개체의 속성 또는 하위 속성에 액세스하려고 하면 정의되지 않은 변수를 사용하는 것과 같은 `$null` 값을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-140">If you try to access a property or sub property of an object that doesn't have the specified property, you get a `$null` value like you would for an undefined variable.</span></span> <span data-ttu-id="d9273-141">이때 변수가 `$null`인지 실제 개체인지는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-141">It doesn't matter if the variable is `$null` or an actual object in this case.</span></span>

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a><span data-ttu-id="d9273-142">Null 값 식에 대한 메서드</span><span class="sxs-lookup"><span data-stu-id="d9273-142">Method on a null-valued expression</span></span>

<span data-ttu-id="d9273-143">`$null` 개체에서 메서드를 호출하면 `RuntimeException`이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-143">Calling a method on a `$null` object throws a `RuntimeException`.</span></span>

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

<span data-ttu-id="d9273-144">`You cannot call a method on a null-valued expression` 구가 표시될 때마다 `$null`에 대해 확인하지 않고 먼저 찾는 것은 변수에 대한 메서드를 호출하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-144">Whenever I see the phrase `You cannot call a method on a null-valued expression` then the first thing I look for are places where I am calling a method on a variable without first checking it for `$null`.</span></span>

## <a name="checking-for-null"></a><span data-ttu-id="d9273-145">$null 확인</span><span class="sxs-lookup"><span data-stu-id="d9273-145">Checking for $null</span></span>

<span data-ttu-id="d9273-146">예제에서 `$null`을 확인하면 항상 `$null`을 왼쪽에 두는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-146">You may have noticed that I always place the `$null` on the left when checking for `$null` in my examples.</span></span> <span data-ttu-id="d9273-147">$null을 왼쪽에 두는 것은 의도적인 것으로 PowerShell 모범 사례로 인정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-147">This is intentional and accepted as a PowerShell best practice.</span></span> <span data-ttu-id="d9273-148">일부 시나리오에서는 $null을 오른쪽에 두면 예상 결과를 얻을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-148">There are some scenarios where placing it on the right doesn't give you the expected result.</span></span>

<span data-ttu-id="d9273-149">다음 예제를 확인하고 결과를 예측해 보세요.</span><span class="sxs-lookup"><span data-stu-id="d9273-149">Look at this next example and try to predict the results:</span></span>

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

<span data-ttu-id="d9273-150">`$value`를 정의하지 않으면 첫 번째는 `$true`로 계산되고 메시지는 `The array is $null`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-150">If I do not define `$value`, the first one evaluates to `$true` and our message is `The array is $null`.</span></span> <span data-ttu-id="d9273-151">여기에서 문제는 두 가지가 모두 `$false`가 되도록 허용하는 `$value`를 만들 수 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-151">The trap here is that it's possible to create a `$value` that allows both of them to be `$false`</span></span>

```powershell
$value = @( $null )
```

<span data-ttu-id="d9273-152">이때 `$value`는 `$null`을 포함하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-152">In this case, the `$value` is an array that contains a `$null`.</span></span> <span data-ttu-id="d9273-153">`-eq`는 배열의 모든 값을 확인하고 일치하는 `$null`을 반환되고</span><span class="sxs-lookup"><span data-stu-id="d9273-153">The `-eq` checks every value in the array and returns the `$null` that is matched.</span></span> <span data-ttu-id="d9273-154">`$false`로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-154">This evaluates to `$false`.</span></span> <span data-ttu-id="d9273-155">`-ne`는 `$null`과 일치하지 않는 모든 항목을 반환하며 이 경우에는 결과가 없습니다(이 또한 `$false`로 계산됨).</span><span class="sxs-lookup"><span data-stu-id="d9273-155">The `-ne` returns everything that doesn't match `$null` and in this case there are no results (This also evaluates to `$false`).</span></span> <span data-ttu-id="d9273-156">둘 중 하나가 true가 되어야 할 것 같지만 모두 `$true`가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-156">Neither one is `$true` even though it looks like one of them should be.</span></span>

<span data-ttu-id="d9273-157">두 값을 모두 `$false`로 계산하는 값을 만들 수 있을 뿐 아니라 둘 다 `$true`로 계산되는 값을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-157">Not only can we create a value that makes both of them evaluate to `$false`, it's possible to create a value where they both evaluate to `$true`.</span></span> <span data-ttu-id="d9273-158">Mathias Jessen(@IISResetMe)은 해당 시나리오에 대해 자세히 설명하는 [유익한 게시물][]을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-158">Mathias Jessen (@IISResetMe) has a [good post][] that dives into that scenario.</span></span>

### <a name="psscriptanalyzer-and-vscode"></a><span data-ttu-id="d9273-159">PSScriptAnalyzer 및 VSCode</span><span class="sxs-lookup"><span data-stu-id="d9273-159">PSScriptAnalyzer and VSCode</span></span>

<span data-ttu-id="d9273-160">[PSScriptAnalyzer][] 모듈에는 `PSPossibleIncorrectComparisonWithNull`이라고 불리는 문제를 확인하는 규칙이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-160">The [PSScriptAnalyzer][] module has a rule that checks for this issue called `PSPossibleIncorrectComparisonWithNull`.</span></span>

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

<span data-ttu-id="d9273-161">VS Code는 PSScriptAnalyser 규칙도 함께 사용하므로 스크립트에서 문제를 식별하거나 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-161">Because VS Code uses the PSScriptAnalyser rules too, it also highlights or identifies this as a problem in your script.</span></span>

### <a name="simple-if-check"></a><span data-ttu-id="d9273-162">간단한 If 확인</span><span class="sxs-lookup"><span data-stu-id="d9273-162">Simple if check</span></span>

<span data-ttu-id="d9273-163">사용자가 $null이 아닌 값을 확인하는 일반적인 방법은 비교하지 않고 간단한 `if()` 문을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-163">A common way that people check for a non-$null value is to use a simple `if()` statement without the comparison.</span></span>

```powershell
if ( $value )
{
    Do-Something
}
```

<span data-ttu-id="d9273-164">값이 `$null`이면 해당 값은 `$false`로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-164">If the value is `$null`, this evaluates to `$false`.</span></span> <span data-ttu-id="d9273-165">이러면 쉽게 읽을 수 있지만 찾고 있는 것을 정확히 찾고 있는지 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-165">This is easy to read, but be careful that it's looking for exactly what you're expecting it to look for.</span></span> <span data-ttu-id="d9273-166">해당 코드 줄은 다음과 같이 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-166">I read that line of code as:</span></span>

> <span data-ttu-id="d9273-167">`$value`에 값이 있는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-167">If `$value` has a value.</span></span>

<span data-ttu-id="d9273-168">그러나 이것이 전부를 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-168">But that's not the whole story.</span></span> <span data-ttu-id="d9273-169">해당 줄은 실제로 다음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-169">That line is actually saying:</span></span>

> <span data-ttu-id="d9273-170">`$value`가 `$null`, `0`, `$false` 또는 `empty string`이 아닌 경우</span><span class="sxs-lookup"><span data-stu-id="d9273-170">If `$value` is not `$null` or `0` or `$false` or an `empty string`</span></span>

<span data-ttu-id="d9273-171">다음은 해당 문의 전체 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-171">Here is a more complete sample of that statement.</span></span>

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

<span data-ttu-id="d9273-172">변수가 값을 가진다는 점뿐만 아니라 다른 값이 `if`로 계산된다는 점을 기억한다면 기본적인 `$false` 확인을 사용해도 괜찮습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-172">It's perfectly OK to use a basic `if` check as long as you remember those other values count as `$false` and not just that a variable has a value.</span></span>

<span data-ttu-id="d9273-173">며칠 전 몇 가지 코드를 리팩터링할 때 이러한 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-173">I ran into this issue when refactoring some code a few days ago.</span></span> <span data-ttu-id="d9273-174">여기에는 다음과 같은 기본적인 속성 검사가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-174">It had a basic property check like this.</span></span>

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="d9273-175">저는 존재하는 경우에만 개체 속성에 값을 할당하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-175">I wanted to assign a value to the object property only if it existed.</span></span> <span data-ttu-id="d9273-176">대부분의 경우 원본 개체에는 `if` 문에서 `$true`로 평가되는 값이 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-176">In most cases, the original object had a value that would evaluate to `$true` in the `if` statement.</span></span> <span data-ttu-id="d9273-177">그러나 가끔 값이 설정되지 않는 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-177">But I ran into an issue where the value was occasionally not getting set.</span></span> <span data-ttu-id="d9273-178">코드를 디버그했는데 속성이 있지만 빈 문자열 값인 개체를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-178">I debugged the code and found that the object had the property but it was a blank string value.</span></span> <span data-ttu-id="d9273-179">이로 인해 이전 논리를 사용한 업데이트가 전혀 진행되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-179">This prevented it from ever getting updated with the previous logic.</span></span> <span data-ttu-id="d9273-180">그래서 적절한 `$null` 확인을 추가했고 모든 작업이 문제없이 진행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-180">So I added a proper `$null` check and everything worked.</span></span>

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="d9273-181">이러한 버그는 발견하기가 어려우며 `$null`에 대한 값을 적극적으로 확인하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-181">It's little bugs like these that are hard to spot and make me aggressively check values for `$null`.</span></span>

## <a name="nullcount"></a><span data-ttu-id="d9273-182">$null.Count</span><span class="sxs-lookup"><span data-stu-id="d9273-182">$null.Count</span></span>

<span data-ttu-id="d9273-183">`$null` 값의 속성에 액세스하려고 하는 경우 해당 속성도 `$null`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-183">If you try to access a property on a `$null` value, that the property is also `$null`.</span></span> <span data-ttu-id="d9273-184">`count` 속성은 해당 규칙의 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-184">The `count` property is the exception to this rule.</span></span>

```powershell
PS> $value = $null
PS> $value.count
0
```

<span data-ttu-id="d9273-185">`$null` 값이 있으면 `count`도 `0`이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-185">When you have a `$null` value, then the `count` is `0`.</span></span> <span data-ttu-id="d9273-186">이 특수 속성은 PowerShell을 통해 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-186">This special property is added by PowerShell.</span></span>

### <a name="pscustomobject-count"></a><span data-ttu-id="d9273-187">[PSCustomObject] 수</span><span class="sxs-lookup"><span data-stu-id="d9273-187">[PSCustomObject] Count</span></span>

<span data-ttu-id="d9273-188">PowerShell의 거의 모든 개체에는 해당 수 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-188">Almost all objects in PowerShell have that count property.</span></span> <span data-ttu-id="d9273-189">한 가지 중요한 예외는 Windows PowerShell 5.1의 `[PSCustomObject]`입니다(PowerShell 6.0에서 수정됨).</span><span class="sxs-lookup"><span data-stu-id="d9273-189">One important exception is the `[PSCustomObject]` in Windows PowerShell 5.1 (This is fixed in PowerShell 6.0).</span></span> <span data-ttu-id="d9273-190">수 속성이 없으므로 해당 값을 사용하려고 하면 `$null` 값을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-190">It doesn't have a count property so you get a `$null` value if you try to use it.</span></span> <span data-ttu-id="d9273-191">사용자가 `$null` 확인 대신 `.Count`를 사용하려고 시도하지 않도록 하기 위해 여기에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-191">I call this out here so that you don't try to use `.Count` instead of a `$null` check.</span></span>

<span data-ttu-id="d9273-192">Windows PowerShell 5.1 및 PowerShell 6.0에서 해당 예제를 실행하면 다른 결과를 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-192">Running this example on Windows PowerShell 5.1 and PowerShell 6.0 gives you different results.</span></span>

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a><span data-ttu-id="d9273-193">빈 null</span><span class="sxs-lookup"><span data-stu-id="d9273-193">Empty null</span></span>

<span data-ttu-id="d9273-194">서로 다르게 작동하는 특수 형식의 `$null`이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-194">There is one special type of `$null` that acts differently than the others.</span></span> <span data-ttu-id="d9273-195">빈 `$null`을 호출하려고 하는데 이것은 사실 [System.Management.Automation.Internal.AutomationNull][]입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-195">I am going to call it the empty `$null` but it's really a [System.Management.Automation.Internal.AutomationNull][].</span></span> <span data-ttu-id="d9273-196">빈 `$null`은 아무것도 반환하지 않는 함수 또는 스크립트 블록의 결과로 얻게 됩니다(무효 결과).</span><span class="sxs-lookup"><span data-stu-id="d9273-196">This empty `$null` is the one you get as the result of a function or script block that returns nothing (a void result).</span></span>

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

<span data-ttu-id="d9273-197">`$null`과 비교하면 `$null` 값을 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-197">If you compare it with `$null`, you get a `$null` value.</span></span> <span data-ttu-id="d9273-198">값이 필요한 평가에서 사용되는 경우 값은 항상 `$null`입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-198">When used in an evaluation where a value is required, the value is always `$null`.</span></span> <span data-ttu-id="d9273-199">하지만 배열 내부에 배치하면 빈 배열과 동일하게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-199">But if you place it inside an array, it's treated the same as an empty array.</span></span>

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

<span data-ttu-id="d9273-200">`$null` 값이 한 개 포함되어 있고 해당 `count`가 `1`인 배열을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-200">You can have an array that contains one `$null` value and its `count` is `1`.</span></span> <span data-ttu-id="d9273-201">하지만 배열 내부에 빈 결과를 배치하면 항목으로 계산되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-201">But if you place an empty result inside an array then it's not counted as an item.</span></span> <span data-ttu-id="d9273-202">수는 `0`입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-202">The count is `0`.</span></span>

<span data-ttu-id="d9273-203">컬렉션처럼 빈 `$null`을 처리하면 이것이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-203">If you treat the empty `$null` like a collection, then it's empty.</span></span>

### <a name="pipeline"></a><span data-ttu-id="d9273-204">파이프라인</span><span class="sxs-lookup"><span data-stu-id="d9273-204">Pipeline</span></span>

<span data-ttu-id="d9273-205">차이점은 파이프라인을 사용할 때 가장 잘 드러납니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-205">The primary place you see the difference is when using the pipeline.</span></span> <span data-ttu-id="d9273-206">`$null` 값을 파이프하지만 빈 `$null` 값은 파이프하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-206">You can pipe a `$null` value but not an empty `$null` value.</span></span>

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

<span data-ttu-id="d9273-207">코드에 따라 논리에서 `$null`을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-207">Depending on your code, you should account for the `$null` in your logic.</span></span>

<span data-ttu-id="d9273-208">먼저 `$null`을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d9273-208">Either check for `$null` first</span></span>

- <span data-ttu-id="d9273-209">파이프라인에서 Null을 필터링(`... | Where {$null -ne $_} | ...`)</span><span class="sxs-lookup"><span data-stu-id="d9273-209">Filter out null on the pipeline (`... | Where {$null -ne $_} | ...`)</span></span>
- <span data-ttu-id="d9273-210">파이프라인 함수에서 처리</span><span class="sxs-lookup"><span data-stu-id="d9273-210">Handle it in the pipeline function</span></span>

## <a name="foreach"></a><span data-ttu-id="d9273-211">foreach</span><span class="sxs-lookup"><span data-stu-id="d9273-211">foreach</span></span>

<span data-ttu-id="d9273-212">`foreach`에서 제가 가장 좋아하는 기능 중 하나는 Foreach가 `$null` 컬렉션에 대해 열거하지 않는다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-212">One of my favorite features of `foreach` is that it doesn't enumerate over a `$null` collection.</span></span>

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

<span data-ttu-id="d9273-213">이로 인해 컬렉션을 열거하기 전에 컬렉션에서 `$null` 확인을 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-213">This saves me from having to `$null` check the collection before I enumerate it.</span></span> <span data-ttu-id="d9273-214">`$null` 값의 컬렉션이 있더라도 `$node`는 여전히 `$null`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-214">If you have a collection of `$null` values, the `$node` can still be `$null`.</span></span>

<span data-ttu-id="d9273-215">Foreach는 PowerShell 3.0을 사용하여 이러한 방식으로 작업하기 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-215">The foreach started working this way with PowerShell 3.0.</span></span> <span data-ttu-id="d9273-216">이전 버전을 사용하는 경우 해당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-216">If you happen to be on an older version, then this is not the case.</span></span> <span data-ttu-id="d9273-217">2\.0 호환성을 위한 백포팅 코드를 사용하는 경우 알아야 할 주요 변경 사항 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-217">This is one of the important changes to be aware of when back-porting code for 2.0 compatibility.</span></span>

## <a name="value-types"></a><span data-ttu-id="d9273-218">값 형식</span><span class="sxs-lookup"><span data-stu-id="d9273-218">Value types</span></span>

<span data-ttu-id="d9273-219">기술적으로는 참조 형식만 `$null`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-219">Technically, only reference types can be `$null`.</span></span> <span data-ttu-id="d9273-220">그러나 PowerShell은 매우 관대하며 변수를 모든 형식으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-220">But PowerShell is very generous and allows for variables to be any type.</span></span> <span data-ttu-id="d9273-221">값 형식을 강력한 형식으로 결정한 경우에는 `$null`이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-221">If you decide to strongly type a value type, it cannot be `$null`.</span></span>
<span data-ttu-id="d9273-222">PowerShell은 `$null`을 여러 형식의 기본값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-222">PowerShell converts `$null` to a default value for many types.</span></span>

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

<span data-ttu-id="d9273-223">일부 형식은 `$null`에서 유효한 전환을 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-223">There are some types that do not have a valid conversion from `$null`.</span></span> <span data-ttu-id="d9273-224">이러한 형식은 `Cannot convert null to type` 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-224">These types generate a `Cannot convert null to type` error.</span></span>

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a><span data-ttu-id="d9273-225">함수 매개 변수</span><span class="sxs-lookup"><span data-stu-id="d9273-225">Function parameters</span></span>

<span data-ttu-id="d9273-226">함수 매개 변수에 강력한 형식의 값을 사용하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-226">Using a strongly typed values in function parameters is very common.</span></span> <span data-ttu-id="d9273-227">일반적으로 스크립트에서 기타 변수의 형식을 정의하지 않는 경우에도 매개 변수의 형식을 정의하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-227">We generally learn to define the types of our parameters even if we tend not to define the types of other variables in our scripts.</span></span> <span data-ttu-id="d9273-228">함수에 강력한 형식의 변수가 이미 있지만 그것을 모르고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-228">You may already have some strongly typed variables in your functions and not even realize it.</span></span>

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

<span data-ttu-id="d9273-229">매개 변수의 형식을 `string`으로 설정하는 즉시 값은 `$null`이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-229">As soon as you set the type of the parameter as a `string`, the value can never be `$null`.</span></span> <span data-ttu-id="d9273-230">사용자가 값을 제공했는지 여부를 확인하기 위해 값이 `$null`인지 확인하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-230">It's common to check if a value is `$null` to see if the user provided a value or not.</span></span>

```powershell
if ( $null -ne $Value ){...}
```

<span data-ttu-id="d9273-231">값을 제공하지 않는 경우 `$Value` 는 빈 문자열 `''`입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-231">`$Value` is an empty string `''` when no value is provided.</span></span> <span data-ttu-id="d9273-232">대신 자동 변수 `$PSBoundParameters.Value`를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d9273-232">Use the automatic variable `$PSBoundParameters.Value` instead.</span></span>

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

<span data-ttu-id="d9273-233">해당 함수가 호출될 때 `$PSBoundParameters`는 지정된 매개 변수만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-233">`$PSBoundParameters` only contains the parameters that were specified when the function was called.</span></span>
<span data-ttu-id="d9273-234">속성을 확인하려면 `ContainsKey` 메서드도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-234">You can also use the `ContainsKey` method to check for the property.</span></span>

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a><span data-ttu-id="d9273-235">IsNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="d9273-235">IsNotNullOrEmpty</span></span>

<span data-ttu-id="d9273-236">값이 문자열인 경우 정적 문자열 함수를 사용하여 값이 `$null`이 되었는지 빈 문자열인지 동시에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-236">If the value is a string, you can use a static string function to check if the value is `$null` or an empty string at the same time.</span></span>

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

<span data-ttu-id="d9273-237">값 형식이 문자열이어야 하는 경우 이것을 자주 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-237">I find myself using this often when I know the value type should be a string.</span></span>

## <a name="when-i-null-check"></a><span data-ttu-id="d9273-238">제가 $null 확인을 할 때</span><span class="sxs-lookup"><span data-stu-id="d9273-238">When I $null check</span></span>

<span data-ttu-id="d9273-239">방어적인 스크립터가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-239">I am a defensive scripter.</span></span> <span data-ttu-id="d9273-240">함수를 호출하고 해당 함수에 변수를 할당할 때마다 저는 `$null`을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-240">Anytime I call a function and assign it to a variable, I check it for `$null`.</span></span>

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

<span data-ttu-id="d9273-241">`try/catch`를 사용하는 것보다 `if` 또는 `foreach`를 사용하는 것을 훨씬 선호합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-241">I much prefer using `if` or `foreach` over using `try/catch`.</span></span> <span data-ttu-id="d9273-242">`try/catch`도 여전히 많이 사용하긴 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-242">Don't get me wrong, I still use `try/catch` a lot.</span></span> <span data-ttu-id="d9273-243">하지만 오류 조건 또는 빈 결과 집합을 테스트할 수 있다면 예외 처리를 실제 예외에만 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-243">But if I can test for an error condition or an empty set of results, I can allow my exception handling be for true exceptions.</span></span>

<span data-ttu-id="d9273-244">또한 개체에 대한 값을 인덱싱하거나 메서드를 호출하기 전에 `$null`을 확인하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-244">I also tend to check for `$null` before I index into a value or call methods on an object.</span></span> <span data-ttu-id="d9273-245">이러한 두 가지 작업은 `$null` 개체에 대해 실패하므로 먼저 유효성을 검사하는 것이 중요하다고 생각합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-245">These two actions fail for a `$null` object so I find it important to validate them first.</span></span> <span data-ttu-id="d9273-246">게시물의 앞부분에서 이러한 시나리오에 대해 이미 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-246">I already covered those scenarios earlier in this post.</span></span>

### <a name="no-results-scenario"></a><span data-ttu-id="d9273-247">결과 없음 시나리오</span><span class="sxs-lookup"><span data-stu-id="d9273-247">No results scenario</span></span>

<span data-ttu-id="d9273-248">다른 함수 및 명령은 결과 없음 시나리오를 다르게 처리한다는 점을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-248">It's important to know that different functions and commands handle the no results scenario differently.</span></span> <span data-ttu-id="d9273-249">많은 PowerShell 명령은 빈 `$null` 및 오류 스트림의 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-249">Many PowerShell commands return the empty `$null` and an error in the error stream.</span></span> <span data-ttu-id="d9273-250">그러나 다른 명령은 예외를 throw하거나 상태 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-250">But others throw exceptions or give you a status object.</span></span> <span data-ttu-id="d9273-251">사용하는 명령이 결과 없음 및 오류 시나리오를 처리하는 방법을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-251">It's still up to you to know how the commands you use deal with the no results and error scenarios.</span></span>

## <a name="initializing-to-null"></a><span data-ttu-id="d9273-252">$null로 초기화</span><span class="sxs-lookup"><span data-stu-id="d9273-252">Initializing to $null</span></span>

<span data-ttu-id="d9273-253">저는 변수를 사용하기 전에 모든 변수를 초기화하는 습관을 가지게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-253">One habit that I have picked up is initializing all my variables before I use them.</span></span> <span data-ttu-id="d9273-254">다른 언어에서는 이 작업을 반드시 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-254">You are required to do this in other languages.</span></span> <span data-ttu-id="d9273-255">함수 맨 위 또는 foreach 루프를 입력하는 경우 사용하는 모든 값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-255">At the top of my function or as I enter a foreach loop, I define all the values that I'm using.</span></span>

<span data-ttu-id="d9273-256">다음 시나리오를 자세히 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="d9273-256">Here is a scenario that I want you to take a close look at.</span></span> <span data-ttu-id="d9273-257">이전에 추적해야 했던 버그의 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-257">It's an example of a bug I had to chase down before.</span></span>

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

<span data-ttu-id="d9273-258">여기에서는 `Get-Something`이 결과 또는 빈 `$null`을 반환할 거라고 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-258">The expectation here is that `Get-Something` returns either a result or an empty `$null`.</span></span> <span data-ttu-id="d9273-259">오류가 발생하면 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-259">If there is an error, we log it.</span></span> <span data-ttu-id="d9273-260">그런 다음 오류를 처리하기 전에 유효한 결과가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-260">Then we check to make sure we got a valid result before processing it.</span></span>

<span data-ttu-id="d9273-261">해당 코드에서 발생하는 버그는 `Get-Something`이 예외를 throw하고 `$result`에 값을 할당하지 않는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-261">The bug hiding in this code is when `Get-Something` throws an exception and doesn't assign a value to `$result`.</span></span> <span data-ttu-id="d9273-262">할당하기 전에 실패했으므로 `$result` 변수에 `$null`을 할당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-262">It fails before the assignment so we don't even assign `$null` to the `$result` variable.</span></span> <span data-ttu-id="d9273-263">`$result`에는 다른 반복에서 이전에 유효했던 `$result`가 계속 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-263">`$result` still contains the previous valid `$result` from other iterations.</span></span>
<span data-ttu-id="d9273-264">이 시나리오에서는 `Update-Something`이 동일한 개체에서 여러 번 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-264">`Update-Something` to execute multiple times on the same object in this example.</span></span>

<span data-ttu-id="d9273-265">해당 문제를 완화하기 위해 사용 전 foreach 루프 내부에 `$result`를 `$null`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-265">I set `$result` to `$null` right inside the foreach loop before I use it to mitigate this issue.</span></span>

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a><span data-ttu-id="d9273-266">범위 문제</span><span class="sxs-lookup"><span data-stu-id="d9273-266">Scope issues</span></span>

<span data-ttu-id="d9273-267">범위 지정 문제를 완화하는 데도 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-267">This also helps mitigate scoping issues.</span></span> <span data-ttu-id="d9273-268">해당 예제에서는 루프에서 값을 `$result`로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-268">In that example, we assign values to `$result` over and over in a loop.</span></span> <span data-ttu-id="d9273-269">그러나 PowerShell은 함수 외부의 변수 값이 현재 함수의 범위에 영향을 미치는 것을 허용하므로 함수 내부에서 이를 초기화하면 해당 방식으로 생길 수 있는 버그가 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-269">But because PowerShell allows variable values from outside the function to bleed into the scope of the current function, initializing them inside your function mitigates bugs that can be introduced that way.</span></span>

<span data-ttu-id="d9273-270">함수에서 초기화되지 않은 변수가 부모 범위의 값으로 설정된 경우 `$null`이 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-270">An uninitialized variable in your function is not `$null` if it's set to a value in a parent scope.</span></span>
<span data-ttu-id="d9273-271">부모 범위는 함수를 호출하고 동일한 변수 이름을 사용하는 또 다른 함수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-271">The parent scope could be another function that calls your function and uses the same variable names.</span></span>

<span data-ttu-id="d9273-272">동일한 `Do-something` 예제를 사용하고 루프를 제거하면 다음 예제와 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-272">If I take that same `Do-something` example and remove the loop, I would end up with something that looks like this example:</span></span>

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

<span data-ttu-id="d9273-273">`Get-Something` 호출이 예외를 throw하는 경우 내 `$null` 확인에서 `Invoke-Something`에서 `$result`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-273">If the call to `Get-Something` throws an exception, then my `$null` check finds the `$result` from `Invoke-Something`.</span></span> <span data-ttu-id="d9273-274">함수 내부의 값을 초기화하면 해당 문제가 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-274">Initializing the value inside your function mitigates this issue.</span></span>

<span data-ttu-id="d9273-275">변수에 이름을 붙이는 것은 어려우며 작성자가 여러 함수에서 동일한 변수 이름을 사용하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-275">Naming variables is hard and it's common for an author to use the same variable names in multiple functions.</span></span> <span data-ttu-id="d9273-276">저는 `$node`, `$result`, `$data`를 항상 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-276">I know I use `$node`,`$result`,`$data` all the time.</span></span> <span data-ttu-id="d9273-277">따라서 다른 범위를 가진 값이 있어서는 안 될 장소에서 표시되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-277">So it would be very easy for values from different scopes to show up in places where they should not be.</span></span>

## <a name="redirect-output-to-null"></a><span data-ttu-id="d9273-278">출력을 $null로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="d9273-278">Redirect output to $null</span></span>

<span data-ttu-id="d9273-279">전체 문서에서 `$null` 값에 대해 설명했고 이제 출력을 `$null`로 리디렉션하는 것에 대해서도 다루려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-279">I have been talking about `$null` values for this entire article but the topic is not complete if I didn't mention redirecting output to `$null`.</span></span> <span data-ttu-id="d9273-280">표시하지 않으려는 정보 또는 개체를 출력하는 명령이 있는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-280">There are times when you have commands that output information or objects that you want to suppress.</span></span> <span data-ttu-id="d9273-281">출력을 `$null`로 리디렉션하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-281">Redirecting output to `$null` does that.</span></span>

### <a name="out-null"></a><span data-ttu-id="d9273-282">Out-Null</span><span class="sxs-lookup"><span data-stu-id="d9273-282">Out-Null</span></span>

<span data-ttu-id="d9273-283">Out-Null 명령은 파이프라인 데이터를 `$null`로 리디렉션하는 기본 제공 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-283">The Out-Null command is the built-in way to redirect pipeline data to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a><span data-ttu-id="d9273-284">$null에 할당</span><span class="sxs-lookup"><span data-stu-id="d9273-284">Assign to $null</span></span>

<span data-ttu-id="d9273-285">`Out-Null`을 사용하는 것과 동일한 효과를 위해 `$null`에 명령 결과를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-285">You can assign the results of a command to `$null` for the same effect as using `Out-Null`.</span></span>

```powershell
$null = New-Item -Type Directory -Path $path
```

<span data-ttu-id="d9273-286">`$null`은 상수 값이므로 덮어쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-286">Because `$null` is a constant value, you can never overwrite it.</span></span> <span data-ttu-id="d9273-287">코드에서 표시되는 방식이 마음에 들진 않지만 `Out-Null`보다 빠르게 실행되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-287">I don't like the way it looks in my code but it often performs faster than `Out-Null`.</span></span>

### <a name="redirect-to-null"></a><span data-ttu-id="d9273-288">$null로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="d9273-288">Redirect to $null</span></span>

<span data-ttu-id="d9273-289">리디렉션 연산자를 사용하여 출력을 `$null`로 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-289">You can also use the redirection operator to send output to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path > $null
```

<span data-ttu-id="d9273-290">다른 스트림에서 출력되는 명령줄 실행 파일을 처리하는 경우</span><span class="sxs-lookup"><span data-stu-id="d9273-290">If you're dealing with command-line executables that output on the different streams.</span></span> <span data-ttu-id="d9273-291">다음과 같이 모든 출력 스트림을 `$null`로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-291">You can redirect all output streams to `$null` like this:</span></span>

```powershell
git status *> $null
```

## <a name="summary"></a><span data-ttu-id="d9273-292">요약</span><span class="sxs-lookup"><span data-stu-id="d9273-292">Summary</span></span>

<span data-ttu-id="d9273-293">해당 문서에서 여러 가지를 설명했고 이것이 다른 심층 분석보다 조각화되었다는 점을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-293">I covered a lot of ground on this one and I know this article is more fragmented than most of my deep dives.</span></span> <span data-ttu-id="d9273-294">이것은 `$null` 값이 PowerShell의 여러 다른 위치에서 표시될 수 있고 발견되는 위치에 따라 미묘한 차이가 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-294">That is because `$null` values can pop up in many different places in PowerShell and all the nuances are specific to where you find it.</span></span> <span data-ttu-id="d9273-295">`$null`에 대해 더 잘 이해하고 접할 가능성이 있는 더 모호한 시나리오에 대해 더 잘 알게 되셨길 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="d9273-295">I hope you walk away from this with a better understanding of `$null` and an awareness of the more obscure scenarios you may run into.</span></span>

<!-- link references -->
[원본 버전]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[유익한 게시물]: https://blog.iisreset.me/schrodingers-argumentlist
[good post]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
