---
title: CustomControl (형식)에 대 한 Customitem 요소의 CustomItem 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 25101c9c156ef91657f51db7044bf9a6653142a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785832"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="b2571-102">View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="b2571-103">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="b2571-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b2571-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="b2571-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2571-106">구문</span><span class="sxs-lookup"><span data-stu-id="b2571-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2571-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b2571-107">Attributes and Elements</span></span>

<span data-ttu-id="b2571-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomItem` .</span><span class="sxs-lookup"><span data-stu-id="b2571-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2571-109">특성</span><span class="sxs-lookup"><span data-stu-id="b2571-109">Attributes</span></span>

<span data-ttu-id="b2571-110">없음</span><span class="sxs-lookup"><span data-stu-id="b2571-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2571-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b2571-111">Child Elements</span></span>

|<span data-ttu-id="b2571-112">요소</span><span class="sxs-lookup"><span data-stu-id="b2571-112">Element</span></span>|<span data-ttu-id="b2571-113">설명</span><span class="sxs-lookup"><span data-stu-id="b2571-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2571-114">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2571-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b2571-116">컨트롤에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b2571-117">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2571-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b2571-119">사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="b2571-120">보기의 사용자 지정 컨트롤에 대 한 CustomItem의 줄 바꿈 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2571-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b2571-122">컨트롤의 표시에 빈 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b2571-123">CustomControl에 대 한 CustomItem의 Text 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="b2571-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b2571-125">컨트롤에 표시 되는 데이터에 대 한 추가 텍스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b2571-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b2571-126">Parent Elements</span></span>

|<span data-ttu-id="b2571-127">요소</span><span class="sxs-lookup"><span data-stu-id="b2571-127">Element</span></span>|<span data-ttu-id="b2571-128">설명</span><span class="sxs-lookup"><span data-stu-id="b2571-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2571-129">View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="b2571-130">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2571-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2571-131">설명</span><span class="sxs-lookup"><span data-stu-id="b2571-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b2571-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2571-132">See Also</span></span>

[<span data-ttu-id="b2571-133">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2571-134">View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2571-135">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2571-136">View에 대한 CustomControl의 CustomItem에 대한 NewLine 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b2571-137">CustomControl에 대 한 CustomItem의 Text 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b2571-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="b2571-138">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b2571-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
