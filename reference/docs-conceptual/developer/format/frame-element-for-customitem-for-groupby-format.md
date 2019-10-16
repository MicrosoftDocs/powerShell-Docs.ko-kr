---
title: GroupBy (형식)의 CustomItem에 대 한 Frame 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362952"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="236f1-102">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="236f1-103">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="236f1-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="236f1-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 CustomControl입니다 .이 요소는 groupby (형식)의 CustomItem에 대 한 GroupBy 항목의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="236f1-106">구문</span><span class="sxs-lookup"><span data-stu-id="236f1-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="236f1-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="236f1-107">Attributes and Elements</span></span>

<span data-ttu-id="236f1-108">다음 섹션에서는 `Frame` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="236f1-109">특성</span><span class="sxs-lookup"><span data-stu-id="236f1-109">Attributes</span></span>

<span data-ttu-id="236f1-110">없음</span><span class="sxs-lookup"><span data-stu-id="236f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="236f1-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="236f1-111">Child Elements</span></span>

|<span data-ttu-id="236f1-112">요소</span><span class="sxs-lookup"><span data-stu-id="236f1-112">Element</span></span>|<span data-ttu-id="236f1-113">설명</span><span class="sxs-lookup"><span data-stu-id="236f1-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="236f1-114">Required 요소</span><span class="sxs-lookup"><span data-stu-id="236f1-114">Required Element</span></span>|
|[<span data-ttu-id="236f1-115">GroupBy의 프레임에 대 한 FirstLineHanging 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="236f1-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="236f1-117">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="236f1-118">GroupBy의 프레임에 대 한 FirstLineIndent 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="236f1-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="236f1-120">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="236f1-121">GroupBy의 프레임에 대 한 왼쪽 들여쓰기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="236f1-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-122">Optional element.</span></span><br /><br /> <span data-ttu-id="236f1-123">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="236f1-124">[GroupBy의 프레임에 대 한 Rightindent 요소 (형식)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="236f1-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="236f1-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-125">Optional element.</span></span><br /><br /> <span data-ttu-id="236f1-126">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="236f1-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="236f1-127">Parent Elements</span></span>

|<span data-ttu-id="236f1-128">요소</span><span class="sxs-lookup"><span data-stu-id="236f1-128">Element</span></span>|<span data-ttu-id="236f1-129">설명</span><span class="sxs-lookup"><span data-stu-id="236f1-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="236f1-130">GroupBy (형식)에 대 한 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="236f1-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="236f1-131">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="236f1-132">설명</span><span class="sxs-lookup"><span data-stu-id="236f1-132">Remarks</span></span>

<span data-ttu-id="236f1-133">같은 `Frame` 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="236f1-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="236f1-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="236f1-134">See Also</span></span>

[<span data-ttu-id="236f1-135">GroupBy의 프레임에 대 한 FirstLineHanging 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="236f1-136">GroupBy의 프레임에 대 한 FirstLineIndent 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="236f1-137">GroupBy의 프레임에 대 한 왼쪽 들여쓰기 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="236f1-138">GroupBy의 프레임에 대 한 RightIndent 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="236f1-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="236f1-139">GroupBy (형식)에 대 한 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="236f1-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="236f1-140">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="236f1-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
