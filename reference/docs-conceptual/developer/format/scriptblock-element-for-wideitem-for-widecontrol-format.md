---
title: WideControl (Format)의 WideItem에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362032"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="1feee-102">WideControl의 WideItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1feee-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="1feee-103">넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1feee-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="1feee-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries element (format) WideEntry Element (format) WideItem element (format) ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1feee-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1feee-105">구문</span><span class="sxs-lookup"><span data-stu-id="1feee-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1feee-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1feee-106">Attributes and Elements</span></span>

<span data-ttu-id="1feee-107">다음 섹션에서는 `ScriptBlock` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1feee-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1feee-108">특성</span><span class="sxs-lookup"><span data-stu-id="1feee-108">Attributes</span></span>

<span data-ttu-id="1feee-109">없음</span><span class="sxs-lookup"><span data-stu-id="1feee-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1feee-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1feee-110">Child Elements</span></span>

<span data-ttu-id="1feee-111">없음</span><span class="sxs-lookup"><span data-stu-id="1feee-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1feee-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1feee-112">Parent Elements</span></span>

|<span data-ttu-id="1feee-113">요소</span><span class="sxs-lookup"><span data-stu-id="1feee-113">Element</span></span>|<span data-ttu-id="1feee-114">설명</span><span class="sxs-lookup"><span data-stu-id="1feee-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1feee-115">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1feee-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1feee-116">값이 넓은 뷰에 표시 되는 속성 또는 스크립트 블록을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1feee-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1feee-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1feee-117">Text Value</span></span>

<span data-ttu-id="1feee-118">값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1feee-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1feee-119">설명</span><span class="sxs-lookup"><span data-stu-id="1feee-119">Remarks</span></span>

<span data-ttu-id="1feee-120">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1feee-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1feee-121">예제</span><span class="sxs-lookup"><span data-stu-id="1feee-121">Example</span></span>

<span data-ttu-id="1feee-122">이 예제에서는 값이 뷰에 표시 되는 스크립트를 정의 하는 `WideItem` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1feee-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="1feee-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1feee-123">See Also</span></span>

[<span data-ttu-id="1feee-124">WideItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1feee-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1feee-125">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="1feee-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1feee-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1feee-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
