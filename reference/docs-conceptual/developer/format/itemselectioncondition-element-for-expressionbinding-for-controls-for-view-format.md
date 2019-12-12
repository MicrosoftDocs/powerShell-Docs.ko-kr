---
title: 보기 (형식)의 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362942"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="c4ef2-102">View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="c4ef2-103">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="c4ef2-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c4ef2-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for view (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry의 요소에 대 한 형식입니다. View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4ef2-106">구문</span><span class="sxs-lookup"><span data-stu-id="c4ef2-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4ef2-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c4ef2-107">Attributes and Elements</span></span>

<span data-ttu-id="c4ef2-108">다음 섹션에서는 특성, 자식 요소 및 `ItemSelectionCondition` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4ef2-109">특성</span><span class="sxs-lookup"><span data-stu-id="c4ef2-109">Attributes</span></span>

<span data-ttu-id="c4ef2-110">없음</span><span class="sxs-lookup"><span data-stu-id="c4ef2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4ef2-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c4ef2-111">Child Elements</span></span>

|<span data-ttu-id="c4ef2-112">요소</span><span class="sxs-lookup"><span data-stu-id="c4ef2-112">Element</span></span>|<span data-ttu-id="c4ef2-113">설명</span><span class="sxs-lookup"><span data-stu-id="c4ef2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4ef2-114">View 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="c4ef2-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c4ef2-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c4ef2-117">View 컨트롤에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="c4ef2-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c4ef2-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4ef2-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c4ef2-120">Parent Elements</span></span>

|<span data-ttu-id="c4ef2-121">요소</span><span class="sxs-lookup"><span data-stu-id="c4ef2-121">Element</span></span>|<span data-ttu-id="c4ef2-122">설명</span><span class="sxs-lookup"><span data-stu-id="c4ef2-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4ef2-123">뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c4ef2-124">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4ef2-125">설명</span><span class="sxs-lookup"><span data-stu-id="c4ef2-125">Remarks</span></span>

<span data-ttu-id="c4ef2-126">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4ef2-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4ef2-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4ef2-127">See Also</span></span>

[<span data-ttu-id="c4ef2-128">View 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c4ef2-129">View 컨트롤에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="c4ef2-130">뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c4ef2-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c4ef2-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c4ef2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
