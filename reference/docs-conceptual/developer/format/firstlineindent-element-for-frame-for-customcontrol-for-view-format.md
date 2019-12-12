---
title: View (Format)의 CustomControl에 대 한 Frame의 FirstLineIndent 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363062"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="25b90-102">View에 대한 CustomControl의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="25b90-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="25b90-103">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b90-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="25b90-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b90-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="25b90-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 CustomControl for View (Format) FirstLineIndent 요소에 대 한 Customentry에 대 한 CustomControlView (Format) Frame 요소의 CustomEntry</span><span class="sxs-lookup"><span data-stu-id="25b90-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="25b90-106">구문</span><span class="sxs-lookup"><span data-stu-id="25b90-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25b90-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="25b90-107">Attributes and Elements</span></span>

<span data-ttu-id="25b90-108">다음 섹션에서는 특성, 자식 요소 및 `FirstLineIndent` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b90-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25b90-109">특성</span><span class="sxs-lookup"><span data-stu-id="25b90-109">Attributes</span></span>

<span data-ttu-id="25b90-110">없음</span><span class="sxs-lookup"><span data-stu-id="25b90-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25b90-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="25b90-111">Child Elements</span></span>

<span data-ttu-id="25b90-112">없음</span><span class="sxs-lookup"><span data-stu-id="25b90-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25b90-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="25b90-113">Parent Elements</span></span>

|<span data-ttu-id="25b90-114">요소</span><span class="sxs-lookup"><span data-stu-id="25b90-114">Element</span></span>|<span data-ttu-id="25b90-115">설명</span><span class="sxs-lookup"><span data-stu-id="25b90-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25b90-116">CustomControl의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="25b90-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="25b90-117">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b90-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="25b90-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="25b90-118">Text Value</span></span>

<span data-ttu-id="25b90-119">데이터의 첫 줄을 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b90-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="25b90-120">설명</span><span class="sxs-lookup"><span data-stu-id="25b90-120">Remarks</span></span>

<span data-ttu-id="25b90-121">이 요소를 지정 하는 경우 [Firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25b90-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="25b90-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25b90-122">See Also</span></span>

[<span data-ttu-id="25b90-123">보기에 대 한 CustomControl Frame의 FirstLineHanging 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="25b90-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="25b90-124">CustomControl의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="25b90-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="25b90-125">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="25b90-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
