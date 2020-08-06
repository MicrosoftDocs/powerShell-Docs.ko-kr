---
title: TableControl (형식)의 TableColumnHeader에 대 한 Label 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b7b1d6825d3bca0e36b230415d19c2ac48377a46
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785747"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="609c5-102">TableControl의 TableColumnHeader에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="609c5-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="609c5-103">열 맨 위에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="609c5-104">이 요소는 테이블 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="609c5-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableControl (format)의 tableheaders 요소에 대 한 TableColumnHeader 요소에 대 한 TableControl (format) Label 요소 for TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="609c5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="609c5-106">구문</span><span class="sxs-lookup"><span data-stu-id="609c5-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="609c5-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="609c5-107">Attributes and Elements</span></span>

<span data-ttu-id="609c5-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Label` .</span><span class="sxs-lookup"><span data-stu-id="609c5-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="609c5-109">각 열에는 하나의 레이블만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="609c5-110">특성</span><span class="sxs-lookup"><span data-stu-id="609c5-110">Attributes</span></span>

<span data-ttu-id="609c5-111">없음</span><span class="sxs-lookup"><span data-stu-id="609c5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="609c5-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="609c5-112">Child Elements</span></span>

<span data-ttu-id="609c5-113">없음</span><span class="sxs-lookup"><span data-stu-id="609c5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="609c5-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="609c5-114">Parent Elements</span></span>

|<span data-ttu-id="609c5-115">요소</span><span class="sxs-lookup"><span data-stu-id="609c5-115">Element</span></span>|<span data-ttu-id="609c5-116">설명</span><span class="sxs-lookup"><span data-stu-id="609c5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="609c5-117">TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소</span><span class="sxs-lookup"><span data-stu-id="609c5-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="609c5-118">테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="609c5-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="609c5-119">Text Value</span></span>

<span data-ttu-id="609c5-120">테이블의 열 맨 위에 표시 되는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="609c5-121">열 레이블에 대해 제한 된 문자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="609c5-122">설명</span><span class="sxs-lookup"><span data-stu-id="609c5-122">Remarks</span></span>

<span data-ttu-id="609c5-123">레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="609c5-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="609c5-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="609c5-125">예제</span><span class="sxs-lookup"><span data-stu-id="609c5-125">Example</span></span>

<span data-ttu-id="609c5-126">이 예에서는 `TableColumnHeader` 레이블이 "열 1" 인 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="609c5-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="609c5-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="609c5-127">See Also</span></span>

[<span data-ttu-id="609c5-128">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="609c5-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="609c5-129">TableColumnHeader 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="609c5-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="609c5-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="609c5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
