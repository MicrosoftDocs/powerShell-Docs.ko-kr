---
title: 문자열의 변수 대체에 대해 알고 싶은 모든 것
description: 문자열에서 다양한 방법으로 변수를 사용하여 서식 있는 텍스트를 만들 수 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 786526fb98dbf1b3ec7c5c6c985ac95b85a96259
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "86301321"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a><span data-ttu-id="0103d-103">문자열의 변수 대체에 대해 알고 싶은 모든 것</span><span class="sxs-lookup"><span data-stu-id="0103d-103">Everything you wanted to know about variable substitution in strings</span></span>

<span data-ttu-id="0103d-104">문자열에서는 다양한 방법으로 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-104">There are many ways to use variables in strings.</span></span> <span data-ttu-id="0103d-105">지금은 이 변수 대체를 호출하지만 변수의 값을 포함하도록 문자열의 서식을 지정하고 싶다면 언제든 참조할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-105">I'm calling this variable substitution but I'm referring to any time you want to format a string to include values from variables.</span></span> <span data-ttu-id="0103d-106">이것은 신입 스크립터에게 자주 설명하는 내용이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-106">This is something that I often find myself explaining to new scripters.</span></span>

> [!NOTE]
> <span data-ttu-id="0103d-107">이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="0103d-108">PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="0103d-109">[PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0103d-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="concatenation"></a><span data-ttu-id="0103d-110">연결</span><span class="sxs-lookup"><span data-stu-id="0103d-110">Concatenation</span></span>

<span data-ttu-id="0103d-111">메서드의 첫 번째 클래스를 연결이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-111">The first class of methods can be referred to as concatenation.</span></span> <span data-ttu-id="0103d-112">기본적으로 여러 문자열을 가져와 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-112">It's basically taking several strings and joining them together.</span></span> <span data-ttu-id="0103d-113">연결은 아주 오랫동안 서식이 지정된 문자열을 작성하는 용도로 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-113">There's a long history of using concatenation to build formatted strings.</span></span>

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

<span data-ttu-id="0103d-114">추가할 값이 몇 개 없어도 연결은 정상적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-114">Concatenation works out OK when there are only a few values to add.</span></span> <span data-ttu-id="0103d-115">하지만 이렇게 되면 머지않아 복잡해질 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-115">But this can get complicated quickly.</span></span>

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

<span data-ttu-id="0103d-116">이 간단한 예제조차 벌써 읽기가 어려워졌습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-116">This simple example is already getting harder to read.</span></span>

## <a name="variable-substitution"></a><span data-ttu-id="0103d-117">변수 대체</span><span class="sxs-lookup"><span data-stu-id="0103d-117">Variable substitution</span></span>

<span data-ttu-id="0103d-118">PowerShell에는 쉽게 읽을 수 있는 다른 선택지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-118">PowerShell has another option that is easier.</span></span> <span data-ttu-id="0103d-119">문자열에서 변수를 직접 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-119">You can specify your variables directly in the strings.</span></span>

```powershell
$message = "Hello, $first $last."
```

<span data-ttu-id="0103d-120">문자열 앞뒤에 사용하는 따옴표 유형에 따라 결과가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-120">The type of quotes you use around the string makes a difference.</span></span> <span data-ttu-id="0103d-121">큰따옴표로 묶은 문자열은 대체를 허용하지만 따옴표로 묶은 단일 문자열은 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-121">A double quoted string allows the substitution but a single quoted string doesn't.</span></span> <span data-ttu-id="0103d-122">상황에 맞는 적합한 방법을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-122">There are times you want one or the other so you have an option.</span></span>

## <a name="command-substitution"></a><span data-ttu-id="0103d-123">명령 대체</span><span class="sxs-lookup"><span data-stu-id="0103d-123">Command substitution</span></span>

<span data-ttu-id="0103d-124">속성 값을 문자열로 가져오는 작업을 시작하면 상황이 좀 더 복잡해집니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-124">Things get a little tricky when you start trying to get the values of properties into a string.</span></span> <span data-ttu-id="0103d-125">많은 초보자가 실수하는 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-125">This is where many new people get tripped up.</span></span> <span data-ttu-id="0103d-126">먼저 초보자가 생각하는 작동 방식을 보여드리겠습니다(실제로도 정상적으로 작동하는 것처럼 보일 것입니다).</span><span class="sxs-lookup"><span data-stu-id="0103d-126">First let me show you what they think should work (and at face value almost looks like it should).</span></span>

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

<span data-ttu-id="0103d-127">`$directory`에서 `CreationTime`을 가져와야 할 것 같지만 실제로는 이 `Time: c:\windows.CreationTime`을 값으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-127">You would be expecting to get the `CreationTime` off of the `$directory`, but instead you get this `Time: c:\windows.CreationTime` as your value.</span></span> <span data-ttu-id="0103d-128">이 유형의 대체는 기본 변수만 확인하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-128">The reason is that this type of substitution only sees the base variable.</span></span> <span data-ttu-id="0103d-129">마침표를 문자열의 일부로 간주하기 때문에 더 깊은 값의 확인을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-129">It considers the period as part of the string so it stops resolving the value any deeper.</span></span>

<span data-ttu-id="0103d-130">이 개체는 문자열에 배치될 때 문자열을 기본값으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-130">It just so happens that this object gives a string as a default value when placed into a string.</span></span>
<span data-ttu-id="0103d-131">일부 개체는 대신 `System.Collections.Hashtable` 같은 형식 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-131">Some objects give you the type name instead like `System.Collections.Hashtable`.</span></span> <span data-ttu-id="0103d-132">주의해야 할 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-132">Just something to watch for.</span></span>

<span data-ttu-id="0103d-133">PowerShell을 사용하면 특수 구문을 사용하여 문자열 내에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-133">PowerShell allows you to do command execution inside the string with a special syntax.</span></span> <span data-ttu-id="0103d-134">이렇게 하면 이러한 개체의 속성을 가져오고 다른 명령을 실행하여 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-134">This allows us to get the properties of these objects and run any other command to get a value.</span></span>

```powershell
$message = "Time: $($directory.CreationTime)"
```

<span data-ttu-id="0103d-135">일부 상황에서는 유용하지만 변수가 몇 개 없다면 연결을 이용할 때만큼 복잡해질 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-135">This works great for some situations but it can get just as crazy as concatenation if you have just a few variables.</span></span>

### <a name="command-execution"></a><span data-ttu-id="0103d-136">명령 실행</span><span class="sxs-lookup"><span data-stu-id="0103d-136">Command execution</span></span>

<span data-ttu-id="0103d-137">문자열 내에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-137">You can run commands inside a string.</span></span> <span data-ttu-id="0103d-138">저도 이 옵션을 이용할 수 있지만 좋아하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-138">Even though I have this option, I don't like it.</span></span> <span data-ttu-id="0103d-139">식간에 복잡해지고 디버그하기도 어렵기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-139">It gets cluttered quickly and hard to debug.</span></span> <span data-ttu-id="0103d-140">명령을 실행하여 변수에 저장하거나 서식 문자열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-140">I either run the command and save to a variable or use a format string.</span></span>

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a><span data-ttu-id="0103d-141">형식 문자열</span><span class="sxs-lookup"><span data-stu-id="0103d-141">Format string</span></span>

<span data-ttu-id="0103d-142">.NET에서는 대단히 쉬운 방식으로 문자열의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-142">.NET has a way to format strings that I find fairly easy to work with.</span></span> <span data-ttu-id="0103d-143">먼저 이를 위한 정적 메서드를 보여드린 다음 같은 작업을 수행하는 PowerShell 단축 방법을 보여드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-143">First let me show you the static method for it before I show you the PowerShell shortcut to do the same thing.</span></span>

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

<span data-ttu-id="0103d-144">여기서는 `{0}` 및 `{1}` 토큰에 대해 문자열을 구문 분석한 다음 이 숫자를 사용하여 제공된 값 중에서 적절한 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-144">What is happening here is that the string is parsed for the tokens `{0}` and `{1}`, then it uses that number to pick from the values provided.</span></span> <span data-ttu-id="0103d-145">문자열의 특정 위치에서 같은 값을 반복하고 싶다면 해당 값을 다시 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-145">If you want to repeat one value some place in the string, you can reuse that values number.</span></span>

<span data-ttu-id="0103d-146">이 접근법은 문자열이 복잡할수록 더 많은 값을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-146">The more complicated the string gets, the more value you get out of this approach.</span></span>

### <a name="format-values-as-arrays"></a><span data-ttu-id="0103d-147">값을 배열로 형식 지정</span><span class="sxs-lookup"><span data-stu-id="0103d-147">Format values as arrays</span></span>

<span data-ttu-id="0103d-148">형식 줄이 너무 길면 먼저 배열에 값을 입력해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-148">If your format line gets too long, you can place your values into an array first.</span></span>

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

<span data-ttu-id="0103d-149">전체 배열을 전달하므로 스플래팅 작업은 아니지만 개념은 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-149">This is not splatting because I'm passing the whole array in, but the idea is similar.</span></span>

## <a name="advanced-formatting"></a><span data-ttu-id="0103d-150">고급 서식 지정</span><span class="sxs-lookup"><span data-stu-id="0103d-150">Advanced formatting</span></span>

<span data-ttu-id="0103d-151">의도적으로 이들을 .NET에서 호출했는데, 이미 수많은 서식 지정 옵션이 [문서화][]되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-151">I intentionally called these out as coming from .NET because there are lots of formatting options already well [documented][] on it.</span></span> <span data-ttu-id="0103d-152">다양한 데이터 형식의 서식을 지정하는 기본 제공 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-152">There are built in ways to format various data types.</span></span>

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

<span data-ttu-id="0103d-153">여기서 살펴보지는 않겠지만 필요하다면 대단히 강력한 서식 지정 엔진으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-153">I'm not going to go into them but I just wanted to let you know that this is a very powerful formatting engine if you need it.</span></span>

## <a name="joining-strings"></a><span data-ttu-id="0103d-154">문자열 조인</span><span class="sxs-lookup"><span data-stu-id="0103d-154">Joining strings</span></span>

<span data-ttu-id="0103d-155">값 목록을 함께 연결해야 할 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-155">Sometimes you actually do want to concatenate a list of values together.</span></span> <span data-ttu-id="0103d-156">이 작업은 `-join` 연산자로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-156">There's a `-join` operator that can do that for you.</span></span> <span data-ttu-id="0103d-157">문자열 사이에 조인할 문자를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-157">It even lets you specify a character to join between the strings.</span></span>

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

<span data-ttu-id="0103d-158">구분 기호 없이 일부 문자열을 `-join`하려면 빈 문자열 `''`를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-158">If you want to `-join` some strings without a separator, you need to specify an empty string `''`.</span></span>
<span data-ttu-id="0103d-159">하지만 이 작업만 해야 한다면 더 빠른 선택지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-159">But if that is all you need, there's a faster option.</span></span>

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

<span data-ttu-id="0103d-160">`-split` 문자열을 사용할 수 있다는 사실도 알면 도움이 될 겁니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-160">It's also worth pointing out that you can also `-split` strings too.</span></span>

## <a name="join-path"></a><span data-ttu-id="0103d-161">Join-Path</span><span class="sxs-lookup"><span data-stu-id="0103d-161">Join-Path</span></span>

<span data-ttu-id="0103d-162">자주 간과되지만 파일 경로를 빌드할 때 아주 유용한 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-162">This is often overlooked but a great cmdlet for building a file path.</span></span>

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

<span data-ttu-id="0103d-163">장점은 여러 값을 함께 넣어도 백슬래시가 올바르게 작동한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-163">The great thing about this is it works out the backslashes correctly when it puts the values together.</span></span> <span data-ttu-id="0103d-164">사용자나 구성 파일에서 값을 가져올 때는 이 사실이 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-164">This is especially important if you are taking values from users or config files.</span></span>

<span data-ttu-id="0103d-165">`Split-Path` 및 `Test-Path`에서도 아주 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-165">This also goes well with `Split-Path` and `Test-Path`.</span></span> <span data-ttu-id="0103d-166">[파일 읽기 및 쓰기][]에 관한 제 포스트에서도 관련 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-166">I also cover these in my post about [reading and saving to files][].</span></span>

## <a name="strings-are-arrays"></a><span data-ttu-id="0103d-167">문자열은 배열입니다</span><span class="sxs-lookup"><span data-stu-id="0103d-167">Strings are arrays</span></span>

<span data-ttu-id="0103d-168">계속하기 전에 문자열 추가를 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-168">I do need to mention adding strings here before I go on.</span></span> <span data-ttu-id="0103d-169">문자열은 단순한 문자 배열임을 잊지 마세요.</span><span class="sxs-lookup"><span data-stu-id="0103d-169">Remember that a string is just an array of characters.</span></span> <span data-ttu-id="0103d-170">여러 문자열을 함께 추가하면 매번 새 배열이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-170">When you add multiple strings together, a new array is created each time.</span></span>

<span data-ttu-id="0103d-171">이 예제를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0103d-171">Look at this example:</span></span>

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

<span data-ttu-id="0103d-172">아주 기본적인 작업 같지만 문자열을 `$message`에 추가할 때마다 완전히 새로운 문자열이 생성된다는 사실은 모르셨을 겁니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-172">It looks very basic but what you don't see is that each time a string is added to `$message` that a whole new string is created.</span></span> <span data-ttu-id="0103d-173">메모리를 할당하고 데이터를 복사한 다음 이전 데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-173">Memory gets allocated, data gets copied and the old one is discarded.</span></span>
<span data-ttu-id="0103d-174">몇 번만 수행할 때는 큰 문제가 아니지만 이런 식의 루프는 문제를 유발합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-174">Not a big deal when it's only done a few times, but a loop like this would really expose the issue.</span></span>

### <a name="stringbuilder"></a><span data-ttu-id="0103d-175">StringBuilder</span><span class="sxs-lookup"><span data-stu-id="0103d-175">StringBuilder</span></span>

<span data-ttu-id="0103d-176">StringBuilder는 수많은 작은 문자열로 큰 문자열을 작성하는 용도로도 자주 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-176">StringBuilder is also very popular for building large strings from lots of smaller strings.</span></span> <span data-ttu-id="0103d-177">사용자가 추가한 문자열만 수집하며 사용자가 값을 검색할 때만 모든 문자열을 연결하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-177">The reason why is because it just collects all the strings you add to it and only concatenates all of them at the end when you retrieve the value.</span></span>

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

<span data-ttu-id="0103d-178">이 역시 .NET에서 사용하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-178">Again, this is something that I'm reaching out to .NET for.</span></span> <span data-ttu-id="0103d-179">개인적으로 지금은 잘 사용하지 않지만 알고 있으면 도움이 될 겁니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-179">I don't use it often anymore but it's good to know it's there.</span></span>

## <a name="delineation-with-braces"></a><span data-ttu-id="0103d-180">중괄호를 이용한 경계 지정</span><span class="sxs-lookup"><span data-stu-id="0103d-180">Delineation with braces</span></span>

<span data-ttu-id="0103d-181">문자열 내에서 접미사를 연결할 때 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-181">This is used for suffix concatenation within the string.</span></span> <span data-ttu-id="0103d-182">변수에 명확한 단어 경계가 없을 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-182">Sometimes your variable doesn't have a clean word boundary.</span></span>

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

<span data-ttu-id="0103d-183">이 사실을 알려 주신 [/u/real_parbold][] 님께 감사드립니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-183">Thank you [/u/real_parbold][] for that one.</span></span>

<span data-ttu-id="0103d-184">다음 방법을 사용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-184">Here is an alternate to this approach:</span></span>

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

<span data-ttu-id="0103d-185">개인적으로는 서식 문자열을 사용하지만 알고 있으면 실제 현장에서 도움이 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-185">I personally use format string for this, but this is good to know incase you see it in the wild.</span></span>

## <a name="find-and-replace-tokens"></a><span data-ttu-id="0103d-186">토큰 찾기 및 바꾸기</span><span class="sxs-lookup"><span data-stu-id="0103d-186">Find and replace tokens</span></span>

<span data-ttu-id="0103d-187">이러한 기능 대부분은 자체 솔루션을 마련할 필요가 없게 하지만, 많은 템플릿 파일에서 내부 문자열을 바꿔야 할 때도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-187">While most of these features limit your need to roll your own solution, there are times where you may have large template files where you want to replace strings inside.</span></span>

<span data-ttu-id="0103d-188">많은 텍스트가 있는 파일에서 템플릿을 끌어낸다고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-188">Let us assume you pulled in a template from a file that has a lot of text.</span></span>

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

<span data-ttu-id="0103d-189">많은 토큰을 교체해야 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-189">You may have lots of tokens to replace.</span></span> <span data-ttu-id="0103d-190">여기서 중요한 점은 쉽게 찾고 바꿀 수 있는 고유한 토큰을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-190">The trick is to use a very distinct token that is easy to find and replace.</span></span> <span data-ttu-id="0103d-191">쉽게 구분할 수 있도록 양쪽 끝에 특수 문자를 사용하곤 합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-191">I tend to use a special character at both ends to help distinguish it.</span></span>

<span data-ttu-id="0103d-192">하지만 얼마 전 새로운 방법을 알게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-192">I recently found a new way to approach this.</span></span> <span data-ttu-id="0103d-193">자주 사용하는 패턴이므로 이 부분은 여기에 남겨 놓기로 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-193">I decided to leave this section in here because this is a pattern that is commonly used.</span></span>

### <a name="replace-multiple-tokens"></a><span data-ttu-id="0103d-194">여러 토큰 바꾸기</span><span class="sxs-lookup"><span data-stu-id="0103d-194">Replace multiple tokens</span></span>

<span data-ttu-id="0103d-195">토큰 목록을 바꾸고 싶을 때 일반적인 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-195">When I have a list of tokens that I need to replace, I take a more generic approach.</span></span> <span data-ttu-id="0103d-196">해시 테이블 안에 배치한 다음 반복 실행하여 바꾸기 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-196">I would place them in a hashtable and iterate over them to do the replace.</span></span>

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

<span data-ttu-id="0103d-197">이러한 토큰은 필요하다면 JSON 또는 CSV에서 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-197">Those tokens could be loaded from JSON or CSV if needed.</span></span>

### <a name="executioncontext-expandstring"></a><span data-ttu-id="0103d-198">ExecutionContext ExpandString</span><span class="sxs-lookup"><span data-stu-id="0103d-198">ExecutionContext ExpandString</span></span>

<span data-ttu-id="0103d-199">작은따옴표를 사용하여 대체 문자열을 정의하고 나중에 변수를 확장한다는 기발한 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-199">There's a clever way to define a substitution string with single quotes and expand the variables later.</span></span> <span data-ttu-id="0103d-200">이 예제를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0103d-200">Look at this example:</span></span>

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

<span data-ttu-id="0103d-201">현재 실행 컨텍스트에 대한 `.InvokeCommand.ExpandString` 호출은 현재 범위에 속하는 변수를 대체에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-201">The call to `.InvokeCommand.ExpandString` on the current execution context uses the variables in the current scope for substitution.</span></span> <span data-ttu-id="0103d-202">여기서 중요한 점은 `$message`는 아주 초기에, 심지어 변수가 존재하기 전에도 정의할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-202">The key thing here is that the `$message` can be defined very early before the variables even exist.</span></span>

<span data-ttu-id="0103d-203">조금만 확장하면 다른 값을 이용해 이 대체를 반복 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-203">If we expand on that just a little bit, we can perform this substitution over and over wih different values.</span></span>

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

<span data-ttu-id="0103d-204">이 작업을 하려면 텍스트 파일에서 대형 이메일 템플릿을 가져오면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-204">To keep going on this idea; you could be importing a large email template from a text file to do this.</span></span> <span data-ttu-id="0103d-205">이 [제안][]을 해 준 [Mark Kraus][]에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-205">I have to thank [Mark Kraus][] for this [suggestion][].</span></span>

## <a name="whatever-works-the-best-for-you"></a><span data-ttu-id="0103d-206">자신의 가장 적합한 작업</span><span class="sxs-lookup"><span data-stu-id="0103d-206">Whatever works the best for you</span></span>

<span data-ttu-id="0103d-207">저는 서식 문자열 방법을 정말 좋아합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-207">I'm a fan of the format string approach.</span></span> <span data-ttu-id="0103d-208">문자열이 복잡하거나 여러 변수가 있을 때 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-208">I definitely do this with the more complicated strings or if there are multiple variables.</span></span> <span data-ttu-id="0103d-209">아주 짧은 요소에는 다음 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-209">On anything that is very short, I may use any one of these.</span></span>

## <a name="anything-else"></a><span data-ttu-id="0103d-210">다른 내용을 알고 싶으신가요?</span><span class="sxs-lookup"><span data-stu-id="0103d-210">Anything else?</span></span>

<span data-ttu-id="0103d-211">지금까지 많은 내용을 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-211">I covered a lot of ground on this one.</span></span> <span data-ttu-id="0103d-212">이제 새로운 내용을 배워 보시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="0103d-212">My hope is that you walk away learning something new.</span></span>

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[original version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[제안]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[suggestion]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[파일 읽기 및 쓰기]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[reading and saving to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[문서화]: /dotnet/api/system.string.format#overloads
[documented]: /dotnet/api/system.string.format#overloads
