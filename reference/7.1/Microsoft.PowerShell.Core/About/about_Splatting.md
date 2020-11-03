---
description: 스 플랫를 사용 하 여 PowerShell에서 명령에 매개 변수를 전달 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: a64cbbe5edd40bf4fc7f9b7347421988d225e666
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221985"
---
# <a name="about-splatting"></a><span data-ttu-id="8fa21-104">스 플랫 정보</span><span class="sxs-lookup"><span data-stu-id="8fa21-104">About Splatting</span></span>

## <a name="short-description"></a><span data-ttu-id="8fa21-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="8fa21-105">Short description</span></span>

<span data-ttu-id="8fa21-106">스 플랫를 사용 하 여 PowerShell에서 명령에 매개 변수를 전달 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-106">Describes how to use splatting to pass parameters to commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="8fa21-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-107">Long description</span></span>

<span data-ttu-id="8fa21-108">스 플랫는 명령에 대 한 매개 변수 값의 컬렉션을 하나의 단위로 전달 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-108">Splatting is a method of passing a collection of parameter values to a command as a unit.</span></span> <span data-ttu-id="8fa21-109">PowerShell은 컬렉션의 각 값을 명령 매개 변수와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-109">PowerShell associates each value in the collection with a command parameter.</span></span> <span data-ttu-id="8fa21-110">Splatted 매개 변수 값은 표준 변수 처럼 보이지만 `@` 달러 기호 () 대신에 기호 ()로 시작 하는 명명 된 스 플랫 변수에 저장 됩니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-110">Splatted parameter values are stored in named splatting variables, which look like standard variables, but begin with an At symbol (`@`) instead of a dollar sign (`$`).</span></span> <span data-ttu-id="8fa21-111">At 기호는 단일 값 대신 값 컬렉션을 전달 하 고 있음을 PowerShell에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-111">The At symbol tells PowerShell that you are passing a collection of values, instead of a single value.</span></span>

<span data-ttu-id="8fa21-112">스 플랫를 사용 하면 명령을 더 짧고 읽기 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-112">Splatting makes your commands shorter and easier to read.</span></span> <span data-ttu-id="8fa21-113">다른 명령 호출에서 스 플랫 값을 다시 사용 하 고 스 플랫를 사용 하 여 `$PSBoundParameters` 자동 변수에서 다른 스크립트 및 함수로 매개 변수 값을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-113">You can reuse the splatting values in different command calls and use splatting to pass parameter values from the `$PSBoundParameters` automatic variable to other scripts and functions.</span></span>

<span data-ttu-id="8fa21-114">Windows PowerShell 3.0 부터는 스 플랫를 사용 하 여 명령의 모든 매개 변수를 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-114">Beginning in Windows PowerShell 3.0, you can also use splatting to represent all parameters of a command.</span></span>

## <a name="syntax"></a><span data-ttu-id="8fa21-115">구문</span><span class="sxs-lookup"><span data-stu-id="8fa21-115">Syntax</span></span>

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

<span data-ttu-id="8fa21-116">매개 변수 이름이 필요 하지 않은 위치 매개 변수에 대 한 매개 변수 값을 제공 하려면 배열 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-116">To provide parameter values for positional parameters, in which parameter names are not required, use the array syntax.</span></span> <span data-ttu-id="8fa21-117">매개 변수 이름 및 값 쌍을 제공 하려면 해시 테이블 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-117">To provide parameter name and value pairs, use the hash table syntax.</span></span> <span data-ttu-id="8fa21-118">Splatted 값은 매개 변수 목록의 어디에 나 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-118">The splatted value can appear anywhere in the parameter list.</span></span>

