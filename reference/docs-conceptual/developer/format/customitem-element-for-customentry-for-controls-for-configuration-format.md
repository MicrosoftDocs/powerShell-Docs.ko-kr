---
title: 구성에 대 한 컨트롤 Customitem의 CustomItem 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bb8124242496f192717127f201674bc1428e5de0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785866"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="fd71f-102">Configuration에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="fd71f-103">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="fd71f-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="fd71f-105">Configuration 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤의 요소 구성 (format) CustomControl 요소 구성 (형식)에 대 한 customentries 요소에 대 한 CustomControl 요소에 대 한의 Customentries 요소 구성에 대 한 컨트롤의 Customentries 요소 구성</span><span class="sxs-lookup"><span data-stu-id="fd71f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="fd71f-106">구문</span><span class="sxs-lookup"><span data-stu-id="fd71f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd71f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fd71f-107">Attributes and Elements</span></span>

<span data-ttu-id="fd71f-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomItem` .</span><span class="sxs-lookup"><span data-stu-id="fd71f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="fd71f-109">자세한 내용은 설명 부분을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd71f-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd71f-110">특성</span><span class="sxs-lookup"><span data-stu-id="fd71f-110">Attributes</span></span>

<span data-ttu-id="fd71f-111">없음</span><span class="sxs-lookup"><span data-stu-id="fd71f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd71f-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fd71f-112">Child Elements</span></span>

|<span data-ttu-id="fd71f-113">요소</span><span class="sxs-lookup"><span data-stu-id="fd71f-113">Element</span></span>|<span data-ttu-id="fd71f-114">설명</span><span class="sxs-lookup"><span data-stu-id="fd71f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd71f-115">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="fd71f-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="fd71f-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="fd71f-118">Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="fd71f-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="fd71f-120">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="fd71f-121">Configuration에 대한 Controls의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="fd71f-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="fd71f-123">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="fd71f-124">Configuration에 대한 Controls의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="fd71f-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="fd71f-126">괄호 또는 대괄호와 같은 텍스트를 컨트롤의 표시에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fd71f-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fd71f-127">Parent Elements</span></span>

|<span data-ttu-id="fd71f-128">요소</span><span class="sxs-lookup"><span data-stu-id="fd71f-128">Element</span></span>|<span data-ttu-id="fd71f-129">설명</span><span class="sxs-lookup"><span data-stu-id="fd71f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd71f-130">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="fd71f-131">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fd71f-132">설명</span><span class="sxs-lookup"><span data-stu-id="fd71f-132">Remarks</span></span>

<span data-ttu-id="fd71f-133">요소의 자식 요소를 지정할 때는 `CustomItem` 다음 사항을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="fd71f-134">자식 요소는 `ExpressionBinding` ,, `NewLine` `Text` 및 순서로 추가 되어야 `Frame` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="fd71f-135">지정할 수 있는 시퀀스 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fd71f-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="fd71f-136">각 시퀀스에는 사용할 수 있는 최대 요소 수에 대 한 제한이 없습니다 `ExpressionBinding` .</span><span class="sxs-lookup"><span data-stu-id="fd71f-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd71f-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd71f-137">See Also</span></span>

[<span data-ttu-id="fd71f-138">Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="fd71f-139">Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="fd71f-140">Configuration에 대한 Controls의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="fd71f-141">Configuration에 대한 Controls의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fd71f-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="fd71f-142">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fd71f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
