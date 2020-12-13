---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651831"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="51958-103">ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="51958-103">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="51958-104">목록 항목에 대 한 .NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51958-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="51958-105">항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51958-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="51958-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (format) SelectionSetName 요소에 대해 ListEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="51958-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51958-107">구문</span><span class="sxs-lookup"><span data-stu-id="51958-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51958-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="51958-108">Attributes and Elements</span></span>

<span data-ttu-id="51958-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="51958-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51958-110">특성</span><span class="sxs-lookup"><span data-stu-id="51958-110">Attributes</span></span>

<span data-ttu-id="51958-111">없음</span><span class="sxs-lookup"><span data-stu-id="51958-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51958-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="51958-112">Child Elements</span></span>

<span data-ttu-id="51958-113">없음</span><span class="sxs-lookup"><span data-stu-id="51958-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="51958-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="51958-114">Parent Elements</span></span>

|<span data-ttu-id="51958-115">요소</span><span class="sxs-lookup"><span data-stu-id="51958-115">Element</span></span>|<span data-ttu-id="51958-116">설명</span><span class="sxs-lookup"><span data-stu-id="51958-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51958-117">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="51958-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="51958-118">이 목록 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="51958-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="51958-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="51958-119">Text Value</span></span>

<span data-ttu-id="51958-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51958-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="51958-121">설명</span><span class="sxs-lookup"><span data-stu-id="51958-121">Remarks</span></span>

<span data-ttu-id="51958-122">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51958-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="51958-123">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51958-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="51958-124">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51958-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="51958-125">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51958-125">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="51958-126">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51958-126">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="51958-127">예제</span><span class="sxs-lookup"><span data-stu-id="51958-127">Example</span></span>

<span data-ttu-id="51958-128">다음 예에서는 목록 뷰의 항목에 대해 선택 집합을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51958-128">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="51958-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51958-129">See Also</span></span>

[<span data-ttu-id="51958-130">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="51958-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="51958-131">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="51958-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="51958-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="51958-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
