---
title: EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063863"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="51ece-102">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="51ece-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="51ece-103">트리거 조건이 있는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="51ece-104">이 형식의 값이 있는 경우에 조건이 충족 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="51ece-105">구성 요소 DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansions 요소 (형식) EntrySelectedBy 요소에 대 한 EntrySelectedBy SelectionCondition 요소 EnumerableExpansion (형식)에 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소 EnumerableExpansion (형식)</span><span class="sxs-lookup"><span data-stu-id="51ece-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51ece-106">구문</span><span class="sxs-lookup"><span data-stu-id="51ece-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51ece-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="51ece-107">Attributes and Elements</span></span>

<span data-ttu-id="51ece-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51ece-109">특성</span><span class="sxs-lookup"><span data-stu-id="51ece-109">Attributes</span></span>

<span data-ttu-id="51ece-110">없음</span><span class="sxs-lookup"><span data-stu-id="51ece-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51ece-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="51ece-111">Child Elements</span></span>

<span data-ttu-id="51ece-112">없음</span><span class="sxs-lookup"><span data-stu-id="51ece-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="51ece-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="51ece-113">Parent Elements</span></span>

|<span data-ttu-id="51ece-114">요소</span><span class="sxs-lookup"><span data-stu-id="51ece-114">Element</span></span>|<span data-ttu-id="51ece-115">설명</span><span class="sxs-lookup"><span data-stu-id="51ece-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51ece-116">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="51ece-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="51ece-117">이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="51ece-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="51ece-118">Text Value</span></span>

<span data-ttu-id="51ece-119">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="51ece-120">설명</span><span class="sxs-lookup"><span data-stu-id="51ece-120">Remarks</span></span>

<span data-ttu-id="51ece-121">선택 조건 선택 집합 또는.NET 형식을 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="51ece-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="51ece-123">선택 영역 집합은 일반적인 그룹 형식 지정 파일을 정의 하는 모든 보기에서 사용할 수 있는.NET 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="51ece-124">만들기 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [선택 영역 설정 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="51ece-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="51ece-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51ece-125">See Also</span></span>

[<span data-ttu-id="51ece-126">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="51ece-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="51ece-127">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="51ece-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="51ece-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="51ece-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
