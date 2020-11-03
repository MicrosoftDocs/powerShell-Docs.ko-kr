---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: 0d9101c751e9ebc0b0c6fe80564bb76524de8bb6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93209826"
---
# <span data-ttu-id="58b10-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-103">Where-Object</span></span>

## <span data-ttu-id="58b10-104">개요</span><span class="sxs-lookup"><span data-stu-id="58b10-104">SYNOPSIS</span></span>
<span data-ttu-id="58b10-105">속성 값에 따라 컬렉션에서 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="58b10-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="58b10-106">SYNTAX</span></span>

### <span data-ttu-id="58b10-107">EqualSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="58b10-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="58b10-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="58b10-109">MatchSet</span><span class="sxs-lookup"><span data-stu-id="58b10-109">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="58b10-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="58b10-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="58b10-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="58b10-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="58b10-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="58b10-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="58b10-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="58b10-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-118">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="58b10-118">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-119">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="58b10-119">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-120">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="58b10-120">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-121">LikeSet</span><span class="sxs-lookup"><span data-stu-id="58b10-121">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-122">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="58b10-122">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-123">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="58b10-123">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-124">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="58b10-124">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="58b10-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="58b10-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="58b10-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-128">ContainsSet</span><span class="sxs-lookup"><span data-stu-id="58b10-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="58b10-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="58b10-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="58b10-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-132">오목</span><span class="sxs-lookup"><span data-stu-id="58b10-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="58b10-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="58b10-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="58b10-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="58b10-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="58b10-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### <span data-ttu-id="58b10-138">Not</span><span class="sxs-lookup"><span data-stu-id="58b10-138">Not</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## <span data-ttu-id="58b10-139">설명</span><span class="sxs-lookup"><span data-stu-id="58b10-139">DESCRIPTION</span></span>

