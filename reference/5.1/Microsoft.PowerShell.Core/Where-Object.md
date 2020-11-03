---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: aaee09926c93bb8c8e72efb5fd4ea34e2fc67391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212681"
---
# <span data-ttu-id="92892-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="92892-103">Where-Object</span></span>

## <span data-ttu-id="92892-104">개요</span><span class="sxs-lookup"><span data-stu-id="92892-104">SYNOPSIS</span></span>
<span data-ttu-id="92892-105">속성 값에 따라 컬렉션에서 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="92892-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92892-106">SYNTAX</span></span>

### <span data-ttu-id="92892-107">EqualSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="92892-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ] [<CommonParameters>]
```

### <span data-ttu-id="92892-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="92892-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="92892-109">MatchSet</span><span class="sxs-lookup"><span data-stu-id="92892-109">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Match]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="92892-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CEQ] [<CommonParameters>]
```

### <span data-ttu-id="92892-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="92892-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NE] [<CommonParameters>]
```

### <span data-ttu-id="92892-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="92892-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNE] [<CommonParameters>]
```

### <span data-ttu-id="92892-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="92892-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GT] [<CommonParameters>]
```

### <span data-ttu-id="92892-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="92892-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGT] [<CommonParameters>]
```

### <span data-ttu-id="92892-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="92892-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LT] [<CommonParameters>]
```

### <span data-ttu-id="92892-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="92892-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLT] [<CommonParameters>]
```

### <span data-ttu-id="92892-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="92892-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GE] [<CommonParameters>]
```

### <span data-ttu-id="92892-118">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="92892-118">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGE] [<CommonParameters>]
```

### <span data-ttu-id="92892-119">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="92892-119">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LE] [<CommonParameters>]
```

### <span data-ttu-id="92892-120">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="92892-120">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLE] [<CommonParameters>]
```

### <span data-ttu-id="92892-121">LikeSet</span><span class="sxs-lookup"><span data-stu-id="92892-121">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Like] [<CommonParameters>]
```

### <span data-ttu-id="92892-122">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="92892-122">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLike] [<CommonParameters>]
```

### <span data-ttu-id="92892-123">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="92892-123">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotLike] [<CommonParameters>]
```

### <span data-ttu-id="92892-124">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="92892-124">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotLike]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="92892-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CMatch] [<CommonParameters>]
```

### <span data-ttu-id="92892-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="92892-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotMatch]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="92892-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotMatch]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-128">ContainsSet</span><span class="sxs-lookup"><span data-stu-id="92892-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Contains]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="92892-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CContains]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="92892-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotContains]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="92892-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotContains]
 [<CommonParameters>]
```

### <span data-ttu-id="92892-132">오목</span><span class="sxs-lookup"><span data-stu-id="92892-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-In] [<CommonParameters>]
```

### <span data-ttu-id="92892-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="92892-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CIn] [<CommonParameters>]
```

### <span data-ttu-id="92892-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="92892-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotIn] [<CommonParameters>]
```

### <span data-ttu-id="92892-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="92892-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotIn] [<CommonParameters>]
```

### <span data-ttu-id="92892-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="92892-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Is] [<CommonParameters>]
```

