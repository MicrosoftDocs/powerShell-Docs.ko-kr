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
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861709"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="1cbfe-102">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1cbfe-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="1cbfe-103">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="1cbfe-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1cbfe-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CutomControlView (형식) 프레임에 대 한 요소의 CustomControl 보려면 (형식)에 대 한 CustomItem CustomEntry</span><span class="sxs-lookup"><span data-stu-id="1cbfe-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1cbfe-106">구문</span><span class="sxs-lookup"><span data-stu-id="1cbfe-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1cbfe-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-107">Attributes and Elements</span></span>

<span data-ttu-id="1cbfe-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1cbfe-109">특성</span><span class="sxs-lookup"><span data-stu-id="1cbfe-109">Attributes</span></span>

<span data-ttu-id="1cbfe-110">없음</span><span class="sxs-lookup"><span data-stu-id="1cbfe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1cbfe-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-111">Child Elements</span></span>

|<span data-ttu-id="1cbfe-112">요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-112">Element</span></span>|<span data-ttu-id="1cbfe-113">설명</span><span class="sxs-lookup"><span data-stu-id="1cbfe-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="1cbfe-114">필수 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-114">Required Element</span></span>|
|[<span data-ttu-id="1cbfe-115">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1cbfe-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-116">Optional element.</span></span><br /><br /> <span data-ttu-id="1cbfe-117">데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="1cbfe-118">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1cbfe-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-119">Optional element.</span></span><br /><br /> <span data-ttu-id="1cbfe-120">데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="1cbfe-121">LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1cbfe-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-122">Optional element.</span></span><br /><br /> <span data-ttu-id="1cbfe-123">왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="1cbfe-124">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="1cbfe-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-125">Optional element.</span></span><br /><br /> <span data-ttu-id="1cbfe-126">오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1cbfe-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-127">Parent Elements</span></span>

|<span data-ttu-id="1cbfe-128">요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-128">Element</span></span>|<span data-ttu-id="1cbfe-129">설명</span><span class="sxs-lookup"><span data-stu-id="1cbfe-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1cbfe-130">뷰 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1cbfe-131">컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1cbfe-132">설명</span><span class="sxs-lookup"><span data-stu-id="1cbfe-132">Remarks</span></span>

<span data-ttu-id="1cbfe-133">지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 하며 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 동일한 요소 `Frame` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1cbfe-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cbfe-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1cbfe-134">See Also</span></span>

[<span data-ttu-id="1cbfe-135">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1cbfe-136">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1cbfe-137">LeftIndent 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1cbfe-138">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1cbfe-139">뷰 (형식)에 대 한 CustomEntry CustomItem 요소</span><span class="sxs-lookup"><span data-stu-id="1cbfe-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1cbfe-140">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1cbfe-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
