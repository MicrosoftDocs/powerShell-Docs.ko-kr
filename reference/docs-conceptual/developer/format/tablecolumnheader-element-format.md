---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnHeader 요소(형식)
description: TableColumnHeader 요소(형식)
ms.openlocfilehash: 30368512875b7c5c4cf3c686f3d09540dea1bd26
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651523"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="6081c-103">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6081c-103">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="6081c-104">테이블의 열에 대 한 레이블, 열의 너비 및 레이블의 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-104">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="6081c-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableHeaders 요소에 대 한 TableControl (format) TableColumnHeader 요소 (형식)의 tableheaders 요소</span><span class="sxs-lookup"><span data-stu-id="6081c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6081c-106">구문</span><span class="sxs-lookup"><span data-stu-id="6081c-106">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6081c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6081c-107">Attributes and Elements</span></span>

<span data-ttu-id="6081c-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TableColumnHeader` .</span><span class="sxs-lookup"><span data-stu-id="6081c-108">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6081c-109">특성</span><span class="sxs-lookup"><span data-stu-id="6081c-109">Attributes</span></span>

<span data-ttu-id="6081c-110">없음</span><span class="sxs-lookup"><span data-stu-id="6081c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6081c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6081c-111">Child Elements</span></span>

|<span data-ttu-id="6081c-112">요소</span><span class="sxs-lookup"><span data-stu-id="6081c-112">Element</span></span>|<span data-ttu-id="6081c-113">설명</span><span class="sxs-lookup"><span data-stu-id="6081c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6081c-114">TableControl (형식)의 TableColumnHeader에 대 한 Label 요소</span><span class="sxs-lookup"><span data-stu-id="6081c-114">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="6081c-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6081c-116">열 맨 위에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-116">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="6081c-117">레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-117">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="6081c-118">TableControl의 TableColumnHeader에 대한 Width 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6081c-118">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="6081c-119">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-119">Required element.</span></span><br /><br /> <span data-ttu-id="6081c-120">열의 너비 (문자)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-120">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="6081c-121">TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6081c-121">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="6081c-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6081c-123">열의 레이블을 표시 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-123">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="6081c-124">맞춤을 지정 하지 않으면 레이블은 왼쪽에 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-124">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6081c-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6081c-125">Parent Elements</span></span>

|<span data-ttu-id="6081c-126">요소</span><span class="sxs-lookup"><span data-stu-id="6081c-126">Element</span></span>|<span data-ttu-id="6081c-127">설명</span><span class="sxs-lookup"><span data-stu-id="6081c-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6081c-128">TableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6081c-128">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="6081c-129">테이블 뷰의 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-129">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6081c-130">설명</span><span class="sxs-lookup"><span data-stu-id="6081c-130">Remarks</span></span>

<span data-ttu-id="6081c-131">테이블의 각 열에 대 한 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-131">Specify a header for each column of the table.</span></span> <span data-ttu-id="6081c-132">열은 요소가 정의 된 순서 대로 표시 됩니다 `TableColumnHeader` .</span><span class="sxs-lookup"><span data-stu-id="6081c-132">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="6081c-133">테이블에는 요소와 동일한 수의 `TableColumnHeader` 요소가 있어야 합니다 `TableRowEntry` .</span><span class="sxs-lookup"><span data-stu-id="6081c-133">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="6081c-134">열 머리글은 테이블의 위쪽에 있는 텍스트가 표시 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-134">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="6081c-135">행 항목은 테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-135">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="6081c-136">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6081c-136">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6081c-137">예제</span><span class="sxs-lookup"><span data-stu-id="6081c-137">Example</span></span>

<span data-ttu-id="6081c-138">다음 예제에서는 두 개의 요소를 보여 줍니다 `TableColumnHeader` .</span><span class="sxs-lookup"><span data-stu-id="6081c-138">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="6081c-139">첫 번째 요소는 레이블이 "열 1"이 고 너비가 16 자인 열을 정의 하며 레이블은 왼쪽에 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-139">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="6081c-140">두 번째 요소는 레이블이 "열 2"이 고 너비는 10 자인 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6081c-140">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="6081c-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6081c-141">See Also</span></span>

[<span data-ttu-id="6081c-142">TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6081c-142">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="6081c-143">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="6081c-143">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6081c-144">TableControl의 TableColumnHeader에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6081c-144">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="6081c-145">TableControl (형식)의 TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="6081c-145">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="6081c-146">TableControl 요소에 대 한 TableColumnHeader의 너비 (형식)</span><span class="sxs-lookup"><span data-stu-id="6081c-146">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="6081c-147">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6081c-147">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
