---
title: WideControl (Format)의 AutoSize 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369052"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="ef253-102">WideControl에 대한 AutoSize 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ef253-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="ef253-103">데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef253-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="ef253-104">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View Element (format) WideControl Element (format) Autosize Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ef253-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef253-105">구문</span><span class="sxs-lookup"><span data-stu-id="ef253-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef253-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ef253-106">Attributes and Elements</span></span>

<span data-ttu-id="ef253-107">다음 섹션에서는 `AutoSize` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef253-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef253-108">특성</span><span class="sxs-lookup"><span data-stu-id="ef253-108">Attributes</span></span>

<span data-ttu-id="ef253-109">없음</span><span class="sxs-lookup"><span data-stu-id="ef253-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef253-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ef253-110">Child Elements</span></span>

<span data-ttu-id="ef253-111">없음</span><span class="sxs-lookup"><span data-stu-id="ef253-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef253-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ef253-112">Parent Elements</span></span>

|<span data-ttu-id="ef253-113">요소</span><span class="sxs-lookup"><span data-stu-id="ef253-113">Element</span></span>|<span data-ttu-id="ef253-114">설명</span><span class="sxs-lookup"><span data-stu-id="ef253-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef253-115">WideControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="ef253-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="ef253-116">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef253-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef253-117">설명</span><span class="sxs-lookup"><span data-stu-id="ef253-117">Remarks</span></span>

<span data-ttu-id="ef253-118">넓은 뷰를 정의할 때 `AutoSize` 요소 또는 [Columnnumber](./columnnumber-element-for-widecontrol-format.md) 요소를 추가할 수 있지만 둘 다를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef253-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="ef253-119">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef253-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="ef253-120">넓은 보기의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef253-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef253-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef253-121">See Also</span></span>

[<span data-ttu-id="ef253-122">WideControl에 대 한 ColumnNumber 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ef253-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="ef253-123">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="ef253-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ef253-124">WideControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="ef253-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="ef253-125">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ef253-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
