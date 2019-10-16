---
title: CustomControl 용 CustomItem에 대 한 ExpressionBinding 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363152"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="55d5a-102">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="55d5a-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="55d5a-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="55d5a-105">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소 CustomControl for View (Format) ExpressionBinding 요소의 CustomItem에 대 한 CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="55d5a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55d5a-106">구문</span><span class="sxs-lookup"><span data-stu-id="55d5a-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55d5a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="55d5a-107">Attributes and Elements</span></span>

<span data-ttu-id="55d5a-108">다음 섹션에서는 `ExpressionBinding` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55d5a-109">특성</span><span class="sxs-lookup"><span data-stu-id="55d5a-109">Attributes</span></span>

<span data-ttu-id="55d5a-110">없음</span><span class="sxs-lookup"><span data-stu-id="55d5a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55d5a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="55d5a-111">Child Elements</span></span>

|<span data-ttu-id="55d5a-112">요소</span><span class="sxs-lookup"><span data-stu-id="55d5a-112">Element</span></span>|<span data-ttu-id="55d5a-113">설명</span><span class="sxs-lookup"><span data-stu-id="55d5a-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="55d5a-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="55d5a-115">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="55d5a-116">CustomControl에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="55d5a-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="55d5a-118">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="55d5a-119">CustomControl에 대 한 ExpressionBinding의 EnumerateCollection 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="55d5a-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="55d5a-121">컬렉션의 요소가 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="55d5a-122">CustomControl에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="55d5a-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="55d5a-124">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="55d5a-125">CustomControl에 대 한 ExpressionBinding의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="55d5a-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-126">Optional element.</span></span><br /><br /> <span data-ttu-id="55d5a-127">컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="55d5a-128">CustomCustomControl에 대 한 ExpressionBinding의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="55d5a-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-129">Optional element.</span></span><br /><br /> <span data-ttu-id="55d5a-130">컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="55d5a-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="55d5a-131">Parent Elements</span></span>

|<span data-ttu-id="55d5a-132">요소</span><span class="sxs-lookup"><span data-stu-id="55d5a-132">Element</span></span>|<span data-ttu-id="55d5a-133">설명</span><span class="sxs-lookup"><span data-stu-id="55d5a-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55d5a-134">CustomControl에 대 한 Customitem 요소의 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="55d5a-135">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d5a-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="55d5a-136">설명</span><span class="sxs-lookup"><span data-stu-id="55d5a-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="55d5a-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55d5a-137">See Also</span></span>

[<span data-ttu-id="55d5a-138">CustomControl에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="55d5a-139">CustomControl에 대 한 ExpressionBinding의 EnumerateCollection 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="55d5a-140">CustomControl에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="55d5a-141">CustomControl에 대 한 ExpressionBinding의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="55d5a-142">CustomControl에 대 한 ExpressionBinding의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="55d5a-143">CustomControl에 대 한 Customitem 요소의 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="55d5a-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="55d5a-144">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="55d5a-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
