---
description: ',,,, `foreach` `for` `while` `do` `switch` 또는 `trap` 문을 즉시 종료 하는 데 사용할 수 있는 문을 설명 합니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 4dbc1a09ca4ec317c4756c65058f661ec41a513a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220761"
---
# <a name="about-break"></a><span data-ttu-id="0355d-104">중단 정보</span><span class="sxs-lookup"><span data-stu-id="0355d-104">About Break</span></span>

## <a name="short-description"></a><span data-ttu-id="0355d-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="0355d-105">Short description</span></span>

<span data-ttu-id="0355d-106">,,,, `foreach` `for` `while` `do` `switch` 또는 `trap` 문을 즉시 종료 하는 데 사용할 수 있는 문을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-106">Describes a statement you can use to immediately exit `foreach`, `for`, `while`, `do`, `switch`, or `trap` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="0355d-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-107">Long description</span></span>

<span data-ttu-id="0355d-108">`break`문은 현재 제어 블록을 종료 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-108">The `break` statement provides a way to exit the current control block.</span></span>
<span data-ttu-id="0355d-109">제어 블록 다음의 문에서 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-109">Execution continues at the next statement after the control block.</span></span> <span data-ttu-id="0355d-110">문은 레이블을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-110">The statement supports labels.</span></span> <span data-ttu-id="0355d-111">레이블은 스크립트의 문에 할당 하는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-111">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-break-in-loops"></a><span data-ttu-id="0355d-112">루프에서 중단 사용</span><span class="sxs-lookup"><span data-stu-id="0355d-112">Using break in loops</span></span>

<span data-ttu-id="0355d-113">루프 (예 `break` :,, 또는 루프)에 문이 `foreach` 나타나면 `for` PowerShell에서 `do` `while` 즉시 루프를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-113">When a `break` statement appears in a loop, such as a `foreach`, `for`, `do`, or `while` loop, PowerShell immediately exits the loop.</span></span>

<span data-ttu-id="0355d-114">`break`문에는 포함 된 루프를 종료할 수 있는 레이블이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-114">A `break` statement can include a label that lets you exit embedded loops.</span></span> <span data-ttu-id="0355d-115">레이블은 `foreach` 스크립트에서, 또는와 같은 루프 키워드를 지정할 수 있습니다 `for` `while` .</span><span class="sxs-lookup"><span data-stu-id="0355d-115">A label can specify any loop keyword, such as `foreach`, `for`, or `while`, in a script.</span></span>

<span data-ttu-id="0355d-116">다음 예에서는 문을 사용 하 여 문을 종료 하는 방법을 보여 줍니다 `break` `for` .</span><span class="sxs-lookup"><span data-stu-id="0355d-116">The following example shows how to use a `break` statement to exit a `for` statement:</span></span>

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

<span data-ttu-id="0355d-117">이 예제에서 `break` 문은 `for` `$i` 변수가 1 이면 루프를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-117">In this example, the `break` statement exits the `for` loop when the `$i` variable equals 1.</span></span> <span data-ttu-id="0355d-118">`for`문이 10 보다 클 때까지 **True** 로 평가 되는 경우에도 `$i` 루프를 처음 실행할 때 PowerShell은 break 문에 도달 합니다 `for` .</span><span class="sxs-lookup"><span data-stu-id="0355d-118">Even though the `for` statement evaluates to **True** until `$i` is greater than 10, PowerShell reaches the break statement the first time the `for` loop is run.</span></span>

<span data-ttu-id="0355d-119">`break`내부 조건이 충족 되어야 하는 루프에서 문을 사용 하는 것이 더 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-119">It is more common to use the `break` statement in a loop where an inner condition must be met.</span></span> <span data-ttu-id="0355d-120">다음 `foreach` 문 예를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="0355d-120">Consider the following `foreach` statement example:</span></span>

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

<span data-ttu-id="0355d-121">이 예제에서 `foreach` 문은 배열을 반복 합니다 `$varB` .</span><span class="sxs-lookup"><span data-stu-id="0355d-121">In this example, the `foreach` statement iterates the `$varB` array.</span></span> <span data-ttu-id="0355d-122">`if`문은 루프를 처음 두 번 실행 하 고 변수가 1 씩 증가 하는 경우 False로 평가 됩니다 `$i` .</span><span class="sxs-lookup"><span data-stu-id="0355d-122">The `if` statement evaluates to False the first two times the loop is run and the variable `$i` is incremented by 1.</span></span> <span data-ttu-id="0355d-123">루프가 실행 되는 세 번째 시간은 `$i` 2이 고 `$val` 변수는 30입니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-123">The third time the loop is run, `$i` equals 2, and the `$val` variable equals 30.</span></span> <span data-ttu-id="0355d-124">이 시점에서 `break` 문이 실행 되 고 `foreach` 루프가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-124">At this point, the `break` statement runs, and the `foreach` loop exits.</span></span>

