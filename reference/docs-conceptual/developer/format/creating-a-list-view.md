---
ms.date: 09/13/2016
ms.topic: reference
title: 목록 보기 만들기
description: 목록 보기 만들기
ms.openlocfilehash: c34c4fddc27d4fd016fba37fc465924d693756a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655633"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="1fec9-103">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="1fec9-103">Creating a List View</span></span>

<span data-ttu-id="1fec9-104">목록 뷰는 단일 열 (순서 대로)에 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-104">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="1fec9-105">목록에 표시 되는 데이터는 .NET 속성의 값 또는 스크립트의 값일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-105">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="1fec9-106">목록 보기 표시</span><span class="sxs-lookup"><span data-stu-id="1fec9-106">A List View Display</span></span>

<span data-ttu-id="1fec9-107">다음 출력은 Windows PowerShell에서 Servicecontroller의 속성을 표시 하는 방법을 보여 줍니다 [. Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) cmdlet에 의해 반환 [되는](/powershell/module/microsoft.powershell.management/get-service) Fullname 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-107">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="1fec9-108">이 예제에서는 세 개의 개체가 반환 되 고 각 개체는 이전 개체와 빈 줄로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-108">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="1fec9-109">목록 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="1fec9-109">Defining the List View</span></span>

<span data-ttu-id="1fec9-110">다음 XML은 Servicecontroller의 여러 속성을 표시 하기 위한 목록 뷰 스키마를 보여 줍니다 [. Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-110">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="1fec9-111">목록 뷰에 표시 하려는 각 속성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-111">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="1fec9-112">다음 XML 요소를 사용 하 여 목록 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-112">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="1fec9-113">[뷰](./view-element-format.md) 요소는 목록 뷰의 부모 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-113">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="1fec9-114">이는 테이블, 전체 및 사용자 지정 컨트롤 뷰의 부모 요소와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-114">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="1fec9-115">[Name](./name-element-for-view-format.md) 요소는 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="1fec9-116">이 요소는 모든 뷰에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-116">This element is required for all views.</span></span>

- <span data-ttu-id="1fec9-117">[Viewselectedby](./viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="1fec9-118">이 요소는 필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-118">This element is required.</span></span>

- <span data-ttu-id="1fec9-119">[GroupBy](./groupby-element-for-view-format.md) 요소는 새 개체 그룹이 표시 되는 시기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="1fec9-120">특정 속성 또는 스크립트의 값이 변경 될 때마다 새 그룹이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="1fec9-121">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-121">This element is optional.</span></span>

- <span data-ttu-id="1fec9-122">[Controls](./controls-element-for-view-format.md) 요소는 목록 뷰에서 정의 된 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-122">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="1fec9-123">컨트롤을 통해 데이터 표시 방법을 추가로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="1fec9-124">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-124">This element is optional.</span></span> <span data-ttu-id="1fec9-125">뷰는 자체 사용자 지정 컨트롤을 정의 하거나 서식 파일의 뷰에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="1fec9-126">사용자 지정 컨트롤에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="1fec9-127">[이 listcontrol](./listcontrol-element-format.md) 요소는 뷰에 표시 되는 내용 및 형식을 지정 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-127">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="1fec9-128">다른 모든 뷰와 마찬가지로 목록 보기에는 스크립트에 의해 생성 된 개체 속성 또는 값의 값이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-128">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="1fec9-129">간단한 목록 뷰를 정의 하는 전체 서식 파일의 예는 [목록 뷰 (Basic)](./list-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-129">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="1fec9-130">목록 뷰에 대 한 정의 제공</span><span class="sxs-lookup"><span data-stu-id="1fec9-130">Providing Definitions for Your List View</span></span>

<span data-ttu-id="1fec9-131">목록 뷰는 [이 listcontrol](./listcontrol-element-format.md) 요소의 자식 요소를 사용 하 여 하나 이상의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-131">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="1fec9-132">일반적으로 보기에는 하나의 정의만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="1fec9-133">다음 예제에서 뷰는 System.object의 여러 속성을 표시 하는 단일 정의를 제공 합니다. [ Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-133">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="1fec9-134">목록 뷰에는 속성 값 또는 스크립트 값 (예제에는 표시 되지 않음)이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-134">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="1fec9-135">다음 XML 요소를 사용 하 여 목록 뷰에 대 한 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-135">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="1fec9-136">[이 listcontrol](./listcontrol-element-format.md) 요소 및 해당 자식 요소는 뷰에 표시 되는 내용을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-136">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="1fec9-137">[ListEntries](./listentries-element-for-listcontrol-format.md) 요소는 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-137">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="1fec9-138">대부분의 경우 보기에는 하나의 정의만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-138">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="1fec9-139">이 요소는 필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-139">This element is required.</span></span>

- <span data-ttu-id="1fec9-140">[ListEntry](./listentry-element-for-listcontrol-format.md) 요소는 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-140">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="1fec9-141">하나 이상의 [ListEntry](./listentry-element-for-listcontrol-format.md) 가 필요 합니다. 그러나 추가할 수 있는 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-141">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="1fec9-142">대부분의 경우 보기에는 하나의 정의만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-142">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="1fec9-143">[Entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소는 특정 정의에 의해 표시 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-143">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="1fec9-144">이 요소는 선택 사항이 며 다른 개체를 표시 하는 여러 [ListEntry](./listentry-element-for-listcontrol-format.md) 요소를 정의 하는 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-144">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="1fec9-145">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) 요소는 목록 뷰의 행에 값이 표시 되는 속성 및 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-145">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="1fec9-146">[ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) 요소는 값이 목록 뷰의 행에 표시 되는 속성 또는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-146">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="1fec9-147">목록 뷰에서 하나 이상의 속성 또는 스크립트를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-147">A list view must specify at least one property or script.</span></span> <span data-ttu-id="1fec9-148">지정할 수 있는 행 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-148">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="1fec9-149">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소는 값이 행에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-149">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="1fec9-150">속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-150">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1fec9-151">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소는 값이 행에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-151">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="1fec9-152">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-152">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="1fec9-153">[Label](./label-element-for-listitem-for-listcontrol-format.md) 요소는 행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-153">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="1fec9-154">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-154">This element is optional.</span></span> <span data-ttu-id="1fec9-155">레이블을 지정 하지 않으면 속성이 나 스크립트의 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-155">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="1fec9-156">전체 예제는 [목록 뷰 (레이블)](./list-view-labels.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-156">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="1fec9-157">[Itemselectioncondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) 요소는 행을 표시 하기 위해 존재 해야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-157">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="1fec9-158">목록 뷰에 조건을 추가 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-158">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="1fec9-159">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-159">This element is optional.</span></span>

- <span data-ttu-id="1fec9-160">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) 요소는 속성이 나 스크립트의 값을 표시 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-160">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="1fec9-161">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-161">This element is optional.</span></span>

<span data-ttu-id="1fec9-162">간단한 목록 뷰를 정의 하는 전체 서식 파일의 예는 [목록 뷰 (Basic)](./list-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-162">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="1fec9-163">목록 뷰를 사용 하는 개체 정의</span><span class="sxs-lookup"><span data-stu-id="1fec9-163">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="1fec9-164">목록 뷰를 사용 하는 .NET 개체를 정의 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-164">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="1fec9-165">[Viewselectedby](./viewselectedby-element-format.md) 요소를 사용 하 여 뷰의 모든 정의에서 표시할 수 있는 개체를 정의 하거나, [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소를 사용 하 여 뷰의 특정 정의에 표시 되는 개체를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-165">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="1fec9-166">대부분의 경우 뷰에는 정의가 하나만 있으므로 개체는 일반적으로 [Viewselectedby](./viewselectedby-element-format.md) 요소에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-166">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="1fec9-167">다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 사용 하 여 목록 뷰에 표시 되는 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-167">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1fec9-168">지정할 수 있는 [TypeName](./typename-element-for-viewselectedby-format.md) 요소의 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-168">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="1fec9-169">다음 XML 요소는 목록 뷰에서 사용 되는 개체를 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-169">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="1fec9-170">[Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-170">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="1fec9-171">[TypeName](./typename-element-for-viewselectedby-format.md) 요소는 뷰에 표시 되는 .net 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-171">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="1fec9-172">정규화 된 .NET 형식 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-172">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="1fec9-173">뷰에 대해 하나 이상의 유형 또는 선택 집합을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-173">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1fec9-174">전체 서식 파일에 대 한 예제는 [목록 뷰 (기본)](./list-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-174">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="1fec9-175">다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-175">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="1fec9-176">동일한 개체에 대 한 목록 뷰 및 테이블 뷰를 정의 하는 경우와 같이 여러 뷰를 사용 하 여 표시 되는 관련 개체 집합이 있는 선택 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-176">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="1fec9-177">선택 집합을 만드는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-177">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="1fec9-178">다음 XML 요소는 목록 뷰에서 사용 되는 개체를 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-178">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="1fec9-179">[Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="1fec9-180">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소는 뷰에서 표시할 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-180">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="1fec9-181">뷰에 대해 하나 이상의 선택 집합 또는 유형을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-181">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="1fec9-182">다음 예제에서는 [Entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소를 사용 하 여 목록 뷰의 특정 정의에 표시 되는 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-182">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="1fec9-183">이 요소를 사용 하 여 개체의 .NET 형식 이름, 개체의 선택 집합 또는 정의가 사용 되는 시기를 지정 하는 선택 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-183">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="1fec9-184">선택 조건을 만드는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-184">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="1fec9-185">다음 XML 요소를 사용 하 여 목록 뷰의 특정 정의에서 사용 되는 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-185">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="1fec9-186">[Entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소는 정의에 의해 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-186">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="1fec9-187">[TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) 요소는 정의에 의해 표시 되는 .net 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-187">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="1fec9-188">이 요소를 사용 하는 경우 정규화 된 .NET 형식 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-188">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="1fec9-189">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-189">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1fec9-190">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의에 의해 표시 될 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-190">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="1fec9-191">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-191">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="1fec9-192">[Selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의를 사용 하기 위해 존재 해야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-192">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="1fec9-193">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-193">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="1fec9-194">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-194">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="1fec9-195">목록 뷰에서 개체 그룹 표시</span><span class="sxs-lookup"><span data-stu-id="1fec9-195">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="1fec9-196">목록 뷰에서 표시 되는 개체를 그룹으로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-196">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="1fec9-197">이는 그룹을 정의 하는 것이 아니라 특정 속성이 나 스크립트의 값이 변경 될 때마다 Windows PowerShell이 새 그룹을 시작 한다는 의미는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-197">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="1fec9-198">다음 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 값이 변경 될 때마다 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-198">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="1fec9-199">다음 XML 요소는 그룹이 시작 되는 시기를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-199">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="1fec9-200">[GroupBy](./groupby-element-for-view-format.md) 요소는 새 그룹을 시작 하 고 그룹이 표시 되는 방법을 정의 하는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-200">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="1fec9-201">[PropertyName](./propertyname-element-for-groupby-format.md) 요소는 값이 변경 될 때마다 새 그룹을 시작 하는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-201">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="1fec9-202">그룹을 시작 하려면 속성이 나 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-202">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="1fec9-203">[ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소는 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-203">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="1fec9-204">그룹을 시작 하려면 스크립트나 속성을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-204">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="1fec9-205">[Label](./label-element-for-groupby-format.md) 요소는 각 그룹의 시작 부분에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-205">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="1fec9-206">이 요소에 지정 된 텍스트 외에도 Windows PowerShell은 새 그룹을 트리거한 값을 표시 하 고 레이블 앞뒤에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-206">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="1fec9-207">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-207">This element is optional.</span></span>

- <span data-ttu-id="1fec9-208">[CustomControl](./customcontrol-element-for-groupby-format.md) 요소는 데이터를 표시 하는 데 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-208">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="1fec9-209">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-209">This element is optional.</span></span>

- <span data-ttu-id="1fec9-210">[Customcontrolname](./customcontrolname-element-for-groupby-format.md) 요소는 데이터를 표시 하는 데 사용 되는 공용 또는 뷰 컨트롤을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-210">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="1fec9-211">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-211">This element is optional.</span></span>

<span data-ttu-id="1fec9-212">그룹을 정의 하는 전체 서식 파일에 대 한 예제는 [목록 뷰 (GroupBy)](./list-view-groupby.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1fec9-212">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="1fec9-213">서식 문자열 사용</span><span class="sxs-lookup"><span data-stu-id="1fec9-213">Using Format Strings</span></span>

<span data-ttu-id="1fec9-214">서식 문자열을 뷰에 추가 하 여 데이터 표시 방법을 추가로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-214">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="1fec9-215">다음 예제에서는 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다 `StartTime` .</span><span class="sxs-lookup"><span data-stu-id="1fec9-215">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="1fec9-216">다음 XML 요소를 사용 하 여 형식 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-216">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="1fec9-217">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-217">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="1fec9-218">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소는 값이 뷰에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-218">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="1fec9-219">속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-219">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="1fec9-220">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) 요소는 속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-220">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="1fec9-221">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-221">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="1fec9-222">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-222">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="1fec9-223">다음 예제에서는 `ToString` 메서드를 호출 하 여 스크립트의 값에 대 한 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-223">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="1fec9-224">스크립트는 개체의 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-224">Scripts can call any method of an object.</span></span> <span data-ttu-id="1fec9-225">따라서 개체에 `ToString` 형식 매개 변수를 포함 하는 등의 메서드가 있는 경우 스크립트는 해당 메서드를 호출 하 여 스크립트의 출력 값에 대 한 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-225">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="1fec9-226">다음 XML 요소를 사용 하 여 메서드를 호출할 수 있습니다 `ToString` .</span><span class="sxs-lookup"><span data-stu-id="1fec9-226">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="1fec9-227">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-227">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="1fec9-228">[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-228">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="1fec9-229">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1fec9-229">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fec9-230">관련 항목</span><span class="sxs-lookup"><span data-stu-id="1fec9-230">See Also</span></span>

[<span data-ttu-id="1fec9-231">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="1fec9-231">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
