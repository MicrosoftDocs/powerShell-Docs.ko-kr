---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl에 대한 WideItem 요소(형식)
description: WideControl에 대한 WideItem 요소(형식)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647810"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="ece5c-103">WideControl에 대한 WideItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ece5c-103">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="ece5c-104">값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-104">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="ece5c-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries element (format) WideEntry Element (format) WideItem Element (format)</span><span class="sxs-lookup"><span data-stu-id="ece5c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ece5c-106">구문</span><span class="sxs-lookup"><span data-stu-id="ece5c-106">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ece5c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ece5c-107">Attributes and Elements</span></span>

<span data-ttu-id="ece5c-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `WideItem` .</span><span class="sxs-lookup"><span data-stu-id="ece5c-108">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="ece5c-109">`FormatString` 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-109">The `FormatString` element is optional.</span></span> <span data-ttu-id="ece5c-110">그러나 또는 요소를 지정 해야 `PropertyName` `ScriptBlock` 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-110">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="ece5c-111">특성</span><span class="sxs-lookup"><span data-stu-id="ece5c-111">Attributes</span></span>

<span data-ttu-id="ece5c-112">없음</span><span class="sxs-lookup"><span data-stu-id="ece5c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ece5c-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ece5c-113">Child Elements</span></span>

|<span data-ttu-id="ece5c-114">요소</span><span class="sxs-lookup"><span data-stu-id="ece5c-114">Element</span></span>|<span data-ttu-id="ece5c-115">설명</span><span class="sxs-lookup"><span data-stu-id="ece5c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ece5c-116">WideControl의 WideItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ece5c-116">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="ece5c-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ece5c-118">속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-118">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="ece5c-119">WideItem에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ece5c-119">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="ece5c-120">넓은 보기에 값이 표시 되는 개체의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-120">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="ece5c-121">WideItem에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ece5c-121">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="ece5c-122">넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-122">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ece5c-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ece5c-123">Parent Elements</span></span>

|<span data-ttu-id="ece5c-124">요소</span><span class="sxs-lookup"><span data-stu-id="ece5c-124">Element</span></span>|<span data-ttu-id="ece5c-125">설명</span><span class="sxs-lookup"><span data-stu-id="ece5c-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ece5c-126">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="ece5c-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="ece5c-127">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ece5c-128">설명</span><span class="sxs-lookup"><span data-stu-id="ece5c-128">Remarks</span></span>

<span data-ttu-id="ece5c-129">넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ece5c-129">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ece5c-130">예제</span><span class="sxs-lookup"><span data-stu-id="ece5c-130">Example</span></span>

<span data-ttu-id="ece5c-131">다음 예제에서는 `WideEntry` 단일 요소를 정의 하는 요소를 보여 줍니다 `WideItem` .</span><span class="sxs-lookup"><span data-stu-id="ece5c-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="ece5c-132">`WideItem`요소는 값이 뷰에 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece5c-132">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="ece5c-133">넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ece5c-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ece5c-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ece5c-134">See Also</span></span>

[<span data-ttu-id="ece5c-135">WideControl의 WideItem에 대한 FormatString 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ece5c-135">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="ece5c-136">WideItem에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ece5c-136">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="ece5c-137">WideItem에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ece5c-137">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="ece5c-138">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="ece5c-138">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="ece5c-139">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ece5c-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
