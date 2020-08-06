---
title: GroupBy (형식)에 대 한 Customitem의 CustomItem 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8086c5330b6644f83316ad4ae33c33ba40d9eee
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783724"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="6006f-102">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="6006f-103">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="6006f-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6006f-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format)의 groupby 요소 (groupby (format) CustomControl 요소에 대 한 CustomControl의 경우 groupby 항목 요소에 대 한 groupby 항목 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6006f-106">구문</span><span class="sxs-lookup"><span data-stu-id="6006f-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6006f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6006f-107">Attributes and Elements</span></span>

<span data-ttu-id="6006f-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomItem` .</span><span class="sxs-lookup"><span data-stu-id="6006f-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6006f-109">특성</span><span class="sxs-lookup"><span data-stu-id="6006f-109">Attributes</span></span>

<span data-ttu-id="6006f-110">없음</span><span class="sxs-lookup"><span data-stu-id="6006f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6006f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6006f-111">Child Elements</span></span>

|<span data-ttu-id="6006f-112">요소</span><span class="sxs-lookup"><span data-stu-id="6006f-112">Element</span></span>|<span data-ttu-id="6006f-113">설명</span><span class="sxs-lookup"><span data-stu-id="6006f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6006f-114">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="6006f-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6006f-116">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="6006f-117">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="6006f-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6006f-119">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="6006f-120">GroupBy의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="6006f-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6006f-122">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="6006f-123">GroupBy의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="6006f-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="6006f-125">컨트롤에 표시 되는 데이터에 대 한 추가 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6006f-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6006f-126">Parent Elements</span></span>

|<span data-ttu-id="6006f-127">요소</span><span class="sxs-lookup"><span data-stu-id="6006f-127">Element</span></span>|<span data-ttu-id="6006f-128">설명</span><span class="sxs-lookup"><span data-stu-id="6006f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6006f-129">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="6006f-130">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6006f-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6006f-131">설명</span><span class="sxs-lookup"><span data-stu-id="6006f-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6006f-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6006f-132">See Also</span></span>

[<span data-ttu-id="6006f-133">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="6006f-134">GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="6006f-135">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="6006f-136">GroupBy의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="6006f-137">GroupBy의 CustomItem에 대한 Text 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6006f-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="6006f-138">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6006f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
