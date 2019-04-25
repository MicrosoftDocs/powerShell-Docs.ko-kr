---
title: TableHeaders 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075412"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="67d04-102">TableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="67d04-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="67d04-103">테이블의 열에 대 한 헤더를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="67d04-104">TableControl (형식)에 대 한 ViewDefinitions 요소 (형식) 보기 요소 (형식) TableControl 요소 (형식) TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="67d04-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67d04-105">구문</span><span class="sxs-lookup"><span data-stu-id="67d04-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="67d04-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="67d04-106">Attributes and Elements</span></span>

<span data-ttu-id="67d04-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `TableHeaders` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="67d04-108">표시 되는 개체의 각 속성에 대 한 자식 요소 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="67d04-109">열 헤더 정보를 자식 요소에 지정 된 순서로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="67d04-110">특성</span><span class="sxs-lookup"><span data-stu-id="67d04-110">Attributes</span></span>

<span data-ttu-id="67d04-111">없음</span><span class="sxs-lookup"><span data-stu-id="67d04-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67d04-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="67d04-112">Child Elements</span></span>

|<span data-ttu-id="67d04-113">요소</span><span class="sxs-lookup"><span data-stu-id="67d04-113">Element</span></span>|<span data-ttu-id="67d04-114">설명</span><span class="sxs-lookup"><span data-stu-id="67d04-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67d04-115">TableColumnHeader 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="67d04-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="67d04-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-116">Optional element.</span></span><br /><br /> <span data-ttu-id="67d04-117">레이블, 너비 및 테이블 뷰의 열에 대 한 데이터의 맞춤을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67d04-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="67d04-118">Parent Elements</span></span>

|<span data-ttu-id="67d04-119">요소</span><span class="sxs-lookup"><span data-stu-id="67d04-119">Element</span></span>|<span data-ttu-id="67d04-120">설명</span><span class="sxs-lookup"><span data-stu-id="67d04-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67d04-121">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="67d04-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="67d04-122">보기에 대 한 테이블 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67d04-123">설명</span><span class="sxs-lookup"><span data-stu-id="67d04-123">Remarks</span></span>

<span data-ttu-id="67d04-124">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="67d04-125">예제</span><span class="sxs-lookup"><span data-stu-id="67d04-125">Example</span></span>

<span data-ttu-id="67d04-126">이 예제는 `TableHeaders` 두 열 헤더를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="67d04-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="67d04-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67d04-127">See Also</span></span>

[<span data-ttu-id="67d04-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="67d04-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="67d04-129">TableColumnHeader 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="67d04-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="67d04-130">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="67d04-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="67d04-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="67d04-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
