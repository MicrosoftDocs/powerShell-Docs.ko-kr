---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: 8c51ca72edc6ad174dc289c61a8987e8f9495d19
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655105"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="f784f-103">WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f784f-103">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="f784f-104">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-104">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="f784f-105">넓은 항목 정의에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-105">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="f784f-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대해 WideEntry (format) SelectionCondition 요소에 대해 WideEntry (형식)에 대 한 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="f784f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f784f-107">구문</span><span class="sxs-lookup"><span data-stu-id="f784f-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f784f-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f784f-108">Attributes and Elements</span></span>

<span data-ttu-id="f784f-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="f784f-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="f784f-110">단일 또는 요소를 지정 해야 합니다 `PropertyName` `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="f784f-110">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="f784f-111">`SelectionSetName`및 `TypeName` 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-111">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="f784f-112">두 요소 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-112">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f784f-113">특성</span><span class="sxs-lookup"><span data-stu-id="f784f-113">Attributes</span></span>

<span data-ttu-id="f784f-114">없음</span><span class="sxs-lookup"><span data-stu-id="f784f-114">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f784f-115">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f784f-115">Child Elements</span></span>

|<span data-ttu-id="f784f-116">요소</span><span class="sxs-lookup"><span data-stu-id="f784f-116">Element</span></span>|<span data-ttu-id="f784f-117">설명</span><span class="sxs-lookup"><span data-stu-id="f784f-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f784f-118">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f784f-118">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="f784f-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f784f-120">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-120">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f784f-121">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="f784f-121">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f784f-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f784f-123">조건을 트리거하는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-123">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="f784f-124">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f784f-124">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="f784f-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f784f-126">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-126">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f784f-127">WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="f784f-127">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f784f-128">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-128">Optional element.</span></span><br /><br /> <span data-ttu-id="f784f-129">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-129">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f784f-130">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f784f-130">Parent Elements</span></span>

|<span data-ttu-id="f784f-131">요소</span><span class="sxs-lookup"><span data-stu-id="f784f-131">Element</span></span>|<span data-ttu-id="f784f-132">설명</span><span class="sxs-lookup"><span data-stu-id="f784f-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f784f-133">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f784f-133">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="f784f-134">이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-134">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f784f-135">설명</span><span class="sxs-lookup"><span data-stu-id="f784f-135">Remarks</span></span>

<span data-ttu-id="f784f-136">각 넓은 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-136">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f784f-137">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-137">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f784f-138">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-138">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f784f-139">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f784f-139">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f784f-140">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f784f-140">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f784f-141">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f784f-141">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f784f-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f784f-142">See Also</span></span>

[<span data-ttu-id="f784f-143">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="f784f-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f784f-144">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="f784f-144">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f784f-145">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f784f-145">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="f784f-146">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f784f-146">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f784f-147">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="f784f-147">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f784f-148">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f784f-148">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f784f-149">WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="f784f-149">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f784f-150">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f784f-150">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
