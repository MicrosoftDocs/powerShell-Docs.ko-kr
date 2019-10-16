---
title: TableControl (형식)의 TableColumnItem에 대 한 Alignment 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369082"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="3a5d6-102">TableControl의 TableColumnItem에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3a5d6-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="3a5d6-103">행의 열에 있는 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="3a5d6-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) TableColumnItems Element (format) TableColumnItem 요소 (format) TableColumnItem에 대 한 Alignment 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3a5d6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a5d6-105">구문</span><span class="sxs-lookup"><span data-stu-id="3a5d6-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a5d6-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3a5d6-106">Attributes and Elements</span></span>

<span data-ttu-id="3a5d6-107">다음 섹션에서는 `Alignment` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a5d6-108">특성</span><span class="sxs-lookup"><span data-stu-id="3a5d6-108">Attributes</span></span>

<span data-ttu-id="3a5d6-109">없음</span><span class="sxs-lookup"><span data-stu-id="3a5d6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a5d6-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3a5d6-110">Child Elements</span></span>

<span data-ttu-id="3a5d6-111">없음</span><span class="sxs-lookup"><span data-stu-id="3a5d6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3a5d6-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3a5d6-112">Parent Elements</span></span>

|<span data-ttu-id="3a5d6-113">요소</span><span class="sxs-lookup"><span data-stu-id="3a5d6-113">Element</span></span>|<span data-ttu-id="3a5d6-114">설명</span><span class="sxs-lookup"><span data-stu-id="3a5d6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a5d6-115">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3a5d6-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="3a5d6-116">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3a5d6-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="3a5d6-117">Text Value</span></span>

<span data-ttu-id="3a5d6-118">다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-118">Specify one of the following values.</span></span> <span data-ttu-id="3a5d6-119">이러한 값은 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="3a5d6-120">왼쪽에 열에 표시 된 데이터를 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="3a5d6-121">이 요소를 지정 하지 않은 경우에는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="3a5d6-122">열에 표시 되는 데이터를 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="3a5d6-123">가운데 열에 표시 되는 데이터를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a5d6-124">설명</span><span class="sxs-lookup"><span data-stu-id="3a5d6-124">Remarks</span></span>

<span data-ttu-id="3a5d6-125">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a5d6-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a5d6-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a5d6-126">See Also</span></span>

[<span data-ttu-id="3a5d6-127">테이블 보기</span><span class="sxs-lookup"><span data-stu-id="3a5d6-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3a5d6-128">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3a5d6-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