### <a name="using-a-labeled-break-in-a-loop"></a><span data-ttu-id="0355d-125">루프에서 레이블이 지정 된 나누기 사용</span><span class="sxs-lookup"><span data-stu-id="0355d-125">Using a labeled break in a loop</span></span>

<span data-ttu-id="0355d-126">`break`문에는 레이블이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-126">A `break` statement can include a label.</span></span> <span data-ttu-id="0355d-127">키워드를 레이블과 함께 사용 하는 경우 `break` PowerShell은 현재 루프를 종료 하는 대신 레이블이 지정 된 루프를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-127">If you use the `break` keyword with a label, PowerShell exits the labeled loop instead of exiting the current loop.</span></span>
<span data-ttu-id="0355d-128">레이블은 콜론 뒤에 사용자가 할당 한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-128">The label is a colon followed by a name that you assign.</span></span> <span data-ttu-id="0355d-129">레이블은 문의 첫 번째 토큰 이어야 하며,와 같은 루핑 키워드 뒤에와 야 합니다 `while` .</span><span class="sxs-lookup"><span data-stu-id="0355d-129">The label must be the first token in a statement, and it must be followed by the looping keyword, such as `while`.</span></span>

<span data-ttu-id="0355d-130">`break` 레이블이 지정 된 루프에서 실행을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-130">`break` moves execution out of the labeled loop.</span></span> <span data-ttu-id="0355d-131">포함 된 루프에서이는 `break` 단독으로 사용 될 때 키워드와 다른 결과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-131">In embedded loops, this has a different result than the `break` keyword has when it is used by itself.</span></span> <span data-ttu-id="0355d-132">이 예제에는 `while` 문이 포함 된 문이 있습니다 `for` .</span><span class="sxs-lookup"><span data-stu-id="0355d-132">This example has a `while` statement with a `for` statement:</span></span>

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

<span data-ttu-id="0355d-133">조건 2가 **True** 로 평가 되는 경우 스크립트 실행은 레이블이 지정 된 루프 뒤의 문으로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-133">If condition 2 evaluates to **True** , the execution of the script skips down to the statement after the labeled loop.</span></span> <span data-ttu-id="0355d-134">이 예제에서는 문을 사용 하 여 실행을 다시 시작 `$a = $c` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-134">In the example, execution starts again with the statement `$a = $c`.</span></span>

<span data-ttu-id="0355d-135">다음 예제와 같이 레이블이 지정 된 여러 루프를 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-135">You can nest many labeled loops, as shown in the following example.</span></span>

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

<span data-ttu-id="0355d-136">`$b`변수가 True로 평가 되 면 "red" 라는 레이블이 지정 된 루프 다음에 스크립트 실행이 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-136">If the `$b` variable evaluates to True, execution of the script resumes after the loop that is labeled "red".</span></span> <span data-ttu-id="0355d-137">`$c`변수가 True로 평가 되 면 "노란색"으로 표시 된 루프 다음에 스크립트 컨트롤의 실행이 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-137">If the `$c` variable evaluates to True, execution of the script control resumes after the loop that is labeled "yellow".</span></span>

<span data-ttu-id="0355d-138">`$a`변수가 True로 평가 되 면 가장 안쪽의 루프 다음에 실행이 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-138">If the `$a` variable evaluates to True, execution resumes after the innermost loop.</span></span> <span data-ttu-id="0355d-139">레이블이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-139">No label is needed.</span></span>

<span data-ttu-id="0355d-140">PowerShell은 레이블 실행을 다시 시작할 수 있는 시간을 제한 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-140">PowerShell does not limit how far labels can resume execution.</span></span> <span data-ttu-id="0355d-141">레이블은 스크립트 및 함수 호출 경계에서 제어를 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-141">The label can even pass control across script and function call boundaries.</span></span>

## <a name="using-break-in-a-switch-statement"></a><span data-ttu-id="0355d-142">Switch 문에서 break 사용</span><span class="sxs-lookup"><span data-stu-id="0355d-142">Using break in a switch statement</span></span>

<span data-ttu-id="0355d-143">구문에서 `switch` PowerShell이 `break` 코드 블록을 종료 하도록 `switch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-143">In a `switch`construct, `break` causes PowerShell to exit the `switch` code block.</span></span>

<span data-ttu-id="0355d-144">`break`키워드는 구문을 종료 하는 데 사용 됩니다 `switch` .</span><span class="sxs-lookup"><span data-stu-id="0355d-144">The `break` keyword is used to leave the `switch` construct.</span></span> <span data-ttu-id="0355d-145">예를 들어 다음 `switch` 문은 문을 사용 하 여 `break` 가장 구체적인 조건을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-145">For example, the following `switch` statement uses `break` statements to test for the most specific condition:</span></span>

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

<span data-ttu-id="0355d-146">이 예에서는 변수를 `$var` 만들고 문자열 값으로 초기화 `word2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-146">In this example, the `$var` variable is created and initialized to a string value of `word2`.</span></span> <span data-ttu-id="0355d-147">`switch`문은 **Regex** 클래스를 사용 하 여 변수 값을 용어와 먼저 일치 시킵니다 `word2` .</span><span class="sxs-lookup"><span data-stu-id="0355d-147">The `switch` statement uses the **Regex** class to match the variable value first with the term `word2`.</span></span> <span data-ttu-id="0355d-148">변수 값과 문의 첫 번째 테스트가 `switch` 일치 하므로 문의 첫 번째 코드 블록이 `switch` 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-148">Because the variable value and the first test in the `switch` statement match, the first code block in the `switch` statement runs.</span></span>

