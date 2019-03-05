---
title: GroupBy (형식)에 대 한 CustomEntry CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856929"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="5b78f-102">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5b78f-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="5b78f-103">사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="5b78f-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5b78f-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomItem 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 GroupBy (형식)에 대 한 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="5b78f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b78f-106">구문</span><span class="sxs-lookup"><span data-stu-id="5b78f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b78f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-107">Attributes and Elements</span></span>

<span data-ttu-id="5b78f-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b78f-109">특성</span><span class="sxs-lookup"><span data-stu-id="5b78f-109">Attributes</span></span>

<span data-ttu-id="5b78f-110">없음</span><span class="sxs-lookup"><span data-stu-id="5b78f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b78f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-111">Child Elements</span></span>

|<span data-ttu-id="5b78f-112">요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-112">Element</span></span>|<span data-ttu-id="5b78f-113">설명</span><span class="sxs-lookup"><span data-stu-id="5b78f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b78f-114">GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5b78f-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5b78f-116">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="5b78f-117">GroupBy (형식)에 대 한 CustomItem 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5b78f-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5b78f-119">사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="5b78f-120">GroupBy (형식)에 대 한 CustomItem 줄 바꿈 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5b78f-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5b78f-122">컨트롤의 표시에 빈 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="5b78f-123">GroupBy (형식)에 대 한 CustomItem에 대 한 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5b78f-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5b78f-125">추가 텍스트 컨트롤에 의해 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5b78f-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-126">Parent Elements</span></span>

|<span data-ttu-id="5b78f-127">요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-127">Element</span></span>|<span data-ttu-id="5b78f-128">설명</span><span class="sxs-lookup"><span data-stu-id="5b78f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b78f-129">GroupBy (형식)에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="5b78f-130">사용자 지정 컨트롤 뷰의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5b78f-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5b78f-131">설명</span><span class="sxs-lookup"><span data-stu-id="5b78f-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5b78f-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b78f-132">See Also</span></span>

[<span data-ttu-id="5b78f-133">GroupBy (형식)에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="5b78f-134">GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5b78f-135">GroupBy (형식)에 대 한 CustomItem 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5b78f-136">GroupBy (형식)에 대 한 CustomItem 줄 바꿈 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5b78f-137">GroupBy (형식)에 대 한 CustomItem에 대 한 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="5b78f-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5b78f-138">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="5b78f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)