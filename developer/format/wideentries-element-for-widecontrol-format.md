---
title: WideEntries 요소 WideControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853279"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="7018d-102">WideControl에 대한 WideEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7018d-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="7018d-103">넓은 보기의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="7018d-104">와이드 보기인 경우 하나 이상의 정의 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="7018d-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7018d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7018d-106">구문</span><span class="sxs-lookup"><span data-stu-id="7018d-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7018d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7018d-107">Attributes and Elements</span></span>

<span data-ttu-id="7018d-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideEntries` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="7018d-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7018d-110">특성</span><span class="sxs-lookup"><span data-stu-id="7018d-110">Attributes</span></span>

<span data-ttu-id="7018d-111">없음</span><span class="sxs-lookup"><span data-stu-id="7018d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7018d-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7018d-112">Child Elements</span></span>

|<span data-ttu-id="7018d-113">요소</span><span class="sxs-lookup"><span data-stu-id="7018d-113">Element</span></span>|<span data-ttu-id="7018d-114">설명</span><span class="sxs-lookup"><span data-stu-id="7018d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7018d-115">WideEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7018d-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="7018d-116">넓은 보기의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7018d-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7018d-117">Parent Elements</span></span>

|<span data-ttu-id="7018d-118">요소</span><span class="sxs-lookup"><span data-stu-id="7018d-118">Element</span></span>|<span data-ttu-id="7018d-119">설명</span><span class="sxs-lookup"><span data-stu-id="7018d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7018d-120">WideControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7018d-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="7018d-121">와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7018d-122">설명</span><span class="sxs-lookup"><span data-stu-id="7018d-122">Remarks</span></span>

<span data-ttu-id="7018d-123">와이드 보기인 경우에 단일 속성 값 또는 각 개체에 대 한 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="7018d-124">넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [뷰 구성 요소를 와이드](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7018d-125">예제</span><span class="sxs-lookup"><span data-stu-id="7018d-125">Example</span></span>

<span data-ttu-id="7018d-126">에서는 다음 예제는 `WideEntries` 단일 정의 하는 요소 `WideEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="7018d-127">합니다 `WideEntry` 하나를 포함 하는 요소 `WideItem` 뷰에서 어떤 스크립트나 속성 값이 표시를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="7018d-128">넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7018d-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7018d-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7018d-129">See Also</span></span>

[<span data-ttu-id="7018d-130">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="7018d-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7018d-131">WideControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7018d-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="7018d-132">WideEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7018d-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="7018d-133">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="7018d-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
