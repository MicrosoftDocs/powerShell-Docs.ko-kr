---
title: 요소 (형식) 보기에 대 한 CustomControl에 대 한 CustomItem에 대 한 프레임 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065583"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="f8690-102">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f8690-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="f8690-103">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f8690-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f8690-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomControlView (형식) 프레임에 대 한 요소의 CustomControl 보려면 (형식)에 대 한 CustomItem CustomEntry</span><span class="sxs-lookup"><span data-stu-id="f8690-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8690-106">구문</span><span class="sxs-lookup"><span data-stu-id="f8690-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8690-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-107">Attributes and Elements</span></span>

<span data-ttu-id="f8690-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8690-109">특성</span><span class="sxs-lookup"><span data-stu-id="f8690-109">Attributes</span></span>

<span data-ttu-id="f8690-110">없음</span><span class="sxs-lookup"><span data-stu-id="f8690-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8690-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-111">Child Elements</span></span>

|<span data-ttu-id="f8690-112">요소</span><span class="sxs-lookup"><span data-stu-id="f8690-112">Element</span></span>|<span data-ttu-id="f8690-113">설명</span><span class="sxs-lookup"><span data-stu-id="f8690-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f8690-114">필수 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-114">Required Element</span></span>|
|[<span data-ttu-id="f8690-115">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f8690-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f8690-117">데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="f8690-118">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f8690-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f8690-120">데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="f8690-121">LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f8690-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f8690-123">왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="f8690-124">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f8690-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f8690-126">오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8690-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-127">Parent Elements</span></span>

|<span data-ttu-id="f8690-128">요소</span><span class="sxs-lookup"><span data-stu-id="f8690-128">Element</span></span>|<span data-ttu-id="f8690-129">설명</span><span class="sxs-lookup"><span data-stu-id="f8690-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8690-130">뷰 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="f8690-131">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f8690-132">설명</span><span class="sxs-lookup"><span data-stu-id="f8690-132">Remarks</span></span>

<span data-ttu-id="f8690-133">지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 하며 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 동일한 요소 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f8690-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8690-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8690-134">See Also</span></span>

[<span data-ttu-id="f8690-135">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f8690-136">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f8690-137">LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f8690-138">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f8690-139">뷰 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="f8690-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f8690-140">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="f8690-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
