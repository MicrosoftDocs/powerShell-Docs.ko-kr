---
title: 구성 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862939"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="7d562-102">Configuration에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7d562-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7d562-103">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="7d562-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7d562-105">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry 구성에 대 한 컨트롤에 대 한 구성 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="7d562-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="7d562-106">구문</span><span class="sxs-lookup"><span data-stu-id="7d562-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d562-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-107">Attributes and Elements</span></span>

<span data-ttu-id="7d562-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="7d562-109">자세한 내용은 설명 부분을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d562-110">특성</span><span class="sxs-lookup"><span data-stu-id="7d562-110">Attributes</span></span>

<span data-ttu-id="7d562-111">없음</span><span class="sxs-lookup"><span data-stu-id="7d562-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d562-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-112">Child Elements</span></span>

|<span data-ttu-id="7d562-113">요소</span><span class="sxs-lookup"><span data-stu-id="7d562-113">Element</span></span>|<span data-ttu-id="7d562-114">설명</span><span class="sxs-lookup"><span data-stu-id="7d562-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d562-115">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="7d562-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-116">Optional element.</span></span><br /><br /> <span data-ttu-id="7d562-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="7d562-118">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="7d562-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-119">Optional element.</span></span><br /><br /> <span data-ttu-id="7d562-120">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="7d562-121">줄 바꿈 (형식) 구성에 대 한 컨트롤에 대 한 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="7d562-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-122">Optional element.</span></span><br /><br /> <span data-ttu-id="7d562-123">컨트롤의 표시에 빈 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="7d562-124">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem에 대 한 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="7d562-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-125">Optional element.</span></span><br /><br /> <span data-ttu-id="7d562-126">컨트롤의 표시에 대괄호 또는 괄호와 같은 텍스트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7d562-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-127">Parent Elements</span></span>

|<span data-ttu-id="7d562-128">요소</span><span class="sxs-lookup"><span data-stu-id="7d562-128">Element</span></span>|<span data-ttu-id="7d562-129">설명</span><span class="sxs-lookup"><span data-stu-id="7d562-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d562-130">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="7d562-131">컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d562-132">설명</span><span class="sxs-lookup"><span data-stu-id="7d562-132">Remarks</span></span>

<span data-ttu-id="7d562-133">자식 요소를 지정 하는 경우는 `CustomItem` 요소를 다음 염두 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="7d562-134">다음 순서 대로 자식 요소를 추가 해야 합니다. `ExpressionBinding`, `NewLine`를 `Text`, 및 `Frame`합니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="7d562-135">지정할 수 있는 시퀀스의 수는 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="7d562-136">각 시퀀스에는 수의 최대 제한이 `ExpressionBinding` 사용할 수 있는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d562-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d562-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d562-137">See Also</span></span>

[<span data-ttu-id="7d562-138">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="7d562-139">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="7d562-140">줄 바꿈 (형식) 구성에 대 한 컨트롤에 대 한 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="7d562-141">구성 (형식)에 대 한 컨트롤에 대 한 CustomItem에 대 한 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="7d562-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="7d562-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="7d562-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
