---
title: CustomControl 용 CustomItem에 대 한 ExpressionBinding 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1885a2820c0cb250aa6fda80544f58d06136cfeb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773796"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="20459-102">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="20459-103">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="20459-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20459-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="20459-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl 요소에 대 한 view (format) Customentries 요소의 view (format) customentries 요소에 대 한 customentries 요소에 대 한 Customentries 요소 (view)의 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="20459-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20459-106">구문</span><span class="sxs-lookup"><span data-stu-id="20459-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="20459-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="20459-107">Attributes and Elements</span></span>

<span data-ttu-id="20459-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ExpressionBinding` .</span><span class="sxs-lookup"><span data-stu-id="20459-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20459-109">특성</span><span class="sxs-lookup"><span data-stu-id="20459-109">Attributes</span></span>

<span data-ttu-id="20459-110">없음</span><span class="sxs-lookup"><span data-stu-id="20459-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20459-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="20459-111">Child Elements</span></span>

|<span data-ttu-id="20459-112">요소</span><span class="sxs-lookup"><span data-stu-id="20459-112">Element</span></span>|<span data-ttu-id="20459-113">설명</span><span class="sxs-lookup"><span data-stu-id="20459-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="20459-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20459-114">Optional element.</span></span><br /><br /> <span data-ttu-id="20459-115">이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="20459-116">View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20459-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20459-117">Optional element.</span></span><br /><br /> <span data-ttu-id="20459-118">공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="20459-119">View에 대한 CustomControl의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20459-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20459-120">Optional element.</span></span><br /><br /> <span data-ttu-id="20459-121">컬렉션의 요소가 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="20459-122">CustomControl에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="20459-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="20459-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20459-123">Optional element.</span></span><br /><br /> <span data-ttu-id="20459-124">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="20459-125">View에 대한 CustomControl의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20459-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20459-126">Optional element.</span></span><br /><br /> <span data-ttu-id="20459-127">컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="20459-128">CustomCustomControl에 대 한 ExpressionBinding의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="20459-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="20459-129">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20459-129">Optional element.</span></span><br /><br /> <span data-ttu-id="20459-130">컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20459-131">부모 요소</span><span class="sxs-lookup"><span data-stu-id="20459-131">Parent Elements</span></span>

|<span data-ttu-id="20459-132">요소</span><span class="sxs-lookup"><span data-stu-id="20459-132">Element</span></span>|<span data-ttu-id="20459-133">설명</span><span class="sxs-lookup"><span data-stu-id="20459-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20459-134">View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="20459-135">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="20459-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20459-136">설명</span><span class="sxs-lookup"><span data-stu-id="20459-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="20459-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20459-137">See Also</span></span>

[<span data-ttu-id="20459-138">View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20459-139">View에 대한 CustomControl의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20459-140">CustomControl에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="20459-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="20459-141">View에 대한 CustomControl의 ExpressionBinding에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20459-142">View에 대한 CustomControl의 ExpressionBinding에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20459-143">View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20459-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="20459-144">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="20459-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
