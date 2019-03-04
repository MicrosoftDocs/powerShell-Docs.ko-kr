---
title: 뷰 (형식)에 대 한 CustomControl 프레임에 대 한 FirstLineIndent 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 9ec6caedcb7cf20d4aab2216cd8a9707269d9452
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854959"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="db7fb-102">View에 대한 CustomControl의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db7fb-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="db7fb-103">데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db7fb-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="db7fb-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db7fb-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="db7fb-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CutomControlView (형식) 프레임에 대 한 요소의 CustomControl (형식) 보기 FirstLineIndent 요소에 대 한 CustomItem CustomEntry</span><span class="sxs-lookup"><span data-stu-id="db7fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="db7fb-106">구문</span><span class="sxs-lookup"><span data-stu-id="db7fb-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db7fb-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="db7fb-107">Attributes and Elements</span></span>

<span data-ttu-id="db7fb-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `FirstLineIndent` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="db7fb-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db7fb-109">특성</span><span class="sxs-lookup"><span data-stu-id="db7fb-109">Attributes</span></span>

<span data-ttu-id="db7fb-110">없음</span><span class="sxs-lookup"><span data-stu-id="db7fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db7fb-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="db7fb-111">Child Elements</span></span>

<span data-ttu-id="db7fb-112">없음</span><span class="sxs-lookup"><span data-stu-id="db7fb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="db7fb-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="db7fb-113">Parent Elements</span></span>

|<span data-ttu-id="db7fb-114">요소</span><span class="sxs-lookup"><span data-stu-id="db7fb-114">Element</span></span>|<span data-ttu-id="db7fb-115">설명</span><span class="sxs-lookup"><span data-stu-id="db7fb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db7fb-116">CustomItem CustomControl 보려면 (형식)에 대 한 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="db7fb-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="db7fb-117">왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="db7fb-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="db7fb-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="db7fb-118">Text Value</span></span>

<span data-ttu-id="db7fb-119">데이터의 첫 번째 줄을 이동 하려는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db7fb-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="db7fb-120">설명</span><span class="sxs-lookup"><span data-stu-id="db7fb-120">Remarks</span></span>

<span data-ttu-id="db7fb-121">이 요소를 지정 하는 경우를 지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="db7fb-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="db7fb-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db7fb-122">See Also</span></span>

[<span data-ttu-id="db7fb-123">뷰 (형식)에 대 한 CustomControl 프레임에 대 한 FirstLineHanging 요소</span><span class="sxs-lookup"><span data-stu-id="db7fb-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db7fb-124">CustomItem CustomControl 보려면 (형식)에 대 한 프레임 요소</span><span class="sxs-lookup"><span data-stu-id="db7fb-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="db7fb-125">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="db7fb-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