<span data-ttu-id="58b10-140">`Where-Object`Cmdlet은 전달 되는 개체의 컬렉션에서 특정 속성 값이 있는 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-140">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="58b10-141">예를 들어 cmdlet을 사용 하 여 특정 `Where-Object` 날짜 이후에 만들어진 파일, 특정 ID를 가진 이벤트 또는 특정 버전의 Windows를 사용 하는 컴퓨터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-141">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="58b10-142">Windows PowerShell 3.0부터 명령을 생성 하는 방법에는 두 가지가 있습니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="58b10-142">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="58b10-143">**스크립트 블록** 입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-143">**Script block** .</span></span> <span data-ttu-id="58b10-144">스크립트 블록을 사용하여 속성 이름, 비교 연산자 및 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-144">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="58b10-145">`Where-Object` 스크립트 블록 문이 true 인 모든 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-145">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="58b10-146">예를 들어 다음 명령은 일반적인 우선 순위 클래스, 즉 **PriorityClass** 속성 값이 normal 인 프로세스의 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-146">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="58b10-147">모든 PowerShell 비교 연산자는 스크립트 블록 형식에서 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-147">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="58b10-148">비교 연산자에 대 한 자세한 내용은 [about_Comparison_Operators](./About/about_Comparison_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58b10-148">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="58b10-149">**Comparison 문** 입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-149">**Comparison statement** .</span></span> <span data-ttu-id="58b10-150">또한 자연어와 더욱 유사하게 비교문을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-150">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="58b10-151">비교문은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-151">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="58b10-152">예를 들어 다음 명령은 Normal의 우선 순위 클래스를 포함 하는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-152">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="58b10-153">이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-153">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="58b10-154">Windows PowerShell 3.0부터, `Where-Object` 명령에서 비교 연산자를 매개 변수로 추가 `Where-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-154">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="58b10-155">지정되지 않은 경우 모든 연산자는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-155">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="58b10-156">Windows PowerShell 3.0 이전에는 PowerShell 언어의 비교 연산자를 스크립트 블록에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-156">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="58b10-157">에 단일 **속성** 을 제공 하면 `Where-Object` 속성의 값이 부울 식으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-157">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="58b10-158">**Length** 값이 0이 아니면 식이 **True** 로 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-158">When the value of **Length** is not zero, the expression evaluates to **True** .</span></span> <span data-ttu-id="58b10-159">`('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="58b10-159">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="58b10-160">이전 예제는와 기능적으로 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-160">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="58b10-161">예제</span><span class="sxs-lookup"><span data-stu-id="58b10-161">EXAMPLES</span></span>

### <span data-ttu-id="58b10-162">예제 1: 중지 된 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="58b10-162">Example 1: Get stopped services</span></span>

<span data-ttu-id="58b10-163">이러한 명령은 현재 중지 된 모든 서비스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-163">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="58b10-164">`$_`자동 변수는 cmdlet에 전달 되는 각 개체를 나타냅니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="58b10-164">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="58b10-165">첫 번째 명령은 스크립트 블록 형식을 사용 하 고 두 번째 명령은 비교 문 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-165">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="58b10-166">이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-166">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="58b10-167">예제 2: 작업 집합을 기반으로 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="58b10-167">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="58b10-168">이 명령은 작업 집합이 250 메가바이트 (KB) 보다 큰 프로세스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-168">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="58b10-169">Scriptblock 및 문 구문은 동일 하며 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-169">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="58b10-170">예제 3: 프로세스 이름에 따라 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="58b10-170">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="58b10-171">이러한 명령은 문자로 시작 하는 **ProcessName** 속성 값을 가진 프로세스를 가져옵니다 `p` .</span><span class="sxs-lookup"><span data-stu-id="58b10-171">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="58b10-172">**Match** 연산자를 사용 하면 정규식 일치 항목을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-172">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="58b10-173">Scriptblock 및 문 구문은 동일 하며 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-173">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="58b10-174">예제 4: 비교 문 형식 사용</span><span class="sxs-lookup"><span data-stu-id="58b10-174">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="58b10-175">이 예에서는 cmdlet의 새 비교 문 형식을 사용 하는 방법을 보여 줍니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="58b10-175">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="58b10-176">첫 번째 명령은 비교문의 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-176">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="58b10-177">이 명령에서 별칭은 사용되지 않고 모든 매개 변수는 매개 변수 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-177">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="58b10-178">두 번째 명령은 비교 명령 형식의 더 자연스러운 용례입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-178">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="58b10-179">`where`별칭은 cmdlet 이름으로 대체 `Where-Object` 되 고 모든 선택적 매개 변수 이름은 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-179">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="58b10-180">예 5: 속성을 기반으로 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="58b10-180">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="58b10-181">이 예제에서는 true 또는 false 항목을 반환하거나 지정된 속성 값을 포함하는 명령을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-181">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="58b10-182">각 예제에는 명령에 대 한 스크립트 블록과 비교 문 형식이 모두 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-182">Each example shows both the script block and comparison statement formats for the command.</span></span>

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### <span data-ttu-id="58b10-183">예제 6: 여러 조건 사용</span><span class="sxs-lookup"><span data-stu-id="58b10-183">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="58b10-184">이 예제에서는 `Where-Object` 여러 조건을 사용 하 여 명령을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-184">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="58b10-185">이 명령은 업데이트할 수 있는 도움말 기능을 지원하는 중요하지 않은 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-185">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="58b10-186">이 명령은 cmdlet의 **ListAvailable** 매개 변수를 사용 하 여 `Get-Module` 컴퓨터의 모든 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-186">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="58b10-187">파이프라인 연산자 ()는 모듈을 `|` cmdlet으로 보냅니다 .이 `Where-Object` cmdlet은 이름이 MICROSOFT 또는 PS로 시작 하지 않는 모듈을 가져오고, 모듈에 대해 업데이트 된 도움말 파일을 찾을 수 있는 위치를 PowerShell에 알리는 **HelpInfoURI** 속성 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-187">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="58b10-188">비교 문은 **And** 논리 연산자로 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-188">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="58b10-189">이 예제에서는 스크립트 블록 명령 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-189">The example uses the script block command format.</span></span> <span data-ttu-id="58b10-190">**And** 및 **Or** 와 같은 논리 연산자는 스크립트 블록 에서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-190">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="58b10-191">명령의 비교 문 형식으로는 사용할 수 없습니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="58b10-191">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="58b10-192">PowerShell 논리 연산자에 대 한 자세한 내용은 [about_Logical_Operators](./About/about_logical_operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58b10-192">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="58b10-193">업데이트할 수 있는 도움말 기능에 대 한 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58b10-193">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="58b10-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="58b10-194">PARAMETERS</span></span>

### <span data-ttu-id="58b10-195">-CContains</span><span class="sxs-lookup"><span data-stu-id="58b10-195">-CContains</span></span>

<span data-ttu-id="58b10-196">이 cmdlet은 개체의 속성 값이 지정 된 값과 정확히 일치 하는 경우 컬렉션에서 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-196">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="58b10-197">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-197">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-198">`Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="58b10-198">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="58b10-199">**Ccontains** 는 값의 컬렉션을 참조 하 고, 지정 된 값과 정확히 일치 하는 항목이 컬렉션에 포함 되어 있으면 true입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-199">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="58b10-200">입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-200">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="58b10-201">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-202">-CEQ</span><span class="sxs-lookup"><span data-stu-id="58b10-202">-CEQ</span></span>

