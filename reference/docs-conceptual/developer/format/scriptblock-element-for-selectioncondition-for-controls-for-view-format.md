---
title: View 컨트롤의 SelectionCondition에 대 한 ScriptBlock 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364802"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="5af53-102">View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5af53-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="5af53-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5af53-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="5af53-104">이 스크립트를 `true`으로 평가 하면 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5af53-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="5af53-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5af53-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5af53-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. View (format) CustomControl 컨트롤에 대 한 컨트롤의 CustomEntry 요소에 대 한 컨트롤에 대 한 Customentry 요소에 대 한 컨트롤의 CustomEntry 요소 Format) 뷰 컨트롤의 SelectionCondition에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5af53-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5af53-107">구문</span><span class="sxs-lookup"><span data-stu-id="5af53-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5af53-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5af53-108">Attributes and Elements</span></span>

<span data-ttu-id="5af53-109">다음 섹션에서는 `ScriptBlock` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5af53-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5af53-110">특성</span><span class="sxs-lookup"><span data-stu-id="5af53-110">Attributes</span></span>

<span data-ttu-id="5af53-111">없음</span><span class="sxs-lookup"><span data-stu-id="5af53-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5af53-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5af53-112">Child Elements</span></span>

<span data-ttu-id="5af53-113">없음</span><span class="sxs-lookup"><span data-stu-id="5af53-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5af53-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5af53-114">Parent Elements</span></span>

|<span data-ttu-id="5af53-115">요소</span><span class="sxs-lookup"><span data-stu-id="5af53-115">Element</span></span>|<span data-ttu-id="5af53-116">설명</span><span class="sxs-lookup"><span data-stu-id="5af53-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5af53-117">보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5af53-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5af53-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5af53-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5af53-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="5af53-119">Text Value</span></span>

<span data-ttu-id="5af53-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5af53-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="5af53-121">설명</span><span class="sxs-lookup"><span data-stu-id="5af53-121">Remarks</span></span>

<span data-ttu-id="5af53-122">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5af53-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5af53-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5af53-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5af53-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5af53-124">See Also</span></span>

[<span data-ttu-id="5af53-125">보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="5af53-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="5af53-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5af53-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
