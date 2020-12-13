---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)
description: TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)
ms.openlocfilehash: 60d64b7c14b40e87825ada36e19f52a66fe8b6cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659766"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="fc2dd-103">TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-103">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="fc2dd-104">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-104">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="fc2dd-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소에 대 한 TableControl (format) TableRowEntry Element for TableRowEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc2dd-106">구문</span><span class="sxs-lookup"><span data-stu-id="fc2dd-106">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc2dd-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fc2dd-107">Attributes and Elements</span></span>

<span data-ttu-id="fc2dd-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableRowEntry` .</span><span class="sxs-lookup"><span data-stu-id="fc2dd-108">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc2dd-109">특성</span><span class="sxs-lookup"><span data-stu-id="fc2dd-109">Attributes</span></span>

<span data-ttu-id="fc2dd-110">없음</span><span class="sxs-lookup"><span data-stu-id="fc2dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc2dd-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fc2dd-111">Child Elements</span></span>

|<span data-ttu-id="fc2dd-112">요소</span><span class="sxs-lookup"><span data-stu-id="fc2dd-112">Element</span></span>|<span data-ttu-id="fc2dd-113">설명</span><span class="sxs-lookup"><span data-stu-id="fc2dd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc2dd-114">TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="fc2dd-114">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fc2dd-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-115">Required element.</span></span><br /><br /> <span data-ttu-id="fc2dd-116">해당 속성 값이 행에 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-116">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="fc2dd-117">TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-117">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fc2dd-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-118">Required element.</span></span><br /><br /> <span data-ttu-id="fc2dd-119">값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-119">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="fc2dd-120">TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-120">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fc2dd-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="fc2dd-122">열 너비를 초과 하는 텍스트를 다음 줄에 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-122">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fc2dd-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fc2dd-123">Parent Elements</span></span>

|<span data-ttu-id="fc2dd-124">요소</span><span class="sxs-lookup"><span data-stu-id="fc2dd-124">Element</span></span>|<span data-ttu-id="fc2dd-125">설명</span><span class="sxs-lookup"><span data-stu-id="fc2dd-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc2dd-126">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-126">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="fc2dd-127">테이블의 행을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-127">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fc2dd-128">설명</span><span class="sxs-lookup"><span data-stu-id="fc2dd-128">Remarks</span></span>

<span data-ttu-id="fc2dd-129">`TableColumnItems`요소 하 나와 요소 하나를 `EntrySelectedBy` 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-129">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="fc2dd-130">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-130">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc2dd-131">예제</span><span class="sxs-lookup"><span data-stu-id="fc2dd-131">Example</span></span>

<span data-ttu-id="fc2dd-132">다음 예제에서는 `TableRowEntry` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fc2dd-132">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="fc2dd-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc2dd-133">See Also</span></span>

[<span data-ttu-id="fc2dd-134">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="fc2dd-134">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fc2dd-135">TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="fc2dd-135">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fc2dd-136">TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-136">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fc2dd-137">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-137">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="fc2dd-138">TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fc2dd-138">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fc2dd-139">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fc2dd-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