<span data-ttu-id="58b10-203">이 cmdlet이 속성 값이 지정 된 값과 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-203">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="58b10-204">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-204">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-205">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-206">-CGE</span><span class="sxs-lookup"><span data-stu-id="58b10-206">-CGE</span></span>

<span data-ttu-id="58b10-207">이 cmdlet이 속성 값이 지정 된 값 보다 크거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-207">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="58b10-208">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-208">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-209">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-209">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-210">-CGT</span><span class="sxs-lookup"><span data-stu-id="58b10-210">-CGT</span></span>

<span data-ttu-id="58b10-211">이 cmdlet이 속성 값이 지정 된 값 보다 큰 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-211">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="58b10-212">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-212">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-213">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-213">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-214">-CIn</span><span class="sxs-lookup"><span data-stu-id="58b10-214">-CIn</span></span>

<span data-ttu-id="58b10-215">속성 값이 지정 된 값을 포함 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-215">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="58b10-216">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-216">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-217">`Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="58b10-217">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="58b10-218">**Cin** 은 속성 및 값 위치가 반전 된다는 점을 제외 하 고는 **cin** 와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-218">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="58b10-219">예를 들어 다음 문은 모두 true입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-219">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="58b10-220">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-221">-CLE</span><span class="sxs-lookup"><span data-stu-id="58b10-221">-CLE</span></span>

<span data-ttu-id="58b10-222">이 cmdlet이 속성 값이 지정 된 값 보다 작거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-222">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="58b10-223">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-223">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-224">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-225">-CLike</span><span class="sxs-lookup"><span data-stu-id="58b10-225">-CLike</span></span>

<span data-ttu-id="58b10-226">속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하는 경우이 cmdlet이 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-226">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="58b10-227">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-227">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-228">`Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="58b10-228">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="58b10-229">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-230">-CLT</span><span class="sxs-lookup"><span data-stu-id="58b10-230">-CLT</span></span>

<span data-ttu-id="58b10-231">이 cmdlet이 속성 값이 지정 된 값 보다 작은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-231">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="58b10-232">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-232">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-233">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-233">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-234">-CMatch</span><span class="sxs-lookup"><span data-stu-id="58b10-234">-CMatch</span></span>

<span data-ttu-id="58b10-235">속성 값이 지정 된 정규식과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-235">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="58b10-236">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-236">This operation is case-sensitive.</span></span> <span data-ttu-id="58b10-237">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-237">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="58b10-238">`Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="58b10-238">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="58b10-239">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-240">-CNE</span><span class="sxs-lookup"><span data-stu-id="58b10-240">-CNE</span></span>

<span data-ttu-id="58b10-241">속성 값이 지정 된 값과 다른 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-241">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="58b10-242">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-242">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-243">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-244">-CNotContains</span><span class="sxs-lookup"><span data-stu-id="58b10-244">-CNotContains</span></span>

