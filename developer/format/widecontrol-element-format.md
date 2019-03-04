---
title: WideControl 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859829"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="4ba2e-102">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-102">WideControl Element (Format)</span></span>

<span data-ttu-id="4ba2e-103">와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="4ba2e-104">이 보기에는 단일 속성 값 또는 각 개체에 대 한 스크립트 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="4ba2e-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ba2e-106">구문</span><span class="sxs-lookup"><span data-stu-id="4ba2e-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ba2e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4ba2e-107">Attributes and Elements</span></span>

<span data-ttu-id="4ba2e-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideControl` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="4ba2e-109">지정할 수 없습니다는 `AutoSize` 및 `ColumnNumber` 동시 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ba2e-110">특성</span><span class="sxs-lookup"><span data-stu-id="4ba2e-110">Attributes</span></span>

<span data-ttu-id="4ba2e-111">없음</span><span class="sxs-lookup"><span data-stu-id="4ba2e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ba2e-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4ba2e-112">Child Elements</span></span>

|<span data-ttu-id="4ba2e-113">요소</span><span class="sxs-lookup"><span data-stu-id="4ba2e-113">Element</span></span>|<span data-ttu-id="4ba2e-114">설명</span><span class="sxs-lookup"><span data-stu-id="4ba2e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ba2e-115">WideControl (형식)에 대 한 자동 크기 조정 요소</span><span class="sxs-lookup"><span data-stu-id="4ba2e-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="4ba2e-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4ba2e-117">조정 여부를 열 크기 및 열 개수는 데이터의 크기를 기준으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="4ba2e-118">ColumnNumber 요소 WideControl (형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="4ba2e-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4ba2e-120">넓은 보기에 표시 된 열의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="4ba2e-121">WideEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="4ba2e-122">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-122">Required element.</span></span><br /><br /> <span data-ttu-id="4ba2e-123">넓은 보기의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4ba2e-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4ba2e-124">Parent Elements</span></span>

|<span data-ttu-id="4ba2e-125">요소</span><span class="sxs-lookup"><span data-stu-id="4ba2e-125">Element</span></span>|<span data-ttu-id="4ba2e-126">설명</span><span class="sxs-lookup"><span data-stu-id="4ba2e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ba2e-127">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4ba2e-128">하나 이상의.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4ba2e-129">설명</span><span class="sxs-lookup"><span data-stu-id="4ba2e-129">Remarks</span></span>

<span data-ttu-id="4ba2e-130">넓은 보기를 정의 하는 경우 추가할 수 있습니다 합니다 `AutoSize` 요소 또는 `ColumnNumber` 있지만 둘 다를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="4ba2e-131">대부분의 경우에서 하나만 정의 각 넓은 보기가에 대 한 필수 이지만 다른.NET 개체를 표시 하려면 같은 뷰를 사용 하려는 경우 정의가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="4ba2e-132">이러한 경우 각 개체 또는 개체 집합에 대 한 별도 정의 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="4ba2e-133">넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [뷰 구성 요소를 와이드](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4ba2e-134">예제</span><span class="sxs-lookup"><span data-stu-id="4ba2e-134">Example</span></span>

<span data-ttu-id="4ba2e-135">에서는 다음 예제는 `WideControl` 의 속성을 표시 하는 데 사용 되는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="4ba2e-136">넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4ba2e-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ba2e-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ba2e-137">See Also</span></span>

[<span data-ttu-id="4ba2e-138">WideControl (형식)에 대 한 자동 크기 조정 요소</span><span class="sxs-lookup"><span data-stu-id="4ba2e-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="4ba2e-139">ColumnNumber 요소 WideControl (형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="4ba2e-140">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="4ba2e-141">WideEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="4ba2e-142">넓은 보기 (Basic)</span><span class="sxs-lookup"><span data-stu-id="4ba2e-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="4ba2e-143">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="4ba2e-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4ba2e-144">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="4ba2e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
