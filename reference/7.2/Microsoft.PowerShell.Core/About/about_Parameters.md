---
description: PowerShell에서 명령 매개 변수를 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: c9d7ab62c13a7cafcf93103f9a70f6575d5dd7b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600867"
---
# <a name="about-parameters"></a><span data-ttu-id="5bf50-103">매개 변수 정보</span><span class="sxs-lookup"><span data-stu-id="5bf50-103">About Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="5bf50-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5bf50-104">Short description</span></span>
<span data-ttu-id="5bf50-105">PowerShell에서 명령 매개 변수를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-105">Describes how to work with command parameters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5bf50-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-106">Long description</span></span>

<span data-ttu-id="5bf50-107">Cmdlet, 함수 및 스크립트와 같은 대부분의 PowerShell 명령은 사용자가 옵션을 선택 하거나 입력을 제공할 수 있도록 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-107">Most PowerShell commands, such as cmdlets, functions, and scripts, rely on parameters to allow users to select options or provide input.</span></span> <span data-ttu-id="5bf50-108">매개 변수는 명령 이름 뒤에 다음과 같은 형식으로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-108">The parameters follow the command name and have the following form:</span></span>

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

<span data-ttu-id="5bf50-109">매개 변수의 이름 앞에는 하이픈 (-)이 붙습니다 .이는 하이픈 뒤의 단어가 매개 변수 이름 임을 PowerShell에 신호로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-109">The name of the parameter is preceded by a hyphen (-), which signals to PowerShell that the word following the hyphen is a parameter name.</span></span> <span data-ttu-id="5bf50-110">매개 변수 이름 및 값은 공백이 나 콜론 문자로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-110">The parameter name and value can be separated by a space or a colon character.</span></span> <span data-ttu-id="5bf50-111">일부 매개 변수는 매개 변수 값을 요구 하거나 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-111">Some parameters do not require or accept a parameter value.</span></span> <span data-ttu-id="5bf50-112">다른 매개 변수에는 값이 필요 하지만 명령에는 매개 변수 이름이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-112">Other parameters require a value, but do not require the parameter name in the command.</span></span>

<span data-ttu-id="5bf50-113">매개 변수의 형식과 해당 매개 변수의 요구 사항은 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-113">The type of parameters and the requirements for those parameters vary.</span></span> <span data-ttu-id="5bf50-114">명령의 매개 변수에 대 한 정보를 확인 하려면 cmdlet을 사용 `Get-Help` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-114">To find information about the parameters of a command, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="5bf50-115">예를 들어 cmdlet의 매개 변수에 대 한 정보 `Get-ChildItem` 를 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-115">For example, to find information about the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="5bf50-116">스크립트의 매개 변수에 대 한 정보를 찾으려면 스크립트 파일의 전체 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-116">To find information about the parameters of a script, use the full path to the script file.</span></span> <span data-ttu-id="5bf50-117">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="5bf50-117">For example:</span></span>

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

<span data-ttu-id="5bf50-118">`Get-Help`Cmdlet은 설명, 명령 구문, 매개 변수에 대 한 정보 및 명령에서 매개 변수를 사용 하는 방법을 보여 주는 예제를 포함 하 여 명령에 대 한 다양 한 세부 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-118">The `Get-Help` cmdlet returns various details about the command, including a description, the command syntax, information about the parameters, and examples showing how to use the parameters in a command.</span></span>

<span data-ttu-id="5bf50-119">Cmdlet의 Parameter 매개 변수를 사용 하 여 `Get-Help` 특정 매개 변수에 대 한 정보를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-119">You can also use the Parameter parameter of the `Get-Help` cmdlet to find information about a particular parameter.</span></span> <span data-ttu-id="5bf50-120">또는 **매개** 변수 매개 변수를 와일드 카드 문자 () 값과 함께 사용 `*` 하 여 명령의 모든 매개 변수에 대 한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-120">Or, you can use the **Parameter** parameter with the wildcard character ( `*` ) value to find information about all parameters of the command.</span></span> <span data-ttu-id="5bf50-121">예를 들어 다음 명령은 cmdlet의 모든 매개 변수에 대 한 정보를 가져옵니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="5bf50-121">For example, the following command gets information about all parameters of the `Get-Member` cmdlet:</span></span>

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a><span data-ttu-id="5bf50-122">기본 매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="5bf50-122">Default parameter values</span></span>

<span data-ttu-id="5bf50-123">선택적 매개 변수에는 매개 변수가 명령에 지정 되지 않은 경우 사용 되거나 사용 되는 값인 기본값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-123">Optional parameters have a default value, which is the value that is used or assumed when the parameter is not specified in the command.</span></span>

