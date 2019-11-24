---
title: TableColumnHeader 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361852"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="8e2a7-102">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8e2a7-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="8e2a7-103">테이블의 열에 대 한 레이블, 열의 너비 및 레이블의 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="8e2a7-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableHeaders 요소에 대 한 TableControl (format) TableColumnHeader 요소 (형식)의 tableheaders 요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e2a7-105">구문</span><span class="sxs-lookup"><span data-stu-id="8e2a7-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e2a7-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-106">Attributes and Elements</span></span>

<span data-ttu-id="8e2a7-107">다음 섹션에서는 특성, 자식 요소 및 `TableColumnHeader` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e2a7-108">특성</span><span class="sxs-lookup"><span data-stu-id="8e2a7-108">Attributes</span></span>

<span data-ttu-id="8e2a7-109">없음</span><span class="sxs-lookup"><span data-stu-id="8e2a7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e2a7-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-110">Child Elements</span></span>

|<span data-ttu-id="8e2a7-111">요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-111">Element</span></span>|<span data-ttu-id="8e2a7-112">설명</span><span class="sxs-lookup"><span data-stu-id="8e2a7-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e2a7-113">TableControl (형식)의 TableColumnHeader에 대 한 Label 요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e2a7-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8e2a7-115">열 맨 위에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="8e2a7-116">레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="8e2a7-117">TableControl의 TableColumnHeader에 대 한 Width 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8e2a7-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e2a7-118">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-118">Required element.</span></span><br /><br /> <span data-ttu-id="8e2a7-119">열의 너비 (문자)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="8e2a7-120">TableControl에 대 한 TableColumnHeader의 Alignment 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8e2a7-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="8e2a7-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8e2a7-122">열의 레이블을 표시 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="8e2a7-123">맞춤을 지정 하지 않으면 레이블은 왼쪽에 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e2a7-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-124">Parent Elements</span></span>

|<span data-ttu-id="8e2a7-125">요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-125">Element</span></span>|<span data-ttu-id="8e2a7-126">설명</span><span class="sxs-lookup"><span data-stu-id="8e2a7-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e2a7-127">TableHeaders 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8e2a7-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="8e2a7-128">테이블 뷰의 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e2a7-129">설명</span><span class="sxs-lookup"><span data-stu-id="8e2a7-129">Remarks</span></span>

<span data-ttu-id="8e2a7-130">테이블의 각 열에 대 한 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="8e2a7-131">열은 `TableColumnHeader` 요소가 정의 된 순서 대로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="8e2a7-132">테이블에는 `TableRowEntry` 요소와 동일한 수의 `TableColumnHeader` 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="8e2a7-133">열 머리글은 테이블의 위쪽에 있는 텍스트가 표시 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="8e2a7-134">행 항목은 테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="8e2a7-135">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e2a7-136">예제</span><span class="sxs-lookup"><span data-stu-id="8e2a7-136">Example</span></span>

<span data-ttu-id="8e2a7-137">다음 예제에서는 두 개의 `TableColumnHeader` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="8e2a7-138">첫 번째 요소는 레이블이 "열 1"이 고 너비가 16 자인 열을 정의 하며 레이블은 왼쪽에 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="8e2a7-139">두 번째 요소는 레이블이 "열 2"이 고 너비는 10 자인 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2a7-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8e2a7-140">관련 항목</span><span class="sxs-lookup"><span data-stu-id="8e2a7-140">See Also</span></span>

[<span data-ttu-id="8e2a7-141">TableControl에 대 한 TableColumnHeader의 Alignment 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8e2a7-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e2a7-142">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="8e2a7-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8e2a7-143">TableControl (형식)의 TableColumnHeader에 대 한 Label 요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e2a7-144">TableControl (형식)의 TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="8e2a7-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="8e2a7-145">TableControl 요소에 대 한 TableColumnHeader의 너비 (형식)</span><span class="sxs-lookup"><span data-stu-id="8e2a7-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="8e2a7-146">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8e2a7-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
