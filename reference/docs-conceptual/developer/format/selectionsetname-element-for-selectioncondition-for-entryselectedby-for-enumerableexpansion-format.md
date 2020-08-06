---
title: EnumerableExpansion (Format)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e18c74bb95c658f2c3e7b7454628f78d523f7609
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787498"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="6a806-102">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6a806-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="6a806-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a806-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="6a806-104">이 집합에 있는 형식이 있으면 조건이 충족 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a806-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="6a806-105">구성 요소 DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)에 대 한 Entryselectedby 요소에 대 한 By enumerableexpansions (형식)의 selectioncondition 요소에 대 한 by</span><span class="sxs-lookup"><span data-stu-id="6a806-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a806-106">구문</span><span class="sxs-lookup"><span data-stu-id="6a806-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a806-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6a806-107">Attributes and Elements</span></span>

<span data-ttu-id="6a806-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="6a806-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a806-109">특성</span><span class="sxs-lookup"><span data-stu-id="6a806-109">Attributes</span></span>

<span data-ttu-id="6a806-110">없음</span><span class="sxs-lookup"><span data-stu-id="6a806-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a806-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6a806-111">Child Elements</span></span>

<span data-ttu-id="6a806-112">없음</span><span class="sxs-lookup"><span data-stu-id="6a806-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a806-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6a806-113">Parent Elements</span></span>

|<span data-ttu-id="6a806-114">요소</span><span class="sxs-lookup"><span data-stu-id="6a806-114">Element</span></span>|<span data-ttu-id="6a806-115">설명</span><span class="sxs-lookup"><span data-stu-id="6a806-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a806-116">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6a806-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6a806-117">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a806-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6a806-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="6a806-118">Text Value</span></span>

<span data-ttu-id="6a806-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a806-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a806-120">설명</span><span class="sxs-lookup"><span data-stu-id="6a806-120">Remarks</span></span>

<span data-ttu-id="6a806-121">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a806-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="6a806-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6a806-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6a806-123">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="6a806-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="6a806-124">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6a806-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a806-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a806-125">See Also</span></span>

[<span data-ttu-id="6a806-126">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="6a806-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6a806-127">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6a806-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6a806-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6a806-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
