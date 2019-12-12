---
title: TableControl (형식)의 TableColumnHeader에 대 한 Alignment 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364382"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="fe425-102">TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fe425-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="fe425-103">열 머리글의 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="fe425-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableHeaders 요소 (format) TableColumnHeader Element (format) Alignment 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="fe425-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe425-105">구문</span><span class="sxs-lookup"><span data-stu-id="fe425-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe425-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fe425-106">Attributes and Elements</span></span>

<span data-ttu-id="fe425-107">다음 섹션에서는 `Alignment` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe425-108">특성</span><span class="sxs-lookup"><span data-stu-id="fe425-108">Attributes</span></span>

<span data-ttu-id="fe425-109">없음</span><span class="sxs-lookup"><span data-stu-id="fe425-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe425-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fe425-110">Child Elements</span></span>

<span data-ttu-id="fe425-111">없음</span><span class="sxs-lookup"><span data-stu-id="fe425-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe425-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fe425-112">Parent Elements</span></span>

|<span data-ttu-id="fe425-113">요소</span><span class="sxs-lookup"><span data-stu-id="fe425-113">Element</span></span>|<span data-ttu-id="fe425-114">설명</span><span class="sxs-lookup"><span data-stu-id="fe425-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe425-115">TableColumnHeader 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="fe425-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="fe425-116">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe425-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="fe425-117">Text Value</span></span>

<span data-ttu-id="fe425-118">다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-118">Specify one of the following values.</span></span> <span data-ttu-id="fe425-119">이러한 값은 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="fe425-120">왼쪽 열에 표시 되는 데이터를 왼쪽에 맞춥니다 .이 요소를 지정 하지 않은 경우에는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="fe425-121">오른쪽 열에 표시 되는 데이터를 오른쪽에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="fe425-122">가운데 열에 표시 되는 데이터를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe425-123">설명</span><span class="sxs-lookup"><span data-stu-id="fe425-123">Remarks</span></span>

<span data-ttu-id="fe425-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fe425-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fe425-125">예제</span><span class="sxs-lookup"><span data-stu-id="fe425-125">Example</span></span>

<span data-ttu-id="fe425-126">이 예제에서는 데이터가 왼쪽에 정렬 된 `TableColumnHeader` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe425-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="fe425-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe425-127">See Also</span></span>

[<span data-ttu-id="fe425-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="fe425-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="fe425-129">TableColumnHeader 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="fe425-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="fe425-130">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fe425-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
