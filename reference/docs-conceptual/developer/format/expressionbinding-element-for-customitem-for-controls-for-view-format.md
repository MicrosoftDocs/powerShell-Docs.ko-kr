---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)
description: View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649901"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="22f96-103">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-103">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="22f96-104">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="22f96-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="22f96-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤의 컨트롤 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤 요소 보기 (형식)의 경우 컨트롤에 대 한 customentries 요소의 customentries 요소 보기 (format)의 컨트롤에 대 한 Customentries 요소 뷰 (format)의 컨트롤에 대 한 Customentries의 요소</span><span class="sxs-lookup"><span data-stu-id="22f96-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22f96-107">구문</span><span class="sxs-lookup"><span data-stu-id="22f96-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="22f96-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="22f96-108">Attributes and Elements</span></span>

<span data-ttu-id="22f96-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ExpressionBinding` .</span><span class="sxs-lookup"><span data-stu-id="22f96-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="22f96-110">특성</span><span class="sxs-lookup"><span data-stu-id="22f96-110">Attributes</span></span>

<span data-ttu-id="22f96-111">없음</span><span class="sxs-lookup"><span data-stu-id="22f96-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22f96-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="22f96-112">Child Elements</span></span>

|<span data-ttu-id="22f96-113">요소</span><span class="sxs-lookup"><span data-stu-id="22f96-113">Element</span></span>|<span data-ttu-id="22f96-114">설명</span><span class="sxs-lookup"><span data-stu-id="22f96-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="22f96-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-115">Optional element.</span></span><br /><br /> <span data-ttu-id="22f96-116">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="22f96-117">View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-117">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="22f96-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-118">Optional element.</span></span><br /><br /> <span data-ttu-id="22f96-119">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="22f96-120">View에 대한 Controls의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-120">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="22f96-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-121">Optional element.</span></span><br /><br /> <span data-ttu-id="22f96-122">컬렉션의 요소를 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-122">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="22f96-123">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-123">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="22f96-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-124">Optional element.</span></span><br /><br /> <span data-ttu-id="22f96-125">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="22f96-126">View에 대한 Controls의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-126">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="22f96-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-127">Optional element.</span></span><br /><br /> <span data-ttu-id="22f96-128">컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="22f96-129">View에 대한 Controls의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-129">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="22f96-130">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-130">Optional element.</span></span><br /><br /> <span data-ttu-id="22f96-131">컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="22f96-132">부모 요소</span><span class="sxs-lookup"><span data-stu-id="22f96-132">Parent Elements</span></span>

|<span data-ttu-id="22f96-133">요소</span><span class="sxs-lookup"><span data-stu-id="22f96-133">Element</span></span>|<span data-ttu-id="22f96-134">설명</span><span class="sxs-lookup"><span data-stu-id="22f96-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22f96-135">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-135">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="22f96-136">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f96-136">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22f96-137">설명</span><span class="sxs-lookup"><span data-stu-id="22f96-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="22f96-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22f96-138">See Also</span></span>

[<span data-ttu-id="22f96-139">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="22f96-140">View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-140">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="22f96-141">View에 대한 Controls의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-141">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="22f96-142">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-142">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="22f96-143">View에 대한 Controls의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-143">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="22f96-144">View에 대한 Controls의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22f96-144">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="22f96-145">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="22f96-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
