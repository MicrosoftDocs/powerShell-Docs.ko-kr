---
title: TableRowEntries의 TableControl 요소에 대 한 TableRowEntry 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 83076ae5b2c48992ce5e621c65fc9937efb68b87
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787413"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="7364a-102">TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7364a-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="7364a-103">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="7364a-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소에 대 한 TableControl (format) TableRowEntry Element for TableRowEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="7364a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7364a-105">구문</span><span class="sxs-lookup"><span data-stu-id="7364a-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7364a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7364a-106">Attributes and Elements</span></span>

<span data-ttu-id="7364a-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableRowEntry` .</span><span class="sxs-lookup"><span data-stu-id="7364a-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7364a-108">특성</span><span class="sxs-lookup"><span data-stu-id="7364a-108">Attributes</span></span>

<span data-ttu-id="7364a-109">없음</span><span class="sxs-lookup"><span data-stu-id="7364a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7364a-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7364a-110">Child Elements</span></span>

|<span data-ttu-id="7364a-111">요소</span><span class="sxs-lookup"><span data-stu-id="7364a-111">Element</span></span>|<span data-ttu-id="7364a-112">설명</span><span class="sxs-lookup"><span data-stu-id="7364a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7364a-113">TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="7364a-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="7364a-114">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-114">Required element.</span></span><br /><br /> <span data-ttu-id="7364a-115">해당 속성 값이 행에 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="7364a-116">TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7364a-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="7364a-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-117">Required element.</span></span><br /><br /> <span data-ttu-id="7364a-118">값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="7364a-119">TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7364a-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="7364a-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7364a-121">열 너비를 초과 하는 텍스트를 다음 줄에 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7364a-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7364a-122">Parent Elements</span></span>

|<span data-ttu-id="7364a-123">요소</span><span class="sxs-lookup"><span data-stu-id="7364a-123">Element</span></span>|<span data-ttu-id="7364a-124">설명</span><span class="sxs-lookup"><span data-stu-id="7364a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7364a-125">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7364a-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="7364a-126">테이블의 행을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7364a-127">설명</span><span class="sxs-lookup"><span data-stu-id="7364a-127">Remarks</span></span>

<span data-ttu-id="7364a-128">`TableColumnItems`요소 하 나와 요소 하나를 `EntrySelectedBy` 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="7364a-129">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7364a-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7364a-130">예제</span><span class="sxs-lookup"><span data-stu-id="7364a-130">Example</span></span>

<span data-ttu-id="7364a-131">다음 예제에서는 `TableRowEntry` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7364a-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7364a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7364a-132">See Also</span></span>

[<span data-ttu-id="7364a-133">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="7364a-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7364a-134">TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="7364a-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="7364a-135">TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7364a-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="7364a-136">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7364a-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="7364a-137">TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7364a-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="7364a-138">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="7364a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
