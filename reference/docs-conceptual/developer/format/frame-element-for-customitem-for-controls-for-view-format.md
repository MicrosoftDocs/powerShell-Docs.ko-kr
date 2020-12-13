---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)
description: View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652212"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="5032e-103">View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-103">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="5032e-104">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5032e-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5032e-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for View (format) Customentries 요소에 대 한 컨트롤의 customentries 요소 뷰 (format)의 컨트롤에 대 한 Customentries 요소에 대 한 컨트롤의 customentries 요소입니다 (형식).</span><span class="sxs-lookup"><span data-stu-id="5032e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5032e-107">구문</span><span class="sxs-lookup"><span data-stu-id="5032e-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5032e-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5032e-108">Attributes and Elements</span></span>

<span data-ttu-id="5032e-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="5032e-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5032e-110">특성</span><span class="sxs-lookup"><span data-stu-id="5032e-110">Attributes</span></span>

<span data-ttu-id="5032e-111">없음</span><span class="sxs-lookup"><span data-stu-id="5032e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5032e-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5032e-112">Child Elements</span></span>

|<span data-ttu-id="5032e-113">요소</span><span class="sxs-lookup"><span data-stu-id="5032e-113">Element</span></span>|<span data-ttu-id="5032e-114">설명</span><span class="sxs-lookup"><span data-stu-id="5032e-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5032e-115">Required 요소</span><span class="sxs-lookup"><span data-stu-id="5032e-115">Required Element</span></span>|
|[<span data-ttu-id="5032e-116">뷰 컨트롤 프레임의 FirstLineHanging 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-116">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5032e-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5032e-118">첫 번째 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-118">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="5032e-119">뷰 컨트롤의 프레임 요소 FirstLineIndent 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-119">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5032e-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5032e-121">첫 번째 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-121">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="5032e-122">뷰 컨트롤 프레임의 왼쪽 들여쓰기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-122">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5032e-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="5032e-124">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="5032e-125">View 컨트롤 프레임의 오른쪽 들여쓰기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-125">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="5032e-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-126">Optional element.</span></span><br /><br /> <span data-ttu-id="5032e-127">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5032e-128">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5032e-128">Parent Elements</span></span>

|<span data-ttu-id="5032e-129">요소</span><span class="sxs-lookup"><span data-stu-id="5032e-129">Element</span></span>|<span data-ttu-id="5032e-130">설명</span><span class="sxs-lookup"><span data-stu-id="5032e-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5032e-131">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-131">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="5032e-132">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5032e-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5032e-133">설명</span><span class="sxs-lookup"><span data-stu-id="5032e-133">Remarks</span></span>

<span data-ttu-id="5032e-134">같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 요소를 지정할 수 없습니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="5032e-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5032e-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5032e-135">See Also</span></span>

[<span data-ttu-id="5032e-136">뷰 컨트롤 프레임의 FirstLineHanging 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-136">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5032e-137">뷰 컨트롤의 프레임 요소 FirstLineIndent 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-137">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5032e-138">뷰 컨트롤 프레임의 왼쪽 들여쓰기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-138">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5032e-139">View 컨트롤 프레임의 오른쪽 들여쓰기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-139">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="5032e-140">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5032e-140">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="5032e-141">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5032e-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