### <span data-ttu-id="92892-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="92892-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-IsNot] [<CommonParameters>]
```

## <span data-ttu-id="92892-138">설명</span><span class="sxs-lookup"><span data-stu-id="92892-138">DESCRIPTION</span></span>

<span data-ttu-id="92892-139">`Where-Object`Cmdlet은 전달 되는 개체의 컬렉션에서 특정 속성 값이 있는 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-139">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="92892-140">예를 들어 cmdlet을 사용 하 여 특정 `Where-Object` 날짜 이후에 만들어진 파일, 특정 ID를 가진 이벤트 또는 특정 버전의 Windows를 사용 하는 컴퓨터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-140">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="92892-141">Windows PowerShell 3.0부터 명령을 생성 하는 방법에는 두 가지가 있습니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="92892-141">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="92892-142">**스크립트 블록** 입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-142">**Script block** .</span></span> <span data-ttu-id="92892-143">스크립트 블록을 사용하여 속성 이름, 비교 연산자 및 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-143">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="92892-144">`Where-Object` 스크립트 블록 문이 true 인 모든 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-144">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="92892-145">예를 들어 다음 명령은 일반적인 우선 순위 클래스, 즉 **PriorityClass** 속성 값이 normal 인 프로세스의 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-145">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="92892-146">모든 PowerShell 비교 연산자는 스크립트 블록 형식에서 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-146">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="92892-147">비교 연산자에 대 한 자세한 내용은 [about_Comparison_Operators](./About/about_Comparison_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92892-147">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="92892-148">**Comparison 문** 입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-148">**Comparison statement** .</span></span> <span data-ttu-id="92892-149">또한 자연어와 더욱 유사하게 비교문을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-149">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="92892-150">비교문은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-150">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="92892-151">예를 들어 다음 명령은 Normal의 우선 순위 클래스를 포함 하는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-151">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="92892-152">이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-152">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="92892-153">Windows PowerShell 3.0부터, `Where-Object` 명령에서 비교 연산자를 매개 변수로 추가 `Where-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-153">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="92892-154">지정되지 않은 경우 모든 연산자는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-154">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="92892-155">Windows PowerShell 3.0 이전에는 PowerShell 언어의 비교 연산자를 스크립트 블록에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-155">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="92892-156">에 단일 **속성** 을 제공 하면 `Where-Object` 속성의 값이 부울 식으로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-156">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="92892-157">**Length** 값이 0이 아니면 식이 **True** 로 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-157">When the value of **Length** is not zero, the expression evaluates to **True** .</span></span> <span data-ttu-id="92892-158">`('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="92892-158">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="92892-159">이전 예제는와 기능적으로 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-159">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="92892-160">예제</span><span class="sxs-lookup"><span data-stu-id="92892-160">EXAMPLES</span></span>

### <span data-ttu-id="92892-161">예제 1: 중지 된 서비스 가져오기</span><span class="sxs-lookup"><span data-stu-id="92892-161">Example 1: Get stopped services</span></span>

<span data-ttu-id="92892-162">이러한 명령은 현재 중지 된 모든 서비스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-162">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="92892-163">`$_`자동 변수는 cmdlet에 전달 되는 각 개체를 나타냅니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="92892-163">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="92892-164">첫 번째 명령은 스크립트 블록 형식을 사용 하 고 두 번째 명령은 비교 문 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-164">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="92892-165">이러한 명령은 동일하므로 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-165">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="92892-166">예제 2: 작업 집합을 기반으로 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="92892-166">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="92892-167">이 명령은 작업 집합이 250 메가바이트 (KB) 보다 큰 프로세스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-167">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="92892-168">Scriptblock 및 문 구문은 동일 하며 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-168">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="92892-169">예제 3: 프로세스 이름에 따라 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="92892-169">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="92892-170">이러한 명령은 문자로 시작 하는 **ProcessName** 속성 값을 가진 프로세스를 가져옵니다 `p` .</span><span class="sxs-lookup"><span data-stu-id="92892-170">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="92892-171">**Match** 연산자를 사용 하면 정규식 일치 항목을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-171">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="92892-172">Scriptblock 및 문 구문은 동일 하며 서로 바꿔 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-172">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="92892-173">예제 4: 비교 문 형식 사용</span><span class="sxs-lookup"><span data-stu-id="92892-173">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="92892-174">이 예에서는 cmdlet의 새 비교 문 형식을 사용 하는 방법을 보여 줍니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="92892-174">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="92892-175">첫 번째 명령은 비교문의 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-175">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="92892-176">이 명령에서 별칭은 사용되지 않고 모든 매개 변수는 매개 변수 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-176">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="92892-177">두 번째 명령은 비교 명령 형식의 더 자연스러운 용례입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-177">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="92892-178">`where`별칭은 cmdlet 이름으로 대체 `Where-Object` 되 고 모든 선택적 매개 변수 이름은 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-178">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="92892-179">예 5: 속성을 기반으로 명령 가져오기</span><span class="sxs-lookup"><span data-stu-id="92892-179">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="92892-180">이 예제에서는 true 또는 false 항목을 반환하거나 지정된 속성 값을 포함하는 명령을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92892-180">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="92892-181">각 예제에는 명령에 대 한 스크립트 블록과 비교 문 형식이 모두 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-181">Each example shows both the script block and comparison statement formats for the command.</span></span>

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

