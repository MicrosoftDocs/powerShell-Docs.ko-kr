---
description: 고급 함수에 매개 변수를 추가 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: da21f6fb7d19fa2ffcd9cd6c5eea217792937ae4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605212"
---
# <a name="about-functions-advanced-parameters"></a><span data-ttu-id="b795b-103">함수 고급 매개 변수 정보</span><span class="sxs-lookup"><span data-stu-id="b795b-103">About Functions Advanced Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="b795b-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="b795b-104">Short description</span></span>

<span data-ttu-id="b795b-105">고급 함수에 매개 변수를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-105">Explains how to add parameters to advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="b795b-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-106">Long description</span></span>

<span data-ttu-id="b795b-107">작성 하는 고급 함수에 매개 변수를 추가 하 고 매개 변수 특성 및 인수를 사용 하 여 함수 사용자가 매개 변수를 사용 하 여 제출 하는 매개 변수 값을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-107">You can add parameters to the advanced functions that you write, and use parameter attributes and arguments to limit the parameter values that function users submit with the parameter.</span></span>

<span data-ttu-id="b795b-108">함수에 추가 하는 매개 변수는 PowerShell이 모든 cmdlet 및 고급 기능에 자동으로 추가 하는 일반 매개 변수 외에도 사용자가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-108">The parameters that you add to your function are available to users in addition to the common parameters that PowerShell adds automatically to all cmdlets and advanced functions.</span></span> <span data-ttu-id="b795b-109">PowerShell 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b795b-109">For more information about the PowerShell common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="b795b-110">PowerShell 3.0 부터는에서 스 플랫를 사용 `@Args` 하 여 명령에 매개 변수를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-110">Beginning in PowerShell 3.0, you can use splatting with `@Args` to represent the parameters in a command.</span></span> <span data-ttu-id="b795b-111">스 플랫은 단순 및 고급 함수에서 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-111">Splatting is valid on simple and advanced functions.</span></span> <span data-ttu-id="b795b-112">자세한 내용은 [about_Functions](about_Functions.md) 및 [about_Splatting](about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b795b-112">For more information, see [about_Functions](about_Functions.md) and [about_Splatting](about_Splatting.md).</span></span>

## <a name="type-conversion-of-parameter-values"></a><span data-ttu-id="b795b-113">매개 변수 값의 형식 변환</span><span class="sxs-lookup"><span data-stu-id="b795b-113">Type conversion of parameter values</span></span>

<span data-ttu-id="b795b-114">다른 형식을 필요로 하는 매개 변수에 대 한 인수로 문자열을 제공 하면 PowerShell에서 암시적으로 문자열을 매개 변수 대상 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-114">When you supply strings as arguments to parameters that expect a different type, PowerShell implicitly converts the strings to the parameter target type.</span></span>
<span data-ttu-id="b795b-115">고급 함수는 매개 변수 값의 문화권 고정 구문 분석을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-115">Advanced functions perform culture-invariant parsing of parameter values.</span></span>

<span data-ttu-id="b795b-116">이와 대조적으로, 컴파일된 cmdlet에 대 한 매개 변수를 바인딩하는 동안 문화권 구분 변환이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-116">By contrast, a culture-sensitive conversion is performed during parameter binding for compiled cmdlets.</span></span>

<span data-ttu-id="b795b-117">이 예에서는 매개 변수를 사용 하는 cmdlet 및 스크립트 함수를 만듭니다 `[datetime]` .</span><span class="sxs-lookup"><span data-stu-id="b795b-117">In this example, we create a cmdlet and a script function that take a `[datetime]` parameter.</span></span> <span data-ttu-id="b795b-118">현재 문화권이 독일어 설정을 사용 하도록 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-118">The current culture is changed to use German settings.</span></span>
<span data-ttu-id="b795b-119">독일어 형식 날짜는 매개 변수로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-119">A German-formatted date is passed to the parameter.</span></span>

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

<span data-ttu-id="b795b-120">위와 같이 cmdlet은 문화권 구분 구문 분석을 사용 하 여 문자열을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-120">As shown above, cmdlets use culture-sensitive parsing to convert the string.</span></span>

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

<span data-ttu-id="b795b-121">고급 함수는 문화권 고정 구문 분석을 사용 하며,이로 인해 다음 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-121">Advanced functions use culture-invariant parsing, which results in the following error.</span></span>

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a><span data-ttu-id="b795b-122">정적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b795b-122">Static parameters</span></span>

<span data-ttu-id="b795b-123">정적 매개 변수는 함수에서 항상 사용할 수 있는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-123">Static parameters are parameters that are always available in the function.</span></span>
<span data-ttu-id="b795b-124">PowerShell cmdlet 및 스크립트의 대부분의 매개 변수는 정적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-124">Most parameters in PowerShell cmdlets and scripts are static parameters.</span></span>

<span data-ttu-id="b795b-125">다음 예제에서는 다음과 같은 특징이 있는 **ComputerName** 매개 변수를 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-125">The following example shows the declaration of a **ComputerName** parameter that has the following characteristics:</span></span>

- <span data-ttu-id="b795b-126">필수 (필수)입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-126">It's mandatory (required).</span></span>
- <span data-ttu-id="b795b-127">파이프라인에서 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-127">It takes input from the pipeline.</span></span>
- <span data-ttu-id="b795b-128">문자열 배열을 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-128">It takes an array of strings as input.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a><span data-ttu-id="b795b-129">매개 변수의 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-129">Attributes of parameters</span></span>

<span data-ttu-id="b795b-130">이 섹션에서는 함수 매개 변수에 추가할 수 있는 특성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-130">This section describes the attributes that you can add to function parameters.</span></span>

<span data-ttu-id="b795b-131">모든 특성은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-131">All attributes are optional.</span></span> <span data-ttu-id="b795b-132">그러나 **Cmdletbinding** 특성을 생략 하 고 고급 함수로 인식 되는 경우 함수는 **매개 변수** 특성을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-132">However, if you omit the **CmdletBinding** attribute, then to be recognized as an advanced function, the function must include the **Parameter** attribute.</span></span>

<span data-ttu-id="b795b-133">각 매개 변수 선언에서 하나 이상의 특성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-133">You can add one or multiple attributes in each parameter declaration.</span></span> <span data-ttu-id="b795b-134">매개 변수 선언에 추가할 수 있는 특성의 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-134">There's no limit to the number of attributes that you can add to a parameter declaration.</span></span>

### <a name="parameter-attribute"></a><span data-ttu-id="b795b-135">매개 변수 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-135">Parameter attribute</span></span>

<span data-ttu-id="b795b-136">**Parameter** 특성은 함수 매개 변수의 특성을 선언 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-136">The **Parameter** attribute is used to declare the attributes of function parameters.</span></span>

<span data-ttu-id="b795b-137">**매개 변수** 특성은 선택 사항이 며, 함수 매개 변수에 특성이 필요 하지 않은 경우 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-137">The **Parameter** attribute is optional, and you can omit it if none of the parameters of your functions need attributes.</span></span> <span data-ttu-id="b795b-138">그러나 간단한 함수 대신 고급 함수로 인식 되려면 함수는 **Cmdletbinding** 특성 또는 **Parameter** 특성 중 하나 또는 둘 다가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-138">But, to be recognized as an advanced function, rather than a simple function, a function must have either the **CmdletBinding** attribute or the **Parameter** attribute, or both.</span></span>

<span data-ttu-id="b795b-139">Parameter **특성에** 는 매개 변수의 특징을 정의 하는 인수 (예: 매개 변수가 필수 인지 또는 선택 사항)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-139">The **Parameter** attribute has arguments that define the characteristics of the parameter, such as whether the parameter is mandatory or optional.</span></span>

<span data-ttu-id="b795b-140">다음 구문을 사용 하 여 **매개 변수** 특성, 인수 및 인수 값을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-140">Use the following syntax to declare the **Parameter** attribute, an argument, and an argument value.</span></span> <span data-ttu-id="b795b-141">인수 및 해당 값을 묶는 괄호는 중간에 공백이 없는 **매개 변수** 다음에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-141">The parentheses that enclose the argument and its value must follow **Parameter** with no intervening space.</span></span>

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

<span data-ttu-id="b795b-142">괄호 안에 쉼표를 사용 하 여 인수를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-142">Use commas to separate arguments within the parentheses.</span></span> <span data-ttu-id="b795b-143">다음 구문을 사용 하 여 **매개 변수** 특성의 두 인수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-143">Use the following syntax to declare two arguments of the **Parameter** attribute.</span></span>

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

<span data-ttu-id="b795b-144">Parameter **특성의** 부울 인수 형식은 **매개 변수** 특성에서 생략 될 경우 기본적으로 **False로 설정** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-144">The boolean argument types of the **Parameter** attribute default to **False** when omitted from the **Parameter** attribute.</span></span> <span data-ttu-id="b795b-145">인수 값을로 설정 `$true` 하거나 인수를 이름으로 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-145">Set the argument value to `$true` or just list the argument by name.</span></span> <span data-ttu-id="b795b-146">예를 들어 다음 **매개 변수** 특성은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-146">For example, the following **Parameter** attributes are equivalent.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

<span data-ttu-id="b795b-147">**Cmdletbinding** 특성을 사용 하는 대신 **매개 변수** 특성을 인수 없이 사용 하는 경우 특성 이름 다음에 오는 괄호는 여전히 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-147">If you use the **Parameter** attribute without arguments, as an alternative to using the **CmdletBinding** attribute, the parentheses that follow the attribute name are still required.</span></span>

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a><span data-ttu-id="b795b-148">필수 인수</span><span class="sxs-lookup"><span data-stu-id="b795b-148">Mandatory argument</span></span>

<span data-ttu-id="b795b-149">`Mandatory`인수는 매개 변수가 필요 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-149">The `Mandatory` argument indicates that the parameter is required.</span></span> <span data-ttu-id="b795b-150">이 인수를 지정 하지 않으면 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-150">If this argument isn't specified, the parameter is optional.</span></span>

<span data-ttu-id="b795b-151">다음 예에서는 **ComputerName** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-151">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="b795b-152">인수를 사용 하 여 `Mandatory` 매개 변수를 필수로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-152">It uses the `Mandatory` argument to make the parameter mandatory.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a><span data-ttu-id="b795b-153">Position 인수</span><span class="sxs-lookup"><span data-stu-id="b795b-153">Position argument</span></span>

<span data-ttu-id="b795b-154">`Position`인수는 매개 변수를 명령에 사용할 때 매개 변수 이름이 필요한 지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-154">The `Position` argument determines whether the parameter name is required when the parameter is used in a command.</span></span> <span data-ttu-id="b795b-155">매개 변수 선언에 인수가 포함 된 경우 `Position` 매개 변수 이름을 생략할 수 있으며, PowerShell에서 명명 되지 않은 매개 변수 값을 명령의 명명 되지 않은 매개 변수 값 목록에서 해당 위치나 순서로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-155">When a parameter declaration includes the `Position` argument, the parameter name can be omitted and PowerShell identifies the unnamed parameter value by its position, or order, in the list of unnamed parameter values in the command.</span></span>

<span data-ttu-id="b795b-156">인수를 지정 하지 않으면 매개 변수가 명령에 사용 될 때마다 매개 변수 이름 또는 매개 변수 이름 또는 약어는 매개 변수 `Position` 값 앞에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-156">If the `Position` argument isn't specified, the parameter name, or a parameter name alias or abbreviation, must precede the parameter value whenever the parameter is used in a command.</span></span>

<span data-ttu-id="b795b-157">기본적으로 모든 함수 매개 변수는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-157">By default, all function parameters are positional.</span></span> <span data-ttu-id="b795b-158">PowerShell은 함수에서 매개 변수가 선언 된 순서 대로 매개 변수에 위치 번호를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-158">PowerShell assigns position numbers to parameters in the order in which the parameters are declared in the function.</span></span> <span data-ttu-id="b795b-159">이 기능을 사용 하지 않도록 설정 하려면 `PositionalBinding` **cmdletbinding** 특성의 인수 값을로 설정 합니다 `$False` .</span><span class="sxs-lookup"><span data-stu-id="b795b-159">To disable this feature, set the value of the `PositionalBinding` argument of the **CmdletBinding** attribute to `$False`.</span></span> <span data-ttu-id="b795b-160">`Position`인수는 `PositionalBinding` **cmdletbinding** 특성의 인수 값 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-160">The `Position` argument takes precedence over the value of the `PositionalBinding` argument of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="b795b-161">자세한 내용은 about_Functions_CmdletBindingAttribute을 참조 `PositionalBinding` 하세요 [](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="b795b-161">For more information, see `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="b795b-162">인수의 값은 `Position` 정수로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-162">The value of the `Position` argument is specified as an integer.</span></span> <span data-ttu-id="b795b-163">Position 값 **0** 은 명령의 첫 번째 위치를 나타내고, position 값 **1** 은 명령의 두 번째 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-163">A position value of **0** represents the first position in the command, a position value of **1** represents the second position in the command, and so on.</span></span>

<span data-ttu-id="b795b-164">함수에 위치 매개 변수가 없으면 PowerShell은 매개 변수가 선언 된 순서에 따라 각 매개 변수에 위치를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-164">If a function has no positional parameters, PowerShell assigns positions to each parameter based on the order in which the parameters are declared.</span></span>
<span data-ttu-id="b795b-165">그러나이 할당을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-165">However, as a best practice, don't rely on this assignment.</span></span> <span data-ttu-id="b795b-166">매개 변수를 위치 하려면 인수를 사용 `Position` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-166">When you want parameters to be positional, use the `Position` argument.</span></span>

<span data-ttu-id="b795b-167">다음 예에서는 **ComputerName** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-167">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="b795b-168">`Position`값이 **0** 인 인수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-168">It uses the `Position` argument with a value of **0**.</span></span> <span data-ttu-id="b795b-169">결과적으로 `-ComputerName` 명령에서을 생략 하면 해당 값은 명령의 첫 번째 또는 유일한 명명 되지 않은 매개 변수 값 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-169">As a result, when `-ComputerName` is omitted from command, its value must be the first or only unnamed parameter value in the command.</span></span>

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a><span data-ttu-id="b795b-170">ParameterSetName 인수</span><span class="sxs-lookup"><span data-stu-id="b795b-170">ParameterSetName argument</span></span>

<span data-ttu-id="b795b-171">`ParameterSetName`인수는 매개 변수가 속하는 매개 변수 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-171">The `ParameterSetName` argument specifies the parameter set to which a parameter belongs.</span></span> <span data-ttu-id="b795b-172">매개 변수 집합이 지정 되지 않은 경우 매개 변수는 함수에 정의 된 모든 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-172">If no parameter set is specified, the parameter belongs to all the parameter sets defined by the function.</span></span> <span data-ttu-id="b795b-173">따라서 고유 하려면 각 매개 변수 집합에 다른 매개 변수 집합의 멤버가 아닌 매개 변수가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-173">Therefore, to be unique, each parameter set must have at least one parameter that isn't a member of any other parameter set.</span></span>

> [!NOTE]
> <span data-ttu-id="b795b-174">Cmdlet 또는 함수의 경우 매개 변수 집합은 32 개로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-174">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

<span data-ttu-id="b795b-175">다음 예에서는 매개 변수 집합에서 **ComputerName** 매개 변수 `Computer` , 매개 변수 집합의 **UserName** 매개 변수 `User` 및 두 매개 변수 집합 모두에 **요약** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-175">The following example declares a **ComputerName** parameter in the `Computer` parameter set, a **UserName** parameter in the `User` parameter set, and a **Summary** parameter in both parameter sets.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

<span data-ttu-id="b795b-176">각 인수에는 값을 하나만 지정할 수 있으며 `ParameterSetName` `ParameterSetName` 각 **매개 변수** 특성에는 하나의 인수만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-176">You can specify only one `ParameterSetName` value in each argument and only one `ParameterSetName` argument in each **Parameter** attribute.</span></span> <span data-ttu-id="b795b-177">매개 변수가 둘 이상의 매개 변수 집합에 표시 되도록 지정 하려면 **매개 변수** 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-177">To indicate that a parameter appears in more than one parameter set, add additional **Parameter** attributes.</span></span>

<span data-ttu-id="b795b-178">다음 예제에서는  `Computer` 및 `User` 매개 변수 집합에 요약 매개 변수를 명시적으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-178">The following example explicitly adds the **Summary** parameter to the `Computer` and `User` parameter sets.</span></span> <span data-ttu-id="b795b-179">**요약** 매개 변수는 매개 변수 집합에서 선택 사항이 며 `Computer` `User` 매개 변수 집합에서 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-179">The **Summary** parameter is optional in the `Computer` parameter set and mandatory in the `User` parameter set.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

<span data-ttu-id="b795b-180">매개 변수 집합에 대 한 자세한 내용은 [매개 변수 집합](about_parameter_sets.md)정보를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b795b-180">For more information about parameter sets, see [About Parameter Sets](about_parameter_sets.md).</span></span>

#### <a name="valuefrompipeline-argument"></a><span data-ttu-id="b795b-181">ValueFromPipeline 인수</span><span class="sxs-lookup"><span data-stu-id="b795b-181">ValueFromPipeline argument</span></span>

<span data-ttu-id="b795b-182">`ValueFromPipeline`인수는 매개 변수가 파이프라인 개체의 입력을 허용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-182">The `ValueFromPipeline` argument indicates that the parameter accepts input from a pipeline object.</span></span> <span data-ttu-id="b795b-183">함수가 개체의 속성 뿐만 아니라 전체 개체를 허용 하는 경우이 인수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-183">Specify this argument if the function accepts the entire object, not just a property of the object.</span></span>

<span data-ttu-id="b795b-184">다음 예제에서는 필수 이며 파이프라인에서 함수로 전달 되는 개체를 허용 하는 **ComputerName** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-184">The following example declares a **ComputerName** parameter that's mandatory and accepts an object that's passed to the function from the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a><span data-ttu-id="b795b-185">ValueFromPipelineByPropertyName 인수</span><span class="sxs-lookup"><span data-stu-id="b795b-185">ValueFromPipelineByPropertyName argument</span></span>

<span data-ttu-id="b795b-186">`ValueFromPipelineByPropertyName`인수는 매개 변수가 파이프라인 개체의 속성에서 입력을 허용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-186">The `ValueFromPipelineByPropertyName` argument indicates that the parameter accepts input from a property of a pipeline object.</span></span> <span data-ttu-id="b795b-187">개체 속성의 이름 또는 별칭이 매개 변수와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-187">The object property must have the same name or alias as the parameter.</span></span>

<span data-ttu-id="b795b-188">예를 들어 함수에 **computername** 매개 변수가 있고 파이프 된 개체에 **computername** 속성이 있는 경우 **computername** 속성의 값은 함수의 **computername** 매개 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-188">For example, if the function has a **ComputerName** parameter, and the piped object has a **ComputerName** property, the value of the **ComputerName** property is assigned to the function's **ComputerName** parameter.</span></span>

<span data-ttu-id="b795b-189">다음 예제에서는 필수 이며 파이프라인을 통해 함수에 전달 되는 개체의 **computername** 속성의 입력을 허용 하는 **computername** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-189">The following example declares a **ComputerName** parameter that's mandatory and accepts input from the object's **ComputerName** property that's passed to the function through the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> <span data-ttu-id="b795b-190">파이프라인 입력 () 또는 ()를 허용 하는 형식화 된 매개 변수는 `by Value` `by PropertyName` 매개 변수에 대해 _지연 바인딩_ 스크립트 블록을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-190">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of _delay-bind_ script blocks on the parameter.</span></span>
>
> <span data-ttu-id="b795b-191">_지연 바인드_ 스크립트 블록은 **parameterbinding** 중에 자동으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-191">The _delay-bind_ script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="b795b-192">결과는 매개 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-192">The result is bound to the parameter.</span></span> <span data-ttu-id="b795b-193">또는 형식으로 정의 된 매개 변수에 대해서는 지연 바인딩이 작동 하지 않습니다 `ScriptBlock` `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="b795b-193">Delay binding does not work for parameters defined as type `ScriptBlock` or `System.Object`.</span></span> <span data-ttu-id="b795b-194">스크립트 블록은 호출 되지 _않고_ 를 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-194">The script block is passed through _without_ being invoked.</span></span>
>
> <span data-ttu-id="b795b-195">About_Script_Blocks _에서 지연 바인딩_ 스크립트 블록을 읽을 수 있습니다 [.](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="b795b-195">You can read about _delay-bind_ script blocks here [about_Script_Blocks.md](about_Script_Blocks.md).</span></span>

#### <a name="valuefromremainingarguments-argument"></a><span data-ttu-id="b795b-196">ValueFromRemainingArguments 인수</span><span class="sxs-lookup"><span data-stu-id="b795b-196">ValueFromRemainingArguments argument</span></span>

<span data-ttu-id="b795b-197">`ValueFromRemainingArguments`인수는 매개 변수가 함수의 다른 매개 변수에 할당 되지 않은 명령의 모든 매개 변수 값을 허용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-197">The `ValueFromRemainingArguments` argument indicates that the parameter accepts all the parameter's values in the command that aren't assigned to other parameters of the function.</span></span>

<span data-ttu-id="b795b-198">다음 예제에서는 필수 매개 **변수 및** 함수에 전송 된 나머지 모든 매개 변수 값을 허용 하는 **나머지** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-198">The following example declares a **Value** parameter that's mandatory and a **Remaining** parameter that accepts all the remaining parameter values that are submitted to the function.</span></span>

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> <span data-ttu-id="b795b-199">PowerShell 6.2 이전에는 **ValueFromRemainingArguments** 컬렉션이 인덱스 **0** 에서 단일 엔터티로 조인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-199">Prior to PowerShell 6.2, the **ValueFromRemainingArguments** collection was joined as single entity under index **0**.</span></span>

#### <a name="helpmessage-argument"></a><span data-ttu-id="b795b-200">HelpMessage 인수</span><span class="sxs-lookup"><span data-stu-id="b795b-200">HelpMessage argument</span></span>

<span data-ttu-id="b795b-201">`HelpMessage`인수는 매개 변수 또는 해당 값에 대 한 간략 한 설명을 포함 하는 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-201">The `HelpMessage` argument specifies a string that contains a brief description of the parameter or its value.</span></span> <span data-ttu-id="b795b-202">PowerShell은 명령에 필수 매개 변수 값이 없을 때 표시 되는 프롬프트에이 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-202">PowerShell displays this message in the prompt that appears when a mandatory parameter value is missing from a command.</span></span> <span data-ttu-id="b795b-203">이 인수는 선택적 매개 변수에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-203">This argument has no effect on optional parameters.</span></span>

<span data-ttu-id="b795b-204">다음 예제에서는 필요한 매개 변수 값을 설명 하는 필수 **ComputerName** 매개 변수와 도움말 메시지를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-204">The following example declares a mandatory **ComputerName** parameter and a help message that explains the expected parameter value.</span></span>

<span data-ttu-id="b795b-205">함수에 대 한 다른 [주석 기반 도움말](./about_comment_based_help.md) 구문이 없는 경우 (예: `.SYNOPSIS` )이 메시지는 출력에도 표시 됩니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="b795b-205">If there is no other [comment-based help](./about_comment_based_help.md) syntax for the function (for example, `.SYNOPSIS`) then this message also shows up in `Get-Help` output.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a><span data-ttu-id="b795b-206">Alias 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-206">Alias attribute</span></span>

<span data-ttu-id="b795b-207">**Alias** 특성은 매개 변수에 대 한 대체 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-207">The **Alias** attribute establishes an alternate name for the parameter.</span></span>
<span data-ttu-id="b795b-208">매개 변수에 할당할 수 있는 별칭의 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-208">There's no limit to the number of aliases that you can assign to a parameter.</span></span>

<span data-ttu-id="b795b-209">다음 예제에서는 필수 **ComputerName** 매개 변수에 **CN** 및 **MachineName** 별칭을 추가 하는 매개 변수 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-209">The following example shows a parameter declaration that adds the **CN** and **MachineName** aliases to the mandatory **ComputerName** parameter.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a><span data-ttu-id="b795b-210">SupportsWildcards 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-210">SupportsWildcards attribute</span></span>

<span data-ttu-id="b795b-211">**SupportsWildcards** 특성은 매개 변수가 와일드 카드 값을 허용 함을 나타내는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-211">The **SupportsWildcards** attribute is used to indicate that the parameter accepts wildcard values.</span></span> <span data-ttu-id="b795b-212">다음 예에서는 와일드 카드 값을 지 원하는 필수 **Path** 매개 변수에 대 한 매개 변수 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-212">The following example shows a parameter declaration for a mandatory **Path** parameter that supports wildcard values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

<span data-ttu-id="b795b-213">이 특성을 사용 해도 와일드 카드 지원이 자동으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-213">Using this attribute does not automatically enable wildcard support.</span></span> <span data-ttu-id="b795b-214">Cmdlet 개발자는 와일드 카드 입력을 처리 하는 코드를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-214">The cmdlet developer must implement the code to handle the wildcard input.</span></span> <span data-ttu-id="b795b-215">지원 되는 와일드 카드는 기본 API 또는 PowerShell 공급자에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-215">The wildcards supported can vary according to the underlying API or PowerShell provider.</span></span> <span data-ttu-id="b795b-216">자세한 내용은 [about_Wildcards](about_Wildcards.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b795b-216">For more information, see [about_Wildcards](about_Wildcards.md).</span></span>

### <a name="parameter-and-variable-validation-attributes"></a><span data-ttu-id="b795b-217">매개 변수 및 변수 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-217">Parameter and variable validation attributes</span></span>

<span data-ttu-id="b795b-218">유효성 검사 특성 PowerShell을 통해 사용자가 고급 함수를 호출할 때 제출 하는 매개 변수 값을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-218">Validation attributes direct PowerShell to test the parameter values that users submit when they call the advanced function.</span></span> <span data-ttu-id="b795b-219">매개 변수 값이 테스트에 실패 하면 오류가 발생 하 고 함수가 호출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-219">If the parameter values fail the test, an error is generated and the function isn't called.</span></span> <span data-ttu-id="b795b-220">매개 변수 유효성 검사는 제공 된 입력에만 적용 되며 기본값 등의 다른 값은 유효성이 검사 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-220">Parameter validation is only applied to the input provided and any other values like default values are not validated.</span></span>

<span data-ttu-id="b795b-221">유효성 검사 특성을 사용 하 여 사용자가 변수에 지정할 수 있는 값을 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-221">You can also use the validation attributes to restrict the values that users can specify for variables.</span></span> <span data-ttu-id="b795b-222">유효성 검사 특성과 함께 형식 변환기를 사용 하는 경우 특성 앞에 형식 변환기를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-222">When you use a type converter along with a validation attribute, the type converter has to be defined before the attribute.</span></span>

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a><span data-ttu-id="b795b-223">AllowNull 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-223">AllowNull validation attribute</span></span>

<span data-ttu-id="b795b-224">**Allownull** 특성을 사용 하면 필수 매개 변수의 값이가 됩니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="b795b-224">The **AllowNull** attribute allows the value of a mandatory parameter to be `$null`.</span></span> <span data-ttu-id="b795b-225">다음 예에서는 **null** 값을 가질 수 있는 Hashtable **computerinfo** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-225">The following example declares a hashtable **ComputerInfo** parameter that can have a **null** value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> <span data-ttu-id="b795b-226">문자열 형식에서 null 값을 허용 하지 않으므로 형식 변환기가 string으로 설정 된 경우 **Allownull** 특성은 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-226">The **AllowNull** attribute doesn't work if the type converter is set to string as the string type will not accept a null value.</span></span> <span data-ttu-id="b795b-227">이 시나리오에는 **AllowEmptyString** 특성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-227">You can use the **AllowEmptyString** attribute for this scenario.</span></span>

### <a name="allowemptystring-validation-attribute"></a><span data-ttu-id="b795b-228">AllowEmptyString validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-228">AllowEmptyString validation attribute</span></span>

<span data-ttu-id="b795b-229">**AllowEmptyString** 특성을 사용 하면 필수 매개 변수의 값이 빈 문자열 ()이 될 수 있습니다 `""` .</span><span class="sxs-lookup"><span data-stu-id="b795b-229">The **AllowEmptyString** attribute allows the value of a mandatory parameter to be an empty string (`""`).</span></span> <span data-ttu-id="b795b-230">다음 예에서는 빈 문자열 값을 가질 수 있는 **ComputerName** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-230">The following example declares a **ComputerName** parameter that can have an empty string value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a><span data-ttu-id="b795b-231">AllowEmptyCollection validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-231">AllowEmptyCollection validation attribute</span></span>

<span data-ttu-id="b795b-232">**AllowEmptyCollection** 특성을 사용 하면 필수 매개 변수의 값이 빈 컬렉션이 될 수 있습니다 `@()` .</span><span class="sxs-lookup"><span data-stu-id="b795b-232">The **AllowEmptyCollection** attribute allows the value of a mandatory parameter to be an empty collection `@()`.</span></span> <span data-ttu-id="b795b-233">다음 예제에서는 빈 컬렉션 값을 가질 수 있는 **ComputerName** 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-233">The following example declares a **ComputerName** parameter that can have an empty collection value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a><span data-ttu-id="b795b-234">ValidateCount 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-234">ValidateCount validation attribute</span></span>

<span data-ttu-id="b795b-235">**Validatecount** 특성은 매개 변수가 허용 하는 매개 변수 값의 최소 및 최대 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-235">The **ValidateCount** attribute specifies the minimum and maximum number of parameter values that a parameter accepts.</span></span> <span data-ttu-id="b795b-236">함수를 호출 하는 명령의 매개 변수 값 수가 범위를 벗어나면 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-236">PowerShell generates an error if the number of parameter values in the command that calls the function is outside that range.</span></span>

<span data-ttu-id="b795b-237">다음 매개 변수 선언은 1 ~ 5 개의 매개 변수 값을 사용 하는 **ComputerName** 매개 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-237">The following parameter declaration creates a **ComputerName** parameter that takes one to five parameter values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a><span data-ttu-id="b795b-238">ValidateLength validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-238">ValidateLength validation attribute</span></span>

<span data-ttu-id="b795b-239">**ValidateLength** 특성은 매개 변수 또는 변수 값의 최소 및 최대 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-239">The **ValidateLength** attribute specifies the minimum and maximum number of characters in a parameter or variable value.</span></span> <span data-ttu-id="b795b-240">매개 변수 또는 변수에 지정 된 값의 길이가 범위를 벗어나면 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-240">PowerShell generates an error if the length of a value specified for a parameter or a variable is outside of the range.</span></span>

<span data-ttu-id="b795b-241">다음 예제에서 각 컴퓨터 이름은 1 자에서 10 자 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-241">In the following example, each computer name must have one to ten characters.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="b795b-242">다음 예에서는 변수 값이 최소 1 자에서 `$number` 최대 10 자 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-242">In the following example, the value of the variable `$number` must be a minimum of one character in length, and a maximum of ten characters.</span></span>

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> <span data-ttu-id="b795b-243">이 예제에서의 값은 `01` 작은따옴표로 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-243">In this example, the value of `01` is wrapped in single quotes.</span></span> <span data-ttu-id="b795b-244">**ValidateLength** 특성은 따옴표로 래핑되지 않고 숫자를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-244">The **ValidateLength** attribute won't accept a number without being wrapped in quotes.</span></span>

### <a name="validatepattern-validation-attribute"></a><span data-ttu-id="b795b-245">ValidatePattern validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-245">ValidatePattern validation attribute</span></span>

<span data-ttu-id="b795b-246">**ValidatePattern** 특성은 매개 변수 또는 변수 값과 비교 되는 정규식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-246">The **ValidatePattern** attribute specifies a regular expression that's compared to the parameter or variable value.</span></span> <span data-ttu-id="b795b-247">값이 정규식 패턴과 일치 하지 않으면 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-247">PowerShell generates an error if the value doesn't match the regular expression pattern.</span></span>

<span data-ttu-id="b795b-248">다음 예제에서 매개 변수 값은 네 자리 숫자를 포함 해야 하며 각 숫자는 0에서 9 사이의 숫자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-248">In the following example, the parameter value must contain a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="b795b-249">다음 예에서는 변수 값 `$number` 이 정확히 4 자리 숫자 여야 하며 각 숫자는 0에서 9 사이의 숫자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-249">In the following example, the value of the variable `$number` must be exactly a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a><span data-ttu-id="b795b-250">ValidateRange validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-250">ValidateRange validation attribute</span></span>

<span data-ttu-id="b795b-251">**ValidateRange** 특성은 각 매개 변수 또는 변수 값에 대해 숫자 범위 또는 **ValidateRangeKind** 열거형 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-251">The **ValidateRange** attribute specifies a numeric range or a **ValidateRangeKind** enum value for each parameter or variable value.</span></span>
<span data-ttu-id="b795b-252">값이 범위를 벗어나면 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-252">PowerShell generates an error if any value is outside that range.</span></span>

<span data-ttu-id="b795b-253">**ValidateRangeKind** 열거형은 다음 값을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-253">The **ValidateRangeKind** enum allows for the following values:</span></span>

- <span data-ttu-id="b795b-254">**양수** -0 보다 큰 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-254">**Positive** - A number greater than zero.</span></span>
- <span data-ttu-id="b795b-255">**음수** -0 보다 작은 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-255">**Negative** - A number less than zero.</span></span>
- <span data-ttu-id="b795b-256">**Nonpositive** 아닙니다. 0 보다 작거나 같은 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-256">**NonPositive** - A number less than or equal to zero.</span></span>
- <span data-ttu-id="b795b-257">**음수가** 아닌-0 보다 크거나 같은 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-257">**NonNegative** - A number greater than or equal to zero.</span></span>

<span data-ttu-id="b795b-258">다음 예에서는 **시도** 매개 변수의 값이 0에서 10 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-258">In the following example, the value of the **Attempts** parameter must be between zero and ten.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

<span data-ttu-id="b795b-259">다음 예에서는 변수 값 `$number` 이 0에서 10 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-259">In the following example, the value of the variable `$number` must be between zero and ten.</span></span>

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

<span data-ttu-id="b795b-260">다음 예에서는 변수 값 `$number` 이 0 보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-260">In the following example, the value of the variable `$number` must be greater than zero.</span></span>

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a><span data-ttu-id="b795b-261">ValidateScript validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-261">ValidateScript validation attribute</span></span>

<span data-ttu-id="b795b-262">**ValidateScript** 특성은 매개 변수 또는 변수 값의 유효성을 검사 하는 데 사용 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-262">The **ValidateScript** attribute specifies a script that is used to validate a parameter or variable value.</span></span> <span data-ttu-id="b795b-263">PowerShell은 스크립트에 값을 파이프 하 고 스크립트가를 반환 하거나 스크립트가 예외를 throw 하는 경우 오류를 생성 합니다 `$false` .</span><span class="sxs-lookup"><span data-stu-id="b795b-263">PowerShell pipes the value to the script, and generates an error if the script returns `$false` or if the script throws an exception.</span></span>

<span data-ttu-id="b795b-264">**ValidateScript** 특성을 사용 하는 경우 유효성을 검사할 값이 `$_` 변수에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-264">When you use the **ValidateScript** attribute, the value that's being validated is mapped to the `$_` variable.</span></span> <span data-ttu-id="b795b-265">변수를 사용 `$_` 하 여 스크립트의 값을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-265">You can use the `$_` variable to refer to the value in the script.</span></span>

<span data-ttu-id="b795b-266">다음 예에서는 **eventdate** 매개 변수 값이 현재 날짜 보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-266">In the following example, the value of the **EventDate** parameter must be greater than or equal to the current date.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

<span data-ttu-id="b795b-267">다음 예에서는 변수 값이 `$date` 현재 날짜 및 시간 보다 크거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-267">In the following example, the value of the variable `$date` must be greater than or equal to the current date and time.</span></span>

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> <span data-ttu-id="b795b-268">**ValidateScript** 를 사용 하는 경우 매개 변수에 값을 전달할 수 없습니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="b795b-268">If you use **ValidateScript**, you cannot pass a `$null` value to the parameter.</span></span> <span data-ttu-id="b795b-269">Null 값을 전달 하는 경우 **ValidateScript** 는 인수의 유효성을 검사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-269">When you pass a null value **ValidateScript** can't validate the argument.</span></span>

### <a name="validateset-attribute"></a><span data-ttu-id="b795b-270">ValidateSet 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-270">ValidateSet attribute</span></span>

<span data-ttu-id="b795b-271">**ValidateSet** 특성은 매개 변수 또는 변수에 대 한 유효한 값 집합을 지정 하 고 탭 완성 기능을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-271">The **ValidateSet** attribute specifies a set of valid values for a parameter or variable and enables tab completion.</span></span> <span data-ttu-id="b795b-272">매개 변수 또는 변수 값이 집합의 값과 일치 하지 않는 경우 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-272">PowerShell generates an error if a parameter or variable value doesn't match a value in the set.</span></span> <span data-ttu-id="b795b-273">다음 예제에서 **Detail** 매개 변수의 값은 Low, Average 또는 High만 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-273">In the following example, the value of the **Detail** parameter can only be Low, Average, or High.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

<span data-ttu-id="b795b-274">다음 예에서는 변수 값이 `$flavor` 초콜릿, Strawberry 또는 바닐라 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-274">In the following example, the value of the variable `$flavor` must be either Chocolate, Strawberry, or Vanilla.</span></span>

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

<span data-ttu-id="b795b-275">유효성 검사는 스크립트 내 에서도 변수가 할당 될 때마다 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-275">The validation occurs whenever that variable is assigned even within the script.</span></span> <span data-ttu-id="b795b-276">예를 들어 다음과 같은 경우 런타임에 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-276">For example, the following results in an error at runtime:</span></span>

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a><span data-ttu-id="b795b-277">동적 validateSet 값</span><span class="sxs-lookup"><span data-stu-id="b795b-277">Dynamic validateSet values</span></span>

<span data-ttu-id="b795b-278">**클래스** 를 사용 하 여 런타임에 **ValidateSet** 에 대 한 값을 동적으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-278">You can use a **Class** to dynamically generate the values for **ValidateSet** at runtime.</span></span> <span data-ttu-id="b795b-279">다음 예제에서는 `$Sound` 사용 가능한 사운드 파일에 대 한 세 개의 filesystem 경로를 확인 하는 **SoundNames** 라는 **클래스** 를 통해 변수에 대 한 유효한 값을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-279">In the following example, the valid values for the variable `$Sound` are generated via a **Class** named **SoundNames** that checks three filesystem paths for available sound files:</span></span>

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

<span data-ttu-id="b795b-280">`[SoundNames]`그런 다음 클래스는 다음과 같이 동적 **ValidateSet** 값으로 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-280">The `[SoundNames]` class is then implemented as a dynamic **ValidateSet** value as follows:</span></span>

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a><span data-ttu-id="b795b-281">ValidateNotNull validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-281">ValidateNotNull validation attribute</span></span>

<span data-ttu-id="b795b-282">**ValidateNotNull** 특성은 매개 변수 값이이 될 수 없도록 지정 합니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="b795b-282">The **ValidateNotNull** attribute specifies that the parameter value can't be `$null`.</span></span> <span data-ttu-id="b795b-283">매개 변수 값이 인 경우 PowerShell에서 오류를 생성 `$null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-283">PowerShell generates an error if the parameter value is `$null`.</span></span>

<span data-ttu-id="b795b-284">**ValidateNotNull** 특성은 매개 변수가 선택 사항이 고 형식이 정의 되지 않았거나 null 값을 암시적으로 **개체** 와 같은 형식 변환기를 포함 하는 경우에 사용 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-284">The **ValidateNotNull** attribute is designed to be used when the parameter is optional and the type is undefined or has a type converter that can't implicitly convert a null value like **object**.</span></span> <span data-ttu-id="b795b-285">**문자열과** 같은 null 값을 암시적으로 변환 하는 형식을 지정 하는 경우 **ValidateNotNull** 특성을 사용 하는 경우에도 null 값이 빈 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-285">If you specify a type that that will implicitly convert a null value such as a **string**, the null value is converted to an empty string even when using the **ValidateNotNull** attribute.</span></span> <span data-ttu-id="b795b-286">이 시나리오의 경우 **ValidateNotNullOrEmpty** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-286">For this scenario use the **ValidateNotNullOrEmpty**</span></span>

<span data-ttu-id="b795b-287">다음 예에서는 **ID** 매개 변수의 값이 일 수 없습니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="b795b-287">In the following example, the value of the **ID** parameter can't be `$null`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a><span data-ttu-id="b795b-288">ValidateNotNullOrEmpty validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-288">ValidateNotNullOrEmpty validation attribute</span></span>

<span data-ttu-id="b795b-289">**ValidateNotNullOrEmpty** 특성은 매개 변수 값이이 될 수 없으며 `$null` 빈 문자열 ()이 될 수 없도록 지정 합니다 `""` .</span><span class="sxs-lookup"><span data-stu-id="b795b-289">The **ValidateNotNullOrEmpty** attribute specifies that the parameter value can't be `$null` and can't be an empty string (`""`).</span></span> <span data-ttu-id="b795b-290">함수 호출에 매개 변수를 사용 하지만 해당 값이 `$null` , 빈 문자열 ( `""` ) 또는 빈 배열인 경우 PowerShell에서 오류를 생성 `@()` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-290">PowerShell generates an error if the parameter is used in a function call, but its value is `$null`, an empty string (`""`), or an empty array `@()`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a><span data-ttu-id="b795b-291">ValidateDrive validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-291">ValidateDrive validation attribute</span></span>

<span data-ttu-id="b795b-292">**ValidateDrive** 특성은 매개 변수 값이 경로를 나타내야 하며,이는 허용 된 드라이브만 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-292">The **ValidateDrive** attribute specifies that the parameter value must represent the path, that's referring to allowed drives only.</span></span> <span data-ttu-id="b795b-293">매개 변수 값이 허용 되는 이외의 드라이브를 참조 하는 경우 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-293">PowerShell generates an error if the parameter value refers to drives other than the allowed.</span></span> <span data-ttu-id="b795b-294">드라이브 자체를 제외한 경로 존재는 확인 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-294">Existence of the path, except for the drive itself, isn't verified.</span></span>

<span data-ttu-id="b795b-295">상대 경로를 사용 하는 경우 현재 드라이브가 허용 되는 드라이브 목록에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-295">If you use relative path, the current drive must be in the allowed drive list.</span></span>

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a><span data-ttu-id="b795b-296">ValidateUserDrive 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-296">ValidateUserDrive validation attribute</span></span>

<span data-ttu-id="b795b-297">**Validateuserdrive** 특성은 매개 변수 값이 드라이브를 참조 하는 경로를 나타내야 함을 지정 합니다 `User` .</span><span class="sxs-lookup"><span data-stu-id="b795b-297">The **ValidateUserDrive** attribute specifies that the parameter value must represent the path, that is referring to `User` drive.</span></span> <span data-ttu-id="b795b-298">경로가 다른 드라이브를 참조 하는 경우 PowerShell에서 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-298">PowerShell generates an error if the path refers to a different drive.</span></span> <span data-ttu-id="b795b-299">유효성 검사 특성은 경로의 드라이브 부분만 있는지를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-299">The validation attribute only tests for the existence of the drive portion of the path.</span></span>

<span data-ttu-id="b795b-300">상대 경로를 사용 하는 경우 현재 드라이브가 이어야 합니다 `User` .</span><span class="sxs-lookup"><span data-stu-id="b795b-300">If you use relative path, the current drive must be `User`.</span></span>

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

<span data-ttu-id="b795b-301">`User`충분 한 관리 (JEA) 세션 구성으로 드라이브를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-301">You can define `User` drive in Just Enough Administration (JEA) session configurations.</span></span> <span data-ttu-id="b795b-302">이 예에서는 사용자: 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-302">For this example, we create the User: drive.</span></span>

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a><span data-ttu-id="b795b-303">ValidateTrustedData validation 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-303">ValidateTrustedData validation attribute</span></span>

<span data-ttu-id="b795b-304">이 특성은 PowerShell 6.1.1에서 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-304">This attribute was added in PowerShell 6.1.1.</span></span>

<span data-ttu-id="b795b-305">현재 특성은 PowerShell 자체에서 내부적으로 사용 되며 외부 사용을 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-305">At this time, the attribute is used internally by PowerShell itself and is not intended for external usage.</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="b795b-306">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b795b-306">Dynamic parameters</span></span>

<span data-ttu-id="b795b-307">동적 매개 변수는 특정 조건 에서만 사용할 수 있는 cmdlet, 함수 또는 스크립트의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-307">Dynamic parameters are parameters of a cmdlet, function, or script that are available only under certain conditions.</span></span>

<span data-ttu-id="b795b-308">예를 들어 공급자 드라이브 또는 공급자 드라이브의 특정 경로에서 cmdlet을 사용 하는 경우에만 사용할 수 있는 매개 변수가 여러 공급자 cmdlet에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-308">For example, several provider cmdlets have parameters that are available only when the cmdlet is used in the provider drive, or in a particular path of the provider drive.</span></span> <span data-ttu-id="b795b-309">예를 들어 **Encoding** 매개 변수는 `Add-Content` `Get-Content` `Set-Content` 파일 시스템 드라이브에서 사용 되는 경우에만, 및 cmdlet에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-309">For example, the **Encoding** parameter is available on the `Add-Content`, `Get-Content`, and `Set-Content` cmdlets only when it's used in a file system drive.</span></span>

<span data-ttu-id="b795b-310">또한 함수 명령에 다른 매개 변수를 사용 하거나 다른 매개 변수에 특정 값이 있는 경우에만 표시 되는 매개 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-310">You can also create a parameter that appears only when another parameter is used in the function command or when another parameter has a certain value.</span></span>

<span data-ttu-id="b795b-311">동적 매개 변수는 유용할 수 있지만 필요한 경우에만 사용할 수 있으므로 사용자가 검색 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-311">Dynamic parameters can be useful, but use them only when necessary, because they can be difficult for users to discover.</span></span> <span data-ttu-id="b795b-312">동적 매개 변수를 찾으려면 사용자가 공급자 경로에 있어야 하 고, cmdlet의 **Argumentlist** 매개 변수를 사용 `Get-Command` 하거나,의 **path** 매개 변수를 사용 해야 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="b795b-312">To find a dynamic parameter, the user must be in the provider path, use the **ArgumentList** parameter of the `Get-Command` cmdlet, or use the **Path** parameter of `Get-Help`.</span></span>

<span data-ttu-id="b795b-313">함수 또는 스크립트에 대 한 동적 매개 변수를 만들려면 키워드를 사용 `DynamicParam` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-313">To create a dynamic parameter for a function or script, use the `DynamicParam` keyword.</span></span>

<span data-ttu-id="b795b-314">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-314">The syntax is as follows:</span></span>

`DynamicParam {<statement-list>}`

<span data-ttu-id="b795b-315">문 목록에서 문을 사용 하 여 `If` 함수에서 매개 변수를 사용할 수 있는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-315">In the statement list, use an `If` statement to specify the conditions under which the parameter is available in the function.</span></span>

<span data-ttu-id="b795b-316">Cmdlet을 사용 하 여 `New-Object` 매개 변수를 나타내는 **RuntimeDefinedParameter** 개체를 만들고 해당 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-316">Use the `New-Object` cmdlet to create a **System.Management.Automation.RuntimeDefinedParameter** object to represent the parameter and specify its name.</span></span>

<span data-ttu-id="b795b-317">명령을 사용 하 여 `New-Object` 매개 변수의 특성 (예: **필수**, **위치** 또는 **ValueFromPipeline** 또는 해당 매개 변수 집합)을 나타내는 **system.object** 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-317">You can use a `New-Object` command to create a **System.Management.Automation.ParameterAttribute** object to represent attributes of the parameter, such as **Mandatory**, **Position**, or **ValueFromPipeline** or its parameter set.</span></span>

<span data-ttu-id="b795b-318">다음 예에서는 **이름** 및 **경로** 라는 표준 매개 변수와 **DP1** 이라는 선택적 동적 매개 변수를 사용 하는 샘플 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-318">The following example shows a sample function with standard parameters named **Name** and **Path**, and an optional dynamic parameter named **DP1**.</span></span> <span data-ttu-id="b795b-319">**DP1** 매개 변수는 `PSet1` 매개 변수 집합에 있고 형식이입니다 `Int32` .</span><span class="sxs-lookup"><span data-stu-id="b795b-319">The **DP1** parameter is in the `PSet1` parameter set and has a type of `Int32`.</span></span>
<span data-ttu-id="b795b-320">**DP1** 매개 변수는 `Get-Sample` **Path** 매개 변수 값이로 시작 하는 경우에만 함수에서 사용할 수 있으며 `HKLM:` ,이는 레지스트리 드라이브에서 사용 중임을 나타냅니다 `HKEY_LOCAL_MACHINE` .</span><span class="sxs-lookup"><span data-stu-id="b795b-320">The **DP1** parameter is available in the `Get-Sample` function only when the value of the **Path** parameter starts with `HKLM:`, indicating that it's being used in the `HKEY_LOCAL_MACHINE` registry drive.</span></span>

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

<span data-ttu-id="b795b-321">자세한 내용은 [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b795b-321">For more information, see [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span></span>

## <a name="switch-parameters"></a><span data-ttu-id="b795b-322">Switch 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b795b-322">Switch parameters</span></span>

<span data-ttu-id="b795b-323">스위치 매개 변수는 매개 변수 값이 없는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-323">Switch parameters are parameters with no parameter value.</span></span> <span data-ttu-id="b795b-324">사용 되는 경우에만 적용 되며 효과가 하나만 있는 경우에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-324">They're effective only when they're used and have only one effect.</span></span>

<span data-ttu-id="b795b-325">예를 들어 **powershell.exe** 의 **noprofile** 매개 변수는 스위치 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-325">For example, the **NoProfile** parameter of **powershell.exe** is a switch parameter.</span></span>

<span data-ttu-id="b795b-326">함수에서 스위치 매개 변수를 만들려면 `Switch` 매개 변수 정의에 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-326">To create a switch parameter in a function, specify the `Switch` type in the parameter definition.</span></span>

<span data-ttu-id="b795b-327">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b795b-327">For example:</span></span>

```powershell
Param([Switch]<ParameterName>)
```

<span data-ttu-id="b795b-328">또는 다른 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-328">Or, you can use an another method:</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

<span data-ttu-id="b795b-329">스위치 매개 변수는 쉽게 사용할 수 있으며 더 어려운 구문을 사용 하는 부울 매개 변수 보다 우선적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-329">Switch parameters are easy to use and are preferred over Boolean parameters, which have a more difficult syntax.</span></span>

<span data-ttu-id="b795b-330">예를 들어 스위치 매개 변수를 사용 하기 위해 사용자는 명령에 매개 변수를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-330">For example, to use a switch parameter, the user types the parameter in the command.</span></span>

`-IncludeAll`

<span data-ttu-id="b795b-331">부울 매개 변수를 사용 하기 위해 사용자는 매개 변수와 부울 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-331">To use a Boolean parameter, the user types the parameter and a Boolean value.</span></span>

`-IncludeAll:$true`

<span data-ttu-id="b795b-332">스위치 매개 변수를 만들 때 매개 변수 이름을 신중 하 게 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-332">When creating switch parameters, choose the parameter name carefully.</span></span> <span data-ttu-id="b795b-333">매개 변수 이름은 매개 변수의 효과를 사용자에 게 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-333">Be sure that the parameter name communicates the effect of the parameter to the user.</span></span>
<span data-ttu-id="b795b-334">값을 암시 하는 **필터** 또는 **최대값과** 같은 모호한 용어를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b795b-334">Avoid ambiguous terms, such as **Filter** or **Maximum** that might imply a value is required.</span></span>

## <a name="argumentcompleter-attribute"></a><span data-ttu-id="b795b-335">ArgumentCompleter 특성</span><span class="sxs-lookup"><span data-stu-id="b795b-335">ArgumentCompleter attribute</span></span>

<span data-ttu-id="b795b-336">**ArgumentCompleter** 특성을 사용 하면 특정 매개 변수에 탭 완성 값을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-336">The **ArgumentCompleter** attribute allows you to add tab completion values to a specific parameter.</span></span> <span data-ttu-id="b795b-337">탭 완성이 필요한 각 매개 변수에 대해 **ArgumentCompleter** 특성을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-337">An **ArgumentCompleter** attribute must be defined for each parameter that needs tab completion.</span></span> <span data-ttu-id="b795b-338">**Dynamicparameters** 와 마찬가지로, 사용자가 매개 변수 이름 뒤에 <kbd>tab</kbd> 키를 누르면 런타임에 사용 가능한 값이 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-338">Similar to **DynamicParameters**, the available values are calculated at runtime when the user presses <kbd>Tab</kbd> after the parameter name.</span></span>

<span data-ttu-id="b795b-339">**ArgumentCompleter** 특성을 추가 하려면 값을 결정 하는 스크립트 블록을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-339">To add an **ArgumentCompleter** attribute, you need to define a script block that determines the values.</span></span> <span data-ttu-id="b795b-340">스크립트 블록은 아래 지정 된 순서 대로 다음 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-340">The script block must take the following parameters in the order specified below.</span></span> <span data-ttu-id="b795b-341">값이 메서드에 액세스할 제공 되므로 매개 변수의 이름은 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-341">The parameter's names don't matter as the values are provided positionally.</span></span>

<span data-ttu-id="b795b-342">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-342">The syntax is as follows:</span></span>

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a><span data-ttu-id="b795b-343">ArgumentCompleter 스크립트 블록</span><span class="sxs-lookup"><span data-stu-id="b795b-343">ArgumentCompleter script block</span></span>

<span data-ttu-id="b795b-344">스크립트 블록 매개 변수는 다음 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-344">The script block parameters are set to the following values:</span></span>

- <span data-ttu-id="b795b-345">`$commandName` (위치 0)-이 매개 변수는 스크립트 블록에서 탭 완성 기능을 제공 하는 명령 이름으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-345">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="b795b-346">`$parameterName` (위치 1)-이 매개 변수는 값이 탭 완성이 필요한 매개 변수로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-346">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="b795b-347">`$wordToComplete` (위치 2)-이 매개 변수는 <kbd>Tab</kbd>키를 누를 때 사용자가 제공한 값으로 설정 됩니다. 스크립트 블록은이 값을 사용 하 여 탭 완성 값을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-347">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="b795b-348">`$commandAst` (위치 3)-이 매개 변수는 현재 입력 줄에 대 한 AST (추상 구문 트리)로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-348">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="b795b-349">자세한 내용은 [Ast 클래스](/dotnet/api/system.management.automation.language.ast)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b795b-349">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="b795b-350">`$fakeBoundParameters` (위치 4)-이 매개 변수는 `$PSBoundParameters` 사용자가 <kbd>Tab</kbd>키를 눌러 cmdlet에 대 한를 포함 하는 해시 테이블로 설정 됩니다. 자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b795b-350">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="b795b-351">**ArgumentCompleter** 스크립트 블록은 `ForEach-Object` , `Where-Object` 또는 다른 적합 한 메서드와 같이 파이프라인을 사용 하 여 값을 언 롤 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-351">The **ArgumentCompleter** script block must unroll the values using the pipeline, such as `ForEach-Object`, `Where-Object`, or another suitable method.</span></span>
<span data-ttu-id="b795b-352">값의 배열을 반환 하면 PowerShell에서 전체 배열을 **하나의** 탭 완성 값으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-352">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="b795b-353">다음 예에서는 **값** 매개 변수에 탭 완성 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-353">The following example adds tab completion to the **Value** parameter.</span></span> <span data-ttu-id="b795b-354">**값** 매개 변수만 지정 된 경우 **값** 에 대 한 모든 가능한 값 또는 인수가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-354">If only the **Value** parameter is specified, all possible values, or arguments, for **Value** are displayed.</span></span> <span data-ttu-id="b795b-355">**형식** 매개 변수를 지정 하면 **값** 매개 변수는 해당 형식에 대 한 가능한 값만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-355">When the **Type** parameter is specified, the **Value** parameter only displays the possible values for that type.</span></span>

<span data-ttu-id="b795b-356">또한 `-like` 연산자는 사용자가 다음 명령을 입력 하 고 <kbd>탭</kbd> 완성 기능을 사용 하는 경우에는 **Apple** 만 반환 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b795b-356">In addition, the `-like` operator ensures that if the user types the following command and uses <kbd>Tab</kbd> completion, only **Apple** is returned.</span></span>

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a><span data-ttu-id="b795b-357">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b795b-357">See also</span></span>

[<span data-ttu-id="b795b-358">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b795b-358">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="b795b-359">about_Functions</span><span class="sxs-lookup"><span data-stu-id="b795b-359">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="b795b-360">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="b795b-360">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="b795b-361">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="b795b-361">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="b795b-362">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="b795b-362">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="b795b-363">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="b795b-363">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
