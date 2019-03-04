---
title: EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862199"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="1527c-102">ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1527c-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="1527c-103">트리거 조건이 있는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1527c-104">있는 경우이 집합의 형식 중 하나는 조건이 충족 하 고 개체 목록 보기의이 정의 사용 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="1527c-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 ListEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소 ListEntry (형식)에</span><span class="sxs-lookup"><span data-stu-id="1527c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1527c-106">구문</span><span class="sxs-lookup"><span data-stu-id="1527c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1527c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1527c-107">Attributes and Elements</span></span>

<span data-ttu-id="1527c-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1527c-109">특성</span><span class="sxs-lookup"><span data-stu-id="1527c-109">Attributes</span></span>

<span data-ttu-id="1527c-110">없음</span><span class="sxs-lookup"><span data-stu-id="1527c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1527c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1527c-111">Child Elements</span></span>

<span data-ttu-id="1527c-112">없음</span><span class="sxs-lookup"><span data-stu-id="1527c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1527c-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1527c-113">Parent Elements</span></span>

|<span data-ttu-id="1527c-114">요소</span><span class="sxs-lookup"><span data-stu-id="1527c-114">Element</span></span>|<span data-ttu-id="1527c-115">설명</span><span class="sxs-lookup"><span data-stu-id="1527c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1527c-116">ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1527c-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1527c-117">이 목록 뷰의이 정의 사용 하도록 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1527c-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1527c-118">Text Value</span></span>

<span data-ttu-id="1527c-119">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1527c-120">설명</span><span class="sxs-lookup"><span data-stu-id="1527c-120">Remarks</span></span>

<span data-ttu-id="1527c-121">선택 조건 선택 집합 또는.NET 형식을 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="1527c-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1527c-123">선택 영역 집합은 일반적인 그룹 형식 지정 파일을 정의 하는 모든 보기에서 사용할 수 있는.NET 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1527c-124">만들기 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1527c-125">목록 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1527c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1527c-126">See Also</span></span>

[<span data-ttu-id="1527c-127">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="1527c-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1527c-128">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1527c-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1527c-129">ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1527c-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1527c-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1527c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
