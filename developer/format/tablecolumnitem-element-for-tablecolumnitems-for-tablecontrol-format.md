---
title: TableControl (형식)에 대 한 TableColumnItems TableColumnItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063941"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="c9ba9-102">TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c9ba9-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="c9ba9-103">속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="c9ba9-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소 TableControl (형식)에 TableControl (형식)에 대 한 TableColumnItems TableColumnItem 요소 TableControl (형식)에 대 한 TableControlEntry TableColumnItems 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9ba9-105">구문</span><span class="sxs-lookup"><span data-stu-id="c9ba9-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9ba9-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-106">Attributes and Elements</span></span>

<span data-ttu-id="c9ba9-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableColumnItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9ba9-108">특성</span><span class="sxs-lookup"><span data-stu-id="c9ba9-108">Attributes</span></span>

<span data-ttu-id="c9ba9-109">없음</span><span class="sxs-lookup"><span data-stu-id="c9ba9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9ba9-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-110">Child Elements</span></span>

|<span data-ttu-id="c9ba9-111">요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-111">Element</span></span>|<span data-ttu-id="c9ba9-112">설명</span><span class="sxs-lookup"><span data-stu-id="c9ba9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9ba9-113">TableControl (형식)에 대 한 TableColumnItem 요소 맞춤</span><span class="sxs-lookup"><span data-stu-id="c9ba9-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c9ba9-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c9ba9-115">데이터 행의 열에 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="c9ba9-116">TableControl (형식)에 대 한 TableColumnItem FormatString 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c9ba9-117">행의 열에 데이터의 형식을 지정 하는 데 사용 되는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="c9ba9-118">TableControl (형식)에 대 한 TableColumnItem PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c9ba9-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c9ba9-120">값은 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="c9ba9-121">TableControl (형식)에 대 한 TableColumnItem ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c9ba9-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c9ba9-123">값을 갖는 행의 열에 표시 됩니다 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c9ba9-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-124">Parent Elements</span></span>

|<span data-ttu-id="c9ba9-125">요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-125">Element</span></span>|<span data-ttu-id="c9ba9-126">설명</span><span class="sxs-lookup"><span data-stu-id="c9ba9-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9ba9-127">TableControl (형식)에 대 한 TableControlEntry TableColumnItems 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="c9ba9-128">속성 또는 행의 값을 표시 하는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9ba9-129">설명</span><span class="sxs-lookup"><span data-stu-id="c9ba9-129">Remarks</span></span>

<span data-ttu-id="c9ba9-130">행의 각 열에는 개체 또는 스크립트의 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="c9ba9-131">지정 된 자식 요소가 없는 경우 항목 자리 표시자 이며 데이터가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="c9ba9-132">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c9ba9-133">예제</span><span class="sxs-lookup"><span data-stu-id="c9ba9-133">Example</span></span>

<span data-ttu-id="c9ba9-134">보여 주는이 예제는 `TableColumnItem` 값을 표시 하는 요소는 `Status` 의 속성을 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체.</span><span class="sxs-lookup"><span data-stu-id="c9ba9-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="c9ba9-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9ba9-135">See Also</span></span>

[<span data-ttu-id="c9ba9-136">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="c9ba9-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c9ba9-137">TableControl (형식)에 대 한 TableColumnItem 요소 맞춤</span><span class="sxs-lookup"><span data-stu-id="c9ba9-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c9ba9-138">TableColumnItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9ba9-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="c9ba9-139">TableControl (형식)에 대 한 TableColumnItem FormatString 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c9ba9-140">TableControl (형식)에 대 한 TableColumnItem PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c9ba9-141">TableControl (형식)에 대 한 TableColumnItem ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="c9ba9-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c9ba9-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="c9ba9-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
