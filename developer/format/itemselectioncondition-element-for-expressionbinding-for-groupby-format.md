---
title: GroupBy (형식)에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065464"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="266a3-102">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="266a3-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="266a3-103">이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="266a3-104">컨트롤 항목에 지정 될 수 있는 선택 조건 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="266a3-105">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="266a3-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry CustomItem GroupBy (형식)에 대 한 ExpressionBinding ItemSelectionCondition 요소 GroupBy (형식)에 대 한 GroupBy (형식) ExpressionBinding 요소에 대 한 GroupBy (형식) CustomItem 요소에</span><span class="sxs-lookup"><span data-stu-id="266a3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="266a3-107">구문</span><span class="sxs-lookup"><span data-stu-id="266a3-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="266a3-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="266a3-108">Attributes and Elements</span></span>

<span data-ttu-id="266a3-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ItemSelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="266a3-110">특성</span><span class="sxs-lookup"><span data-stu-id="266a3-110">Attributes</span></span>

<span data-ttu-id="266a3-111">없음</span><span class="sxs-lookup"><span data-stu-id="266a3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="266a3-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="266a3-112">Child Elements</span></span>

|<span data-ttu-id="266a3-113">요소</span><span class="sxs-lookup"><span data-stu-id="266a3-113">Element</span></span>|<span data-ttu-id="266a3-114">설명</span><span class="sxs-lookup"><span data-stu-id="266a3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="266a3-115">GroupBy (형식)에 대 한 ItemSelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="266a3-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="266a3-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="266a3-117">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="266a3-118">GroupBy (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="266a3-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="266a3-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="266a3-120">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="266a3-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="266a3-121">Parent Elements</span></span>

|<span data-ttu-id="266a3-122">요소</span><span class="sxs-lookup"><span data-stu-id="266a3-122">Element</span></span>|<span data-ttu-id="266a3-123">설명</span><span class="sxs-lookup"><span data-stu-id="266a3-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="266a3-124">GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="266a3-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="266a3-125">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="266a3-126">설명</span><span class="sxs-lookup"><span data-stu-id="266a3-126">Remarks</span></span>

<span data-ttu-id="266a3-127">하면 하나의 속성 이름 또는이 조건에 대 한 스크립트를 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="266a3-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="266a3-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="266a3-128">See Also</span></span>

[<span data-ttu-id="266a3-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="266a3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="266a3-130">GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="266a3-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
