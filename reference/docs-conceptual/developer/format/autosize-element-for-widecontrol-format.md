---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl에 대한 AutoSize 요소(형식)
description: WideControl에 대한 AutoSize 요소(형식)
ms.openlocfilehash: 42dfae337ba8805e1ddcff4269401afdb3e281f6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650011"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="ad962-103">WideControl에 대한 AutoSize 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ad962-103">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="ad962-104">데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad962-104">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="ad962-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View Element (format) WideControl Element (format) Autosize Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ad962-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad962-106">구문</span><span class="sxs-lookup"><span data-stu-id="ad962-106">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad962-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ad962-107">Attributes and Elements</span></span>

<span data-ttu-id="ad962-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `AutoSize` .</span><span class="sxs-lookup"><span data-stu-id="ad962-108">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad962-109">특성</span><span class="sxs-lookup"><span data-stu-id="ad962-109">Attributes</span></span>

<span data-ttu-id="ad962-110">없음</span><span class="sxs-lookup"><span data-stu-id="ad962-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad962-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ad962-111">Child Elements</span></span>

<span data-ttu-id="ad962-112">없음</span><span class="sxs-lookup"><span data-stu-id="ad962-112">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad962-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ad962-113">Parent Elements</span></span>

|<span data-ttu-id="ad962-114">요소</span><span class="sxs-lookup"><span data-stu-id="ad962-114">Element</span></span>|<span data-ttu-id="ad962-115">설명</span><span class="sxs-lookup"><span data-stu-id="ad962-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad962-116">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ad962-116">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="ad962-117">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad962-117">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ad962-118">설명</span><span class="sxs-lookup"><span data-stu-id="ad962-118">Remarks</span></span>

<span data-ttu-id="ad962-119">넓은 뷰를 정의할 때는 `AutoSize` 요소나 [columnnumber](./columnnumber-element-for-widecontrol-format.md) 요소를 추가할 수 있지만 둘 다를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad962-119">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="ad962-120">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad962-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="ad962-121">넓은 보기의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad962-121">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad962-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad962-122">See Also</span></span>

[<span data-ttu-id="ad962-123">WideControl에 대한 ColumnNumber 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ad962-123">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="ad962-124">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ad962-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ad962-125">WideControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ad962-125">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="ad962-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ad962-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
