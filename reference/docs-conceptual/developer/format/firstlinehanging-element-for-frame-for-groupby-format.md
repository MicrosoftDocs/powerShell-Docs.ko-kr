---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)
description: GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)
ms.openlocfilehash: 6a4ded9cced484440636aee694cd8381b2889ba8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652265"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="ac8cb-103">GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ac8cb-103">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="ac8cb-104">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8cb-104">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="ac8cb-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac8cb-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ac8cb-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl 요소의 groupby (format) CustomEntries 요소에 대 한 groupby 요소 (형식) Customentries 요소 groupby (format) Customentries 요소에 대 한 CustomControl 요소에 대 한 customentries 요소에 대 한 customentries에 대 한 Customentries의 경우 groupby (형식)에 대 한 프레임의 groupby 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ac8cb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac8cb-107">구문</span><span class="sxs-lookup"><span data-stu-id="ac8cb-107">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac8cb-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ac8cb-108">Attributes and Elements</span></span>

<span data-ttu-id="ac8cb-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `FirstLineHanging` .</span><span class="sxs-lookup"><span data-stu-id="ac8cb-109">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac8cb-110">특성</span><span class="sxs-lookup"><span data-stu-id="ac8cb-110">Attributes</span></span>

<span data-ttu-id="ac8cb-111">없음</span><span class="sxs-lookup"><span data-stu-id="ac8cb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac8cb-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ac8cb-112">Child Elements</span></span>

<span data-ttu-id="ac8cb-113">없음</span><span class="sxs-lookup"><span data-stu-id="ac8cb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac8cb-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ac8cb-114">Parent Elements</span></span>

|<span data-ttu-id="ac8cb-115">요소</span><span class="sxs-lookup"><span data-stu-id="ac8cb-115">Element</span></span>|<span data-ttu-id="ac8cb-116">설명</span><span class="sxs-lookup"><span data-stu-id="ac8cb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac8cb-117">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ac8cb-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="ac8cb-118">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8cb-118">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac8cb-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ac8cb-119">Text Value</span></span>

<span data-ttu-id="ac8cb-120">데이터의 첫 줄을 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac8cb-120">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac8cb-121">설명</span><span class="sxs-lookup"><span data-stu-id="ac8cb-121">Remarks</span></span>

<span data-ttu-id="ac8cb-122">이 요소를 지정 하는 경우 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac8cb-122">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac8cb-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac8cb-123">See Also</span></span>

[<span data-ttu-id="ac8cb-124">GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ac8cb-124">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="ac8cb-125">GroupBy의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ac8cb-125">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="ac8cb-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ac8cb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
