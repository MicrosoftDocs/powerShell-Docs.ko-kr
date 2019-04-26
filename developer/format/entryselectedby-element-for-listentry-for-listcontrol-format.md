---
title: ListControl (형식)에 대 한 ListEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066195"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="ab214-102">ListControl의 ListEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ab214-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="ab214-103">이 목록 뷰 정의 사용 하는.NET 형식 또는이 정의를 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ab214-104">대부분의 경우 목록 보기에 대 한 정의 하나만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="ab214-105">그러나 동일한 목록 뷰를 사용 하 여 다른 개체에 대 한 다양 한 데이터를 표시 하려면 목록 보기에 대 한 여러 정의 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="ab214-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntry ListControl (형식) EntrySelectedBy 요소에 대 한 (형식) ListControl ListEntry 요소에 ListEntry ListControl (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="ab214-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab214-107">구문</span><span class="sxs-lookup"><span data-stu-id="ab214-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab214-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-108">Attributes and Elements</span></span>

<span data-ttu-id="ab214-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab214-110">특성</span><span class="sxs-lookup"><span data-stu-id="ab214-110">Attributes</span></span>

<span data-ttu-id="ab214-111">없음</span><span class="sxs-lookup"><span data-stu-id="ab214-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab214-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-112">Child Elements</span></span>

|<span data-ttu-id="ab214-113">요소</span><span class="sxs-lookup"><span data-stu-id="ab214-113">Element</span></span>|<span data-ttu-id="ab214-114">설명</span><span class="sxs-lookup"><span data-stu-id="ab214-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab214-115">ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="ab214-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ab214-117">이 목록 뷰 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="ab214-118">ListControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="ab214-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ab214-120">이 목록 뷰 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="ab214-121">EntrySelectedBy ListControl (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="ab214-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ab214-123">이 목록 뷰 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab214-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-124">Parent Elements</span></span>

|<span data-ttu-id="ab214-125">요소</span><span class="sxs-lookup"><span data-stu-id="ab214-125">Element</span></span>|<span data-ttu-id="ab214-126">설명</span><span class="sxs-lookup"><span data-stu-id="ab214-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab214-127">ListControl (형식)에 대 한 ListEntry 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="ab214-128">목록의 행 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab214-129">설명</span><span class="sxs-lookup"><span data-stu-id="ab214-129">Remarks</span></span>

<span data-ttu-id="ab214-130">하나 이상의 형식, 선택 항목 집합 또는 목록 뷰 정의 대 한 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="ab214-131">사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="ab214-132">선택 조건을 사용 하 여 정의 개체의 특정 속성에 때와 같이 사용할 수 있어야 하는 조건을 정의 또는 스크립트나 특정 속성 값으로 계산 되는 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="ab214-133">선택 조건에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ab214-134">목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ab214-135">예제</span><span class="sxs-lookup"><span data-stu-id="ab214-135">Example</span></span>

<span data-ttu-id="ab214-136">다음 예제에서는 해당.NET 형식 이름을 사용 하는 목록 보기에 대 한 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="ab214-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab214-137">See Also</span></span>

[<span data-ttu-id="ab214-138">ListControl (형식)에 대 한 ListEntry 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="ab214-139">ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ab214-140">ListControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ab214-141">EntrySelectedBy ListControl (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="ab214-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ab214-142">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="ab214-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ab214-143">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab214-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ab214-144">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="ab214-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
