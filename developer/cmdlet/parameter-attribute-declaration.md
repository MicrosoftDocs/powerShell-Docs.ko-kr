---
title: 매개 변수 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735142"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="a66f5-102">Parameter 특성 선언</span><span class="sxs-lookup"><span data-stu-id="a66f5-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="a66f5-103">매개 변수 특성을 cmdlet 매개 변수로 cmdlet 클래스의 공용 속성을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a66f5-104">구문</span><span class="sxs-lookup"><span data-stu-id="a66f5-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="a66f5-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a66f5-105">Parameters</span></span>

<span data-ttu-id="a66f5-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a66f5-107">`True` 필요한 cmdlet 매개 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="a66f5-108">Cmdlet을 호출 하면 필수 매개 변수를 제공 하지 않으면, Windows PowerShell 매개 변수 값에 대 한 사용자를 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="a66f5-109">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-109">The default is `false`.</span></span>

<span data-ttu-id="a66f5-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="a66f5-111">이 cmdlet은 매개 변수가 속한 매개 변수 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="a66f5-112">없는 매개 변수 집합을 지정 하는 경우 매개 변수는 모든 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="a66f5-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="a66f5-114">Windows PowerShell 명령 내에서 매개 변수의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="a66f5-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a66f5-116">`True` cmdlet 매개 변수는 파이프라인 개체에서 해당 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="a66f5-117">Cmdlet은 전체 액세스 하는 경우이 키워드를 지정 합니다. 개체의 속성 뿐 아니라 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="a66f5-118">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-118">The default is `false`.</span></span>

<span data-ttu-id="a66f5-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a66f5-120">`True` cmdlet 매개 변수는 동일한 이름 또는이 매개 변수는 동일한 별칭이 있는 파이프라인 개체의 속성에서 해당 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="a66f5-121">예를 들어 cmdlet에는 `Name` 매개 변수 및 파이프라인 개체도 있습니다.을 `Name` 속성, 값을 `Name` 속성에 할당 된는 `Name` cmdlet의 매개 변수.</span><span class="sxs-lookup"><span data-stu-id="a66f5-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="a66f5-122">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-122">The default is `false`.</span></span>

<span data-ttu-id="a66f5-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="a66f5-124">`True` cmdlet 매개 변수를 cmdlet으로 전달 되는 모든 나머지 인수를 허용 하는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="a66f5-125">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-125">The default is `false`.</span></span>

<span data-ttu-id="a66f5-126">`HelpMessage` 명명 된 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="a66f5-127">매개 변수에 대 한 간단한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="a66f5-128">Windows PowerShell cmdlet이 실행 되 고 필수 매개 변수를 지정 하지 않으면 하는 경우이 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="a66f5-129">`HelpMessageBaseName` 명명 된 매개 변수는 선택 사항입니다. 리소스 식별자가 있는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="a66f5-130">예를 들어이 매개 변수 지역화 하려는 도움말 메시지를 포함 하는 리소스 어셈블리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="a66f5-131">`HelpMessageResourceId` 명명 된 매개 변수는 선택 사항입니다. 도움말 메시지를의 리소스 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="a66f5-132">설명</span><span class="sxs-lookup"><span data-stu-id="a66f5-132">Remarks</span></span>

- <span data-ttu-id="a66f5-133">이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수를 선언 하는 방법을](./how-to-declare-cmdlet-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="a66f5-134">Cmdlet 매개 변수 수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="a66f5-135">그러나 사용자 경험 개선을 위해 매개 변수 개수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="a66f5-136">매개 변수는 공용 비정적 필드 또는 속성에 선언 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="a66f5-137">매개 변수 속성에 선언 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="a66f5-138">속성에 public set 접근자에 있어야 합니다. 경우에 `ValueFromPipeline` 또는 `ValueFromPipelineByPropertyName` 키워드를 지정한 경우 속성 공용 get 접근자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="a66f5-139">위치 매개 변수를 지정 하는 경우 매개 변수를 5 보다 작게 설정에서 위치 매개 변수 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="a66f5-140">및 위치 매개 변수를 연속일 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="a66f5-141">5, 100 및 250 위치 0, 1 및 2 위치와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="a66f5-142">경우는 `Position` 키워드를 지정 하지 않으면 cmdlet 매개 변수 이름별으로 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="a66f5-143">매개 변수 집합을 사용 하면 다음 note:</span><span class="sxs-lookup"><span data-stu-id="a66f5-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="a66f5-144">각 매개 변수 집합에는 고유한 매개 변수가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="a66f5-145">좋은 cmdlet 설계가 고유한 매개 변수 역시 필수 가능한 경우를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="a66f5-146">Cmdlet 매개 변수 없이 실행 되도록 디자인 된, 경우 unique 매개 변수는 필수 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="a66f5-147">매개 변수 집합에 없는 동일한 위치를 사용 하 여 둘 이상의 위치 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="a66f5-148">매개 변수 집합에 하나의 매개 변수를 선언 해야 합니다 `ValueFromPipeline = true`합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="a66f5-149">여러 매개 변수를 정의할 수 `ValueFromPipelineByPropertyName = true`입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="a66f5-150">여러 매개 변수를 정의할 수 `ValueFromPipelineByPropertyName = true`입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="a66f5-151">매개 변수 이름에 대 한 지침에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 이름은](standard-cmdlet-parameter-names-and-types.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="a66f5-152">매개 변수 특성은 정의한 합니다 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="a66f5-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a66f5-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a66f5-153">See Also</span></span>

[<span data-ttu-id="a66f5-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="a66f5-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="a66f5-155">Cmdlet 매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="a66f5-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

<span data-ttu-id="a66f5-156">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="a66f5-156">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
