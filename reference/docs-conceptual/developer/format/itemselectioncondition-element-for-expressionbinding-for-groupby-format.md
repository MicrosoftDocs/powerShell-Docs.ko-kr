---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
description: GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651977"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="ed8c9-103">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ed8c9-103">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="ed8c9-104">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="ed8c9-105">컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="ed8c9-106">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ed8c9-107">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl groupby (format) Customentries 요소에 대 한 Customentries의 경우 CustomControl에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 Customentries에 대 한 요소에 대 한 형식</span><span class="sxs-lookup"><span data-stu-id="ed8c9-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed8c9-108">구문</span><span class="sxs-lookup"><span data-stu-id="ed8c9-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed8c9-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ed8c9-109">Attributes and Elements</span></span>

<span data-ttu-id="ed8c9-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="ed8c9-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed8c9-111">특성</span><span class="sxs-lookup"><span data-stu-id="ed8c9-111">Attributes</span></span>

<span data-ttu-id="ed8c9-112">없음</span><span class="sxs-lookup"><span data-stu-id="ed8c9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed8c9-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ed8c9-113">Child Elements</span></span>

|<span data-ttu-id="ed8c9-114">요소</span><span class="sxs-lookup"><span data-stu-id="ed8c9-114">Element</span></span>|<span data-ttu-id="ed8c9-115">설명</span><span class="sxs-lookup"><span data-stu-id="ed8c9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed8c9-116">GroupBy의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ed8c9-116">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="ed8c9-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ed8c9-118">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ed8c9-119">GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ed8c9-119">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="ed8c9-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ed8c9-121">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ed8c9-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ed8c9-122">Parent Elements</span></span>

|<span data-ttu-id="ed8c9-123">요소</span><span class="sxs-lookup"><span data-stu-id="ed8c9-123">Element</span></span>|<span data-ttu-id="ed8c9-124">설명</span><span class="sxs-lookup"><span data-stu-id="ed8c9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed8c9-125">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ed8c9-125">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ed8c9-126">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ed8c9-127">설명</span><span class="sxs-lookup"><span data-stu-id="ed8c9-127">Remarks</span></span>

<span data-ttu-id="ed8c9-128">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ed8c9-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed8c9-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed8c9-129">See Also</span></span>

[<span data-ttu-id="ed8c9-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ed8c9-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="ed8c9-131">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ed8c9-131">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
