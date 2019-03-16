---
title: TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58059899"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="ecf81-102">TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="ecf81-103">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="ecf81-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소 TableControl (형식)에</span><span class="sxs-lookup"><span data-stu-id="ecf81-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ecf81-105">구문</span><span class="sxs-lookup"><span data-stu-id="ecf81-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ecf81-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-106">Attributes and Elements</span></span>

<span data-ttu-id="ecf81-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableRowEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ecf81-108">특성</span><span class="sxs-lookup"><span data-stu-id="ecf81-108">Attributes</span></span>

<span data-ttu-id="ecf81-109">없음</span><span class="sxs-lookup"><span data-stu-id="ecf81-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ecf81-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-110">Child Elements</span></span>

|<span data-ttu-id="ecf81-111">요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-111">Element</span></span>|<span data-ttu-id="ecf81-112">설명</span><span class="sxs-lookup"><span data-stu-id="ecf81-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecf81-113">TableControl (형식)에 대 한 TableRowEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ecf81-114">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-114">Required element.</span></span><br /><br /> <span data-ttu-id="ecf81-115">속성 값은 행에 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="ecf81-116">TableControl (형식)에 대 한 TableRowEntry TableColumnItems 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ecf81-117">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-117">Required element.</span></span><br /><br /> <span data-ttu-id="ecf81-118">속성 또는 값을 표시 하는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="ecf81-119">TableControl (형식)에 대 한 TableRowEntry 하기 위해 요소를 래핑</span><span class="sxs-lookup"><span data-stu-id="ecf81-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ecf81-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ecf81-121">지정 된 열 너비를 초과 하는 텍스트가 다음 줄에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ecf81-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-122">Parent Elements</span></span>

|<span data-ttu-id="ecf81-123">요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-123">Element</span></span>|<span data-ttu-id="ecf81-124">설명</span><span class="sxs-lookup"><span data-stu-id="ecf81-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecf81-125">TableControl (형식)에 대 한 TableRowEntries 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="ecf81-126">테이블의 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ecf81-127">설명</span><span class="sxs-lookup"><span data-stu-id="ecf81-127">Remarks</span></span>

<span data-ttu-id="ecf81-128">하나의 `TableColumnItems` 요소와 `EntrySelectedBy` 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="ecf81-129">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ecf81-130">예제</span><span class="sxs-lookup"><span data-stu-id="ecf81-130">Example</span></span>

<span data-ttu-id="ecf81-131">에서는 다음 예제는 `TableRowEntry` 의 두 속성의 값을 표시 하는 행을 정의 하는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ecf81-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ecf81-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ecf81-132">See Also</span></span>

[<span data-ttu-id="ecf81-133">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="ecf81-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ecf81-134">TableControl (형식)에 대 한 TableRowEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ecf81-135">TableControl (형식)에 대 한 TableRowEntry TableColumnItems 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ecf81-136">TableControl (형식)에 대 한 TableRowEntries 요소</span><span class="sxs-lookup"><span data-stu-id="ecf81-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="ecf81-137">TableControl (형식)에 대 한 TableRowEntry 하기 위해 요소를 래핑</span><span class="sxs-lookup"><span data-stu-id="ecf81-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ecf81-138">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="ecf81-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
