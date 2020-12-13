---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnHeader에 대한 Label 요소(형식)
description: TableControl의 TableColumnHeader에 대한 Label 요소(형식)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667796"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="ad937-103">TableControl의 TableColumnHeader에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ad937-103">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="ad937-104">열 맨 위에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-104">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="ad937-105">이 요소는 테이블 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-105">This element is used when defining a table view.</span></span>

<span data-ttu-id="ad937-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableControl (format)의 tableheaders 요소에 대 한 TableColumnHeader 요소에 대 한 TableControl (format) Label 요소 for TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="ad937-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad937-107">구문</span><span class="sxs-lookup"><span data-stu-id="ad937-107">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad937-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ad937-108">Attributes and Elements</span></span>

<span data-ttu-id="ad937-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Label` .</span><span class="sxs-lookup"><span data-stu-id="ad937-109">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="ad937-110">각 열에는 하나의 레이블만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-110">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad937-111">특성</span><span class="sxs-lookup"><span data-stu-id="ad937-111">Attributes</span></span>

<span data-ttu-id="ad937-112">없음</span><span class="sxs-lookup"><span data-stu-id="ad937-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad937-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ad937-113">Child Elements</span></span>

<span data-ttu-id="ad937-114">없음</span><span class="sxs-lookup"><span data-stu-id="ad937-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad937-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ad937-115">Parent Elements</span></span>

|<span data-ttu-id="ad937-116">요소</span><span class="sxs-lookup"><span data-stu-id="ad937-116">Element</span></span>|<span data-ttu-id="ad937-117">설명</span><span class="sxs-lookup"><span data-stu-id="ad937-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad937-118">TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소</span><span class="sxs-lookup"><span data-stu-id="ad937-118">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="ad937-119">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-119">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ad937-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ad937-120">Text Value</span></span>

<span data-ttu-id="ad937-121">테이블의 열 맨 위에 표시 되는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-121">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="ad937-122">열 레이블에 대해 제한 된 문자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-122">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad937-123">설명</span><span class="sxs-lookup"><span data-stu-id="ad937-123">Remarks</span></span>

<span data-ttu-id="ad937-124">레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-124">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="ad937-125">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad937-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ad937-126">예제</span><span class="sxs-lookup"><span data-stu-id="ad937-126">Example</span></span>

<span data-ttu-id="ad937-127">이 예에서는 `TableColumnHeader` 레이블이 "열 1" 인 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad937-127">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="ad937-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad937-128">See Also</span></span>

[<span data-ttu-id="ad937-129">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ad937-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ad937-130">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ad937-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="ad937-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ad937-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
