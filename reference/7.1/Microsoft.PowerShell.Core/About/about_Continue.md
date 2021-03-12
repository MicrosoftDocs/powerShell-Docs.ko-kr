---
description: '`continue`문이 프로그램 루프, `switch` 문 또는 문 맨 위에 프로그램 흐름을 즉시 반환 하는 방법에 대해 설명 합니다 `trap` .'
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 5a4ec2713ceed6d60cbca48b3795b4236c65ba88
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195914"
---
# <a name="about-continue"></a><span data-ttu-id="c8a61-103">계속 정보</span><span class="sxs-lookup"><span data-stu-id="c8a61-103">About Continue</span></span>

## <a name="short-description"></a><span data-ttu-id="c8a61-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c8a61-104">Short description</span></span>

<span data-ttu-id="c8a61-105">`continue`문이 프로그램 루프, `switch` 문 또는 문 맨 위에 프로그램 흐름을 즉시 반환 하는 방법에 대해 설명 합니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="c8a61-105">Describes how the `continue` statement immediately returns the program flow to the top of a program loop, a `switch` statement, or a `trap` statement.</span></span>

## <a name="long-description"></a><span data-ttu-id="c8a61-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-106">Long description</span></span>

<span data-ttu-id="c8a61-107">`continue`문은 완전히 종료 하는 대신 현재 제어 블록을 끝내는 방법을 제공 하지만 실행을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-107">The `continue` statement provides a way to exit the current control block but continue execution, rather than exit completely.</span></span> <span data-ttu-id="c8a61-108">문은 레이블을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-108">The statement supports labels.</span></span>
<span data-ttu-id="c8a61-109">레이블은 스크립트의 문에 할당 하는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-109">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-continue-in-loops"></a><span data-ttu-id="c8a61-110">루프에서 계속 사용</span><span class="sxs-lookup"><span data-stu-id="c8a61-110">Using continue in loops</span></span>

<span data-ttu-id="c8a61-111">레이블 없는 `continue` 문은 즉시 프로그램 흐름을 `for` ,, `foreach` `do` 또는 문에 의해 제어 되는 가장 안쪽 루프의 맨 위로 반환 합니다 `while` .</span><span class="sxs-lookup"><span data-stu-id="c8a61-111">An unlabeled `continue` statement immediately returns the program flow to the top of the innermost loop that is controlled by a `for`, `foreach`, `do`, or `while` statement.</span></span> <span data-ttu-id="c8a61-112">루프의 현재 반복이 종료 되 고 루프는 다음 반복에서 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-112">The current iteration of the loop is terminated and the loop continues with the next iteration.</span></span>

<span data-ttu-id="c8a61-113">다음 예제에서 프로그램 흐름은 `while` `$ctr` 변수가 5와 같은 경우 루프의 맨 위로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-113">In the following example, program flow returns to the top of the `while` loop if the `$ctr` variable is equal to 5.</span></span> <span data-ttu-id="c8a61-114">따라서 5를 제외 하 고 1과 10 사이의 모든 숫자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-114">As a result, all the numbers between 1 and 10 are displayed except for 5:</span></span>

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

<span data-ttu-id="c8a61-115">루프를 사용 하는 경우 `for` 문에서 실행이 계속 되 고 `<Repeat>` 그 다음에 `<Condition>` 테스트가 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-115">When using a `for` loop, execution continues at the `<Repeat>` statement, followed by the `<Condition>` test.</span></span> <span data-ttu-id="c8a61-116">아래 예제에서는가 키워드 다음에 감소 하는 경우 무한 루프가 발생 하지 않습니다 `$i` `continue` .</span><span class="sxs-lookup"><span data-stu-id="c8a61-116">In the example below, an infinite loop will not occur because the decrement of `$i` occurs after the `continue` keyword.</span></span>

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a><span data-ttu-id="c8a61-117">루프에서 레이블이 지정 된 continue 사용</span><span class="sxs-lookup"><span data-stu-id="c8a61-117">Using a labeled continue in a loop</span></span>

<span data-ttu-id="c8a61-118">레이블이 지정 된 `continue` 문은 반복의 실행을 종료 하 고 대상으로 지정 된 포함 반복 또는 문 레이블로 제어를 전달 합니다 `switch` .</span><span class="sxs-lookup"><span data-stu-id="c8a61-118">A labeled `continue` statement terminates execution of the iteration and transfers control to the targeted enclosing iteration or `switch` statement label.</span></span>

