---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d5858145e092dc962174a776889a4f62db366d71
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785339"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f7c20-102">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7c20-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f7c20-103">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="f7c20-104">Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)-enumerableexpansions (format)의 경우 entryselectedby 요소에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="f7c20-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7c20-105">구문</span><span class="sxs-lookup"><span data-stu-id="f7c20-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7c20-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f7c20-106">Attributes and Elements</span></span>

<span data-ttu-id="f7c20-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="f7c20-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="f7c20-108">단일 또는 요소를 지정 해야 합니다 `PropertyName` `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="f7c20-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="f7c20-109">`SelectionSetName`및 `TypeName` 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="f7c20-110">두 요소 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7c20-111">특성</span><span class="sxs-lookup"><span data-stu-id="f7c20-111">Attributes</span></span>

<span data-ttu-id="f7c20-112">없음</span><span class="sxs-lookup"><span data-stu-id="f7c20-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7c20-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f7c20-113">Child Elements</span></span>

|<span data-ttu-id="f7c20-114">요소</span><span class="sxs-lookup"><span data-stu-id="f7c20-114">Element</span></span>|<span data-ttu-id="f7c20-115">설명</span><span class="sxs-lookup"><span data-stu-id="f7c20-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7c20-116">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7c20-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f7c20-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f7c20-118">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f7c20-119">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7c20-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f7c20-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f7c20-121">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f7c20-122">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7c20-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f7c20-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-123">Optional element.</span></span><br /><br /> <span data-ttu-id="f7c20-124">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f7c20-125">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7c20-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f7c20-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-126">Optional element.</span></span><br /><br /> <span data-ttu-id="f7c20-127">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7c20-128">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f7c20-128">Parent Elements</span></span>

|<span data-ttu-id="f7c20-129">요소</span><span class="sxs-lookup"><span data-stu-id="f7c20-129">Element</span></span>|<span data-ttu-id="f7c20-130">설명</span><span class="sxs-lookup"><span data-stu-id="f7c20-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7c20-131">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7c20-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="f7c20-132">이 정의에 의해 확장 되는 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7c20-133">설명</span><span class="sxs-lookup"><span data-stu-id="f7c20-133">Remarks</span></span>

<span data-ttu-id="f7c20-134">각 정의에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f7c20-135">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f7c20-136">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f7c20-137">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7c20-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f7c20-138">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [Diplaying 하는 데이터에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7c20-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f7c20-139">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7c20-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7c20-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7c20-140">See Also</span></span>

[<span data-ttu-id="f7c20-141">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="f7c20-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f7c20-142">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f7c20-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
