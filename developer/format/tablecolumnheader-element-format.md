---
title: TableColumnHeader 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057878"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="d4d6e-102">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d4d6e-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="d4d6e-103">레이블, 열 너비와 테이블의 열 레이블 맞춤을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="d4d6e-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableHeaders 요소 TableControl (형식)에 대 한 TableHeaders TableColumnHeader 요소 TableControl (형식)에</span><span class="sxs-lookup"><span data-stu-id="d4d6e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4d6e-105">구문</span><span class="sxs-lookup"><span data-stu-id="d4d6e-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4d6e-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-106">Attributes and Elements</span></span>

<span data-ttu-id="d4d6e-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableColumnHeader` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4d6e-108">특성</span><span class="sxs-lookup"><span data-stu-id="d4d6e-108">Attributes</span></span>

<span data-ttu-id="d4d6e-109">없음</span><span class="sxs-lookup"><span data-stu-id="d4d6e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4d6e-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-110">Child Elements</span></span>

|<span data-ttu-id="d4d6e-111">요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-111">Element</span></span>|<span data-ttu-id="d4d6e-112">설명</span><span class="sxs-lookup"><span data-stu-id="d4d6e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4d6e-113">TableControl (형식)에 대 한 TableColumnHeader 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d4d6e-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d4d6e-115">열의 맨 위에 있는 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="d4d6e-116">레이블이 없으면 지정 된 경우 값은 행에 표시 되는 속성의 이름을 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="d4d6e-117">TableControl (형식)에 대 한 TableColumnHeader 너비 요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d4d6e-118">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-118">Required element.</span></span><br /><br /> <span data-ttu-id="d4d6e-119">너비 (문자 단위) 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="d4d6e-120">TableControl (형식)에 대 한 TableColumnHeader 요소 맞춤</span><span class="sxs-lookup"><span data-stu-id="d4d6e-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="d4d6e-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d4d6e-122">열 레이블이 표시 되는 방식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="d4d6e-123">맞춤 없음이 지정 된 경우 레이블 왼쪽에 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d4d6e-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-124">Parent Elements</span></span>

|<span data-ttu-id="d4d6e-125">요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-125">Element</span></span>|<span data-ttu-id="d4d6e-126">설명</span><span class="sxs-lookup"><span data-stu-id="d4d6e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4d6e-127">TableHeaders 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d4d6e-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="d4d6e-128">테이블 보기의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d4d6e-129">설명</span><span class="sxs-lookup"><span data-stu-id="d4d6e-129">Remarks</span></span>

<span data-ttu-id="d4d6e-130">테이블의 각 열에 대 한 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="d4d6e-131">열이 나타나는 순서 대로 표시 됩니다는 `TableColumnHeader` 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="d4d6e-132">테이블에 동일한 수 있어야 합니다. `TableColumnHeader` 요소가 `TableRowEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="d4d6e-133">열 머리글을 테이블의 맨 위에 있는 텍스트를 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="d4d6e-134">행 항목을 테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="d4d6e-135">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d4d6e-136">예제</span><span class="sxs-lookup"><span data-stu-id="d4d6e-136">Example</span></span>

<span data-ttu-id="d4d6e-137">다음 예제에서는 두 개의 `TableColumnHeader` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="d4d6e-138">첫 번째 요소 레이블을 "열 1", 16 자 너비 및 해당 레이블 왼쪽에 맞춰집니다 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="d4d6e-139">두 번째 요소 레이블을 가운데 열에 있는 레이블 "열인지 2", 너비가 10 자 및 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d6e-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d4d6e-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4d6e-140">See Also</span></span>

[<span data-ttu-id="d4d6e-141">TableControl (형식)에 대 한 TableColumnHeader 요소 맞춤</span><span class="sxs-lookup"><span data-stu-id="d4d6e-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d4d6e-142">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="d4d6e-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d4d6e-143">TableControl (형식)에 대 한 TableColumnHeader 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d4d6e-144">TableControl (형식)에 대 한 TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="d4d6e-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="d4d6e-145">TableControl 요소 (형식)에 대 한 TableColumnHeader 너비</span><span class="sxs-lookup"><span data-stu-id="d4d6e-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="d4d6e-146">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="d4d6e-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
