---
title: TableHeaders 요소 (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b3176cbe1316d5b30cb61831d9915a80389709a5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787430"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="4c1b7-102">TableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4c1b7-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="4c1b7-103">테이블의 열에 대 한 헤더를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="4c1b7-104">ViewDefinitions 요소 (Format) View 요소 (format) TableControl Element (format) TableHeaders 요소 TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="4c1b7-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c1b7-105">구문</span><span class="sxs-lookup"><span data-stu-id="4c1b7-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c1b7-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4c1b7-106">Attributes and Elements</span></span>

<span data-ttu-id="4c1b7-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableHeaders` .</span><span class="sxs-lookup"><span data-stu-id="4c1b7-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="4c1b7-108">표시 될 개체의 각 속성에 대 한 자식 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="4c1b7-109">열 머리글 정보는 자식 요소가 지정 된 순서 대로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c1b7-110">특성</span><span class="sxs-lookup"><span data-stu-id="4c1b7-110">Attributes</span></span>

<span data-ttu-id="4c1b7-111">없음</span><span class="sxs-lookup"><span data-stu-id="4c1b7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c1b7-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4c1b7-112">Child Elements</span></span>

|<span data-ttu-id="4c1b7-113">요소</span><span class="sxs-lookup"><span data-stu-id="4c1b7-113">Element</span></span>|<span data-ttu-id="4c1b7-114">설명</span><span class="sxs-lookup"><span data-stu-id="4c1b7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c1b7-115">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4c1b7-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="4c1b7-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4c1b7-117">테이블 뷰의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4c1b7-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4c1b7-118">Parent Elements</span></span>

|<span data-ttu-id="4c1b7-119">요소</span><span class="sxs-lookup"><span data-stu-id="4c1b7-119">Element</span></span>|<span data-ttu-id="4c1b7-120">설명</span><span class="sxs-lookup"><span data-stu-id="4c1b7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c1b7-121">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4c1b7-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="4c1b7-122">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4c1b7-123">설명</span><span class="sxs-lookup"><span data-stu-id="4c1b7-123">Remarks</span></span>

<span data-ttu-id="4c1b7-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4c1b7-125">예제</span><span class="sxs-lookup"><span data-stu-id="4c1b7-125">Example</span></span>

<span data-ttu-id="4c1b7-126">이 예제에서는 `TableHeaders` 두 개의 열 머리글을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4c1b7-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4c1b7-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c1b7-127">See Also</span></span>

[<span data-ttu-id="4c1b7-128">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="4c1b7-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4c1b7-129">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4c1b7-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="4c1b7-130">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4c1b7-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="4c1b7-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4c1b7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
