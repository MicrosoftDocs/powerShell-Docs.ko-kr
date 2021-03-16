---
description: While 또는 Until 조건이 적용 되는 문 목록을 한 번 이상 실행 합니다.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 412a13669e86df5804dd74d75fcb5b4389192c79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605017"
---
# <a name="about-do"></a><span data-ttu-id="2bf0b-103">작업 정보</span><span class="sxs-lookup"><span data-stu-id="2bf0b-103">About Do</span></span>

## <a name="short-description"></a><span data-ttu-id="2bf0b-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="2bf0b-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2bf0b-105">While 또는 Until 조건이 적용 되는 문 목록을 한 번 이상 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-105">Runs a statement list one or more times, subject to a While or Until condition.</span></span>

## <a name="long-description"></a><span data-ttu-id="2bf0b-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="2bf0b-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="2bf0b-107">Do 키워드는 While 키워드 또는 Until 키워드와 함께 작동 하 여 조건에 따라 스크립트 블록에서 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-107">The Do keyword works with the While keyword or the Until keyword to run the statements in a script block, subject to a condition.</span></span> <span data-ttu-id="2bf0b-108">관련 While 루프와 달리 Do 루프의 스크립트 블록은 항상 한 번 이상 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-108">Unlike the related While loop, the script block in a Do loop always runs at least once.</span></span>

<span data-ttu-id="2bf0b-109">**Do while** 루프는 다양 한 while 루프입니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-109">A **Do-While** loop is a variety of the While loop.</span></span> <span data-ttu-id="2bf0b-110">**Do while** 루프에서 조건은 스크립트 블록이 실행 된 후 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-110">In a **Do-While** loop, the condition is evaluated after the script block has run.</span></span> <span data-ttu-id="2bf0b-111">While 루프 에서처럼 조건이 true로 평가 되는 한 스크립트 블록을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-111">As in a While loop, the script block is repeated as long as the condition evaluates to true.</span></span>

<span data-ttu-id="2bf0b-112">**Do while** **루프와** 마찬가지로 항상 조건을 평가 하기 전에 항상 한 번 이상 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-112">Like a **Do-While** loop, a **Do-Until** loop always runs at least once before the condition is evaluated.</span></span> <span data-ttu-id="2bf0b-113">그러나 스크립트 블록은 조건이 false 인 경우에만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-113">However, the script block runs only while the condition is false.</span></span>

<span data-ttu-id="2bf0b-114">*Continue* 및 *Break* Flow 제어 키워드는 **Do while** 루프 또는 **do until** 루프에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-114">The *Continue* and *Break* flow control keywords can be used in a **Do-While** loop or in a **Do-Until** loop.</span></span>

### <a name="syntax"></a><span data-ttu-id="2bf0b-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="2bf0b-115">Syntax</span></span>

<span data-ttu-id="2bf0b-116">다음은 **Do While** 문의 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-116">The following shows the syntax of the **Do-While** statement:</span></span>

```powershell
do {<statement list>} while (<condition>)
```

<span data-ttu-id="2bf0b-117">다음은 **Do Until** 문의 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-117">The following shows the syntax of the **Do-Until** statement:</span></span>

```powershell
do {<statement list>} until (<condition>)
```

<span data-ttu-id="2bf0b-118">문 목록에는 루프가 입력 되거나 반복 될 때마다 실행 되는 문이 하나 이상 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-118">The statement list contains one or more statements that run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="2bf0b-119">문의 조건 부분은 true 또는 false로 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-119">The condition portion of the statement resolves to true or false.</span></span>

### <a name="example"></a><span data-ttu-id="2bf0b-120">예제</span><span class="sxs-lookup"><span data-stu-id="2bf0b-120">Example</span></span>

<span data-ttu-id="2bf0b-121">Do 문의 다음 예제는 값이 0 인 항목에 도달할 때까지 배열의 항목 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-121">The following example of a Do statement counts the items in an array until it reaches an item with a value of 0.</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

<span data-ttu-id="2bf0b-122">다음 예에서는 Until 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-122">The following example uses the Until keyword.</span></span> <span data-ttu-id="2bf0b-123">같지 않음 연산자 ( `-ne` )는 같음 연산자 ()로 대체 됩니다 `-eq` .</span><span class="sxs-lookup"><span data-stu-id="2bf0b-123">Notice that the not equal to operator (`-ne`) is replaced by the equal to operator (`-eq`).</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

<span data-ttu-id="2bf0b-124">다음 예제에서는 0 보다 작은 값을 건너뛰어 배열의 모든 값을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="2bf0b-124">The following example writes all the values of an array, skipping any value that is less than zero.</span></span>

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a><span data-ttu-id="2bf0b-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2bf0b-125">SEE ALSO</span></span>

[<span data-ttu-id="2bf0b-126">about_While</span><span class="sxs-lookup"><span data-stu-id="2bf0b-126">about_While</span></span>](about_While.md)

[<span data-ttu-id="2bf0b-127">about_Operators</span><span class="sxs-lookup"><span data-stu-id="2bf0b-127">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="2bf0b-128">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="2bf0b-128">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="2bf0b-129">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="2bf0b-129">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="2bf0b-130">about_Break</span><span class="sxs-lookup"><span data-stu-id="2bf0b-130">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="2bf0b-131">about_Continue</span><span class="sxs-lookup"><span data-stu-id="2bf0b-131">about_Continue</span></span>](about_Continue.md)
