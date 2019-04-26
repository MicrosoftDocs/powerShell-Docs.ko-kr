---
title: ExpressionBinding 요소 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065953"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="a1b08-102">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a1b08-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="a1b08-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="a1b08-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a1b08-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry CustomItem 보기 (형식)에 대 한 컨트롤에 대 한 보기 (형식) ExpressionBinding 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="a1b08-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1b08-106">구문</span><span class="sxs-lookup"><span data-stu-id="a1b08-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a1b08-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-107">Attributes and Elements</span></span>

<span data-ttu-id="a1b08-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ExpressionBinding` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1b08-109">특성</span><span class="sxs-lookup"><span data-stu-id="a1b08-109">Attributes</span></span>

<span data-ttu-id="a1b08-110">없음</span><span class="sxs-lookup"><span data-stu-id="a1b08-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1b08-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-111">Child Elements</span></span>

|<span data-ttu-id="a1b08-112">요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-112">Element</span></span>|<span data-ttu-id="a1b08-113">설명</span><span class="sxs-lookup"><span data-stu-id="a1b08-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="a1b08-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a1b08-115">이 컨트롤에서 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="a1b08-116">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="a1b08-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a1b08-118">공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="a1b08-119">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="a1b08-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a1b08-121">컬렉션의 요소 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="a1b08-122">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="a1b08-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a1b08-124">이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="a1b08-125">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="a1b08-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a1b08-127">컨트롤에서 해당 값이 표시.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="a1b08-128">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="a1b08-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-129">Optional element.</span></span><br /><br /> <span data-ttu-id="a1b08-130">컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1b08-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-131">Parent Elements</span></span>

|<span data-ttu-id="a1b08-132">요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-132">Element</span></span>|<span data-ttu-id="a1b08-133">설명</span><span class="sxs-lookup"><span data-stu-id="a1b08-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1b08-134">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="a1b08-135">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1b08-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1b08-136">설명</span><span class="sxs-lookup"><span data-stu-id="a1b08-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a1b08-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1b08-137">See Also</span></span>

[<span data-ttu-id="a1b08-138">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="a1b08-139">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="a1b08-140">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="a1b08-141">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="a1b08-142">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="a1b08-143">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="a1b08-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="a1b08-144">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="a1b08-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
