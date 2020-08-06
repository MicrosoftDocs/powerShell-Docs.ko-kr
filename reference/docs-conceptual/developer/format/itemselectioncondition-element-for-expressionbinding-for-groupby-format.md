---
title: GroupBy (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a9b74f1882efc578f7d9ab27b8cd2f8a52833ab8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773439"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="b8f15-102">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8f15-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="b8f15-103">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b8f15-104">컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="b8f15-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b8f15-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl groupby (format) Customentries 요소에 대 한 Customentries의 경우 CustomControl에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 Customentries에 대 한 요소에 대 한 형식</span><span class="sxs-lookup"><span data-stu-id="b8f15-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8f15-107">구문</span><span class="sxs-lookup"><span data-stu-id="b8f15-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8f15-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b8f15-108">Attributes and Elements</span></span>

<span data-ttu-id="b8f15-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="b8f15-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8f15-110">특성</span><span class="sxs-lookup"><span data-stu-id="b8f15-110">Attributes</span></span>

<span data-ttu-id="b8f15-111">없음</span><span class="sxs-lookup"><span data-stu-id="b8f15-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8f15-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b8f15-112">Child Elements</span></span>

|<span data-ttu-id="b8f15-113">요소</span><span class="sxs-lookup"><span data-stu-id="b8f15-113">Element</span></span>|<span data-ttu-id="b8f15-114">설명</span><span class="sxs-lookup"><span data-stu-id="b8f15-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8f15-115">GroupBy의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8f15-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="b8f15-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b8f15-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b8f15-118">GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8f15-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="b8f15-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b8f15-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8f15-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b8f15-121">Parent Elements</span></span>

|<span data-ttu-id="b8f15-122">요소</span><span class="sxs-lookup"><span data-stu-id="b8f15-122">Element</span></span>|<span data-ttu-id="b8f15-123">설명</span><span class="sxs-lookup"><span data-stu-id="b8f15-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8f15-124">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8f15-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="b8f15-125">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8f15-126">설명</span><span class="sxs-lookup"><span data-stu-id="b8f15-126">Remarks</span></span>

<span data-ttu-id="b8f15-127">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8f15-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8f15-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8f15-128">See Also</span></span>

[<span data-ttu-id="b8f15-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b8f15-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="b8f15-130">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8f15-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