<span data-ttu-id="58b10-245">이 cmdlet은 개체의 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-245">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="58b10-246">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-246">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-247">`Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="58b10-247">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="58b10-248">**Notcontains** 및 **cnotcontains** 는 값의 컬렉션을 참조 하 고 컬렉션에 지정 된 값과 정확히 일치 하는 항목이 포함 되지 않은 경우 true입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-248">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="58b10-249">입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-249">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="58b10-250">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-251">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="58b10-251">-CNotIn</span></span>

<span data-ttu-id="58b10-252">이 cmdlet은 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-252">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="58b10-253">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-253">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-254">`Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="58b10-254">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="58b10-255">**Notin** 및 **cnotin** 연산자는 속성 및 값 위치가 반전 된다는 점을 제외 하 고 **Notin** 및 **cnotin** 와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-255">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="58b10-256">예를 들어 다음 문은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-256">For example, the following statements are true.</span></span>

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-257">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="58b10-257">-CNotLike</span></span>

<span data-ttu-id="58b10-258">이 cmdlet은 속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하지 않는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-258">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="58b10-259">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-259">This operation is case-sensitive.</span></span>

<span data-ttu-id="58b10-260">`Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="58b10-260">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="58b10-261">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-262">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="58b10-262">-CNotMatch</span></span>

<span data-ttu-id="58b10-263">이 cmdlet은 속성 값이 지정 된 정규식과 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-263">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="58b10-264">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-264">This operation is case-sensitive.</span></span> <span data-ttu-id="58b10-265">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-265">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="58b10-266">`Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="58b10-266">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="58b10-267">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-268">-포함</span><span class="sxs-lookup"><span data-stu-id="58b10-268">-Contains</span></span>

<span data-ttu-id="58b10-269">개체의 속성 값에 있는 항목이 지정 된 값과 정확히 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-269">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="58b10-270">`Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="58b10-270">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="58b10-271">속성 값이 단일 개체를 포함 하는 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-271">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="58b10-272">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-273">-EQ</span><span class="sxs-lookup"><span data-stu-id="58b10-273">-EQ</span></span>

<span data-ttu-id="58b10-274">이 cmdlet이 속성 값이 지정 된 값과 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-274">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="58b10-275">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-276">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="58b10-276">-FilterScript</span></span>

<span data-ttu-id="58b10-277">개체를 필터링하는 데 사용되는 스크립트 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-277">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="58b10-278">스크립트 블록을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="58b10-278">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="58b10-279">매개 변수 이름 **Filterscript** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-279">The parameter name, **FilterScript** , is optional.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-280">-GE</span><span class="sxs-lookup"><span data-stu-id="58b10-280">-GE</span></span>

<span data-ttu-id="58b10-281">이 cmdlet이 속성 값이 지정 된 값 보다 크거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-281">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="58b10-282">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-282">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-283">-GT</span><span class="sxs-lookup"><span data-stu-id="58b10-283">-GT</span></span>

<span data-ttu-id="58b10-284">이 cmdlet이 속성 값이 지정 된 값 보다 큰 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-284">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="58b10-285">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-286">-In</span><span class="sxs-lookup"><span data-stu-id="58b10-286">-In</span></span>

<span data-ttu-id="58b10-287">속성 값이 지정 된 값과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-287">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="58b10-288">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="58b10-288">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="58b10-289">**값** 매개 변수 값이 단일 개체인 경우 PowerShell은이를 하나의 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-289">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="58b10-290">개체의 속성 값이 배열인 경우 PowerShell은 참조 같음을 사용 하 여 일치 하는 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-290">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="58b10-291">`Where-Object`**Property** 매개 변수의 값과 **값** 의 값이 개체의 동일한 인스턴스인 경우에만 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-291">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="58b10-292">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-293">-InputObject</span><span class="sxs-lookup"><span data-stu-id="58b10-293">-InputObject</span></span>

