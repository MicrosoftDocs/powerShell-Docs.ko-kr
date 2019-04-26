---
title: ExpressionBinding CustomControl (형식)에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065827"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="99ed4-102">CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="99ed4-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="99ed4-103">이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="99ed4-104">컨트롤 항목에 지정 될 수 있는 선택 조건 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="99ed4-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="99ed4-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry CustomItem CustomControl CustomControl에 대 한 보기 (형식)에 대 한 식 바인딩 ItemSelectionCondition 요소 (형식) 보기에 대 한에 대 한 보기 (형식) ExpressionBinding 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="99ed4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99ed4-107">구문</span><span class="sxs-lookup"><span data-stu-id="99ed4-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99ed4-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-108">Attributes and Elements</span></span>

<span data-ttu-id="99ed4-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ItemSelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99ed4-110">특성</span><span class="sxs-lookup"><span data-stu-id="99ed4-110">Attributes</span></span>

<span data-ttu-id="99ed4-111">없음</span><span class="sxs-lookup"><span data-stu-id="99ed4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99ed4-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-112">Child Elements</span></span>

|<span data-ttu-id="99ed4-113">요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-113">Element</span></span>|<span data-ttu-id="99ed4-114">설명</span><span class="sxs-lookup"><span data-stu-id="99ed4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99ed4-115">PropertyName ItemSelectionCondition CustomControl 보려면 (형식에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="99ed4-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="99ed4-117">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="99ed4-118">CustomControl 보려면 (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="99ed4-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="99ed4-120">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="99ed4-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-121">Parent Elements</span></span>

|<span data-ttu-id="99ed4-122">요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-122">Element</span></span>|<span data-ttu-id="99ed4-123">설명</span><span class="sxs-lookup"><span data-stu-id="99ed4-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99ed4-124">ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="99ed4-125">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="99ed4-126">설명</span><span class="sxs-lookup"><span data-stu-id="99ed4-126">Remarks</span></span>

<span data-ttu-id="99ed4-127">하면 하나의 속성 이름 또는이 조건에 대 한 스크립트를 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99ed4-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="99ed4-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99ed4-128">See Also</span></span>

[<span data-ttu-id="99ed4-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="99ed4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="99ed4-130">ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="99ed4-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
