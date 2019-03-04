---
title: TableControl (형식)에 대 한 TableRowEntry TableColumnItems 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859449"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="428f3-102">TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="428f3-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="428f3-103">속성 또는 행의 값을 표시 하는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="428f3-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소 TableControl (형식)에 TableControl (형식)에 대 한 TableControlEntry TableColumnItems 요소</span><span class="sxs-lookup"><span data-stu-id="428f3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="428f3-105">구문</span><span class="sxs-lookup"><span data-stu-id="428f3-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="428f3-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="428f3-106">Attributes and Elements</span></span>

<span data-ttu-id="428f3-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableColumnItems` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="428f3-108">특성</span><span class="sxs-lookup"><span data-stu-id="428f3-108">Attributes</span></span>

<span data-ttu-id="428f3-109">없음</span><span class="sxs-lookup"><span data-stu-id="428f3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="428f3-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="428f3-110">Child Elements</span></span>

|<span data-ttu-id="428f3-111">요소</span><span class="sxs-lookup"><span data-stu-id="428f3-111">Element</span></span>|<span data-ttu-id="428f3-112">설명</span><span class="sxs-lookup"><span data-stu-id="428f3-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="428f3-113">TableControl (형식)에 대 한 TableColumnItems TableColumnItem 요소</span><span class="sxs-lookup"><span data-stu-id="428f3-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="428f3-114">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-114">Required element.</span></span><br /><br /> <span data-ttu-id="428f3-115">속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="428f3-116">부모 요소</span><span class="sxs-lookup"><span data-stu-id="428f3-116">Parent Elements</span></span>

|<span data-ttu-id="428f3-117">요소</span><span class="sxs-lookup"><span data-stu-id="428f3-117">Element</span></span>|<span data-ttu-id="428f3-118">설명</span><span class="sxs-lookup"><span data-stu-id="428f3-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="428f3-119">TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소</span><span class="sxs-lookup"><span data-stu-id="428f3-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="428f3-120">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="428f3-121">설명</span><span class="sxs-lookup"><span data-stu-id="428f3-121">Remarks</span></span>

<span data-ttu-id="428f3-122">`TableColumnItem` 요소는 행의 각 열에 대 한 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="428f3-123">첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="428f3-124">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="428f3-125">예제</span><span class="sxs-lookup"><span data-stu-id="428f3-125">Example</span></span>

<span data-ttu-id="428f3-126">에서는 다음 예제는 `TableColumnItems` 의 세 가지 속성을 정의 하는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="428f3-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="428f3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="428f3-127">See Also</span></span>

[<span data-ttu-id="428f3-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="428f3-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="428f3-129">TableColumnItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="428f3-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="428f3-130">TableRowEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="428f3-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="428f3-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="428f3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
