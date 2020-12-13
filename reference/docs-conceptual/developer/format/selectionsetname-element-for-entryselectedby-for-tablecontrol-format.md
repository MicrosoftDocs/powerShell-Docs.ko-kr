---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651784"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d4759-103">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d4759-103">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d4759-104">테이블 뷰의이 항목을 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-104">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="d4759-105">항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="d4759-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (format) SelectionSetName 요소에 대 한 EntrySelectedBy TableRowEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="d4759-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4759-107">구문</span><span class="sxs-lookup"><span data-stu-id="d4759-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4759-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d4759-108">Attributes and Elements</span></span>

<span data-ttu-id="d4759-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4759-110">특성</span><span class="sxs-lookup"><span data-stu-id="d4759-110">Attributes</span></span>

<span data-ttu-id="d4759-111">없음</span><span class="sxs-lookup"><span data-stu-id="d4759-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4759-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d4759-112">Child Elements</span></span>

<span data-ttu-id="d4759-113">없음</span><span class="sxs-lookup"><span data-stu-id="d4759-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d4759-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d4759-114">Parent Elements</span></span>

|<span data-ttu-id="d4759-115">요소</span><span class="sxs-lookup"><span data-stu-id="d4759-115">Element</span></span>|<span data-ttu-id="d4759-116">설명</span><span class="sxs-lookup"><span data-stu-id="d4759-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4759-117">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d4759-117">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d4759-118">이 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-118">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d4759-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d4759-119">Text Value</span></span>

<span data-ttu-id="d4759-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4759-121">설명</span><span class="sxs-lookup"><span data-stu-id="d4759-121">Remarks</span></span>

<span data-ttu-id="d4759-122">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d4759-123">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d4759-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4759-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d4759-125">항목에 대 한 선택 집합을 지정 하는 경우 형식 이름을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4759-125">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="d4759-126">.NET 형식을 지정 하는 방법에 대 한 자세한 내용은 [TableRowEntry (형식)에 대 한 EntrySelectedBy에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-tablecontrol-format.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4759-126">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="d4759-127">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4759-127">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4759-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4759-128">See Also</span></span>

[<span data-ttu-id="d4759-129">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d4759-129">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d4759-130">보기에 대 한 개체 집합 정의</span><span class="sxs-lookup"><span data-stu-id="d4759-130">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d4759-131">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d4759-131">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d4759-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d4759-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
