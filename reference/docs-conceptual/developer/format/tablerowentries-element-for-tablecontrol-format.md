---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl에 대한 TableRowEntries 요소(형식)
description: TableControl에 대한 TableRowEntries 요소(형식)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651467"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="86a72-103">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86a72-103">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="86a72-104">테이블의 행을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a72-104">Defines the rows of the table.</span></span>

<span data-ttu-id="86a72-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="86a72-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86a72-106">구문</span><span class="sxs-lookup"><span data-stu-id="86a72-106">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86a72-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="86a72-107">Attributes and Elements</span></span>

<span data-ttu-id="86a72-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableRowEntries` .</span><span class="sxs-lookup"><span data-stu-id="86a72-108">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86a72-109">특성</span><span class="sxs-lookup"><span data-stu-id="86a72-109">Attributes</span></span>

<span data-ttu-id="86a72-110">없음</span><span class="sxs-lookup"><span data-stu-id="86a72-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86a72-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="86a72-111">Child Elements</span></span>

|<span data-ttu-id="86a72-112">요소</span><span class="sxs-lookup"><span data-stu-id="86a72-112">Element</span></span>|<span data-ttu-id="86a72-113">설명</span><span class="sxs-lookup"><span data-stu-id="86a72-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86a72-114">TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86a72-114">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="86a72-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="86a72-115">Required element.</span></span><br /><br /> <span data-ttu-id="86a72-116">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a72-116">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86a72-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="86a72-117">Parent Elements</span></span>

|<span data-ttu-id="86a72-118">요소</span><span class="sxs-lookup"><span data-stu-id="86a72-118">Element</span></span>|<span data-ttu-id="86a72-119">설명</span><span class="sxs-lookup"><span data-stu-id="86a72-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86a72-120">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86a72-120">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="86a72-121">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86a72-121">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86a72-122">설명</span><span class="sxs-lookup"><span data-stu-id="86a72-122">Remarks</span></span>

<span data-ttu-id="86a72-123">테이블 뷰에 대해 하나 이상의 요소를 지정 해야 합니다 `TableRowEntry` .</span><span class="sxs-lookup"><span data-stu-id="86a72-123">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="86a72-124">추가할 수 있는 요소 수에 대 한 최대 제한 `TableRowEntry` 또는 순서가 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86a72-124">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="86a72-125">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86a72-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="86a72-126">예제</span><span class="sxs-lookup"><span data-stu-id="86a72-126">Example</span></span>

<span data-ttu-id="86a72-127">다음 예제에서는 `TableRowEntries` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86a72-127">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="86a72-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86a72-128">See Also</span></span>

[<span data-ttu-id="86a72-129">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="86a72-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="86a72-130">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86a72-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="86a72-131">TableRowEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="86a72-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="86a72-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="86a72-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
