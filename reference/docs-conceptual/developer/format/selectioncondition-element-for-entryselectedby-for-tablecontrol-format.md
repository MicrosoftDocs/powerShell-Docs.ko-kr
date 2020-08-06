---
title: TableControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4a829f9daef22c4b3fd6b21dfb3af2f8539bdeb3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780290"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="2e7c3-102">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2e7c3-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="2e7c3-103">테이블 뷰의이 정의에 사용할 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="2e7c3-104">테이블 정의에 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="2e7c3-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소에 대해 TableRowEntry (format) SelectionCondition 요소에 대해 TableRowEntry (형식)에 대 한 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="2e7c3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e7c3-106">구문</span><span class="sxs-lookup"><span data-stu-id="2e7c3-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e7c3-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-107">Attributes and Elements</span></span>

<span data-ttu-id="2e7c3-108">다음 섹션에서는 SelectionCondition 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e7c3-109">특성</span><span class="sxs-lookup"><span data-stu-id="2e7c3-109">Attributes</span></span>

<span data-ttu-id="2e7c3-110">없음</span><span class="sxs-lookup"><span data-stu-id="2e7c3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e7c3-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-111">Child Elements</span></span>

|<span data-ttu-id="2e7c3-112">요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-112">Element</span></span>|<span data-ttu-id="2e7c3-113">설명</span><span class="sxs-lookup"><span data-stu-id="2e7c3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e7c3-114">TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2e7c3-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="2e7c3-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2e7c3-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2e7c3-117">TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2e7c3-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2e7c3-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2e7c3-120">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2e7c3-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2e7c3-122">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="2e7c3-123">TableRowEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2e7c3-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2e7c3-125">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2e7c3-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-126">Parent Elements</span></span>

|<span data-ttu-id="2e7c3-127">요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-127">Element</span></span>|<span data-ttu-id="2e7c3-128">설명</span><span class="sxs-lookup"><span data-stu-id="2e7c3-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e7c3-129">TableRowEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2e7c3-130">이 테이블 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2e7c3-131">설명</span><span class="sxs-lookup"><span data-stu-id="2e7c3-131">Remarks</span></span>

<span data-ttu-id="2e7c3-132">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2e7c3-133">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2e7c3-134">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2e7c3-135">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2e7c3-136">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2e7c3-137">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2e7c3-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e7c3-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e7c3-138">See Also</span></span>

[<span data-ttu-id="2e7c3-139">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="2e7c3-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2e7c3-140">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="2e7c3-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2e7c3-141">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2e7c3-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2e7c3-142">TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2e7c3-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="2e7c3-143">TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2e7c3-144">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2e7c3-145">TableRowEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="2e7c3-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2e7c3-146">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2e7c3-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