<span data-ttu-id="8fa21-119">스 플랫 경우 모든 매개 변수를 전달 하기 위해 해시 테이블 또는 배열을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-119">When splatting, you do not need to use a hash table or an array to pass all parameters.</span></span> <span data-ttu-id="8fa21-120">스 플랫를 사용 하 여 일부 매개 변수를 전달 하 고 위치나 매개 변수 이름을 사용 하 여 다른 매개 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-120">You may pass some parameters by using splatting and pass others by position or by parameter name.</span></span> <span data-ttu-id="8fa21-121">또한 각 매개 변수에 두 개 이상의 값을 전달 하지 않도록 단일 명령으로 여러 개체를 스 플랫 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-121">Also, you can splat multiple objects in a single command so you don't pass more than one value for each parameter.</span></span>

<span data-ttu-id="8fa21-122">PowerShell 7.1에서 명령에 매개 변수를 명시적으로 정의 하 여 splatted 매개 변수를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-122">As of PowerShell 7.1, you can override a splatted parameter by explicitly defining a parameter in a command.</span></span>

## <a name="splatting-with-hash-tables"></a><span data-ttu-id="8fa21-123">해시 테이블이 있는 스 플랫</span><span class="sxs-lookup"><span data-stu-id="8fa21-123">Splatting with hash tables</span></span>

<span data-ttu-id="8fa21-124">해시 테이블을 사용 하 여 매개 변수 이름 및 값 쌍을 스 플랫 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-124">Use a hash table to splat parameter name and value pairs.</span></span> <span data-ttu-id="8fa21-125">위치 및 스위치 매개 변수를 포함 하 여 모든 매개 변수 형식에 대해이 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-125">You can use this format for all parameter types, including positional and switch parameters.</span></span>
<span data-ttu-id="8fa21-126">위치 매개 변수는 이름으로 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-126">Positional parameters must be assigned by name.</span></span>

<span data-ttu-id="8fa21-127">다음 예에서는 `Copy-Item` Test.txt 파일을 동일한 디렉터리의 Test2.txt 파일에 복사 하는 두 명령을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-127">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="8fa21-128">첫 번째 예제에서는 매개 변수 이름이 포함 된 일반 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-128">The first example uses the traditional format in which parameter names are included.</span></span>

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

<span data-ttu-id="8fa21-129">두 번째 예제에서는 해시 테이블 스 플랫를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-129">The second example uses hash table splatting.</span></span> <span data-ttu-id="8fa21-130">첫 번째 명령은 매개 변수 이름 및 매개 변수-값 쌍의 해시 테이블을 만들어 변수에 저장 합니다 `$HashArguments` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-130">The first command creates a hash table of parameter-name and parameter-value pairs and stores it in the `$HashArguments` variable.</span></span> <span data-ttu-id="8fa21-131">두 번째 명령은 `$HashArguments` 스 플랫를 사용 하 여 명령에 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-131">The second command uses the `$HashArguments` variable in a command with splatting.</span></span> <span data-ttu-id="8fa21-132">At 기호 ( `@HashArguments` )는 명령에서 달러 기호 ()를 대체 합니다 `$HashArguments` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-132">The At symbol (`@HashArguments`) replaces the dollar sign (`$HashArguments`) in the command.</span></span>

