---
title: WideEntry 요소 WideControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856529"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="df484-102">WideControl에 대한 WideEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="df484-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="df484-103">넓은 보기의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="df484-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="df484-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="df484-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="df484-105">구문</span><span class="sxs-lookup"><span data-stu-id="df484-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df484-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="df484-106">Attributes and Elements</span></span>

<span data-ttu-id="df484-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="df484-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="df484-108">단일 지정 해야 `WideItem` 자식 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="df484-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="df484-109">특성</span><span class="sxs-lookup"><span data-stu-id="df484-109">Attributes</span></span>

<span data-ttu-id="df484-110">없음</span><span class="sxs-lookup"><span data-stu-id="df484-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="df484-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="df484-111">Child Elements</span></span>

|<span data-ttu-id="df484-112">요소</span><span class="sxs-lookup"><span data-stu-id="df484-112">Element</span></span>|<span data-ttu-id="df484-113">설명</span><span class="sxs-lookup"><span data-stu-id="df484-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df484-114">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="df484-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="df484-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="df484-115">Optional element.</span></span><br /><br /> <span data-ttu-id="df484-116">이 와이드 항목 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="df484-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="df484-117">WideItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="df484-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="df484-118">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="df484-118">Required element.</span></span><br /><br /> <span data-ttu-id="df484-119">속성 또는 해당 값이 표시 되는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="df484-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="df484-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="df484-120">Parent Elements</span></span>

|<span data-ttu-id="df484-121">요소</span><span class="sxs-lookup"><span data-stu-id="df484-121">Element</span></span>|<span data-ttu-id="df484-122">설명</span><span class="sxs-lookup"><span data-stu-id="df484-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df484-123">WideEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="df484-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="df484-124">넓은 보기의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="df484-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="df484-125">설명</span><span class="sxs-lookup"><span data-stu-id="df484-125">Remarks</span></span>

<span data-ttu-id="df484-126">와이드 보기인 경우에 단일 속성 값 또는 각 개체에 대 한 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="df484-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="df484-127">뷰의 다른 형식과 달리 각 뷰 정의 대해 하나의 항목 요소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df484-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="df484-128">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="df484-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="df484-129">예제</span><span class="sxs-lookup"><span data-stu-id="df484-129">Example</span></span>

<span data-ttu-id="df484-130">에서는 다음 예제는 `WideEntry` 단일 정의 하는 요소 `WideItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="df484-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="df484-131">`WideItem` 요소 값은 뷰에 표시 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="df484-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="df484-132">넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="df484-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df484-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df484-133">See Also</span></span>

[<span data-ttu-id="df484-134">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="df484-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="df484-135">WideEntry (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="df484-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="df484-136">WideEntry (형식)에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="df484-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="df484-137">WideEntry (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="df484-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="df484-138">WideEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="df484-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="df484-139">WideItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="df484-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="df484-140">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="df484-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
