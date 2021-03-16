---
description: PowerShell에서 문을 연결 하는 연산자에 대해 설명 합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 8602551f3ecf74027b59715e1f47aab1b10bea92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601433"
---
# <a name="about_logical_operators"></a><span data-ttu-id="c4da0-103">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="c4da0-103">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="c4da0-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c4da0-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c4da0-105">PowerShell에서 문을 연결 하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-105">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c4da0-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="c4da0-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="c4da0-107">PowerShell 논리 연산자는 식과 문을 연결 하 여 여러 조건을 테스트할 단일 식을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-107">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="c4da0-108">예를 들어 다음 문에서는 and 연산자와 or 연산자를 사용 하 여 세 개의 조건문을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-108">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="c4da0-109">$A 값이 $b 값 보다 크고 $a 또는 $b가 보다 작은 경우에만 문은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-109">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="c4da0-110">PowerShell은 다음과 같은 논리 연산자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-110">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="c4da0-111">연산자</span><span class="sxs-lookup"><span data-stu-id="c4da0-111">Operator</span></span>|<span data-ttu-id="c4da0-112">설명</span><span class="sxs-lookup"><span data-stu-id="c4da0-112">Description</span></span>                        |<span data-ttu-id="c4da0-113">예제</span><span class="sxs-lookup"><span data-stu-id="c4da0-113">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="c4da0-114">논리 AND.</span><span class="sxs-lookup"><span data-stu-id="c4da0-114">Logical AND.</span></span> <span data-ttu-id="c4da0-115">둘 다</span><span class="sxs-lookup"><span data-stu-id="c4da0-115">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="c4da0-116">문은 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-116">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="c4da0-117">논리 OR.</span><span class="sxs-lookup"><span data-stu-id="c4da0-117">Logical OR.</span></span> <span data-ttu-id="c4da0-118">다음 중 하나에 해당 하는 경우 TRUE</span><span class="sxs-lookup"><span data-stu-id="c4da0-118">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="c4da0-119">문은 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-119">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="c4da0-120">논리적 배타적 OR입니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-120">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="c4da0-121">다음의 경우 TRUE</span><span class="sxs-lookup"><span data-stu-id="c4da0-121">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="c4da0-122">문은 하나 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-122">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="c4da0-123">논리적 not.</span><span class="sxs-lookup"><span data-stu-id="c4da0-123">Logical not.</span></span> <span data-ttu-id="c4da0-124">문을 부정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-124">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="c4da0-125">이는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-125">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="c4da0-126">`-not`과 동일</span><span class="sxs-lookup"><span data-stu-id="c4da0-126">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="c4da0-127">참고:</span><span class="sxs-lookup"><span data-stu-id="c4da0-127">Note:</span></span>

<span data-ttu-id="c4da0-128">이전 예제에서는 같음 비교 연산자를 사용 합니다 `-eq` .</span><span class="sxs-lookup"><span data-stu-id="c4da0-128">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="c4da0-129">자세한 내용은 [about_Comparison_Operators](about_Comparison_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c4da0-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="c4da0-130">또한이 예제에서는 정수의 부울 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-130">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="c4da0-131">정수 0의 값은 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-131">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="c4da0-132">다른 모든 정수의 값은 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-132">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="c4da0-133">논리 연산자의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-133">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="c4da0-134">논리 연산자를 사용 하는 문은 부울 값 (TRUE 또는 FALSE)을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-134">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="c4da0-135">PowerShell 논리 연산자는 문의 참 값을 확인 하는 데 필요한 문만 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-135">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="c4da0-136">And 연산자를 포함 하는 문의 왼쪽 피연산자가 FALSE 이면 오른쪽 피연산자가 계산 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-136">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="c4da0-137">또는 문이 포함 된 문의 왼쪽 피연산자가 TRUE 이면 오른쪽 피연산자가 계산 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4da0-137">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="c4da0-138">따라서 문을 사용 하는 것과 같은 방법으로 이러한 문을 사용할 수 있습니다 `If` .</span><span class="sxs-lookup"><span data-stu-id="c4da0-138">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4da0-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4da0-139">SEE ALSO</span></span>

[<span data-ttu-id="c4da0-140">about_Operators</span><span class="sxs-lookup"><span data-stu-id="c4da0-140">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="c4da0-141">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="c4da0-141">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="c4da0-142">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="c4da0-142">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="c4da0-143">about_If</span><span class="sxs-lookup"><span data-stu-id="c4da0-143">about_If</span></span>](about_If.md)
