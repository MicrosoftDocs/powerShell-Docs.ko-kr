---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)
description: View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)
ms.openlocfilehash: 1ffe071bb6c4f590e4c79803a3faff2108c7b636
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652196"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="022bc-103">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="022bc-103">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="022bc-104">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="022bc-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="022bc-106">Configuration 요소 (Format) Viewcontrolelement (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="022bc-107">구문</span><span class="sxs-lookup"><span data-stu-id="022bc-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="022bc-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-108">Attributes and Elements</span></span>

<span data-ttu-id="022bc-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="022bc-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="022bc-110">특성</span><span class="sxs-lookup"><span data-stu-id="022bc-110">Attributes</span></span>

<span data-ttu-id="022bc-111">없음</span><span class="sxs-lookup"><span data-stu-id="022bc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="022bc-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-112">Child Elements</span></span>

|<span data-ttu-id="022bc-113">요소</span><span class="sxs-lookup"><span data-stu-id="022bc-113">Element</span></span>|<span data-ttu-id="022bc-114">설명</span><span class="sxs-lookup"><span data-stu-id="022bc-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="022bc-115">Required 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-115">Required Element</span></span>|
|[<span data-ttu-id="022bc-116">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-116">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="022bc-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="022bc-118">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="022bc-119">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-119">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="022bc-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-120">Optional element.</span></span><br /><br /> <span data-ttu-id="022bc-121">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="022bc-122">왼쪽 들여쓰기 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-122">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="022bc-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-123">Optional element.</span></span><br /><br /> <span data-ttu-id="022bc-124">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="022bc-125">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-125">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="022bc-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-126">Optional element.</span></span><br /><br /> <span data-ttu-id="022bc-127">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="022bc-128">부모 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-128">Parent Elements</span></span>

|<span data-ttu-id="022bc-129">요소</span><span class="sxs-lookup"><span data-stu-id="022bc-129">Element</span></span>|<span data-ttu-id="022bc-130">설명</span><span class="sxs-lookup"><span data-stu-id="022bc-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="022bc-131">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="022bc-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="022bc-132">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="022bc-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="022bc-133">설명</span><span class="sxs-lookup"><span data-stu-id="022bc-133">Remarks</span></span>

<span data-ttu-id="022bc-134">같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="022bc-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="022bc-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="022bc-135">See Also</span></span>

[<span data-ttu-id="022bc-136">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-136">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022bc-137">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-137">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022bc-138">왼쪽 들여쓰기 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-138">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022bc-139">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="022bc-139">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022bc-140">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="022bc-140">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022bc-141">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="022bc-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