<span data-ttu-id="58b10-294">필터링할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-294">Specifies the objects to be filtered.</span></span> <span data-ttu-id="58b10-295">개체를로 파이프 할 수도 있습니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="58b10-295">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="58b10-296">에 **inputobject** 매개 변수를 사용 하는 경우 `Where-Object` 명령 결과를로 파이프 하는 대신 `Where-Object` **inputobject** 값은 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-296">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="58b10-297">이는 값이 명령 결과인 컬렉션 (예:) 인 경우에도 마찬가지입니다 `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="58b10-297">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="58b10-298">**InputObject** 는 배열 또는 개체 컬렉션의 개별 속성을 반환할 수 없으므로를 사용 하 여 `Where-Object` 정의 된 속성에 특정 값이 있는 개체에 대 한 개체의 컬렉션을 필터링 하는 경우 `Where-Object` 이 항목의 예제에 나와 있는 것 처럼 파이프라인에서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-298">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-299">-Is</span><span class="sxs-lookup"><span data-stu-id="58b10-299">-Is</span></span>

<span data-ttu-id="58b10-300">이 cmdlet은 속성 값이 지정 된 .NET 형식의 인스턴스인 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-300">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="58b10-301">유형 이름은 대괄호로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="58b10-301">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="58b10-302">예를 들어 `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="58b10-302">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="58b10-303">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-303">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-304">-IsNot</span><span class="sxs-lookup"><span data-stu-id="58b10-304">-IsNot</span></span>

<span data-ttu-id="58b10-305">이 cmdlet이 속성 값이 지정 된 .NET 형식의 인스턴스가 아닌 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-305">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="58b10-306">예를 들어 `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="58b10-306">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="58b10-307">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-307">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-308">-LE</span><span class="sxs-lookup"><span data-stu-id="58b10-308">-LE</span></span>

<span data-ttu-id="58b10-309">이 cmdlet이 속성 값이 지정 된 값 보다 작거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-309">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="58b10-310">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-310">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-311">-좋아요</span><span class="sxs-lookup"><span data-stu-id="58b10-311">-Like</span></span>

<span data-ttu-id="58b10-312">속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하는 경우이 cmdlet이 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-312">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="58b10-313">`Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="58b10-313">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="58b10-314">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-314">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-315">-LT</span><span class="sxs-lookup"><span data-stu-id="58b10-315">-LT</span></span>

<span data-ttu-id="58b10-316">이 cmdlet이 속성 값이 지정 된 값 보다 작은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-316">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="58b10-317">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-317">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-318">-Match</span><span class="sxs-lookup"><span data-stu-id="58b10-318">-Match</span></span>

<span data-ttu-id="58b10-319">속성 값이 지정 된 정규식과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-319">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="58b10-320">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-320">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="58b10-321">`Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="58b10-321">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="58b10-322">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-323">-NE</span><span class="sxs-lookup"><span data-stu-id="58b10-323">-NE</span></span>

<span data-ttu-id="58b10-324">속성 값이 지정 된 값과 다른 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-324">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="58b10-325">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-326">-Not</span><span class="sxs-lookup"><span data-stu-id="58b10-326">-Not</span></span>

<span data-ttu-id="58b10-327">속성이 없거나 null 또는 false 값을 포함 하는 경우이 cmdlet은 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-327">Indicates that this cmdlet gets objects if the property does not exist or has a value of null or false.</span></span>

<span data-ttu-id="58b10-328">`Get-Service | where -Not "DependentServices"`</span><span class="sxs-lookup"><span data-stu-id="58b10-328">For example: `Get-Service | where -Not "DependentServices"`</span></span>

<span data-ttu-id="58b10-329">이 매개 변수는 Windows PowerShell 6.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-329">This parameter was introduced in Windows PowerShell 6.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-330">-NotContains</span><span class="sxs-lookup"><span data-stu-id="58b10-330">-NotContains</span></span>

<span data-ttu-id="58b10-331">속성 값에 지정 된 값과 정확히 일치 하는 항목이 없는 경우이 cmdlet이 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-331">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="58b10-332">`Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="58b10-332">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="58b10-333">**Notcontains** 는 값의 컬렉션을 참조 하며, 지정 된 값과 정확히 일치 하는 항목이 컬렉션에 포함 되어 있지 않으면 true입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-333">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="58b10-334">입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-334">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="58b10-335">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-335">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-336">-NotIn</span><span class="sxs-lookup"><span data-stu-id="58b10-336">-NotIn</span></span>

