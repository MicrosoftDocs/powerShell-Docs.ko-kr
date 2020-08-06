---
title: 구성에 대 한 컨트롤의 CustomItem에 대 한 Frame 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa435b8d6b868d2d7c94b7926321d94edc2ec290
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781480"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="3cf42-102">Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3cf42-103">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="3cf42-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3cf42-105">Configuration 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤의 요소 구성 (format) CustomControl 요소 구성 (형식)에 대 한 컨트롤의 Customentries 요소 구성 (format) Customentries 요소에 대 한 컨트롤의 customentries 요소에 대 한 컨트롤의 Customentries 요소에 대 한 컨트롤의 Customentries 요소 구성</span><span class="sxs-lookup"><span data-stu-id="3cf42-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3cf42-106">구문</span><span class="sxs-lookup"><span data-stu-id="3cf42-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3cf42-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-107">Attributes and Elements</span></span>

<span data-ttu-id="3cf42-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="3cf42-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3cf42-109">특성</span><span class="sxs-lookup"><span data-stu-id="3cf42-109">Attributes</span></span>

<span data-ttu-id="3cf42-110">없음</span><span class="sxs-lookup"><span data-stu-id="3cf42-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3cf42-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-111">Child Elements</span></span>

|<span data-ttu-id="3cf42-112">요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-112">Element</span></span>|<span data-ttu-id="3cf42-113">설명</span><span class="sxs-lookup"><span data-stu-id="3cf42-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="3cf42-114">Required 요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-114">Required Element</span></span>|
|[<span data-ttu-id="3cf42-115">Configuration에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3cf42-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3cf42-117">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="3cf42-118">Configuration에 대한 Controls의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3cf42-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3cf42-120">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="3cf42-121">Configuration에 대한 Controls의 Frame에 대한 LeftIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3cf42-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3cf42-123">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="3cf42-124">Configuration에 대한 Controls의 Frame에 대한 RightIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="3cf42-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-125">Optional element.</span></span><br /><br /> <span data-ttu-id="3cf42-126">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3cf42-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-127">Parent Elements</span></span>

|<span data-ttu-id="3cf42-128">요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-128">Element</span></span>|<span data-ttu-id="3cf42-129">설명</span><span class="sxs-lookup"><span data-stu-id="3cf42-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cf42-130">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3cf42-131">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cf42-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3cf42-132">설명</span><span class="sxs-lookup"><span data-stu-id="3cf42-132">Remarks</span></span>

<span data-ttu-id="3cf42-133">같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 요소를 지정할 수 없습니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="3cf42-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cf42-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3cf42-134">See Also</span></span>

[<span data-ttu-id="3cf42-135">Configuration에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3cf42-136">Configuration에 대한 Controls의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3cf42-137">Configuration에 대한 Controls의 Frame에 대한 LeftIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3cf42-138">Configuration에 대한 Controls의 Frame에 대한 RightIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3cf42-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="3cf42-139">구성에 대 한 컨트롤 Customitem의 CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="3cf42-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3cf42-140">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3cf42-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
