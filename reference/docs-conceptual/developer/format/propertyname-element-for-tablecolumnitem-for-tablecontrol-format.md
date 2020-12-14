---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)
description: TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)
ms.openlocfilehash: e83bbdb96d2755013cb9fe065cb98731ba44917f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665586"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="4a1b3-103">TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a1b3-103">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="4a1b3-104">행의 열에 값이 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1b3-104">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="4a1b3-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl element (format) TableRowEntries element (format) TableRowEntry element (format) TableColumnItems element (format) TableColumnItem element (format) PropertyName Element for TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4a1b3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a1b3-106">구문</span><span class="sxs-lookup"><span data-stu-id="4a1b3-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a1b3-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4a1b3-107">Attributes and Elements</span></span>

<span data-ttu-id="4a1b3-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="4a1b3-108">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a1b3-109">특성</span><span class="sxs-lookup"><span data-stu-id="4a1b3-109">Attributes</span></span>

<span data-ttu-id="4a1b3-110">없음</span><span class="sxs-lookup"><span data-stu-id="4a1b3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a1b3-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4a1b3-111">Child Elements</span></span>

<span data-ttu-id="4a1b3-112">없음</span><span class="sxs-lookup"><span data-stu-id="4a1b3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a1b3-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4a1b3-113">Parent Elements</span></span>

|<span data-ttu-id="4a1b3-114">요소</span><span class="sxs-lookup"><span data-stu-id="4a1b3-114">Element</span></span>|<span data-ttu-id="4a1b3-115">설명</span><span class="sxs-lookup"><span data-stu-id="4a1b3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a1b3-116">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="4a1b3-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="4a1b3-117">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1b3-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4a1b3-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4a1b3-118">Text Value</span></span>

<span data-ttu-id="4a1b3-119">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1b3-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a1b3-120">설명</span><span class="sxs-lookup"><span data-stu-id="4a1b3-120">Remarks</span></span>

<span data-ttu-id="4a1b3-121">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4a1b3-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4a1b3-122">예제</span><span class="sxs-lookup"><span data-stu-id="4a1b3-122">Example</span></span>

<span data-ttu-id="4a1b3-123">이 예제에서는 `TableColumnItem` `Status` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 지정 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4a1b3-123">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="4a1b3-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a1b3-124">See Also</span></span>

[<span data-ttu-id="4a1b3-125">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="4a1b3-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4a1b3-126">TableColumnItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="4a1b3-126">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="4a1b3-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4a1b3-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
