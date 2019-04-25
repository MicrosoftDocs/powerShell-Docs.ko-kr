---
title: Cmdlet 매개 변수 설정 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068523"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="656fd-102">Cmdlet 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="656fd-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="656fd-103">Windows PowerShell 매개 변수 집합을 사용 하 여 다양 한 시나리오에 대 한 다양 한 작업을 수행할 수 있는 단일 cmdlet를 작성할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="656fd-104">매개 변수 집합을 사용 하면 사용자가 지정한 매개 변수를 기반으로 하는 다양 한 정보를 반환 하 고 사용자에 게 서로 다른 매개 변수를 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="656fd-105">매개 변수 집합의 예</span><span class="sxs-lookup"><span data-stu-id="656fd-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="656fd-106">예를 들어 합니다 `Get-EventLog` 사용자 지정 여부에 따라 다른 정보를 반환 하는 cmdlet (Windows PowerShell에서 제공)를 `List` 또는 `LogName` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="656fd-107">경우는 `List` 매개 변수를 지정, 자체 하지만 포함 된 이벤트 정보가 아니라 로그 파일에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="656fd-108">경우는 `LogName` 특정 이벤트 로그에서 이벤트에 대 한 정보를 반환 하는 cmdlet, 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="656fd-109">합니다 `List` 고 `LogName` 매개 변수 두 개의 별도 매개 변수 집합을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="656fd-110">고유한 매개 변수</span><span class="sxs-lookup"><span data-stu-id="656fd-110">Unique Parameter</span></span>

<span data-ttu-id="656fd-111">각 매개 변수 집합에는 Windows PowerShell 런타임에 적절 한 매개 변수 집합을 노출 하는 데 사용할 수 있는 고유한 매개 변수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="656fd-112">가능 하면 unique 매개 변수는 필수 매개 변수 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="656fd-113">매개 변수가 필수 이면 매개 변수를 지정 하는 사용자가 강제 적용 및 Windows PowerShell 런타임을 사용 하도록 설정 하는 매개 변수를 식별 하는 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="656fd-114">Unique 매개 변수는 cmdlet 매개 변수를 지정 하지 않아도 실행 되도록 설계 된 경우 필수 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="656fd-115">여러 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="656fd-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="656fd-116">다음 그림에서 왼쪽된 열 세 가지 유효한 매개 변수 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="656fd-117">매개 변수는 첫 번째 매개 변수 집합에 고유한, B 매개 변수는 두 번째 매개 변수를 설정 하려면 고유한 이며 매개 변수 C 세 번째 매개 변수 집합에 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="656fd-118">그러나 오른쪽 열에서 매개 변수 집합이 없는 고유한 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="656fd-120">매개 변수 요구 사항을 설정</span><span class="sxs-lookup"><span data-stu-id="656fd-120">Parameter Set Requirements</span></span>

<span data-ttu-id="656fd-121">다음 요구 사항을 모든 매개 변수 집합에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="656fd-122">각 매개 변수 집합에는 고유한 매개 변수가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="656fd-123">가능 하면이 매개 변수는 필수 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="656fd-124">여러 위치 매개 변수를 포함 하는 매개 변수 집합을 각 매개 변수에 대해 고유한 위치를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="656fd-125">두 위치 매개 변수 없이 동일한 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="656fd-126">집합에서 하나의 매개 변수를 선언할 수는 `ValueFromPipeline` 키워드의 값을 사용 하 여 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="656fd-127">여러 매개 변수를 정의할 수는 `ValueFromPipelineByPropertyName` 키워드의 값을 사용 하 여 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="656fd-128">없는 매개 변수 집합이 매개 변수에 대해 지정 된, 매개 변수는 모든 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="656fd-129">기본 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="656fd-129">Default Parameter Sets</span></span>

<span data-ttu-id="656fd-130">여러 매개 변수 집합이 정의 되어 있는 경우 사용할 수는 `DefaultParameterSetName` 기본 매개 변수 집합을 지정 하는 Cmdlet 특성의 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="656fd-131">Windows PowerShell 명령에서 제공 정보를 기반으로 사용 하도록 설정 하는 매개 변수를 확인할 수 없을 때를 설정 합니다. 기본 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="656fd-132">Cmdlet 특성에 대 한 자세한 내용은 참조 하세요. [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="656fd-133">선언 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="656fd-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="656fd-134">매개 변수 집합을 만들려면 지정 해야 합니다는 `ParameterSetName` 키워드 매개 변수 집합의 모든 매개 변수에 대해 매개 변수 특성을 선언 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="656fd-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="656fd-135">여러 매개 변수 집합에 속하는 매개 변수를 각 매개 변수 집합에 대 한 매개 변수 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="656fd-136">이 옵션을 사용 하면 각 매개 변수 집합에 대해 다르게 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="656fd-137">예를 들어, 하나의 집합에 필수 및 다른 선택적으로 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="656fd-138">그러나 각 매개 변수 집합에 고유한 매개 변수가 하나 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="656fd-139">다음 예제에서는 `UserName` 매개 변수는 Test01 매개 변수 집합의 고유한 매개 변수 및 `ComputerName` 매개 변수는 Test02 매개 변수 집합의 unique 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="656fd-140">`SharedParam` 매개 변수 집합 모두에 속하며 Test02 매개 변수 집합에 대 한 선택 사항 이지만 설정 Test01 매개 변수에 대 한 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="656fd-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```