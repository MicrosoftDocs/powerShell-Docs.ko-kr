---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl에 대한 WideEntry 요소(형식)
description: WideControl에 대한 WideEntry 요소(형식)
ms.openlocfilehash: 3faaf767d11914792effd6765beed956a502c642
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664554"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="663a7-103">WideControl에 대한 WideEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="663a7-103">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="663a7-104">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-104">Provides a definition of the wide view.</span></span>

<span data-ttu-id="663a7-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="663a7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="663a7-106">구문</span><span class="sxs-lookup"><span data-stu-id="663a7-106">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="663a7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="663a7-107">Attributes and Elements</span></span>

<span data-ttu-id="663a7-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `WideEntry` .</span><span class="sxs-lookup"><span data-stu-id="663a7-108">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="663a7-109">단일 자식 요소를 지정 해야 합니다 `WideItem` .</span><span class="sxs-lookup"><span data-stu-id="663a7-109">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="663a7-110">특성</span><span class="sxs-lookup"><span data-stu-id="663a7-110">Attributes</span></span>

<span data-ttu-id="663a7-111">없음</span><span class="sxs-lookup"><span data-stu-id="663a7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="663a7-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="663a7-112">Child Elements</span></span>

|<span data-ttu-id="663a7-113">요소</span><span class="sxs-lookup"><span data-stu-id="663a7-113">Element</span></span>|<span data-ttu-id="663a7-114">설명</span><span class="sxs-lookup"><span data-stu-id="663a7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="663a7-115">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="663a7-115">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="663a7-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="663a7-117">이 정의를 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목 정의를 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-117">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="663a7-118">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="663a7-118">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="663a7-119">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-119">Required element.</span></span><br /><br /> <span data-ttu-id="663a7-120">값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-120">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="663a7-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="663a7-121">Parent Elements</span></span>

|<span data-ttu-id="663a7-122">요소</span><span class="sxs-lookup"><span data-stu-id="663a7-122">Element</span></span>|<span data-ttu-id="663a7-123">설명</span><span class="sxs-lookup"><span data-stu-id="663a7-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="663a7-124">WideEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="663a7-124">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="663a7-125">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-125">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="663a7-126">설명</span><span class="sxs-lookup"><span data-stu-id="663a7-126">Remarks</span></span>

<span data-ttu-id="663a7-127">넓은 보기는 각 개체에 대 한 단일 속성 값 또는 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-127">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="663a7-128">다른 보기 유형과 달리 각 뷰 정의에는 item 요소를 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-128">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="663a7-129">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="663a7-129">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="663a7-130">예제</span><span class="sxs-lookup"><span data-stu-id="663a7-130">Example</span></span>

<span data-ttu-id="663a7-131">다음 예제에서는 `WideEntry` 단일 요소를 정의 하는 요소를 보여 줍니다 `WideItem` .</span><span class="sxs-lookup"><span data-stu-id="663a7-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="663a7-132">`WideItem`요소는 값이 뷰에 표시 되는 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="663a7-132">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="663a7-133">넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="663a7-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="663a7-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="663a7-134">See Also</span></span>

[<span data-ttu-id="663a7-135">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="663a7-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="663a7-136">WideEntry에 대 한 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="663a7-136">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="663a7-137">WideEntry에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="663a7-137">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="663a7-138">WideEntry에 대 한 TypeName 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="663a7-138">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="663a7-139">WideEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="663a7-139">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="663a7-140">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="663a7-140">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="663a7-141">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="663a7-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
