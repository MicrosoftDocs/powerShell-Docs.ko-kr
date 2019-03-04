---
title: CustomControl 보려면 (형식)에 대 한 CustomEntry CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856189"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="9db3a-102">View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9db3a-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="9db3a-103">사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="9db3a-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9db3a-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry 보려면 (형식)</span><span class="sxs-lookup"><span data-stu-id="9db3a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9db3a-106">구문</span><span class="sxs-lookup"><span data-stu-id="9db3a-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9db3a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-107">Attributes and Elements</span></span>

<span data-ttu-id="9db3a-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9db3a-109">특성</span><span class="sxs-lookup"><span data-stu-id="9db3a-109">Attributes</span></span>

<span data-ttu-id="9db3a-110">없음</span><span class="sxs-lookup"><span data-stu-id="9db3a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9db3a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-111">Child Elements</span></span>

|<span data-ttu-id="9db3a-112">요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-112">Element</span></span>|<span data-ttu-id="9db3a-113">설명</span><span class="sxs-lookup"><span data-stu-id="9db3a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9db3a-114">ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="9db3a-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9db3a-116">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="9db3a-117">CustomItem CustomControl 보려면 (형식)에 대 한 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="9db3a-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9db3a-119">사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="9db3a-120">줄 바꿈 (형식) 보기에 대 한 사용자 지정 컨트롤에 대 한 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="9db3a-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9db3a-122">컨트롤의 표시에 빈 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="9db3a-123">CustomItem CustomControl 보려면 (형식)에 대 한 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="9db3a-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9db3a-125">추가 텍스트 컨트롤에 의해 표시 되는 데이터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9db3a-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-126">Parent Elements</span></span>

|<span data-ttu-id="9db3a-127">요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-127">Element</span></span>|<span data-ttu-id="9db3a-128">설명</span><span class="sxs-lookup"><span data-stu-id="9db3a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9db3a-129">CustomControl 보려면 (형식)에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="9db3a-130">사용자 지정 컨트롤 뷰의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9db3a-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9db3a-131">설명</span><span class="sxs-lookup"><span data-stu-id="9db3a-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9db3a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9db3a-132">See Also</span></span>

[<span data-ttu-id="9db3a-133">뷰 (형식)에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9db3a-134">ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9db3a-135">CustomItem CustomControl 보려면 (형식)에 대 한 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9db3a-136">줄 바꿈 CustomItem CustomControl 보려면 (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9db3a-137">CustomItem CustomControl 보려면 (형식)에 대 한 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="9db3a-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="9db3a-138">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="9db3a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
