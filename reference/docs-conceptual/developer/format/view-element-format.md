---
title: View 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361462"
---
# <a name="view-element-format"></a><span data-ttu-id="b334f-102">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b334f-102">View Element (Format)</span></span>

<span data-ttu-id="b334f-103">하나 이상의 .NET 개체를 표시 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="b334f-104">서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="b334f-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b334f-106">구문</span><span class="sxs-lookup"><span data-stu-id="b334f-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b334f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b334f-107">Attributes and Elements</span></span>

<span data-ttu-id="b334f-108">다음 섹션에서는 특성, 자식 요소 및 `View` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="b334f-109">컨트롤 자식 요소 중 하나만 지정 해야 하며 뷰 이름 및 뷰를 사용 하는 개체를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="b334f-110">사용자 지정 컨트롤을 정의 하 고, 개체를 그룹화 하 고, 뷰가 대역외 인지 여부를 지정 하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="b334f-111">특성</span><span class="sxs-lookup"><span data-stu-id="b334f-111">Attributes</span></span>

<span data-ttu-id="b334f-112">없음</span><span class="sxs-lookup"><span data-stu-id="b334f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b334f-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b334f-113">Child Elements</span></span>

|<span data-ttu-id="b334f-114">요소</span><span class="sxs-lookup"><span data-stu-id="b334f-114">Element</span></span>|<span data-ttu-id="b334f-115">설명</span><span class="sxs-lookup"><span data-stu-id="b334f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b334f-116">View 요소에 대 한 Controls 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="b334f-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b334f-118">뷰 내에서 이름으로 참조할 수 있는 컨트롤의 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="b334f-119">CustomControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="b334f-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b334f-121">뷰의 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="b334f-122">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b334f-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="b334f-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b334f-124">.NET 개체의 멤버를 그룹화 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="b334f-125">이 listcontrol 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="b334f-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b334f-127">뷰의 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="b334f-128">View의 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="b334f-129">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-129">Required element.</span></span><br /><br /> <span data-ttu-id="b334f-130">뷰를 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="b334f-131">TableControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="b334f-132">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-132">Optional element.</span></span><br /><br /> <span data-ttu-id="b334f-133">뷰의 테이블 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="b334f-134">보기에 대 한 ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b334f-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="b334f-135">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-135">Required element.</span></span><br /><br /> <span data-ttu-id="b334f-136">이 뷰가 표시 하는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="b334f-137">WideControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="b334f-138">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-138">Optional element.</span></span><br /><br /> <span data-ttu-id="b334f-139">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b334f-140">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b334f-140">Parent Elements</span></span>

|<span data-ttu-id="b334f-141">요소</span><span class="sxs-lookup"><span data-stu-id="b334f-141">Element</span></span>|<span data-ttu-id="b334f-142">설명</span><span class="sxs-lookup"><span data-stu-id="b334f-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b334f-143">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b334f-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="b334f-144">개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b334f-145">설명</span><span class="sxs-lookup"><span data-stu-id="b334f-145">Remarks</span></span>

<span data-ttu-id="b334f-146">다양 한 보기 및 사용자 지정 컨트롤의 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b334f-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="b334f-147">테이블 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b334f-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="b334f-148">목록 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b334f-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="b334f-149">넓은 뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b334f-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="b334f-150">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="b334f-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="b334f-151">예제</span><span class="sxs-lookup"><span data-stu-id="b334f-151">Example</span></span>

<span data-ttu-id="b334f-152">이 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 `View` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b334f-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b334f-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b334f-153">See Also</span></span>

[<span data-ttu-id="b334f-154">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b334f-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="b334f-155">View의 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="b334f-156">ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b334f-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="b334f-157">View 요소에 대 한 Controls 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="b334f-158">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b334f-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="b334f-159">TableControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="b334f-160">이 listcontrol 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="b334f-161">WideControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="b334f-162">CustomControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b334f-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="b334f-163">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b334f-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
