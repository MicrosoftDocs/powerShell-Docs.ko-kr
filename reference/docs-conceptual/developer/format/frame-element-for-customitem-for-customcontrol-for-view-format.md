---
title: CustomControl의 CustomItem에 대 한 Frame 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363642"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="533d0-102">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="533d0-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="533d0-103">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="533d0-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="533d0-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 CustomControl for View (Format)의 Customentry에 대 한 customentry 뷰 (Format) Frame 요소에 대 한 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="533d0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="533d0-106">구문</span><span class="sxs-lookup"><span data-stu-id="533d0-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="533d0-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-107">Attributes and Elements</span></span>

<span data-ttu-id="533d0-108">다음 섹션에서는 `Frame` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="533d0-109">특성</span><span class="sxs-lookup"><span data-stu-id="533d0-109">Attributes</span></span>

<span data-ttu-id="533d0-110">없음</span><span class="sxs-lookup"><span data-stu-id="533d0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="533d0-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-111">Child Elements</span></span>

|<span data-ttu-id="533d0-112">요소</span><span class="sxs-lookup"><span data-stu-id="533d0-112">Element</span></span>|<span data-ttu-id="533d0-113">설명</span><span class="sxs-lookup"><span data-stu-id="533d0-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="533d0-114">Required 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-114">Required Element</span></span>|
|[<span data-ttu-id="533d0-115">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="533d0-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="533d0-117">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="533d0-118">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="533d0-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="533d0-120">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="533d0-121">왼쪽 들여쓰기 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="533d0-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-122">Optional element.</span></span><br /><br /> <span data-ttu-id="533d0-123">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="533d0-124">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="533d0-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-125">Optional element.</span></span><br /><br /> <span data-ttu-id="533d0-126">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="533d0-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-127">Parent Elements</span></span>

|<span data-ttu-id="533d0-128">요소</span><span class="sxs-lookup"><span data-stu-id="533d0-128">Element</span></span>|<span data-ttu-id="533d0-129">설명</span><span class="sxs-lookup"><span data-stu-id="533d0-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="533d0-130">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="533d0-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="533d0-131">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="533d0-132">설명</span><span class="sxs-lookup"><span data-stu-id="533d0-132">Remarks</span></span>

<span data-ttu-id="533d0-133">같은 `Frame` 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="533d0-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="533d0-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="533d0-134">See Also</span></span>

[<span data-ttu-id="533d0-135">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="533d0-136">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="533d0-137">왼쪽 들여쓰기 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="533d0-138">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="533d0-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="533d0-139">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="533d0-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="533d0-140">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="533d0-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
