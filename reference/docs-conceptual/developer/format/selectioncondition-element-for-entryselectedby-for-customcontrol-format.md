---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: CustomControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: 6d4cc5a2d5fef0445d586e320b3729d3a7044063
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649766"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="41e86-103">CustomControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-103">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="41e86-104">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-104">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="41e86-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="41e86-106">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) Customentries 요소 CustomControl for view (format) EntrySelectedBy for view (format) CustomControl for view (format) SelectionCondition Element for CustomControl for view (Format)</span><span class="sxs-lookup"><span data-stu-id="41e86-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41e86-107">구문</span><span class="sxs-lookup"><span data-stu-id="41e86-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41e86-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="41e86-108">Attributes and Elements</span></span>

<span data-ttu-id="41e86-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="41e86-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41e86-110">특성</span><span class="sxs-lookup"><span data-stu-id="41e86-110">Attributes</span></span>

<span data-ttu-id="41e86-111">없음</span><span class="sxs-lookup"><span data-stu-id="41e86-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41e86-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="41e86-112">Child Elements</span></span>

|<span data-ttu-id="41e86-113">요소</span><span class="sxs-lookup"><span data-stu-id="41e86-113">Element</span></span>|<span data-ttu-id="41e86-114">설명</span><span class="sxs-lookup"><span data-stu-id="41e86-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41e86-115">View에 대한 CustomControl의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-115">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="41e86-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-116">Optional element.</span></span><br /><br /> <span data-ttu-id="41e86-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="41e86-118">View에 대한 CustomControl의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-118">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="41e86-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-119">Optional element.</span></span><br /><br /> <span data-ttu-id="41e86-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="41e86-121">보기에 대 한 사용자 지정 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-121">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="41e86-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-122">Optional element.</span></span><br /><br /> <span data-ttu-id="41e86-123">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="41e86-124">View에 대한 CustomControl의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-124">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="41e86-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-125">Optional element.</span></span><br /><br /> <span data-ttu-id="41e86-126">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="41e86-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="41e86-127">Parent Elements</span></span>

|<span data-ttu-id="41e86-128">요소</span><span class="sxs-lookup"><span data-stu-id="41e86-128">Element</span></span>|<span data-ttu-id="41e86-129">설명</span><span class="sxs-lookup"><span data-stu-id="41e86-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41e86-130">View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-130">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="41e86-131">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="41e86-132">설명</span><span class="sxs-lookup"><span data-stu-id="41e86-132">Remarks</span></span>

<span data-ttu-id="41e86-133">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="41e86-134">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="41e86-135">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41e86-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="41e86-136">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41e86-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41e86-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="41e86-137">See Also</span></span>

[<span data-ttu-id="41e86-138">View에 대한 CustomControl의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-138">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41e86-139">View에 대한 CustomControl의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-139">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41e86-140">보기에 대 한 사용자 지정 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-140">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41e86-141">View에 대한 CustomControl의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-141">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41e86-142">View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="41e86-142">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="41e86-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="41e86-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
