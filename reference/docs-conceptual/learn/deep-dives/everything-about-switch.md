---
title: Switch 문에 대해 알고 싶은 모든 것
description: PowerShell의 switch 문은 다른 언어에서 찾을 수 없는 기능을 제공합니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: c2e77aa5fb36d04fec1bc86f751291205120c729
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355122"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a><span data-ttu-id="cc798-103">Switch 문에 대해 알고 싶은 모든 것</span><span class="sxs-lookup"><span data-stu-id="cc798-103">Everything you ever wanted to know about the switch statement</span></span>

<span data-ttu-id="cc798-104">다른 많은 언어처럼 PowerShell에도 스크립트 내의 실행 흐름을 제어하는 명령이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-104">Like many other languages, PowerShell has commands for controlling the flow of execution within your scripts.</span></span> <span data-ttu-id="cc798-105">이러한 문 중 하나가 [switch][] 문이며, PowerShell에서 이 문은 다른 언어에는 없는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-105">One of those statements is the [switch][] statement and in PowerShell, it offers features that aren't found in other languages.</span></span> <span data-ttu-id="cc798-106">오늘은 PowerShell `switch` 이용 방법을 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-106">Today, we take a deep dive into working with the PowerShell `switch`.</span></span>

> [!NOTE]
> <span data-ttu-id="cc798-107">이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="cc798-108">PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="cc798-109">[PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="cc798-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="cc798-110">`if` 문</span><span class="sxs-lookup"><span data-stu-id="cc798-110">The `if` statement</span></span>

<span data-ttu-id="cc798-111">`if` 문은 가장 먼저 배우는 문에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-111">One of the first statements that you learn is the `if` statement.</span></span> <span data-ttu-id="cc798-112">문이 `$true`라면 스크립트 블록을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-112">It lets you execute a script block if a statement is `$true`.</span></span>

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

<span data-ttu-id="cc798-113">`elseif` 및 `else` 문을 사용하면 훨씬 더 복잡한 논리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-113">You can have much more complicated logic by using `elseif` and `else` statements.</span></span> <span data-ttu-id="cc798-114">다음은 요일에 대한 숫자 값이 있고 이름을 문자열로 가져오는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-114">Here is an example where I have a numeric value for day of the week and I want to get the name as a string.</span></span>

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

<span data-ttu-id="cc798-115">이것은 일반적인 패턴이며 처리하는 방법은 대단히 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-115">It turns out that this is a common pattern and there are many ways to deal with this.</span></span> <span data-ttu-id="cc798-116">그중 하나가 `switch`를 이용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-116">One of them is with a `switch`.</span></span>

## <a name="switch-statement"></a><span data-ttu-id="cc798-117">Switch 문</span><span class="sxs-lookup"><span data-stu-id="cc798-117">Switch statement</span></span>

<span data-ttu-id="cc798-118">`switch` 문을 사용하면 변수와 가능한 값 목록을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-118">The `switch` statement allows you to provide a variable and a list of possible values.</span></span> <span data-ttu-id="cc798-119">값이 변수와 일치하면 관련 scriptblock이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-119">If the value matches the variable, then its scriptblock is executed.</span></span>

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

<span data-ttu-id="cc798-120">이 예제에서는 `$day` 값이 숫자 값 중 하 나와 일치하면 `$result`에 올바른 이름이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-120">For this example, the value of `$day` matches one of the numeric values, then the correct name is assigned to `$result`.</span></span> <span data-ttu-id="cc798-121">이 예제에서는 변수 할당만 수행하지만 이러한 스크립트 블록에서는 어떤 PowerShell도 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-121">We are only doing a variable assignment in this example, but any PowerShell can be executed in those script blocks.</span></span>

### <a name="assign-to-a-variable"></a><span data-ttu-id="cc798-122">변수에 할당</span><span class="sxs-lookup"><span data-stu-id="cc798-122">Assign to a variable</span></span>

<span data-ttu-id="cc798-123">마지막 예제를 다른 방식으로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-123">We can write that last example in another way.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

<span data-ttu-id="cc798-124">지금은 PowerShell 파이프라인에 값을 배치하고 이 값을 `$result`에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-124">We are placing the value on the PowerShell pipeline and assigning it to the `$result`.</span></span> <span data-ttu-id="cc798-125">`if` 및 `foreach` 문을 사용하여 같은 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-125">You can do this same thing with the `if` and `foreach` statements.</span></span>

### <a name="default"></a><span data-ttu-id="cc798-126">기본값</span><span class="sxs-lookup"><span data-stu-id="cc798-126">Default</span></span>

<span data-ttu-id="cc798-127">`default` 키워드를 사용하면 일치하는 항목이 없을 때 수행할 동작을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-127">We can use the `default` keyword to identify the what should happen if there is no match.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

<span data-ttu-id="cc798-128">여기서는 기본 사례에서 `Unknown` 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-128">Here we return the value `Unknown` in the default case.</span></span>

### <a name="strings"></a><span data-ttu-id="cc798-129">문자열</span><span class="sxs-lookup"><span data-stu-id="cc798-129">Strings</span></span>

<span data-ttu-id="cc798-130">이전 예제 모음에서는 숫자를 일치시켰지만 문자열을 일치시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-130">I was matching numbers in those last examples, but you can also match strings.</span></span>

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="cc798-131">선택사항임을 강조하기 위해 `Component`,`Role` 및 `Location` 매치를 따옴표로 래핑하지는 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-131">I decided not to wrap the `Component`,`Role` and `Location` matches in quotes here to highlight that they're optional.</span></span> <span data-ttu-id="cc798-132">대부분의 경우 `switch`는 이를 문자열로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-132">The `switch` treats those as a string in most cases.</span></span>

## <a name="arrays"></a><span data-ttu-id="cc798-133">배열</span><span class="sxs-lookup"><span data-stu-id="cc798-133">Arrays</span></span>

<span data-ttu-id="cc798-134">PowerShell `switch`의 대표적인 멋진 기능은 배열 처리 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-134">One of the cool features of the PowerShell `switch` is the way it handles arrays.</span></span> <span data-ttu-id="cc798-135">`switch`에 배열을 제공하면 관련 컬렉션의 각 요소를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-135">If you give a `switch` an array, it processes each element in that collection.</span></span>

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

<span data-ttu-id="cc798-136">배열에 반복된 항목이 있다면 관련 섹션에서 여러 번 일치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-136">If you have repeated items in your array, then they're matched multiple times by the appropriate section.</span></span>

### <a name="psitem"></a><span data-ttu-id="cc798-137">PSItem</span><span class="sxs-lookup"><span data-stu-id="cc798-137">PSItem</span></span>

<span data-ttu-id="cc798-138">`$PSItem` 또는 `$_`를 사용하면 처리된 현재 항목을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-138">You can use the `$PSItem` or `$_` to reference the current item that was processed.</span></span> <span data-ttu-id="cc798-139">간단한 일치를 수행할 때는 `$PSItem`이 우리가 일치하는 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-139">When we do a simple match, `$PSItem` is the value that we are matching.</span></span> <span data-ttu-id="cc798-140">이 변수를 사용하는 다음 섹션에서 몇 가지 고급 일치를 수행하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-140">I'll be performing some advanced matches in the next section where this variable is used.</span></span>

## <a name="parameters"></a><span data-ttu-id="cc798-141">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cc798-141">Parameters</span></span>

<span data-ttu-id="cc798-142">PowerShell `switch`의 고유한 기능은 다양한 [switch 매개 변수][]로 작동 방식을 변경하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-142">A unique feature of the PowerShell `switch` is that it has a number of [switch parameters][] that change how it performs.</span></span>

### <a name="-casesensitive"></a><span data-ttu-id="cc798-143">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="cc798-143">-CaseSensitive</span></span>

<span data-ttu-id="cc798-144">기본적으로 일치는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-144">The matches aren't case-sensitive by default.</span></span> <span data-ttu-id="cc798-145">대/소문자를 구분해야 한다면 `-CaseSensitive`를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-145">If you need to be case-sensitive, you can use `-CaseSensitive`.</span></span> <span data-ttu-id="cc798-146">다른 switch 매개 변수와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-146">This can be used in combination with the other switch parameters.</span></span>

### <a name="-wildcard"></a><span data-ttu-id="cc798-147">-Wildcard</span><span class="sxs-lookup"><span data-stu-id="cc798-147">-Wildcard</span></span>

<span data-ttu-id="cc798-148">`-wildcard` switch를 사용하면 와일드카드 지원을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-148">We can enable wildcard support with the `-wildcard` switch.</span></span> <span data-ttu-id="cc798-149">`-like` 연산자로 각 일치를 수행할 때와 같은 와일드카드 논리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-149">This uses the same wildcard logic as the `-like` operator to do each match.</span></span>

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

<span data-ttu-id="cc798-150">여기서는 메시지를 처리한 다음 내용에 따라 서로 다른 스트림에 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-150">Here we are processing a message and then outputting it on different streams based on the contents.</span></span>

### <a name="-regex"></a><span data-ttu-id="cc798-151">-Regex</span><span class="sxs-lookup"><span data-stu-id="cc798-151">-Regex</span></span>

<span data-ttu-id="cc798-152">Switch 문은 와일드카드처럼 정규식 일치도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-152">The switch statement supports regex matches just like it does wildcards.</span></span>

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

<span data-ttu-id="cc798-153">제가 작성한 다른 문서에서 정규식을 사용하는 추가 예제를 확인할 수 있습니다. [정규식을 사용하는 다양한 방법][]</span><span class="sxs-lookup"><span data-stu-id="cc798-153">I have more examples of using regex in another article I wrote: [The many ways to use regex][].</span></span>

### <a name="-file"></a><span data-ttu-id="cc798-154">-File</span><span class="sxs-lookup"><span data-stu-id="cc798-154">-File</span></span>

<span data-ttu-id="cc798-155">Switch 문은 `-File` 매개 변수로 파일을 처리한다는 잘 알려지지 않은 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-155">A little known feature of the switch statement is that it can process a file with the `-File` parameter.</span></span> <span data-ttu-id="cc798-156">변수 식을 제공하는 대신 `-file`을 파일 경로와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-156">You use `-file` with a path to a file instead of giving it a variable expression.</span></span>

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="cc798-157">배열 처리와 비슷한 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-157">It works just like processing an array.</span></span> <span data-ttu-id="cc798-158">이 예제에서는 이를 와일드카드와 일치와 결합하고 `$PSItem`을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-158">In this example, I combine it with wildcard matching and make use of the `$PSItem`.</span></span> <span data-ttu-id="cc798-159">그러면 로그 파일을 처리하고 정규식 일치에 따라 경고 및 오류 메시지로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-159">This would process a log file and convert it to warning and error messages depending on the regex matches.</span></span>

## <a name="advanced-details"></a><span data-ttu-id="cc798-160">고급 정보</span><span class="sxs-lookup"><span data-stu-id="cc798-160">Advanced details</span></span>

<span data-ttu-id="cc798-161">문서화된 기능을 모두 확인했으니 이제 더 복잡한 처리 컨텍스트에서 이러한 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-161">Now that you're aware of all these documented features, we can use them in the context of more advanced processing.</span></span>

### <a name="expressions"></a><span data-ttu-id="cc798-162">식</span><span class="sxs-lookup"><span data-stu-id="cc798-162">Expressions</span></span>

<span data-ttu-id="cc798-163">`switch`는 변수 대신 식에 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-163">The `switch` can be on an expression instead of a variable.</span></span>

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

<span data-ttu-id="cc798-164">식의 평가 대상은 일치에 사용한 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-164">Whatever the expression evaluates to is the value used for the match.</span></span>

### <a name="multiple-matches"></a><span data-ttu-id="cc798-165">다중 일치</span><span class="sxs-lookup"><span data-stu-id="cc798-165">Multiple matches</span></span>

<span data-ttu-id="cc798-166">이 기능은 이미 알고 계실지도 모르지만, `switch`는 여러 조건에 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-166">You may have already picked up on this, but a `switch` can match to multiple conditions.</span></span> <span data-ttu-id="cc798-167">`-wildcard` 또는 `-regex` 일치를 사용할 때는 더욱더 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-167">This is especially true when using `-wildcard` or `-regex` matches.</span></span> <span data-ttu-id="cc798-168">동일한 조건을 여러 번 추가할 수 있으며 이 경우 모든 조건이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-168">You can add the same condition multiple times and all of them are triggered.</span></span>

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

<span data-ttu-id="cc798-169">다음 문 3가지는 모두 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-169">All three of these statements are fired.</span></span> <span data-ttu-id="cc798-170">모든 조건이 (순서대로) 확인됨을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-170">This shows that every condition is checked (in order).</span></span> <span data-ttu-id="cc798-171">이것은 각 항목이 각 조건을 확인하는 배열을 처리하는 경우에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-171">This holds true for processing arrays where each item checks each condition.</span></span>

### <a name="continue"></a><span data-ttu-id="cc798-172">계속</span><span class="sxs-lookup"><span data-stu-id="cc798-172">Continue</span></span>

<span data-ttu-id="cc798-173">보통은 이 시점에서 `break` 문을 소개하지만 `continue` 사용 방법을 먼저 확인하면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-173">Normally, this is where I would introduce the `break` statement, but it's better that we learn how to use `continue` first.</span></span> <span data-ttu-id="cc798-174">`foreach` 루프처럼 `continue`는 컬렉션의 다음 항목으로 계속 진행하거나 남은 항목이 없다면 `switch`를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-174">Just like with a `foreach` loop, `continue` continues onto the next item in the collection or exits the `switch` if there are no more items.</span></span> <span data-ttu-id="cc798-175">마지막 예제를 continue 문으로 다시 작성하면 문을 하나만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-175">We can rewrite that last example with continue statements so that only one statement executes.</span></span>

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

<span data-ttu-id="cc798-176">3가지 항목을 모두 일치시키는 대신 첫 번째 항목을 일치시키며 switch는 다음 값으로 계속 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-176">Instead of matching all three items, the first one is matched and the switch continues to the next value.</span></span> <span data-ttu-id="cc798-177">처리할 값이 없기 때문에 switch는 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-177">Because there are no values left to process, the switch exits.</span></span> <span data-ttu-id="cc798-178">다음 예제에서는 와일드카드로 여러 항목을 일치시키는 방법을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-178">This next example is showing how a wildcard could match multiple items.</span></span>

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="cc798-179">입력 파일의 줄에 `Error`와 `Warning` 단어가 모두 포함될 수 있어 첫 번째 항목만 실행하고 파일을 계속 처리하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-179">Because a line in the input file could contain both the word `Error` and `Warning`, we only want the first one to execute and then continue processing the file.</span></span>

### <a name="break"></a><span data-ttu-id="cc798-180">중단</span><span class="sxs-lookup"><span data-stu-id="cc798-180">Break</span></span>

<span data-ttu-id="cc798-181">`break` 문은 switch를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-181">A `break` statement exits the switch.</span></span> <span data-ttu-id="cc798-182">`continue`가 단일 값에 대해 제공하는 동작과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-182">This is the same behavior that `continue` presents for single values.</span></span> <span data-ttu-id="cc798-183">차이점은 배열을 처리할 때 드러납니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-183">The difference is shown when processing an array.</span></span> <span data-ttu-id="cc798-184">`break`는 switch의 모든 처리를 중지하며 `continue`는 다음 항목으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-184">`break` stops all processing in the switch and `continue` moves onto the next item.</span></span>

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

<span data-ttu-id="cc798-185">이 경우 `Error`로 시작하는 줄에 도달하면 오류가 발생하고 switch가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-185">In this case, if we hit any lines that start with `Error` then we get an error and the switch stops.</span></span>
<span data-ttu-id="cc798-186">`break` 문이 수행하는 작업과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-186">This is what that `break` statement is doing for us.</span></span> <span data-ttu-id="cc798-187">문자열 내에 `Error`가 있고 시작 부분이 아니라면 이를 경고라고 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-187">If we find `Error` inside the string and not just at the beginning, we write it as a warning.</span></span> <span data-ttu-id="cc798-188">`Warning`에서도 같은 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-188">We do the same thing for `Warning`.</span></span> <span data-ttu-id="cc798-189">한 줄에 `Error`와 `Warning` 단어가 모두 포함될 수 있지만 하나만 처리하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-189">It's possible that a line could have both the word `Error` and `Warning`, but we only need one to process.</span></span> <span data-ttu-id="cc798-190">`continue` 문은 바로 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-190">This is what the `continue` statement is doing for us.</span></span>

### <a name="break-labels"></a><span data-ttu-id="cc798-191">Break 레이블</span><span class="sxs-lookup"><span data-stu-id="cc798-191">Break labels</span></span>

<span data-ttu-id="cc798-192">`switch` 문은 `foreach`처럼 `break/continue` 레이블을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-192">The `switch` statement supports `break/continue` labels just like `foreach`.</span></span>

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

<span data-ttu-id="cc798-193">개인적으로는 break 레이블을 사용하지 않지만 이 레이블을 처음 보신다면 혼란스러울 수 있으니 설명해드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-193">I personally don't like the use of break labels but I wanted to point them out because they're confusing if you've never seen them before.</span></span> <span data-ttu-id="cc798-194">여러 `switch`나 `foreach` 문이 중첩되어 있다면 가장 안쪽에 있는 항목 이외의 항목도 중단해야 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-194">When you have multiple `switch` or `foreach` statements that are nested, you may want to break out of more than the inner most item.</span></span> <span data-ttu-id="cc798-195">`break`의 대상이 될 수 있는 `switch`에 레이블을 배치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-195">You can place a label on a `switch` that can be the target of your `break`.</span></span>

### <a name="enum"></a><span data-ttu-id="cc798-196">열거형</span><span class="sxs-lookup"><span data-stu-id="cc798-196">Enum</span></span>

<span data-ttu-id="cc798-197">PowerShell 5.0에서 열거형이 도입되었고 이를 switch에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-197">PowerShell 5.0 gave us enums and we can use them in a switch.</span></span>

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="cc798-198">모든 항목을 강력한 형식의 열거형으로 유지하고 싶다면 괄호 안에 배치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-198">If you want to keep everything as strongly typed enums, then you can place them in parentheses.</span></span>

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

<span data-ttu-id="cc798-199">괄호가 필요한 이유는 switch가 `[Context]::Location` 값을 리터럴 문자열로 처리하면 안 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-199">The parentheses are needed here so that the switch doesn't treat the value `[Context]::Location` as a literal string.</span></span>

### <a name="scriptblock"></a><span data-ttu-id="cc798-200">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="cc798-200">ScriptBlock</span></span>

<span data-ttu-id="cc798-201">필요하다면 scriptblock을 사용하여 일치 항목 평가를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-201">We can use a scriptblock to perform the evaluation for a match if needed.</span></span>

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

<span data-ttu-id="cc798-202">이렇게 하면 더 복잡해지고 `switch`를 읽기가 어려워질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-202">This adds complexity and can make your `switch` hard to read.</span></span> <span data-ttu-id="cc798-203">이와 같은 요소를 사용하는 대부분의 경우에는 `if` 및 `elseif` 문을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-203">In most cases where you would use something like this it would be better to use `if` and `elseif` statements.</span></span> <span data-ttu-id="cc798-204">이미 많은 스위치가 있고 두 항목이 같은 평가 블록에 적중하게 해야 할 때 이것을 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-204">I would consider using this if I already had a large switch in place and I needed two items to hit the same evaluation block.</span></span>

<span data-ttu-id="cc798-205">가독성을 높일 수 있는 한 가지 방법은 scriptblock을 괄호 안에 넣는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-205">One thing that I think helps with legibility is to place the scriptblock in parentheses.</span></span>

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

<span data-ttu-id="cc798-206">같은 방식으로 실행되지만 중단된 부분을 더 명확하게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-206">It still executes the same way and gives a better visual break when quickly looking at it.</span></span>

### <a name="regex-matches"></a><span data-ttu-id="cc798-207">정규식 $matches</span><span class="sxs-lookup"><span data-stu-id="cc798-207">Regex $matches</span></span>

<span data-ttu-id="cc798-208">아직 명확하지 않은 항목을 다룰 때는 정규식을 다시 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-208">We need to revisit regex to touch on something that isn't immediately obvious.</span></span> <span data-ttu-id="cc798-209">정규식을 사용하면 `$matches` 변수가 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-209">The use of regex populates the `$matches` variable.</span></span> <span data-ttu-id="cc798-210">`$matches` 사용 방법은 [정규식을 사용하는 다양한 방법][]을 말할 때 자세하게 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-210">I do go into the use of `$matches` more when I talk about [The many ways to use regex][].</span></span> <span data-ttu-id="cc798-211">다음은 명명된 일치를 사용하여 실제로 작동하는 방식을 보여 주는 간단한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-211">Here is a quick sample to show it in action with named matches.</span></span>

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a><span data-ttu-id="cc798-212">$null</span><span class="sxs-lookup"><span data-stu-id="cc798-212">$null</span></span>

<span data-ttu-id="cc798-213">기본값이 아니어도 되는 `$null` 값을 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-213">You can match a `$null` value that doesn't have to be the default.</span></span>

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

<span data-ttu-id="cc798-214">빈 문자열에서도 마찬가집니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-214">Same goes for an empty string.</span></span>

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a><span data-ttu-id="cc798-215">상수 식</span><span class="sxs-lookup"><span data-stu-id="cc798-215">Constant expression</span></span>

<span data-ttu-id="cc798-216">Lee Dailey가 상수 `$true` 식을 사용하여 `[bool]` 항목을 평가할 수 있다고 알려주었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-216">Lee Dailey pointed out that we can use a constant `$true` expression to evaluate `[bool]` items.</span></span>
<span data-ttu-id="cc798-217">몇 가지 부울 검사를 수행해야 한다고 상상해 보세요.</span><span class="sxs-lookup"><span data-stu-id="cc798-217">Imagine if we have several boolean checks that need to happen.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

<span data-ttu-id="cc798-218">이 방법을 이용하면 쉽게 여러 부울 필드의 상태를 평가하고 조치를 취할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-218">This is a clean way to evaluate and take action on the status of several boolean fields.</span></span> <span data-ttu-id="cc798-219">이 방법의 장점은 아직 평가되지 않은 값의 상태를 한 번 일치 대칭 이동할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-219">The cool thing about this is that you can have one match flip the status of a value that hasn't been evaluated yet.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

<span data-ttu-id="cc798-220">이 예제에서 `$isEnabled`를 `$true`로 설정하면 `$isVisible`도 `$true`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-220">Setting `$isEnabled` to `$true` in this example makes sure that `$isVisible` is also set to `$true`.</span></span> <span data-ttu-id="cc798-221">그리고 `$isVisible`이 평가되면 관련 scriptblock이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-221">Then when `$isVisible` gets evaluated, its scriptblock is invoked.</span></span> <span data-ttu-id="cc798-222">직관적이진 않지만 현명한 작동 방식 활용법입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-222">This is a bit counter-intuitive but is a clever use of the mechanics.</span></span>

### <a name="switch-automatic-variable"></a><span data-ttu-id="cc798-223">$switch 자동 변수</span><span class="sxs-lookup"><span data-stu-id="cc798-223">$switch automatic variable</span></span>

<span data-ttu-id="cc798-224">`switch`는 관련 값을 처리할 때 열거자를 만들고 `$switch`라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-224">When the `switch` is processing its values, it creates an enumerator and calls it `$switch`.</span></span> <span data-ttu-id="cc798-225">이것은 PowerShell에서 자동으로 생성되는 변수이며 사용자가 직접 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-225">This is an automatic variable created by PowerShell and you can manipulate it directly.</span></span>

```powershell
$a = 1, 2, 3, 4

switch($a) {
    1 { [void]$switch.MoveNext(); $switch.Current }
    3 { [void]$switch.MoveNext(); $switch.Current }
}
```

<span data-ttu-id="cc798-226">다음과 같은 결과가 도출됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-226">This gives you the results of:</span></span>

```Output
2
4
```

<span data-ttu-id="cc798-227">열거자를 앞으로 옮기면 다음 항목은 `switch`에서 처리하지 않지만 사용자는 해당 값에 직접 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-227">By moving the enumerator forward, the next item doesn't get processed by the `switch` but you can access that value directly.</span></span> <span data-ttu-id="cc798-228">저는 이것을 광기라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-228">I would call it madness.</span></span>

## <a name="other-patterns"></a><span data-ttu-id="cc798-229">기타 패턴</span><span class="sxs-lookup"><span data-stu-id="cc798-229">Other patterns</span></span>

### <a name="hashtables"></a><span data-ttu-id="cc798-230">해시 테이블</span><span class="sxs-lookup"><span data-stu-id="cc798-230">Hashtables</span></span>

<span data-ttu-id="cc798-231">제 게시물 중 최고의 인기를 자랑하는 것은 [해시 테이블][] 관련 게시물입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-231">One of my most popular posts is the one I did on [hashtables][].</span></span> <span data-ttu-id="cc798-232">`hashtable`의 대표적인 사용 사례는 조회 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-232">One of the use cases for a `hashtable` is to be a lookup table.</span></span> <span data-ttu-id="cc798-233">`switch` 문이 자주 처리하는 일반적인 패턴에 대한 또 다른 접근 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-233">That is an alternate approach to a common pattern that a `switch` statement is often addressing.</span></span>

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

<span data-ttu-id="cc798-234">`switch`를 조회로만 사용할 때는 주로 `hashtable`를 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-234">If I'm only using a `switch` as a lookup, I often use a `hashtable` instead.</span></span>

### <a name="enum"></a><span data-ttu-id="cc798-235">열거형</span><span class="sxs-lookup"><span data-stu-id="cc798-235">Enum</span></span>

<span data-ttu-id="cc798-236">PowerShell 5.0에서 도입된 `Enum`을 이 경우에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-236">PowerShell 5.0 introduced the `Enum` and it's also an option in this case.</span></span>

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

<span data-ttu-id="cc798-237">이 문제를 해결하는 방법을 모두 살펴보려면 종일 해도 모자랄 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-237">We could go all day looking at different ways to solve this problem.</span></span> <span data-ttu-id="cc798-238">여러분에게 이러한 선택지가 있음을 알려드리고 싶을 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-238">I just wanted to make sure you knew you had options.</span></span>

## <a name="final-words"></a><span data-ttu-id="cc798-239">맺음말</span><span class="sxs-lookup"><span data-stu-id="cc798-239">Final words</span></span>

<span data-ttu-id="cc798-240">Switch 문은 겉으로 보기엔 간단하지만 대부분의 사용자는 사용할 수 있음을 알지도 못하는 고급 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-240">The switch statement is simple on the surface but it offers some advanced features that most people don't realize are available.</span></span> <span data-ttu-id="cc798-241">Switch 문은 이러한 기능을 함께 사용할 때 강력한 효과를 발휘합니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-241">Stringing those features together makes this a powerful feature.</span></span> <span data-ttu-id="cc798-242">이제까지 몰랐던 사실을 배우셨길 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="cc798-242">I hope you learned something that you had not realized before.</span></span>

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[original version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch 매개 변수]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[switch parameters]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[정규식을 사용하는 다양한 방법]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[해시 테이블]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
