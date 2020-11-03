---
description: 컴파일된 cmdlet 처럼 함수가 작동 하 게 하는 특성에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: 816bee647702fca4a2b9196491b2525f0338ab31
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222289"
---
# <a name="about-functions-cmdletbindingattribute"></a><span data-ttu-id="c6b4b-104">함수 CmdletBindingAttribute 정보</span><span class="sxs-lookup"><span data-stu-id="c6b4b-104">About Functions CmdletBindingAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="c6b4b-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c6b4b-105">Short description</span></span>
<span data-ttu-id="c6b4b-106">컴파일된 cmdlet 처럼 함수가 작동 하 게 하는 특성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-106">Describes the attribute that makes a function work like a compiled cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="c6b4b-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-107">Long description</span></span>

<span data-ttu-id="c6b4b-108">`CmdletBinding`특성은 c #으로 작성 된 컴파일된 cmdlet 처럼 작동 하 게 하는 함수의 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-108">The `CmdletBinding` attribute is an attribute of functions that makes them operate like compiled cmdlets written in C#.</span></span> <span data-ttu-id="c6b4b-109">Cmdlet의 기능에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-109">It provides access to the features of cmdlets.</span></span>

<span data-ttu-id="c6b4b-110">PowerShell은 특성이 포함 된 함수의 매개 변수를 `CmdletBinding` 컴파일된 cmdlet의 매개 변수를 바인딩하는 것과 동일한 방식으로 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-110">PowerShell binds the parameters of functions that have the `CmdletBinding` attribute in the same way that it binds the parameters of compiled cmdlets.</span></span> <span data-ttu-id="c6b4b-111">`$PSCmdlet`자동 변수는 특성을 사용 하는 함수에 사용할 수 `CmdletBinding` 있지만 `$Args` 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-111">The `$PSCmdlet` automatic variable is available to functions with the `CmdletBinding` attribute, but the `$Args` variable is not available.</span></span>

<span data-ttu-id="c6b4b-112">특성이 있는 함수에서 `CmdletBinding` , 위치 매개 변수가 일치 하지 않는 위치 인수를 알 수 없는 경우 매개 변수 바인딩이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-112">In functions that have the `CmdletBinding` attribute, unknown parameters and positional arguments that have no matching positional parameters cause parameter binding to fail.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b4b-113">컴파일된 cmdlet은 `Cmdlet` 이 항목에 설명 된 특성과 비슷한 필수 특성을 사용 `CmdletBinding` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-113">Compiled cmdlets use the required `Cmdlet` attribute, which is similar to the `CmdletBinding` attribute that is described in this topic.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6b4b-114">구문</span><span class="sxs-lookup"><span data-stu-id="c6b4b-114">Syntax</span></span>

