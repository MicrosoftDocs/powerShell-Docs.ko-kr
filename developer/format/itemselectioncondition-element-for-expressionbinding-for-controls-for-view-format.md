---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861849"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="1799d-102">View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1799d-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="1799d-103">이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="1799d-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1799d-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry CustomItem 보기 (형식)에 대 한 컨트롤에 대 한 보기 (형식) ExpressionBinding 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한 뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1799d-106">구문</span><span class="sxs-lookup"><span data-stu-id="1799d-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1799d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-107">Attributes and Elements</span></span>

<span data-ttu-id="1799d-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ItemSelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1799d-109">특성</span><span class="sxs-lookup"><span data-stu-id="1799d-109">Attributes</span></span>

<span data-ttu-id="1799d-110">없음</span><span class="sxs-lookup"><span data-stu-id="1799d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1799d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-111">Child Elements</span></span>

|<span data-ttu-id="1799d-112">요소</span><span class="sxs-lookup"><span data-stu-id="1799d-112">Element</span></span>|<span data-ttu-id="1799d-113">설명</span><span class="sxs-lookup"><span data-stu-id="1799d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1799d-114">뷰 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="1799d-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1799d-116">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1799d-117">뷰 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="1799d-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1799d-119">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1799d-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-120">Parent Elements</span></span>

|<span data-ttu-id="1799d-121">요소</span><span class="sxs-lookup"><span data-stu-id="1799d-121">Element</span></span>|<span data-ttu-id="1799d-122">설명</span><span class="sxs-lookup"><span data-stu-id="1799d-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1799d-123">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1799d-124">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1799d-125">설명</span><span class="sxs-lookup"><span data-stu-id="1799d-125">Remarks</span></span>

<span data-ttu-id="1799d-126">하면 하나의 속성 이름 또는이 조건에 대 한 스크립트를 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1799d-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="1799d-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1799d-127">See Also</span></span>

[<span data-ttu-id="1799d-128">뷰 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="1799d-129">뷰 (형식)에 대 한 컨트롤에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="1799d-130">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="1799d-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1799d-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1799d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
