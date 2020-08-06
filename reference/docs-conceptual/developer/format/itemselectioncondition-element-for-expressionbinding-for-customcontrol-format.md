---
title: CustomControl (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781191"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="763a1-102">CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="763a1-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="763a1-103">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="763a1-104">컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="763a1-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="763a1-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소 (형식) Customentries에 대 한 customentries 요소 View (format) CustomControl for view (format) ItemSelectionCondition 요소에 대 한 Customentries에 대 한 CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="763a1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="763a1-107">구문</span><span class="sxs-lookup"><span data-stu-id="763a1-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="763a1-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="763a1-108">Attributes and Elements</span></span>

<span data-ttu-id="763a1-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="763a1-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="763a1-110">특성</span><span class="sxs-lookup"><span data-stu-id="763a1-110">Attributes</span></span>

<span data-ttu-id="763a1-111">없음</span><span class="sxs-lookup"><span data-stu-id="763a1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="763a1-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="763a1-112">Child Elements</span></span>

|<span data-ttu-id="763a1-113">요소</span><span class="sxs-lookup"><span data-stu-id="763a1-113">Element</span></span>|<span data-ttu-id="763a1-114">설명</span><span class="sxs-lookup"><span data-stu-id="763a1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="763a1-115">CustomControl에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식</span><span class="sxs-lookup"><span data-stu-id="763a1-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="763a1-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="763a1-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="763a1-118">View에 대한 CustomControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="763a1-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="763a1-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="763a1-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="763a1-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="763a1-121">Parent Elements</span></span>

|<span data-ttu-id="763a1-122">요소</span><span class="sxs-lookup"><span data-stu-id="763a1-122">Element</span></span>|<span data-ttu-id="763a1-123">설명</span><span class="sxs-lookup"><span data-stu-id="763a1-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="763a1-124">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="763a1-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="763a1-125">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="763a1-126">설명</span><span class="sxs-lookup"><span data-stu-id="763a1-126">Remarks</span></span>

<span data-ttu-id="763a1-127">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="763a1-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="763a1-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="763a1-128">See Also</span></span>

[<span data-ttu-id="763a1-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="763a1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="763a1-130">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="763a1-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
