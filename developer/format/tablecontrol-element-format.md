---
title: TableControl 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063831"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="c732b-102">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c732b-102">TableControl Element (Format)</span></span>

<span data-ttu-id="c732b-103">보기에 대 한 테이블 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-103">Defines a table format for a view.</span></span>

<span data-ttu-id="c732b-104">ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c732b-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c732b-105">구문</span><span class="sxs-lookup"><span data-stu-id="c732b-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c732b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-106">Attributes and Elements</span></span>

<span data-ttu-id="c732b-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableControl` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="c732b-108">테이블의 행을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-108">You must specify the rows of the table.</span></span> <span data-ttu-id="c732b-109">다른 모든 자식 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="c732b-110">특성</span><span class="sxs-lookup"><span data-stu-id="c732b-110">Attributes</span></span>

<span data-ttu-id="c732b-111">없음</span><span class="sxs-lookup"><span data-stu-id="c732b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c732b-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-112">Child Elements</span></span>

|<span data-ttu-id="c732b-113">요소</span><span class="sxs-lookup"><span data-stu-id="c732b-113">Element</span></span>|<span data-ttu-id="c732b-114">설명</span><span class="sxs-lookup"><span data-stu-id="c732b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c732b-115">TableControl (형식)에 대 한 자동 크기 조정 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="c732b-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c732b-117">조정 여부를 열 크기 및 열 개수는 데이터의 크기를 기준으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="c732b-118">TableControl (형식)에 대 한 HideTableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="c732b-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c732b-120">테이블의 머리글을 표시 하지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="c732b-121">TableControl (형식)에 대 한 TableHeaders 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="c732b-122">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-122">Required element.</span></span><br /><br /> <span data-ttu-id="c732b-123">레이블, 너비 및 테이블 뷰의 열에 대 한 데이터의 맞춤을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="c732b-124">TableControl (형식)에 대 한 TableRowEntries 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="c732b-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c732b-126">테이블 보기의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c732b-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-127">Parent Elements</span></span>

|<span data-ttu-id="c732b-128">요소</span><span class="sxs-lookup"><span data-stu-id="c732b-128">Element</span></span>|<span data-ttu-id="c732b-129">설명</span><span class="sxs-lookup"><span data-stu-id="c732b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c732b-130">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c732b-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c732b-131">하나 이상의 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c732b-132">설명</span><span class="sxs-lookup"><span data-stu-id="c732b-132">Remarks</span></span>

<span data-ttu-id="c732b-133">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c732b-134">예제</span><span class="sxs-lookup"><span data-stu-id="c732b-134">Example</span></span>

<span data-ttu-id="c732b-135">이 예제는 `TableControl` 의 속성을 표시 하는 데 사용 되는 요소는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c732b-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c732b-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c732b-136">See Also</span></span>

[<span data-ttu-id="c732b-137">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="c732b-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c732b-138">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c732b-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c732b-139">TableControl (형식)에 대 한 자동 크기 조정 요소</span><span class="sxs-lookup"><span data-stu-id="c732b-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="c732b-140">HideTableHeaders 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c732b-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="c732b-141">TableHeaders 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c732b-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="c732b-142">TableRowEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c732b-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="c732b-143">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="c732b-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
