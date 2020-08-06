---
title: TableColumnHeader 요소 (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6296aea5c567663b1c3c0a2cf0a57b21aa5394de
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785186"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="42bc9-102">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42bc9-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="42bc9-103">테이블의 열에 대 한 레이블, 열의 너비 및 레이블의 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="42bc9-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableHeaders 요소에 대 한 TableControl (format) TableColumnHeader 요소 (형식)의 tableheaders 요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42bc9-105">구문</span><span class="sxs-lookup"><span data-stu-id="42bc9-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42bc9-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-106">Attributes and Elements</span></span>

<span data-ttu-id="42bc9-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TableColumnHeader` .</span><span class="sxs-lookup"><span data-stu-id="42bc9-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42bc9-108">특성</span><span class="sxs-lookup"><span data-stu-id="42bc9-108">Attributes</span></span>

<span data-ttu-id="42bc9-109">없음</span><span class="sxs-lookup"><span data-stu-id="42bc9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42bc9-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-110">Child Elements</span></span>

|<span data-ttu-id="42bc9-111">요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-111">Element</span></span>|<span data-ttu-id="42bc9-112">설명</span><span class="sxs-lookup"><span data-stu-id="42bc9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42bc9-113">TableControl (형식)의 TableColumnHeader에 대 한 Label 요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="42bc9-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="42bc9-115">열 맨 위에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="42bc9-116">레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="42bc9-117">TableControl의 TableColumnHeader에 대한 Width 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42bc9-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="42bc9-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-118">Required element.</span></span><br /><br /> <span data-ttu-id="42bc9-119">열의 너비 (문자)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="42bc9-120">TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42bc9-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="42bc9-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="42bc9-122">열의 레이블을 표시 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="42bc9-123">맞춤을 지정 하지 않으면 레이블은 왼쪽에 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="42bc9-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-124">Parent Elements</span></span>

|<span data-ttu-id="42bc9-125">요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-125">Element</span></span>|<span data-ttu-id="42bc9-126">설명</span><span class="sxs-lookup"><span data-stu-id="42bc9-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42bc9-127">TableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42bc9-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="42bc9-128">테이블 뷰의 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="42bc9-129">설명</span><span class="sxs-lookup"><span data-stu-id="42bc9-129">Remarks</span></span>

<span data-ttu-id="42bc9-130">테이블의 각 열에 대 한 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="42bc9-131">열은 요소가 정의 된 순서 대로 표시 됩니다 `TableColumnHeader` .</span><span class="sxs-lookup"><span data-stu-id="42bc9-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="42bc9-132">테이블에는 요소와 동일한 수의 `TableColumnHeader` 요소가 있어야 합니다 `TableRowEntry` .</span><span class="sxs-lookup"><span data-stu-id="42bc9-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="42bc9-133">열 머리글은 테이블의 위쪽에 있는 텍스트가 표시 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="42bc9-134">행 항목은 테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="42bc9-135">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42bc9-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="42bc9-136">예제</span><span class="sxs-lookup"><span data-stu-id="42bc9-136">Example</span></span>

<span data-ttu-id="42bc9-137">다음 예제에서는 두 개의 요소를 보여 줍니다 `TableColumnHeader` .</span><span class="sxs-lookup"><span data-stu-id="42bc9-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="42bc9-138">첫 번째 요소는 레이블이 "열 1"이 고 너비가 16 자인 열을 정의 하며 레이블은 왼쪽에 정렬 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="42bc9-139">두 번째 요소는 레이블이 "열 2"이 고 너비는 10 자인 열을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42bc9-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="42bc9-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42bc9-140">See Also</span></span>

[<span data-ttu-id="42bc9-141">TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42bc9-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="42bc9-142">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="42bc9-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="42bc9-143">TableControl의 TableColumnHeader에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42bc9-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="42bc9-144">TableControl (형식)의 TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="42bc9-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="42bc9-145">TableControl 요소에 대 한 TableColumnHeader의 너비 (형식)</span><span class="sxs-lookup"><span data-stu-id="42bc9-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="42bc9-146">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="42bc9-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
