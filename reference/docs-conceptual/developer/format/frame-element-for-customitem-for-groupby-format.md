---
title: GroupBy (형식)의 CustomItem에 대 한 Frame 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1568236ff7b6142f7e41be70a3ae5e28307cf790
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785764"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="c3e38-102">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="c3e38-103">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="c3e38-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c3e38-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소 (format) CustomControl 요소에 대 한 CustomControl의 Customentries 요소 (groupby)의 경우 CustomControl에 대 한 customentries 요소 (형식)의 경우 customentries 요소에 대 한 Customentries 요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3e38-106">구문</span><span class="sxs-lookup"><span data-stu-id="c3e38-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3e38-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-107">Attributes and Elements</span></span>

<span data-ttu-id="c3e38-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="c3e38-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3e38-109">특성</span><span class="sxs-lookup"><span data-stu-id="c3e38-109">Attributes</span></span>

<span data-ttu-id="c3e38-110">없음</span><span class="sxs-lookup"><span data-stu-id="c3e38-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3e38-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-111">Child Elements</span></span>

|<span data-ttu-id="c3e38-112">요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-112">Element</span></span>|<span data-ttu-id="c3e38-113">설명</span><span class="sxs-lookup"><span data-stu-id="c3e38-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="c3e38-114">Required 요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-114">Required Element</span></span>|
|[<span data-ttu-id="c3e38-115">GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="c3e38-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c3e38-117">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="c3e38-118">GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="c3e38-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c3e38-120">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="c3e38-121">GroupBy의 Frame에 대한 LeftIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="c3e38-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c3e38-123">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="c3e38-124">[GroupBy의 프레임에 대 한 Rightindent 요소 (형식)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="c3e38-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c3e38-126">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c3e38-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-127">Parent Elements</span></span>

|<span data-ttu-id="c3e38-128">요소</span><span class="sxs-lookup"><span data-stu-id="c3e38-128">Element</span></span>|<span data-ttu-id="c3e38-129">설명</span><span class="sxs-lookup"><span data-stu-id="c3e38-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3e38-130">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="c3e38-131">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3e38-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c3e38-132">설명</span><span class="sxs-lookup"><span data-stu-id="c3e38-132">Remarks</span></span>

<span data-ttu-id="c3e38-133">같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="c3e38-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3e38-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3e38-134">See Also</span></span>

[<span data-ttu-id="c3e38-135">GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c3e38-136">GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c3e38-137">GroupBy의 Frame에 대한 LeftIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c3e38-138">GroupBy의 Frame에 대한 RightIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c3e38-139">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3e38-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="c3e38-140">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c3e38-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