<span data-ttu-id="0355d-149">PowerShell이 첫 번째 문에 도달할 때 `break` `switch` 문이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-149">When PowerShell reaches the first `break` statement, the `switch` statement exits.</span></span> <span data-ttu-id="0355d-150">이 예에서는 네 개의 `break` 문이 제거 될 경우 네 가지 조건이 모두 충족 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-150">If the four `break` statements are removed from the example, all four conditions are met.</span></span> <span data-ttu-id="0355d-151">이 예에서는 문을 사용 하 여 `break` 가장 구체적인 조건이 충족 될 때 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-151">This example uses the `break` statement to display results when the most specific condition is met.</span></span>

## <a name="using-break-in-a-trap-statement"></a><span data-ttu-id="0355d-152">Trap 문에서 break 사용</span><span class="sxs-lookup"><span data-stu-id="0355d-152">Using break in a trap statement</span></span>

<span data-ttu-id="0355d-153">문의 본문에서 실행 된 마지막 문이 `trap` 인 경우 `break` 오류 개체는 표시 되지 않고 예외가 다시 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-153">If the final statement executed in the body of a `trap` statement is `break`, the error object is suppressed and the exception is re-thrown.</span></span>

<span data-ttu-id="0355d-154">다음 예에서는 문을 사용 하 여 트랩 된 **DivideByZeroException** 예외를 만듭니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="0355d-154">The following example create a **DivideByZeroException** exception that is trapped using the `trap` statement.</span></span>

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

예외가 발생 하면 실행이 중지 됩니다. <span data-ttu-id="0355d-156">에 `After loop` 도달 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-156">The `After loop` is never reached.</span></span>
<span data-ttu-id="0355d-157">가 실행 된 후 예외가 다시 throw 됩니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="0355d-157">The exception is re-thrown after the `trap` executes.</span></span>

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
ParentContainsErrorRecordException:
Line |
  10 |       "1 / $i = " + (1 / $i--)
     |       ~~~~~~~~~~~~~~~~~~~~~~~~
     | Attempted to divide by zero.
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="0355d-158">루프, 스위치 또는 트랩 외부에서 break를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="0355d-158">Do not use break outside of a loop, switch, or trap</span></span>

<span data-ttu-id="0355d-159">를 `break` 직접 지 원하는 구문 외부에서 사용 하는 경우 (루프, `switch` , `trap` ) PowerShell에서 바깥쪽 구문에 대 한 _호출 스택을_ 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-159">When `break` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="0355d-160">바깥쪽 구문을 찾을 수 없는 경우 현재 runspace가 자동으로 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-160">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="0355d-161">즉, 실수로를 지 원하는 바깥쪽 구문 외부에서를 사용 하는 함수 및 스크립트는 `break` 실수로 _호출자_ 를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-161">This means that functions and scripts that inadvertently use a `break` outside of an enclosing construct that supports it can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="0355d-162">`break`스크립트 블록과 같은 파이프라인 내에서를 사용 하면 `break` `ForEach-Object` 파이프라인이 종료 될 뿐만 아니라 전체 runspace가 종료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0355d-162">Using `break` inside a pipeline `break`, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="0355d-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0355d-163">See also</span></span>

[<span data-ttu-id="0355d-164">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="0355d-164">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="0355d-165">about_Continue</span><span class="sxs-lookup"><span data-stu-id="0355d-165">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="0355d-166">about_For</span><span class="sxs-lookup"><span data-stu-id="0355d-166">about_For</span></span>](about_For.md)

[<span data-ttu-id="0355d-167">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="0355d-167">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="0355d-168">about_Switch</span><span class="sxs-lookup"><span data-stu-id="0355d-168">about_Switch</span></span>](about_Switch.md)

[<span data-ttu-id="0355d-169">about_Throw</span><span class="sxs-lookup"><span data-stu-id="0355d-169">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="0355d-170">about_Trap</span><span class="sxs-lookup"><span data-stu-id="0355d-170">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="0355d-171">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="0355d-171">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

[<span data-ttu-id="0355d-172">about_While</span><span class="sxs-lookup"><span data-stu-id="0355d-172">about_While</span></span>](about_While.md)