<span data-ttu-id="58b10-337">이 cmdlet은 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-337">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="58b10-338">`Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="58b10-338">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="58b10-339">**Value** 값이 단일 개체 이면 PowerShell은이를 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-339">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="58b10-340">개체의 속성 값이 배열인 경우 PowerShell은 참조 같음을 사용 하 여 일치 하는 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-340">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="58b10-341">`Where-Object`**속성** 값과 **값** 값이 개체의 동일한 인스턴스가 아닌 경우에만 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-341">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="58b10-342">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-342">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-343">-NotLike</span><span class="sxs-lookup"><span data-stu-id="58b10-343">-NotLike</span></span>

<span data-ttu-id="58b10-344">이 cmdlet은 속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하지 않는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-344">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="58b10-345">`Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="58b10-345">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="58b10-346">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-347">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="58b10-347">-NotMatch</span></span>

<span data-ttu-id="58b10-348">이 cmdlet이 속성 값이 지정 된 정규식과 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-348">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="58b10-349">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-349">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="58b10-350">`Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="58b10-350">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="58b10-351">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-351">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-352">-속성</span><span class="sxs-lookup"><span data-stu-id="58b10-352">-Property</span></span>

<span data-ttu-id="58b10-353">object 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-353">Specifies the name of an object property.</span></span> <span data-ttu-id="58b10-354">매개 변수 이름 **속성** 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-354">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="58b10-355">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-355">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, CaseSensitiveNotLikeSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="58b10-356">-Value</span><span class="sxs-lookup"><span data-stu-id="58b10-356">-Value</span></span>

<span data-ttu-id="58b10-357">속성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-357">Specifies a property value.</span></span> <span data-ttu-id="58b10-358">매개 변수 이름 **값** 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-358">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="58b10-359">이 매개 변수는 다음 비교 매개 변수와 함께 사용할 경우 와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-359">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="58b10-360">**CLike**</span><span class="sxs-lookup"><span data-stu-id="58b10-360">**CLike**</span></span>
- <span data-ttu-id="58b10-361">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="58b10-361">**CNotLike**</span></span>
- <span data-ttu-id="58b10-362">**이와**</span><span class="sxs-lookup"><span data-stu-id="58b10-362">**Like**</span></span>
- <span data-ttu-id="58b10-363">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="58b10-363">**NotLike**</span></span>

<span data-ttu-id="58b10-364">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-364">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Object
Parameter Sets: EqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="58b10-365">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="58b10-365">CommonParameters</span></span>

<span data-ttu-id="58b10-366">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="58b10-366">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="58b10-367">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58b10-367">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="58b10-368">입력</span><span class="sxs-lookup"><span data-stu-id="58b10-368">INPUTS</span></span>

### <span data-ttu-id="58b10-369">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="58b10-369">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="58b10-370">개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-370">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="58b10-371">출력</span><span class="sxs-lookup"><span data-stu-id="58b10-371">OUTPUTS</span></span>

### <span data-ttu-id="58b10-372">Object</span><span class="sxs-lookup"><span data-stu-id="58b10-372">Object</span></span>

<span data-ttu-id="58b10-373">이 cmdlet은 입력 개체 집합에서 선택한 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-373">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="58b10-374">참고</span><span class="sxs-lookup"><span data-stu-id="58b10-374">NOTES</span></span>

<span data-ttu-id="58b10-375">Windows PowerShell 4.0부터 `Where` `ForEach` 컬렉션과 함께 사용 하기 위해 메서드가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="58b10-375">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="58b10-376">이러한 새 메서드에 대 한 자세한 내용은 여기를 참조 하세요 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="58b10-376">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="58b10-377">관련 링크</span><span class="sxs-lookup"><span data-stu-id="58b10-377">RELATED LINKS</span></span>

[<span data-ttu-id="58b10-378">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-378">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="58b10-379">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-379">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="58b10-380">Group-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-380">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="58b10-381">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-381">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="58b10-382">New-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-382">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="58b10-383">Select-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-383">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="58b10-384">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-384">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="58b10-385">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="58b10-385">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
