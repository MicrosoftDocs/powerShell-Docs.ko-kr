---
description: 하나 이상의 조건부 테스트의 결과에 따라 문 목록을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 8b1be96167dab47e7e15e3e5b89c46126f117541
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223449"
---
# <a name="about-if"></a><span data-ttu-id="11514-104">If 정보</span><span class="sxs-lookup"><span data-stu-id="11514-104">About If</span></span>

## <a name="short-description"></a><span data-ttu-id="11514-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="11514-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="11514-106">하나 이상의 조건부 테스트의 결과에 따라 문 목록을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="11514-106">Describes a language command you can use to run statement lists based on the results of one or more conditional tests.</span></span>

## <a name="long-description"></a><span data-ttu-id="11514-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="11514-107">LONG DESCRIPTION</span></span>
<span data-ttu-id="11514-108">`If`지정 된 조건 테스트가 true로 평가 되는 경우 문을 사용 하 여 코드 블록을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-108">You can use the `If` statement to run code blocks if a specified conditional test evaluates to true.</span></span> <span data-ttu-id="11514-109">모든 이전 테스트가 false로 평가 되는 경우 실행할 하나 이상의 추가 조건부 테스트를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-109">You can also specify one or more additional conditional tests to run if all the prior tests evaluate to false.</span></span> <span data-ttu-id="11514-110">마지막으로, 다른 이전 조건 테스트가 true로 평가 되지 않으면 실행 되는 추가 코드 블록을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-110">Finally, you can specify an additional code block that is run if no other prior conditional test evaluates to true.</span></span>

### <a name="syntax"></a><span data-ttu-id="11514-111">구문</span><span class="sxs-lookup"><span data-stu-id="11514-111">Syntax</span></span>

<span data-ttu-id="11514-112">다음 예에서는 `If` 문 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11514-112">The following example shows the `If` statement syntax:</span></span>

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

<span data-ttu-id="11514-113">문을 실행 하면 `If` PowerShell은 `<test1>` 조건식을 true 또는 false로 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="11514-113">When you run an `If` statement, PowerShell evaluates the `<test1>` conditional expression as true or false.</span></span> <span data-ttu-id="11514-114">`<test1>`이 true 이면를 `<statement list 1>` 실행 하 고 PowerShell은 `If` 문을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="11514-114">If `<test1>` is true, `<statement list 1>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="11514-115">`<test1>`가 false 인 경우 PowerShell은 조건문에 지정 된 조건을 평가 합니다 `<test2>` .</span><span class="sxs-lookup"><span data-stu-id="11514-115">If `<test1>` is false, PowerShell evaluates the condition specified by the `<test2>` conditional statement.</span></span>

<span data-ttu-id="11514-116">`<test2>`이 true 이면를 `<statement list 2>` 실행 하 고 PowerShell은 `If` 문을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="11514-116">If `<test2>` is true, `<statement list 2>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="11514-117">및가 `<test1>` 모두 `<test2>` false로 평가 되 면 `<statement list 3`> 코드 블록이 실행 되 고 PowerShell에서 if 문을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="11514-117">If both `<test1>` and `<test2>` evaluate to false, the `<statement list 3`> code block runs, and PowerShell exits the If statement.</span></span>

<span data-ttu-id="11514-118">여러 Elseif 문을 사용 하 여 일련의 조건부 테스트를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-118">You can use multiple Elseif statements to chain a series of conditional tests.</span></span> <span data-ttu-id="11514-119">따라서 각 테스트는 이전 테스트가 모두 false 인 경우에만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11514-119">So, that each test is run only if all the previous tests are false.</span></span>
<span data-ttu-id="11514-120">`If`여러 Elseif 문을 포함 하는 문을 만들어야 하는 경우 Switch 문을 대신 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-120">If you need to create an `If` statement that contains many Elseif statements, consider using a Switch statement instead.</span></span>

<span data-ttu-id="11514-121">예제:</span><span class="sxs-lookup"><span data-stu-id="11514-121">Examples:</span></span>

<span data-ttu-id="11514-122">가장 간단한 `If` 문에는 단일 명령이 포함 되 고 Elseif 문이나 Else 문은 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-122">The simplest `If` statement contains a single command and does not contain any Elseif statements or any Else statements.</span></span> <span data-ttu-id="11514-123">다음 예에서는 문의 가장 간단한 형식을 보여 줍니다 `If` .</span><span class="sxs-lookup"><span data-stu-id="11514-123">The following example shows the simplest form of the `If` statement:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

<span data-ttu-id="11514-124">이 예에서는 $a 변수가 2 보다 크면 조건이 true로 평가 되 고 문 목록이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11514-124">In this example, if the $a variable is greater than 2, the condition evaluates to true, and the statement list runs.</span></span> <span data-ttu-id="11514-125">그러나 $a이 2 보다 작거나 같거나 기존 변수가 아니면 `If` 문에 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-125">However, if $a is less than or equal to 2 or is not an existing variable, the `If` statement does not display a message.</span></span>

<span data-ttu-id="11514-126">Else 문을 추가 하면 $a이 2 보다 작거나 같은 경우 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11514-126">By adding an Else statement, a message is displayed when $a is less than or equal to 2.</span></span> <span data-ttu-id="11514-127">다음 예제와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11514-127">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

<span data-ttu-id="11514-128">이 예를 추가로 구체화 하려면 $a 값이 2 인 경우 Elseif 문을 사용 하 여 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11514-128">To further refine this example, you can use the Elseif statement to display a message when the value of $a is equal to 2.</span></span> <span data-ttu-id="11514-129">다음 예제와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11514-129">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

## <a name="see-also"></a><span data-ttu-id="11514-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11514-130">SEE ALSO</span></span>

[<span data-ttu-id="11514-131">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="11514-131">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="11514-132">about_Switch</span><span class="sxs-lookup"><span data-stu-id="11514-132">about_Switch</span></span>](about_Switch.md)
