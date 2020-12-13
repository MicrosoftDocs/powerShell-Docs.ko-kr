---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: 22f304615c6433ffb67f3b4046b645d0c37be8a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645756"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ca623-103">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ca623-103">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ca623-104">테이블 뷰의이 정의에 사용할 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-104">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="ca623-105">테이블 정의에 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-105">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="ca623-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소에 대해 TableRowEntry (format) SelectionCondition 요소에 대해 TableRowEntry (형식)에 대 한 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="ca623-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca623-107">구문</span><span class="sxs-lookup"><span data-stu-id="ca623-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca623-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-108">Attributes and Elements</span></span>

<span data-ttu-id="ca623-109">다음 섹션에서는 SelectionCondition 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-109">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca623-110">특성</span><span class="sxs-lookup"><span data-stu-id="ca623-110">Attributes</span></span>

<span data-ttu-id="ca623-111">없음</span><span class="sxs-lookup"><span data-stu-id="ca623-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca623-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-112">Child Elements</span></span>

|<span data-ttu-id="ca623-113">요소</span><span class="sxs-lookup"><span data-stu-id="ca623-113">Element</span></span>|<span data-ttu-id="ca623-114">설명</span><span class="sxs-lookup"><span data-stu-id="ca623-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca623-115">TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ca623-115">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="ca623-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ca623-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="ca623-118">TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="ca623-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ca623-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="ca623-121">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="ca623-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ca623-123">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="ca623-124">TableRowEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-124">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="ca623-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-125">Optional element.</span></span><br /><br /> <span data-ttu-id="ca623-126">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca623-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-127">Parent Elements</span></span>

|<span data-ttu-id="ca623-128">요소</span><span class="sxs-lookup"><span data-stu-id="ca623-128">Element</span></span>|<span data-ttu-id="ca623-129">설명</span><span class="sxs-lookup"><span data-stu-id="ca623-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca623-130">TableRowEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ca623-131">이 테이블 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca623-132">설명</span><span class="sxs-lookup"><span data-stu-id="ca623-132">Remarks</span></span>

<span data-ttu-id="ca623-133">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-133">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ca623-134">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-134">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="ca623-135">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-135">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="ca623-136">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca623-136">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="ca623-137">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca623-137">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ca623-138">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca623-138">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca623-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca623-139">See Also</span></span>

[<span data-ttu-id="ca623-140">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ca623-140">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ca623-141">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="ca623-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ca623-142">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ca623-142">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ca623-143">TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ca623-143">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="ca623-144">TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-144">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ca623-145">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-145">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ca623-146">TableRowEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="ca623-146">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ca623-147">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ca623-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
