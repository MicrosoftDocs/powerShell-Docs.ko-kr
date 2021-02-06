---
description: 스위치를 사용 하 여 여러 문을 처리 하는 방법을 설명 합니다 `If` .
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 5ca12fe1d5052c1589c5dfecca8cf08cf68901e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599772"
---
# <a name="about-switch"></a><span data-ttu-id="9e9d7-103">스위치 정보</span><span class="sxs-lookup"><span data-stu-id="9e9d7-103">About Switch</span></span>

## <a name="short-description"></a><span data-ttu-id="9e9d7-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9e9d7-104">Short description</span></span>
<span data-ttu-id="9e9d7-105">스위치를 사용 하 여 여러 문을 처리 하는 방법을 설명 합니다 `If` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-105">Explains how to use a switch to handle multiple `If` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="9e9d7-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-106">Long description</span></span>

<span data-ttu-id="9e9d7-107">스크립트나 함수에서 조건을 확인 하려면 `If` 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-107">To check a condition in a script or function, use an `If` statement.</span></span> <span data-ttu-id="9e9d7-108">`If`문은 변수의 값과 개체의 속성을 포함 하 여 다양 한 유형의 조건을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-108">The `If` statement can check many types of conditions, including the value of variables and the properties of objects.</span></span>

<span data-ttu-id="9e9d7-109">여러 조건을 확인 하려면 `Switch` 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-109">To check multiple conditions, use a `Switch` statement.</span></span> <span data-ttu-id="9e9d7-110">`Switch`문은 일련의 `If` 문과 동일 하지만 더 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-110">The `Switch` statement is equivalent to a series of `If` statements, but it is simpler.</span></span> <span data-ttu-id="9e9d7-111">`Switch`문은 각 조건과 선택적 동작을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-111">The `Switch` statement lists each condition and an optional action.</span></span> <span data-ttu-id="9e9d7-112">조건이 가져오는 경우 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-112">If a condition obtains, the action is performed.</span></span>

<span data-ttu-id="9e9d7-113">`Switch`문은 `$_` 및 자동 변수를 사용할 수 있습니다 `$switch` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-113">The `Switch` statement can use the `$_` and `$switch` automatic variables.</span></span> <span data-ttu-id="9e9d7-114">자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-114">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="9e9d7-115">기본 `Switch` 문의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-115">A basic `Switch` statement has the following format:</span></span>

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

<span data-ttu-id="9e9d7-116">예를 들어 다음 `Switch` 문은 테스트 값 3을 각 조건과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-116">For example, the following `Switch` statement compares the test value, 3, to each of the conditions.</span></span> <span data-ttu-id="9e9d7-117">테스트 값이 조건과 일치 하면 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-117">When the test value matches the condition, the action is performed.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

<span data-ttu-id="9e9d7-118">이 간단한 예제에서는 값 3과 일치 하는 경우에도 값이 목록의 각 조건과 비교 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-118">In this simple example, the value is compared to each condition in the list, even though there is a match for the value 3.</span></span> <span data-ttu-id="9e9d7-119">다음 `Switch` 문에는 값이 3 인 두 개의 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-119">The following `Switch` statement has two conditions for a value of 3.</span></span> <span data-ttu-id="9e9d7-120">기본적으로 모든 조건이 테스트 됨을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-120">It demonstrates that, by default, all conditions are tested.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

<span data-ttu-id="9e9d7-121">`Switch`일치 항목 뒤의 비교를 중지 하려면 문을 사용 합니다 `Break` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-121">To direct the `Switch` to stop comparing after a match, use the `Break` statement.</span></span> <span data-ttu-id="9e9d7-122">문은 `Break` `Switch` 문을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-122">The `Break` statement terminates the `Switch` statement.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

<span data-ttu-id="9e9d7-123">테스트 값이 배열과 같은 컬렉션인 경우 컬렉션의 각 항목이 표시 되는 순서 대로 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-123">If the test value is a collection, such as an array, each item in the collection is evaluated in the order in which it appears.</span></span> <span data-ttu-id="9e9d7-124">다음 예에서는 4와 2를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-124">The following examples evaluates 4 and then 2.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

<span data-ttu-id="9e9d7-125">`Break`다음 예제와 같이 모든 문은 컬렉션에 적용 되 고 각 값에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-125">Any `Break` statements apply to the collection, not to each value, as shown in the following example.</span></span> <span data-ttu-id="9e9d7-126">`Switch`문은 `Break` 값 4 조건의 문으로 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-126">The `Switch` statement is terminated by the `Break` statement in the condition of value 4.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a><span data-ttu-id="9e9d7-127">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e9d7-127">Syntax</span></span>

