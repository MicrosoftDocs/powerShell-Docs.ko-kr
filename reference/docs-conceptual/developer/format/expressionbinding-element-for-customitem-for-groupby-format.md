---
title: GroupBy (형식)의 CustomItem에 대 한 ExpressionBinding 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368632"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="36687-102">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="36687-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="36687-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="36687-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36687-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="36687-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 CustomControl (형식)에 대 한 customitem에 대 한 customitem에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="36687-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36687-106">구문</span><span class="sxs-lookup"><span data-stu-id="36687-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="36687-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="36687-107">Attributes and Elements</span></span>

<span data-ttu-id="36687-108">다음 섹션에서는 특성, 자식 요소 및 `ExpressionBinding` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36687-109">특성</span><span class="sxs-lookup"><span data-stu-id="36687-109">Attributes</span></span>

<span data-ttu-id="36687-110">없음</span><span class="sxs-lookup"><span data-stu-id="36687-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36687-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="36687-111">Child Elements</span></span>

|<span data-ttu-id="36687-112">요소</span><span class="sxs-lookup"><span data-stu-id="36687-112">Element</span></span>|<span data-ttu-id="36687-113">설명</span><span class="sxs-lookup"><span data-stu-id="36687-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="36687-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36687-114">Optional element.</span></span><br /><br /> <span data-ttu-id="36687-115">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="36687-116">GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="36687-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="36687-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36687-117">Optional element.</span></span><br /><br /> <span data-ttu-id="36687-118">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="36687-119">[GroupBy (형식)에 대 한 ExpressionBinding의 Enumeratecollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) GroupBy (형식)에 대 한 ExpressionBinding의 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="36687-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="36687-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36687-120">Optional element.</span></span><br /><br /> <span data-ttu-id="36687-121">컬렉션의 요소가 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="36687-122">GroupBy (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="36687-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="36687-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36687-123">Optional element.</span></span><br /><br /> <span data-ttu-id="36687-124">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="36687-125">GroupBy (형식)에 대 한 ExpressionBinding의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="36687-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="36687-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36687-126">Optional element.</span></span><br /><br /> <span data-ttu-id="36687-127">컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="36687-128">GroupBy (형식)에 대 한 ExpressionBinding의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="36687-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="36687-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36687-129">Optional element.</span></span><br /><br /> <span data-ttu-id="36687-130">컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="36687-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="36687-131">Parent Elements</span></span>

|<span data-ttu-id="36687-132">요소</span><span class="sxs-lookup"><span data-stu-id="36687-132">Element</span></span>|<span data-ttu-id="36687-133">설명</span><span class="sxs-lookup"><span data-stu-id="36687-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36687-134">GroupBy (형식)에 대 한 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="36687-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="36687-135">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36687-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="36687-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36687-136">See Also</span></span>

[<span data-ttu-id="36687-137">GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="36687-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="36687-138">GroupBy (형식)에 대 한 ExpressionBinding의 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="36687-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="36687-139">GroupBy (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="36687-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="36687-140">GroupBy (형식)에 대 한 ExpressionBinding의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="36687-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="36687-141">GroupBy (형식)에 대 한 ExpressionBinding의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="36687-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="36687-142">GroupBy (형식)에 대 한 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="36687-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="36687-143">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="36687-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
