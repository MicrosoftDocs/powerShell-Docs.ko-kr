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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363412"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="0b476-102">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="0b476-102">Creating a Table View</span></span>

<span data-ttu-id="0b476-103">테이블 뷰는 하나 이상의 열에 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="0b476-104">테이블의 각 행은 .NET 개체를 나타내고, 테이블의 각 열은 개체 또는 스크립트 값의 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="0b476-105">개체의 모든 속성 또는 개체 속성의 하위 집합을 표시 하는 테이블 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="0b476-106">테이블 보기 표시</span><span class="sxs-lookup"><span data-stu-id="0b476-106">A Table View Display</span></span>

<span data-ttu-id="0b476-107">다음 예제에서는 Windows PowerShell에서 [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet이 반환하는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체를 표시하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="0b476-108">이 개체의 경우 Windows PowerShell은 `Status` 속성, `Name` 속성 (이 속성은 `ServiceName` 속성의 별칭 속성) 및 `DisplayName` 속성을 표시 하는 테이블 뷰를 정의 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="0b476-109">테이블의 각 행은 cmdlet에서 반환 된 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="0b476-110">테이블 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="0b476-110">Defining the Table View</span></span>

<span data-ttu-id="0b476-111">다음 XML은 Servicecontroller을 표시 하기 위한 테이블 뷰 스키마를 보여 줍니다. [ Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="0b476-112">테이블 뷰에 표시 하려는 각 속성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="0b476-113">다음 XML 요소를 사용 하 여 목록 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="0b476-114">[뷰](./view-element-format.md) 요소는 테이블 뷰의 부모 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="0b476-115">이 요소는 목록, 전체 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="0b476-116">[Name](./name-element-for-view-format.md) 요소는 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="0b476-117">이 요소는 모든 뷰에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-117">This element is required for all views.</span></span>

- <span data-ttu-id="0b476-118">[Viewselectedby](./viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="0b476-119">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="0b476-119">This element is required.</span></span>

- <span data-ttu-id="0b476-120">[GroupBy](./groupby-element-for-view-format.md) 요소 (이 예제에는 표시 되지 않음)는 새 개체 그룹이 표시 되는 시점을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="0b476-121">특정 속성 또는 스크립트의 값이 변경 될 때마다 새 그룹이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="0b476-122">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-122">This element is optional.</span></span>

- <span data-ttu-id="0b476-123">[Controls](./controls-element-for-view-format.md) 요소 (이 예제에는 표시 되지 않음)는 테이블 뷰로 정의 된 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="0b476-124">컨트롤을 통해 데이터 표시 방법을 추가로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="0b476-125">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-125">This element is optional.</span></span> <span data-ttu-id="0b476-126">뷰는 자체 사용자 지정 컨트롤을 정의 하거나 서식 파일의 뷰에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="0b476-127">사용자 지정 컨트롤에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b476-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="0b476-128">[HideTableHeaders](./hidetableheaders-element-format.md) 요소 (이 예에서는 표시 되지 않음)는 테이블의 맨 위에 레이블을 표시 하지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="0b476-129">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-129">This element is optional.</span></span>

- <span data-ttu-id="0b476-130">테이블의 헤더 및 행 정보를 정의 하는 [TableControl](./tablecontrol-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="0b476-131">다른 모든 뷰와 마찬가지로, 테이블 뷰에서는 스크립트에 의해 생성 된 개체 속성 또는 값의 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="0b476-132">열 머리글 정의</span><span class="sxs-lookup"><span data-stu-id="0b476-132">Defining Column Headers</span></span>

1. <span data-ttu-id="0b476-133">[Tableheaders](./tableheaders-element-format.md) 요소와 해당 자식 요소는 테이블의 맨 위에 표시 되는 내용을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="0b476-134">[TableColumnHeader](./tablecolumnheader-element-format.md) 요소는 테이블의 열 맨 위에 표시 되는 항목을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="0b476-135">헤더를 표시할 순서 대로 이러한 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="0b476-136">사용할 수 있는 이러한 요소 수에는 제한이 없지만 테이블 뷰의 [TableColumnHeader](./tablecolumnheader-element-format.md) 요소 수는 사용 하는 [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 요소 수와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="0b476-137">[Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 표시 되는 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="0b476-138">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-138">This element is optional.</span></span>

4. <span data-ttu-id="0b476-139">[Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 열의 너비 (문자)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="0b476-140">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-140">This element is optional.</span></span>

5. <span data-ttu-id="0b476-141">[Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 레이블이 표시 되는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="0b476-142">레이블은 왼쪽, 오른쪽 또는 가운데에 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="0b476-143">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="0b476-144">테이블 행 정의</span><span class="sxs-lookup"><span data-stu-id="0b476-144">Defining the Table Rows</span></span>

<span data-ttu-id="0b476-145">테이블 뷰는 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소의 자식 요소를 사용 하 여 테이블의 행에 표시 되는 데이터를 지정 하는 하나 이상의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="0b476-146">테이블의 행에 대 한 여러 정의를 지정할 수 있지만 행의 머리글은 사용 되는 행 정의에 관계 없이 동일 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="0b476-147">일반적으로 테이블에는 정의가 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="0b476-148">다음 예제에서 뷰는 System.object의 여러 속성 값을 표시 하는 단일 정의를 제공 합니다. [ Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="0b476-149">테이블 뷰에서는 속성 값 또는 스크립트 값 (예제에서는 표시 되지 않음)을 행에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="0b476-150">다음 XML 요소를 사용 하 여 행에 대 한 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="0b476-151">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소 및 해당 자식 요소는 테이블의 행에 표시 되는 항목을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="0b476-152">[TableRowEntry](./listentry-element-for-listcontrol-format.md) 요소는 행의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="0b476-153">하나 이상의 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 가 필요 합니다. 그러나 추가할 수 있는 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="0b476-154">대부분의 경우 보기에는 하나의 정의만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="0b476-155">[Entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 특정 정의에 의해 표시 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="0b476-156">이 요소는 선택 사항이 며 다른 개체를 표시 하는 여러 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 요소를 정의 하는 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="0b476-157">[Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 열 너비를 초과 하는 텍스트를 다음 줄에 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="0b476-158">기본적으로 열 너비를 초과하는 텍스트는 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="0b476-159">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="0b476-160">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="0b476-161">행의 각 열에는 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="0b476-162">첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="0b476-163">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="0b476-164">속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="0b476-165">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="0b476-166">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="0b476-167">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소는 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="0b476-168">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-168">This element is optional.</span></span>

- <span data-ttu-id="0b476-169">[Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 속성이 나 스크립트의 값이 표시 되는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="0b476-170">값을 왼쪽, 오른쪽 또는 가운데에 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="0b476-171">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="0b476-172">테이블 뷰를 사용 하는 개체 정의</span><span class="sxs-lookup"><span data-stu-id="0b476-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="0b476-173">테이블 뷰를 사용 하는 .NET 개체를 정의 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="0b476-174">[Viewselectedby](./viewselectedby-element-format.md) 요소를 사용 하 여 뷰의 모든 정의에서 표시할 수 있는 개체를 정의 하거나, [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소를 사용 하 여 뷰의 특정 정의에 표시 되는 개체를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="0b476-175">대부분의 경우 뷰에는 정의가 하나만 있으므로 개체는 일반적으로 [Viewselectedby](./viewselectedby-element-format.md) 요소에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="0b476-176">다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 사용 하 여 테이블 뷰에 표시 되는 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="0b476-177">지정할 수 있는 [TypeName](./typename-element-for-viewselectedby-format.md) 요소의 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="0b476-178">다음 XML 요소를 사용 하 여 테이블 뷰에서 사용 되는 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="0b476-179">[Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="0b476-180">[TypeName](./typename-element-for-viewselectedby-format.md) 요소는 뷰에 표시 되는 .net 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="0b476-181">정규화 된 .NET 형식 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="0b476-182">뷰에 대해 하나 이상의 유형 또는 선택 집합을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="0b476-183">다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="0b476-184">동일한 개체에 대 한 목록 뷰 및 테이블 뷰를 정의 하는 경우와 같이 여러 뷰를 사용 하 여 표시 되는 관련 개체 집합이 있는 선택 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="0b476-185">선택 집합을 만드는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b476-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="0b476-186">다음 XML 요소는 목록 뷰에서 사용 되는 개체를 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="0b476-187">[Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="0b476-188">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소는 뷰에서 표시할 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="0b476-189">뷰에 대해 하나 이상의 선택 집합 또는 유형을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="0b476-190">다음 예에서는 [Entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소를 사용 하 여 테이블 뷰의 특정 정의에 표시 되는 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="0b476-191">이 요소를 사용 하 여 개체의 .NET 형식 이름, 개체의 선택 집합 또는 정의가 사용 되는 시기를 지정 하는 선택 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="0b476-192">선택 조건을 만드는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b476-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0b476-193">테이블 뷰의 정의를 여러 개 만들 때 다른 열 머리글을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="0b476-194">표시 되는 개체와 같이 테이블의 행에 표시 되는 항목을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="0b476-195">다음 XML 요소를 사용 하 여 목록 뷰의 특정 정의에서 사용 되는 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="0b476-196">[Entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 정의에 의해 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="0b476-197">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) 요소는 정의에 의해 표시 되는 .net 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="0b476-198">이 요소를 사용 하는 경우 정규화 된 .NET 형식 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="0b476-199">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="0b476-200">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의에 의해 표시 될 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="0b476-201">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="0b476-202">[Selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의를 사용 하기 위해 존재 해야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0b476-203">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="0b476-204">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b476-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="0b476-205">서식 문자열 사용</span><span class="sxs-lookup"><span data-stu-id="0b476-205">Using Format Strings</span></span>

<span data-ttu-id="0b476-206">서식 문자열을 뷰에 추가 하 여 데이터 표시 방법을 추가로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="0b476-207">다음 예제에서는 `StartTime` 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="0b476-208">다음 XML 요소를 사용 하 여 형식 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="0b476-209">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="0b476-210">행의 각 열에는 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="0b476-211">첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="0b476-212">[PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="0b476-213">속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="0b476-214">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소는 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="0b476-215">다음 예제에서는 스크립트의 값에 대 한 서식을 지정 하기 위해 `ToString` 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="0b476-216">스크립트는 개체의 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="0b476-217">따라서 개체에 형식 지정 매개 변수가 있는 `ToString`와 같은 메서드가 있는 경우 스크립트는 해당 메서드를 호출 하 여 스크립트의 출력 값에 대 한 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="0b476-218">다음 XML 요소를 사용 하 여 `ToString` 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="0b476-219">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="0b476-220">행의 각 열에는 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="0b476-221">첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="0b476-222">[ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="0b476-223">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b476-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b476-224">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b476-224">See Also</span></span>

[<span data-ttu-id="0b476-225">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="0b476-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