<span data-ttu-id="5bf50-124">예를 들어 많은 cmdlet의 **ComputerName** 매개 변수 기본값은 로컬 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-124">For example, the default value of the **ComputerName** parameter of many cmdlets is the name of the local computer.</span></span> <span data-ttu-id="5bf50-125">따라서 **ComputerName** 매개 변수가 지정 되지 않은 경우 로컬 컴퓨터 이름이 명령에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-125">As a result, the local computer name is used in the command unless the **ComputerName** parameter is specified.</span></span>

<span data-ttu-id="5bf50-126">기본 매개 변수 값을 찾으려면 cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5bf50-126">To find the default parameter value, see help topic for the cmdlet.</span></span> <span data-ttu-id="5bf50-127">매개 변수 설명은 기본값을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-127">The parameter description should include the default value.</span></span>

<span data-ttu-id="5bf50-128">Cmdlet 또는 고급 함수의 매개 변수에 대해 사용자 지정 기본값을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-128">You can also set a custom default value for any parameter of a cmdlet or advanced function.</span></span> <span data-ttu-id="5bf50-129">사용자 지정 기본값을 설정 하는 방법에 대 한 자세한 내용은 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5bf50-129">For information about setting custom default values, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="5bf50-130">Parameter 특성 표</span><span class="sxs-lookup"><span data-stu-id="5bf50-130">Parameter attribute table</span></span>

<span data-ttu-id="5bf50-131">Cmdlet의 **Full**, **Parameter** 또는 **Online** 매개 변수를 사용 하는 경우 매개 변수에 `Get-Help` `Get-Help` 대 한 자세한 정보를 포함 하는 매개 변수 특성 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-131">When you use the **Full**, **Parameter**, or **Online** parameters of the `Get-Help` cmdlet, `Get-Help` displays a parameter attribute table with detailed information about the parameter.</span></span>

<span data-ttu-id="5bf50-132">이 정보는 매개 변수를 사용 하기 위해 알아야 하는 세부 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-132">This information includes the details you need to know to use the parameter.</span></span>
<span data-ttu-id="5bf50-133">예를 들어 cmdlet에 대 한 도움말 항목에는 `Get-ChildItem` Path 매개 변수에 대 한 다음과 같은 세부 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-133">For example, the help topic for the `Get-ChildItem` cmdlet includes the following details about its Path parameter:</span></span>

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

<span data-ttu-id="5bf50-134">매개 변수 정보에는 매개 변수 구문, 매개 변수에 대 한 설명 및 매개 변수 특성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-134">The parameter information includes the parameter syntax, a description of the parameter, and the parameter attributes.</span></span> <span data-ttu-id="5bf50-135">다음 섹션에서는 매개 변수 특성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-135">The following sections describe the parameter attributes.</span></span>

#### <a name="parameter-required"></a><span data-ttu-id="5bf50-136">매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-136">Parameter Required</span></span>

<span data-ttu-id="5bf50-137">이 설정은 매개 변수가 필수 인지 여부, 즉이 cmdlet을 사용 하는 모든 명령에이 매개 변수가 포함 되어야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-137">This setting indicates whether the parameter is mandatory, that is, whether all commands that use this cmdlet must include this parameter.</span></span> <span data-ttu-id="5bf50-138">값이 **True** 이 고 매개 변수가 명령에 없으면 PowerShell에서 매개 변수의 값을 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-138">When the value is **True** and the parameter is missing from the command, PowerShell prompts you for a value for the parameter.</span></span>

#### <a name="parameter-position"></a><span data-ttu-id="5bf50-139">매개 변수 위치</span><span class="sxs-lookup"><span data-stu-id="5bf50-139">Parameter Position</span></span>

<span data-ttu-id="5bf50-140">`Position`설정이 양의 정수로 설정 된 경우 매개 변수 이름은 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-140">If the `Position` setting is set to a positive integer, the parameter name is not required.</span></span> <span data-ttu-id="5bf50-141">이 형식의 매개 변수는 위치 매개 변수 라고 하며, 숫자는 다른 위치 매개 변수와 관련 하 여 매개 변수가 표시 되어야 하는 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-141">This type of parameter is referred to as a positional parameter, and the number indicates the position in which the parameter must appear in relation to other positional parameters.</span></span> <span data-ttu-id="5bf50-142">명명 된 매개 변수는 cmdlet 이름 다음의 임의 위치에 나열 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-142">A named parameter can be listed in any position after the cmdlet name.</span></span> <span data-ttu-id="5bf50-143">위치 매개 변수에 대 한 매개 변수 이름을 포함 하는 경우 매개 변수는 cmdlet 이름 다음의 임의 위치에 나열 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-143">If you include the parameter name for a positional parameter, the parameter can be listed in any position after the cmdlet name.</span></span>

