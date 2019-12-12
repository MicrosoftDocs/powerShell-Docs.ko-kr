---
title: 뷰의 컨트롤에 대 한 CustomItem 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363942"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="c9e50-102">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="c9e50-103">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="c9e50-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c9e50-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for View (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 (형식)에 대 한 CustomEntry 요소의 Customentry 요소</span><span class="sxs-lookup"><span data-stu-id="c9e50-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9e50-106">구문</span><span class="sxs-lookup"><span data-stu-id="c9e50-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9e50-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c9e50-107">Attributes and Elements</span></span>

<span data-ttu-id="c9e50-108">다음 섹션에서는 특성, 자식 요소 및 `CustomItem` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="c9e50-109">자세한 내용은 설명 부분을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9e50-110">특성</span><span class="sxs-lookup"><span data-stu-id="c9e50-110">Attributes</span></span>

<span data-ttu-id="c9e50-111">없음</span><span class="sxs-lookup"><span data-stu-id="c9e50-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9e50-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c9e50-112">Child Elements</span></span>

|<span data-ttu-id="c9e50-113">요소</span><span class="sxs-lookup"><span data-stu-id="c9e50-113">Element</span></span>|<span data-ttu-id="c9e50-114">설명</span><span class="sxs-lookup"><span data-stu-id="c9e50-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9e50-115">뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c9e50-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c9e50-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="c9e50-118">View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c9e50-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c9e50-120">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="c9e50-121">뷰 컨트롤의 CustomItem에 대 한 줄 바꿈 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c9e50-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c9e50-123">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="c9e50-124">뷰 컨트롤의 CustomItem에 대 한 텍스트 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c9e50-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c9e50-126">괄호 또는 대괄호와 같은 텍스트를 컨트롤의 표시에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c9e50-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c9e50-127">Parent Elements</span></span>

|<span data-ttu-id="c9e50-128">요소</span><span class="sxs-lookup"><span data-stu-id="c9e50-128">Element</span></span>|<span data-ttu-id="c9e50-129">설명</span><span class="sxs-lookup"><span data-stu-id="c9e50-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9e50-130">뷰의 컨트롤에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="c9e50-131">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9e50-132">설명</span><span class="sxs-lookup"><span data-stu-id="c9e50-132">Remarks</span></span>

<span data-ttu-id="c9e50-133">`CustomItem` 요소의 자식 요소를 지정할 때는 다음 사항을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="c9e50-134">자식 요소는 `ExpressionBinding`, `NewLine`, `Text`및 `Frame`순서로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="c9e50-135">지정할 수 있는 시퀀스 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="c9e50-136">각 시퀀스에서 사용할 수 있는 `ExpressionBinding` 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e50-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9e50-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9e50-137">See Also</span></span>

[<span data-ttu-id="c9e50-138">뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c9e50-139">View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c9e50-140">뷰 컨트롤의 CustomItem에 대 한 줄 바꿈 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c9e50-141">뷰 컨트롤의 CustomItem에 대 한 텍스트 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c9e50-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c9e50-142">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c9e50-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
