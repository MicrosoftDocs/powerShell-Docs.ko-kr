---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855609"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="0fd50-102">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0fd50-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="0fd50-103">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="0fd50-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="0fd50-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry 보기 (형식)에 대 한 컨트롤에 대 한 보기 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="0fd50-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0fd50-106">구문</span><span class="sxs-lookup"><span data-stu-id="0fd50-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0fd50-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-107">Attributes and Elements</span></span>

<span data-ttu-id="0fd50-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="0fd50-109">자세한 내용은 설명 부분을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="0fd50-110">특성</span><span class="sxs-lookup"><span data-stu-id="0fd50-110">Attributes</span></span>

<span data-ttu-id="0fd50-111">없음</span><span class="sxs-lookup"><span data-stu-id="0fd50-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0fd50-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-112">Child Elements</span></span>

|<span data-ttu-id="0fd50-113">요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-113">Element</span></span>|<span data-ttu-id="0fd50-114">설명</span><span class="sxs-lookup"><span data-stu-id="0fd50-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fd50-115">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0fd50-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0fd50-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="0fd50-118">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0fd50-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0fd50-120">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="0fd50-121">줄 바꿈 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0fd50-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-122">Optional element.</span></span><br /><br /> <span data-ttu-id="0fd50-123">컨트롤의 표시에 빈 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="0fd50-124">텍스트 보기 (형식)에 대 한 컨트롤에 대 한 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="0fd50-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0fd50-126">컨트롤의 표시에 대괄호 또는 괄호와 같은 텍스트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0fd50-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-127">Parent Elements</span></span>

|<span data-ttu-id="0fd50-128">요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-128">Element</span></span>|<span data-ttu-id="0fd50-129">설명</span><span class="sxs-lookup"><span data-stu-id="0fd50-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fd50-130">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="0fd50-131">컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0fd50-132">설명</span><span class="sxs-lookup"><span data-stu-id="0fd50-132">Remarks</span></span>

<span data-ttu-id="0fd50-133">자식 요소를 지정 하는 경우는 `CustomItem` 요소를 다음 염두 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="0fd50-134">다음 순서 대로 자식 요소를 추가 해야 합니다. `ExpressionBinding`, `NewLine`를 `Text`, 및 `Frame`합니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="0fd50-135">지정할 수 있는 시퀀스의 수는 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="0fd50-136">각 시퀀스에는 수의 최대 제한이 `ExpressionBinding` 사용할 수 있는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0fd50-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fd50-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fd50-137">See Also</span></span>

[<span data-ttu-id="0fd50-138">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0fd50-139">뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0fd50-140">줄 바꿈 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0fd50-141">텍스트 보기 (형식)에 대 한 컨트롤에 대 한 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="0fd50-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="0fd50-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="0fd50-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
