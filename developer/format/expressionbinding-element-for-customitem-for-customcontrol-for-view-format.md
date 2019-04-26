---
title: ExpressionBinding 요소 CustomControl 보려면 (형식)에 대 한 CustomItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065923"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="b3716-102">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b3716-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="b3716-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b3716-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b3716-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 CustomControl CustomEntries CustomControl 보기 (에 대 한 보기 (형식) CustomEntry 요소에 대 한 보기 (형식) CustomEntries 요소에 CustomControl CustomItem CustomControl 보려면 (형식)에 대 한 보기 (형식) ExpressionBinding 요소에 대 한 CustomEntry CustomItem 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="b3716-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3716-106">구문</span><span class="sxs-lookup"><span data-stu-id="b3716-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b3716-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-107">Attributes and Elements</span></span>

<span data-ttu-id="b3716-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ExpressionBinding` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3716-109">특성</span><span class="sxs-lookup"><span data-stu-id="b3716-109">Attributes</span></span>

<span data-ttu-id="b3716-110">없음</span><span class="sxs-lookup"><span data-stu-id="b3716-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3716-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-111">Child Elements</span></span>

|<span data-ttu-id="b3716-112">요소</span><span class="sxs-lookup"><span data-stu-id="b3716-112">Element</span></span>|<span data-ttu-id="b3716-113">설명</span><span class="sxs-lookup"><span data-stu-id="b3716-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b3716-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b3716-115">이 컨트롤에서 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b3716-116">ExpressionBinding CustomControl 보려면 (형식)에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3716-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b3716-118">공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="b3716-119">ExpressionBinding CustomControl 보려면 (형식)에 대 한 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3716-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b3716-121">지정한 컬렉션의 요소는 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b3716-122">ExpressionBinding CustomControl 보려면 (형식)에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="b3716-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b3716-124">이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b3716-125">ExpressionBinding CustomControl 보려면 (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3716-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b3716-127">컨트롤에서 해당 값이 표시.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b3716-128">ExpressionBinding CustomCustomControl 보려면 (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3716-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b3716-130">컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b3716-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-131">Parent Elements</span></span>

|<span data-ttu-id="b3716-132">요소</span><span class="sxs-lookup"><span data-stu-id="b3716-132">Element</span></span>|<span data-ttu-id="b3716-133">설명</span><span class="sxs-lookup"><span data-stu-id="b3716-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3716-134">CustomControl 보려면 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3716-135">사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3716-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b3716-136">설명</span><span class="sxs-lookup"><span data-stu-id="b3716-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b3716-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3716-137">See Also</span></span>

[<span data-ttu-id="b3716-138">ExpressionBinding CustomControl 보려면 (형식)에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3716-139">ExpressionBinding CustomControl 보려면 (형식)에 대 한 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3716-140">ExpressionBinding CustomControl 보려면 (형식)에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="b3716-141">ExpressionBinding CustomControl 보려면 (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3716-142">ExpressionBinding CustomControl 보려면 (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3716-143">CustomControl 보려면 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="b3716-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3716-144">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="b3716-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