<span data-ttu-id="8fa21-133">**WhatIf** 스위치 매개 변수에 대 한 값을 제공 하려면 또는를 사용 `$True` `$False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-133">To provide a value for the **WhatIf** switch parameter, use `$True` or `$False`.</span></span>

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> <span data-ttu-id="8fa21-134">첫 번째 명령에서 At 기호 ()는 `@` splatted 값이 아닌 해시 테이블을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-134">In the first command, the At symbol (`@`) indicates a hash table, not a splatted value.</span></span> <span data-ttu-id="8fa21-135">PowerShell의 해시 테이블에 대 한 구문은 다음과 같습니다. `@{<name>=<value>; <name>=<value>; ...}`</span><span class="sxs-lookup"><span data-stu-id="8fa21-135">The syntax for hash tables in PowerShell is: `@{<name>=<value>; <name>=<value>; ...}`</span></span>

## <a name="splatting-with-arrays"></a><span data-ttu-id="8fa21-136">배열이 있는 스 플랫</span><span class="sxs-lookup"><span data-stu-id="8fa21-136">Splatting with arrays</span></span>

<span data-ttu-id="8fa21-137">배열을 사용 하 여 매개 변수 이름이 필요 하지 않은 위치 매개 변수의 값을 스 플랫 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-137">Use an array to splat values for positional parameters, which do not require parameter names.</span></span> <span data-ttu-id="8fa21-138">값은 배열의 위치 번호 순서 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-138">The values must be in position-number order in the array.</span></span>

<span data-ttu-id="8fa21-139">다음 예에서는 `Copy-Item` Test.txt 파일을 동일한 디렉터리의 Test2.txt 파일에 복사 하는 두 명령을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-139">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="8fa21-140">첫 번째 예제에서는 매개 변수 이름을 생략 하는 일반적인 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-140">The first example uses the traditional format in which parameter names are omitted.</span></span> <span data-ttu-id="8fa21-141">매개 변수 값은 명령에서 위치 순서 대로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-141">The parameter values appear in position order in the command.</span></span>

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

<span data-ttu-id="8fa21-142">두 번째 예제에서는 스 플랫 배열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-142">The second example uses array splatting.</span></span> <span data-ttu-id="8fa21-143">첫 번째 명령은 매개 변수 값의 배열을 만들어 변수에 저장 합니다 `$ArrayArguments` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-143">The first command creates an array of the parameter values and stores it in the `$ArrayArguments` variable.</span></span> <span data-ttu-id="8fa21-144">값은 배열의 위치 순서에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-144">The values are in position order in the array.</span></span> <span data-ttu-id="8fa21-145">두 번째 명령은 `$ArrayArguments` 스 플랫의 명령에서 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-145">The second command uses the `$ArrayArguments` variable in a command in splatting.</span></span> <span data-ttu-id="8fa21-146">At 기호 ( `@ArrayArguments` )는 명령에서 달러 기호 ()를 대체 합니다 `$ArrayArguments` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-146">The At symbol (`@ArrayArguments`) replaces the dollar sign (`$ArrayArguments`) in the command.</span></span>

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a><span data-ttu-id="8fa21-147">ArgumentList 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="8fa21-147">Using the ArgumentList parameter</span></span>

<span data-ttu-id="8fa21-148">여러 cmdlet에는 매개 변수 값을 cmdlet에 의해 실행 되는 스크립트 블록에 전달 하는 데 사용 되는 **Argumentlist** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-148">Several cmdlets have an **ArgumentList** parameter that is used to pass parameter values to a script block that is executed by the cmdlet.</span></span> <span data-ttu-id="8fa21-149">**Argumentlist** 매개 변수는 스크립트 블록으로 전달 되는 값의 배열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-149">The **ArgumentList** parameter takes an array of values that is passed to the script block.</span></span> <span data-ttu-id="8fa21-150">PowerShell은 효과적으로 배열 스 플랫를 사용 하 여 값을 스크립트 블록의 매개 변수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-150">PowerShell is effectively using array splatting to bind the values to the parameters of the script block.</span></span> <span data-ttu-id="8fa21-151">**Argumentlist** 를 사용 하는 경우 단일 매개 변수에 바인딩된 단일 개체로 배열을 전달 해야 하는 경우에는 배열을 다른 배열의 유일한 요소로 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-151">When using **ArgumentList** , if you need to pass an array as a single object bound to a single parameter, you must wrap the array as the only element of another array.</span></span>

<span data-ttu-id="8fa21-152">다음 예제에는 문자열 배열인 단일 매개 변수를 사용 하는 스크립트 블록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-152">The following example has a script block that takes a single parameter that is an array of strings.</span></span>

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```
<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="8fa21-153">이 예제에서는의 첫 번째 항목만 `$array` 스크립트 블록으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-153">In this example, only the first item in `$array` is passed to the script block.</span></span>

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

