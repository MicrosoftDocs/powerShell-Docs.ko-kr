---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)
description: TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)
ms.openlocfilehash: 8ef5158c9bb9f074d5c58190d4d3b20c10c83744
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659859"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="693d5-103">TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-103">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="693d5-104">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-104">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="693d5-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format) TableControl Element (format) TableRowEntries Element for TableRowEntries (format) TableControl 요소 for TableColumnItems for TableControlEntry (format) TableControl element for TableColumnItem for TableColumnItems (Format)</span><span class="sxs-lookup"><span data-stu-id="693d5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="693d5-106">구문</span><span class="sxs-lookup"><span data-stu-id="693d5-106">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="693d5-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="693d5-107">Attributes and Elements</span></span>

<span data-ttu-id="693d5-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableColumnItem` .</span><span class="sxs-lookup"><span data-stu-id="693d5-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="693d5-109">특성</span><span class="sxs-lookup"><span data-stu-id="693d5-109">Attributes</span></span>

<span data-ttu-id="693d5-110">없음</span><span class="sxs-lookup"><span data-stu-id="693d5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="693d5-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="693d5-111">Child Elements</span></span>

|<span data-ttu-id="693d5-112">요소</span><span class="sxs-lookup"><span data-stu-id="693d5-112">Element</span></span>|<span data-ttu-id="693d5-113">설명</span><span class="sxs-lookup"><span data-stu-id="693d5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="693d5-114">TableControl의 TableColumnItem에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-114">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="693d5-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="693d5-116">행의 열에 있는 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-116">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="693d5-117">TableControl의 TableColumnItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-117">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="693d5-118">행의 열에 있는 데이터의 서식을 지정 하는 데 사용 되는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-118">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="693d5-119">TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-119">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="693d5-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="693d5-121">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-121">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="693d5-122">TableControl의 TableColumnItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-122">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="693d5-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="693d5-124">행의 열에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-124">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="693d5-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="693d5-125">Parent Elements</span></span>

|<span data-ttu-id="693d5-126">요소</span><span class="sxs-lookup"><span data-stu-id="693d5-126">Element</span></span>|<span data-ttu-id="693d5-127">설명</span><span class="sxs-lookup"><span data-stu-id="693d5-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="693d5-128">TableControl의 TableControlEntry 요소에 대 한 TableColumnItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-128">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="693d5-129">행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-129">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="693d5-130">설명</span><span class="sxs-lookup"><span data-stu-id="693d5-130">Remarks</span></span>

<span data-ttu-id="693d5-131">행의 각 열에 개체 또는 스크립트의 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-131">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="693d5-132">자식 요소가 지정 되지 않은 경우 해당 항목은 자리 표시자 이며 데이터는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-132">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="693d5-133">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="693d5-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="693d5-134">예제</span><span class="sxs-lookup"><span data-stu-id="693d5-134">Example</span></span>

<span data-ttu-id="693d5-135">이 예제에서는 `TableColumnItem` `Status` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성 값을 표시 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="693d5-135">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="693d5-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="693d5-136">See Also</span></span>

[<span data-ttu-id="693d5-137">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="693d5-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="693d5-138">TableControl의 TableColumnItem에 대한 Alignment 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-138">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="693d5-139">TableColumnItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="693d5-139">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="693d5-140">TableControl의 TableColumnItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-140">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="693d5-141">TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-141">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="693d5-142">TableControl의 TableColumnItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="693d5-142">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="693d5-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="693d5-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
