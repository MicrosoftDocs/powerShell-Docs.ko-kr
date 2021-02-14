---
ms.date: 09/13/2016
ms.topic: reference
title: Parameter 특성 선언
description: Parameter 특성 선언
ms.openlocfilehash: 24a49406b1493a7f8c23bca798ddb3e73a901111
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500232"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="fcd9a-103">Parameter 특성 선언</span><span class="sxs-lookup"><span data-stu-id="fcd9a-103">Parameter Attribute Declaration</span></span>

<span data-ttu-id="fcd9a-104">Parameter 특성은 cmdlet 클래스의 공용 속성을 cmdlet 매개 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-104">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcd9a-105">구문</span><span class="sxs-lookup"><span data-stu-id="fcd9a-105">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="fcd9a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="fcd9a-106">Parameters</span></span>

<span data-ttu-id="fcd9a-107">`Mandatory` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-107">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="fcd9a-108">`True` cmdlet 매개 변수가 필요 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-108">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="fcd9a-109">Cmdlet을 호출할 때 필수 매개 변수를 제공 하지 않으면 Windows PowerShell에서 사용자에 게 매개 변수 값을 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-109">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="fcd9a-110">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-110">The default is `false`.</span></span>

<span data-ttu-id="fcd9a-111">`ParameterSetName` ([System.string](/dotnet/api/System.String)) 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-111">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="fcd9a-112">이 cmdlet 매개 변수가 속하는 매개 변수 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-112">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="fcd9a-113">매개 변수 집합이 지정 되지 않은 경우 매개 변수는 모든 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-113">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="fcd9a-114">`Position` ([System.web](/dotnet/api/System.Int32)) 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-114">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="fcd9a-115">Windows PowerShell 명령 내에서 매개 변수의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-115">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="fcd9a-116">`ValueFromPipeline` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-116">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="fcd9a-117">`True` cmdlet 매개 변수가 파이프라인 개체에서 해당 값을 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-117">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="fcd9a-118">Cmdlet이 개체의 속성 뿐만 아니라 전체 개체에 액세스 하는 경우이 키워드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-118">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="fcd9a-119">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-119">The default is `false`.</span></span>

<span data-ttu-id="fcd9a-120">`ValueFromPipelineByPropertyName` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-120">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="fcd9a-121">`True` cmdlet 매개 변수가이 매개 변수와 이름이 같거나 동일한 별칭을 가진 파이프라인 개체의 속성에서 해당 값을 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-121">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="fcd9a-122">예를 들어 cmdlet에 `Name` 매개 변수가 있고 파이프라인 개체에 `Name` 속성도 있으면 속성의 값 `Name` 이 `Name` cmdlet의 매개 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-122">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="fcd9a-123">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-123">The default is `false`.</span></span>

<span data-ttu-id="fcd9a-124">`ValueFromRemainingArguments` ([System.string) 선택적](/dotnet/api/System.Boolean)명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-124">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="fcd9a-125">`True` cmdlet 매개 변수가 cmdlet에 전달 되는 나머지 인수를 모두 허용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-125">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="fcd9a-126">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-126">The default is `false`.</span></span>

<span data-ttu-id="fcd9a-127">`HelpMessage` 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-127">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="fcd9a-128">매개 변수에 대 한 간단한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-128">Specifies a short description of the parameter.</span></span> <span data-ttu-id="fcd9a-129">Windows PowerShell은 cmdlet을 실행할 때 필수 매개 변수를 지정 하지 않은 경우이 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-129">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="fcd9a-130">`HelpMessageBaseName` 선택적 명명 된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-130">`HelpMessageBaseName` Optional named parameter.</span></span> <span data-ttu-id="fcd9a-131">리소스 식별자가 있는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-131">Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="fcd9a-132">예를 들어이 매개 변수는 지역화할 도움말 메시지를 포함 하는 리소스 어셈블리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-132">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="fcd9a-133">`HelpMessageResourceId` 선택적 명명 된 매개 변수입니다. 도움말 메시지의 리소스 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-133">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcd9a-134">설명</span><span class="sxs-lookup"><span data-stu-id="fcd9a-134">Remarks</span></span>

- <span data-ttu-id="fcd9a-135">이 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-135">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="fcd9a-136">Cmdlet에는 원하는 수의 매개 변수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-136">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="fcd9a-137">그러나 사용자 환경을 개선 하려면 매개 변수 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-137">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="fcd9a-138">매개 변수는 public 비정적 필드 또는 속성에서 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-138">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="fcd9a-139">매개 변수는 속성에서 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-139">Parameters should be declared on properties.</span></span> <span data-ttu-id="fcd9a-140">속성에는 public set 접근자가 있어야 하 고 `ValueFromPipeline` 또는 키워드가 지정 된 경우에 `ValueFromPipelineByPropertyName` 는 속성에 public get 접근자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-140">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="fcd9a-141">위치 매개 변수를 지정 하는 경우 매개 변수 집합의 위치 매개 변수 수를 5 개 미만으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-141">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="fcd9a-142">위치 매개 변수는 연속적 일 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-142">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="fcd9a-143">5, 100 및 250 위치는 0, 1, 2 위치와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-143">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="fcd9a-144">키워드를 `Position` 지정 하지 않은 경우에는 cmdlet 매개 변수를 이름으로 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-144">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="fcd9a-145">매개 변수 집합을 사용 하는 경우 다음에 유의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-145">When you use parameter sets, note the following:</span></span>

  - <span data-ttu-id="fcd9a-146">각 매개 변수 집합에는 하나 이상의 고유 매개 변수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-146">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="fcd9a-147">바람직한 cmdlet 디자인은 가능 하면이 unique 매개 변수도 필수 매개 변수 여야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-147">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="fcd9a-148">Cmdlet이 매개 변수 없이 실행 되도록 디자인 된 경우 unique 매개 변수는 필수 매개 변수가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-148">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

  - <span data-ttu-id="fcd9a-149">위치 매개 변수를 두 개 이상 포함 하는 매개 변수 집합은 동일 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-149">No parameter set should contain more than one positional parameter with the same position.</span></span>

  - <span data-ttu-id="fcd9a-150">매개 변수 집합에서 하나의 매개 변수만 선언 해야 `ValueFromPipeline = true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-150">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span>

  - <span data-ttu-id="fcd9a-151">여러 매개 변수에서를 정의할 수 있습니다 `ValueFromPipelineByPropertyName = true` .</span><span class="sxs-lookup"><span data-stu-id="fcd9a-151">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="fcd9a-152">매개 변수 이름에 대 한 지침에 대 한 자세한 내용은 [Cmdlet 매개 변수 이름](standard-cmdlet-parameter-names-and-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-152">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="fcd9a-153">Parameter 특성은 [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 클래스에서 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcd9a-153">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcd9a-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fcd9a-154">See Also</span></span>

[<span data-ttu-id="fcd9a-155">System.object. Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="fcd9a-155">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="fcd9a-156">Cmdlet 매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="fcd9a-156">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

<span data-ttu-id="fcd9a-157">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="fcd9a-157">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