<span data-ttu-id="9e9d7-128">전체 `Switch` 문 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-128">The complete `Switch` statement syntax is as follows:</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="9e9d7-129">or</span><span class="sxs-lookup"><span data-stu-id="9e9d7-129">or</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="9e9d7-130">매개 변수를 사용 하지 않는 경우는 `Switch` **정확한** 매개 변수를 사용 하는 것과 동일 하 게 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-130">If no parameters are used, `Switch` behaves the same as using the **Exact** parameter.</span></span> <span data-ttu-id="9e9d7-131">값에 대해 대/소문자를 구분 하지 않는 일치를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-131">It performs a case-insensitive match for the value.</span></span> <span data-ttu-id="9e9d7-132">값이 컬렉션인 경우 각 요소는 표시 된 순서 대로 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-132">If the value is a collection, each element is evaluated in the order in which it appears.</span></span>

<span data-ttu-id="9e9d7-133">`Switch`문에는 하나 이상의 condition 문이 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-133">The `Switch` statement must include at least one condition statement.</span></span>

<span data-ttu-id="9e9d7-134">`Default`값이 조건과 일치 하지 않는 경우 절이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-134">The `Default` clause is triggered when the value does not match any of the conditions.</span></span> <span data-ttu-id="9e9d7-135">`Else`문의 절과 동일 `If` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-135">It is equivalent to an `Else` clause in an `If` statement.</span></span> <span data-ttu-id="9e9d7-136">`Default`각 문에는 하나의 절만 사용할 수 `Switch` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-136">Only one `Default` clause is permitted in each `Switch` statement.</span></span>

<span data-ttu-id="9e9d7-137">`Switch` 에는 다음 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-137">`Switch` has the following parameters:</span></span>

- <span data-ttu-id="9e9d7-138">**와일드 카드** -조건이 와일드 카드 문자열 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-138">**Wildcard** - Indicates that the condition is a wildcard string.</span></span> <span data-ttu-id="9e9d7-139">Match 절이 문자열이 아니면 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-139">If the match clause is not a string, the parameter is ignored.</span></span> <span data-ttu-id="9e9d7-140">비교는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-140">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="9e9d7-141">**Exact** -match 절 (문자열 인 경우)이 정확 하 게 일치 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-141">**Exact** - Indicates that the match clause, if it is a string, must match exactly.</span></span> <span data-ttu-id="9e9d7-142">Match 절이 문자열이 아니면이 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-142">If the match clause is not a string, this parameter is ignored.</span></span> <span data-ttu-id="9e9d7-143">비교는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-143">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="9e9d7-144">**CaseSensitive** -대/소문자를 구분 하는 일치를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-144">**CaseSensitive** - Performs a case-sensitive match.</span></span> <span data-ttu-id="9e9d7-145">Match 절이 문자열이 아니면이 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-145">If the match clause is not a string, this parameter is ignored.</span></span>
- <span data-ttu-id="9e9d7-146">**파일**-값 문이 아닌 파일에서 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-146">**File**- Takes input from a file rather than a value statement.</span></span> <span data-ttu-id="9e9d7-147">여러 **파일** 매개 변수가 포함 된 경우에는 마지막 매개 변수만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-147">If multiple **File** parameters are included, only the last one is used.</span></span> <span data-ttu-id="9e9d7-148">파일의 각 줄은 문에 의해 읽고 평가 됩니다 `Switch` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-148">Each line of the file is read and evaluated by the `Switch` statement.</span></span> <span data-ttu-id="9e9d7-149">비교는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-149">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="9e9d7-150">**Regex** -조건에 대 한 값의 정규식 일치를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-150">**Regex** - Performs regular expression matching of the value to the condition.</span></span> <span data-ttu-id="9e9d7-151">Match 절이 문자열이 아니면이 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-151">If the match clause is not a string, this parameter is ignored.</span></span>
  <span data-ttu-id="9e9d7-152">비교는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-152">The comparison is case-insensitive.</span></span> <span data-ttu-id="9e9d7-153">`$matches`자동 변수는 일치 하는 문 블록 내에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-153">The `$matches` automatic variable is available for use within the matching statement block.</span></span>

> [!NOTE]
> <span data-ttu-id="9e9d7-154">**Regex** 및 **와일드 카드** 와 같이 충돌 하는 값을 지정 하는 경우 마지막으로 지정 된 매개 변수가 우선적으로 적용 되며 충돌 하는 모든 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-154">When specifying conflicting values, like **Regex** and **Wildcard**, the last parameter specified takes precedence, and all conflicting parameters are ignored.</span></span> <span data-ttu-id="9e9d7-155">여러 매개 변수 인스턴스도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-155">Multiple instances of parameters are also permitted.</span></span> <span data-ttu-id="9e9d7-156">그러나 마지막으로 사용한 매개 변수만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-156">However, only the last parameter used is effective.</span></span>

