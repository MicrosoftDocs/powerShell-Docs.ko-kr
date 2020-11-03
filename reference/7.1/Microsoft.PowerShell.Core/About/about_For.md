---
description: 조건부 테스트를 기반으로 문을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 07037b73a5507bb0ef420ad39271be8832f7500b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220921"
---
# <a name="about-for"></a><span data-ttu-id="2f1df-104">정보</span><span class="sxs-lookup"><span data-stu-id="2f1df-104">About For</span></span>

## <a name="short-description"></a><span data-ttu-id="2f1df-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="2f1df-105">Short description</span></span>
<span data-ttu-id="2f1df-106">조건부 테스트를 기반으로 문을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-106">Describes a language command you can use to run statements based on a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="2f1df-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-107">Long description</span></span>

<span data-ttu-id="2f1df-108">`For`문 (루프 라고도 함 `For` )은 지정 된 조건이로 평가 되는 동안 명령 블록에서 명령을 실행 하는 루프를 만드는 데 사용할 수 있는 언어 구문입니다 `$true` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-108">The `For` statement (also known as a `For` loop) is a language construct you can use to create a loop that runs commands in a command block while a specified condition evaluates to `$true`.</span></span>

<span data-ttu-id="2f1df-109">루프의 일반적인 용도는 `For` 값의 배열을 반복 하 고 이러한 값의 하위 집합에 대해 작동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-109">A typical use of the `For` loop is to iterate an array of values and to operate on a subset of these values.</span></span> <span data-ttu-id="2f1df-110">대부분의 경우 배열의 모든 값을 반복 하려면 문을 사용 하는 것이 좋습니다 `Foreach` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-110">In most cases, if you want to iterate all the values in an array, consider using a `Foreach` statement.</span></span>

### <a name="syntax"></a><span data-ttu-id="2f1df-111">구문</span><span class="sxs-lookup"><span data-stu-id="2f1df-111">Syntax</span></span>

<span data-ttu-id="2f1df-112">다음은 `For` 문 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-112">The following shows the `For` statement syntax.</span></span>

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

<span data-ttu-id="2f1df-113">**Init** 자리 표시자는 루프가 시작 되기 전에 실행 되는 하나 이상의 명령을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-113">The **Init** placeholder represents one or more commands that are run before the loop begins.</span></span> <span data-ttu-id="2f1df-114">일반적으로 문의 **Init** 부분을 사용 하 여 시작 값을 사용 하 여 변수를 만들고 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-114">You typically use the **Init** portion of the statement to create and initialize a variable with a starting value.</span></span>

<span data-ttu-id="2f1df-115">이 변수는 문의 다음 부분에서 테스트할 조건의 기반이 됩니다 `For` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-115">This variable will then be the basis for the condition to be tested in the next portion of the `For` statement.</span></span>

<span data-ttu-id="2f1df-116">**조건** 자리 표시자는 `For` `$true` 또는 `$false` **부울** 값으로 확인 되는 문의 부분을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-116">The **Condition** placeholder represents the portion of the `For` statement that resolves to a `$true` or `$false` **Boolean** value.</span></span> <span data-ttu-id="2f1df-117">PowerShell은 루프가 실행 될 때마다 조건을 평가 `For` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-117">PowerShell evaluates the condition each time the `For` loop runs.</span></span> <span data-ttu-id="2f1df-118">문이 이면 `$true` 명령 블록의 명령이 실행 되 고 문이 다시 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-118">If the statement is `$true`, the commands in the command block run, and the statement is evaluated again.</span></span> <span data-ttu-id="2f1df-119">조건이 여전히 이면 `$true` **문 목록의** 명령이 다시 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-119">If the condition is still `$true`, the commands in the **Statement list** run again.</span></span> <span data-ttu-id="2f1df-120">조건이이 될 때까지 루프가 반복 됩니다 `$false` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-120">The loop is repeated until the condition becomes `$false`.</span></span>

