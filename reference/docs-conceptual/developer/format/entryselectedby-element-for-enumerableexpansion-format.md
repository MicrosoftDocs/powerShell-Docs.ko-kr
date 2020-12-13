---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)
description: EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652325"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="874bf-103">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-103">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="874bf-104">이 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-104">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="874bf-105">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions element (format) enumerableexpansions 요소 (format) EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="874bf-106">구문</span><span class="sxs-lookup"><span data-stu-id="874bf-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="874bf-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="874bf-107">Attributes and Elements</span></span>

<span data-ttu-id="874bf-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="874bf-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="874bf-109">특성</span><span class="sxs-lookup"><span data-stu-id="874bf-109">Attributes</span></span>

<span data-ttu-id="874bf-110">없음</span><span class="sxs-lookup"><span data-stu-id="874bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="874bf-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="874bf-111">Child Elements</span></span>

|<span data-ttu-id="874bf-112">요소</span><span class="sxs-lookup"><span data-stu-id="874bf-112">Element</span></span>|<span data-ttu-id="874bf-113">설명</span><span class="sxs-lookup"><span data-stu-id="874bf-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="874bf-114">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-114">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="874bf-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-115">Optional element.</span></span><br /><br /> <span data-ttu-id="874bf-116">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="874bf-117">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-117">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="874bf-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-118">Optional element.</span></span><br /><br /> <span data-ttu-id="874bf-119">컬렉션 개체를 확장 하는 방법에 대 한이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-119">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="874bf-120">EnumerableExpansion의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-120">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="874bf-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-121">Optional element.</span></span><br /><br /> <span data-ttu-id="874bf-122">컬렉션 개체를 확장 하는 방법에 대 한이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-122">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="874bf-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="874bf-123">Parent Elements</span></span>

|<span data-ttu-id="874bf-124">요소</span><span class="sxs-lookup"><span data-stu-id="874bf-124">Element</span></span>|<span data-ttu-id="874bf-125">설명</span><span class="sxs-lookup"><span data-stu-id="874bf-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="874bf-126">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-126">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="874bf-127">특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-127">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="874bf-128">설명</span><span class="sxs-lookup"><span data-stu-id="874bf-128">Remarks</span></span>

<span data-ttu-id="874bf-129">정의 항목에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-129">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="874bf-130">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="874bf-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="874bf-131">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="874bf-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="874bf-132">선택 조건에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="874bf-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="874bf-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="874bf-133">See Also</span></span>

[<span data-ttu-id="874bf-134">데이터 표시 조건 정의</span><span class="sxs-lookup"><span data-stu-id="874bf-134">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="874bf-135">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-135">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="874bf-136">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-136">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="874bf-137">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-137">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="874bf-138">EnumerableExpansion의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="874bf-138">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="874bf-139">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="874bf-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