<span data-ttu-id="9e9d7-157">이 예제에서 문자열이 나 숫자 데이터가 아닌 개체는에 전달 됩니다 `Switch` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-157">In this example, an object that's not a string or numerical data is passed to the `Switch`.</span></span> <span data-ttu-id="9e9d7-158">는 `Switch` 개체에 대해 문자열 강제 변환을 수행 하 고 결과를 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-158">The `Switch` performs a string coercion on the object and evaluates the outcome.</span></span>

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

<span data-ttu-id="9e9d7-159">이 예제에서는 일치 하는 대/소문자가 없으므로 출력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-159">In this example, there is no matching case so there is no output.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

<span data-ttu-id="9e9d7-160">절을 추가 하 여 `Default` 다른 조건이 충족 되지 않을 때 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-160">By adding the `Default` clause, you can perform an action when no other conditions succeed.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

<span data-ttu-id="9e9d7-161">Case와 일치 하는 단어 "14"의 경우 `-Wildcard` 또는 매개 변수를 사용 해야 합니다 `-Regex` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-161">For the word "fourteen" to match a case you must use the `-Wildcard` or `-Regex` parameter.</span></span>

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

<span data-ttu-id="9e9d7-162">다음 예제에서는 매개 변수를 사용 합니다 `-Regex` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-162">The following example uses the `-Regex` parameter.</span></span>

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

<span data-ttu-id="9e9d7-163">Switch 문 조건은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-163">A Switch statement condition may be either:</span></span>

- <span data-ttu-id="9e9d7-164">값이 입력 값과 비교 되는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-164">An expression whose value is compared to the input value</span></span>
- <span data-ttu-id="9e9d7-165">조건을 충족 하는 경우를 반환 해야 하는 스크립트 블록입니다 `$true` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-165">A script block which should return `$true` if a condition is met.</span></span>

<span data-ttu-id="9e9d7-166">`$_`자동 변수는 switch 문에 전달 되는 값을 포함 하며 조건문의 범위 내에서 평가 하 고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-166">The `$_` automatic variable contains the value passed to the switch statement and is available for evaluation and use within the scope of the condition statements.</span></span>

<span data-ttu-id="9e9d7-167">각 조건에 대 한 작업은 다른 조건의 작업과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-167">The action for each condition is independent of the actions in other conditions.</span></span>

<span data-ttu-id="9e9d7-168">다음 예에서는 문 조건으로 스크립트 블록을 사용 하는 방법을 보여 줍니다 `Switch` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-168">The following example demonstrates the use of script blocks as `Switch` statement conditions.</span></span>

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

<span data-ttu-id="9e9d7-169">값이 여러 조건과 일치 하면 각 조건에 대 한 동작이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-169">If the value matches multiple conditions, the action for each condition is executed.</span></span> <span data-ttu-id="9e9d7-170">이 동작을 변경 하려면 `Break` 또는 키워드를 사용 `Continue` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-170">To change this behavior, use the `Break` or `Continue` keywords.</span></span>

<span data-ttu-id="9e9d7-171">`Break`키워드는 처리를 중지 하 고 `Switch` 문을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-171">The `Break` keyword stops processing and exits the `Switch` statement.</span></span>

<span data-ttu-id="9e9d7-172">`Continue`키워드는 현재 값의 처리를 중지 하지만 후속 값의 처리를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-172">The `Continue` keyword stops processing the current value, but continues processing any subsequent values.</span></span>

<span data-ttu-id="9e9d7-173">다음 예제에서는 숫자 배열을 처리 하 고 홀수 또는 짝수 인지 여부를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e9d7-173">The following example processes an array of numbers and displays if they are odd or even.</span></span> <span data-ttu-id="9e9d7-174">음수는 키워드를 사용 하 여 건너뜁니다 `Continue` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-174">Negative numbers are skipped with the `Continue` keyword.</span></span> <span data-ttu-id="9e9d7-175">숫자가 아닌 값이 발견 되 면 실행이 키워드를 사용 하 여 종료 됩니다 `Break` .</span><span class="sxs-lookup"><span data-stu-id="9e9d7-175">If a non-number is encountered, execution is terminated with the `Break` keyword.</span></span>

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a><span data-ttu-id="9e9d7-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e9d7-176">See also</span></span>

[<span data-ttu-id="9e9d7-177">about_Break</span><span class="sxs-lookup"><span data-stu-id="9e9d7-177">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="9e9d7-178">about_Continue</span><span class="sxs-lookup"><span data-stu-id="9e9d7-178">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="9e9d7-179">about_If</span><span class="sxs-lookup"><span data-stu-id="9e9d7-179">about_If</span></span>](about_If.md)

[<span data-ttu-id="9e9d7-180">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="9e9d7-180">about_Script_Blocks</span></span>](about_Script_Blocks.md)