<span data-ttu-id="2f1df-121">**반복** 자리 표시자는 루프가 반복 될 때마다 실행 되는 쉼표로 구분 된 하나 이상의 명령을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-121">The **Repeat** placeholder represents one or more commands, separated by commas, that are executed each time the loop repeats.</span></span> <span data-ttu-id="2f1df-122">일반적으로이는 문의 **조건** 부분 내에서 테스트 되는 변수를 수정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-122">Typically, this is used to modify a variable that is tested inside the **Condition** part of the statement.</span></span>

<span data-ttu-id="2f1df-123">**문 목록** 자리 표시자는 루프가 입력 되거나 반복 될 때마다 실행 되는 하나 이상의 명령 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-123">The **Statement list** placeholder represents a set of one or more commands that are run each time the loop is entered or repeated.</span></span> <span data-ttu-id="2f1df-124">**문 목록의** 내용은 중괄호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-124">The contents of the **Statement list** are surrounded by braces.</span></span>

### <a name="support-for-multiple-operations"></a><span data-ttu-id="2f1df-125">여러 작업 지원</span><span class="sxs-lookup"><span data-stu-id="2f1df-125">Support for multiple operations</span></span>

<span data-ttu-id="2f1df-126">**Init** 문의 여러 할당 작업에 대해 다음과 같은 구문이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-126">The following syntaxes are supported for multiple assignment operations in the **Init** statement:</span></span>

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="2f1df-127">다음 구문은 **반복** 문의 여러 할당 연산에 대해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-127">The following syntaxes are supported for multiple assignment operations in the **Repeat** statement:</span></span>

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> <span data-ttu-id="2f1df-128">이전 또는 이후 증분 이외의 작업은 일부 구문에서 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-128">Operations other than pre or post increment may not work with all syntaxes.</span></span>

