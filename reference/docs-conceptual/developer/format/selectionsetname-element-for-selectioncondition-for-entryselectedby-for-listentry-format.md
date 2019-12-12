---
title: ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368402"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="de414-102">ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="de414-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="de414-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de414-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="de414-104">이 집합에 있는 형식이 있으면 조건이 충족 되 고 목록 뷰의이 정의를 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de414-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="de414-105">Configuration 요소 (Format) ViewDefinitions 요소 (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (Format) SelectionCondition 요소 ListEntry (형식)에 대 한 EntrySelectedBy ListEntry (Format) SelectionSetName 요소에 대 한 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="de414-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de414-106">구문</span><span class="sxs-lookup"><span data-stu-id="de414-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de414-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="de414-107">Attributes and Elements</span></span>

<span data-ttu-id="de414-108">다음 섹션에서는 특성, 자식 요소 및 `SelectionSetName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="de414-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de414-109">특성</span><span class="sxs-lookup"><span data-stu-id="de414-109">Attributes</span></span>

<span data-ttu-id="de414-110">없음</span><span class="sxs-lookup"><span data-stu-id="de414-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de414-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="de414-111">Child Elements</span></span>

<span data-ttu-id="de414-112">없음</span><span class="sxs-lookup"><span data-stu-id="de414-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de414-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="de414-113">Parent Elements</span></span>

|<span data-ttu-id="de414-114">요소</span><span class="sxs-lookup"><span data-stu-id="de414-114">Element</span></span>|<span data-ttu-id="de414-115">설명</span><span class="sxs-lookup"><span data-stu-id="de414-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de414-116">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="de414-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="de414-117">목록 뷰의이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="de414-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="de414-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="de414-118">Text Value</span></span>

<span data-ttu-id="de414-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="de414-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="de414-120">설명</span><span class="sxs-lookup"><span data-stu-id="de414-120">Remarks</span></span>

<span data-ttu-id="de414-121">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de414-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="de414-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de414-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="de414-123">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="de414-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="de414-124">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de414-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="de414-125">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de414-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de414-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de414-126">See Also</span></span>

[<span data-ttu-id="de414-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="de414-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="de414-128">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="de414-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="de414-129">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="de414-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="de414-130">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="de414-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
