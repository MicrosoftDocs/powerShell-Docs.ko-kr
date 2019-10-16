---
title: CustomControl (형식)에 대 한 Customitem 요소의 CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363952"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="a4cf4-102">View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="a4cf4-103">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="a4cf4-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a4cf4-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 보기에 대 한 CustomEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4cf4-106">구문</span><span class="sxs-lookup"><span data-stu-id="a4cf4-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4cf4-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a4cf4-107">Attributes and Elements</span></span>

<span data-ttu-id="a4cf4-108">다음 섹션에서는 `CustomItem` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4cf4-109">특성</span><span class="sxs-lookup"><span data-stu-id="a4cf4-109">Attributes</span></span>

<span data-ttu-id="a4cf4-110">없음</span><span class="sxs-lookup"><span data-stu-id="a4cf4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4cf4-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a4cf4-111">Child Elements</span></span>

|<span data-ttu-id="a4cf4-112">요소</span><span class="sxs-lookup"><span data-stu-id="a4cf4-112">Element</span></span>|<span data-ttu-id="a4cf4-113">설명</span><span class="sxs-lookup"><span data-stu-id="a4cf4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4cf4-114">CustomControl의 CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="a4cf4-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a4cf4-116">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="a4cf4-117">CustomControl의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="a4cf4-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a4cf4-119">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="a4cf4-120">보기의 사용자 지정 컨트롤에 대 한 CustomItem의 줄 바꿈 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="a4cf4-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a4cf4-122">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="a4cf4-123">CustomControl에 대 한 CustomItem의 Text 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="a4cf4-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a4cf4-125">컨트롤에 표시 되는 데이터에 대 한 추가 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a4cf4-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a4cf4-126">Parent Elements</span></span>

|<span data-ttu-id="a4cf4-127">요소</span><span class="sxs-lookup"><span data-stu-id="a4cf4-127">Element</span></span>|<span data-ttu-id="a4cf4-128">설명</span><span class="sxs-lookup"><span data-stu-id="a4cf4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4cf4-129">CustomControl (형식)에 대 한 Customentry의 CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="a4cf4-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="a4cf4-130">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4cf4-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4cf4-131">설명</span><span class="sxs-lookup"><span data-stu-id="a4cf4-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a4cf4-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4cf4-132">See Also</span></span>

[<span data-ttu-id="a4cf4-133">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a4cf4-134">CustomControl의 CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a4cf4-135">CustomControl의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a4cf4-136">CustomControl의 CustomItem에 대 한 줄 바꿈 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a4cf4-137">CustomControl에 대 한 CustomItem의 Text 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a4cf4-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="a4cf4-138">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a4cf4-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
