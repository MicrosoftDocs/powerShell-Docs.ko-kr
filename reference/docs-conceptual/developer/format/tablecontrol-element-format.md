---
title: TableControl 요소 (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 34e20006a7501650f2a22f71a3d7e999fb8b2337
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785135"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="08be5-102">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-102">TableControl Element (Format)</span></span>

<span data-ttu-id="08be5-103">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-103">Defines a table format for a view.</span></span>

<span data-ttu-id="08be5-104">ViewDefinitions 요소 (Format) View 요소 (format) TableControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="08be5-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08be5-105">구문</span><span class="sxs-lookup"><span data-stu-id="08be5-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="08be5-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="08be5-106">Attributes and Elements</span></span>

<span data-ttu-id="08be5-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableControl` .</span><span class="sxs-lookup"><span data-stu-id="08be5-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="08be5-108">테이블의 행을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-108">You must specify the rows of the table.</span></span> <span data-ttu-id="08be5-109">다른 모든 자식 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="08be5-110">특성</span><span class="sxs-lookup"><span data-stu-id="08be5-110">Attributes</span></span>

<span data-ttu-id="08be5-111">없음</span><span class="sxs-lookup"><span data-stu-id="08be5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08be5-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="08be5-112">Child Elements</span></span>

|<span data-ttu-id="08be5-113">요소</span><span class="sxs-lookup"><span data-stu-id="08be5-113">Element</span></span>|<span data-ttu-id="08be5-114">설명</span><span class="sxs-lookup"><span data-stu-id="08be5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08be5-115">TableControl에 대한 AutoSize 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="08be5-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="08be5-117">데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="08be5-118">TableControl에 대 한 HideTableHeaders 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="08be5-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="08be5-120">테이블의 헤더가 표시 되지 않는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="08be5-121">TableControl (형식)의 TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="08be5-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="08be5-122">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-122">Required element.</span></span><br /><br /> <span data-ttu-id="08be5-123">테이블 뷰의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="08be5-124">TableControl에 대한 TableRowEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="08be5-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-125">Optional element.</span></span><br /><br /> <span data-ttu-id="08be5-126">테이블 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="08be5-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="08be5-127">Parent Elements</span></span>

|<span data-ttu-id="08be5-128">요소</span><span class="sxs-lookup"><span data-stu-id="08be5-128">Element</span></span>|<span data-ttu-id="08be5-129">설명</span><span class="sxs-lookup"><span data-stu-id="08be5-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08be5-130">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="08be5-131">하나 이상의 개체 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="08be5-132">설명</span><span class="sxs-lookup"><span data-stu-id="08be5-132">Remarks</span></span>

<span data-ttu-id="08be5-133">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08be5-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="08be5-134">예제</span><span class="sxs-lookup"><span data-stu-id="08be5-134">Example</span></span>

<span data-ttu-id="08be5-135">이 예제에서는 `TableControl` [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체의 속성을 표시 하는 데 사용 되는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="08be5-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="08be5-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08be5-136">See Also</span></span>

[<span data-ttu-id="08be5-137">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="08be5-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="08be5-138">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="08be5-139">TableControl에 대한 AutoSize 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="08be5-140">HideTableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="08be5-141">TableHeaders 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08be5-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="08be5-142">TableRowEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="08be5-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="08be5-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="08be5-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