<span data-ttu-id="8fa21-154">이 예제에서 `$array` 는 전체 배열이 스크립트 블록에 단일 개체로 전달 되도록 배열에 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-154">In this example, `$array` is wrapped in an array so that the entire array is passed to the script block as a single object.</span></span>

```Output
Hello World!
```

## <a name="examples"></a><span data-ttu-id="8fa21-155">예</span><span class="sxs-lookup"><span data-stu-id="8fa21-155">Examples</span></span>

### <a name="example-1-reuse-splatted-parameters-in-different-commands"></a><span data-ttu-id="8fa21-156">예제 1: 다른 명령에서 splatted 매개 변수 다시 사용</span><span class="sxs-lookup"><span data-stu-id="8fa21-156">Example 1: Reuse splatted parameters in different commands</span></span>

<span data-ttu-id="8fa21-157">이 예제에서는 다양 한 명령에서 splatted 값을 다시 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-157">This example shows how to reuse splatted values in different commands.</span></span> <span data-ttu-id="8fa21-158">이 예제의 명령은 cmdlet을 사용 `Write-Host` 하 여 호스트 프로그램 콘솔에 메시지를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-158">The commands in this example use the `Write-Host` cmdlet to write messages to the host program console.</span></span> <span data-ttu-id="8fa21-159">스 플랫를 사용 하 여 전경 색과 배경색을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-159">It uses splatting to specify the foreground and background colors.</span></span>

<span data-ttu-id="8fa21-160">모든 명령의 색을 변경 하려면 변수 값을 변경 하면 `$Colors` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-160">To change the colors of all commands, just change the value of the `$Colors` variable.</span></span>

<span data-ttu-id="8fa21-161">첫 번째 명령은 매개 변수 이름 및 값의 해시 테이블을 만들고 해시 테이블을 변수에 저장 합니다 `$Colors` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-161">The first command creates a hash table of parameter names and values and stores the hash table in the `$Colors` variable.</span></span>

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

<span data-ttu-id="8fa21-162">두 번째 및 세 번째 명령은 `$Colors` 명령에 스 플랫에 대 한 변수를 사용 합니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-162">The second and third commands use the `$Colors` variable for splatting in a `Write-Host` command.</span></span> <span data-ttu-id="8fa21-163">을 사용 하려면 `$Colors variable` 달러 기호 ( `$Colors` )를 At 기호 ()로 바꿉니다 `@Colors` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-163">To use the `$Colors variable`, replace the dollar sign (`$Colors`) with an At symbol (`@Colors`).</span></span>

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

### <a name="example-2-forward-parameters-using-psboundparameters"></a><span data-ttu-id="8fa21-164">예제 2: $PSBoundParameters를 사용 하 여 매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="8fa21-164">Example 2: Forward parameters using $PSBoundParameters</span></span>

<span data-ttu-id="8fa21-165">이 예에서는 스 플랫 및 자동 변수를 사용 하 여 다른 명령에 매개 변수를 전달 하는 방법을 보여 줍니다 `$PSBoundParameters` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-165">This example shows how to forward their parameters to other commands by using splatting and the `$PSBoundParameters` automatic variable.</span></span>

<span data-ttu-id="8fa21-166">`$PSBoundParameters`자동 변수는 스크립트나 함수를 실행할 때 사용 되는 모든 매개 변수 이름 및 값을 포함 하는 사전 개체 (Collections)입니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-166">The `$PSBoundParameters` automatic variable is a dictionary object (System.Collections.Generic.Dictionary) that contains all the parameter names and values that are used when a script or function is run.</span></span>