<span data-ttu-id="c8a61-119">다음 예제에서는 `for` `$condition` 가 **True** 이 고에서 두 번째 루프를 사용 하 여 반복이 계속 되 면 가장 안쪽이 종료 됩니다 `for` `labelB` .</span><span class="sxs-lookup"><span data-stu-id="c8a61-119">In the following example, the innermost `for` is terminated when `$condition` is **True** and iteration continues with the second `for` loop at `labelB`.</span></span>

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a><span data-ttu-id="c8a61-120">Switch 문에서 continue 사용</span><span class="sxs-lookup"><span data-stu-id="c8a61-120">Using continue in a switch statement</span></span>

<span data-ttu-id="c8a61-121">`continue`내에서 레이블이 없는 문은 `switch` 현재 반복의 실행을 종료 하 `switch` 고 컨트롤을의 위쪽으로 전달 `switch` 하 여 다음 입력 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-121">An unlabeled `continue` statement within a `switch` terminates execution of the current `switch` iteration and transfers control to the top of the `switch` to get the next input item.</span></span>

<span data-ttu-id="c8a61-122">단일 입력 항목이 있으면 `continue` 전체 `switch` 문을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-122">When there is a single input item `continue` exits the entire `switch` statement.</span></span>
<span data-ttu-id="c8a61-123">`switch`입력이 컬렉션인 경우는 `switch` 컬렉션의 각 요소를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-123">When the `switch` input is a collection, the `switch` tests each element of the collection.</span></span> <span data-ttu-id="c8a61-124">는 `continue` 현재 반복을 종료 하 고는 `switch` 다음 요소를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-124">The `continue` exits the current iteration and the `switch` continues with the next element.</span></span>

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a><span data-ttu-id="c8a61-125">Trap 문에서 continue 사용</span><span class="sxs-lookup"><span data-stu-id="c8a61-125">Using continue in a trap statement</span></span>

<span data-ttu-id="c8a61-126">본문에서 실행 된 마지막 문이 `trap` 인 경우 `continue` 트랩 된 오류는 자동으로 무시 되 고 발생 한 원인이 되는 문 바로 다음의 문을 사용 하 여 실행이 계속 됩니다 `trap` .</span><span class="sxs-lookup"><span data-stu-id="c8a61-126">If the final statement executed in the body a `trap` statement is `continue`, the trapped error is silently ignored and execution continues with the statement immediately following the one that caused `trap` to occur.</span></span>

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="c8a61-127">루프, 스위치 또는 트랩 외부에서 계속 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="c8a61-127">Do not use continue outside of a loop, switch, or trap</span></span>

<span data-ttu-id="c8a61-128">를 `continue` 직접 지 원하는 구문 외부에서 사용 하는 경우 (루프, `switch` , `trap` ) PowerShell에서 바깥쪽 구문에 대 한 _호출 스택을_ 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-128">When `continue` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="c8a61-129">바깥쪽 구문을 찾을 수 없는 경우 현재 runspace가 자동으로 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-129">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="c8a61-130">즉, 실수로이를 지 원하는 바깥쪽 구문 외부에서를 사용 하는 함수 및 스크립트는 `continue` 실수로 _호출자_ 를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-130">This means that functions and scripts that inadvertently use a `continue` outside of an enclosing construct that supports it, can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="c8a61-131">`continue`스크립트 블록과 같은 파이프라인 내에서를 사용 하면 `ForEach-Object` 파이프라인이 종료 될 뿐만 아니라 전체 runspace가 종료 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8a61-131">Using `continue` inside a pipeline, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8a61-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8a61-132">See also</span></span>

[<span data-ttu-id="c8a61-133">about_Break</span><span class="sxs-lookup"><span data-stu-id="c8a61-133">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="c8a61-134">about_For</span><span class="sxs-lookup"><span data-stu-id="c8a61-134">about_For</span></span>](about_For.md)

[<span data-ttu-id="c8a61-135">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="c8a61-135">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="c8a61-136">about_Throw</span><span class="sxs-lookup"><span data-stu-id="c8a61-136">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="c8a61-137">about_Trap</span><span class="sxs-lookup"><span data-stu-id="c8a61-137">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="c8a61-138">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="c8a61-138">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
