---
title: 요소 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem에 대 한 프레임 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859819"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="3e5b7-102">View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3e5b7-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="3e5b7-103">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="3e5b7-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3e5b7-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry (형식) 보기 프레임에 대 한 요소의 CustomItem 보기 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="3e5b7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e5b7-106">구문</span><span class="sxs-lookup"><span data-stu-id="3e5b7-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e5b7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-107">Attributes and Elements</span></span>

<span data-ttu-id="3e5b7-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e5b7-109">특성</span><span class="sxs-lookup"><span data-stu-id="3e5b7-109">Attributes</span></span>

<span data-ttu-id="3e5b7-110">없음</span><span class="sxs-lookup"><span data-stu-id="3e5b7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e5b7-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-111">Child Elements</span></span>

|<span data-ttu-id="3e5b7-112">요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-112">Element</span></span>|<span data-ttu-id="3e5b7-113">설명</span><span class="sxs-lookup"><span data-stu-id="3e5b7-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="3e5b7-114">필수 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-114">Required Element</span></span>|
|[<span data-ttu-id="3e5b7-115">컨트롤의 보기 (형식)의 프레임 FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3e5b7-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3e5b7-117">첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="3e5b7-118">컨트롤의 보기 (형식)의 프레임 FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3e5b7-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3e5b7-120">첫 번째 줄은 오른쪽으로 이동 하 여 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="3e5b7-121">컨트롤의 보기 (형식)의 프레임 LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3e5b7-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3e5b7-123">왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="3e5b7-124">컨트롤의 보기 (형식)의 프레임 RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3e5b7-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-125">Optional element.</span></span><br /><br /> <span data-ttu-id="3e5b7-126">오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3e5b7-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-127">Parent Elements</span></span>

|<span data-ttu-id="3e5b7-128">요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-128">Element</span></span>|<span data-ttu-id="3e5b7-129">설명</span><span class="sxs-lookup"><span data-stu-id="3e5b7-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e5b7-130">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="3e5b7-131">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3e5b7-132">설명</span><span class="sxs-lookup"><span data-stu-id="3e5b7-132">Remarks</span></span>

<span data-ttu-id="3e5b7-133">지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 하며 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 동일한 요소 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3e5b7-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e5b7-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e5b7-134">See Also</span></span>

[<span data-ttu-id="3e5b7-135">컨트롤의 보기 (형식)의 프레임 FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3e5b7-136">컨트롤의 보기 (형식)의 프레임 FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3e5b7-137">컨트롤의 보기 (형식)의 프레임 LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3e5b7-138">컨트롤의 보기 (형식)의 프레임 RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3e5b7-139">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="3e5b7-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="3e5b7-140">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="3e5b7-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
