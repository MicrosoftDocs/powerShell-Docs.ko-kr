---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 요소(형식)
description: TableControl 요소(형식)
ms.openlocfilehash: 93e05e22d61504d7781b6f3c07f9a3fd0b3c9e8a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651462"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="5f431-103">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-103">TableControl Element (Format)</span></span>

<span data-ttu-id="5f431-104">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-104">Defines a table format for a view.</span></span>

<span data-ttu-id="5f431-105">ViewDefinitions 요소 (Format) View 요소 (format) TableControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5f431-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5f431-106">구문</span><span class="sxs-lookup"><span data-stu-id="5f431-106">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5f431-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5f431-107">Attributes and Elements</span></span>

<span data-ttu-id="5f431-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableControl` .</span><span class="sxs-lookup"><span data-stu-id="5f431-108">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="5f431-109">테이블의 행을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-109">You must specify the rows of the table.</span></span> <span data-ttu-id="5f431-110">다른 모든 자식 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-110">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="5f431-111">특성</span><span class="sxs-lookup"><span data-stu-id="5f431-111">Attributes</span></span>

<span data-ttu-id="5f431-112">없음</span><span class="sxs-lookup"><span data-stu-id="5f431-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5f431-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5f431-113">Child Elements</span></span>

|<span data-ttu-id="5f431-114">요소</span><span class="sxs-lookup"><span data-stu-id="5f431-114">Element</span></span>|<span data-ttu-id="5f431-115">설명</span><span class="sxs-lookup"><span data-stu-id="5f431-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f431-116">TableControl에 대한 AutoSize 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-116">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="5f431-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5f431-118">데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="5f431-119">TableControl에 대 한 HideTableHeaders 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-119">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="5f431-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5f431-121">테이블의 헤더가 표시 되지 않는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-121">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="5f431-122">TableControl (형식)의 TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="5f431-122">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="5f431-123">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-123">Required element.</span></span><br /><br /> <span data-ttu-id="5f431-124">테이블 뷰의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-124">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="5f431-125">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="5f431-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-126">Optional element.</span></span><br /><br /> <span data-ttu-id="5f431-127">테이블 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-127">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5f431-128">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5f431-128">Parent Elements</span></span>

|<span data-ttu-id="5f431-129">요소</span><span class="sxs-lookup"><span data-stu-id="5f431-129">Element</span></span>|<span data-ttu-id="5f431-130">설명</span><span class="sxs-lookup"><span data-stu-id="5f431-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5f431-131">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-131">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5f431-132">하나 이상의 개체 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-132">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f431-133">설명</span><span class="sxs-lookup"><span data-stu-id="5f431-133">Remarks</span></span>

<span data-ttu-id="5f431-134">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5f431-134">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5f431-135">예제</span><span class="sxs-lookup"><span data-stu-id="5f431-135">Example</span></span>

<span data-ttu-id="5f431-136">이 예제에서는 `TableControl` [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체의 속성을 표시 하는 데 사용 되는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f431-136">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="5f431-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f431-137">See Also</span></span>

[<span data-ttu-id="5f431-138">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="5f431-138">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5f431-139">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-139">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5f431-140">TableControl에 대한 AutoSize 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-140">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="5f431-141">HideTableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-141">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="5f431-142">TableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5f431-142">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="5f431-143">TableRowEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5f431-143">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="5f431-144">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5f431-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
