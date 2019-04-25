---
title: 테이블 뷰 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066841"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="eb76c-102">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="eb76c-102">Creating a Table View</span></span>

<span data-ttu-id="eb76c-103">테이블 뷰를 하나 이상의 열에 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="eb76c-104">표의 각 행.NET 개체를 나타내며 테이블의 각 열에 스크립트 값 또는 개체의 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="eb76c-105">개체의 모든 속성 또는 개체의 속성 하위 집합을 표시 하는 테이블 보기를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="eb76c-106">테이블 뷰 표시</span><span class="sxs-lookup"><span data-stu-id="eb76c-106">A Table View Display</span></span>

<span data-ttu-id="eb76c-107">다음 예제에서는 Windows PowerShell의 표시 하는 방법을 보여 줍니다.는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 에서 반환 되는 개체를 [Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb76c-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="eb76c-108">Windows PowerShell이이 개체에 대해 표시 되는 테이블 뷰를 정의 했습니다를 `Status` 속성을 `Name` 속성 (이 속성에 대 한 별칭 속성인를 `ServiceName` 속성), 및 `DisplayName` 속성.</span><span class="sxs-lookup"><span data-stu-id="eb76c-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="eb76c-109">표의 각 행은 cmdlet에서 반환 된 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="eb76c-110">테이블 보기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-110">Defining the Table View</span></span>

<span data-ttu-id="eb76c-111">다음 XML에 표시 하기 위한 테이블 뷰 스키마를 보여 줍니다는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="eb76c-112">테이블 보기에 표시 되는 각 속성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
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
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="eb76c-113">다음 XML 요소는 목록 뷰를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="eb76c-114">합니다 [보기](./view-element-format.md) 요소는 부모 요소 테이블 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="eb76c-115">(목록, 넓게 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="eb76c-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="eb76c-116">합니다 [이름을](./name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="eb76c-117">이 요소는 모든 보기에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-117">This element is required for all views.</span></span>

- <span data-ttu-id="eb76c-118">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 뷰를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="eb76c-119">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="eb76c-119">This element is required.</span></span>

- <span data-ttu-id="eb76c-120">합니다 [GroupBy](./groupby-element-for-view-format.md) 요소 (이 예제에 표시 되지 않음) 개체의 새 그룹을이 표시 되는 때를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="eb76c-121">새 그룹을 특정 속성이 나 스크립트의 값이 변경 될 때마다 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="eb76c-122">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-122">This element is optional.</span></span>

- <span data-ttu-id="eb76c-123">합니다 [컨트롤](./controls-element-for-view-format.md) 테이블 보기에서 정의한 사용자 지정 컨트롤을 정의 하는 요소 (이 예제에 표시 되지 않음).</span><span class="sxs-lookup"><span data-stu-id="eb76c-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="eb76c-124">컨트롤 추가 데이터가 표시 되는 방식을 지정 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="eb76c-125">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-125">This element is optional.</span></span> <span data-ttu-id="eb76c-126">뷰 자체 사용자 지정 컨트롤을 정의 하거나 형식 지정 파일의 보기 중 하나에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="eb76c-127">사용자 지정 컨트롤에 대 한 자세한 내용은 참조 하세요. [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="eb76c-128">합니다 [HideTableHeaders](./hidetableheaders-element-format.md) 요소 (이 예에 표시 되지 않습니다)은 테이블의 맨 위에 있는 레이블이 표시 되지 것입니다 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="eb76c-129">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-129">This element is optional.</span></span>

- <span data-ttu-id="eb76c-130">합니다 [TableControl](./tablecontrol-element-format.md) 테이블의 머리글 및 행 정보를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="eb76c-131">다른 모든 보기와 마찬가지로 테이블 뷰를 표시할 수 있습니다 개체 속성의 값 또는 스크립트에서 생성 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="eb76c-132">열 헤더를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-132">Defining Column Headers</span></span>

1. <span data-ttu-id="eb76c-133">합니다 [TableHeaders](./tableheaders-element-format.md) 테이블의 맨 위에 있는 표시 되는 항목 정의 요소 및 해당 자식 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="eb76c-134">합니다 [TableColumnHeader](./tablecolumnheader-element-format.md) 요소 테이블의 열 위쪽에 표시 되는 항목을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="eb76c-135">표시 된 헤더를 원하는 순서로 이러한 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="eb76c-136">사용할 수 있는 이러한 요소의 수 있지만 수 제한이 [TableColumnHeader](./tablecolumnheader-element-format.md) 테이블 보기의 요소 수가 같아야 [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 사용 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="eb76c-137">합니다 [레이블](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소 표시 되는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="eb76c-138">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-138">This element is optional.</span></span>

4. <span data-ttu-id="eb76c-139">합니다 [너비](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 너비 (문자 단위) 열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="eb76c-140">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-140">This element is optional.</span></span>

5. <span data-ttu-id="eb76c-141">합니다 [맞춤](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소 레이블이 표시 되는 방식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="eb76c-142">레이블은 왼쪽, 오른쪽에 정렬 또는 가운데 맞춤 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="eb76c-143">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="eb76c-144">테이블 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-144">Defining the Table Rows</span></span>

<span data-ttu-id="eb76c-145">테이블 보기의 자식 요소를 사용 하 여 테이블의 행에 표시 되는 데이터를 지정 하는 하나 이상의 정의 제공할 수는 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="eb76c-146">테이블의 행에 대 한 여러 정의 지정할 수 있지만 행에 대 한 헤더 어떤 행 정의 관계 없이 동일 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="eb76c-147">일반적으로 테이블을 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="eb76c-148">다음 예제에서는 보기에서는 일부의 속성의 값을 표시 하는 단일 정의 [System.Diagnostics.Process? Displayproperty =](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="eb76c-149">테이블 뷰를 해당 행에서 속성의 값 이나 스크립트 (예제에 표시 되지 않음)의 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
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
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="eb76c-150">행에 대 한 정의 제공 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="eb76c-151">합니다 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소와 해당 자식 요소는 테이블의 행에 표시 되는 항목을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="eb76c-152">합니다 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 요소 행의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="eb76c-153">하나 이상의 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 필수 사항입니다; 그러나는 추가할 수 있는 요소의 수를 최대 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="eb76c-154">대부분의 경우에서 뷰를 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="eb76c-155">합니다 [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 특정 정의 의해 표시 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="eb76c-156">이 요소는 선택 사항이 며 여러 개를 정의 하는 경우에 필요 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 다른 개체를 표시 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="eb76c-157">합니다 [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 지정 된 열 너비를 초과 하는 텍스트가 다음 줄에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="eb76c-158">기본적으로 열 너비를 초과하는 텍스트는 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="eb76c-159">합니다 [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) 요소 속성 또는 행의 값을 표시 하는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="eb76c-160">합니다 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="eb76c-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 각 열에 대 한 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="eb76c-162">첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="eb76c-163">합니다 [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 행에 해당 값이 표시 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="eb76c-164">속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="eb76c-165">합니다 [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 값은 행에 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="eb76c-166">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="eb76c-167">합니다 [FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소 스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="eb76c-168">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-168">This element is optional.</span></span>

- <span data-ttu-id="eb76c-169">합니다 [맞춤](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 속성 또는 스크립트의 값이 표시 되는 방식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="eb76c-170">값을 왼쪽, 오른쪽으로 정렬 또는 가운데 맞춤 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="eb76c-171">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="eb76c-172">테이블 보기를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="eb76c-173">테이블 뷰를 사용 하 여.NET 개체를 정의 하는 방법은 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="eb76c-174">사용할 수는 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의의 보기를 통해 표시 될 수 있는 개체 정의를 사용할 수는 [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 정의 개체를 표시 하는 요소는 특정 뷰의 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="eb76c-175">대부분의 경우에서 보기 있으므로 하나만 정의 하 여 개체는 일반적으로 정의 된 [ViewSelectedBy](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="eb76c-176">다음 예제에서는 사용 하 여 테이블 보기에 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [TypeName](./typename-element-for-viewselectedby-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="eb76c-177">수에 제한이 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 지정 하 고 해당 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="eb76c-178">테이블 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="eb76c-179">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의 목록 뷰에 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="eb76c-180">합니다 [TypeName](./typename-element-for-viewselectedby-format.md) 요소 보기에 표시 되는.NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="eb76c-181">정규화 된.NET 유형 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="eb76c-182">하나 이상의 형식 또는 선택이 보기에 대 한 설정 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="eb76c-183">다음 예제에서는 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="eb76c-184">관련된 목록 뷰를 정의 하는 경우와 같은 여러 뷰와 테이블 뷰를 사용 하 여 동일한 개체에 대해 표시 되는 개체 집합이 있는 선택 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="eb76c-185">선택 영역 집합을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [선택 집합 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="eb76c-186">목록 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="eb76c-187">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의 목록 뷰에 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="eb76c-188">합니다 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 보기에서 표시할 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="eb76c-189">하나 이상 선택 집합 또는 보기에 대 한 형식을 지정 해야 하지만 지정할 수 있는 요소의 최대 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="eb76c-190">다음 예제에서는 사용 하 여 테이블 보기의 특정 정의 의해 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="eb76c-191">이 요소를 사용 하 여, 개체, 개체 집합을 선택 또는 선택 조건 정의 사용 하는 경우를 지정 하는.NET 형식 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="eb76c-192">선택 조건을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="eb76c-193">테이블 보기의 정의가 여러 개 만들 때 다른 열 헤더를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="eb76c-194">어떤 개체는 같은 테이블의 행에 표시할 항목만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="eb76c-195">특정 목록 보기의 정의 의해 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="eb76c-196">합니다 [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소 정의 의해 표시 되는 객체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="eb76c-197">합니다 [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) 요소 정의 의해 표시 되는.NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="eb76c-198">이 요소를 사용 하는 경우 정규화 된.NET 유형 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="eb76c-199">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="eb76c-200">합니다 [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)이이 정의 의해 표시 될 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="eb76c-201">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="eb76c-202">합니다 [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)이이 정의를 사용할 수 있어야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="eb76c-203">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="eb76c-204">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="eb76c-205">서식 문자열 사용</span><span class="sxs-lookup"><span data-stu-id="eb76c-205">Using Format Strings</span></span>

<span data-ttu-id="eb76c-206">데이터 표시 되는 방법을 추가로 정의할 보기로 서식 문자열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="eb76c-207">다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="eb76c-208">다음 XML 요소가 형식 패턴을 지정 하려면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="eb76c-209">합니다 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="eb76c-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 각 열에 대 한 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="eb76c-211">첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="eb76c-212">합니다 [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 행에 해당 값이 표시 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="eb76c-213">속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="eb76c-214">합니다 [FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소 스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="eb76c-215">다음 예제에서는 `ToString` 메서드를 호출 하는 스크립트의 값의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="eb76c-216">스크립트 개체의 모든 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="eb76c-217">따라서 개체에 있는 경우 메서드를 같은 `ToString`형식 매개 변수가 있는, 스크립트는 스크립트의 출력 값의 서식을 지정 하는 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="eb76c-218">호출 하는 다음 XML 요소를 사용할 수는 `ToString` 메서드:</span><span class="sxs-lookup"><span data-stu-id="eb76c-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="eb76c-219">합니다 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="eb76c-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 각 열에 대 한 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="eb76c-221">첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="eb76c-222">합니다 [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 값은 행에 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="eb76c-223">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb76c-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb76c-224">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb76c-224">See Also</span></span>

[<span data-ttu-id="eb76c-225">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="eb76c-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
