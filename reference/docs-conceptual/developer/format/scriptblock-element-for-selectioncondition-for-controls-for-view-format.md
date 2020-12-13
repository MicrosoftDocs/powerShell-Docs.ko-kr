---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)
description: View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: 7eed3b8a06bc45396026b8e2a7454447b3090d74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664937"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="48d80-103">View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="48d80-103">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="48d80-104">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="48d80-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="48d80-105">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48d80-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="48d80-106">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48d80-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="48d80-107">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소입니다. view (format) EntrySelectedBy의 컨트롤에 대 한 CustomEntries 요소의 항목 요소에 대 한 참조 요소 뷰 (format)의 컨트롤에 대 한 컨트롤의 SelectionCondition 요소에 대 한 컨트롤에 대 한 SelectionCondition 요소에 대 한 컨트롤의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="48d80-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48d80-108">구문</span><span class="sxs-lookup"><span data-stu-id="48d80-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48d80-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="48d80-109">Attributes and Elements</span></span>

<span data-ttu-id="48d80-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="48d80-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48d80-111">특성</span><span class="sxs-lookup"><span data-stu-id="48d80-111">Attributes</span></span>

<span data-ttu-id="48d80-112">없음</span><span class="sxs-lookup"><span data-stu-id="48d80-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48d80-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="48d80-113">Child Elements</span></span>

<span data-ttu-id="48d80-114">없음</span><span class="sxs-lookup"><span data-stu-id="48d80-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48d80-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="48d80-115">Parent Elements</span></span>

|<span data-ttu-id="48d80-116">요소</span><span class="sxs-lookup"><span data-stu-id="48d80-116">Element</span></span>|<span data-ttu-id="48d80-117">설명</span><span class="sxs-lookup"><span data-stu-id="48d80-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48d80-118">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="48d80-118">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="48d80-119">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="48d80-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="48d80-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="48d80-120">Text Value</span></span>

<span data-ttu-id="48d80-121">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="48d80-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="48d80-122">설명</span><span class="sxs-lookup"><span data-stu-id="48d80-122">Remarks</span></span>

<span data-ttu-id="48d80-123">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="48d80-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="48d80-124">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="48d80-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48d80-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48d80-125">See Also</span></span>

[<span data-ttu-id="48d80-126">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="48d80-126">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="48d80-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="48d80-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
