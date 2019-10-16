---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368802"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="ab08b-102">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ab08b-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="ab08b-103">이 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="ab08b-104">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions element (format) enumerableexpansions 요소 (format) EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ab08b-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab08b-105">구문</span><span class="sxs-lookup"><span data-stu-id="ab08b-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab08b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-106">Attributes and Elements</span></span>

<span data-ttu-id="ab08b-107">다음 섹션에서는 `EntrySelectedBy` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab08b-108">특성</span><span class="sxs-lookup"><span data-stu-id="ab08b-108">Attributes</span></span>

<span data-ttu-id="ab08b-109">없음</span><span class="sxs-lookup"><span data-stu-id="ab08b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab08b-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-110">Child Elements</span></span>

|<span data-ttu-id="ab08b-111">요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-111">Element</span></span>|<span data-ttu-id="ab08b-112">설명</span><span class="sxs-lookup"><span data-stu-id="ab08b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab08b-113">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ab08b-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ab08b-115">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="ab08b-116">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ab08b-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ab08b-118">컬렉션 개체를 확장 하는 방법에 대 한이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="ab08b-119">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ab08b-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ab08b-121">컬렉션 개체를 확장 하는 방법에 대 한이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab08b-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-122">Parent Elements</span></span>

|<span data-ttu-id="ab08b-123">요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-123">Element</span></span>|<span data-ttu-id="ab08b-124">설명</span><span class="sxs-lookup"><span data-stu-id="ab08b-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab08b-125">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ab08b-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="ab08b-126">특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab08b-127">설명</span><span class="sxs-lookup"><span data-stu-id="ab08b-127">Remarks</span></span>

<span data-ttu-id="ab08b-128">정의 항목에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="ab08b-129">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="ab08b-130">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가 `true`으로 평가 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab08b-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="ab08b-131">선택 조건에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab08b-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab08b-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab08b-132">See Also</span></span>

[<span data-ttu-id="ab08b-133">데이터 표시 조건 정의</span><span class="sxs-lookup"><span data-stu-id="ab08b-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ab08b-134">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ab08b-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="ab08b-135">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ab08b-136">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ab08b-137">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="ab08b-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ab08b-138">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ab08b-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
