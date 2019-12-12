---
title: CustomControl (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362912"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="a51fe-102">CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a51fe-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="a51fe-103">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="a51fe-104">컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="a51fe-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a51fe-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 뷰 (형식)에 대 한 CustomEntry CustomControl for view (format) ItemSelectionCondition 요소에 대 한 Customentry for view (format)의 CustomControl에 대 한 식 바인딩</span><span class="sxs-lookup"><span data-stu-id="a51fe-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a51fe-107">구문</span><span class="sxs-lookup"><span data-stu-id="a51fe-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a51fe-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a51fe-108">Attributes and Elements</span></span>

<span data-ttu-id="a51fe-109">다음 섹션에서는 특성, 자식 요소 및 `ItemSelectionCondition` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a51fe-110">특성</span><span class="sxs-lookup"><span data-stu-id="a51fe-110">Attributes</span></span>

<span data-ttu-id="a51fe-111">없음</span><span class="sxs-lookup"><span data-stu-id="a51fe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a51fe-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a51fe-112">Child Elements</span></span>

|<span data-ttu-id="a51fe-113">요소</span><span class="sxs-lookup"><span data-stu-id="a51fe-113">Element</span></span>|<span data-ttu-id="a51fe-114">설명</span><span class="sxs-lookup"><span data-stu-id="a51fe-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a51fe-115">CustomControl에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식</span><span class="sxs-lookup"><span data-stu-id="a51fe-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a51fe-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a51fe-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a51fe-118">CustomControl에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a51fe-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a51fe-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a51fe-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a51fe-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a51fe-121">Parent Elements</span></span>

|<span data-ttu-id="a51fe-122">요소</span><span class="sxs-lookup"><span data-stu-id="a51fe-122">Element</span></span>|<span data-ttu-id="a51fe-123">설명</span><span class="sxs-lookup"><span data-stu-id="a51fe-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a51fe-124">CustomControl의 CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a51fe-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="a51fe-125">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a51fe-126">설명</span><span class="sxs-lookup"><span data-stu-id="a51fe-126">Remarks</span></span>

<span data-ttu-id="a51fe-127">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a51fe-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a51fe-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a51fe-128">See Also</span></span>

[<span data-ttu-id="a51fe-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a51fe-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="a51fe-130">CustomControl의 CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a51fe-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
