---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)
description: View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)
ms.openlocfilehash: 9090a3ada5316ba5ddb4a9c46eee37c11982ae6e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666742"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="cf7d3-103">View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-103">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="cf7d3-104">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="cf7d3-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="cf7d3-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="cf7d3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf7d3-107">구문</span><span class="sxs-lookup"><span data-stu-id="cf7d3-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf7d3-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cf7d3-108">Attributes and Elements</span></span>

<span data-ttu-id="cf7d3-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomItem` .</span><span class="sxs-lookup"><span data-stu-id="cf7d3-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf7d3-110">특성</span><span class="sxs-lookup"><span data-stu-id="cf7d3-110">Attributes</span></span>

<span data-ttu-id="cf7d3-111">없음</span><span class="sxs-lookup"><span data-stu-id="cf7d3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf7d3-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cf7d3-112">Child Elements</span></span>

|<span data-ttu-id="cf7d3-113">요소</span><span class="sxs-lookup"><span data-stu-id="cf7d3-113">Element</span></span>|<span data-ttu-id="cf7d3-114">설명</span><span class="sxs-lookup"><span data-stu-id="cf7d3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf7d3-115">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-115">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf7d3-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="cf7d3-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="cf7d3-118">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-118">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf7d3-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="cf7d3-120">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="cf7d3-121">보기의 사용자 지정 컨트롤에 대 한 CustomItem의 줄 바꿈 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-121">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf7d3-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-122">Optional element.</span></span><br /><br /> <span data-ttu-id="cf7d3-123">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="cf7d3-124">CustomControl에 대 한 CustomItem의 Text 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-124">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="cf7d3-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-125">Optional element.</span></span><br /><br /> <span data-ttu-id="cf7d3-126">컨트롤에 표시 되는 데이터에 대 한 추가 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cf7d3-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cf7d3-127">Parent Elements</span></span>

|<span data-ttu-id="cf7d3-128">요소</span><span class="sxs-lookup"><span data-stu-id="cf7d3-128">Element</span></span>|<span data-ttu-id="cf7d3-129">설명</span><span class="sxs-lookup"><span data-stu-id="cf7d3-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf7d3-130">View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-130">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf7d3-131">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf7d3-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cf7d3-132">설명</span><span class="sxs-lookup"><span data-stu-id="cf7d3-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="cf7d3-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf7d3-133">See Also</span></span>

[<span data-ttu-id="cf7d3-134">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-134">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cf7d3-135">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-135">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cf7d3-136">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-136">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cf7d3-137">View에 대한 CustomControl의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-137">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cf7d3-138">CustomControl에 대 한 CustomItem의 Text 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cf7d3-138">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="cf7d3-139">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="cf7d3-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
