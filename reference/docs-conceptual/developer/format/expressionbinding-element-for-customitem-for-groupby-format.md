---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)
description: GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655300"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="7b031-103">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-103">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="7b031-104">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="7b031-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7b031-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소에 대 한 CustomControl 요소의 groupby (format) customentries 요소에 대 한 CustomControl의 경우 CustomControl에 대 한 customentries 요소에 대 한 Customentries 요소에 대 한 Customentries 요소</span><span class="sxs-lookup"><span data-stu-id="7b031-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b031-107">구문</span><span class="sxs-lookup"><span data-stu-id="7b031-107">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b031-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7b031-108">Attributes and Elements</span></span>

<span data-ttu-id="7b031-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ExpressionBinding` .</span><span class="sxs-lookup"><span data-stu-id="7b031-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b031-110">특성</span><span class="sxs-lookup"><span data-stu-id="7b031-110">Attributes</span></span>

<span data-ttu-id="7b031-111">없음</span><span class="sxs-lookup"><span data-stu-id="7b031-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b031-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7b031-112">Child Elements</span></span>

|<span data-ttu-id="7b031-113">요소</span><span class="sxs-lookup"><span data-stu-id="7b031-113">Element</span></span>|<span data-ttu-id="7b031-114">설명</span><span class="sxs-lookup"><span data-stu-id="7b031-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="7b031-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7b031-116">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="7b031-117">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-117">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7b031-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7b031-119">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-119">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="7b031-120">[GroupBy (형식)에 대 한 ExpressionBinding의 Enumeratecollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) GroupBy (형식)에 대 한 ExpressionBinding의 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="7b031-120">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="7b031-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7b031-122">컬렉션의 요소가 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="7b031-123">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-123">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7b031-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7b031-125">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="7b031-126">GroupBy의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-126">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7b031-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-127">Optional element.</span></span><br /><br /> <span data-ttu-id="7b031-128">컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="7b031-129">GroupBy의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-129">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7b031-130">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-130">Optional element.</span></span><br /><br /> <span data-ttu-id="7b031-131">컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7b031-132">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7b031-132">Parent Elements</span></span>

|<span data-ttu-id="7b031-133">요소</span><span class="sxs-lookup"><span data-stu-id="7b031-133">Element</span></span>|<span data-ttu-id="7b031-134">설명</span><span class="sxs-lookup"><span data-stu-id="7b031-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b031-135">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-135">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7b031-136">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b031-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7b031-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b031-137">See Also</span></span>

[<span data-ttu-id="7b031-138">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-138">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7b031-139">GroupBy의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-139">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7b031-140">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-140">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7b031-141">GroupBy의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-141">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7b031-142">GroupBy의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-142">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7b031-143">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7b031-143">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7b031-144">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="7b031-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
