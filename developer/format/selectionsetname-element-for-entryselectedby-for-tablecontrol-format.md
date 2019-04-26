---
title: TableControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063924"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="22a7a-102">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="22a7a-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="22a7a-103">.NET의 집합 형식을 사용 하 여 테이블 보기의이 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="22a7a-104">항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="22a7a-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 (형식) SelectionSetName 요소에 대 한 EntrySelectedBy TableRowEntry (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="22a7a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22a7a-106">구문</span><span class="sxs-lookup"><span data-stu-id="22a7a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22a7a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="22a7a-107">Attributes and Elements</span></span>

<span data-ttu-id="22a7a-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="22a7a-109">특성</span><span class="sxs-lookup"><span data-stu-id="22a7a-109">Attributes</span></span>

<span data-ttu-id="22a7a-110">없음</span><span class="sxs-lookup"><span data-stu-id="22a7a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22a7a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="22a7a-111">Child Elements</span></span>

<span data-ttu-id="22a7a-112">없음</span><span class="sxs-lookup"><span data-stu-id="22a7a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22a7a-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="22a7a-113">Parent Elements</span></span>

|<span data-ttu-id="22a7a-114">요소</span><span class="sxs-lookup"><span data-stu-id="22a7a-114">Element</span></span>|<span data-ttu-id="22a7a-115">설명</span><span class="sxs-lookup"><span data-stu-id="22a7a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22a7a-116">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="22a7a-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="22a7a-117">이 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="22a7a-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="22a7a-118">Text Value</span></span>

<span data-ttu-id="22a7a-119">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="22a7a-120">설명</span><span class="sxs-lookup"><span data-stu-id="22a7a-120">Remarks</span></span>

<span data-ttu-id="22a7a-121">선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="22a7a-122">예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="22a7a-123">선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [보기에 대 한 개체 집합을 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="22a7a-124">선택 항목에 대 한 세트를 지정 하는 경우 형식 이름을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="22a7a-125">.NET 형식을 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [EntrySelectedBy TableRowEntry (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-tablecontrol-format.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="22a7a-126">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="22a7a-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22a7a-127">See Also</span></span>

[<span data-ttu-id="22a7a-128">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="22a7a-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="22a7a-129">보기에 대 한 개체의 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="22a7a-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="22a7a-130">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="22a7a-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="22a7a-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="22a7a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
