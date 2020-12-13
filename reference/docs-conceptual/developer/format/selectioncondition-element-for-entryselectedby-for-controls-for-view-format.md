---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: 16b048e73195b3d6168724714ff223851dc1b20b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664851"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="8f869-103">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-103">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="8f869-104">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-104">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="8f869-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8f869-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤 요소 (format) CustomControl 요소 컨트롤에 대 한 컨트롤 요소 view (format) Entry 항목의 경우 컨트롤의 customentries 요소에 대 한 customentries 요소에 대 한 컨트롤의 Customentries 요소 (형식)에 대 한 컨트롤의 경우 EntrySelectedBy의 view (format) SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="8f869-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f869-107">구문</span><span class="sxs-lookup"><span data-stu-id="8f869-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f869-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8f869-108">Attributes and Elements</span></span>

<span data-ttu-id="8f869-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="8f869-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f869-110">특성</span><span class="sxs-lookup"><span data-stu-id="8f869-110">Attributes</span></span>

<span data-ttu-id="8f869-111">없음</span><span class="sxs-lookup"><span data-stu-id="8f869-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f869-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8f869-112">Child Elements</span></span>

|<span data-ttu-id="8f869-113">요소</span><span class="sxs-lookup"><span data-stu-id="8f869-113">Element</span></span>|<span data-ttu-id="8f869-114">설명</span><span class="sxs-lookup"><span data-stu-id="8f869-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f869-115">View에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-115">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f869-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-116">Optional element.</span></span><br /><br /> <span data-ttu-id="8f869-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8f869-118">View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-118">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f869-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-119">Optional element.</span></span><br /><br /> <span data-ttu-id="8f869-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8f869-121">View에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-121">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f869-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-122">Optional element.</span></span><br /><br /> <span data-ttu-id="8f869-123">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8f869-124">View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-124">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8f869-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-125">Optional element.</span></span><br /><br /> <span data-ttu-id="8f869-126">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f869-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8f869-127">Parent Elements</span></span>

|<span data-ttu-id="8f869-128">요소</span><span class="sxs-lookup"><span data-stu-id="8f869-128">Element</span></span>|<span data-ttu-id="8f869-129">설명</span><span class="sxs-lookup"><span data-stu-id="8f869-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f869-130">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-130">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="8f869-131">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f869-132">설명</span><span class="sxs-lookup"><span data-stu-id="8f869-132">Remarks</span></span>

<span data-ttu-id="8f869-133">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8f869-134">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8f869-135">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f869-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8f869-136">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f869-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f869-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f869-137">See Also</span></span>

[<span data-ttu-id="8f869-138">View에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-138">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f869-139">View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-139">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f869-140">View에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-140">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f869-141">View에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-141">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8f869-142">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8f869-142">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="8f869-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8f869-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