### <span data-ttu-id="92892-182">예제 6: 여러 조건 사용</span><span class="sxs-lookup"><span data-stu-id="92892-182">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="92892-183">이 예제에서는 `Where-Object` 여러 조건을 사용 하 여 명령을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92892-183">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="92892-184">이 명령은 업데이트할 수 있는 도움말 기능을 지원하는 중요하지 않은 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-184">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="92892-185">이 명령은 cmdlet의 **ListAvailable** 매개 변수를 사용 하 여 `Get-Module` 컴퓨터의 모든 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-185">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="92892-186">파이프라인 연산자 ()는 모듈을 `|` cmdlet으로 보냅니다 .이 `Where-Object` cmdlet은 이름이 MICROSOFT 또는 PS로 시작 하지 않는 모듈을 가져오고, 모듈에 대해 업데이트 된 도움말 파일을 찾을 수 있는 위치를 PowerShell에 알리는 **HelpInfoURI** 속성 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-186">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="92892-187">비교 문은 **And** 논리 연산자로 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-187">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="92892-188">이 예제에서는 스크립트 블록 명령 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-188">The example uses the script block command format.</span></span> <span data-ttu-id="92892-189">**And** 및 **Or** 와 같은 논리 연산자는 스크립트 블록 에서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-189">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="92892-190">명령의 비교 문 형식으로는 사용할 수 없습니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="92892-190">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="92892-191">PowerShell 논리 연산자에 대 한 자세한 내용은 [about_Logical_Operators](./About/about_logical_operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92892-191">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="92892-192">업데이트할 수 있는 도움말 기능에 대 한 자세한 내용은 [about_Updatable_Help](./About/about_Updatable_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92892-192">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="92892-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="92892-193">PARAMETERS</span></span>

### <span data-ttu-id="92892-194">-CContains</span><span class="sxs-lookup"><span data-stu-id="92892-194">-CContains</span></span>

<span data-ttu-id="92892-195">이 cmdlet은 개체의 속성 값이 지정 된 값과 정확히 일치 하는 경우 컬렉션에서 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-195">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="92892-196">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-196">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-197">`Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="92892-197">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="92892-198">**Ccontains** 는 값의 컬렉션을 참조 하 고, 지정 된 값과 정확히 일치 하는 항목이 컬렉션에 포함 되어 있으면 true입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-198">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="92892-199">입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-199">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="92892-200">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-200">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-201">-CEQ</span><span class="sxs-lookup"><span data-stu-id="92892-201">-CEQ</span></span>

<span data-ttu-id="92892-202">이 cmdlet이 속성 값이 지정 된 값과 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-202">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="92892-203">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-203">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-204">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-205">-CGE</span><span class="sxs-lookup"><span data-stu-id="92892-205">-CGE</span></span>

<span data-ttu-id="92892-206">이 cmdlet이 속성 값이 지정 된 값 보다 크거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-206">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="92892-207">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-207">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-208">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-209">-CGT</span><span class="sxs-lookup"><span data-stu-id="92892-209">-CGT</span></span>

<span data-ttu-id="92892-210">이 cmdlet이 속성 값이 지정 된 값 보다 큰 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-210">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="92892-211">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-211">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-212">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-213">-CIn</span><span class="sxs-lookup"><span data-stu-id="92892-213">-CIn</span></span>

<span data-ttu-id="92892-214">속성 값이 지정 된 값을 포함 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92892-214">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="92892-215">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-215">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-216">`Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="92892-216">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="92892-217">**Cin** 은 속성 및 값 위치가 반전 된다는 점을 제외 하 고는 **cin** 와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-217">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="92892-218">예를 들어 다음 문은 모두 true입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-218">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="92892-219">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-219">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-220">-CLE</span><span class="sxs-lookup"><span data-stu-id="92892-220">-CLE</span></span>

<span data-ttu-id="92892-221">이 cmdlet이 속성 값이 지정 된 값 보다 작거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-221">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="92892-222">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-222">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-223">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-223">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-224">-CLike</span><span class="sxs-lookup"><span data-stu-id="92892-224">-CLike</span></span>

<span data-ttu-id="92892-225">속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하는 경우이 cmdlet이 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-225">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="92892-226">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-226">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-227">`Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="92892-227">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="92892-228">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-229">-CLT</span><span class="sxs-lookup"><span data-stu-id="92892-229">-CLT</span></span>