<span data-ttu-id="8fa21-167">다음 예에서는 변수를 사용 하 여 `$PSBoundParameters` 함수에서 함수로 전달 된 매개 변수 값을 함수에서 함수로 전달 `Test2` `Test1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-167">In the following example, we use the `$PSBoundParameters` variable to forward the parameters values passed to a script or function from `Test2` function to the `Test1` function.</span></span> <span data-ttu-id="8fa21-168">에서 함수에 대 한 두 호출은 모두 `Test1` `Test2` 스 플랫를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-168">Both calls to the `Test1` function from `Test2` use splatting.</span></span>

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

### <a name="example-3-override-splatted-parameters-with-explicitly-defined-parameters"></a><span data-ttu-id="8fa21-169">예제 3: 명시적으로 정의 된 매개 변수를 사용 하 여 splatted 매개 변수 재정의</span><span class="sxs-lookup"><span data-stu-id="8fa21-169">Example 3: Override splatted parameters with explicitly defined parameters</span></span>

<span data-ttu-id="8fa21-170">이 예에서는 명시적으로 정의 된 매개 변수를 사용 하 여 splatted 매개 변수를 재정의 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-170">This example shows how to override a splatted parameter using explicitly defined parameters.</span></span> <span data-ttu-id="8fa21-171">이는 새 hashtable을 빌드하거나 사용 중인 해시 테이블의 값을 스 플랫로 변경 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-171">This is useful when you don't want to build a new hashtable or change a value in the hashtable you are using to splat.</span></span>

<span data-ttu-id="8fa21-172">`$commonParams`변수는 위치에 가상 컴퓨터를 만들기 위한 매개 변수를 저장 `East US` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-172">The `$commonParams` variable stores the parameters to create virtual machines in the `East US` location.</span></span> <span data-ttu-id="8fa21-173">`$allVms`변수는 만들 가상 컴퓨터의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-173">The `$allVms` variable is a list of virtual machines to create.</span></span> <span data-ttu-id="8fa21-174">이 목록을 반복 하 고를 사용 하 여 `$commonParams` 각 가상 컴퓨터를 만드는 매개 변수를 스 플랫 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-174">We loop through the list and use `$commonParams` to splat the parameters to create each virtual machine.</span></span> <span data-ttu-id="8fa21-175">그러나 `myVM2` 다른 가상 컴퓨터와는 다른 지역에 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-175">However, we want `myVM2` to be created in a different region than the other virtual machines.</span></span> <span data-ttu-id="8fa21-176">Hashtable를 조정 하는 대신에서 `$commonParams` **위치** 매개 변수를 명시적으로 정의 `New-AzVm` 하 여의 키 값을 대체할 수 있습니다 `Location` `$commonParams` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-176">Instead of adjusting the `$commonParams` hashtable, you can explicitly define the **Location** parameter in `New-AzVm` to supersede the value of the `Location` key in `$commonParams`.</span></span>

```powershell
$commonParams = @{
    ResourceGroupName = "myResourceGroup"
    Location = "East US"
    VirtualNetworkName = "myVnet"
    SubnetName = "mySubnet"
    SecurityGroupName = "myNetworkSecurityGroup"
    PublicIpAddressName = "myPublicIpAddress"
}

$allVms = @('myVM1','myVM2','myVM3',)

