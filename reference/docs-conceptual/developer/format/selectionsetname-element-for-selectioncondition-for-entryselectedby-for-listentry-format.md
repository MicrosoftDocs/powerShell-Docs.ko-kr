---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)
description: ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651538"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="ea2d9-103">ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ea2d9-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="ea2d9-104">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="ea2d9-105">이 집합에 있는 형식이 있으면 조건이 충족 되 고 목록 뷰의이 정의를 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="ea2d9-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (format) SelectionCondition 요소에 대 한 요소 (형식)의 selectioncondition 요소에 대 한 SelectionCondition for ListEntry (형식)에 대 한 SelectionCondition의 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="ea2d9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea2d9-107">구문</span><span class="sxs-lookup"><span data-stu-id="ea2d9-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea2d9-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ea2d9-108">Attributes and Elements</span></span>

<span data-ttu-id="ea2d9-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="ea2d9-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea2d9-110">특성</span><span class="sxs-lookup"><span data-stu-id="ea2d9-110">Attributes</span></span>

<span data-ttu-id="ea2d9-111">없음</span><span class="sxs-lookup"><span data-stu-id="ea2d9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea2d9-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ea2d9-112">Child Elements</span></span>

<span data-ttu-id="ea2d9-113">없음</span><span class="sxs-lookup"><span data-stu-id="ea2d9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea2d9-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ea2d9-114">Parent Elements</span></span>

|<span data-ttu-id="ea2d9-115">요소</span><span class="sxs-lookup"><span data-stu-id="ea2d9-115">Element</span></span>|<span data-ttu-id="ea2d9-116">설명</span><span class="sxs-lookup"><span data-stu-id="ea2d9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea2d9-117">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ea2d9-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="ea2d9-118">목록 뷰의이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-118">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea2d9-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ea2d9-119">Text Value</span></span>

<span data-ttu-id="ea2d9-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea2d9-121">설명</span><span class="sxs-lookup"><span data-stu-id="ea2d9-121">Remarks</span></span>

<span data-ttu-id="ea2d9-122">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="ea2d9-123">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ea2d9-124">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="ea2d9-125">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ea2d9-126">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea2d9-126">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea2d9-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea2d9-127">See Also</span></span>

[<span data-ttu-id="ea2d9-128">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ea2d9-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ea2d9-129">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="ea2d9-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ea2d9-130">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ea2d9-130">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ea2d9-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ea2d9-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
