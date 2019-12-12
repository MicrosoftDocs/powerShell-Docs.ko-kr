---
title: TableRowEntries의 TableControl 요소에 대 한 TableRowEntry 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361802"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="fe8f9-102">TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="fe8f9-103">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="fe8f9-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소에 대 한 TableControl (format) TableRowEntry Element for TableRowEntries (Format)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe8f9-105">구문</span><span class="sxs-lookup"><span data-stu-id="fe8f9-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe8f9-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fe8f9-106">Attributes and Elements</span></span>

<span data-ttu-id="fe8f9-107">다음 섹션에서는 특성, 자식 요소 및 `TableRowEntry` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe8f9-108">특성</span><span class="sxs-lookup"><span data-stu-id="fe8f9-108">Attributes</span></span>

<span data-ttu-id="fe8f9-109">없음</span><span class="sxs-lookup"><span data-stu-id="fe8f9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe8f9-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fe8f9-110">Child Elements</span></span>

|<span data-ttu-id="fe8f9-111">요소</span><span class="sxs-lookup"><span data-stu-id="fe8f9-111">Element</span></span>|<span data-ttu-id="fe8f9-112">설명</span><span class="sxs-lookup"><span data-stu-id="fe8f9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe8f9-113">TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="fe8f9-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fe8f9-114">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-114">Required element.</span></span><br /><br /> <span data-ttu-id="fe8f9-115">해당 속성 값이 행에 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="fe8f9-116">TableControl의 TableRowEntry 요소에 대 한 TableColumnItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fe8f9-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-117">Required element.</span></span><br /><br /> <span data-ttu-id="fe8f9-118">값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="fe8f9-119">TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="fe8f9-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="fe8f9-121">열 너비를 초과 하는 텍스트를 다음 줄에 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fe8f9-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fe8f9-122">Parent Elements</span></span>

|<span data-ttu-id="fe8f9-123">요소</span><span class="sxs-lookup"><span data-stu-id="fe8f9-123">Element</span></span>|<span data-ttu-id="fe8f9-124">설명</span><span class="sxs-lookup"><span data-stu-id="fe8f9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe8f9-125">TableControl에 대 한 TableRowEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="fe8f9-126">테이블의 행을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fe8f9-127">설명</span><span class="sxs-lookup"><span data-stu-id="fe8f9-127">Remarks</span></span>

<span data-ttu-id="fe8f9-128">`TableColumnItems` 요소 하 나와 `EntrySelectedBy` 요소 하나를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="fe8f9-129">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fe8f9-130">예제</span><span class="sxs-lookup"><span data-stu-id="fe8f9-130">Example</span></span>

<span data-ttu-id="fe8f9-131">다음 예에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 `TableRowEntry` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe8f9-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fe8f9-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe8f9-132">See Also</span></span>

[<span data-ttu-id="fe8f9-133">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="fe8f9-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fe8f9-134">TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="fe8f9-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fe8f9-135">TableControl의 TableRowEntry 요소에 대 한 TableColumnItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fe8f9-136">TableControl에 대 한 TableRowEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="fe8f9-137">TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fe8f9-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="fe8f9-138">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fe8f9-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
