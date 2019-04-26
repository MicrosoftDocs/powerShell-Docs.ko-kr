---
title: GroupBy (형식)에 대 한 요소 CustomItem에 대 한 프레임 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065600"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="6bd26-102">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6bd26-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="6bd26-103">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="6bd26-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6bd26-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 GroupBy (형식) 프레임에 대 한 요소의 GroupBy (형식)에 대 한 CustomItem CustomEntry CustomItem 요소 GroupBy (형식)에 CustomControl</span><span class="sxs-lookup"><span data-stu-id="6bd26-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6bd26-106">구문</span><span class="sxs-lookup"><span data-stu-id="6bd26-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6bd26-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-107">Attributes and Elements</span></span>

<span data-ttu-id="6bd26-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6bd26-109">특성</span><span class="sxs-lookup"><span data-stu-id="6bd26-109">Attributes</span></span>

<span data-ttu-id="6bd26-110">없음</span><span class="sxs-lookup"><span data-stu-id="6bd26-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6bd26-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-111">Child Elements</span></span>

|<span data-ttu-id="6bd26-112">요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-112">Element</span></span>|<span data-ttu-id="6bd26-113">설명</span><span class="sxs-lookup"><span data-stu-id="6bd26-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="6bd26-114">필수 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-114">Required Element</span></span>|
|[<span data-ttu-id="6bd26-115">GroupBy (형식)에 대 한 프레임에 대 한 FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="6bd26-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd26-117">데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="6bd26-118">GroupBy (형식)에 대 한 프레임에 대 한 FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="6bd26-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd26-120">데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="6bd26-121">GroupBy (형식)에 대 한 프레임에 대 한 LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="6bd26-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd26-123">왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="6bd26-124">[GroupBy (형식)에 대 한 프레임에 대 한 RightIndent 요소](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="6bd26-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6bd26-126">오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6bd26-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-127">Parent Elements</span></span>

|<span data-ttu-id="6bd26-128">요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-128">Element</span></span>|<span data-ttu-id="6bd26-129">설명</span><span class="sxs-lookup"><span data-stu-id="6bd26-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6bd26-130">GroupBy (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="6bd26-131">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6bd26-132">설명</span><span class="sxs-lookup"><span data-stu-id="6bd26-132">Remarks</span></span>

<span data-ttu-id="6bd26-133">지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 하며 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 동일한 요소 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6bd26-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bd26-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bd26-134">See Also</span></span>

[<span data-ttu-id="6bd26-135">GroupBy (형식)에 대 한 프레임에 대 한 FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6bd26-136">GroupBy (형식)에 대 한 프레임에 대 한 FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6bd26-137">GroupBy (형식)에 대 한 프레임에 대 한 LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6bd26-138">GroupBy (형식)에 대 한 프레임에 대 한 RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6bd26-139">GroupBy (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="6bd26-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="6bd26-140">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="6bd26-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
