---
title: WideControl (형식)에 대 한 ColumnNumber 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364222"
---
# <a name="columnnumber-element-for-widecontrol-format"></a><span data-ttu-id="30550-102">WideControl에 대한 ColumnNumber 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="30550-102">ColumnNumber Element for WideControl (Format)</span></span>

<span data-ttu-id="30550-103">넓은 보기에 표시 되는 열 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30550-103">Specifies the number of columns displayed in the wide view.</span></span>

<span data-ttu-id="30550-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) ColumnNumber Element for WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="30550-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) ColumnNumber Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="30550-105">구문</span><span class="sxs-lookup"><span data-stu-id="30550-105">Syntax</span></span>

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="30550-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="30550-106">Attributes and Elements</span></span>

<span data-ttu-id="30550-107">다음 섹션에서는 특성, 자식 요소 및 `ColumnNumber` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="30550-107">The following sections describe attributes, child elements, and the parent element of the `ColumnNumber` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="30550-108">특성</span><span class="sxs-lookup"><span data-stu-id="30550-108">Attributes</span></span>

<span data-ttu-id="30550-109">없음</span><span class="sxs-lookup"><span data-stu-id="30550-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="30550-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="30550-110">Child Elements</span></span>

<span data-ttu-id="30550-111">없음</span><span class="sxs-lookup"><span data-stu-id="30550-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="30550-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="30550-112">Parent Elements</span></span>

|<span data-ttu-id="30550-113">요소</span><span class="sxs-lookup"><span data-stu-id="30550-113">Element</span></span>|<span data-ttu-id="30550-114">설명</span><span class="sxs-lookup"><span data-stu-id="30550-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="30550-115">WideControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="30550-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="30550-116">뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="30550-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="30550-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="30550-117">Text Value</span></span>

<span data-ttu-id="30550-118">양의 정수 값을 지정 하십시오.</span><span class="sxs-lookup"><span data-stu-id="30550-118">Specify a positive integer value.</span></span>

## <a name="remarks"></a><span data-ttu-id="30550-119">설명</span><span class="sxs-lookup"><span data-stu-id="30550-119">Remarks</span></span>

<span data-ttu-id="30550-120">넓은 뷰를 정의할 때 `AutoSize` 요소나 `ColumnNumber` 요소를 추가할 수 있지만 둘 다를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30550-120">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` element, but you cannot add both.</span></span>

<span data-ttu-id="30550-121">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30550-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="30550-122">넓은 보기의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30550-122">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30550-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30550-123">See Also</span></span>

[<span data-ttu-id="30550-124">WideControl에 대 한 Autosize 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="30550-124">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="30550-125">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="30550-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="30550-126">넓은 보기 (기본)</span><span class="sxs-lookup"><span data-stu-id="30550-126">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="30550-127">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="30550-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