foreach ($vm in $allVms)
{
    if ($vm -eq 'myVM2')
    {
        New-AzVm @commonParams -Name $vm -Location "West US"
    }
    else
    {
        New-AzVm @commonParams -Name $vm
    }
}
```

## <a name="splatting-command-parameters"></a><span data-ttu-id="8fa21-177">스 플랫 명령 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8fa21-177">Splatting command parameters</span></span>

<span data-ttu-id="8fa21-178">스 플랫를 사용 하 여 명령의 매개 변수를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-178">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="8fa21-179">이 기법은 프록시 함수, 즉 다른 명령을 호출 하는 함수를 만들 때 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-179">This technique is useful when you are creating a proxy function, that is, a function that calls another command.</span></span> <span data-ttu-id="8fa21-180">이 기능은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-180">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="8fa21-181">명령의 매개 변수를 스 플랫 하려면 `@Args` 를 사용 하 여 명령 매개 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-181">To splat the parameters of a command, use `@Args` to represent the command parameters.</span></span> <span data-ttu-id="8fa21-182">이 기법은 명령 매개 변수를 열거 하는 것 보다 쉽지만 호출 된 명령의 매개 변수가 변경 되는 경우에도 수정 하지 않고 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-182">This technique is easier than enumerating command parameters and it works without revision even if the parameters of the called command change.</span></span>

<span data-ttu-id="8fa21-183">이 기능은 할당 되지 `$Args` 않은 모든 매개 변수 값을 포함 하는 자동 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-183">The feature uses the `$Args` automatic variable, which contains all unassigned parameter values.</span></span>

<span data-ttu-id="8fa21-184">예를 들어 다음 함수는 cmdlet를 호출 합니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-184">For example, the following function calls the `Get-Process` cmdlet.</span></span> <span data-ttu-id="8fa21-185">이 함수에서는 `@Args` cmdlet의 모든 매개 변수를 나타냅니다 `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="8fa21-185">In this function, `@Args` represents all the parameters of the `Get-Process` cmdlet.</span></span>

```powershell
function Get-MyProcess { Get-Process @Args }
```

<span data-ttu-id="8fa21-186">함수를 사용 하는 경우 `Get-MyProcess` `@Args` 다음 명령에 표시 된 것 처럼 할당 되지 않은 모든 매개 변수 및 매개 변수 값이에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-186">When you use the `Get-MyProcess` function, all unassigned parameters and parameter values are passed to `@Args`, as shown in the following commands.</span></span>

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

<span data-ttu-id="8fa21-187">`@Args`명시적으로 선언 된 매개 변수가 있는 함수에서을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-187">You can use `@Args` in a function that has explicitly declared parameters.</span></span> <span data-ttu-id="8fa21-188">함수에서 두 번 이상 사용할 수 있지만 `@Args` 다음 예제와 같이 입력 하는 모든 매개 변수는의 모든 인스턴스에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-188">You can use it more than once in a function, but all parameters that you enter are passed to all instances of `@Args`, as shown in the following example.</span></span>

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a><span data-ttu-id="8fa21-189">메모</span><span class="sxs-lookup"><span data-stu-id="8fa21-189">Notes</span></span>

<span data-ttu-id="8fa21-190">**Cmdletbinding** 또는 **매개 변수** 특성을 사용 하 여 고급 함수로 함수를 만드는 경우 `$args` 함수에서 자동 변수를 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-190">If you make a function into an advanced function by using either the **CmdletBinding** or **Parameter** attributes, the `$args` automatic variable is no longer available in the function.</span></span> <span data-ttu-id="8fa21-191">고급 함수에는 명시적 매개 변수 정의가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-191">Advanced functions require explicit parameter definition.</span></span>

<span data-ttu-id="8fa21-192">PowerShell DSC (필요한 상태 구성)가 스 플랫를 사용 하도록 설계 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-192">PowerShell Desired State Configuration (DSC) was not designed to use splatting.</span></span>
<span data-ttu-id="8fa21-193">스 플랫를 사용 하 여 DSC 리소스에 값을 전달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fa21-193">You cannot use splatting to pass values into a DSC resource.</span></span> <span data-ttu-id="8fa21-194">자세한 내용은 Gael Colas ' 문서 [의사 (Pseudo) 스 플랫 DSC 리소스](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8fa21-194">For more information, see Gael Colas' article [Pseudo-Splatting DSC Resources](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fa21-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8fa21-195">See also</span></span>

[<span data-ttu-id="8fa21-196">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="8fa21-196">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="8fa21-197">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="8fa21-197">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="8fa21-198">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="8fa21-198">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="8fa21-199">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="8fa21-199">about_Parameters</span></span>](about_Parameters.md)
