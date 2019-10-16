---
title: WideControl에 대 한 WideItem 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361402"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="891be-102">WideControl에 대한 WideItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="891be-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="891be-103">값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="891be-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="891be-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries element (format) WideEntry Element (format) WideItem Element (format)</span><span class="sxs-lookup"><span data-stu-id="891be-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="891be-105">구문</span><span class="sxs-lookup"><span data-stu-id="891be-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="891be-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="891be-106">Attributes and Elements</span></span>

<span data-ttu-id="891be-107">다음 섹션에서는 `WideItem` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="891be-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="891be-108">@No__t-0 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="891be-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="891be-109">그러나 `PropertyName` 또는 `ScriptBlock` 요소를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="891be-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="891be-110">특성</span><span class="sxs-lookup"><span data-stu-id="891be-110">Attributes</span></span>

<span data-ttu-id="891be-111">없음</span><span class="sxs-lookup"><span data-stu-id="891be-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="891be-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="891be-112">Child Elements</span></span>

|<span data-ttu-id="891be-113">요소</span><span class="sxs-lookup"><span data-stu-id="891be-113">Element</span></span>|<span data-ttu-id="891be-114">설명</span><span class="sxs-lookup"><span data-stu-id="891be-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="891be-115">WideControl의 WideItem에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="891be-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="891be-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="891be-116">Optional element.</span></span><br /><br /> <span data-ttu-id="891be-117">속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="891be-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="891be-118">WideItem에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="891be-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="891be-119">넓은 보기에 값이 표시 되는 개체의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="891be-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="891be-120">WideItem에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="891be-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="891be-121">넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="891be-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="891be-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="891be-122">Parent Elements</span></span>

|<span data-ttu-id="891be-123">요소</span><span class="sxs-lookup"><span data-stu-id="891be-123">Element</span></span>|<span data-ttu-id="891be-124">설명</span><span class="sxs-lookup"><span data-stu-id="891be-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="891be-125">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="891be-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="891be-126">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="891be-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="891be-127">설명</span><span class="sxs-lookup"><span data-stu-id="891be-127">Remarks</span></span>

<span data-ttu-id="891be-128">넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="891be-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="891be-129">예제</span><span class="sxs-lookup"><span data-stu-id="891be-129">Example</span></span>

<span data-ttu-id="891be-130">다음 예에서는 단일 `WideItem` 요소를 정의 하는 `WideEntry` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="891be-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="891be-131">@No__t-0 요소는 값이 뷰에 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="891be-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="891be-132">넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="891be-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="891be-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="891be-133">See Also</span></span>

[<span data-ttu-id="891be-134">WideControl의 WideItem에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="891be-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="891be-135">WideItem에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="891be-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="891be-136">WideItem에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="891be-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="891be-137">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="891be-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="891be-138">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="891be-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
