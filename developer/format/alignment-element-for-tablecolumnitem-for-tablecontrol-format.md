---
title: TableControl (형식)에 대 한 TableColumnItem에 대 한 맞춤 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858209"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="03eac-102">TableControl의 TableColumnItem에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="03eac-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="03eac-103">데이터 행의 열에 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="03eac-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) TableColumnItems 요소 (형식) TableColumnItem 요소 (형식) TableColumnItem (형식)에 대 한 맞춤 요소</span><span class="sxs-lookup"><span data-stu-id="03eac-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03eac-105">구문</span><span class="sxs-lookup"><span data-stu-id="03eac-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03eac-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="03eac-106">Attributes and Elements</span></span>

<span data-ttu-id="03eac-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Alignment` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="03eac-108">특성</span><span class="sxs-lookup"><span data-stu-id="03eac-108">Attributes</span></span>

<span data-ttu-id="03eac-109">없음</span><span class="sxs-lookup"><span data-stu-id="03eac-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="03eac-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="03eac-110">Child Elements</span></span>

<span data-ttu-id="03eac-111">없음</span><span class="sxs-lookup"><span data-stu-id="03eac-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03eac-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="03eac-112">Parent Elements</span></span>

|<span data-ttu-id="03eac-113">요소</span><span class="sxs-lookup"><span data-stu-id="03eac-113">Element</span></span>|<span data-ttu-id="03eac-114">설명</span><span class="sxs-lookup"><span data-stu-id="03eac-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03eac-115">TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="03eac-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="03eac-116">레이블, 너비 및 테이블의 열에 대 한 데이터의 맞춤을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="03eac-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="03eac-117">Text Value</span></span>

<span data-ttu-id="03eac-118">다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-118">Specify one of the following values.</span></span> <span data-ttu-id="03eac-119">(이 값은 대/소문자 구분 합니다.)</span><span class="sxs-lookup"><span data-stu-id="03eac-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="03eac-120">왼쪽된 시프트 왼쪽 열에 표시 되는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="03eac-121">(이 경우 기본이이 요소가 지정 되지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="03eac-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="03eac-122">오른쪽 시프트 오른쪽 열에 표시 되는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="03eac-123">열에 표시 되는 데이터 센터를 center입니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="03eac-124">설명</span><span class="sxs-lookup"><span data-stu-id="03eac-124">Remarks</span></span>

<span data-ttu-id="03eac-125">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="03eac-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03eac-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03eac-126">See Also</span></span>

[<span data-ttu-id="03eac-127">테이블 뷰</span><span class="sxs-lookup"><span data-stu-id="03eac-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="03eac-128">TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="03eac-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
