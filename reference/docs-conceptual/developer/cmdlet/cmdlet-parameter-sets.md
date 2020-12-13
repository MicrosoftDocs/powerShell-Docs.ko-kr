---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 매개 변수 집합
description: Cmdlet 매개 변수 집합
ms.openlocfilehash: e84af7faf5b7459d8dbe06847526efe804e2c5e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668289"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="9ec6d-103">Cmdlet 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="9ec6d-103">Cmdlet parameter sets</span></span>

<span data-ttu-id="9ec6d-104">PowerShell은 매개 변수 집합을 사용 하 여 다양 한 시나리오에 대해 다른 작업을 수행할 수 있는 단일 cmdlet을 작성할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-104">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="9ec6d-105">매개 변수 집합을 사용 하면 사용자에 게 서로 다른 매개 변수를 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-105">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="9ec6d-106">사용자가 지정한 매개 변수를 기반으로 다른 정보를 반환 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-106">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="9ec6d-107">매개 변수 집합의 예</span><span class="sxs-lookup"><span data-stu-id="9ec6d-107">Examples of parameter sets</span></span>

<span data-ttu-id="9ec6d-108">예를 들어 PowerShell `Get-EventLog` cmdlet은 사용자가 **List** 또는 **LogName** 매개 변수를 지정 하는지에 따라 다른 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-108">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="9ec6d-109">**List** 매개 변수가 지정 된 경우 cmdlet은 로그 파일 자체에 대 한 정보를 반환 하지만 여기에 포함 된 이벤트 정보는 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-109">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="9ec6d-110">**LogName** 매개 변수가 지정 된 경우 cmdlet은 특정 이벤트 로그의 이벤트에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-110">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="9ec6d-111">**List** 및 **LogName** 매개 변수는 두 개의 개별 매개 변수 집합을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-111">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="9ec6d-112">Unique 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9ec6d-112">Unique parameter</span></span>

<span data-ttu-id="9ec6d-113">각 매개 변수 집합에는 PowerShell 런타임에서 적절 한 매개 변수 집합을 노출 하는 데 사용 하는 고유한 매개 변수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-113">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="9ec6d-114">가능 하면 unique 매개 변수는 필수 매개 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-114">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="9ec6d-115">매개 변수가 필수 이면 사용자는 매개 변수를 지정 해야 하 고 PowerShell 런타임에서는 매개 변수 집합을 식별 하는 데 해당 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-115">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="9ec6d-116">매개 변수를 지정 하지 않고 cmdlet을 실행 하도록 디자인 된 경우 unique 매개 변수는 필수 매개 변수 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-116">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="9ec6d-117">여러 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="9ec6d-117">Multiple parameter sets</span></span>

<span data-ttu-id="9ec6d-118">다음 그림에서 왼쪽 열에는 세 개의 유효한 매개 변수 집합이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-118">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="9ec6d-119">**A 매개 변수는** 첫 번째 매개 변수 집합에 대해 고유 하며, **매개 변수 B** 는 두 번째 매개 변수 집합에 고유 하며, **C 매개 변수** 는 세 번째 매개 변수 집합에 대해 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-119">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="9ec6d-120">오른쪽 열에서 매개 변수 집합에는 고유한 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-120">In the right column, the parameter sets don't have a unique parameter.</span></span>

![매개 변수 집합의 그림](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="9ec6d-122">매개 변수 집합 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9ec6d-122">Parameter set requirements</span></span>

<span data-ttu-id="9ec6d-123">모든 매개 변수 집합에는 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-123">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="9ec6d-124">각 매개 변수 집합에는 하나 이상의 고유 매개 변수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-124">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="9ec6d-125">가능 하면이 매개 변수를 필수 매개 변수로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-125">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="9ec6d-126">여러 위치 매개 변수를 포함 하는 매개 변수 집합은 각 매개 변수에 대해 고유한 위치를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-126">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="9ec6d-127">두 위치 매개 변수는 같은 위치를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-127">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="9ec6d-128">집합에 있는 하나의 매개 변수만 `ValueFromPipeline` 값을 사용 하 여 키워드를 선언할 수 있습니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="9ec6d-128">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="9ec6d-129">여러 매개 변수는 `ValueFromPipelineByPropertyName` 값을 사용 하 여 키워드를 정의할 수 있습니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="9ec6d-129">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="9ec6d-130">매개 변수에 대 한 매개 변수 집합이 지정 되지 않은 경우 매개 변수는 모든 매개 변수 집합에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-130">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="9ec6d-131">Cmdlet 또는 함수의 경우 매개 변수 집합은 32 개로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-131">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="9ec6d-132">기본 매개 변수 집합</span><span class="sxs-lookup"><span data-stu-id="9ec6d-132">Default parameter sets</span></span>

<span data-ttu-id="9ec6d-133">여러 매개 변수 집합을 정의 하는 경우 `DefaultParameterSetName` **Cmdlet** 특성의 키워드를 사용 하 여 기본 매개 변수 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-133">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="9ec6d-134">명령에서 제공 하는 정보에 따라 사용할 매개 변수 집합을 확인할 수 없는 경우 PowerShell은 기본 매개 변수 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-134">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="9ec6d-135">**Cmdlet** 특성에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-135">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="9ec6d-136">매개 변수 집합 선언</span><span class="sxs-lookup"><span data-stu-id="9ec6d-136">Declaring parameter sets</span></span>

<span data-ttu-id="9ec6d-137">매개 변수 집합을 만들려면 매개 변수 `ParameterSetName` 집합의 모든 매개 변수에 대 한 **매개 변수** 특성을 선언할 때 키워드를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-137">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="9ec6d-138">여러 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 **매개 변수** 특성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-138">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="9ec6d-139">이 특성을 사용 하면 매개 변수 집합 마다 매개 변수를 다르게 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-139">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="9ec6d-140">예를 들어 매개 변수를 한 집합에서 필수로 정의 하 고 다른 집합에서는 선택적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-140">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="9ec6d-141">그러나 각 매개 변수 집합에는 하나의 고유 매개 변수가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-141">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="9ec6d-142">자세한 내용은 [매개 변수 특성 선언](parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-142">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="9ec6d-143">다음 예제에서 **UserName** 매개 변수는 매개 변수 집합의 고유한 매개 변수이 `Test01` 고 **ComputerName** 매개 변수는 `Test02` 매개 변수 집합의 고유한 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-143">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="9ec6d-144">**Sharedparam** 매개 변수는 두 집합에 속하며 매개 변수 집합에는 필수 `Test01` 이지만 `Test02` 매개 변수 집합의 경우 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9ec6d-144">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
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
private string sharedParam;
```
