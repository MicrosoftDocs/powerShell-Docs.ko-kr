---
title: TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 047a10fb6b38dfa8f78a7741fd50b781d4a14b6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787702"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="76ce1-102">TableControl의 TableRowEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="76ce1-103">이 정의를 사용 하기 위해 존재 해야 하는 조건 또는이 테이블 뷰의 정의를 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="76ce1-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="76ce1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76ce1-105">구문</span><span class="sxs-lookup"><span data-stu-id="76ce1-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76ce1-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="76ce1-106">Attributes and Elements</span></span>

<span data-ttu-id="76ce1-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="76ce1-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76ce1-108">특성</span><span class="sxs-lookup"><span data-stu-id="76ce1-108">Attributes</span></span>

<span data-ttu-id="76ce1-109">없음</span><span class="sxs-lookup"><span data-stu-id="76ce1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76ce1-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="76ce1-110">Child Elements</span></span>

|<span data-ttu-id="76ce1-111">요소</span><span class="sxs-lookup"><span data-stu-id="76ce1-111">Element</span></span>|<span data-ttu-id="76ce1-112">설명</span><span class="sxs-lookup"><span data-stu-id="76ce1-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76ce1-113">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="76ce1-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="76ce1-115">이 테이블 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="76ce1-116">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="76ce1-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="76ce1-118">이 테이블 뷰 정의를 사용 하는 .NET 유형 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="76ce1-119">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="76ce1-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="76ce1-121">이 테이블 뷰 정의를 사용 하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="76ce1-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="76ce1-122">Parent Elements</span></span>

|<span data-ttu-id="76ce1-123">요소</span><span class="sxs-lookup"><span data-stu-id="76ce1-123">Element</span></span>|<span data-ttu-id="76ce1-124">설명</span><span class="sxs-lookup"><span data-stu-id="76ce1-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76ce1-125">TableControl에 대 한 TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="76ce1-126">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="76ce1-127">설명</span><span class="sxs-lookup"><span data-stu-id="76ce1-127">Remarks</span></span>

<span data-ttu-id="76ce1-128">테이블 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="76ce1-129">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="76ce1-130">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="76ce1-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="76ce1-131">선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76ce1-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="76ce1-132">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76ce1-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="76ce1-133">예제</span><span class="sxs-lookup"><span data-stu-id="76ce1-133">Example</span></span>

<span data-ttu-id="76ce1-134">다음 예제에서는 `TableRowEntry` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 표시 하는 데 사용 되는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76ce1-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="76ce1-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76ce1-135">See Also</span></span>

[<span data-ttu-id="76ce1-136">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="76ce1-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="76ce1-137">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="76ce1-138">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="76ce1-139">TableControl에 대 한 TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="76ce1-140">TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="76ce1-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="76ce1-141">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="76ce1-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
