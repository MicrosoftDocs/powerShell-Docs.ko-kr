---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)
description: GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)
ms.openlocfilehash: 5db23ad4dad5bd66ea64b9c6e91b8224a4aa4eca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645982"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="50161-103">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-103">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="50161-104">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="50161-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="50161-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50161-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="50161-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format)의 groupby 요소 (groupby (format) CustomControl 요소에 대 한 CustomControl의 경우 groupby 항목 요소에 대 한 groupby 항목 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="50161-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50161-107">구문</span><span class="sxs-lookup"><span data-stu-id="50161-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50161-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="50161-108">Attributes and Elements</span></span>

<span data-ttu-id="50161-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomItem` .</span><span class="sxs-lookup"><span data-stu-id="50161-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="50161-110">특성</span><span class="sxs-lookup"><span data-stu-id="50161-110">Attributes</span></span>

<span data-ttu-id="50161-111">없음</span><span class="sxs-lookup"><span data-stu-id="50161-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50161-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="50161-112">Child Elements</span></span>

|<span data-ttu-id="50161-113">요소</span><span class="sxs-lookup"><span data-stu-id="50161-113">Element</span></span>|<span data-ttu-id="50161-114">설명</span><span class="sxs-lookup"><span data-stu-id="50161-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50161-115">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-115">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="50161-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="50161-116">Optional element.</span></span><br /><br /> <span data-ttu-id="50161-117">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="50161-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="50161-118">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-118">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="50161-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="50161-119">Optional element.</span></span><br /><br /> <span data-ttu-id="50161-120">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="50161-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="50161-121">GroupBy의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-121">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="50161-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="50161-122">Optional element.</span></span><br /><br /> <span data-ttu-id="50161-123">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="50161-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="50161-124">GroupBy의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-124">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="50161-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="50161-125">Optional element.</span></span><br /><br /> <span data-ttu-id="50161-126">컨트롤에 표시 되는 데이터에 대 한 추가 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50161-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50161-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="50161-127">Parent Elements</span></span>

|<span data-ttu-id="50161-128">요소</span><span class="sxs-lookup"><span data-stu-id="50161-128">Element</span></span>|<span data-ttu-id="50161-129">설명</span><span class="sxs-lookup"><span data-stu-id="50161-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50161-130">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-130">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="50161-131">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="50161-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50161-132">설명</span><span class="sxs-lookup"><span data-stu-id="50161-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="50161-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50161-133">See Also</span></span>

[<span data-ttu-id="50161-134">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-134">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="50161-135">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-135">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="50161-136">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-136">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="50161-137">GroupBy의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-137">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="50161-138">GroupBy의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50161-138">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="50161-139">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="50161-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
