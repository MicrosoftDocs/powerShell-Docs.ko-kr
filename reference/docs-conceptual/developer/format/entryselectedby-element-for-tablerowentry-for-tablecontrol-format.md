---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableRowEntry에 대한 EntrySelectedBy 요소(형식)
description: TableControl의 TableRowEntry에 대한 EntrySelectedBy 요소(형식)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645892"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="05bbb-103">TableControl의 TableRowEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-103">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="05bbb-104">이 정의를 사용 하기 위해 존재 해야 하는 조건 또는이 테이블 뷰의 정의를 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-104">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="05bbb-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="05bbb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05bbb-106">구문</span><span class="sxs-lookup"><span data-stu-id="05bbb-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05bbb-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="05bbb-107">Attributes and Elements</span></span>

<span data-ttu-id="05bbb-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="05bbb-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05bbb-109">특성</span><span class="sxs-lookup"><span data-stu-id="05bbb-109">Attributes</span></span>

<span data-ttu-id="05bbb-110">없음</span><span class="sxs-lookup"><span data-stu-id="05bbb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05bbb-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="05bbb-111">Child Elements</span></span>

|<span data-ttu-id="05bbb-112">요소</span><span class="sxs-lookup"><span data-stu-id="05bbb-112">Element</span></span>|<span data-ttu-id="05bbb-113">설명</span><span class="sxs-lookup"><span data-stu-id="05bbb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05bbb-114">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-114">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="05bbb-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="05bbb-116">이 테이블 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-116">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="05bbb-117">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-117">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="05bbb-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="05bbb-119">이 테이블 뷰 정의를 사용 하는 .NET 유형 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-119">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="05bbb-120">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-120">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="05bbb-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-121">Optional element.</span></span><br /><br /> <span data-ttu-id="05bbb-122">이 테이블 뷰 정의를 사용 하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-122">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="05bbb-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="05bbb-123">Parent Elements</span></span>

|<span data-ttu-id="05bbb-124">요소</span><span class="sxs-lookup"><span data-stu-id="05bbb-124">Element</span></span>|<span data-ttu-id="05bbb-125">설명</span><span class="sxs-lookup"><span data-stu-id="05bbb-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05bbb-126">TableControl에 대 한 TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-126">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="05bbb-127">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-127">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="05bbb-128">설명</span><span class="sxs-lookup"><span data-stu-id="05bbb-128">Remarks</span></span>

<span data-ttu-id="05bbb-129">테이블 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-129">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="05bbb-130">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="05bbb-131">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="05bbb-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="05bbb-132">선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05bbb-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="05bbb-133">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05bbb-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="05bbb-134">예제</span><span class="sxs-lookup"><span data-stu-id="05bbb-134">Example</span></span>

<span data-ttu-id="05bbb-135">다음 예제에서는 `TableRowEntry` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 표시 하는 데 사용 되는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05bbb-135">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="05bbb-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05bbb-136">See Also</span></span>

[<span data-ttu-id="05bbb-137">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="05bbb-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="05bbb-138">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-138">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="05bbb-139">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-139">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="05bbb-140">TableControl에 대 한 TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-140">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="05bbb-141">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="05bbb-141">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="05bbb-142">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="05bbb-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
