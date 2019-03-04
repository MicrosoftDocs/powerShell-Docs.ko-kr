---
title: 넓은 보기 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858499"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="12d5a-102">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="12d5a-102">Creating a Wide View</span></span>

<span data-ttu-id="12d5a-103">넓은 보기가 표시 되는 각 개체에 대 한 단일 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="12d5a-104">표시 된 값은.NET 개체 속성의 값 또는 스크립트의 값 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="12d5a-105">기본적으로 레이블 또는이 보기에 대 한 헤더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="12d5a-106">넓은 보기 표시</span><span class="sxs-lookup"><span data-stu-id="12d5a-106">A Wide View Display</span></span>

<span data-ttu-id="12d5a-107">다음 예제에서는 Windows PowerShell의 표시 하는 방법을 보여 줍니다.는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 에서 반환 되는 개체를 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet의 출력을 [ Format-wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12d5a-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="12d5a-108">(기본적으로 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 테이블 뷰를 반환 합니다.) 이 예제에서는 두 열은 반환 된 각 개체에 대 한 프로세스의 이름을 표시 하려면 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="12d5a-109">개체의 속성의 이름을 표시 되지 않으면 속성의 값만 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="12d5a-110">넓은 보기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-110">Defining the Wide View</span></span>

<span data-ttu-id="12d5a-111">다음 XML의 넓은 보기 스키마를 표시 합니다 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="12d5a-112">다음 XML 요소를 와이드 뷰를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="12d5a-113">합니다 [보기](./view-element-format.md) 요소는 부모 요소를 와이드 보기인 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="12d5a-114">(테이블, 목록 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="12d5a-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="12d5a-115">합니다 [이름을](./name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="12d5a-116">이 요소는 모든 보기에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-116">This element is required for all views.</span></span>

- <span data-ttu-id="12d5a-117">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 뷰를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="12d5a-118">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="12d5a-118">This element is required.</span></span>

- <span data-ttu-id="12d5a-119">합니다 [GroupBy](./groupby-element-for-view-format.md) 요소 개체의 새 그룹을 표시 될 때를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="12d5a-120">새 그룹을 특정 속성이 나 스크립트의 값이 변경 될 때마다 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="12d5a-121">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-121">This element is optional.</span></span>

- <span data-ttu-id="12d5a-122">합니다 [컨트롤](./controls-element-for-view-format.md) 요소 넓은 보기에서 정의한 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="12d5a-123">컨트롤 추가 데이터가 표시 되는 방식을 지정 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="12d5a-124">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-124">This element is optional.</span></span> <span data-ttu-id="12d5a-125">뷰 자체 사용자 지정 컨트롤을 정의 하거나 형식 지정 파일의 보기 중 하나에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="12d5a-126">사용자 지정 컨트롤에 대 한 자세한 내용은 참조 하세요. [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="12d5a-127">합니다 [WideControl](./widecontrol-element-format.md) 요소와 해당 자식 요소 보기에 표시 되는 항목을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="12d5a-128">앞의 예제에서 뷰를 표시 하도록 디자인 된 [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="12d5a-129">간단한 넓은 보기가 정의 하는 전체 서식 파일의 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="12d5a-130">넓은 보기에 대 한 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="12d5a-131">와이드 뷰가의 자식 요소를 사용 하 여 하나 이상의 정의 제공할 수는 [WideControl](./widecontrol-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="12d5a-132">일반적으로 뷰를 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="12d5a-133">다음 예제에서 보기의 값을 표시 하는 단일 정의 제공 합니다 [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="12d5a-134">속성의 값 또는 값 (이 예제에 표시 되지 않음) 스크립트의 넓은 보기를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="12d5a-135">넓은 보기에 대 한 정의 제공 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="12d5a-136">합니다 [WideControl](./widecontrol-element-format.md) 요소와 해당 자식 요소 보기에 표시 되는 항목을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="12d5a-137">합니다 [AutoSize](./autosize-element-for-widecontrol-format.md) 조정 여부를 열 크기 및 열 개수는 데이터의 크기를 기준으로 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="12d5a-138">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-138">This element is optional.</span></span>

- <span data-ttu-id="12d5a-139">합니다 [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) 요소 넓은 보기에 표시 된 열의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="12d5a-140">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-140">This element is optional.</span></span>

- <span data-ttu-id="12d5a-141">합니다 [WideEntries](./wideentries-element-for-widecontrol-format.md) 요소는 뷰의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="12d5a-142">대부분의 경우에서 뷰를 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="12d5a-143">필수적 요소로,</span><span class="sxs-lookup"><span data-stu-id="12d5a-143">This element is required.</span></span>

- <span data-ttu-id="12d5a-144">합니다 [WideEntry](./wideentry-element-for-widecontrol-format.md) 요소 뷰의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="12d5a-145">하나 이상의 [WideEntry](./wideentry-element-for-widecontrol-format.md) 필수 사항입니다; 그러나는 추가할 수 있는 요소의 수를 최대 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="12d5a-146">대부분의 경우에서 뷰를 하나만 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="12d5a-147">합니다 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 요소는 특정 정의 의해 표시 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="12d5a-148">이 요소는 선택 사항이 며 여러 개를 정의 하는 경우에 필요 [WideEntry](./wideentry-element-for-widecontrol-format.md) 다른 개체를 표시 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="12d5a-149">합니다 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="12d5a-150">다른 유형의 보기와 달리 와이드 컨트롤 항목을 하나만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="12d5a-151">합니다 [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소 보기에서 해당 값이 표시 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="12d5a-152">속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="12d5a-153">합니다 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="12d5a-154">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="12d5a-155">합니다 [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 요소 데이터를 표시 하는 데 사용 되는 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="12d5a-156">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-156">This element is optional.</span></span>

<span data-ttu-id="12d5a-157">넓은 보기 정의 정의 하는 전체 서식 파일의 예제를 보려면 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="12d5a-158">넓은 보기를 사용 하는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="12d5a-159">넓은 보기를 사용 하 여.NET 개체를 정의 하는 방법은 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="12d5a-160">사용할 수는 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의의 보기를 통해 표시 될 수 있는 개체 정의를 사용할 수는 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 정의 개체를 표시 하는 요소는 특정 뷰의 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="12d5a-161">대부분의 경우에서 보기 있으므로 하나만 정의 하 여 개체는 일반적으로 정의 된 [ViewSelectedBy](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="12d5a-162">다음 예제에서는 와이드 보기인 경우 사용 하 여 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [TypeName](./typename-element-for-viewselectedby-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="12d5a-163">수에 제한이 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 지정 하 고 해당 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="12d5a-164">넓은 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="12d5a-165">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 넓은 보기에서 표시 되는 객체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="12d5a-166">합니다 [TypeName](./typename-element-for-viewselectedby-format.md) 요소 보기에 표시 되는.NET을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="12d5a-167">정규화 된.NET 유형 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="12d5a-168">하나 이상의 형식 또는 선택이 보기에 대 한 설정 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="12d5a-169">전체 서식 파일의 예제를 보려면 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="12d5a-170">다음 예제에서는 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="12d5a-171">관련된 넓은 보기를 정의 하는 경우와 같은 여러 뷰와 테이블 뷰를 사용 하 여 동일한 개체에 대해 표시 되는 개체 집합이 있는 선택 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="12d5a-172">선택 영역 집합을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [선택 집합 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="12d5a-173">넓은 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="12d5a-174">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 넓은 보기에서 표시 되는 객체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="12d5a-175">합니다 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 보기에서 표시할 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="12d5a-176">하나 이상 선택 집합 또는 보기에 대 한 형식을 지정 해야 하지만 지정할 수 있는 요소의 최대 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="12d5a-177">다음 예제에서는 사용 하 여 와이드 보기인 경우 특정 정의 의해 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="12d5a-178">이 요소를 사용 하 여, 개체, 개체 집합을 선택 또는 선택 조건 정의 사용 하는 경우를 지정 하는.NET 형식 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="12d5a-179">선택 조건을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="12d5a-180">넓은 보기 특정 정의에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="12d5a-181">합니다 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 요소 정의 의해 표시 되는 객체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="12d5a-182">합니다 [TypeName](./typename-element-for-viewselectedby-format.md) 요소 정의 의해 표시 되는.NET을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="12d5a-183">이 요소를 사용 하는 경우 정규화 된.NET 유형 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="12d5a-184">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="12d5a-185">합니다 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 (표시 되지 않음)이이 정의 의해 표시 될 수 있는 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="12d5a-186">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="12d5a-187">합니다 [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) 요소 (표시 되지 않음)이이 정의를 사용할 수 있어야 하는 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="12d5a-188">하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="12d5a-189">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="12d5a-190">넓은 보기에서 개체의 그룹 표시</span><span class="sxs-lookup"><span data-stu-id="12d5a-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="12d5a-191">그룹으로 넓은 보기에 표시 되는 개체를 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="12d5a-192">그렇다고 그룹을 정의 하는 Windows PowerShell 스크립트 또는 특정 속성의 값이 변경 될 때마다 새 그룹을 시작만 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="12d5a-193">다음 예제에서는 새 그룹을 시작 됩니다 때마다 값은 [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="12d5a-194">다음 XML 요소가 그룹 시작 될 때를 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="12d5a-195">합니다 [GroupBy](./groupby-element-for-view-format.md) 속성 또는 새 그룹을 시작 하 고 그룹 표시 되는 방식을 정의 하는 스크립트 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="12d5a-196">합니다 [PropertyName](./propertyname-element-for-groupby-format.md) 요소 값이 변경 될 때마다 새 그룹을 시작 하는 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="12d5a-197">속성 또는 그룹을 시작 하는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="12d5a-198">합니다 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소는 해당 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="12d5a-199">스크립트 또는 그룹을 시작 하는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="12d5a-200">합니다 [레이블](./label-element-for-groupby-format.md) 요소는 각 그룹의 시작 부분에 표시 되는 레이블을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="12d5a-201">이 요소에 의해 지정 된 텍스트를 외에도 Windows PowerShell에는 새 그룹 트리거되고 레이블을 전후에 빈 줄을 추가 하는 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="12d5a-202">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-202">This element is optional.</span></span>

- <span data-ttu-id="12d5a-203">합니다 [CustomControl](./customcontrol-element-for-groupby-format.md) 요소에는 데이터를 표시 하는 데 사용 되는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="12d5a-204">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-204">This element is optional.</span></span>

- <span data-ttu-id="12d5a-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md) 요소 지정 일반적인 보거나 데이터를 표시 하는 데 사용 되는 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="12d5a-206">이 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-206">This element is optional.</span></span>

<span data-ttu-id="12d5a-207">그룹을 정의 하는 전체 서식 파일의 예제를 보려면 [넓은 보기 (GroupBy)](./wide-view-groupby.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="12d5a-208">서식 문자열 사용</span><span class="sxs-lookup"><span data-stu-id="12d5a-208">Using Format Strings</span></span>

<span data-ttu-id="12d5a-209">데이터 표시 되는 방법을 추가로 정의할 넓은 보기로 서식 문자열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="12d5a-210">다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="12d5a-211">다음 XML 요소가 형식 패턴을 지정 하려면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="12d5a-212">합니다 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="12d5a-213">합니다 [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소 보기에서 해당 값이 표시 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="12d5a-214">속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="12d5a-215">합니다 [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 스크립트나 속성 값을 보기에 표시 되는 방식을 정의 하는 형식 패턴을 지정 하는 요소</span><span class="sxs-lookup"><span data-stu-id="12d5a-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="12d5a-216">합니다 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음) 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="12d5a-217">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="12d5a-218">다음 예제에서는 `ToString` 메서드를 호출 하는 스크립트의 값의 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="12d5a-219">스크립트 개체의 모든 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="12d5a-220">따라서 개체에 있는 경우 메서드를 같은 `ToString`형식 매개 변수가 있는, 스크립트는 스크립트의 출력 값의 서식을 지정 하는 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="12d5a-221">호출 하는 다음 XML 요소를 사용할 수는 `ToString` 메서드:</span><span class="sxs-lookup"><span data-stu-id="12d5a-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="12d5a-222">합니다 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="12d5a-223">합니다 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음) 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="12d5a-224">스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12d5a-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="12d5a-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12d5a-225">See Also</span></span>

[<span data-ttu-id="12d5a-226">넓은 보기 (Basic)</span><span class="sxs-lookup"><span data-stu-id="12d5a-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="12d5a-227">넓은 보기 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="12d5a-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="12d5a-228">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="12d5a-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
