---
title: 구성에 대 한 컨트롤의 프레임에 대 한 FirstLineHanging 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363172"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="75584-102">Configuration에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="75584-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="75584-103">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75584-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="75584-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75584-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="75584-105">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) CustomControl에 대 한 컨트롤의 CustomEntry 요소 구성 (Format) Customentry 요소 구성 요소에 대 한 컨트롤의 Customentry 요소 구성 (형식)에 대 한 요소 구성 (형식)에 대 한 컨트롤</span><span class="sxs-lookup"><span data-stu-id="75584-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75584-106">구문</span><span class="sxs-lookup"><span data-stu-id="75584-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75584-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="75584-107">Attributes and Elements</span></span>

<span data-ttu-id="75584-108">다음 섹션에서는 `FirstLineHanging` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="75584-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75584-109">특성</span><span class="sxs-lookup"><span data-stu-id="75584-109">Attributes</span></span>

<span data-ttu-id="75584-110">없음</span><span class="sxs-lookup"><span data-stu-id="75584-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75584-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="75584-111">Child Elements</span></span>

<span data-ttu-id="75584-112">없음</span><span class="sxs-lookup"><span data-stu-id="75584-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75584-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="75584-113">Parent Elements</span></span>

|<span data-ttu-id="75584-114">요소</span><span class="sxs-lookup"><span data-stu-id="75584-114">Element</span></span>|<span data-ttu-id="75584-115">설명</span><span class="sxs-lookup"><span data-stu-id="75584-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75584-116">구성에 대 한 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="75584-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="75584-117">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="75584-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="75584-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="75584-118">Text Value</span></span>

<span data-ttu-id="75584-119">데이터의 첫 줄을 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="75584-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="75584-120">설명</span><span class="sxs-lookup"><span data-stu-id="75584-120">Remarks</span></span>

<span data-ttu-id="75584-121">이 요소를 지정 하는 경우 `FirstLineIndent` 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="75584-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="75584-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75584-122">See Also</span></span>

[<span data-ttu-id="75584-123">구성에 대 한 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="75584-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="75584-124">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="75584-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
