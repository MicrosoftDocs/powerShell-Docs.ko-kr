---
title: 뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363782"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="3a9fb-102">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="3a9fb-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="3a9fb-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3a9fb-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for view (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry의 요소에 대 한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a9fb-106">구문</span><span class="sxs-lookup"><span data-stu-id="3a9fb-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3a9fb-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3a9fb-107">Attributes and Elements</span></span>

<span data-ttu-id="3a9fb-108">다음 섹션에서는 `ExpressionBinding` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a9fb-109">특성</span><span class="sxs-lookup"><span data-stu-id="3a9fb-109">Attributes</span></span>

<span data-ttu-id="3a9fb-110">없음</span><span class="sxs-lookup"><span data-stu-id="3a9fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a9fb-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3a9fb-111">Child Elements</span></span>

|<span data-ttu-id="3a9fb-112">요소</span><span class="sxs-lookup"><span data-stu-id="3a9fb-112">Element</span></span>|<span data-ttu-id="3a9fb-113">설명</span><span class="sxs-lookup"><span data-stu-id="3a9fb-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="3a9fb-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3a9fb-115">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="3a9fb-116">뷰의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3a9fb-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3a9fb-118">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="3a9fb-119">View 컨트롤의 ExpressionBinding에 대 한 EnumerateCollection 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3a9fb-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3a9fb-121">컬렉션의 요소를 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="3a9fb-122">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3a9fb-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-123">Optional element.</span></span><br /><br /> <span data-ttu-id="3a9fb-124">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="3a9fb-125">View 컨트롤의 ExpressionBinding에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3a9fb-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-126">Optional element.</span></span><br /><br /> <span data-ttu-id="3a9fb-127">컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="3a9fb-128">View 컨트롤의 ExpressionBinding에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="3a9fb-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-129">Optional element.</span></span><br /><br /> <span data-ttu-id="3a9fb-130">컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3a9fb-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3a9fb-131">Parent Elements</span></span>

|<span data-ttu-id="3a9fb-132">요소</span><span class="sxs-lookup"><span data-stu-id="3a9fb-132">Element</span></span>|<span data-ttu-id="3a9fb-133">설명</span><span class="sxs-lookup"><span data-stu-id="3a9fb-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a9fb-134">뷰의 컨트롤에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="3a9fb-135">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a9fb-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3a9fb-136">설명</span><span class="sxs-lookup"><span data-stu-id="3a9fb-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3a9fb-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a9fb-137">See Also</span></span>

[<span data-ttu-id="3a9fb-138">뷰의 컨트롤에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="3a9fb-139">뷰의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3a9fb-140">View 컨트롤의 ExpressionBinding에 대 한 EnumerateCollection 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3a9fb-141">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3a9fb-142">View 컨트롤의 ExpressionBinding에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3a9fb-143">View 컨트롤의 ExpressionBinding에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3a9fb-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="3a9fb-144">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3a9fb-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
