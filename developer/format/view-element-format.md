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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856149"
---
# <a name="view-element-format"></a><span data-ttu-id="b4e44-102">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-102">View Element (Format)</span></span>

<span data-ttu-id="b4e44-103">하나 이상의.NET 개체를 표시 하는 보기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="b4e44-104">서식 파일에 정의 될 수 있는 뷰의 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="b4e44-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4e44-106">구문</span><span class="sxs-lookup"><span data-stu-id="b4e44-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b4e44-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-107">Attributes and Elements</span></span>

<span data-ttu-id="b4e44-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `View` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="b4e44-109">컨트롤 자식 요소를 하나만 지정 해야 하며 뷰와 뷰를 사용 하는 개체의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="b4e44-110">사용자 지정 컨트롤을 정의 그룹화 하는 방법을 개체 및 있으면 뷰는 대역을 지정 하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4e44-111">특성</span><span class="sxs-lookup"><span data-stu-id="b4e44-111">Attributes</span></span>

<span data-ttu-id="b4e44-112">없음</span><span class="sxs-lookup"><span data-stu-id="b4e44-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4e44-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-113">Child Elements</span></span>

|<span data-ttu-id="b4e44-114">요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-114">Element</span></span>|<span data-ttu-id="b4e44-115">설명</span><span class="sxs-lookup"><span data-stu-id="b4e44-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4e44-116">뷰 (형식)에 대 한 controls 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="b4e44-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e44-118">뷰 내에서 이름으로 참조할 수 있는 컨트롤의 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="b4e44-119">CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="b4e44-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e44-121">뷰에 대 한 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="b4e44-122">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="b4e44-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e44-124">.NET 개체 멤버의 그룹화 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="b4e44-125">ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="b4e44-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e44-127">뷰를 목록 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="b4e44-128">뷰 (형식)의 name 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="b4e44-129">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-129">Required element.</span></span><br /><br /> <span data-ttu-id="b4e44-130">뷰를 참조 하는 데 사용 하는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="b4e44-131">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="b4e44-132">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-132">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e44-133">뷰에 대 한 테이블 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="b4e44-134">뷰 (형식)에 대 한 ViewSelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="b4e44-135">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-135">Required element.</span></span><br /><br /> <span data-ttu-id="b4e44-136">이 보기를 표시 하는.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="b4e44-137">WideControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="b4e44-138">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-138">Optional element.</span></span><br /><br /> <span data-ttu-id="b4e44-139">와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4e44-140">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-140">Parent Elements</span></span>

|<span data-ttu-id="b4e44-141">요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-141">Element</span></span>|<span data-ttu-id="b4e44-142">설명</span><span class="sxs-lookup"><span data-stu-id="b4e44-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4e44-143">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="b4e44-144">개체를 표시 하는 데 사용 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4e44-145">설명</span><span class="sxs-lookup"><span data-stu-id="b4e44-145">Remarks</span></span>

<span data-ttu-id="b4e44-146">다른 보기와 사용자 지정 컨트롤의 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="b4e44-147">테이블 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="b4e44-148">목록 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="b4e44-149">와이드 보기인 경우 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="b4e44-150">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="b4e44-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="b4e44-151">예제</span><span class="sxs-lookup"><span data-stu-id="b4e44-151">Example</span></span>

<span data-ttu-id="b4e44-152">보여 주는이 예제는 `View` 테이블 뷰를 정의 하는 요소는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e44-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4e44-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4e44-153">See Also</span></span>

[<span data-ttu-id="b4e44-154">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="b4e44-155">뷰 (형식)의 name 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="b4e44-156">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="b4e44-157">뷰 (형식)에 대 한 controls 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="b4e44-158">뷰 (형식)에 대 한 GroupBy 요소</span><span class="sxs-lookup"><span data-stu-id="b4e44-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="b4e44-159">TableControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="b4e44-160">ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="b4e44-161">WideControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="b4e44-162">CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4e44-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="b4e44-163">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="b4e44-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
