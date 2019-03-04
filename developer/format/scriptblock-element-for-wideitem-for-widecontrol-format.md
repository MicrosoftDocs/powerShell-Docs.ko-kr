---
title: ScriptBlock 요소 WideControl (형식)에 대 한 WideItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858029"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="fccc4-102">WideControl의 WideItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fccc4-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="fccc4-103">값을 갖는 넓은 보기에 표시 됩니다 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fccc4-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="fccc4-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) WideItem 요소 (형식) ScriptBlock 요소 WideItem (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="fccc4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fccc4-105">구문</span><span class="sxs-lookup"><span data-stu-id="fccc4-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fccc4-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fccc4-106">Attributes and Elements</span></span>

<span data-ttu-id="fccc4-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fccc4-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fccc4-108">특성</span><span class="sxs-lookup"><span data-stu-id="fccc4-108">Attributes</span></span>

<span data-ttu-id="fccc4-109">없음</span><span class="sxs-lookup"><span data-stu-id="fccc4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fccc4-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fccc4-110">Child Elements</span></span>

<span data-ttu-id="fccc4-111">없음</span><span class="sxs-lookup"><span data-stu-id="fccc4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fccc4-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fccc4-112">Parent Elements</span></span>

|<span data-ttu-id="fccc4-113">요소</span><span class="sxs-lookup"><span data-stu-id="fccc4-113">Element</span></span>|<span data-ttu-id="fccc4-114">설명</span><span class="sxs-lookup"><span data-stu-id="fccc4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fccc4-115">WideItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fccc4-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="fccc4-116">값을 갖는 넓은 보기에 표시 됩니다 속성 또는 스크립트 블록을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fccc4-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fccc4-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="fccc4-117">Text Value</span></span>

<span data-ttu-id="fccc4-118">해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fccc4-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="fccc4-119">설명</span><span class="sxs-lookup"><span data-stu-id="fccc4-119">Remarks</span></span>

<span data-ttu-id="fccc4-120">넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fccc4-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fccc4-121">예제</span><span class="sxs-lookup"><span data-stu-id="fccc4-121">Example</span></span>

<span data-ttu-id="fccc4-122">이 예제는 `WideItem` 값인 보기에 표시 되는 스크립트를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fccc4-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="fccc4-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fccc4-123">See Also</span></span>

[<span data-ttu-id="fccc4-124">WideItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="fccc4-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="fccc4-125">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="fccc4-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fccc4-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="fccc4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
