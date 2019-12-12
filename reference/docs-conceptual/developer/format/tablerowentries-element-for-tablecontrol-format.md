---
title: TableControl에 대 한 TableRowEntries 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368152"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="1f9df-102">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1f9df-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="1f9df-103">테이블의 행을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-103">Defines the rows of the table.</span></span>

<span data-ttu-id="1f9df-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1f9df-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f9df-105">구문</span><span class="sxs-lookup"><span data-stu-id="1f9df-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f9df-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1f9df-106">Attributes and Elements</span></span>

<span data-ttu-id="1f9df-107">다음 섹션에서는 `TableRowEntries` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f9df-108">특성</span><span class="sxs-lookup"><span data-stu-id="1f9df-108">Attributes</span></span>

<span data-ttu-id="1f9df-109">없음</span><span class="sxs-lookup"><span data-stu-id="1f9df-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f9df-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1f9df-110">Child Elements</span></span>

|<span data-ttu-id="1f9df-111">요소</span><span class="sxs-lookup"><span data-stu-id="1f9df-111">Element</span></span>|<span data-ttu-id="1f9df-112">설명</span><span class="sxs-lookup"><span data-stu-id="1f9df-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f9df-113">TableControl의 TableRowEntries 요소에 대 한 TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1f9df-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="1f9df-114">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-114">Required element.</span></span><br /><br /> <span data-ttu-id="1f9df-115">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1f9df-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1f9df-116">Parent Elements</span></span>

|<span data-ttu-id="1f9df-117">요소</span><span class="sxs-lookup"><span data-stu-id="1f9df-117">Element</span></span>|<span data-ttu-id="1f9df-118">설명</span><span class="sxs-lookup"><span data-stu-id="1f9df-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f9df-119">TableControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1f9df-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="1f9df-120">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1f9df-121">설명</span><span class="sxs-lookup"><span data-stu-id="1f9df-121">Remarks</span></span>

<span data-ttu-id="1f9df-122">테이블 뷰에 대해 하나 이상의 `TableRowEntry` 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="1f9df-123">추가할 수 있는 `TableRowEntry` 요소 수에는 제한이 없으며 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="1f9df-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f9df-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1f9df-125">예제</span><span class="sxs-lookup"><span data-stu-id="1f9df-125">Example</span></span>

<span data-ttu-id="1f9df-126">다음 예에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 `TableRowEntries` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f9df-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1f9df-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f9df-127">See Also</span></span>

[<span data-ttu-id="1f9df-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="1f9df-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1f9df-129">TableControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1f9df-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="1f9df-130">TableRowEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1f9df-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="1f9df-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1f9df-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
