---
title: GroupBy (형식)의 CustomItem에 대 한 ExpressionBinding 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5b0017e487aab4ffcbf901cd44aad9b275b22832
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773728"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="8bad3-102">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="8bad3-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="8bad3-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8bad3-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소에 대 한 CustomControl 요소의 groupby (format) customentries 요소에 대 한 CustomControl의 경우 CustomControl에 대 한 customentries 요소에 대 한 Customentries 요소에 대 한 Customentries 요소</span><span class="sxs-lookup"><span data-stu-id="8bad3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8bad3-106">구문</span><span class="sxs-lookup"><span data-stu-id="8bad3-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8bad3-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8bad3-107">Attributes and Elements</span></span>

<span data-ttu-id="8bad3-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ExpressionBinding` .</span><span class="sxs-lookup"><span data-stu-id="8bad3-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8bad3-109">특성</span><span class="sxs-lookup"><span data-stu-id="8bad3-109">Attributes</span></span>

<span data-ttu-id="8bad3-110">없음</span><span class="sxs-lookup"><span data-stu-id="8bad3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8bad3-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8bad3-111">Child Elements</span></span>

|<span data-ttu-id="8bad3-112">요소</span><span class="sxs-lookup"><span data-stu-id="8bad3-112">Element</span></span>|<span data-ttu-id="8bad3-113">설명</span><span class="sxs-lookup"><span data-stu-id="8bad3-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="8bad3-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8bad3-115">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="8bad3-116">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bad3-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8bad3-118">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="8bad3-119">[GroupBy (형식)에 대 한 ExpressionBinding의 Enumeratecollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) GroupBy (형식)에 대 한 ExpressionBinding의 EnumerateCollection 요소</span><span class="sxs-lookup"><span data-stu-id="8bad3-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="8bad3-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8bad3-121">컬렉션의 요소가 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="8bad3-122">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bad3-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-123">Optional element.</span></span><br /><br /> <span data-ttu-id="8bad3-124">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="8bad3-125">GroupBy의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bad3-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-126">Optional element.</span></span><br /><br /> <span data-ttu-id="8bad3-127">컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="8bad3-128">GroupBy의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="8bad3-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-129">Optional element.</span></span><br /><br /> <span data-ttu-id="8bad3-130">컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8bad3-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8bad3-131">Parent Elements</span></span>

|<span data-ttu-id="8bad3-132">요소</span><span class="sxs-lookup"><span data-stu-id="8bad3-132">Element</span></span>|<span data-ttu-id="8bad3-133">설명</span><span class="sxs-lookup"><span data-stu-id="8bad3-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8bad3-134">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="8bad3-135">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bad3-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8bad3-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8bad3-136">See Also</span></span>

[<span data-ttu-id="8bad3-137">GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bad3-138">GroupBy의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bad3-139">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bad3-140">GroupBy의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bad3-141">GroupBy의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="8bad3-142">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8bad3-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="8bad3-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8bad3-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
