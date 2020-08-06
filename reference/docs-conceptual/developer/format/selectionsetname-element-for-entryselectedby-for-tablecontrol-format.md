---
title: TableControl (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e68aa74b201abf345e87411db6cb2787ddd4f72b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772691"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="8062b-102">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8062b-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="8062b-103">테이블 뷰의이 항목을 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="8062b-104">항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="8062b-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (format) SelectionSetName 요소에 대 한 EntrySelectedBy TableRowEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="8062b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8062b-106">구문</span><span class="sxs-lookup"><span data-stu-id="8062b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8062b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8062b-107">Attributes and Elements</span></span>

<span data-ttu-id="8062b-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8062b-109">특성</span><span class="sxs-lookup"><span data-stu-id="8062b-109">Attributes</span></span>

<span data-ttu-id="8062b-110">없음</span><span class="sxs-lookup"><span data-stu-id="8062b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8062b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8062b-111">Child Elements</span></span>

<span data-ttu-id="8062b-112">없음</span><span class="sxs-lookup"><span data-stu-id="8062b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8062b-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8062b-113">Parent Elements</span></span>

|<span data-ttu-id="8062b-114">요소</span><span class="sxs-lookup"><span data-stu-id="8062b-114">Element</span></span>|<span data-ttu-id="8062b-115">설명</span><span class="sxs-lookup"><span data-stu-id="8062b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8062b-116">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8062b-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="8062b-117">이 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8062b-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="8062b-118">Text Value</span></span>

<span data-ttu-id="8062b-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8062b-120">설명</span><span class="sxs-lookup"><span data-stu-id="8062b-120">Remarks</span></span>

<span data-ttu-id="8062b-121">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8062b-122">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="8062b-123">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8062b-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8062b-124">항목에 대 한 선택 집합을 지정 하는 경우 형식 이름을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8062b-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="8062b-125">.NET 형식을 지정 하는 방법에 대 한 자세한 내용은 [TableRowEntry (형식)에 대 한 EntrySelectedBy에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-tablecontrol-format.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8062b-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="8062b-126">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8062b-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8062b-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8062b-127">See Also</span></span>

[<span data-ttu-id="8062b-128">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8062b-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="8062b-129">보기에 대 한 개체 집합 정의</span><span class="sxs-lookup"><span data-stu-id="8062b-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8062b-130">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="8062b-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8062b-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8062b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