<span data-ttu-id="2f1df-129">여러 **조건의** 경우 다음 예제에서 보여 주는 것 처럼 논리 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-129">For multiple **Conditions** use logical operators as demonstrated by the following example.</span></span>

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="2f1df-130">자세한 내용은 [about_Logical_Operators](about_Logical_Operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2f1df-130">For more information, see [about_Logical_Operators](about_Logical_Operators.md).</span></span>

### <a name="examples"></a><span data-ttu-id="2f1df-131">예</span><span class="sxs-lookup"><span data-stu-id="2f1df-131">Examples</span></span>

<span data-ttu-id="2f1df-132">문에는 최소한 문의 `For` **Init** , **Condition** 및 **Repeat** 부분을 둘러싼 괄호가 필요 하 고 문의 **문 목록** 부분에서 중괄호로 묶은 명령이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-132">At a minimum, a `For` statement requires the parenthesis surrounding the **Init** , **Condition** , and **Repeat** part of the statement and a command surrounded by braces in the **Statement list** part of the statement.</span></span>

<span data-ttu-id="2f1df-133">이후 예제에서는 의도적으로 문 외부의 코드를 보여 줍니다 `For` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-133">Note that the upcoming examples intentionally show code outside the `For` statement.</span></span> <span data-ttu-id="2f1df-134">이후 예제에서 코드는 문에 통합 되어 `For` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-134">In later examples, code is integrated into the `For` statement.</span></span>

<span data-ttu-id="2f1df-135">예를 들어 다음 `For` 문은 `$i` CTRL + C를 눌러 명령을 수동으로 해제할 때까지 변수 값을 계속 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-135">For example, the following `For` statement continually displays the value of the `$i` variable until you manually break out of the command by pressing CTRL+C.</span></span>

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

<span data-ttu-id="2f1df-136">`$i`다음 예제와 같이 루프가 실행 될 때마다의 값이 1 씩 증가 하도록 문 목록에 추가 명령을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-136">You can add additional commands to the statement list so that the value of `$i` is incremented by 1 each time the loop is run, as the following example shows.</span></span>

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

<span data-ttu-id="2f1df-137">CTRL + C를 눌러 명령에서 분리 될 때까지이 명령문은 `$i` 루프가 실행 될 때마다 1 씩 증가 하는 변수 값을 계속 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-137">Until you break out of the command by pressing CTRL+C, this statement will continually display the value of the `$i` variable as it is incremented by 1 each time the loop is run.</span></span>

<span data-ttu-id="2f1df-138">문의 문 목록 부분에 있는 변수 값을 변경 하는 대신 다음과 같이 `For` 문의 **반복** 부분을 대신 사용할 수 있습니다 `For` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-138">Rather than change the value of the variable in the statement list part of the `For` statement, you can use the **Repeat** portion of the `For` statement instead, as follows.</span></span>

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="2f1df-139">이 문은 CTRL + C를 눌러 명령에서 중단 될 때까지 계속 무기한 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-139">This statement will still repeat indefinitely until you break out of the command by pressing CTRL+C.</span></span>

<span data-ttu-id="2f1df-140">`For` *조건을* 사용 하 여 루프를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-140">You can terminate the `For` loop using a *condition*.</span></span> <span data-ttu-id="2f1df-141">문의 **조건** 부분을 사용 하 여 조건을 지정할 수 있습니다 `For` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-141">You can place a condition using the **Condition** portion of the `For` statement.</span></span> <span data-ttu-id="2f1df-142">`For`조건이로 평가 되 면 루프가 종료 `$false` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-142">The `For` loop terminates when the condition evaluates to `$false`.</span></span>

<span data-ttu-id="2f1df-143">다음 예제에서 `For` 루프는의 값 `$i` 이 10 보다 작거나 같은 경우에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-143">In the following example, the `For` loop runs while the value of `$i` is less than or equal to 10.</span></span>

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="2f1df-144">문 외부에서 변수를 만들고 초기화 하는 대신 `For` `For` 문의 **Init** 부분을 사용 하 여 루프 내에서이 작업을 수행할 수 있습니다 `For` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-144">Instead of creating and initializing the variable outside the `For` statement, you can perform this task inside the `For` loop by using the **Init** portion of the `For` statement.</span></span>

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

<span data-ttu-id="2f1df-145">세미콜론 대신 캐리지 리턴을 사용 하 여 문의 **Init** , **Condition** 및 **Repeat** 부분을 구분할 수 있습니다 `For` .</span><span class="sxs-lookup"><span data-stu-id="2f1df-145">You can use carriage returns instead of semicolons to delimit the **Init** , **Condition** , and **Repeat** portions of the `For` statement.</span></span> <span data-ttu-id="2f1df-146">다음 예제에서는 `For` 이 대체 구문을 사용 하는을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-146">The following example shows a `For` that uses this alternative syntax.</span></span>

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

<span data-ttu-id="2f1df-147">이 문의 대체 형식은 `For` powershell 스크립트 파일 및 powershell 명령 프롬프트에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-147">This alternative form of the `For` statement works in PowerShell script files and at the PowerShell command prompt.</span></span> <span data-ttu-id="2f1df-148">그러나 `For` 명령 프롬프트에서 대화형 명령을 입력할 때 세미콜론으로 문 구문을 사용 하는 것이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-148">However, it is easier to use the `For` statement syntax with semicolons when you enter interactive commands at the command prompt.</span></span>

<span data-ttu-id="2f1df-149">루프는 `For` `Foreach` 패턴을 사용 하 여 배열 또는 컬렉션의 값을 증가 시킬 수 있기 때문에 루프 보다 더 유연 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-149">The `For` loop is more flexible than the `Foreach` loop because it allows you to increment values in an array or collection by using patterns.</span></span> <span data-ttu-id="2f1df-150">다음 예제에서 `$i` 변수는 문의 **반복** 부분에서 2 씩 증가 `For` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-150">In the following example, the `$i` variable is incremented by 2 in the **Repeat** portion of the `For` statement.</span></span>

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

<span data-ttu-id="2f1df-151">`For`루프는 다음 예제와 같이 한 줄에 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f1df-151">The `For` loop can also be written on one line as in the following example.</span></span>

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a><span data-ttu-id="2f1df-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f1df-152">SEE ALSO</span></span>

[<span data-ttu-id="2f1df-153">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="2f1df-153">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="2f1df-154">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="2f1df-154">about_Foreach</span></span>](about_Foreach.md)