<span data-ttu-id="c6b4b-115">다음 예에서는 특성의 모든 선택적 인수를 지정 하는 함수의 형식을 보여 줍니다 `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="c6b4b-115">The following example shows the format of a function that specifies all the optional arguments of the `CmdletBinding` attribute.</span></span> <span data-ttu-id="c6b4b-116">각 인수에 대 한 간략 한 설명은이 예제를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-116">A brief description of each argument follows this example.</span></span>

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a><span data-ttu-id="c6b4b-117">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="c6b4b-117">ConfirmImpact</span></span>

<span data-ttu-id="c6b4b-118">인수 동작 인수는 **Shouldprocess** 메서드를 호출 하 여 함수의 동작을 확인 해야 **하는 경우** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-118">The **ConfirmImpact** argument specifies when the action of the function should be confirmed by a call to the **ShouldProcess** method.</span></span> <span data-ttu-id="c6b4b-119">**Shouldprocess** 메서드를 호출 하는 경우에는 기본 설정 **인수 값** 이 `$ConfirmPreference` 기본 설정 변수 값 보다 크거나 같은 경우에만 확인 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-119">The call to the **ShouldProcess** method displays a confirmation prompt only when the **ConfirmImpact** argument is equal to or greater than the value of the `$ConfirmPreference` preference variable.</span></span> <span data-ttu-id="c6b4b-120">인수의 기본값은 **Medium** 입니다. **Supportsshouldprocess** 인수도 지정 된 경우에만이 인수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-120">(The default value of the argument is **Medium**.) Specify this argument only when the **SupportsShouldProcess** argument is also specified.</span></span>

<span data-ttu-id="c6b4b-121">확인 요청에 대 한 자세한 내용은 [확인 요청](/powershell/scripting/developer/cmdlet/requesting-confirmation)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-121">For more information about confirmation requests, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

## <a name="defaultparametersetname"></a><span data-ttu-id="c6b4b-122">DefaultParameterSetName</span><span class="sxs-lookup"><span data-stu-id="c6b4b-122">DefaultParameterSetName</span></span>

<span data-ttu-id="c6b4b-123">**DefaultParameterSetName** 인수는 사용할 매개 변수 집합을 확인할 수 없는 경우 PowerShell에서 사용 하려고 하는 매개 변수 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-123">The **DefaultParameterSetName** argument specifies the name of the parameter set that PowerShell will attempt to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="c6b4b-124">각 매개 변수의 고유한 매개 변수를 필수 매개 변수로 설정 하면이 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-124">You can avoid this issue by making the unique parameter of each parameter set a mandatory parameter.</span></span>

## <a name="helpuri"></a><span data-ttu-id="c6b4b-125">HelpURI</span><span class="sxs-lookup"><span data-stu-id="c6b4b-125">HelpURI</span></span>

<span data-ttu-id="c6b4b-126">**HelpURI** 인수는 함수를 설명 하는 온라인 버전의 도움말 항목에 대 한 인터넷 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-126">The **HelpURI** argument specifies the internet address of the online version of the help topic that describes the function.</span></span> <span data-ttu-id="c6b4b-127">**HelpURI** 인수의 값은 "http" 또는 "https"로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-127">The value of the **HelpURI** argument must begin with "http" or "https".</span></span>

<span data-ttu-id="c6b4b-128">**HelpURI** 인수 값은 함수에 대해를 반환 하는 **Commandinfo** 개체의 **HelpURI** 속성 값에 사용 됩니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="c6b4b-128">The **HelpURI** argument value is used for the value of the **HelpURI** property of the **CommandInfo** object that `Get-Command` returns for the function.</span></span>

<span data-ttu-id="c6b4b-129">그러나 도움말 파일이 컴퓨터에 설치 되어 있고 도움말 파일의 **RelatedLinks** 섹션에 있는 첫 번째 링크의 값이 uri 이거나 주석 기반 도움말의 첫 번째 지시문의 값이 uri 인 경우에는 `.Link` 도움말 파일의 Uri가 함수의 **HelpUri** 속성 값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-129">However, when help files are installed on the computer and the value of the first link in the **RelatedLinks** section of the help file is a URI, or the value of the first `.Link` directive in comment-based help is a URI, the URI in the help file is used as the value of the **HelpUri** property of the function.</span></span>

<span data-ttu-id="c6b4b-130">`Get-Help`명령에의 **online** 매개 변수가 지정 된 경우 cmdlet은 **HelpURI** 속성의 값을 사용 하 여 함수 도움말 항목의 온라인 버전을 찾습니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="c6b4b-130">The `Get-Help` cmdlet uses the value of the **HelpURI** property to locate the online version of the function help topic when the **Online** parameter of `Get-Help` is specified in a command.</span></span>

## <a name="supportspaging"></a><span data-ttu-id="c6b4b-131">SupportsPaging</span><span class="sxs-lookup"><span data-stu-id="c6b4b-131">SupportsPaging</span></span>

<span data-ttu-id="c6b4b-132">**Supportspaging** 인수는 **첫 번째** , **Skip** 및 **IncludeTotalCount** 매개 변수를 함수에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-132">The **SupportsPaging** argument adds the **First** , **Skip** , and **IncludeTotalCount** parameters to the function.</span></span> <span data-ttu-id="c6b4b-133">이러한 매개 변수를 통해 사용자는 매우 큰 결과 집합에서 출력을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-133">These parameters allow users to select output from a very large result set.</span></span> <span data-ttu-id="c6b4b-134">이 인수는 SQL database와 같은 데이터 선택을 지 원하는 대량 데이터 저장소에서 데이터를 반환 하는 cmdlet 및 함수를 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-134">This argument is designed for cmdlets and functions that return data from large data stores that support data selection, such as an SQL database.</span></span>

<span data-ttu-id="c6b4b-135">이 인수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-135">This argument was introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="c6b4b-136">**First** : 첫 번째 ' n ' 개의 개체만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-136">**First** : Gets only the first 'n' objects.</span></span>
- <span data-ttu-id="c6b4b-137">**Skip** : 첫 번째 ' n ' 개체를 무시 한 다음 나머지 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-137">**Skip** :  Ignores the first 'n' objects and then gets the remaining objects.</span></span>
- <span data-ttu-id="c6b4b-138">**IncludeTotalCount** : 데이터 집합의 개체 수 (정수)와 개체를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-138">**IncludeTotalCount** : Reports the number of objects in the data set (an integer) followed by the objects.</span></span> <span data-ttu-id="c6b4b-139">Cmdlet이 총 개수를 확인할 수 없으면 "알 수 없는 총 개수"를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-139">If the cmdlet cannot determine the total count, it returns "Unknown total count".</span></span>

<span data-ttu-id="c6b4b-140">PowerShell에는 반환할 총 개수 값을 가져오고 총 개수 값의 정확도를 포함 하는 도우미 메서드인 **NewTotalCount** 이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-140">PowerShell includes **NewTotalCount** , a helper method that gets the total count value to return and includes an estimate of the accuracy of the total count value.</span></span>

<span data-ttu-id="c6b4b-141">다음 샘플 함수는 고급 함수에 페이징 매개 변수에 대 한 지원을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-141">The following sample function shows how to add support for the paging parameters to an advanced function.</span></span>

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="c6b4b-142">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="c6b4b-142">SupportsShouldProcess</span></span>

<span data-ttu-id="c6b4b-143">**Supportsshouldprocess** 인수는 **Confirm** 및 **WhatIf** 매개 변수를 함수에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-143">The **SupportsShouldProcess** argument adds **Confirm** and **WhatIf** parameters to the function.</span></span> <span data-ttu-id="c6b4b-144">**Confirm** 매개 변수는 파이프라인의 각 개체에 대해 명령을 실행 하기 전에 사용자에 게 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-144">The **Confirm** parameter prompts the user before it runs the command on each object in the pipeline.</span></span> <span data-ttu-id="c6b4b-145">**WhatIf** 매개 변수는 명령을 실행 하는 대신 명령이 수행 하는 변경 내용을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-145">The **WhatIf** parameter lists the changes that the command would make, instead of running the command.</span></span>

## <a name="positionalbinding"></a><span data-ttu-id="c6b4b-146">PositionalBinding</span><span class="sxs-lookup"><span data-stu-id="c6b4b-146">PositionalBinding</span></span>

<span data-ttu-id="c6b4b-147">**Positionalbinding** 인수는 함수의 매개 변수가 기본적으로 위치 인지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-147">The **PositionalBinding** argument determines whether parameters in the function are positional by default.</span></span> <span data-ttu-id="c6b4b-148">기본값은 `$True`입니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-148">The default value is `$True`.</span></span> <span data-ttu-id="c6b4b-149">값으로 **Positionalbinding** 인수를 사용 `$False` 하 여 위치 바인딩을 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-149">You can use the **PositionalBinding** argument with a value of `$False` to disable positional binding.</span></span>

<span data-ttu-id="c6b4b-150">**Positionalbinding** 인수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-150">The **PositionalBinding** argument is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="c6b4b-151">매개 변수가 위치 이면 매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-151">When parameters are positional, the parameter name is optional.</span></span>
<span data-ttu-id="c6b4b-152">PowerShell은 함수 명령에 있는 명명 되지 않은 매개 변수 값의 순서나 위치에 따라 함수 매개 변수와 명명 되지 않은 매개 변수 값을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-152">PowerShell associates unnamed parameter values with the function parameters according to the order or position of the unnamed parameter values in the function command.</span></span>

<span data-ttu-id="c6b4b-153">매개 변수가 위치 ("명명 된")가 아닌 경우 명령에 매개 변수 이름 (또는 이름의 약어 또는 별칭)이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-153">When parameters are not positional (they are "named"), the parameter name (or an abbreviation or alias of the name) is required in the command.</span></span>

<span data-ttu-id="c6b4b-154">**Positionalbinding** 이 인 경우 `$True` 함수 매개 변수는 기본적으로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-154">When **PositionalBinding** is `$True`, function parameters are positional by default.</span></span> <span data-ttu-id="c6b4b-155">PowerShell은 함수에 선언 된 순서 대로 매개 변수에 위치 번호를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-155">PowerShell assigns position number to the parameters in the order in which they are declared in the function.</span></span>

<span data-ttu-id="c6b4b-156">**Positionalbinding** 이 인 경우 `$False` 함수 매개 변수는 기본적으로 위치에 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-156">When **PositionalBinding** is `$False`, function parameters are not positional by default.</span></span> <span data-ttu-id="c6b4b-157">**매개 변수 특성의** **Position** 인수를 매개 변수에 선언 하지 않으면 매개 변수가 함수에 사용 될 때 매개 변수 이름 (또는 별칭 또는 약어)이 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-157">Unless the **Position** argument of the **Parameter** attribute is declared on the parameter, the parameter name (or an alias or abbreviation) must be included when the parameter is used in a function.</span></span>

<span data-ttu-id="c6b4b-158">**매개 변수** 특성의 **Position** 인수가 **positionalbinding** 기본값 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-158">The **Position** argument of the **Parameter** attribute takes precedence over the **PositionalBinding** default value.</span></span> <span data-ttu-id="c6b4b-159">**Position** 인수를 사용 하 여 매개 변수에 대 한 위치 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-159">You can use the **Position** argument to specify a position value for a parameter.</span></span> <span data-ttu-id="c6b4b-160">**Position** 인수에 대 한 자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-160">For more information about the **Position** argument, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="notes"></a><span data-ttu-id="c6b4b-161">메모</span><span class="sxs-lookup"><span data-stu-id="c6b4b-161">Notes</span></span>

<span data-ttu-id="c6b4b-162">**SupportsTransactions** 인수는 고급 함수에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6b4b-162">The **SupportsTransactions** argument is not supported in advanced functions.</span></span>

## <a name="keywords"></a><span data-ttu-id="c6b4b-163">키워드</span><span class="sxs-lookup"><span data-stu-id="c6b4b-163">Keywords</span></span>

<span data-ttu-id="c6b4b-164">about_Functions_CmdletBinding_Attribute</span><span class="sxs-lookup"><span data-stu-id="c6b4b-164">about_Functions_CmdletBinding_Attribute</span></span>

## <a name="see-also"></a><span data-ttu-id="c6b4b-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6b4b-165">See also</span></span>

[<span data-ttu-id="c6b4b-166">about_Functions</span><span class="sxs-lookup"><span data-stu-id="c6b4b-166">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="c6b4b-167">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="c6b4b-167">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="c6b4b-168">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="c6b4b-168">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="c6b4b-169">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="c6b4b-169">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="c6b4b-170">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="c6b4b-170">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
