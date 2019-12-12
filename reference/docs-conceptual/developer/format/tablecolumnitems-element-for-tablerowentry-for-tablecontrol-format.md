---
title: TableRowEntry의 TableControl 요소에 대 한 TableColumnItems 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361812"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="4f97c-102">TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4f97c-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="4f97c-103">값이 행에 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="4f97c-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소에 대 한 TableControl (format) TableRowEntry Element for TableRowEntries (Format) TableControl의 TableControlEntry 요소에 대 한 TableColumnItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4f97c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f97c-105">구문</span><span class="sxs-lookup"><span data-stu-id="4f97c-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f97c-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4f97c-106">Attributes and Elements</span></span>

<span data-ttu-id="4f97c-107">다음 섹션에서는 `TableColumnItems` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f97c-108">특성</span><span class="sxs-lookup"><span data-stu-id="4f97c-108">Attributes</span></span>

<span data-ttu-id="4f97c-109">없음</span><span class="sxs-lookup"><span data-stu-id="4f97c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f97c-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4f97c-110">Child Elements</span></span>

|<span data-ttu-id="4f97c-111">요소</span><span class="sxs-lookup"><span data-stu-id="4f97c-111">Element</span></span>|<span data-ttu-id="4f97c-112">설명</span><span class="sxs-lookup"><span data-stu-id="4f97c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f97c-113">TableControl의 TableColumnItems 요소에 대 한 TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4f97c-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="4f97c-114">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-114">Required element.</span></span><br /><br /> <span data-ttu-id="4f97c-115">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f97c-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4f97c-116">Parent Elements</span></span>

|<span data-ttu-id="4f97c-117">요소</span><span class="sxs-lookup"><span data-stu-id="4f97c-117">Element</span></span>|<span data-ttu-id="4f97c-118">설명</span><span class="sxs-lookup"><span data-stu-id="4f97c-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f97c-119">TableControl의 TableRowEntries 요소에 대 한 TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4f97c-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="4f97c-120">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f97c-121">설명</span><span class="sxs-lookup"><span data-stu-id="4f97c-121">Remarks</span></span>

<span data-ttu-id="4f97c-122">행의 각 열에 `TableColumnItem` 요소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="4f97c-123">첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="4f97c-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f97c-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4f97c-125">예제</span><span class="sxs-lookup"><span data-stu-id="4f97c-125">Example</span></span>

<span data-ttu-id="4f97c-126">다음 예제에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 세 가지 속성을 정의 하는 `TableColumnItems` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f97c-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="4f97c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f97c-127">See Also</span></span>

[<span data-ttu-id="4f97c-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="4f97c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4f97c-129">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="4f97c-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="4f97c-130">TableRowEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="4f97c-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="4f97c-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4f97c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
