---
title: CustomControl의 CustomItem에 대 한 Frame 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4864ea1a865f77c9de6e495d7e8296e81c19b366
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781446"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="98d63-102">View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98d63-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="98d63-103">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="98d63-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="98d63-105">Configuration 요소 (Format) Viewcontrolelement (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98d63-106">구문</span><span class="sxs-lookup"><span data-stu-id="98d63-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98d63-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-107">Attributes and Elements</span></span>

<span data-ttu-id="98d63-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="98d63-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98d63-109">특성</span><span class="sxs-lookup"><span data-stu-id="98d63-109">Attributes</span></span>

<span data-ttu-id="98d63-110">없음</span><span class="sxs-lookup"><span data-stu-id="98d63-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98d63-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-111">Child Elements</span></span>

|<span data-ttu-id="98d63-112">요소</span><span class="sxs-lookup"><span data-stu-id="98d63-112">Element</span></span>|<span data-ttu-id="98d63-113">설명</span><span class="sxs-lookup"><span data-stu-id="98d63-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="98d63-114">Required 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-114">Required Element</span></span>|
|[<span data-ttu-id="98d63-115">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="98d63-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-116">Optional element.</span></span><br /><br /> <span data-ttu-id="98d63-117">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="98d63-118">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="98d63-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-119">Optional element.</span></span><br /><br /> <span data-ttu-id="98d63-120">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="98d63-121">왼쪽 들여쓰기 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="98d63-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-122">Optional element.</span></span><br /><br /> <span data-ttu-id="98d63-123">왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="98d63-124">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="98d63-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-125">Optional element.</span></span><br /><br /> <span data-ttu-id="98d63-126">데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="98d63-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-127">Parent Elements</span></span>

|<span data-ttu-id="98d63-128">요소</span><span class="sxs-lookup"><span data-stu-id="98d63-128">Element</span></span>|<span data-ttu-id="98d63-129">설명</span><span class="sxs-lookup"><span data-stu-id="98d63-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98d63-130">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="98d63-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="98d63-131">컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d63-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98d63-132">설명</span><span class="sxs-lookup"><span data-stu-id="98d63-132">Remarks</span></span>

<span data-ttu-id="98d63-133">같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다 `Frame` .</span><span class="sxs-lookup"><span data-stu-id="98d63-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="98d63-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98d63-134">See Also</span></span>

[<span data-ttu-id="98d63-135">FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="98d63-136">FirstLineIndent 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="98d63-137">왼쪽 들여쓰기 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="98d63-138">RightIndent 요소</span><span class="sxs-lookup"><span data-stu-id="98d63-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="98d63-139">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="98d63-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="98d63-140">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="98d63-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
