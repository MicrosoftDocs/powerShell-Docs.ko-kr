---
title: 넓은 뷰 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368952"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="36519-102">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="36519-102">Creating a Wide View</span></span>

<span data-ttu-id="36519-103">넓은 보기에는 표시 되는 각 개체에 대 한 단일 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36519-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="36519-104">표시 되는 값은 .NET 개체 속성의 값 또는 스크립트의 값일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="36519-105">이 보기에는 기본적으로 레이블이나 머리글이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="36519-106">넓은 보기 표시</span><span class="sxs-lookup"><span data-stu-id="36519-106">A Wide View Display</span></span>

<span data-ttu-id="36519-107">다음 예제에서는 Windows PowerShell에서 출력이 [형식 전체](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet으로 파이프 되는 경우에는 [Get process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet에 의해 반환 되는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체를 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36519-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="36519-108">기본적으로, [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 테이블 뷰를 반환 합니다. 이 예에서는 두 개의 열을 사용 하 여 반환 된 각 개체에 대 한 프로세스의 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="36519-109">개체의 속성 이름이 표시 되지 않고 속성의 값만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36519-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="36519-110">넓은 뷰 정의</span><span class="sxs-lookup"><span data-stu-id="36519-110">Defining the Wide View</span></span>

<span data-ttu-id="36519-111">다음 XML에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체에 대 한 넓은 뷰 스키마를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36519-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="36519-112">다음 XML 요소는 넓은 뷰를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36519-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="36519-113">[뷰](./view-element-format.md) 요소는 넓은 뷰의 부모 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="36519-114">이 요소는 테이블, 목록 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="36519-115">[Name](./name-element-for-view-format.md) 요소는 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="36519-116">이 요소는 모든 뷰에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-116">This element is required for all views.</span></span>

- <span data-ttu-id="36519-117">[Viewselectedby](./viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="36519-118">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="36519-118">This element is required.</span></span>

- <span data-ttu-id="36519-119">[GroupBy](./groupby-element-for-view-format.md) 요소는 새 개체 그룹이 표시 되는 시기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="36519-120">특정 속성 또는 스크립트의 값이 변경 될 때마다 새 그룹이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36519-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="36519-121">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-121">This element is optional.</span></span>

- <span data-ttu-id="36519-122">[Controls](./controls-element-for-view-format.md) 요소는 넓은 뷰로 정의 된 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="36519-123">컨트롤을 통해 데이터 표시 방법을 추가로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="36519-124">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-124">This element is optional.</span></span> <span data-ttu-id="36519-125">뷰는 자체 사용자 지정 컨트롤을 정의 하거나 서식 파일의 뷰에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="36519-126">사용자 지정 컨트롤에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="36519-127">[WideControl](./widecontrol-element-format.md) 요소 및 해당 자식 요소는 뷰에 표시 되는 내용을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="36519-128">위의 예제에서 뷰는 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성을 표시 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="36519-129">간단한 넓은 뷰를 정의 하는 전체 서식 파일의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="36519-130">넓은 보기에 대 한 정의 제공</span><span class="sxs-lookup"><span data-stu-id="36519-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="36519-131">넓은 보기는 [WideControl](./widecontrol-element-format.md) 요소의 자식 요소를 사용 하 여 하나 이상의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="36519-132">일반적으로 보기에는 하나의 정의만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="36519-133">다음 예제에서는 뷰가 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성의 값을 표시 하는 단일 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="36519-134">넓은 보기에는 속성 값 또는 스크립트 값 (예제에는 표시 되지 않음)이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="36519-135">다음 XML 요소를 사용 하 여 넓은 보기에 대 한 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="36519-136">[WideControl](./widecontrol-element-format.md) 요소 및 해당 자식 요소는 뷰에 표시 되는 내용을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="36519-137">[AutoSize](./autosize-element-for-widecontrol-format.md) 요소는 데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="36519-138">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-138">This element is optional.</span></span>

- <span data-ttu-id="36519-139">[Columnnumber](./columnnumber-element-for-widecontrol-format.md) 요소는 넓은 보기에 표시 되는 열 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="36519-140">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-140">This element is optional.</span></span>

- <span data-ttu-id="36519-141">[WideEntries](./wideentries-element-for-widecontrol-format.md) 요소는 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="36519-142">대부분의 경우 보기에는 하나의 정의만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="36519-143">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="36519-143">This element is required.</span></span>

- <span data-ttu-id="36519-144">[WideEntry](./wideentry-element-for-widecontrol-format.md) 요소는 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="36519-145">하나 이상의 [WideEntry](./wideentry-element-for-widecontrol-format.md) 가 필요 합니다. 그러나 추가할 수 있는 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="36519-146">대부분의 경우 보기에는 하나의 정의만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="36519-147">[Entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소는 특정 정의에 의해 표시 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="36519-148">이 요소는 선택 사항이 며 다른 개체를 표시 하는 여러 [WideEntry](./wideentry-element-for-widecontrol-format.md) 요소를 정의 하는 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="36519-149">[WideItem](./wideitem-element-for-widecontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="36519-150">다른 뷰 형식과 달리, 넓은 컨트롤은 하나의 항목만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="36519-151">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소는 값이 뷰에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="36519-152">속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="36519-153">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소는 값이 뷰에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="36519-154">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="36519-155">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 요소는 데이터를 표시 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="36519-156">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-156">This element is optional.</span></span>

<span data-ttu-id="36519-157">넓은 뷰 정의를 정의 하는 전체 서식 파일의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="36519-158">넓은 뷰를 사용 하는 개체 정의</span><span class="sxs-lookup"><span data-stu-id="36519-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="36519-159">넓은 뷰를 사용 하는 .NET 개체를 정의 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="36519-160">[Viewselectedby](./viewselectedby-element-format.md) 요소를 사용 하 여 뷰의 모든 정의에서 표시할 수 있는 개체를 정의 하거나, [entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소를 사용 하 여 뷰의 특정 정의에 표시 되는 개체를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="36519-161">대부분의 경우 뷰에는 정의가 하나만 있으므로 개체는 일반적으로 [Viewselectedby](./viewselectedby-element-format.md) 요소에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36519-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="36519-162">다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 사용 하 여 넓은 뷰로 표시 되는 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36519-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="36519-163">지정할 수 있는 [TypeName](./typename-element-for-viewselectedby-format.md) 요소의 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="36519-164">다음 XML 요소를 사용 하 여 넓은 보기에서 사용 되는 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="36519-165">[Viewselectedby](./viewselectedby-element-format.md) 요소는 넓은 뷰로 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="36519-166">[TypeName](./typename-element-for-viewselectedby-format.md) 요소는 뷰에 표시 되는 .net을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="36519-167">정규화 된 .NET 형식 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="36519-168">뷰에 대해 하나 이상의 유형 또는 선택 집합을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="36519-169">전체 서식 파일의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="36519-170">다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="36519-171">여러 뷰를 사용 하 여 표시 되는 관련 개체 집합을 사용 하는 선택 집합을 사용 합니다. 예를 들어, 동일한 개체에 대 한 넓은 뷰와 테이블 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="36519-172">선택 집합을 만드는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="36519-173">다음 XML 요소를 사용 하 여 넓은 보기에서 사용 되는 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="36519-174">[Viewselectedby](./viewselectedby-element-format.md) 요소는 넓은 뷰로 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="36519-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소는 뷰에서 표시할 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="36519-176">뷰에 대해 하나 이상의 선택 집합 또는 유형을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="36519-177">다음 예제에서는 [Entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소를 사용 하 여 넓은 뷰의 특정 정의에 표시 되는 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36519-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="36519-178">이 요소를 사용 하 여 개체의 .NET 형식 이름, 개체의 선택 집합 또는 정의가 사용 되는 시기를 지정 하는 선택 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="36519-179">선택 조건을 만드는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="36519-180">다음 XML 요소를 사용 하 여 넓은 보기의 특정 정의에 사용 되는 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="36519-181">[Entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소는 정의에 의해 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="36519-182">[TypeName](./typename-element-for-viewselectedby-format.md) 요소는 정의에 의해 표시 되는 .net을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="36519-183">이 요소를 사용 하는 경우 정규화 된 .NET 형식 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="36519-184">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="36519-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 (표시 되지 않음)는이 정의에 의해 표시 될 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="36519-186">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="36519-187">[Selectioncondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) 요소 (표시 되지 않음)는이 정의를 사용 하기 위해 존재 해야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="36519-188">정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="36519-189">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="36519-190">넓은 보기에서 개체 그룹 표시</span><span class="sxs-lookup"><span data-stu-id="36519-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="36519-191">넓은 보기에 표시 되는 개체를 그룹으로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="36519-192">이는 그룹을 정의 하는 것이 아니라 특정 속성이 나 스크립트의 값이 변경 될 때마다 Windows PowerShell이 새 그룹을 시작 한다는 의미는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="36519-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="36519-193">다음 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 값이 변경 될 때마다 새 그룹을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="36519-194">다음 XML 요소는 그룹이 시작 되는 시기를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36519-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="36519-195">[GroupBy](./groupby-element-for-view-format.md) 요소는 새 그룹을 시작 하 고 그룹이 표시 되는 방법을 정의 하는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="36519-196">[PropertyName](./propertyname-element-for-groupby-format.md) 요소는 값이 변경 될 때마다 새 그룹을 시작 하는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="36519-197">그룹을 시작 하려면 속성이 나 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="36519-198">[ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소는 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="36519-199">그룹을 시작 하려면 스크립트나 속성을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="36519-200">[Label](./label-element-for-groupby-format.md) 요소는 각 그룹의 시작 부분에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="36519-201">이 요소에 지정 된 텍스트 외에도 Windows PowerShell은 새 그룹을 트리거한 값을 표시 하 고 레이블 앞뒤에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="36519-202">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-202">This element is optional.</span></span>

- <span data-ttu-id="36519-203">[CustomControl](./customcontrol-element-for-groupby-format.md) 요소는 데이터를 표시 하는 데 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="36519-204">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-204">This element is optional.</span></span>

- <span data-ttu-id="36519-205">[Customcontrolname](./customcontrolname-element-for-groupby-format.md) 요소는 데이터를 표시 하는 데 사용 되는 공용 또는 뷰 컨트롤을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="36519-206">이 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="36519-206">This element is optional.</span></span>

<span data-ttu-id="36519-207">그룹을 정의 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36519-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="36519-208">서식 문자열 사용</span><span class="sxs-lookup"><span data-stu-id="36519-208">Using Format Strings</span></span>

<span data-ttu-id="36519-209">서식 문자열을 넓은 보기에 추가 하 여 데이터가 표시 되는 방법을 추가로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="36519-210">다음 예제에서는 `StartTime` 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36519-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="36519-211">다음 XML 요소를 사용 하 여 형식 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="36519-212">[WideItem](./wideitem-element-for-widecontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="36519-213">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소는 값이 뷰에 표시 되는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="36519-214">속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="36519-215">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 요소는 속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="36519-216">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="36519-217">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="36519-218">다음 예제에서는 스크립트의 값에 대 한 서식을 지정 하기 위해 `ToString` 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="36519-219">스크립트는 개체의 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="36519-220">따라서 개체에 형식 지정 매개 변수가 있는 `ToString`와 같은 메서드가 있는 경우 스크립트는 해당 메서드를 호출 하 여 스크립트의 출력 값에 대 한 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="36519-221">다음 XML 요소를 사용 하 여 `ToString` 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="36519-222">[WideItem](./wideitem-element-for-widecontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="36519-223">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36519-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="36519-224">스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36519-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="36519-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36519-225">See Also</span></span>

[<span data-ttu-id="36519-226">넓은 보기 (기본)</span><span class="sxs-lookup"><span data-stu-id="36519-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="36519-227">넓은 뷰 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="36519-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="36519-228">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="36519-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
