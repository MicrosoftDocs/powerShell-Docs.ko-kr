---
title: 구성 (형식)에 대 한 컨트롤에 대 한 요소 CustomItem에 대 한 프레임 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065566"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="22cb7-102">Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22cb7-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="22cb7-103">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="22cb7-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="22cb7-105">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry CustomItem 구성 (형식)에 대 한 컨트롤에 대 한 구성 프레임 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="22cb7-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22cb7-106">구문</span><span class="sxs-lookup"><span data-stu-id="22cb7-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22cb7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-107">Attributes and Elements</span></span>

<span data-ttu-id="22cb7-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="22cb7-109">특성</span><span class="sxs-lookup"><span data-stu-id="22cb7-109">Attributes</span></span>

<span data-ttu-id="22cb7-110">없음</span><span class="sxs-lookup"><span data-stu-id="22cb7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22cb7-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-111">Child Elements</span></span>

|<span data-ttu-id="22cb7-112">요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-112">Element</span></span>|<span data-ttu-id="22cb7-113">설명</span><span class="sxs-lookup"><span data-stu-id="22cb7-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="22cb7-114">필수 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-114">Required Element</span></span>|
|[<span data-ttu-id="22cb7-115">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="22cb7-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="22cb7-117">데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="22cb7-118">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="22cb7-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="22cb7-120">데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="22cb7-121">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="22cb7-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="22cb7-123">왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="22cb7-124">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="22cb7-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-125">Optional element.</span></span><br /><br /> <span data-ttu-id="22cb7-126">오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="22cb7-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-127">Parent Elements</span></span>

|<span data-ttu-id="22cb7-128">요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-128">Element</span></span>|<span data-ttu-id="22cb7-129">설명</span><span class="sxs-lookup"><span data-stu-id="22cb7-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22cb7-130">구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="22cb7-131">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22cb7-132">설명</span><span class="sxs-lookup"><span data-stu-id="22cb7-132">Remarks</span></span>

<span data-ttu-id="22cb7-133">지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 하며 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 동일한 요소 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="22cb7-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="22cb7-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22cb7-134">See Also</span></span>

[<span data-ttu-id="22cb7-135">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="22cb7-136">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="22cb7-137">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="22cb7-138">구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="22cb7-139">구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="22cb7-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="22cb7-140">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="22cb7-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
