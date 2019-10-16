---
title: 이 listcontrol (형식)의 ListEntry에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363832"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="2fae3-102">ListControl의 ListEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2fae3-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="2fae3-103">이 목록 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="2fae3-104">대부분의 경우 목록 뷰에 대 한 정의는 하나만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="2fae3-105">그러나 같은 목록 뷰를 사용 하 여 다른 개체에 대해 서로 다른 데이터를 표시 하려는 경우 목록 뷰에 대 한 여러 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="2fae3-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 for ListEntry for이 listcontrol (format) EntrySelectedBy 요소 이 listcontrol에 대 한 ListEntry (형식)</span><span class="sxs-lookup"><span data-stu-id="2fae3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2fae3-107">구문</span><span class="sxs-lookup"><span data-stu-id="2fae3-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2fae3-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-108">Attributes and Elements</span></span>

<span data-ttu-id="2fae3-109">다음 섹션에서는 `EntrySelectedBy` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2fae3-110">특성</span><span class="sxs-lookup"><span data-stu-id="2fae3-110">Attributes</span></span>

<span data-ttu-id="2fae3-111">없음</span><span class="sxs-lookup"><span data-stu-id="2fae3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2fae3-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-112">Child Elements</span></span>

|<span data-ttu-id="2fae3-113">요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-113">Element</span></span>|<span data-ttu-id="2fae3-114">설명</span><span class="sxs-lookup"><span data-stu-id="2fae3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fae3-115">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2fae3-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2fae3-117">이 목록 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="2fae3-118">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2fae3-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2fae3-120">이 목록 뷰 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="2fae3-121">이 listcontrol에 대 한 EntrySelectedBy (형식)의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2fae3-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2fae3-123">이 목록 뷰 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2fae3-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-124">Parent Elements</span></span>

|<span data-ttu-id="2fae3-125">요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-125">Element</span></span>|<span data-ttu-id="2fae3-126">설명</span><span class="sxs-lookup"><span data-stu-id="2fae3-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fae3-127">이 listcontrol에 대 한 ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2fae3-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="2fae3-128">목록의 행을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2fae3-129">설명</span><span class="sxs-lookup"><span data-stu-id="2fae3-129">Remarks</span></span>

<span data-ttu-id="2fae3-130">목록 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="2fae3-131">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="2fae3-132">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가 `true`으로 평가 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="2fae3-133">선택 조건에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2fae3-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2fae3-134">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2fae3-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2fae3-135">예제</span><span class="sxs-lookup"><span data-stu-id="2fae3-135">Example</span></span>

<span data-ttu-id="2fae3-136">다음 예제에서는 .NET 형식 이름을 사용 하 여 목록 뷰에 대 한 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2fae3-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="2fae3-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2fae3-137">See Also</span></span>

[<span data-ttu-id="2fae3-138">이 listcontrol에 대 한 ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2fae3-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="2fae3-139">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2fae3-140">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2fae3-141">이 listcontrol에 대 한 EntrySelectedBy (형식)의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="2fae3-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2fae3-142">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="2fae3-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2fae3-143">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="2fae3-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2fae3-144">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2fae3-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
