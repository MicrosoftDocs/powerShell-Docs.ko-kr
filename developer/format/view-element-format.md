---
title: 보기 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083725"
---
# <a name="view-element-format"></a><span data-ttu-id="90fbf-102">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-102">View Element (Format)</span></span>

<span data-ttu-id="90fbf-103">하나 이상의.NET 개체를 표시 하는 보기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="90fbf-104">서식 파일에 정의 될 수 있는 뷰의 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="90fbf-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90fbf-106">구문</span><span class="sxs-lookup"><span data-stu-id="90fbf-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90fbf-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-107">Attributes and Elements</span></span>

<span data-ttu-id="90fbf-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `View` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="90fbf-109">컨트롤 자식 요소를 하나만 지정 해야 하며 뷰와 뷰를 사용 하는 개체의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="90fbf-110">사용자 지정 컨트롤을 정의 그룹화 하는 방법을 개체 및 있으면 뷰는 대역을 지정 하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="90fbf-111">특성</span><span class="sxs-lookup"><span data-stu-id="90fbf-111">Attributes</span></span>

<span data-ttu-id="90fbf-112">없음</span><span class="sxs-lookup"><span data-stu-id="90fbf-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90fbf-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-113">Child Elements</span></span>

|<span data-ttu-id="90fbf-114">요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-114">Element</span></span>|<span data-ttu-id="90fbf-115">설명</span><span class="sxs-lookup"><span data-stu-id="90fbf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90fbf-116">뷰 (형식)에 대 한 controls 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="90fbf-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-117">Optional element.</span></span><br /><br /> <span data-ttu-id="90fbf-118">뷰 내에서 이름으로 참조할 수 있는 컨트롤의 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="90fbf-119">CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="90fbf-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-120">Optional element.</span></span><br /><br /> <span data-ttu-id="90fbf-121">뷰에 대 한 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="90fbf-122">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="90fbf-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-123">Optional element.</span></span><br /><br /> <span data-ttu-id="90fbf-124">.NET 개체 멤버의 그룹화 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="90fbf-125">ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="90fbf-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-126">Optional element.</span></span><br /><br /> <span data-ttu-id="90fbf-127">뷰를 목록 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="90fbf-128">뷰 (형식)의 name 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="90fbf-129">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-129">Required element.</span></span><br /><br /> <span data-ttu-id="90fbf-130">뷰를 참조 하는 데 사용 하는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="90fbf-131">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="90fbf-132">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-132">Optional element.</span></span><br /><br /> <span data-ttu-id="90fbf-133">뷰에 대 한 테이블 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="90fbf-134">뷰 (형식)에 대 한 ViewSelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="90fbf-135">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-135">Required element.</span></span><br /><br /> <span data-ttu-id="90fbf-136">이 보기를 표시 하는.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="90fbf-137">WideControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="90fbf-138">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-138">Optional element.</span></span><br /><br /> <span data-ttu-id="90fbf-139">와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90fbf-140">부모 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-140">Parent Elements</span></span>

|<span data-ttu-id="90fbf-141">요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-141">Element</span></span>|<span data-ttu-id="90fbf-142">설명</span><span class="sxs-lookup"><span data-stu-id="90fbf-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90fbf-143">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="90fbf-144">개체를 표시 하는 데 사용 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90fbf-145">설명</span><span class="sxs-lookup"><span data-stu-id="90fbf-145">Remarks</span></span>

<span data-ttu-id="90fbf-146">다른 보기와 사용자 지정 컨트롤의 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="90fbf-147">테이블 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="90fbf-148">목록 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="90fbf-149">와이드 보기인 경우 구성 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="90fbf-150">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="90fbf-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="90fbf-151">예제</span><span class="sxs-lookup"><span data-stu-id="90fbf-151">Example</span></span>

<span data-ttu-id="90fbf-152">보여 주는이 예제는 `View` 테이블 뷰를 정의 하는 요소는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="90fbf-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="90fbf-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90fbf-153">See Also</span></span>

[<span data-ttu-id="90fbf-154">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="90fbf-155">뷰 (형식)의 name 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="90fbf-156">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="90fbf-157">뷰 (형식)에 대 한 controls 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="90fbf-158">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="90fbf-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="90fbf-159">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="90fbf-160">ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="90fbf-161">WideControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="90fbf-162">CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="90fbf-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="90fbf-163">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="90fbf-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
