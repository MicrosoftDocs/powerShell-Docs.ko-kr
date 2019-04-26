---
title: WideItem 요소 WideControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083640"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="20de1-102">WideControl에 대한 WideItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20de1-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="20de1-103">속성 또는 해당 값이 표시 되는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="20de1-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) WideItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="20de1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20de1-105">구문</span><span class="sxs-lookup"><span data-stu-id="20de1-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20de1-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-106">Attributes and Elements</span></span>

<span data-ttu-id="20de1-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="20de1-108">`FormatString` 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="20de1-109">그러나 지정 해야 합니다는 `PropertyName` 또는 `ScriptBlock` 있지만 요소를 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="20de1-110">특성</span><span class="sxs-lookup"><span data-stu-id="20de1-110">Attributes</span></span>

<span data-ttu-id="20de1-111">없음</span><span class="sxs-lookup"><span data-stu-id="20de1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20de1-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-112">Child Elements</span></span>

|<span data-ttu-id="20de1-113">요소</span><span class="sxs-lookup"><span data-stu-id="20de1-113">Element</span></span>|<span data-ttu-id="20de1-114">설명</span><span class="sxs-lookup"><span data-stu-id="20de1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20de1-115">WideControl (형식)에 대 한 WideItem FormatString 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="20de1-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="20de1-117">속성 또는 스크립트 값 보기에 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="20de1-118">WideItem (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="20de1-119">값은 넓은 보기에서 표시 된 개체의 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="20de1-120">WideItem (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="20de1-121">값을 갖는 넓은 보기에 표시 됩니다 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20de1-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-122">Parent Elements</span></span>

|<span data-ttu-id="20de1-123">요소</span><span class="sxs-lookup"><span data-stu-id="20de1-123">Element</span></span>|<span data-ttu-id="20de1-124">설명</span><span class="sxs-lookup"><span data-stu-id="20de1-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20de1-125">WideEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="20de1-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="20de1-126">넓은 보기의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20de1-127">설명</span><span class="sxs-lookup"><span data-stu-id="20de1-127">Remarks</span></span>

<span data-ttu-id="20de1-128">넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [와이드 보기인 경우](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="20de1-129">예제</span><span class="sxs-lookup"><span data-stu-id="20de1-129">Example</span></span>

<span data-ttu-id="20de1-130">에서는 다음 예제는 `WideEntry` 단일 정의 하는 요소 `WideItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="20de1-131">`WideItem` 속성 또는 값 보기에 표시 되는 스크립트 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="20de1-132">넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="20de1-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20de1-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20de1-133">See Also</span></span>

[<span data-ttu-id="20de1-134">WideControl (형식)에 대 한 WideItem FormatString 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="20de1-135">WideItem (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="20de1-136">WideItem (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="20de1-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="20de1-137">WideEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="20de1-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="20de1-138">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="20de1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
