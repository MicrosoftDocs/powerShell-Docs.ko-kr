---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 요소(형식)
description: WideControl 요소(형식)
ms.openlocfilehash: f88e1ce18f87e5e47de473298b3ecf070b71c192
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651273"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="751c2-103">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="751c2-103">WideControl Element (Format)</span></span>

<span data-ttu-id="751c2-104">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-104">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="751c2-105">이 보기에는 각 개체에 대 한 단일 속성 값 또는 스크립트 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-105">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="751c2-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="751c2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="751c2-107">구문</span><span class="sxs-lookup"><span data-stu-id="751c2-107">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="751c2-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="751c2-108">Attributes and Elements</span></span>

<span data-ttu-id="751c2-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `WideControl` .</span><span class="sxs-lookup"><span data-stu-id="751c2-109">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="751c2-110">및 요소를 동시에 지정할 수 없습니다 `AutoSize` `ColumnNumber` .</span><span class="sxs-lookup"><span data-stu-id="751c2-110">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="751c2-111">특성</span><span class="sxs-lookup"><span data-stu-id="751c2-111">Attributes</span></span>

<span data-ttu-id="751c2-112">없음</span><span class="sxs-lookup"><span data-stu-id="751c2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="751c2-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="751c2-113">Child Elements</span></span>

|<span data-ttu-id="751c2-114">요소</span><span class="sxs-lookup"><span data-stu-id="751c2-114">Element</span></span>|<span data-ttu-id="751c2-115">설명</span><span class="sxs-lookup"><span data-stu-id="751c2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="751c2-116">WideControl에 대한 AutoSize 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="751c2-116">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="751c2-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="751c2-118">데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="751c2-119">WideControl에 대한 ColumnNumber 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="751c2-119">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="751c2-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="751c2-121">넓은 보기에 표시 되는 열 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-121">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="751c2-122">WideEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="751c2-122">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="751c2-123">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-123">Required element.</span></span><br /><br /> <span data-ttu-id="751c2-124">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-124">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="751c2-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="751c2-125">Parent Elements</span></span>

|<span data-ttu-id="751c2-126">요소</span><span class="sxs-lookup"><span data-stu-id="751c2-126">Element</span></span>|<span data-ttu-id="751c2-127">설명</span><span class="sxs-lookup"><span data-stu-id="751c2-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="751c2-128">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="751c2-128">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="751c2-129">하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-129">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="751c2-130">설명</span><span class="sxs-lookup"><span data-stu-id="751c2-130">Remarks</span></span>

<span data-ttu-id="751c2-131">넓은 뷰를 정의할 때는 `AutoSize` 요소 또는를 추가할 수 `ColumnNumber` 있지만 둘 다를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-131">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="751c2-132">대부분의 경우 각 넓은 뷰에 대해 정의가 하나만 필요 하지만 동일한 뷰를 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-132">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="751c2-133">이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-133">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="751c2-134">넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide View 구성 요소](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="751c2-134">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="751c2-135">예제</span><span class="sxs-lookup"><span data-stu-id="751c2-135">Example</span></span>

<span data-ttu-id="751c2-136">다음 예제에서는 `WideControl` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 표시 하는 데 사용 되는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="751c2-136">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="751c2-137">넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="751c2-137">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="751c2-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="751c2-138">See Also</span></span>

[<span data-ttu-id="751c2-139">WideControl에 대 한 Autosize 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="751c2-139">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="751c2-140">WideControl에 대한 ColumnNumber 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="751c2-140">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="751c2-141">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="751c2-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="751c2-142">WideEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="751c2-142">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="751c2-143">넓게 보기(기본)</span><span class="sxs-lookup"><span data-stu-id="751c2-143">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="751c2-144">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="751c2-144">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="751c2-145">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="751c2-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
