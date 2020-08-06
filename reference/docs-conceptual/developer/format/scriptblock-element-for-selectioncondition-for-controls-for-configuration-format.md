---
title: 구성 (형식)의 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24584aacd7869abd3dcfc6ff546e6dea4c2c04fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785441"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="b5ce3-102">Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5ce3-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b5ce3-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="b5ce3-104">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="b5ce3-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b5ce3-106">구성 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) Customentries 요소에 대 한 CustomControl 요소에 대 한 CustomControl configuration (format) EntrySelectedBy 요소에 대해 구성 (format)의 컨트롤에 대 한 컨트롤에 대 한 컨트롤에 대 한 구성 (형식) ScriptBlock 요소에 대 한 컨트롤의 selectioncondition 요소 구성 (형식)에 대 한 컨트롤의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b5ce3-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5ce3-107">구문</span><span class="sxs-lookup"><span data-stu-id="b5ce3-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5ce3-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b5ce3-108">Attributes and Elements</span></span>

<span data-ttu-id="b5ce3-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="b5ce3-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5ce3-110">특성</span><span class="sxs-lookup"><span data-stu-id="b5ce3-110">Attributes</span></span>

<span data-ttu-id="b5ce3-111">없음</span><span class="sxs-lookup"><span data-stu-id="b5ce3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5ce3-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b5ce3-112">Child Elements</span></span>

<span data-ttu-id="b5ce3-113">없음</span><span class="sxs-lookup"><span data-stu-id="b5ce3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5ce3-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b5ce3-114">Parent Elements</span></span>

|<span data-ttu-id="b5ce3-115">요소</span><span class="sxs-lookup"><span data-stu-id="b5ce3-115">Element</span></span>|<span data-ttu-id="b5ce3-116">설명</span><span class="sxs-lookup"><span data-stu-id="b5ce3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5ce3-117">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5ce3-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b5ce3-118">공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5ce3-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b5ce3-119">Text Value</span></span>

<span data-ttu-id="b5ce3-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5ce3-121">설명</span><span class="sxs-lookup"><span data-stu-id="b5ce3-121">Remarks</span></span>

<span data-ttu-id="b5ce3-122">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b5ce3-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5ce3-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5ce3-124">See Also</span></span>

[<span data-ttu-id="b5ce3-125">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5ce3-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="b5ce3-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b5ce3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
