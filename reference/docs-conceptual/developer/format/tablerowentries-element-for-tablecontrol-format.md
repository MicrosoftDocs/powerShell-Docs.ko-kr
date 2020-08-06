---
title: TableControl에 대 한 TableRowEntries 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4cc5d354df3e552e181a95148caa020f0041db92
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785118"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="b4606-102">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4606-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="b4606-103">테이블의 행을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4606-103">Defines the rows of the table.</span></span>

<span data-ttu-id="b4606-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b4606-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4606-105">구문</span><span class="sxs-lookup"><span data-stu-id="b4606-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4606-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b4606-106">Attributes and Elements</span></span>

<span data-ttu-id="b4606-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableRowEntries` .</span><span class="sxs-lookup"><span data-stu-id="b4606-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4606-108">특성</span><span class="sxs-lookup"><span data-stu-id="b4606-108">Attributes</span></span>

<span data-ttu-id="b4606-109">없음</span><span class="sxs-lookup"><span data-stu-id="b4606-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4606-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b4606-110">Child Elements</span></span>

|<span data-ttu-id="b4606-111">요소</span><span class="sxs-lookup"><span data-stu-id="b4606-111">Element</span></span>|<span data-ttu-id="b4606-112">설명</span><span class="sxs-lookup"><span data-stu-id="b4606-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4606-113">TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4606-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="b4606-114">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4606-114">Required element.</span></span><br /><br /> <span data-ttu-id="b4606-115">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4606-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4606-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b4606-116">Parent Elements</span></span>

|<span data-ttu-id="b4606-117">요소</span><span class="sxs-lookup"><span data-stu-id="b4606-117">Element</span></span>|<span data-ttu-id="b4606-118">설명</span><span class="sxs-lookup"><span data-stu-id="b4606-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4606-119">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4606-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="b4606-120">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4606-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4606-121">설명</span><span class="sxs-lookup"><span data-stu-id="b4606-121">Remarks</span></span>

<span data-ttu-id="b4606-122">테이블 뷰에 대해 하나 이상의 요소를 지정 해야 합니다 `TableRowEntry` .</span><span class="sxs-lookup"><span data-stu-id="b4606-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="b4606-123">추가할 수 있는 요소 수에 대 한 최대 제한 `TableRowEntry` 또는 순서가 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4606-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="b4606-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4606-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4606-125">예제</span><span class="sxs-lookup"><span data-stu-id="b4606-125">Example</span></span>

<span data-ttu-id="b4606-126">다음 예제에서는 `TableRowEntries` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4606-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4606-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4606-127">See Also</span></span>

[<span data-ttu-id="b4606-128">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="b4606-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b4606-129">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4606-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="b4606-130">TableRowEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b4606-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="b4606-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b4606-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