<span data-ttu-id="92892-230">이 cmdlet이 속성 값이 지정 된 값 보다 작은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-230">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="92892-231">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-231">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-232">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-233">-CMatch</span><span class="sxs-lookup"><span data-stu-id="92892-233">-CMatch</span></span>

<span data-ttu-id="92892-234">속성 값이 지정 된 정규식과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92892-234">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="92892-235">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-235">This operation is case-sensitive.</span></span> <span data-ttu-id="92892-236">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-236">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="92892-237">`Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="92892-237">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="92892-238">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-239">-CNE</span><span class="sxs-lookup"><span data-stu-id="92892-239">-CNE</span></span>

<span data-ttu-id="92892-240">속성 값이 지정 된 값과 다른 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92892-240">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="92892-241">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-241">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-242">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-242">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-243">-CNotContains</span><span class="sxs-lookup"><span data-stu-id="92892-243">-CNotContains</span></span>

<span data-ttu-id="92892-244">이 cmdlet은 개체의 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-244">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="92892-245">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-245">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-246">`Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="92892-246">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="92892-247">**Notcontains** 및 **cnotcontains** 는 값의 컬렉션을 참조 하 고 컬렉션에 지정 된 값과 정확히 일치 하는 항목이 포함 되지 않은 경우 true입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-247">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="92892-248">입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-248">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="92892-249">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-250">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="92892-250">-CNotIn</span></span>

<span data-ttu-id="92892-251">이 cmdlet은 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-251">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="92892-252">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-252">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-253">`Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="92892-253">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="92892-254">**Notin** 및 **cnotin** 연산자는 속성 및 값 위치가 반전 된다는 점을 제외 하 고 **Notin** 및 **cnotin** 와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-254">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="92892-255">예를 들어 다음 문은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-255">For example, the following statements are true.</span></span>

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

### <span data-ttu-id="92892-256">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="92892-256">-CNotLike</span></span>

<span data-ttu-id="92892-257">이 cmdlet은 속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하지 않는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-257">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="92892-258">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-258">This operation is case-sensitive.</span></span>

<span data-ttu-id="92892-259">`Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="92892-259">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="92892-260">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-261">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="92892-261">-CNotMatch</span></span>

<span data-ttu-id="92892-262">이 cmdlet은 속성 값이 지정 된 정규식과 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-262">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="92892-263">이 작업은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-263">This operation is case-sensitive.</span></span> <span data-ttu-id="92892-264">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-264">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="92892-265">`Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="92892-265">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="92892-266">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-267">-포함</span><span class="sxs-lookup"><span data-stu-id="92892-267">-Contains</span></span>

<span data-ttu-id="92892-268">개체의 속성 값에 있는 항목이 지정 된 값과 정확히 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92892-268">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="92892-269">`Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="92892-269">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="92892-270">속성 값이 단일 개체를 포함 하는 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-270">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="92892-271">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-272">-EQ</span><span class="sxs-lookup"><span data-stu-id="92892-272">-EQ</span></span>

<span data-ttu-id="92892-273">이 cmdlet이 속성 값이 지정 된 값과 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-273">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="92892-274">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-274">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-275">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="92892-275">-FilterScript</span></span>

<span data-ttu-id="92892-276">개체를 필터링하는 데 사용되는 스크립트 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-276">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="92892-277">스크립트 블록을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="92892-277">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="92892-278">매개 변수 이름 **Filterscript** 는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-278">The parameter name, **FilterScript** , is optional.</span></span>

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

### <span data-ttu-id="92892-279">-GE</span><span class="sxs-lookup"><span data-stu-id="92892-279">-GE</span></span>

<span data-ttu-id="92892-280">이 cmdlet이 속성 값이 지정 된 값 보다 크거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-280">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="92892-281">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-282">-GT</span><span class="sxs-lookup"><span data-stu-id="92892-282">-GT</span></span>

<span data-ttu-id="92892-283">이 cmdlet이 속성 값이 지정 된 값 보다 큰 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-283">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="92892-284">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-284">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-285">-In</span><span class="sxs-lookup"><span data-stu-id="92892-285">-In</span></span>

