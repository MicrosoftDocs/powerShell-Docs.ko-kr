---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnItem에 대한 Alignment 요소(형식)
description: TableControl의 TableColumnItem에 대한 Alignment 요소(형식)
ms.openlocfilehash: d2bb81ff894cad44e16212891faffd22ee627383
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646115"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="0a410-103">TableControl의 TableColumnItem에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0a410-103">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="0a410-104">행의 열에 있는 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-104">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="0a410-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl element (format) TableRowEntries element (format) TableRowEntry Element (format) TableColumnItems Element (format) TableColumnItem 요소 (format) Alignment 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="0a410-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a410-106">구문</span><span class="sxs-lookup"><span data-stu-id="0a410-106">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a410-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0a410-107">Attributes and Elements</span></span>

<span data-ttu-id="0a410-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Alignment` .</span><span class="sxs-lookup"><span data-stu-id="0a410-108">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a410-109">특성</span><span class="sxs-lookup"><span data-stu-id="0a410-109">Attributes</span></span>

<span data-ttu-id="0a410-110">없음</span><span class="sxs-lookup"><span data-stu-id="0a410-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a410-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0a410-111">Child Elements</span></span>

<span data-ttu-id="0a410-112">없음</span><span class="sxs-lookup"><span data-stu-id="0a410-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a410-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0a410-113">Parent Elements</span></span>

|<span data-ttu-id="0a410-114">요소</span><span class="sxs-lookup"><span data-stu-id="0a410-114">Element</span></span>|<span data-ttu-id="0a410-115">설명</span><span class="sxs-lookup"><span data-stu-id="0a410-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a410-116">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0a410-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="0a410-117">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-117">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0a410-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="0a410-118">Text Value</span></span>

<span data-ttu-id="0a410-119">다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-119">Specify one of the following values.</span></span> <span data-ttu-id="0a410-120">이러한 값은 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-120">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="0a410-121">왼쪽에 열에 표시 된 데이터를 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-121">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="0a410-122">이 요소를 지정 하지 않은 경우에는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-122">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="0a410-123">열에 표시 되는 데이터를 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-123">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="0a410-124">가운데 열에 표시 되는 데이터를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="0a410-124">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a410-125">설명</span><span class="sxs-lookup"><span data-stu-id="0a410-125">Remarks</span></span>

<span data-ttu-id="0a410-126">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a410-126">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a410-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a410-127">See Also</span></span>

[<span data-ttu-id="0a410-128">테이블 보기</span><span class="sxs-lookup"><span data-stu-id="0a410-128">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0a410-129">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0a410-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
