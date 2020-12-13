---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)
description: View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)
ms.openlocfilehash: 67bff97c27cfedf046b17eea438efcd66ae2ee4a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666759"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="d69c7-103">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-103">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="d69c7-104">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-104">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="d69c7-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d69c7-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤의 컨트롤 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소 (format) Customentries 요소에 대 한 컨트롤의 CustomEntries 요소에 대 한 컨트롤의 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="d69c7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d69c7-107">구문</span><span class="sxs-lookup"><span data-stu-id="d69c7-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d69c7-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d69c7-108">Attributes and Elements</span></span>

<span data-ttu-id="d69c7-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomItem` .</span><span class="sxs-lookup"><span data-stu-id="d69c7-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="d69c7-110">자세한 내용은 설명 부분을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d69c7-110">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="d69c7-111">특성</span><span class="sxs-lookup"><span data-stu-id="d69c7-111">Attributes</span></span>

<span data-ttu-id="d69c7-112">없음</span><span class="sxs-lookup"><span data-stu-id="d69c7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d69c7-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d69c7-113">Child Elements</span></span>

|<span data-ttu-id="d69c7-114">요소</span><span class="sxs-lookup"><span data-stu-id="d69c7-114">Element</span></span>|<span data-ttu-id="d69c7-115">설명</span><span class="sxs-lookup"><span data-stu-id="d69c7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d69c7-116">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="d69c7-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d69c7-118">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-118">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="d69c7-119">View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-119">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="d69c7-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d69c7-121">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-121">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="d69c7-122">View에 대한 Controls의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-122">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="d69c7-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d69c7-124">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-124">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="d69c7-125">View에 대한 Controls의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-125">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="d69c7-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d69c7-127">괄호 또는 대괄호와 같은 텍스트를 컨트롤의 표시에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-127">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d69c7-128">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d69c7-128">Parent Elements</span></span>

|<span data-ttu-id="d69c7-129">요소</span><span class="sxs-lookup"><span data-stu-id="d69c7-129">Element</span></span>|<span data-ttu-id="d69c7-130">설명</span><span class="sxs-lookup"><span data-stu-id="d69c7-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d69c7-131">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-131">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="d69c7-132">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-132">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d69c7-133">설명</span><span class="sxs-lookup"><span data-stu-id="d69c7-133">Remarks</span></span>

<span data-ttu-id="d69c7-134">요소의 자식 요소를 지정할 때는 `CustomItem` 다음 사항을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-134">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="d69c7-135">자식 요소는 `ExpressionBinding` ,, `NewLine` `Text` 및 순서로 추가 되어야 `Frame` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-135">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="d69c7-136">지정할 수 있는 시퀀스 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d69c7-136">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="d69c7-137">각 시퀀스에는 사용할 수 있는 최대 요소 수에 대 한 제한이 없습니다 `ExpressionBinding` .</span><span class="sxs-lookup"><span data-stu-id="d69c7-137">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="d69c7-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d69c7-138">See Also</span></span>

[<span data-ttu-id="d69c7-139">View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-139">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d69c7-140">View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-140">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d69c7-141">View에 대한 Controls의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-141">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d69c7-142">View에 대한 Controls의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d69c7-142">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d69c7-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d69c7-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
