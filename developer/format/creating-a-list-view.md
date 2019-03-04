---
title: 목록 뷰 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861579"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="a6738-102">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="a6738-102">Creating a List View</span></span>

<span data-ttu-id="a6738-103">목록 뷰 (순차적인 순서) 대로 단일 열에 데이터가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="a6738-104">목록에 표시 되는 데이터는.NET 속성의 값 또는 스크립트의 값 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="a6738-105">목록 뷰 표시</span><span class="sxs-lookup"><span data-stu-id="a6738-105">A List View Display</span></span>

<span data-ttu-id="a6738-106">다음 출력에서는 Windows PowerShell의 속성을 표시 하는 방법을 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 에서 반환 되는 개체를 [Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6738-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="a6738-107">이 예제에서는 세 가지 개체 이전 개체에서 빈 줄으로 구분 된 각 개체를 사용 하 여 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="a6738-108">목록 뷰를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-108">Defining the List View</span></span>

<span data-ttu-id="a6738-109">다음 XML의 여러 속성을 표시 하는 것에 대 한 목록 뷰 스키마를 보여 줍니다.는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="a6738-110">목록 보기에 표시 되는 각 속성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="a6738-111">다음 XML 요소는 목록 뷰를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="a6738-112">합니다 [보기](./view-element-format.md) 요소는 목록 보기의 부모 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="a6738-113">(테이블, 넓게 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="a6738-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="a6738-114">합니다 [이름을](./name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="a6738-115">이 요소는 모든 보기에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-115">This element is required for all views.</span></span>

- <span data-ttu-id="a6738-116">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 뷰를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="a6738-117">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="a6738-117">This element is required.</span></span>

- <span data-ttu-id="a6738-118">합니다 [GroupBy](./groupby-element-for-view-format.md) 요소 개체의 새 그룹을 표시 될 때를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="a6738-119">새 그룹을 특정 속성이 나 스크립트의 값이 변경 될 때마다 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="a6738-120">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-120">This element is optional.</span></span>

- <span data-ttu-id="a6738-121">합니다 [컨트롤](./controls-element-for-view-format.md) 요소 목록 보기에서 정의한 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="a6738-122">컨트롤 추가 데이터가 표시 되는 방식을 지정 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="a6738-123">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-123">This element is optional.</span></span> <span data-ttu-id="a6738-124">뷰 자체 사용자 지정 컨트롤을 정의 하거나 형식 지정 파일의 보기 중 하나에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="a6738-125">사용자 지정 컨트롤에 대 한 자세한 내용은 참조 하세요. [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="a6738-126">합니다 [ListControl](./listcontrol-element-format.md) 요소 보기에 표시 되는 항목 및 서식 지정 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="a6738-127">다른 모든 보기와 마찬가지로, 목록 뷰를 표시할 수 있습니다 개체 속성의 값 또는 스크립트에서 생성 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="a6738-128">간단한 목록 뷰를 정의 하는 전체 서식 파일의 예제를 보려면 [목록 보기 (기본)](./list-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="a6738-129">목록 보기에 대 한 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="a6738-130">목록 보기의 자식 요소를 사용 하 여 하나 이상의 정의 제공할 수는 [ListControl](./listcontrol-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="a6738-131">일반적으로 뷰를 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="a6738-132">다음 예제에서는 보기에서는 일부의 속성을 표시 하는 단일 정의 [System.Diagnostics.Process? Displayproperty =](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="a6738-133">속성의 값 또는 값 (이 예제에 표시 되지 않음) 스크립트의 목록 뷰를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="a6738-134">목록 보기에 대 한 정의 제공 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="a6738-135">합니다 [ListControl](./listcontrol-element-format.md) 요소와 해당 자식 요소 보기에 표시 되는 항목을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="a6738-136">합니다 [ListEntries](./listentries-element-for-listcontrol-format.md) 요소는 뷰의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="a6738-137">대부분의 경우에서 뷰를 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="a6738-138">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="a6738-138">This element is required.</span></span>

- <span data-ttu-id="a6738-139">합니다 [ListEntry](./listentry-element-for-listcontrol-format.md) 요소 뷰의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="a6738-140">하나 이상의 [ListEntry](./listentry-element-for-listcontrol-format.md) 필수 사항입니다; 그러나는 추가할 수 있는 요소의 수를 최대 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="a6738-141">대부분의 경우에서 뷰를 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="a6738-142">합니다 [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소는 특정 정의 의해 표시 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="a6738-143">이 요소는 선택 사항이 며 여러 개를 정의 하는 경우에 필요 [ListEntry](./listentry-element-for-listcontrol-format.md) 다른 개체를 표시 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="a6738-144">합니다 [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) 요소 속성 및 값을 목록 뷰의 행에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="a6738-145">합니다 [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) 요소 속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="a6738-146">목록 뷰는 하나 이상의 속성이 나 스크립트에 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="a6738-147">지정할 수 있는 행의 수는 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="a6738-148">합니다 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소 행에 해당 값이 표시 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="a6738-149">속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a6738-150">합니다 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소 값은 행에 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="a6738-151">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="a6738-152">합니다 [레이블](./label-element-for-listitem-for-listcontrol-format.md) 요소에는 행의 속성이 나 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="a6738-153">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-153">This element is optional.</span></span> <span data-ttu-id="a6738-154">레이블을 지정 하지 않으면 속성 또는 스크립트의 이름을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="a6738-155">전체 예제를 참조 하세요 [목록 보기 (레이블)](./list-view-labels.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="a6738-156">합니다 [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) 요소 표시할 행의 존재 해야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="a6738-157">목록 보기에 조건을 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="a6738-158">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-158">This element is optional.</span></span>

- <span data-ttu-id="a6738-159">합니다 [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) 요소 속성 또는 스크립트의 값을 표시 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="a6738-160">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-160">This element is optional.</span></span>

<span data-ttu-id="a6738-161">간단한 목록 뷰를 정의 하는 전체 서식 파일의 예제를 보려면 [목록 보기 (기본)](./list-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="a6738-162">목록 보기를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="a6738-163">목록 뷰를 사용 하는.NET 개체를 정의 하는 방법은 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="a6738-164">사용할 수는 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의의 보기를 통해 표시 될 수 있는 개체 정의를 사용할 수는 [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 정의 개체를 표시 하는 요소는 특정 뷰의 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="a6738-165">대부분의 경우에서 보기 있으므로 하나만 정의 하 여 개체는 일반적으로 정의 된 [ViewSelectedBy](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="a6738-166">다음 예제에서는 사용 하 여 목록 보기에 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [TypeName](./typename-element-for-viewselectedby-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a6738-167">수에 제한이 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 지정 하 고 해당 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="a6738-168">목록 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="a6738-169">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의 목록 뷰에 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a6738-170">합니다 [TypeName](./typename-element-for-viewselectedby-format.md) 요소 보기에 표시 되는.NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="a6738-171">정규화 된.NET 유형 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="a6738-172">하나 이상의 형식 또는 선택이 보기에 대 한 설정 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a6738-173">전체 서식 파일의 예제를 보려면 [목록 보기 (기본)](./list-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="a6738-174">다음 예제에서는 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a6738-175">관련된 목록 뷰를 정의 하는 경우와 같은 여러 뷰와 테이블 뷰를 사용 하 여 동일한 개체에 대해 표시 되는 개체 집합이 있는 선택 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="a6738-176">선택 영역 집합을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [선택 집합 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="a6738-177">목록 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="a6738-178">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의 목록 뷰에 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a6738-179">합니다 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 보기에서 표시할 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="a6738-180">하나 이상 선택 집합 또는 보기에 대 한 형식을 지정 해야 하지만 지정할 수 있는 요소의 최대 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a6738-181">다음 예제에서는 특정 정의 사용 하 여 목록 뷰에 의해 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="a6738-182">이 요소를 사용 하 여, 개체, 개체 집합을 선택 또는 선택 조건 정의 사용 하는 경우를 지정 하는.NET 형식 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="a6738-183">선택 조건을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="a6738-184">특정 목록 보기의 정의 의해 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="a6738-185">합니다 [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소 정의 의해 표시 되는 객체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="a6738-186">합니다 [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) 요소 정의 의해 표시 되는.NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="a6738-187">이 요소를 사용 하는 경우 정규화 된.NET 유형 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="a6738-188">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a6738-189">합니다 [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)이이 정의 의해 표시 될 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="a6738-190">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a6738-191">합니다 [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)이이 정의를 사용할 수 있어야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a6738-192">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="a6738-193">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="a6738-194">개체의 그룹 목록 뷰 표시</span><span class="sxs-lookup"><span data-stu-id="a6738-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="a6738-195">그룹화 목록 보기에 표시 되는 개체를 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="a6738-196">그렇다고 그룹을 정의 하는 Windows PowerShell 스크립트 또는 특정 속성의 값이 변경 될 때마다 새 그룹을 시작만 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="a6738-197">다음 예제에서는 새 그룹을 시작 됩니다 때마다 값은 [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="a6738-198">다음 XML 요소가 그룹 시작 될 때를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="a6738-199">합니다 [GroupBy](./groupby-element-for-view-format.md) 속성 또는 새 그룹을 시작 하 고 그룹 표시 되는 방식을 정의 하는 스크립트 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="a6738-200">합니다 [PropertyName](./propertyname-element-for-groupby-format.md) 요소 값이 변경 될 때마다 새 그룹을 시작 하는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="a6738-201">속성 또는 그룹을 시작 하는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="a6738-202">합니다 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소는 해당 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="a6738-203">스크립트 또는 그룹을 시작 하는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="a6738-204">합니다 [레이블](./label-element-for-groupby-format.md) 요소는 각 그룹의 시작 부분에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="a6738-205">이 요소에 의해 지정 된 텍스트를 외에도 Windows PowerShell에는 새 그룹 트리거되고 레이블을 전후에 빈 줄을 추가 하는 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="a6738-206">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-206">This element is optional.</span></span>

- <span data-ttu-id="a6738-207">합니다 [CustomControl](./customcontrol-element-for-groupby-format.md) 요소에는 데이터를 표시 하는 데 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="a6738-208">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-208">This element is optional.</span></span>

- <span data-ttu-id="a6738-209">[CustomControlName](./customcontrolname-element-for-groupby-format.md) 요소 지정 일반적인 보거나 데이터를 표시 하는 데 사용 되는 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="a6738-210">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-210">This element is optional.</span></span>

<span data-ttu-id="a6738-211">그룹을 정의 하는 전체 서식 파일의 예제를 보려면 [목록 보기 (GroupBy)](./list-view-groupby.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="a6738-212">서식 문자열 사용</span><span class="sxs-lookup"><span data-stu-id="a6738-212">Using Format Strings</span></span>

<span data-ttu-id="a6738-213">데이터 표시 되는 방법을 추가로 정의할 보기로 서식 문자열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="a6738-214">다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="a6738-215">다음 XML 요소가 형식 패턴을 지정 하려면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="a6738-216">합니다 [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="a6738-217">합니다 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소 보기에서 해당 값이 표시 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="a6738-218">속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a6738-219">합니다 [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) 요소 속성 또는 스크립트 값 보기에 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="a6738-220">합니다 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소 (표시 되지 않음) 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="a6738-221">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="a6738-222">다음 예제에서는 `ToString` 메서드를 호출 하는 스크립트의 값의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="a6738-223">스크립트 개체의 모든 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="a6738-224">따라서 개체에 있는 경우 메서드를 같은 `ToString`형식 매개 변수가 있는, 스크립트는 스크립트의 출력 값의 서식을 지정 하는 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="a6738-225">호출 하는 다음 XML 요소를 사용할 수는 `ToString` 메서드:</span><span class="sxs-lookup"><span data-stu-id="a6738-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="a6738-226">합니다 [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="a6738-227">합니다 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소 (표시 되지 않음) 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="a6738-228">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6738-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6738-229">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6738-229">See Also</span></span>

<span data-ttu-id="a6738-230">[Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="a6738-230">[Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)</span></span>