<span data-ttu-id="92892-286">속성 값이 지정 된 값과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92892-286">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="92892-287">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="92892-287">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="92892-288">**값** 매개 변수 값이 단일 개체인 경우 PowerShell은이를 하나의 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-288">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="92892-289">개체의 속성 값이 배열인 경우 PowerShell은 참조 같음을 사용 하 여 일치 하는 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-289">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="92892-290">`Where-Object`**Property** 매개 변수의 값과 **값** 의 값이 개체의 동일한 인스턴스인 경우에만 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-290">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="92892-291">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-291">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-292">-InputObject</span><span class="sxs-lookup"><span data-stu-id="92892-292">-InputObject</span></span>

<span data-ttu-id="92892-293">필터링할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-293">Specifies the objects to be filtered.</span></span> <span data-ttu-id="92892-294">개체를로 파이프 할 수도 있습니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="92892-294">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="92892-295">에 **inputobject** 매개 변수를 사용 하는 경우 `Where-Object` 명령 결과를로 파이프 하는 대신 `Where-Object` **inputobject** 값은 단일 개체로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-295">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="92892-296">이는 값이 명령 결과인 컬렉션 (예:) 인 경우에도 마찬가지입니다 `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="92892-296">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="92892-297">**InputObject** 는 배열 또는 개체 컬렉션의 개별 속성을 반환할 수 없으므로를 사용 하 여 `Where-Object` 정의 된 속성에 특정 값이 있는 개체에 대 한 개체의 컬렉션을 필터링 하는 경우 `Where-Object` 이 항목의 예제에 나와 있는 것 처럼 파이프라인에서를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-297">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="92892-298">-Is</span><span class="sxs-lookup"><span data-stu-id="92892-298">-Is</span></span>

<span data-ttu-id="92892-299">이 cmdlet은 속성 값이 지정 된 .NET 형식의 인스턴스인 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-299">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="92892-300">유형 이름은 대괄호로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="92892-300">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="92892-301">예를 들어 `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="92892-301">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="92892-302">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-302">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-303">-IsNot</span><span class="sxs-lookup"><span data-stu-id="92892-303">-IsNot</span></span>

<span data-ttu-id="92892-304">이 cmdlet이 속성 값이 지정 된 .NET 형식의 인스턴스가 아닌 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-304">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="92892-305">예를 들어 `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="92892-305">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="92892-306">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-306">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-307">-LE</span><span class="sxs-lookup"><span data-stu-id="92892-307">-LE</span></span>

<span data-ttu-id="92892-308">이 cmdlet이 속성 값이 지정 된 값 보다 작거나 같은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-308">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="92892-309">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-309">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-310">-좋아요</span><span class="sxs-lookup"><span data-stu-id="92892-310">-Like</span></span>

<span data-ttu-id="92892-311">속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하는 경우이 cmdlet이 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-311">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="92892-312">`Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="92892-312">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="92892-313">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-313">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-314">-LT</span><span class="sxs-lookup"><span data-stu-id="92892-314">-LT</span></span>

<span data-ttu-id="92892-315">이 cmdlet이 속성 값이 지정 된 값 보다 작은 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-315">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="92892-316">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-317">-Match</span><span class="sxs-lookup"><span data-stu-id="92892-317">-Match</span></span>

<span data-ttu-id="92892-318">속성 값이 지정 된 정규식과 일치 하는 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92892-318">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="92892-319">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-319">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="92892-320">`Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="92892-320">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="92892-321">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-321">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-322">-NE</span><span class="sxs-lookup"><span data-stu-id="92892-322">-NE</span></span>

<span data-ttu-id="92892-323">속성 값이 지정 된 값과 다른 경우이 cmdlet이 개체를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92892-323">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="92892-324">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-324">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-325">-NotContains</span><span class="sxs-lookup"><span data-stu-id="92892-325">-NotContains</span></span>

<span data-ttu-id="92892-326">속성 값에 지정 된 값과 정확히 일치 하는 항목이 없는 경우이 cmdlet이 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-326">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="92892-327">`Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="92892-327">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="92892-328">**Notcontains** 는 값의 컬렉션을 참조 하며, 지정 된 값과 정확히 일치 하는 항목이 컬렉션에 포함 되어 있지 않으면 true입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-328">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="92892-329">입력이 단일 개체인 경우 PowerShell은 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-329">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="92892-330">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-330">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-331">-NotIn</span><span class="sxs-lookup"><span data-stu-id="92892-331">-NotIn</span></span>