<span data-ttu-id="5bf50-144">예를 들어 cmdlet에는 `Get-ChildItem` Path 및 Exclude 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-144">For example, the `Get-ChildItem` cmdlet has Path and Exclude parameters.</span></span> <span data-ttu-id="5bf50-145">`Position` **Path** 에 대 한 설정은 위치 매개 변수 임을 의미 하는 **0** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-145">The `Position` setting for **Path** is **0**, which means that it is a positional parameter.</span></span> <span data-ttu-id="5bf50-146">`Position` **Exclude** 의 설정은로 **지정** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-146">The `Position` setting for **Exclude** is **named**.</span></span>

<span data-ttu-id="5bf50-147">즉, **경로** 에 매개 변수 이름이 필요 하지 않지만 매개 변수 값이 명령의 첫 번째 또는 유일한 명명 되지 않은 매개 변수 값 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-147">This means that **Path** does not require the parameter name, but its parameter value must be the first or only unnamed parameter value in the command.</span></span>
<span data-ttu-id="5bf50-148">그러나 Exclude 매개 변수는 명명 된 매개 변수 이므로 명령에서 임의의 위치에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-148">However, because the Exclude parameter is a named parameter, you can place it in any position in the command.</span></span>

<span data-ttu-id="5bf50-149">`Position`이러한 두 매개 변수에 대 한 설정의 결과로 다음 명령 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-149">As a result of the `Position` settings for these two parameters, you can use any of the following commands:</span></span>

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

<span data-ttu-id="5bf50-150">매개 변수 이름을 포함 하지 않고 다른 위치 매개 변수를 포함 하는 경우 해당 매개 변수는 설정에 지정 된 순서에 따라 배치 되어야 합니다 `Position` .</span><span class="sxs-lookup"><span data-stu-id="5bf50-150">If you were to include another positional parameter without including the parameter name, that parameter must be placed in the order specified by the `Position` setting.</span></span>

#### <a name="parameter-type"></a><span data-ttu-id="5bf50-151">매개 변수 유형</span><span class="sxs-lookup"><span data-stu-id="5bf50-151">Parameter Type</span></span>

