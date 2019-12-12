---
title: GroupBy (Format)의 프레임에 대 한 FirstLineIndent 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363082"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="856e8-102">GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="856e8-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="856e8-103">첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="856e8-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="856e8-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="856e8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="856e8-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 customitem 요소에 대 한 CustomControl 요소에 대 한 CustomItem의 경우 groupby (format)의 경우 Frame 요소는 groupby (형식)에 대 한 Frame 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="856e8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="856e8-106">구문</span><span class="sxs-lookup"><span data-stu-id="856e8-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="856e8-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="856e8-107">Attributes and Elements</span></span>

<span data-ttu-id="856e8-108">다음 섹션에서는 특성, 자식 요소 및 `FirstLineIndent` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="856e8-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="856e8-109">특성</span><span class="sxs-lookup"><span data-stu-id="856e8-109">Attributes</span></span>

<span data-ttu-id="856e8-110">없음</span><span class="sxs-lookup"><span data-stu-id="856e8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="856e8-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="856e8-111">Child Elements</span></span>

<span data-ttu-id="856e8-112">없음</span><span class="sxs-lookup"><span data-stu-id="856e8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="856e8-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="856e8-113">Parent Elements</span></span>

|<span data-ttu-id="856e8-114">요소</span><span class="sxs-lookup"><span data-stu-id="856e8-114">Element</span></span>|<span data-ttu-id="856e8-115">설명</span><span class="sxs-lookup"><span data-stu-id="856e8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="856e8-116">GroupBy의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="856e8-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="856e8-117">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="856e8-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="856e8-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="856e8-118">Text Value</span></span>

<span data-ttu-id="856e8-119">데이터의 첫 줄을 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="856e8-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="856e8-120">설명</span><span class="sxs-lookup"><span data-stu-id="856e8-120">Remarks</span></span>

<span data-ttu-id="856e8-121">이 요소를 지정 하는 경우 [Firstlinehanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="856e8-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="856e8-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="856e8-122">See Also</span></span>

[<span data-ttu-id="856e8-123">GroupBy의 프레임에 대 한 FirstLineHanging 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="856e8-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="856e8-124">GroupBy의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="856e8-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="856e8-125">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="856e8-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
