---
title: EnumerableExpansion (Format)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361992"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b11e7-102">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b11e7-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b11e7-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b11e7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b11e7-104">이 집합에 있는 형식이 있으면 조건이 충족 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b11e7-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="b11e7-105">구성 요소 DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format) EntrySelectedBy 요소에 대 한 요소 (format) SelectionCondition 요소에 대 한 EnumerableExpansion (Format) SelectionSetName 요소 (형식)에 대 한 EntrySelectedBy의 SelectionCondition</span><span class="sxs-lookup"><span data-stu-id="b11e7-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b11e7-106">구문</span><span class="sxs-lookup"><span data-stu-id="b11e7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b11e7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b11e7-107">Attributes and Elements</span></span>

<span data-ttu-id="b11e7-108">다음 섹션에서는 `SelectionSetName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b11e7-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b11e7-109">특성</span><span class="sxs-lookup"><span data-stu-id="b11e7-109">Attributes</span></span>

<span data-ttu-id="b11e7-110">없음</span><span class="sxs-lookup"><span data-stu-id="b11e7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b11e7-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b11e7-111">Child Elements</span></span>

<span data-ttu-id="b11e7-112">없음</span><span class="sxs-lookup"><span data-stu-id="b11e7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b11e7-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b11e7-113">Parent Elements</span></span>

|<span data-ttu-id="b11e7-114">요소</span><span class="sxs-lookup"><span data-stu-id="b11e7-114">Element</span></span>|<span data-ttu-id="b11e7-115">설명</span><span class="sxs-lookup"><span data-stu-id="b11e7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b11e7-116">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b11e7-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b11e7-117">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b11e7-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b11e7-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b11e7-118">Text Value</span></span>

<span data-ttu-id="b11e7-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b11e7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b11e7-120">설명</span><span class="sxs-lookup"><span data-stu-id="b11e7-120">Remarks</span></span>

<span data-ttu-id="b11e7-121">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b11e7-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b11e7-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b11e7-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b11e7-123">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="b11e7-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b11e7-124">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b11e7-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b11e7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b11e7-125">See Also</span></span>

[<span data-ttu-id="b11e7-126">선택 집합 정의</span><span class="sxs-lookup"><span data-stu-id="b11e7-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b11e7-127">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b11e7-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b11e7-128">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b11e7-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
