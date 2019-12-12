---
title: GroupBy (형식)를 위해 EntrySelectedBy의 SelectionCondition에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368602"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="b845d-102">GroupBy에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b845d-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="b845d-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b845d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="b845d-104">이 스크립트가 `true`평가 되 면 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b845d-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="b845d-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b845d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b845d-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) EntrySelectedBy 요소에 대 한 CustomControl 요소에 대 한 CustomEntry for groupby (형식)에 대 한 selectioncondition 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="b845d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b845d-107">구문</span><span class="sxs-lookup"><span data-stu-id="b845d-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b845d-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b845d-108">Attributes and Elements</span></span>

<span data-ttu-id="b845d-109">다음 섹션에서는 특성, 자식 요소 및 `ScriptBlock` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b845d-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b845d-110">특성</span><span class="sxs-lookup"><span data-stu-id="b845d-110">Attributes</span></span>

<span data-ttu-id="b845d-111">없음</span><span class="sxs-lookup"><span data-stu-id="b845d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b845d-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b845d-112">Child Elements</span></span>

<span data-ttu-id="b845d-113">없음</span><span class="sxs-lookup"><span data-stu-id="b845d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b845d-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b845d-114">Parent Elements</span></span>

|<span data-ttu-id="b845d-115">요소</span><span class="sxs-lookup"><span data-stu-id="b845d-115">Element</span></span>|<span data-ttu-id="b845d-116">설명</span><span class="sxs-lookup"><span data-stu-id="b845d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b845d-117">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b845d-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="b845d-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b845d-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b845d-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b845d-119">Text Value</span></span>

<span data-ttu-id="b845d-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b845d-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b845d-121">설명</span><span class="sxs-lookup"><span data-stu-id="b845d-121">Remarks</span></span>

<span data-ttu-id="b845d-122">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b845d-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b845d-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b845d-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b845d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b845d-124">See Also</span></span>

[<span data-ttu-id="b845d-125">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b845d-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="b845d-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b845d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
