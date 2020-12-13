---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)
description: TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)
ms.openlocfilehash: cf8b90c12c28951283b5870186e2c88d427318a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666827"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="83153-103">TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="83153-103">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="83153-104">열 머리글의 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83153-104">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="83153-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableHeaders 요소 (format) TableColumnHeader Element (format) Alignment 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="83153-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83153-106">구문</span><span class="sxs-lookup"><span data-stu-id="83153-106">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83153-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="83153-107">Attributes and Elements</span></span>

<span data-ttu-id="83153-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Alignment` .</span><span class="sxs-lookup"><span data-stu-id="83153-108">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83153-109">특성</span><span class="sxs-lookup"><span data-stu-id="83153-109">Attributes</span></span>

<span data-ttu-id="83153-110">없음</span><span class="sxs-lookup"><span data-stu-id="83153-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83153-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="83153-111">Child Elements</span></span>

<span data-ttu-id="83153-112">없음</span><span class="sxs-lookup"><span data-stu-id="83153-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83153-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="83153-113">Parent Elements</span></span>

|<span data-ttu-id="83153-114">요소</span><span class="sxs-lookup"><span data-stu-id="83153-114">Element</span></span>|<span data-ttu-id="83153-115">설명</span><span class="sxs-lookup"><span data-stu-id="83153-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83153-116">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="83153-116">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="83153-117">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83153-117">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="83153-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="83153-118">Text Value</span></span>

<span data-ttu-id="83153-119">다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83153-119">Specify one of the following values.</span></span> <span data-ttu-id="83153-120">이러한 값은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83153-120">These values are not case-sensitive.</span></span>

<span data-ttu-id="83153-121">왼쪽 열에 표시 되는 데이터를 왼쪽에 맞춥니다 .이 요소를 지정 하지 않은 경우에는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="83153-121">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="83153-122">오른쪽 열에 표시 되는 데이터를 오른쪽에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="83153-122">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="83153-123">가운데 열에 표시 되는 데이터를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="83153-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="83153-124">설명</span><span class="sxs-lookup"><span data-stu-id="83153-124">Remarks</span></span>

<span data-ttu-id="83153-125">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83153-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="83153-126">예제</span><span class="sxs-lookup"><span data-stu-id="83153-126">Example</span></span>

<span data-ttu-id="83153-127">이 예제에서는 `TableColumnHeader` 데이터가 왼쪽에 정렬 된 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="83153-127">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="83153-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83153-128">See Also</span></span>

[<span data-ttu-id="83153-129">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="83153-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="83153-130">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="83153-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="83153-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="83153-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
