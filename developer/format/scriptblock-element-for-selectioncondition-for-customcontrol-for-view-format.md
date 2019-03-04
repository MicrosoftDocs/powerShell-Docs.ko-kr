---
title: ScriptBlock 요소 CustomControl 보려면 (형식)에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857419"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="fe59c-102">View에 대한 CustomControl의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fe59c-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="fe59c-103">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fe59c-104">이 스크립트를 계산할 때 `true`조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="fe59c-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="fe59c-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 CustomControl CustomEntries CustomControl 보기 (에 대 한 보기 (형식) CustomEntry 요소에 대 한 보기 (형식) CustomEntries 요소에 CustomControl EntrySelectedBy CustomControl SelectionCondition CustomControl 보려면 (형식)에 대 한 보기 (형식) ScriptBlock 요소에 대 한 보기 (형식) SelectionCondition 요소에 대 한 CustomEntry CustomItem 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="fe59c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe59c-107">구문</span><span class="sxs-lookup"><span data-stu-id="fe59c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe59c-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fe59c-108">Attributes and Elements</span></span>

<span data-ttu-id="fe59c-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe59c-110">특성</span><span class="sxs-lookup"><span data-stu-id="fe59c-110">Attributes</span></span>

<span data-ttu-id="fe59c-111">없음</span><span class="sxs-lookup"><span data-stu-id="fe59c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe59c-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fe59c-112">Child Elements</span></span>

<span data-ttu-id="fe59c-113">없음</span><span class="sxs-lookup"><span data-stu-id="fe59c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe59c-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fe59c-114">Parent Elements</span></span>

|<span data-ttu-id="fe59c-115">요소</span><span class="sxs-lookup"><span data-stu-id="fe59c-115">Element</span></span>|<span data-ttu-id="fe59c-116">설명</span><span class="sxs-lookup"><span data-stu-id="fe59c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe59c-117">CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="fe59c-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="fe59c-118">사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe59c-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="fe59c-119">Text Value</span></span>

<span data-ttu-id="fe59c-120">계산 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe59c-121">설명</span><span class="sxs-lookup"><span data-stu-id="fe59c-121">Remarks</span></span>

<span data-ttu-id="fe59c-122">선택 조건 최소 하나의 스크립트 또는 속성 이름을 평가 수행 하려면을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="fe59c-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fe59c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe59c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe59c-124">See Also</span></span>

[<span data-ttu-id="fe59c-125">CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="fe59c-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="fe59c-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="fe59c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
