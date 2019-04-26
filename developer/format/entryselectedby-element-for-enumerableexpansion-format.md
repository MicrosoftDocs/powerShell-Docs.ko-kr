---
title: EntrySelectedBy 요소 EnumerableExpansion (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066212"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="0565a-102">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0565a-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="0565a-103">이 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="0565a-104">구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소 EnumerableExpansion (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="0565a-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0565a-105">구문</span><span class="sxs-lookup"><span data-stu-id="0565a-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0565a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-106">Attributes and Elements</span></span>

<span data-ttu-id="0565a-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0565a-108">특성</span><span class="sxs-lookup"><span data-stu-id="0565a-108">Attributes</span></span>

<span data-ttu-id="0565a-109">없음</span><span class="sxs-lookup"><span data-stu-id="0565a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0565a-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-110">Child Elements</span></span>

|<span data-ttu-id="0565a-111">요소</span><span class="sxs-lookup"><span data-stu-id="0565a-111">Element</span></span>|<span data-ttu-id="0565a-112">설명</span><span class="sxs-lookup"><span data-stu-id="0565a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0565a-113">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0565a-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0565a-115">이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="0565a-116">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0565a-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0565a-118">이 정의의 컬렉션 개체를 확장 하는 방법을 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="0565a-119">EntrySelectedBy EnumerableExpansion (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0565a-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0565a-121">컬렉션 개체를 확장 하는 방법을이 정의 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0565a-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-122">Parent Elements</span></span>

|<span data-ttu-id="0565a-123">요소</span><span class="sxs-lookup"><span data-stu-id="0565a-123">Element</span></span>|<span data-ttu-id="0565a-124">설명</span><span class="sxs-lookup"><span data-stu-id="0565a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0565a-125">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0565a-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="0565a-126">개체는 뷰에서 표시 되는 확장은 어떻게 특정.NET 컬렉션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0565a-127">설명</span><span class="sxs-lookup"><span data-stu-id="0565a-127">Remarks</span></span>

<span data-ttu-id="0565a-128">하나 이상의 형식, 선택 영역 집합 또는 정의 항목에 대 한 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="0565a-129">사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="0565a-130">선택 조건을 사용 하 여 정의 개체의 특정 속성에 때와 같이 사용할 수 있어야 하는 조건을 정의 또는 스크립트나 특정 속성 값으로 계산 되는 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0565a-131">선택 조건에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0565a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0565a-132">See Also</span></span>

[<span data-ttu-id="0565a-133">데이터를 표시 하기 위한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0565a-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0565a-134">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0565a-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="0565a-135">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0565a-136">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0565a-137">EntrySelectedBy EnumerableExpansion (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="0565a-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0565a-138">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="0565a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
