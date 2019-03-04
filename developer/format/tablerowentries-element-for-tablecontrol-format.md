---
title: TableControl (형식)에 대 한 TableRowEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862189"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="9c52a-102">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c52a-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="9c52a-103">테이블의 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-103">Defines the rows of the table.</span></span>

<span data-ttu-id="9c52a-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="9c52a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c52a-105">구문</span><span class="sxs-lookup"><span data-stu-id="9c52a-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c52a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9c52a-106">Attributes and Elements</span></span>

<span data-ttu-id="9c52a-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableRowEntries` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c52a-108">특성</span><span class="sxs-lookup"><span data-stu-id="9c52a-108">Attributes</span></span>

<span data-ttu-id="9c52a-109">없음</span><span class="sxs-lookup"><span data-stu-id="9c52a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c52a-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9c52a-110">Child Elements</span></span>

|<span data-ttu-id="9c52a-111">요소</span><span class="sxs-lookup"><span data-stu-id="9c52a-111">Element</span></span>|<span data-ttu-id="9c52a-112">설명</span><span class="sxs-lookup"><span data-stu-id="9c52a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c52a-113">TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소</span><span class="sxs-lookup"><span data-stu-id="9c52a-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="9c52a-114">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-114">Required element.</span></span><br /><br /> <span data-ttu-id="9c52a-115">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9c52a-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9c52a-116">Parent Elements</span></span>

|<span data-ttu-id="9c52a-117">요소</span><span class="sxs-lookup"><span data-stu-id="9c52a-117">Element</span></span>|<span data-ttu-id="9c52a-118">설명</span><span class="sxs-lookup"><span data-stu-id="9c52a-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c52a-119">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9c52a-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="9c52a-120">보기에 대 한 테이블 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c52a-121">설명</span><span class="sxs-lookup"><span data-stu-id="9c52a-121">Remarks</span></span>

<span data-ttu-id="9c52a-122">하나 이상 지정 해야 `TableRowEntry` 테이블 보기에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="9c52a-123">수의 최대 제한은 없습니다 `TableRowEntry` 추가할 수 있는 요소와 순서는 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="9c52a-124">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9c52a-125">예제</span><span class="sxs-lookup"><span data-stu-id="9c52a-125">Example</span></span>

<span data-ttu-id="9c52a-126">에서는 다음 예제는 `TableRowEntries` 의 두 속성의 값을 표시 하는 행을 정의 하는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="9c52a-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9c52a-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c52a-127">See Also</span></span>

[<span data-ttu-id="9c52a-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="9c52a-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9c52a-129">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9c52a-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="9c52a-130">TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9c52a-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="9c52a-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="9c52a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
