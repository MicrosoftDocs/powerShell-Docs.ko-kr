---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
description: View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648058"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="496ae-103">View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="496ae-103">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="496ae-104">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="496ae-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="496ae-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 view (format) CustomEntries 요소에 대 한 컨트롤 요소 (형식) Customentries 뷰 (형식)의 컨트롤에 대 한 Customentries 요소의 Customentries 요소 뷰 (format)의 컨트롤에 대 한 customentries 요소에 대 한 컨트롤의 customentries 요소에 대 한 컨트롤의 Customentries 요소에 대 한 컨트롤의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="496ae-107">구문</span><span class="sxs-lookup"><span data-stu-id="496ae-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="496ae-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="496ae-108">Attributes and Elements</span></span>

<span data-ttu-id="496ae-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="496ae-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="496ae-110">특성</span><span class="sxs-lookup"><span data-stu-id="496ae-110">Attributes</span></span>

<span data-ttu-id="496ae-111">없음</span><span class="sxs-lookup"><span data-stu-id="496ae-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="496ae-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="496ae-112">Child Elements</span></span>

|<span data-ttu-id="496ae-113">요소</span><span class="sxs-lookup"><span data-stu-id="496ae-113">Element</span></span>|<span data-ttu-id="496ae-114">설명</span><span class="sxs-lookup"><span data-stu-id="496ae-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="496ae-115">View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="496ae-115">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="496ae-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-116">Optional element.</span></span><br /><br /> <span data-ttu-id="496ae-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="496ae-118">View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="496ae-118">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="496ae-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-119">Optional element.</span></span><br /><br /> <span data-ttu-id="496ae-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="496ae-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="496ae-121">Parent Elements</span></span>

|<span data-ttu-id="496ae-122">요소</span><span class="sxs-lookup"><span data-stu-id="496ae-122">Element</span></span>|<span data-ttu-id="496ae-123">설명</span><span class="sxs-lookup"><span data-stu-id="496ae-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="496ae-124">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="496ae-124">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="496ae-125">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="496ae-126">설명</span><span class="sxs-lookup"><span data-stu-id="496ae-126">Remarks</span></span>

<span data-ttu-id="496ae-127">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="496ae-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="496ae-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="496ae-128">See Also</span></span>

[<span data-ttu-id="496ae-129">View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="496ae-129">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="496ae-130">View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="496ae-130">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="496ae-131">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="496ae-131">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="496ae-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="496ae-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
