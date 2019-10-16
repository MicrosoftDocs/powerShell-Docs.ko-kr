---
title: GroupBy (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365292"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="3c5d5-102">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3c5d5-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="3c5d5-103">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="3c5d5-104">컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="3c5d5-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3c5d5-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 CustomControl에 대 한 customitem 요소에 대 한 customitem에 대 한 customitem에 대 한 CustomItem에 대 한 CustomItem의 경우 groupby (형식)에 대 한 ExpressionBinding에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c5d5-107">구문</span><span class="sxs-lookup"><span data-stu-id="3c5d5-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c5d5-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-108">Attributes and Elements</span></span>

<span data-ttu-id="3c5d5-109">다음 섹션에서는 `ItemSelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c5d5-110">특성</span><span class="sxs-lookup"><span data-stu-id="3c5d5-110">Attributes</span></span>

<span data-ttu-id="3c5d5-111">없음</span><span class="sxs-lookup"><span data-stu-id="3c5d5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c5d5-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-112">Child Elements</span></span>

|<span data-ttu-id="3c5d5-113">요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-113">Element</span></span>|<span data-ttu-id="3c5d5-114">설명</span><span class="sxs-lookup"><span data-stu-id="3c5d5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c5d5-115">GroupBy (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="3c5d5-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3c5d5-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3c5d5-118">GroupBy (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="3c5d5-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3c5d5-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c5d5-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-121">Parent Elements</span></span>

|<span data-ttu-id="3c5d5-122">요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-122">Element</span></span>|<span data-ttu-id="3c5d5-123">설명</span><span class="sxs-lookup"><span data-stu-id="3c5d5-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c5d5-124">GroupBy (형식)에 대 한 CustomItem의 ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="3c5d5-125">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c5d5-126">설명</span><span class="sxs-lookup"><span data-stu-id="3c5d5-126">Remarks</span></span>

<span data-ttu-id="3c5d5-127">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c5d5-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c5d5-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c5d5-128">See Also</span></span>

[<span data-ttu-id="3c5d5-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3c5d5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="3c5d5-130">GroupBy (형식)에 대 한 CustomItem의 ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="3c5d5-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
