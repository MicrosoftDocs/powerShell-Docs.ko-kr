---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 WideItem에 대한 ScriptBlock 요소(형식)
description: WideControl의 WideItem에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: 68e47926e5e6b846c8a0a3dbc16d1f0d59f11dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659880"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="20493-103">WideControl의 WideItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="20493-103">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="20493-104">넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20493-104">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="20493-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries element (format) WideEntry Element (format) WideItem element (format) ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="20493-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20493-106">구문</span><span class="sxs-lookup"><span data-stu-id="20493-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20493-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="20493-107">Attributes and Elements</span></span>

<span data-ttu-id="20493-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="20493-108">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20493-109">특성</span><span class="sxs-lookup"><span data-stu-id="20493-109">Attributes</span></span>

<span data-ttu-id="20493-110">없음</span><span class="sxs-lookup"><span data-stu-id="20493-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20493-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="20493-111">Child Elements</span></span>

<span data-ttu-id="20493-112">없음</span><span class="sxs-lookup"><span data-stu-id="20493-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20493-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="20493-113">Parent Elements</span></span>

|<span data-ttu-id="20493-114">요소</span><span class="sxs-lookup"><span data-stu-id="20493-114">Element</span></span>|<span data-ttu-id="20493-115">설명</span><span class="sxs-lookup"><span data-stu-id="20493-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20493-116">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="20493-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="20493-117">값이 넓은 뷰에 표시 되는 속성 또는 스크립트 블록을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="20493-117">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="20493-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="20493-118">Text Value</span></span>

<span data-ttu-id="20493-119">값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20493-119">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="20493-120">설명</span><span class="sxs-lookup"><span data-stu-id="20493-120">Remarks</span></span>

<span data-ttu-id="20493-121">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="20493-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="20493-122">예제</span><span class="sxs-lookup"><span data-stu-id="20493-122">Example</span></span>

<span data-ttu-id="20493-123">이 예제에서는 `WideItem` 값이 뷰에 표시 되는 스크립트를 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20493-123">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="20493-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20493-124">See Also</span></span>

[<span data-ttu-id="20493-125">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="20493-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="20493-126">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="20493-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="20493-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="20493-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
