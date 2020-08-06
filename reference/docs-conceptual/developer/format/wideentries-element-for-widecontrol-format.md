---
title: WideControl에 대 한 WideEntries 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785050"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="fa084-102">WideControl에 대한 WideEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fa084-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="fa084-103">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa084-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="fa084-104">넓은 보기는 하나 이상의 정의를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa084-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="fa084-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fa084-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa084-106">구문</span><span class="sxs-lookup"><span data-stu-id="fa084-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa084-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fa084-107">Attributes and Elements</span></span>

<span data-ttu-id="fa084-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `WideEntries` .</span><span class="sxs-lookup"><span data-stu-id="fa084-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="fa084-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa084-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa084-110">특성</span><span class="sxs-lookup"><span data-stu-id="fa084-110">Attributes</span></span>

<span data-ttu-id="fa084-111">없음</span><span class="sxs-lookup"><span data-stu-id="fa084-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa084-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fa084-112">Child Elements</span></span>

|<span data-ttu-id="fa084-113">요소</span><span class="sxs-lookup"><span data-stu-id="fa084-113">Element</span></span>|<span data-ttu-id="fa084-114">설명</span><span class="sxs-lookup"><span data-stu-id="fa084-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa084-115">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="fa084-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="fa084-116">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa084-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fa084-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fa084-117">Parent Elements</span></span>

|<span data-ttu-id="fa084-118">요소</span><span class="sxs-lookup"><span data-stu-id="fa084-118">Element</span></span>|<span data-ttu-id="fa084-119">설명</span><span class="sxs-lookup"><span data-stu-id="fa084-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa084-120">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fa084-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="fa084-121">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa084-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fa084-122">설명</span><span class="sxs-lookup"><span data-stu-id="fa084-122">Remarks</span></span>

<span data-ttu-id="fa084-123">넓은 보기는 각 개체에 대 한 단일 속성 값 또는 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="fa084-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="fa084-124">넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide View 구성 요소](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa084-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fa084-125">예제</span><span class="sxs-lookup"><span data-stu-id="fa084-125">Example</span></span>

<span data-ttu-id="fa084-126">다음 예제에서는 `WideEntries` 단일 요소를 정의 하는 요소를 보여 줍니다 `WideEntry` .</span><span class="sxs-lookup"><span data-stu-id="fa084-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="fa084-127">`WideEntry`요소는 `WideItem` 뷰에 표시 되는 속성 또는 스크립트 값을 정의 하는 단일 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa084-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="fa084-128">넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa084-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa084-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa084-129">See Also</span></span>

[<span data-ttu-id="fa084-130">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="fa084-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fa084-131">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fa084-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="fa084-132">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="fa084-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="fa084-133">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fa084-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
