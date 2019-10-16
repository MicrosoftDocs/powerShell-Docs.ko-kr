---
title: 구성 (형식)의 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368622"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="ac0aa-102">Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ac0aa-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ac0aa-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ac0aa-104">이 스크립트를 `true`으로 평가 하면 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="ac0aa-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ac0aa-106">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) CustomControl에 대 한 컨트롤의 CustomEntry 요소 구성 (형식)의 컨트롤에 대 한 CustomEntry 요소 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 SelectionCondition 요소 구성 (형식)에 대 한 컨트롤입니다. 구성 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ac0aa-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac0aa-107">구문</span><span class="sxs-lookup"><span data-stu-id="ac0aa-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac0aa-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ac0aa-108">Attributes and Elements</span></span>

<span data-ttu-id="ac0aa-109">다음 섹션에서는 `ScriptBlock` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac0aa-110">특성</span><span class="sxs-lookup"><span data-stu-id="ac0aa-110">Attributes</span></span>

<span data-ttu-id="ac0aa-111">없음</span><span class="sxs-lookup"><span data-stu-id="ac0aa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac0aa-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ac0aa-112">Child Elements</span></span>

<span data-ttu-id="ac0aa-113">없음</span><span class="sxs-lookup"><span data-stu-id="ac0aa-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac0aa-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ac0aa-114">Parent Elements</span></span>

|<span data-ttu-id="ac0aa-115">요소</span><span class="sxs-lookup"><span data-stu-id="ac0aa-115">Element</span></span>|<span data-ttu-id="ac0aa-116">설명</span><span class="sxs-lookup"><span data-stu-id="ac0aa-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac0aa-117">구성에 대 한 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ac0aa-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="ac0aa-118">공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac0aa-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ac0aa-119">Text Value</span></span>

<span data-ttu-id="ac0aa-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac0aa-121">설명</span><span class="sxs-lookup"><span data-stu-id="ac0aa-121">Remarks</span></span>

<span data-ttu-id="ac0aa-122">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ac0aa-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac0aa-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac0aa-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac0aa-124">See Also</span></span>

[<span data-ttu-id="ac0aa-125">구성에 대 한 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ac0aa-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac0aa-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ac0aa-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
