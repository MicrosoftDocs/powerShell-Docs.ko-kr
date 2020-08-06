---
title: 뷰의 컨트롤 프레임에 대 한 FirstLineHanging 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 88c64619715c935089eb6c5a771584e4f69171d3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773626"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="352e9-102">View에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="352e9-102">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="352e9-103">첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="352e9-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="352e9-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="352e9-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="352e9-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤 요소 (format) CustomControl 요소에 대 한 컨트롤에 대 한 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 CustomControl for View (Format) Customentries 보기 (형식)의 컨트롤에 대 한 CustomEntries 컨트롤의 Customentries 요소 컨트롤에 대 한 Customentries 요소 컨트롤의 customentries에 대 한 컨트롤의 Customentries에 대 한 컨트롤의 Customentries에 대 한 컨트롤의 요소입니다. (형식)</span><span class="sxs-lookup"><span data-stu-id="352e9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineHanging Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="352e9-106">구문</span><span class="sxs-lookup"><span data-stu-id="352e9-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="352e9-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="352e9-107">Attributes and Elements</span></span>

<span data-ttu-id="352e9-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `FirstLineHanging` .</span><span class="sxs-lookup"><span data-stu-id="352e9-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="352e9-109">특성</span><span class="sxs-lookup"><span data-stu-id="352e9-109">Attributes</span></span>

<span data-ttu-id="352e9-110">없음</span><span class="sxs-lookup"><span data-stu-id="352e9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="352e9-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="352e9-111">Child Elements</span></span>

<span data-ttu-id="352e9-112">없음</span><span class="sxs-lookup"><span data-stu-id="352e9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="352e9-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="352e9-113">Parent Elements</span></span>

|<span data-ttu-id="352e9-114">요소</span><span class="sxs-lookup"><span data-stu-id="352e9-114">Element</span></span>|<span data-ttu-id="352e9-115">설명</span><span class="sxs-lookup"><span data-stu-id="352e9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="352e9-116">View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="352e9-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="352e9-117">데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="352e9-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="352e9-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="352e9-118">Text Value</span></span>

<span data-ttu-id="352e9-119">데이터의 첫 줄을 이동할 문자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="352e9-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="352e9-120">설명</span><span class="sxs-lookup"><span data-stu-id="352e9-120">Remarks</span></span>

<span data-ttu-id="352e9-121">이 요소를 지정 하는 경우 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="352e9-121">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="352e9-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="352e9-122">See Also</span></span>

[<span data-ttu-id="352e9-123">View에 대한 Controls의 Frame에 대한 FirstLineIndent 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="352e9-123">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="352e9-124">View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="352e9-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="352e9-125">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="352e9-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
