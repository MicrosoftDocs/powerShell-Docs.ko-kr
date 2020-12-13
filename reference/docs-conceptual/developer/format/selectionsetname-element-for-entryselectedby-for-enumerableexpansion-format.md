---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: EnumerableExpansion의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: 074f810f5a3cbad61ee8be69408967758f0591df
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651885"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="67e39-103">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="67e39-103">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="67e39-104">이 정의에 의해 확장 되는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e39-104">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="67e39-105">Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format) SelectionSetName 요소에 대 한 enumerableexpansions (format) EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="67e39-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67e39-106">구문</span><span class="sxs-lookup"><span data-stu-id="67e39-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="67e39-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="67e39-107">Attributes and Elements</span></span>

<span data-ttu-id="67e39-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="67e39-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67e39-109">특성</span><span class="sxs-lookup"><span data-stu-id="67e39-109">Attributes</span></span>

<span data-ttu-id="67e39-110">없음</span><span class="sxs-lookup"><span data-stu-id="67e39-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67e39-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="67e39-111">Child Elements</span></span>

<span data-ttu-id="67e39-112">없음</span><span class="sxs-lookup"><span data-stu-id="67e39-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67e39-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="67e39-113">Parent Elements</span></span>

|<span data-ttu-id="67e39-114">요소</span><span class="sxs-lookup"><span data-stu-id="67e39-114">Element</span></span>|<span data-ttu-id="67e39-115">설명</span><span class="sxs-lookup"><span data-stu-id="67e39-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67e39-116">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="67e39-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="67e39-117">이 정의에 의해 확장 되는 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e39-117">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67e39-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="67e39-118">Text Value</span></span>

<span data-ttu-id="67e39-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e39-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="67e39-120">설명</span><span class="sxs-lookup"><span data-stu-id="67e39-120">Remarks</span></span>

<span data-ttu-id="67e39-121">각 정의는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67e39-121">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="67e39-122">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67e39-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="67e39-123">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67e39-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="67e39-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="67e39-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67e39-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67e39-125">See Also</span></span>

[<span data-ttu-id="67e39-126">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="67e39-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="67e39-127">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="67e39-127">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="67e39-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="67e39-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
