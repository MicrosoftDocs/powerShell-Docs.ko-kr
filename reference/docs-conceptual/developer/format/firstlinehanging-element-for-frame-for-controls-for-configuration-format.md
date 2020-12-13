---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)
description: Configuration에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)
ms.openlocfilehash: 94d59ef7b54e036f76e38a3b06b769700443b9fb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655223"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="b5c50-103">Configuration에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5c50-103">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b5c50-104">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c50-104">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="b5c50-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5c50-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b5c50-106">구성 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) Customentries 요소에 대 한 구성 (형식) CustomEntries 요소 CustomControl for Controls for Configuration (Format) Customentries 요소 컨트롤에 대 한 컨트롤의 customentries 요소 구성의 컨트롤에 대 한 Customentries 요소 구성 (형식)</span><span class="sxs-lookup"><span data-stu-id="b5c50-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5c50-107">구문</span><span class="sxs-lookup"><span data-stu-id="b5c50-107">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5c50-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b5c50-108">Attributes and Elements</span></span>

<span data-ttu-id="b5c50-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `FirstLineHanging` .</span><span class="sxs-lookup"><span data-stu-id="b5c50-109">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5c50-110">특성</span><span class="sxs-lookup"><span data-stu-id="b5c50-110">Attributes</span></span>

<span data-ttu-id="b5c50-111">없음</span><span class="sxs-lookup"><span data-stu-id="b5c50-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5c50-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b5c50-112">Child Elements</span></span>

<span data-ttu-id="b5c50-113">없음</span><span class="sxs-lookup"><span data-stu-id="b5c50-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5c50-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b5c50-114">Parent Elements</span></span>

|<span data-ttu-id="b5c50-115">요소</span><span class="sxs-lookup"><span data-stu-id="b5c50-115">Element</span></span>|<span data-ttu-id="b5c50-116">설명</span><span class="sxs-lookup"><span data-stu-id="b5c50-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5c50-117">Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5c50-117">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b5c50-118">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c50-118">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5c50-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b5c50-119">Text Value</span></span>

<span data-ttu-id="b5c50-120">데이터의 첫 줄을 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5c50-120">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5c50-121">설명</span><span class="sxs-lookup"><span data-stu-id="b5c50-121">Remarks</span></span>

<span data-ttu-id="b5c50-122">이 요소를 지정 하면 요소를 지정할 수 없습니다 `FirstLineIndent` .</span><span class="sxs-lookup"><span data-stu-id="b5c50-122">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5c50-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5c50-123">See Also</span></span>

[<span data-ttu-id="b5c50-124">Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5c50-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b5c50-125">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b5c50-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
