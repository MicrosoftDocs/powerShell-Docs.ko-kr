---
description: PowerShell에서 함수를 만들고 사용 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: 25ef4d3f12752bfabc47d6519988d0da3d5ab0db
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220674"
---
# <a name="about-functions"></a><span data-ttu-id="1cb53-104">함수 정보</span><span class="sxs-lookup"><span data-stu-id="1cb53-104">About Functions</span></span>

## <a name="short-description"></a><span data-ttu-id="1cb53-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="1cb53-105">Short description</span></span>

<span data-ttu-id="1cb53-106">PowerShell에서 함수를 만들고 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-106">Describes how to create and use functions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="1cb53-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-107">Long description</span></span>

<span data-ttu-id="1cb53-108">함수는 사용자가 지정 하는 이름을 가진 PowerShell 문의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-108">A function is a list of PowerShell statements that has a name that you assign.</span></span> <span data-ttu-id="1cb53-109">함수를 실행 하는 경우 함수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-109">When you run a function, you type the function name.</span></span> <span data-ttu-id="1cb53-110">명령 프롬프트에서 입력 한 것 처럼 목록의 문이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-110">The statements in the list run as if you had typed them at the command prompt.</span></span>

<span data-ttu-id="1cb53-111">함수는 다음과 같이 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-111">Functions can be as simple as:</span></span>

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

<span data-ttu-id="1cb53-112">함수는 cmdlet 또는 응용 프로그램 처럼 복잡할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-112">A function can also be as complex as a cmdlet or an application program.</span></span>

<span data-ttu-id="1cb53-113">Cmdlet과 마찬가지로 함수에는 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-113">Like cmdlets, functions can have parameters.</span></span> <span data-ttu-id="1cb53-114">매개 변수 이름, 위치, 스위치 또는 동적 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-114">The parameters can be named, positional, switch, or dynamic parameters.</span></span> <span data-ttu-id="1cb53-115">함수 매개 변수는 명령줄 이나 파이프라인에서 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-115">Function parameters can be read from the command line or from the pipeline.</span></span>

