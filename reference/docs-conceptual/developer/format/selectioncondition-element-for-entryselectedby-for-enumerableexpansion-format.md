---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: 3ecf7fde99b9ee66a153eea416792f351ff62af3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647916"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="dd0dc-103">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-103">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="dd0dc-104">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-104">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="dd0dc-105">Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)-enumerableexpansions (format)의 경우 entryselectedby 요소에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="dd0dc-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd0dc-106">구문</span><span class="sxs-lookup"><span data-stu-id="dd0dc-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd0dc-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="dd0dc-107">Attributes and Elements</span></span>

<span data-ttu-id="dd0dc-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="dd0dc-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="dd0dc-109">단일 또는 요소를 지정 해야 합니다 `PropertyName` `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="dd0dc-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="dd0dc-110">`SelectionSetName`및 `TypeName` 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="dd0dc-111">두 요소 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd0dc-112">특성</span><span class="sxs-lookup"><span data-stu-id="dd0dc-112">Attributes</span></span>

<span data-ttu-id="dd0dc-113">없음</span><span class="sxs-lookup"><span data-stu-id="dd0dc-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd0dc-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="dd0dc-114">Child Elements</span></span>

|<span data-ttu-id="dd0dc-115">요소</span><span class="sxs-lookup"><span data-stu-id="dd0dc-115">Element</span></span>|<span data-ttu-id="dd0dc-116">설명</span><span class="sxs-lookup"><span data-stu-id="dd0dc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd0dc-117">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-117">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="dd0dc-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="dd0dc-119">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="dd0dc-120">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="dd0dc-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="dd0dc-122">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-122">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="dd0dc-123">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="dd0dc-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="dd0dc-125">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="dd0dc-126">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-126">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="dd0dc-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-127">Optional element.</span></span><br /><br /> <span data-ttu-id="dd0dc-128">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dd0dc-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="dd0dc-129">Parent Elements</span></span>

|<span data-ttu-id="dd0dc-130">요소</span><span class="sxs-lookup"><span data-stu-id="dd0dc-130">Element</span></span>|<span data-ttu-id="dd0dc-131">설명</span><span class="sxs-lookup"><span data-stu-id="dd0dc-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd0dc-132">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-132">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="dd0dc-133">이 정의에 의해 확장 되는 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-133">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd0dc-134">설명</span><span class="sxs-lookup"><span data-stu-id="dd0dc-134">Remarks</span></span>

<span data-ttu-id="dd0dc-135">각 정의에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-135">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="dd0dc-136">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="dd0dc-137">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="dd0dc-138">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="dd0dc-139">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [Diplaying 하는 데이터에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-139">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dd0dc-140">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-140">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd0dc-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd0dc-141">See Also</span></span>

[<span data-ttu-id="dd0dc-142">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="dd0dc-142">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dd0dc-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="dd0dc-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
