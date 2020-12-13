---
ms.date: 09/13/2016
ms.topic: reference
title: View 요소(형식)
description: View 요소(형식)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649733"
---
# <a name="view-element-format"></a><span data-ttu-id="cac69-103">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-103">View Element (Format)</span></span>

<span data-ttu-id="cac69-104">하나 이상의 .NET 개체를 표시 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-104">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="cac69-105">서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-105">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="cac69-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="cac69-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cac69-107">구문</span><span class="sxs-lookup"><span data-stu-id="cac69-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="cac69-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cac69-108">Attributes and Elements</span></span>

<span data-ttu-id="cac69-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `View` .</span><span class="sxs-lookup"><span data-stu-id="cac69-109">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="cac69-110">컨트롤 자식 요소 중 하나만 지정 해야 하며 뷰 이름 및 뷰를 사용 하는 개체를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-110">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="cac69-111">사용자 지정 컨트롤을 정의 하 고, 개체를 그룹화 하 고, 뷰가 대역외 인지 여부를 지정 하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-111">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="cac69-112">특성</span><span class="sxs-lookup"><span data-stu-id="cac69-112">Attributes</span></span>

<span data-ttu-id="cac69-113">없음</span><span class="sxs-lookup"><span data-stu-id="cac69-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cac69-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cac69-114">Child Elements</span></span>

|<span data-ttu-id="cac69-115">요소</span><span class="sxs-lookup"><span data-stu-id="cac69-115">Element</span></span>|<span data-ttu-id="cac69-116">설명</span><span class="sxs-lookup"><span data-stu-id="cac69-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cac69-117">View에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-117">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="cac69-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cac69-119">뷰 내에서 이름으로 참조할 수 있는 컨트롤의 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-119">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="cac69-120">CustomControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="cac69-120">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="cac69-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cac69-122">뷰의 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-122">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="cac69-123">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-123">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="cac69-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cac69-125">.NET 개체의 멤버를 그룹화 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-125">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="cac69-126">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-126">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="cac69-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-127">Optional element.</span></span><br /><br /> <span data-ttu-id="cac69-128">뷰의 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-128">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="cac69-129">View에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-129">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="cac69-130">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-130">Required element.</span></span><br /><br /> <span data-ttu-id="cac69-131">뷰를 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-131">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="cac69-132">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-132">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="cac69-133">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-133">Optional element.</span></span><br /><br /> <span data-ttu-id="cac69-134">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-134">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="cac69-135">보기에 대 한 ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-135">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="cac69-136">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-136">Required element.</span></span><br /><br /> <span data-ttu-id="cac69-137">이 뷰가 표시 하는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-137">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="cac69-138">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-138">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="cac69-139">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-139">Optional element.</span></span><br /><br /> <span data-ttu-id="cac69-140">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-140">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cac69-141">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cac69-141">Parent Elements</span></span>

|<span data-ttu-id="cac69-142">요소</span><span class="sxs-lookup"><span data-stu-id="cac69-142">Element</span></span>|<span data-ttu-id="cac69-143">설명</span><span class="sxs-lookup"><span data-stu-id="cac69-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cac69-144">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-144">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="cac69-145">개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-145">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cac69-146">설명</span><span class="sxs-lookup"><span data-stu-id="cac69-146">Remarks</span></span>

<span data-ttu-id="cac69-147">다양 한 보기 및 사용자 지정 컨트롤의 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cac69-147">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="cac69-148">테이블 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="cac69-148">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="cac69-149">목록 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="cac69-149">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="cac69-150">넓은 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="cac69-150">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="cac69-151">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="cac69-151">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="cac69-152">예제</span><span class="sxs-lookup"><span data-stu-id="cac69-152">Example</span></span>

<span data-ttu-id="cac69-153">이 예에서는 `View` [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cac69-153">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cac69-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cac69-154">See Also</span></span>

[<span data-ttu-id="cac69-155">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-155">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="cac69-156">View에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-156">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="cac69-157">ViewSelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-157">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="cac69-158">View에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-158">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="cac69-159">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-159">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="cac69-160">TableControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-160">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="cac69-161">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-161">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="cac69-162">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cac69-162">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="cac69-163">CustomControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="cac69-163">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="cac69-164">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="cac69-164">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
