---
title: WideControl에 대 한 WideEntry 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367902"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="8aa8a-102">WideControl에 대한 WideEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="8aa8a-103">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="8aa8a-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8aa8a-105">구문</span><span class="sxs-lookup"><span data-stu-id="8aa8a-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8aa8a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8aa8a-106">Attributes and Elements</span></span>

<span data-ttu-id="8aa8a-107">다음 섹션에서는 특성, 자식 요소 및 `WideEntry` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="8aa8a-108">단일 `WideItem` 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8aa8a-109">특성</span><span class="sxs-lookup"><span data-stu-id="8aa8a-109">Attributes</span></span>

<span data-ttu-id="8aa8a-110">없음</span><span class="sxs-lookup"><span data-stu-id="8aa8a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8aa8a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8aa8a-111">Child Elements</span></span>

|<span data-ttu-id="8aa8a-112">요소</span><span class="sxs-lookup"><span data-stu-id="8aa8a-112">Element</span></span>|<span data-ttu-id="8aa8a-113">설명</span><span class="sxs-lookup"><span data-stu-id="8aa8a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8aa8a-114">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="8aa8a-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="8aa8a-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8aa8a-116">이 정의를 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목 정의를 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="8aa8a-117">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="8aa8a-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-118">Required element.</span></span><br /><br /> <span data-ttu-id="8aa8a-119">값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8aa8a-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8aa8a-120">Parent Elements</span></span>

|<span data-ttu-id="8aa8a-121">요소</span><span class="sxs-lookup"><span data-stu-id="8aa8a-121">Element</span></span>|<span data-ttu-id="8aa8a-122">설명</span><span class="sxs-lookup"><span data-stu-id="8aa8a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8aa8a-123">WideEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="8aa8a-124">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8aa8a-125">설명</span><span class="sxs-lookup"><span data-stu-id="8aa8a-125">Remarks</span></span>

<span data-ttu-id="8aa8a-126">넓은 보기는 각 개체에 대 한 단일 속성 값 또는 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="8aa8a-127">다른 보기 유형과 달리 각 뷰 정의에는 item 요소를 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="8aa8a-128">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8aa8a-129">예제</span><span class="sxs-lookup"><span data-stu-id="8aa8a-129">Example</span></span>

<span data-ttu-id="8aa8a-130">다음 예제에서는 단일 `WideItem` 요소를 정의 하는 `WideEntry` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="8aa8a-131">`WideItem` 요소는 값이 뷰에 표시 되는 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="8aa8a-132">넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8aa8a-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8aa8a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8aa8a-133">See Also</span></span>

[<span data-ttu-id="8aa8a-134">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="8aa8a-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8aa8a-135">WideEntry에 대 한 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8aa8a-136">WideEntry에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8aa8a-137">WideEntry에 대 한 TypeName 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="8aa8a-138">WideEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="8aa8a-139">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8aa8a-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="8aa8a-140">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8aa8a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