<span data-ttu-id="1cb53-116">함수는 표시 하거나 변수에 할당 하거나 다른 함수 또는 cmdlet에 전달할 수 있는 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-116">Functions can return values that can be displayed, assigned to variables, or passed to other functions or cmdlets.</span></span> <span data-ttu-id="1cb53-117">키워드를 사용 하 여 반환 값을 지정할 수도 있습니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-117">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="1cb53-118">`return`키워드는 함수에서 반환 된 다른 출력에 영향을 주거나 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-118">The `return` keyword does not affect or suppress other output returned from your function.</span></span> <span data-ttu-id="1cb53-119">그러나 키워드는 `return` 해당 줄에서 함수를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-119">However, the `return` keyword exits the function at that line.</span></span> <span data-ttu-id="1cb53-120">자세한 내용은 [about_Return](about_Return.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-120">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="1cb53-121">함수의 문 목록에는, 및 키워드를 사용 하는 다양 한 유형의 문 목록이 포함 될 수 있습니다 `Begin` `Process` `End` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-121">The function's statement list can contain different types of statement lists with the keywords `Begin`, `Process`, and `End`.</span></span> <span data-ttu-id="1cb53-122">이러한 문은 파이프라인의 핸들 입력을 다르게 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-122">These statement lists handle input from the pipeline differently.</span></span>

<span data-ttu-id="1cb53-123">필터는 키워드를 사용 하는 특수 한 종류의 함수입니다 `Filter` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-123">A filter is a special kind of function that uses the `Filter` keyword.</span></span>

<span data-ttu-id="1cb53-124">함수는 cmdlet 처럼 동작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-124">Functions can also act like cmdlets.</span></span> <span data-ttu-id="1cb53-125">프로그래밍을 사용 하지 않고 cmdlet과 마찬가지로 작동 하는 함수를 만들 수 있습니다 `C#` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-125">You can create a function that works just like a cmdlet without using `C#` programming.</span></span> <span data-ttu-id="1cb53-126">자세한 내용은 [about_Functions_Advanced](about_Functions_Advanced.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-126">For more information, see [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="1cb53-127">구문</span><span class="sxs-lookup"><span data-stu-id="1cb53-127">Syntax</span></span>

<span data-ttu-id="1cb53-128">다음은 함수에 대 한 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-128">The following is the syntax for a function:</span></span>

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="1cb53-129">함수에는 다음 항목이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-129">A function includes the following items:</span></span>

- <span data-ttu-id="1cb53-130">`Function`키워드</span><span class="sxs-lookup"><span data-stu-id="1cb53-130">A `Function` keyword</span></span>
- <span data-ttu-id="1cb53-131">범위 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="1cb53-131">A scope (optional)</span></span>
- <span data-ttu-id="1cb53-132">선택한 이름</span><span class="sxs-lookup"><span data-stu-id="1cb53-132">A name that you select</span></span>
- <span data-ttu-id="1cb53-133">임의의 수의 명명 된 매개 변수 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="1cb53-133">Any number of named parameters (optional)</span></span>
- <span data-ttu-id="1cb53-134">하나 이상의 PowerShell 명령이 중괄호로 묶여 있습니다. `{}`</span><span class="sxs-lookup"><span data-stu-id="1cb53-134">One or more PowerShell commands enclosed in braces `{}`</span></span>

<span data-ttu-id="1cb53-135">`Dynamicparam`함수의 키워드 및 동적 매개 변수에 대 한 자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-135">For more information about the `Dynamicparam` keyword and dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="simple-functions"></a><span data-ttu-id="1cb53-136">간단한 함수</span><span class="sxs-lookup"><span data-stu-id="1cb53-136">Simple Functions</span></span>

<span data-ttu-id="1cb53-137">함수는 유용 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-137">Functions do not have to be complicated to be useful.</span></span> <span data-ttu-id="1cb53-138">가장 간단한 함수는 다음과 같은 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-138">The simplest functions have the following format:</span></span>

```
function <function-name> {statements}
```

<span data-ttu-id="1cb53-139">예를 들어 다음 함수는 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-139">For example, the following function starts PowerShell with the Run as Administrator option.</span></span>

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

<span data-ttu-id="1cb53-140">함수를 사용 하려면 다음을 입력 합니다. `Start-PSAdmin`</span><span class="sxs-lookup"><span data-stu-id="1cb53-140">To use the function, type: `Start-PSAdmin`</span></span>

<span data-ttu-id="1cb53-141">함수에 문을 추가 하려면 각 문을 별도의 줄에 입력 하거나 세미콜론을 사용 `;` 하 여 문을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-141">To add statements to the function, type each statement on a separate line, or use a semi-colon `;` to separate the statements.</span></span>

<span data-ttu-id="1cb53-142">예를 들어 다음 함수는 `.jpg` 시작 날짜 이후 변경 된 현재 사용자의 디렉터리에 있는 모든 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-142">For example, the following function finds all `.jpg` files in the current user's directories that were changed after the start date.</span></span>

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

<span data-ttu-id="1cb53-143">유용한 작은 기능의 도구 상자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-143">You can create a toolbox of useful small functions.</span></span> <span data-ttu-id="1cb53-144">이 항목의 뒷부분에 나오는 [about_Profiles](about_Profiles.md) 에 설명 된 대로 PowerShell 프로필에 이러한 함수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-144">Add these functions to your PowerShell profile, as described in [about_Profiles](about_Profiles.md) and later in this topic.</span></span>

## <a name="function-names"></a><span data-ttu-id="1cb53-145">함수 이름</span><span class="sxs-lookup"><span data-stu-id="1cb53-145">Function Names</span></span>

<span data-ttu-id="1cb53-146">함수에 임의의 이름을 지정할 수 있지만 다른 사용자와 공유 하는 함수는 모든 PowerShell 명령에 대해 설정 된 명명 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-146">You can assign any name to a function, but functions that you share with others should follow the naming rules that have been established for all PowerShell commands.</span></span>

<span data-ttu-id="1cb53-147">함수 이름은 동사가 함수에서 수행 하는 작업을 식별 하는 동사-명사 쌍으로 구성 되어야 하며, 명사는 cmdlet이 해당 동작을 수행 하는 항목을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-147">Functions names should consist of a verb-noun pair in which the verb identifies the action that the function performs and the noun identifies the item on which the cmdlet performs its action.</span></span>

<span data-ttu-id="1cb53-148">함수는 모든 PowerShell 명령에 대해 승인 된 표준 동사를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-148">Functions should use the standard verbs that have been approved for all PowerShell commands.</span></span> <span data-ttu-id="1cb53-149">이러한 동사는 사용자가 쉽게 이해할 수 있도록 명령 이름을 간단 하 고 일관 된 상태로 유지 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-149">These verbs help us to keep our command names simple, consistent, and easy for users to understand.</span></span>

<span data-ttu-id="1cb53-150">표준 PowerShell 동사에 대 한 자세한 내용은 Microsoft Docs에서 [승인 된 동사](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-150">For more information about the standard PowerShell verbs, see [Approved Verbs](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in the Microsoft Docs.</span></span>

## <a name="functions-with-parameters"></a><span data-ttu-id="1cb53-151">매개 변수가 있는 함수</span><span class="sxs-lookup"><span data-stu-id="1cb53-151">Functions with Parameters</span></span>

<span data-ttu-id="1cb53-152">명명 된 매개 변수, 위치 매개 변수, 스위치 매개 변수 및 동적 매개 변수를 포함 하 여 함수에 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-152">You can use parameters with functions, including named parameters, positional parameters, switch parameters, and dynamic parameters.</span></span> <span data-ttu-id="1cb53-153">함수의 동적 매개 변수에 대 한 자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-153">For more information about dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="named-parameters"></a><span data-ttu-id="1cb53-154">명명된 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1cb53-154">Named Parameters</span></span>

<span data-ttu-id="1cb53-155">원하는 수의 명명 된 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-155">You can define any number of named parameters.</span></span> <span data-ttu-id="1cb53-156">이 항목의 뒷부분에 설명 된 대로 명명 된 매개 변수에 대 한 기본값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-156">You can include a default value for named parameters, as described later in this topic.</span></span>

<span data-ttu-id="1cb53-157">다음 샘플 구문과 같이 키워드를 사용 하 여 중괄호 안에 매개 변수를 정의할 수 있습니다 `Param` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-157">You can define parameters inside the braces using the `Param` keyword, as shown in the following sample syntax:</span></span>

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

<span data-ttu-id="1cb53-158">`Param`다음 샘플 구문에서와 같이 키워드 없이 중괄호 외부에 매개 변수를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-158">You can also define parameters outside the braces without the `Param` keyword, as shown in the following sample syntax:</span></span>

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

<span data-ttu-id="1cb53-159">다음은이 대체 구문의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-159">Below is an example of this alternative syntax.</span></span>

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

<span data-ttu-id="1cb53-160">첫 번째 방법은 기본 설정 이지만 이러한 두 방법의 차이점은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-160">While the first method is preferred, there is no difference between these two methods.</span></span>

<span data-ttu-id="1cb53-161">함수를 실행 하면 매개 변수에 대해 제공 하는 값이 매개 변수 이름을 포함 하는 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-161">When you run the function, the value you supply for a parameter is assigned to a variable that contains the parameter name.</span></span> <span data-ttu-id="1cb53-162">이 변수의 값은 함수에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-162">The value of that variable can be used in the function.</span></span>

<span data-ttu-id="1cb53-163">다음 예제는 라는 함수입니다 `Get-SmallFiles` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-163">The following example is a function called `Get-SmallFiles`.</span></span> <span data-ttu-id="1cb53-164">이 함수에는 `$Size` 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-164">This function has a `$Size` parameter.</span></span> <span data-ttu-id="1cb53-165">함수는 매개 변수 값 보다 작은 모든 파일 `$Size` 을 표시 하 고 디렉터리를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-165">The function displays all the files that are smaller than the value of the `$Size` parameter, and it excludes directories:</span></span>

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="1cb53-166">함수에서 `$Size` 매개 변수에 대해 정의 된 이름인 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-166">In the function, you can use the `$Size` variable, which is the name defined for the parameter.</span></span>

<span data-ttu-id="1cb53-167">이 함수를 사용 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-167">To use this function, type the following command:</span></span>

```powershell
Get-SmallFiles -Size 50
```

<span data-ttu-id="1cb53-168">매개 변수 이름 없이 명명 된 매개 변수에 대 한 값을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-168">You can also enter a value for a named parameter without the parameter name.</span></span>
<span data-ttu-id="1cb53-169">예를 들어 다음 명령은 **Size** 매개 변수의 이름을 나타내는 명령과 동일한 결과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-169">For example, the following command gives the same result as a command that names the **Size** parameter:</span></span>

```powershell
Get-SmallFiles 50
```

<span data-ttu-id="1cb53-170">매개 변수의 기본값을 정의 하려면 다음 예제의 변형에 표시 된 것 처럼 매개 변수 이름 뒤에 등호와 값을 입력 합니다 `Get-SmallFiles` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-170">To define a default value for a parameter, type an equal sign and the value after the parameter name, as shown in the following variation of the `Get-SmallFiles` example:</span></span>

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="1cb53-171">값 없이를 입력 하 `Get-SmallFiles` 는 경우 함수는 100를에 할당 `$size` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-171">If you type `Get-SmallFiles` without a value, the function assigns 100 to `$size`.</span></span> <span data-ttu-id="1cb53-172">값을 제공 하는 경우 함수는 해당 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-172">If you provide a value, the function uses that value.</span></span>

<span data-ttu-id="1cb53-173">필요에 따라 매개 변수 설명에 **psdefaultvalue** 특성을 추가 하 고 **psdefaultvalue** 의 **help** 속성을 지정 하 여 매개 변수의 기본값을 설명 하는 간단한 도움말 문자열을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-173">Optionally, you can provide a brief help string that describes the default value of your parameter, by adding the **PSDefaultValue** attribute to the description of your parameter, and specifying the **Help** property of **PSDefaultValue**.</span></span> <span data-ttu-id="1cb53-174">함수에서 **Size** 매개 변수의 기본값 (100)을 설명 하는 도움말 문자열을 제공 하려면 `Get-SmallFiles` 다음 예제와 같이 **psdefaultvalue** 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-174">To provide a help string that describes the default value (100) of the **Size** parameter in the `Get-SmallFiles` function, add the **PSDefaultValue** attribute as shown in the following example.</span></span>

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

<span data-ttu-id="1cb53-175">**Psdefaultvalue** 특성 클래스에 대 한 자세한 내용은 [Psdefaultvalue 특성 멤버](/dotnet/api/system.management.automation.psdefaultvalueattribute)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1cb53-175">For more information about the **PSDefaultValue** attribute class, see [PSDefaultValue Attribute Members](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span></span>

### <a name="positional-parameters"></a><span data-ttu-id="1cb53-176">위치 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1cb53-176">Positional Parameters</span></span>

<span data-ttu-id="1cb53-177">위치 매개 변수는 매개 변수 이름이 없는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-177">A positional parameter is a parameter without a parameter name.</span></span> <span data-ttu-id="1cb53-178">PowerShell은 매개 변수 값 순서를 사용 하 여 각 매개 변수 값을 함수의 매개 변수와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-178">PowerShell uses the parameter value order to associate each parameter value with a parameter in the function.</span></span>

<span data-ttu-id="1cb53-179">위치 매개 변수를 사용 하는 경우 함수 이름 뒤에 하나 이상의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-179">When you use positional parameters, type one or more values after the function name.</span></span> <span data-ttu-id="1cb53-180">위치 매개 변수 값은 `$args` 배열 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-180">Positional parameter values are assigned to the `$args` array variable.</span></span>
<span data-ttu-id="1cb53-181">함수 이름 다음에 오는 값은 배열의 첫 번째 위치에 할당 됩니다 `$args` `$args[0]` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-181">The value that follows the function name is assigned to the first position in the `$args` array, `$args[0]`.</span></span>

<span data-ttu-id="1cb53-182">다음 `Get-Extension` 함수는 사용자가 `.txt` 제공 하는 파일 이름에 파일 이름 확장명을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-182">The following `Get-Extension` function adds the `.txt` file name extension to a file name that you supply:</span></span>

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a><span data-ttu-id="1cb53-183">스위치 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1cb53-183">Switch Parameters</span></span>

<span data-ttu-id="1cb53-184">스위치는 값이 필요 없는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-184">A switch is a parameter that does not require a value.</span></span> <span data-ttu-id="1cb53-185">대신 함수 이름, 스위치 매개 변수 이름을 차례로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-185">Instead, you type the function name followed by the name of the switch parameter.</span></span>

<span data-ttu-id="1cb53-186">스위치 매개 변수를 정의 하려면 `[switch]` 다음 예제와 같이 매개 변수 이름 앞에 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-186">To define a switch parameter, specify the type `[switch]` before the parameter name, as shown in the following example:</span></span>

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

<span data-ttu-id="1cb53-187">`On`함수 이름 뒤에 switch 매개 변수를 입력 하면 함수는 "switch on"을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-187">When you type the `On` switch parameter after the function name, the function displays "Switch on".</span></span> <span data-ttu-id="1cb53-188">스위치 매개 변수를 사용 하지 않으면 "Switch off"가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-188">Without the switch parameter, it displays "Switch off".</span></span>

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

<span data-ttu-id="1cb53-189">또한 다음 예제와 같이 함수를 실행할 때 스위치에 **부울** 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-189">You can also assign a **Boolean** value to a switch when you run the function, as shown in the following example:</span></span>

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a><span data-ttu-id="1cb53-190">스 플랫를 사용 하 여 명령 매개 변수 표시</span><span class="sxs-lookup"><span data-stu-id="1cb53-190">Using Splatting to Represent Command Parameters</span></span>

<span data-ttu-id="1cb53-191">스 플랫를 사용 하 여 명령의 매개 변수를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-191">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="1cb53-192">이 기능은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-192">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="1cb53-193">세션에서 명령을 호출 하는 함수에서이 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-193">Use this technique in functions that call commands in the session.</span></span> <span data-ttu-id="1cb53-194">명령 매개 변수를 선언 또는 열거 하거나 명령 매개 변수가 변경 될 때 함수를 변경 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-194">You do not need to declare or enumerate the command parameters, or change the function when command parameters change.</span></span>

<span data-ttu-id="1cb53-195">다음 샘플 함수는 cmdlet를 호출 합니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-195">The following sample function calls the `Get-Command` cmdlet.</span></span> <span data-ttu-id="1cb53-196">명령은를 사용 `@Args` 하 여의 매개 변수를 나타냅니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-196">The command uses `@Args` to represent the parameters of `Get-Command`.</span></span>

```powershell
function Get-MyCommand { Get-Command @Args }
```

<span data-ttu-id="1cb53-197">`Get-Command`함수를 호출할 때의 모든 매개 변수를 사용할 수 있습니다 `Get-MyCommand` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-197">You can use all of the parameters of `Get-Command` when you call the `Get-MyCommand` function.</span></span> <span data-ttu-id="1cb53-198">매개 변수 및 매개 변수 값은를 사용 하 여 명령에 전달 됩니다 `@Args` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-198">The parameters and parameter values are passed to the command using `@Args`.</span></span>

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

<span data-ttu-id="1cb53-199">`@Args`이 기능은 선언 되지 `$Args` 않은 cmdlet 매개 변수와 나머지 인수 값을 나타내는 자동 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-199">The `@Args` feature uses the `$Args` automatic parameter, which represents undeclared cmdlet parameters and values from remaining arguments.</span></span>

<span data-ttu-id="1cb53-200">스 플랫에 대 한 자세한 내용은 [about_Splatting](about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-200">For more information about splatting, see [about_Splatting](about_Splatting.md).</span></span>

## <a name="piping-objects-to-functions"></a><span data-ttu-id="1cb53-201">함수에 개체 파이핑</span><span class="sxs-lookup"><span data-stu-id="1cb53-201">Piping Objects to Functions</span></span>

<span data-ttu-id="1cb53-202">모든 함수는 파이프라인에서 입력을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-202">Any function can take input from the pipeline.</span></span> <span data-ttu-id="1cb53-203">함수에서 `Begin` , 및 키워드를 사용 하 여 파이프라인의 입력을 처리 하는 방법을 제어할 수 있습니다 `Process` `End` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-203">You can control how a function processes input from the pipeline using `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="1cb53-204">다음 샘플 구문에서는 세 가지 키워드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-204">The following sample syntax shows the three keywords:</span></span>

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="1cb53-205">`Begin`문 목록은 함수 시작 부분에서 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-205">The `Begin` statement list runs one time only, at the beginning of the function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1cb53-206">함수에서 또는 블록을 정의 하는 경우 `Begin` `Process` `End` 모든 코드는 해당 블록 내에 상주해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-206">If your function defines a `Begin`, `Process` or `End` block, all of your code must reside inside those blocks.</span></span> <span data-ttu-id="1cb53-207">블록 *을 정의 하는 경우 블록* 외부에서 코드가 인식 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-207">No code will be recognized outside the blocks if *any* of the blocks are defined.</span></span>

<span data-ttu-id="1cb53-208">`Process`문 목록은 파이프라인의 각 개체에 대해 한 번씩 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-208">The `Process` statement list runs one time for each object in the pipeline.</span></span>
<span data-ttu-id="1cb53-209">`Process`블록이 실행 되는 동안 각 파이프라인 개체는 `$_` 한 번에 하나의 파이프라인 개체와 자동 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-209">While the `Process` block is running, each pipeline object is assigned to the `$_` automatic variable, one pipeline object at a time.</span></span>

<span data-ttu-id="1cb53-210">함수는 파이프라인의 모든 개체를 수신 하 고 나면 `End` 문 목록이 한 번 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-210">After the function receives all the objects in the pipeline, the `End` statement list runs one time.</span></span> <span data-ttu-id="1cb53-211">`Begin`, `Process` 또는 키워드를 사용 하지 않으면 `End` 모든 문이 문 목록 처럼 처리 됩니다 `End` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-211">If no `Begin`, `Process`, or `End` keywords are used, all the statements are treated like an `End` statement list.</span></span>

<span data-ttu-id="1cb53-212">다음 함수는 키워드를 사용 합니다 `Process` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-212">The following function uses the `Process` keyword.</span></span> <span data-ttu-id="1cb53-213">함수는 파이프라인의 예제를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-213">The function displays examples from the pipeline:</span></span>

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

<span data-ttu-id="1cb53-214">이 함수를 보여 주기 위해 다음 예제와 같이 쉼표로 구분 된 숫자 목록을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-214">To demonstrate this function, enter an list of numbers separated by commas, as shown in the following example:</span></span>

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

<span data-ttu-id="1cb53-215">파이프라인에서 함수를 사용 하는 경우 함수로 파이프 된 개체가 `$input` 자동 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-215">When you use a function in a pipeline, the objects piped to the function are assigned to the `$input` automatic variable.</span></span> <span data-ttu-id="1cb53-216">함수는 `Begin` 파이프라인에서 개체를 가져오도록 키워드를 사용 하 여 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-216">The function runs statements with the `Begin` keyword before any objects come from the pipeline.</span></span> <span data-ttu-id="1cb53-217">함수는 `End` 파이프라인에서 모든 개체를 받은 후 키워드를 사용 하 여 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-217">The function runs statements with the `End` keyword after all the objects have been received from the pipeline.</span></span>

<span data-ttu-id="1cb53-218">다음 예에서는 `$input` 및 키워드가 있는 자동 변수를 보여 줍니다 `Begin` `End` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-218">The following example shows the `$input` automatic variable with `Begin` and `End` keywords.</span></span>

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

<span data-ttu-id="1cb53-219">파이프라인을 사용 하 여이 함수를 실행 하면 다음과 같은 결과가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-219">If this function is run by using the pipeline, it displays the following results:</span></span>

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

<span data-ttu-id="1cb53-220">`Begin`문이 실행 될 때 함수는 파이프라인의 입력을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-220">When the `Begin` statement runs, the function does not have the input from the pipeline.</span></span> <span data-ttu-id="1cb53-221">`End`함수는 함수 값을 포함 한 후 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-221">The `End` statement runs after the function has the values.</span></span>

<span data-ttu-id="1cb53-222">함수에 키워드가 있는 경우 `Process` 의 각 개체 `$input` 는에서 제거 되 `$input` 고에 할당 됩니다 `$_` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-222">If the function has a `Process` keyword, each object in `$input` is removed from `$input` and assigned to `$_`.</span></span> <span data-ttu-id="1cb53-223">다음 예제에는 `Process` 문 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-223">The following example has a `Process` statement list:</span></span>

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

<span data-ttu-id="1cb53-224">이 예제에서 함수로 파이프 된 각 개체는 문 목록으로 전송 됩니다 `Process` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-224">In this example, each object that is piped to the function is sent to the `Process` statement list.</span></span> <span data-ttu-id="1cb53-225">`Process`문은 각 개체에서 한 번에 하나의 개체에 대해 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-225">The `Process` statements run on each object, one object at a time.</span></span> <span data-ttu-id="1cb53-226">`$input`함수가 키워드에 도달 하면 자동 변수가 비어 `End` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-226">The `$input` automatic variable is empty when the function reaches the `End` keyword.</span></span>

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

<span data-ttu-id="1cb53-227">자세한 내용은 [열거자 사용](about_Automatic_Variables.md#using-enumerators) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-227">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators)</span></span>

## <a name="filters"></a><span data-ttu-id="1cb53-228">필터</span><span class="sxs-lookup"><span data-stu-id="1cb53-228">Filters</span></span>

<span data-ttu-id="1cb53-229">필터는 파이프라인의 각 개체에 대해 실행 되는 함수 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-229">A filter is a type of function that runs on each object in the pipeline.</span></span> <span data-ttu-id="1cb53-230">필터는 블록의 모든 문을 포함 하는 함수와 유사 `Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-230">A filter resembles a function with all its statements in a `Process` block.</span></span>

<span data-ttu-id="1cb53-231">필터의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-231">The syntax of a filter is as follows:</span></span>

```
filter [<scope:>]<name> {<statement list>}
```

<span data-ttu-id="1cb53-232">다음 필터는 파이프라인에서 로그 항목을 가져온 다음 전체 항목이 나 항목의 메시지 부분만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-232">The following filter takes log entries from the pipeline and then displays either the whole entry or only the message portion of the entry:</span></span>

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a><span data-ttu-id="1cb53-233">함수 범위</span><span class="sxs-lookup"><span data-stu-id="1cb53-233">Function Scope</span></span>

<span data-ttu-id="1cb53-234">함수가 생성 된 범위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-234">A function exists in the scope in which it was created.</span></span>

<span data-ttu-id="1cb53-235">함수가 스크립트의 일부인 경우 해당 스크립트 내의 문에서 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-235">If a function is part of a script, the function is available to statements within that script.</span></span> <span data-ttu-id="1cb53-236">기본적으로 스크립트의 함수는 명령 프롬프트에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-236">By default, a function in a script is not available at the command prompt.</span></span>

<span data-ttu-id="1cb53-237">함수의 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-237">You can specify the scope of a function.</span></span> <span data-ttu-id="1cb53-238">예를 들어 함수는 다음 예제에서 전역 범위에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-238">For example, the function is added to the global scope in the following example:</span></span>

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

<span data-ttu-id="1cb53-239">함수가 전역 범위에 있으면 스크립트, 함수 및 명령줄에서 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-239">When a function is in the global scope, you can use the function in scripts, in functions, and at the command line.</span></span>

<span data-ttu-id="1cb53-240">함수는 일반적으로 범위를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-240">Functions normally create a scope.</span></span> <span data-ttu-id="1cb53-241">함수에서 생성 된 항목 (예: 변수)은 함수 범위에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-241">The items created in a function, such as variables, exist only in the function scope.</span></span>

<span data-ttu-id="1cb53-242">PowerShell의 범위에 대 한 자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-242">For more information about scope in PowerShell, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="finding-and-managing-functions-using-the-function-drive"></a><span data-ttu-id="1cb53-243">함수를 사용 하 여 함수 찾기 및 관리: 드라이브</span><span class="sxs-lookup"><span data-stu-id="1cb53-243">Finding and Managing Functions Using the Function: Drive</span></span>

<span data-ttu-id="1cb53-244">PowerShell의 모든 함수와 필터가 자동으로 드라이브에 저장 됩니다 `Function:` .</span><span class="sxs-lookup"><span data-stu-id="1cb53-244">All the functions and filters in PowerShell are automatically stored in the `Function:` drive.</span></span> <span data-ttu-id="1cb53-245">이 드라이브는 PowerShell **함수** 공급자에 의해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-245">This drive is exposed by the PowerShell **Function** provider.</span></span>

<span data-ttu-id="1cb53-246">드라이브를 참조할 때 `Function:` 컴퓨터의 또는 드라이브를 참조할 때와 마찬가지로 **함수** 뒤에 콜론을 입력 `C` `D` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-246">When referring to the `Function:` drive, type a colon after **Function** , just as you would do when referencing the `C` or `D` drive of a computer.</span></span>

<span data-ttu-id="1cb53-247">다음 명령은 PowerShell의 현재 세션에 있는 모든 함수를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-247">The following command displays all the functions in the current session of PowerShell:</span></span>

```powershell
Get-ChildItem function:
```

<span data-ttu-id="1cb53-248">함수의 명령은 함수의 정의 속성에 스크립트 블록으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-248">The commands in the function are stored as a script block in the definition property of the function.</span></span> <span data-ttu-id="1cb53-249">예를 들어 PowerShell과 함께 제공 되는 도움말 함수의 명령을 표시 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-249">For example, to display the commands in the Help function that comes with PowerShell, type:</span></span>

```powershell
(Get-ChildItem function:help).Definition
```

<span data-ttu-id="1cb53-250">다음 구문을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-250">You can also use the following syntax.</span></span>

```powershell
$function:help
```

<span data-ttu-id="1cb53-251">드라이브에 대 한 자세한 내용은 `Function:` **함수** 공급자에 대 한 도움말 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1cb53-251">For more information about the `Function:` drive, see the help topic for the **Function** provider.</span></span> <span data-ttu-id="1cb53-252">`Get-Help Function`.</span><span class="sxs-lookup"><span data-stu-id="1cb53-252">Type `Get-Help Function`.</span></span>

## <a name="reusing-functions-in-new-sessions"></a><span data-ttu-id="1cb53-253">새 세션에서 함수 다시 사용</span><span class="sxs-lookup"><span data-stu-id="1cb53-253">Reusing Functions in New Sessions</span></span>

<span data-ttu-id="1cb53-254">PowerShell 명령 프롬프트에서 함수를 입력 하면 함수가 현재 세션의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-254">When you type a function at the PowerShell command prompt, the function becomes part of the current session.</span></span> <span data-ttu-id="1cb53-255">세션이 종료 될 때까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-255">It is available until the session ends.</span></span>

<span data-ttu-id="1cb53-256">모든 PowerShell 세션에서 함수를 사용 하려면 PowerShell 프로필에 함수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-256">To use your function in all PowerShell sessions, add the function to your PowerShell profile.</span></span> <span data-ttu-id="1cb53-257">프로필에 대한 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-257">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="1cb53-258">PowerShell 스크립트 파일에 함수를 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-258">You can also save your function in a PowerShell script file.</span></span> <span data-ttu-id="1cb53-259">텍스트 파일에 함수를 입력 한 다음 파일 이름 확장명을 사용 하 여 파일을 저장 `.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-259">Type your function in a text file, and then save the file with the `.ps1` file name extension.</span></span>

## <a name="writing-help-for-functions"></a><span data-ttu-id="1cb53-260">함수에 대 한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="1cb53-260">Writing Help for Functions</span></span>

<span data-ttu-id="1cb53-261">`Get-Help`Cmdlet은 함수 및 cmdlet, 공급자 및 스크립트에 대 한 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-261">The `Get-Help` cmdlet gets help for functions, as well as for cmdlets, providers, and scripts.</span></span> <span data-ttu-id="1cb53-262">함수에 대 한 도움말을 보려면를 입력 한 `Get-Help` 다음 함수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-262">To get help for a function, type `Get-Help` followed by the function name.</span></span>

<span data-ttu-id="1cb53-263">예를 들어 함수에 대 한 도움말을 보려면 `Get-MyDisks` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-263">For example, to get help for the `Get-MyDisks` function, type:</span></span>

```powershell
Get-Help Get-MyDisks
```

<span data-ttu-id="1cb53-264">다음 두 가지 방법 중 하나를 사용 하 여 함수에 대 한 도움말을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-264">You can write help for a function by using either of the two following methods:</span></span>

- <span data-ttu-id="1cb53-265">함수에 대 한 Comment-Based 도움말</span><span class="sxs-lookup"><span data-stu-id="1cb53-265">Comment-Based Help for Functions</span></span>

  <span data-ttu-id="1cb53-266">주석에 특수 키워드를 사용 하 여 도움말 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-266">Create a help topic by using special keywords in the comments.</span></span> <span data-ttu-id="1cb53-267">함수에 대 한 주석 기반 도움말을 만들려면 주석을 함수 본문의 시작 또는 끝 이나 함수 키워드 앞의 줄에 배치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-267">To create comment-based help for a function, the comments must be placed at the beginning or end of the function body or on the lines preceding the function keyword.</span></span> <span data-ttu-id="1cb53-268">주석 기반 도움말에 대 한 자세한 내용은 [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-268">For more information about comment-based help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="1cb53-269">함수에 대 한 XML-Based 도움말</span><span class="sxs-lookup"><span data-stu-id="1cb53-269">XML-Based Help for Functions</span></span>

  <span data-ttu-id="1cb53-270">일반적으로 cmdlet에 대해 생성 되는 형식과 같은 XML 기반 도움말 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-270">Create an XML-based help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="1cb53-271">도움말 항목을 여러 언어로 지역화 하는 경우에는 XML 기반 도움말이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-271">XML-based help is required if you are localizing help topics into multiple languages.</span></span>

  <span data-ttu-id="1cb53-272">함수를 XML 기반 도움말 항목과 연결 하려면 `.ExternalHelp` 주석 기반 도움말 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-272">To associate the function with the XML-based help topic, use the `.ExternalHelp` comment-based help keyword.</span></span> <span data-ttu-id="1cb53-273">이 키워드가 없으면 `Get-Help` 함수 도움말 항목을 찾을 수 없습니다 `Get-Help` . 함수에 대 한 호출은 자동 생성 된 도움말만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cb53-273">Without this keyword, `Get-Help` cannot find the function help topic and calls to `Get-Help` for the function return only auto-generated help.</span></span>

  <span data-ttu-id="1cb53-274">키워드에 대 한 자세한 내용은 `ExternalHelp` [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1cb53-274">For more information about the `ExternalHelp` keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="1cb53-275">XML 기반 도움말에 대 한 자세한 내용은 MSDN library에서 [Cmdlet 도움말을 작성 하는 방법](https://go.microsoft.com/fwlink/?LinkID=123415) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1cb53-275">For more information about XML-based help, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cb53-276">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1cb53-276">See also</span></span>

[<span data-ttu-id="1cb53-277">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1cb53-277">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="1cb53-278">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="1cb53-278">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="1cb53-279">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="1cb53-279">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="1cb53-280">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="1cb53-280">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="1cb53-281">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="1cb53-281">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="1cb53-282">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="1cb53-282">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="1cb53-283">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="1cb53-283">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="1cb53-284">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="1cb53-284">about_Parameters</span></span>](about_Parameters.md)

[<span data-ttu-id="1cb53-285">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1cb53-285">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="1cb53-286">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="1cb53-286">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="1cb53-287">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="1cb53-287">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="1cb53-288">about_Function_provider</span><span class="sxs-lookup"><span data-stu-id="1cb53-288">about_Function_provider</span></span>](about_Function_provider.md)
