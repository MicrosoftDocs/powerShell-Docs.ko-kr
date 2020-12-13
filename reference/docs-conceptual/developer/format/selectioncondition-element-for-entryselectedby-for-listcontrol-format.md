---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655093"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="63311-103">ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="63311-103">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="63311-104">목록 뷰의이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63311-104">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="63311-105">목록 정의에 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63311-105">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="63311-106">Configuration 요소 (Format) ViewDefinitions 요소 (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대해 ListEntry (format) SelectionCondition 요소에 대해 ListEntry (형식)에 대 한 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="63311-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63311-107">구문</span><span class="sxs-lookup"><span data-stu-id="63311-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63311-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="63311-108">Attributes and Elements</span></span>

<span data-ttu-id="63311-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="63311-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63311-110">특성</span><span class="sxs-lookup"><span data-stu-id="63311-110">Attributes</span></span>

<span data-ttu-id="63311-111">없음</span><span class="sxs-lookup"><span data-stu-id="63311-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63311-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="63311-112">Child Elements</span></span>

|<span data-ttu-id="63311-113">요소</span><span class="sxs-lookup"><span data-stu-id="63311-113">Element</span></span>|<span data-ttu-id="63311-114">설명</span><span class="sxs-lookup"><span data-stu-id="63311-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63311-115">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="63311-115">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="63311-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="63311-116">Optional element.</span></span><br /><br /> <span data-ttu-id="63311-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63311-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="63311-118">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="63311-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="63311-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="63311-119">Optional element.</span></span><br /><br /> <span data-ttu-id="63311-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63311-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="63311-121">ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="63311-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="63311-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="63311-122">Optional element.</span></span><br /><br /> <span data-ttu-id="63311-123">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63311-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="63311-124">ListEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="63311-124">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="63311-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="63311-125">Optional element.</span></span><br /><br /> <span data-ttu-id="63311-126">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63311-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63311-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="63311-127">Parent Elements</span></span>

|<span data-ttu-id="63311-128">요소</span><span class="sxs-lookup"><span data-stu-id="63311-128">Element</span></span>|<span data-ttu-id="63311-129">설명</span><span class="sxs-lookup"><span data-stu-id="63311-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63311-130">TableRowEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="63311-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="63311-131">이 테이블 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63311-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63311-132">설명</span><span class="sxs-lookup"><span data-stu-id="63311-132">Remarks</span></span>

<span data-ttu-id="63311-133">lWhen 선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63311-133">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="63311-134">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63311-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="63311-135">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63311-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="63311-136">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63311-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="63311-137">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63311-137">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63311-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63311-138">See Also</span></span>

[<span data-ttu-id="63311-139">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="63311-139">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="63311-140">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="63311-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="63311-141">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="63311-141">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="63311-142">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="63311-142">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="63311-143">ListEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="63311-143">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="63311-144">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="63311-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
