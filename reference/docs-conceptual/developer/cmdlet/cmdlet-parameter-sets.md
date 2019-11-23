---
title: Cmdlet Parameter Sets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: dfe747893b4aef6376ea3b12dd79b7c144455ed0
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415693"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="db153-102">Cmdlet parameter sets</span><span class="sxs-lookup"><span data-stu-id="db153-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="db153-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span><span class="sxs-lookup"><span data-stu-id="db153-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="db153-104">Parameter sets enable you to expose different parameters to the user.</span><span class="sxs-lookup"><span data-stu-id="db153-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="db153-105">And, to return different information based on the parameters specified by the user.</span><span class="sxs-lookup"><span data-stu-id="db153-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="db153-106">Examples of parameter sets</span><span class="sxs-lookup"><span data-stu-id="db153-106">Examples of parameter sets</span></span>

<span data-ttu-id="db153-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span><span class="sxs-lookup"><span data-stu-id="db153-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="db153-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span><span class="sxs-lookup"><span data-stu-id="db153-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="db153-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span><span class="sxs-lookup"><span data-stu-id="db153-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="db153-110">The **List** and **LogName** parameters identify two separate parameter sets.</span><span class="sxs-lookup"><span data-stu-id="db153-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="db153-111">Unique parameter</span><span class="sxs-lookup"><span data-stu-id="db153-111">Unique parameter</span></span>

<span data-ttu-id="db153-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="db153-113">If possible, the unique parameter should be a mandatory parameter.</span><span class="sxs-lookup"><span data-stu-id="db153-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="db153-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="db153-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span><span class="sxs-lookup"><span data-stu-id="db153-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="db153-116">Multiple parameter sets</span><span class="sxs-lookup"><span data-stu-id="db153-116">Multiple parameter sets</span></span>

<span data-ttu-id="db153-117">In the following illustration, the left column shows three valid parameter sets.</span><span class="sxs-lookup"><span data-stu-id="db153-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="db153-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="db153-119">In the right column, the parameter sets don't have a unique parameter.</span><span class="sxs-lookup"><span data-stu-id="db153-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="db153-121">Parameter set requirements</span><span class="sxs-lookup"><span data-stu-id="db153-121">Parameter set requirements</span></span>

<span data-ttu-id="db153-122">The following requirements apply to all parameter sets.</span><span class="sxs-lookup"><span data-stu-id="db153-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="db153-123">Each parameter set must have at least one unique parameter.</span><span class="sxs-lookup"><span data-stu-id="db153-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="db153-124">If possible, make this parameter a mandatory parameter.</span><span class="sxs-lookup"><span data-stu-id="db153-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="db153-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span><span class="sxs-lookup"><span data-stu-id="db153-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="db153-126">No two positional parameters can specify the same position.</span><span class="sxs-lookup"><span data-stu-id="db153-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="db153-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span><span class="sxs-lookup"><span data-stu-id="db153-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="db153-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span><span class="sxs-lookup"><span data-stu-id="db153-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="db153-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span><span class="sxs-lookup"><span data-stu-id="db153-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="db153-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span><span class="sxs-lookup"><span data-stu-id="db153-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="db153-131">Default parameter sets</span><span class="sxs-lookup"><span data-stu-id="db153-131">Default parameter sets</span></span>

<span data-ttu-id="db153-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="db153-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span><span class="sxs-lookup"><span data-stu-id="db153-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="db153-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="db153-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="db153-135">Declaring parameter sets</span><span class="sxs-lookup"><span data-stu-id="db153-135">Declaring parameter sets</span></span>

<span data-ttu-id="db153-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="db153-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="db153-138">This attribute enables you to define the parameter differently for each parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="db153-139">For example, you can define a parameter as mandatory in one set and optional in another.</span><span class="sxs-lookup"><span data-stu-id="db153-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="db153-140">However, each parameter set must contain one unique parameter.</span><span class="sxs-lookup"><span data-stu-id="db153-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="db153-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="db153-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="db153-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="db153-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span><span class="sxs-lookup"><span data-stu-id="db153-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

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
