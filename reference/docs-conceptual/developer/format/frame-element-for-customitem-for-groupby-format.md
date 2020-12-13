---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomItem에 대한 Frame 요소(형식)
description: GroupBy의 CustomItem에 대한 Frame 요소(형식)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652172"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="9c901-103">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-103">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="9c901-104">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="9c901-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9c901-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소 (format) CustomControl 요소에 대 한 CustomControl의 Customentries 요소 (groupby)의 경우 CustomControl에 대 한 customentries 요소 (형식)의 경우 customentries 요소에 대 한 Customentries 요소</span><span class="sxs-lookup"><span data-stu-id="9c901-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c901-107">구문</span><span class="sxs-lookup"><span data-stu-id="9c901-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c901-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9c901-108">Attributes and Elements</span></span>

<span data-ttu-id="9c901-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="9c901-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c901-110">특성</span><span class="sxs-lookup"><span data-stu-id="9c901-110">Attributes</span></span>

<span data-ttu-id="9c901-111">없음</span><span class="sxs-lookup"><span data-stu-id="9c901-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c901-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9c901-112">Child Elements</span></span>

|<span data-ttu-id="9c901-113">요소</span><span class="sxs-lookup"><span data-stu-id="9c901-113">Element</span></span>|<span data-ttu-id="9c901-114">설명</span><span class="sxs-lookup"><span data-stu-id="9c901-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="9c901-115">Required 요소</span><span class="sxs-lookup"><span data-stu-id="9c901-115">Required Element</span></span>|
|[<span data-ttu-id="9c901-116">GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-116">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="9c901-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9c901-118">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="9c901-119">GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-119">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="9c901-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9c901-121">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="9c901-122">GroupBy의 Frame에 대한 LeftIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-122">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="9c901-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9c901-124">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="9c901-125">[GroupBy의 프레임에 대 한 Rightindent 요소 (형식)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="9c901-125">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="9c901-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-126">Optional element.</span></span><br /><br /> <span data-ttu-id="9c901-127">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9c901-128">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9c901-128">Parent Elements</span></span>

|<span data-ttu-id="9c901-129">요소</span><span class="sxs-lookup"><span data-stu-id="9c901-129">Element</span></span>|<span data-ttu-id="9c901-130">설명</span><span class="sxs-lookup"><span data-stu-id="9c901-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c901-131">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-131">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9c901-132">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c901-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c901-133">설명</span><span class="sxs-lookup"><span data-stu-id="9c901-133">Remarks</span></span>

<span data-ttu-id="9c901-134">같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="9c901-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c901-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c901-135">See Also</span></span>

[<span data-ttu-id="9c901-136">GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-136">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="9c901-137">GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-137">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="9c901-138">GroupBy의 Frame에 대한 LeftIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-138">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="9c901-139">GroupBy의 Frame에 대한 RightIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-139">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="9c901-140">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c901-140">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9c901-141">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9c901-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
