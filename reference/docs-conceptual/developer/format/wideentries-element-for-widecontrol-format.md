---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl에 대한 WideEntries 요소(형식)
description: WideControl에 대한 WideEntries 요소(형식)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651237"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="189c9-103">WideControl에 대한 WideEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="189c9-103">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="189c9-104">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="189c9-104">Provides the definitions of the wide view.</span></span> <span data-ttu-id="189c9-105">넓은 보기는 하나 이상의 정의를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="189c9-105">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="189c9-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="189c9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="189c9-107">구문</span><span class="sxs-lookup"><span data-stu-id="189c9-107">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="189c9-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="189c9-108">Attributes and Elements</span></span>

<span data-ttu-id="189c9-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `WideEntries` .</span><span class="sxs-lookup"><span data-stu-id="189c9-109">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="189c9-110">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="189c9-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="189c9-111">특성</span><span class="sxs-lookup"><span data-stu-id="189c9-111">Attributes</span></span>

<span data-ttu-id="189c9-112">없음</span><span class="sxs-lookup"><span data-stu-id="189c9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="189c9-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="189c9-113">Child Elements</span></span>

|<span data-ttu-id="189c9-114">요소</span><span class="sxs-lookup"><span data-stu-id="189c9-114">Element</span></span>|<span data-ttu-id="189c9-115">설명</span><span class="sxs-lookup"><span data-stu-id="189c9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="189c9-116">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="189c9-116">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="189c9-117">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="189c9-117">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="189c9-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="189c9-118">Parent Elements</span></span>

|<span data-ttu-id="189c9-119">요소</span><span class="sxs-lookup"><span data-stu-id="189c9-119">Element</span></span>|<span data-ttu-id="189c9-120">설명</span><span class="sxs-lookup"><span data-stu-id="189c9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="189c9-121">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="189c9-121">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="189c9-122">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="189c9-122">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="189c9-123">설명</span><span class="sxs-lookup"><span data-stu-id="189c9-123">Remarks</span></span>

<span data-ttu-id="189c9-124">넓은 보기는 각 개체에 대 한 단일 속성 값 또는 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="189c9-124">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="189c9-125">넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide View 구성 요소](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="189c9-125">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="189c9-126">예제</span><span class="sxs-lookup"><span data-stu-id="189c9-126">Example</span></span>

<span data-ttu-id="189c9-127">다음 예제에서는 `WideEntries` 단일 요소를 정의 하는 요소를 보여 줍니다 `WideEntry` .</span><span class="sxs-lookup"><span data-stu-id="189c9-127">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="189c9-128">`WideEntry`요소는 `WideItem` 뷰에 표시 되는 속성 또는 스크립트 값을 정의 하는 단일 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="189c9-128">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="189c9-129">넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="189c9-129">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="189c9-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="189c9-130">See Also</span></span>

[<span data-ttu-id="189c9-131">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="189c9-131">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="189c9-132">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="189c9-132">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="189c9-133">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="189c9-133">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="189c9-134">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="189c9-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