<span data-ttu-id="92892-332">이 cmdlet은 속성 값이 지정 된 값과 정확히 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-332">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="92892-333">`Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="92892-333">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="92892-334">**Value** 값이 단일 개체 이면 PowerShell은이를 한 개체의 컬렉션으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-334">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="92892-335">개체의 속성 값이 배열인 경우 PowerShell은 참조 같음을 사용 하 여 일치 하는 항목을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-335">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="92892-336">`Where-Object`**속성** 값과 **값** 값이 개체의 동일한 인스턴스가 아닌 경우에만 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-336">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="92892-337">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-337">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-338">-NotLike</span><span class="sxs-lookup"><span data-stu-id="92892-338">-NotLike</span></span>

<span data-ttu-id="92892-339">이 cmdlet은 속성 값이 와일드 카드 문자를 포함 하는 값과 일치 하지 않는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-339">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="92892-340">`Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="92892-340">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="92892-341">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-341">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-342">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="92892-342">-NotMatch</span></span>

<span data-ttu-id="92892-343">이 cmdlet이 속성 값이 지정 된 정규식과 일치 하지 않는 경우 해당 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="92892-343">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="92892-344">입력이 스칼라 인 경우 일치 하는 값이 `$Matches` 자동 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92892-344">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="92892-345">`Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="92892-345">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="92892-346">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="92892-347">-속성</span><span class="sxs-lookup"><span data-stu-id="92892-347">-Property</span></span>

<span data-ttu-id="92892-348">object 속성의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-348">Specifies the name of an object property.</span></span> <span data-ttu-id="92892-349">매개 변수 이름 **속성** 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-349">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="92892-350">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-350">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92892-351">-Value</span><span class="sxs-lookup"><span data-stu-id="92892-351">-Value</span></span>

<span data-ttu-id="92892-352">속성 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-352">Specifies a property value.</span></span> <span data-ttu-id="92892-353">매개 변수 이름 **값** 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="92892-353">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="92892-354">이 매개 변수는 다음 비교 매개 변수와 함께 사용할 경우 와일드 카드 문자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-354">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="92892-355">**CLike**</span><span class="sxs-lookup"><span data-stu-id="92892-355">**CLike**</span></span>
- <span data-ttu-id="92892-356">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="92892-356">**CNotLike**</span></span>
- <span data-ttu-id="92892-357">**이와**</span><span class="sxs-lookup"><span data-stu-id="92892-357">**Like**</span></span>
- <span data-ttu-id="92892-358">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="92892-358">**NotLike**</span></span>

<span data-ttu-id="92892-359">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-359">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="92892-360">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92892-360">CommonParameters</span></span>

<span data-ttu-id="92892-361">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92892-361">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92892-362">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="92892-362">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92892-363">입력</span><span class="sxs-lookup"><span data-stu-id="92892-363">INPUTS</span></span>

### <span data-ttu-id="92892-364">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="92892-364">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="92892-365">개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-365">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="92892-366">출력</span><span class="sxs-lookup"><span data-stu-id="92892-366">OUTPUTS</span></span>

### <span data-ttu-id="92892-367">Object</span><span class="sxs-lookup"><span data-stu-id="92892-367">Object</span></span>

<span data-ttu-id="92892-368">이 cmdlet은 입력 개체 집합에서 선택한 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="92892-368">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="92892-369">참고</span><span class="sxs-lookup"><span data-stu-id="92892-369">NOTES</span></span>

<span data-ttu-id="92892-370">Windows PowerShell 4.0부터 `Where` `ForEach` 컬렉션과 함께 사용 하기 위해 메서드가 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="92892-370">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="92892-371">이러한 새 메서드에 대 한 자세한 내용은 여기를 참조 하세요 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="92892-371">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="92892-372">관련 링크</span><span class="sxs-lookup"><span data-stu-id="92892-372">RELATED LINKS</span></span>

[<span data-ttu-id="92892-373">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="92892-373">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="92892-374">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="92892-374">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="92892-375">Group-Object</span><span class="sxs-lookup"><span data-stu-id="92892-375">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="92892-376">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="92892-376">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="92892-377">New-Object</span><span class="sxs-lookup"><span data-stu-id="92892-377">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="92892-378">Select-Object</span><span class="sxs-lookup"><span data-stu-id="92892-378">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="92892-379">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="92892-379">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="92892-380">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="92892-380">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
