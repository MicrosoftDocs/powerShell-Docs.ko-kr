---
title: 이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362002"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="02b2f-102">ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="02b2f-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="02b2f-103">목록 항목에 대 한 .NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="02b2f-104">항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="02b2f-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (Format) SelectionSetName 요소 ListEntry에 대 한 EntrySelectedBy (형식)</span><span class="sxs-lookup"><span data-stu-id="02b2f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="02b2f-106">구문</span><span class="sxs-lookup"><span data-stu-id="02b2f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="02b2f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="02b2f-107">Attributes and Elements</span></span>

<span data-ttu-id="02b2f-108">다음 섹션에서는 `SelectionSetName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="02b2f-109">특성</span><span class="sxs-lookup"><span data-stu-id="02b2f-109">Attributes</span></span>

<span data-ttu-id="02b2f-110">없음</span><span class="sxs-lookup"><span data-stu-id="02b2f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="02b2f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="02b2f-111">Child Elements</span></span>

<span data-ttu-id="02b2f-112">없음</span><span class="sxs-lookup"><span data-stu-id="02b2f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="02b2f-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="02b2f-113">Parent Elements</span></span>

|<span data-ttu-id="02b2f-114">요소</span><span class="sxs-lookup"><span data-stu-id="02b2f-114">Element</span></span>|<span data-ttu-id="02b2f-115">설명</span><span class="sxs-lookup"><span data-stu-id="02b2f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02b2f-116">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="02b2f-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="02b2f-117">이 목록 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="02b2f-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="02b2f-118">Text Value</span></span>

<span data-ttu-id="02b2f-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="02b2f-120">설명</span><span class="sxs-lookup"><span data-stu-id="02b2f-120">Remarks</span></span>

<span data-ttu-id="02b2f-121">각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="02b2f-122">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="02b2f-123">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="02b2f-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="02b2f-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="02b2f-125">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="02b2f-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="02b2f-126">예제</span><span class="sxs-lookup"><span data-stu-id="02b2f-126">Example</span></span>

<span data-ttu-id="02b2f-127">다음 예에서는 목록 뷰의 항목에 대해 선택 집합을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="02b2f-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="02b2f-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02b2f-128">See Also</span></span>

[<span data-ttu-id="02b2f-129">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="02b2f-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="02b2f-130">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="02b2f-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="02b2f-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="02b2f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
