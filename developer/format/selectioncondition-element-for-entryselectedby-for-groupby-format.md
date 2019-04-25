---
title: GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075718"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="e1581-102">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e1581-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="e1581-103">사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="e1581-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e1581-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 GroupBy (형식)에 대 한 GroupBy (형식) EntrySelectedBy 요소에</span><span class="sxs-lookup"><span data-stu-id="e1581-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1581-106">구문</span><span class="sxs-lookup"><span data-stu-id="e1581-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1581-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-107">Attributes and Elements</span></span>

<span data-ttu-id="e1581-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1581-109">특성</span><span class="sxs-lookup"><span data-stu-id="e1581-109">Attributes</span></span>

<span data-ttu-id="e1581-110">없음</span><span class="sxs-lookup"><span data-stu-id="e1581-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1581-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-111">Child Elements</span></span>

|<span data-ttu-id="e1581-112">요소</span><span class="sxs-lookup"><span data-stu-id="e1581-112">Element</span></span>|<span data-ttu-id="e1581-113">설명</span><span class="sxs-lookup"><span data-stu-id="e1581-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1581-114">GroupBy (형식)에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="e1581-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e1581-116">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e1581-117">GroupBy (형식)에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="e1581-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e1581-119">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e1581-120">GroupBy (형식)에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="e1581-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e1581-122">조건이 트리거하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="e1581-123">GroupBy (형식)에 대 한 SelectionCondition TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="e1581-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e1581-125">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1581-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-126">Parent Elements</span></span>

|<span data-ttu-id="e1581-127">요소</span><span class="sxs-lookup"><span data-stu-id="e1581-127">Element</span></span>|<span data-ttu-id="e1581-128">설명</span><span class="sxs-lookup"><span data-stu-id="e1581-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1581-129">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e1581-130">이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1581-131">설명</span><span class="sxs-lookup"><span data-stu-id="e1581-131">Remarks</span></span>

<span data-ttu-id="e1581-132">선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="e1581-133">선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e1581-134">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e1581-135">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e1581-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1581-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1581-136">See Also</span></span>

[<span data-ttu-id="e1581-137">PropertyName SelectionCondition CustomControl 보려면 (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e1581-138">CustomControl 보려면 (형식)에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e1581-139">뷰 (형식)에 대 한 사용자 지정 컨트롤에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e1581-140">GroupBy (형식)에 대 한 SelectionCondition TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="e1581-141">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="e1581-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e1581-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="e1581-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