<span data-ttu-id="5bf50-152">이 설정은 매개 변수 값의 Microsoft .NET Framework 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-152">This setting specifies the Microsoft .NET Framework type of the parameter value.</span></span> <span data-ttu-id="5bf50-153">예를 들어, 형식이 **Int32** 인 경우 매개 변수 값은 정수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-153">For example, if the type is **Int32**, the parameter value must be an integer.</span></span> <span data-ttu-id="5bf50-154">형식이 문자열인 경우 매개 변수 값은 문자열 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-154">If the type is string, the parameter value must be a character string.</span></span> <span data-ttu-id="5bf50-155">문자열에 공백이 포함 된 경우에는 값을 따옴표로 묶어야 합니다. 그렇지 않으면 공백이 이스케이프 문자 (') 뒤에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-155">If the string contains spaces, the value must be enclosed in quotation marks, or the spaces must be preceded by the escape character ( \` ).</span></span>

#### <a name="default-value"></a><span data-ttu-id="5bf50-156">기본값</span><span class="sxs-lookup"><span data-stu-id="5bf50-156">Default Value</span></span>

<span data-ttu-id="5bf50-157">이 설정은 다른 값이 제공 되지 않은 경우 매개 변수에 의해 가정 되는 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-157">This setting specifies the value that the parameter will assume if no other value is provided.</span></span> <span data-ttu-id="5bf50-158">예를 들어 Path 매개 변수의 기본값은 대개 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-158">For example, the default value of the Path parameter is often the current directory.</span></span> <span data-ttu-id="5bf50-159">필수 매개 변수에는 기본값이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-159">Required parameters never have a default value.</span></span>
<span data-ttu-id="5bf50-160">여러 선택적 매개 변수의 경우 매개 변수가 사용 되지 않는 경우에는이 매개 변수가 적용 되지 않기 때문에 기본값이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-160">For many optional parameters, there is no default because the parameter has no effect if it is not used.</span></span>

#### <a name="accepts-multiple-values"></a><span data-ttu-id="5bf50-161">여러 값 허용</span><span class="sxs-lookup"><span data-stu-id="5bf50-161">Accepts Multiple Values</span></span>

<span data-ttu-id="5bf50-162">이 설정은 매개 변수에서 여러 매개 변수 값을 허용 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-162">This setting indicates whether a parameter accepts multiple parameter values.</span></span>
<span data-ttu-id="5bf50-163">매개 변수가 여러 값을 허용 하는 경우 쉼표로 구분 된 목록을 명령의 매개 변수 값으로 입력 하거나 쉼표로 구분 된 목록 (배열)을 변수에 저장 한 다음 변수를 매개 변수 값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-163">When a parameter accepts multiple values, you can type a comma-separated list as the value of the parameter in the command, or save a comma-separated list (an array) in a variable, and then specify the variable as the parameter value.</span></span>

<span data-ttu-id="5bf50-164">예를 들어 cmdlet의 ServiceName 매개 변수는 `Get-Service` 여러 값을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-164">For example, the ServiceName parameter of the `Get-Service` cmdlet accepts multiple values.</span></span> <span data-ttu-id="5bf50-165">다음 명령은 모두 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-165">The following commands are both valid:</span></span>

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a><span data-ttu-id="5bf50-166">파이프라인 입력 허용</span><span class="sxs-lookup"><span data-stu-id="5bf50-166">Accepts Pipeline Input</span></span>

<span data-ttu-id="5bf50-167">이 설정은 파이프라인 연산자 ()를 사용 `|` 하 여 값을 매개 변수로 보낼지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-167">This setting indicates whether you can use the pipeline operator ( `|` ) to send a value to the parameter.</span></span>

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

<span data-ttu-id="5bf50-168">매개 변수가 "True (값으로)" 인 경우 PowerShell은 다른 메서드를 사용 하 여 명령을 해석 하기 전에 파이프 된 모든 값을 해당 매개 변수와 연결 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-168">When a parameter is "True (by Value)", PowerShell tries to associate any piped values with that parameter before it tries other methods to interpret the command.</span></span>

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

<span data-ttu-id="5bf50-169">예를 들어 값에 **name** 속성이 있는 경우에만 값을 **이름** 매개 변수로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-169">For example, you can pipe a value to a **Name** parameter only when the value has a property called **Name**.</span></span>

> [!NOTE]
> <span data-ttu-id="5bf50-170">파이프라인 입력 () 또는 ()를 허용 하는 형식화 된 매개 변수는 `by Value` `by PropertyName` 매개 변수에 대해 **지연 바인딩** 스크립트 블록을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-170">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
>
> <span data-ttu-id="5bf50-171">**지연 바인드** 스크립트 블록은 **parameterbinding** 중에 자동으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-171">The **delay-bind** script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="5bf50-172">결과는 매개 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-172">The result is bound to the parameter.</span></span> <span data-ttu-id="5bf50-173">또는 형식으로 정의 된 매개 변수에 대해서는 지연 바인딩이 작동 **하지** 않습니다 `ScriptBlock` `System.Object` . 스크립트 블록은 호출 되지 **않고** 를 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-173">Delay binding does **not** work for parameters defined as type `ScriptBlock` or `System.Object`, the script block is passed through **without** being invoked.</span></span>
>
> <span data-ttu-id="5bf50-174">About_Script_Blocks **에서 지연 바인딩** 스크립트 블록에 대해 읽을 수 있습니다 [.](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="5bf50-174">You can read about **delay-bind** script blocks here [about_Script_Blocks.md](about_Script_Blocks.md)</span></span>

#### <a name="accepts-wildcard-characters"></a><span data-ttu-id="5bf50-175">와일드 카드 문자 허용</span><span class="sxs-lookup"><span data-stu-id="5bf50-175">Accepts Wildcard Characters</span></span>

<span data-ttu-id="5bf50-176">이 설정은 매개 변수 값이 대상 컨테이너에 있는 둘 이상의 기존 항목에 일치할 수 있도록 매개 변수의 값에 와일드 카드 문자를 포함할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-176">This setting indicates whether the parameter's value can contain wildcard characters so that the parameter value can be matched to more than one existing item in the target container.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="5bf50-177">일반 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5bf50-177">Common Parameters</span></span>

<span data-ttu-id="5bf50-178">일반 매개 변수는 모든 cmdlet에서 사용할 수 있는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5bf50-178">Common parameters are parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="5bf50-179">일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5bf50-179">For more information about common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5bf50-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bf50-180">See also</span></span>

[<span data-ttu-id="5bf50-181">about_Command_syntax</span><span class="sxs-lookup"><span data-stu-id="5bf50-181">about_Command_syntax</span></span>](about_Command_syntax.md)

[<span data-ttu-id="5bf50-182">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="5bf50-182">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="5bf50-183">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="5bf50-183">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="5bf50-184">about_Parameters_Default_Values</span><span class="sxs-lookup"><span data-stu-id="5bf50-184">about_Parameters_Default_Values</span></span>](about_Parameters_Default_Values.md)

[<span data-ttu-id="5bf50-185">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="5bf50-185">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="5bf50-186">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="5bf50-186">about_Wildcards</span></span>](about_Wildcards.md)

