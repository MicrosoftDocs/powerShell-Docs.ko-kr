---
title: 보기에 대 한 CustomControl Frame의 FirstLineHanging 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363162"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="33a5f-102">View에 대한 CustomControl의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="33a5f-102">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="33a5f-103">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33a5f-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="33a5f-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33a5f-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="33a5f-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 CustomControl for View (format)의 프레임에 대 한 CustomControl for View (Format) FirstLineHanging 요소에 대 한 CustomControlView (format) Frame 요소에 대 한 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="33a5f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33a5f-106">구문</span><span class="sxs-lookup"><span data-stu-id="33a5f-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33a5f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="33a5f-107">Attributes and Elements</span></span>

<span data-ttu-id="33a5f-108">다음 섹션에서는 `FirstLineHanging` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="33a5f-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33a5f-109">특성</span><span class="sxs-lookup"><span data-stu-id="33a5f-109">Attributes</span></span>

<span data-ttu-id="33a5f-110">없음</span><span class="sxs-lookup"><span data-stu-id="33a5f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33a5f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="33a5f-111">Child Elements</span></span>

<span data-ttu-id="33a5f-112">없음</span><span class="sxs-lookup"><span data-stu-id="33a5f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33a5f-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="33a5f-113">Parent Elements</span></span>

|<span data-ttu-id="33a5f-114">요소</span><span class="sxs-lookup"><span data-stu-id="33a5f-114">Element</span></span>|<span data-ttu-id="33a5f-115">설명</span><span class="sxs-lookup"><span data-stu-id="33a5f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33a5f-116">CustomControl의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="33a5f-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="33a5f-117">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="33a5f-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="33a5f-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="33a5f-118">Text Value</span></span>

<span data-ttu-id="33a5f-119">데이터의 첫 줄을 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33a5f-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="33a5f-120">설명</span><span class="sxs-lookup"><span data-stu-id="33a5f-120">Remarks</span></span>

<span data-ttu-id="33a5f-121">이 요소를 지정 하는 경우 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33a5f-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="33a5f-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33a5f-122">See Also</span></span>

[<span data-ttu-id="33a5f-123">CustomControl에 대 한 Frame 요소에 대 한 FirstLineIndent 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="33a5f-123">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33a5f-124">CustomControl의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="33a5f-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33a5f-125">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="33a5f-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
