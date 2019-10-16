---
title: TableColumnItems의 TableControl 요소에 대 한 TableColumnItem 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368232"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="3ab42-102">TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="3ab42-103">행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="3ab42-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소에 대 한 TableControl (format) TableRowEntry Element for TableRowEntries (Format) TableColumnItems에 대 한 TableControlEntry for TableControl (Format) TableColumnItem 요소에 대 한 TableColumnItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ab42-105">구문</span><span class="sxs-lookup"><span data-stu-id="3ab42-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ab42-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3ab42-106">Attributes and Elements</span></span>

<span data-ttu-id="3ab42-107">다음 섹션에서는 `TableColumnItem` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ab42-108">특성</span><span class="sxs-lookup"><span data-stu-id="3ab42-108">Attributes</span></span>

<span data-ttu-id="3ab42-109">없음</span><span class="sxs-lookup"><span data-stu-id="3ab42-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ab42-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3ab42-110">Child Elements</span></span>

|<span data-ttu-id="3ab42-111">요소</span><span class="sxs-lookup"><span data-stu-id="3ab42-111">Element</span></span>|<span data-ttu-id="3ab42-112">설명</span><span class="sxs-lookup"><span data-stu-id="3ab42-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ab42-113">TableControl에 대 한 TableColumnItem의 Alignment 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3ab42-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="3ab42-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3ab42-115">행의 열에 있는 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="3ab42-116">TableControl의 TableColumnItem에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="3ab42-117">행의 열에 있는 데이터의 서식을 지정 하는 데 사용 되는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="3ab42-118">TableControl의 TableColumnItem에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="3ab42-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3ab42-120">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="3ab42-121">TableControl의 TableColumnItem에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="3ab42-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3ab42-123">행의 열에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ab42-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3ab42-124">Parent Elements</span></span>

|<span data-ttu-id="3ab42-125">요소</span><span class="sxs-lookup"><span data-stu-id="3ab42-125">Element</span></span>|<span data-ttu-id="3ab42-126">설명</span><span class="sxs-lookup"><span data-stu-id="3ab42-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ab42-127">TableControl의 TableControlEntry 요소에 대 한 TableColumnItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="3ab42-128">행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3ab42-129">설명</span><span class="sxs-lookup"><span data-stu-id="3ab42-129">Remarks</span></span>

<span data-ttu-id="3ab42-130">행의 각 열에 개체 또는 스크립트의 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="3ab42-131">자식 요소가 지정 되지 않은 경우 해당 항목은 자리 표시자 이며 데이터는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="3ab42-132">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3ab42-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3ab42-133">예제</span><span class="sxs-lookup"><span data-stu-id="3ab42-133">Example</span></span>

<span data-ttu-id="3ab42-134">이 예제에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 `Status` 속성 값을 표시 하는 `TableColumnItem` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ab42-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="3ab42-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ab42-135">See Also</span></span>

[<span data-ttu-id="3ab42-136">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="3ab42-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3ab42-137">TableControl에 대 한 TableColumnItem의 Alignment 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3ab42-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="3ab42-138">TableColumnItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3ab42-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="3ab42-139">TableControl의 TableColumnItem에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="3ab42-140">TableControl의 TableColumnItem에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="3ab42-141">TableControl의 TableColumnItem에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3ab42-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="3ab42-142">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3ab42-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
