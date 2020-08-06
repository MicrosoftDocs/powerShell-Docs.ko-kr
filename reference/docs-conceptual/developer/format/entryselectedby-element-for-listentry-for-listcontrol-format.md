---
title: 이 listcontrol (형식)의 ListEntry에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774119"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="98859-102">ListControl의 ListEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="98859-103">이 목록 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="98859-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="98859-104">대부분의 경우 목록 뷰에 대 한 정의는 하나만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="98859-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="98859-105">그러나 같은 목록 뷰를 사용 하 여 다른 개체에 대해 서로 다른 데이터를 표시 하려는 경우 목록 뷰에 대 한 여러 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98859-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="98859-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format)이 listcontrol Element (format) ListEntries Element for ListEntry (format) EntrySelectedBy 요소 for이 listcontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="98859-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98859-107">구문</span><span class="sxs-lookup"><span data-stu-id="98859-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98859-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="98859-108">Attributes and Elements</span></span>

<span data-ttu-id="98859-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="98859-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98859-110">특성</span><span class="sxs-lookup"><span data-stu-id="98859-110">Attributes</span></span>

<span data-ttu-id="98859-111">없음</span><span class="sxs-lookup"><span data-stu-id="98859-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98859-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="98859-112">Child Elements</span></span>

|<span data-ttu-id="98859-113">요소</span><span class="sxs-lookup"><span data-stu-id="98859-113">Element</span></span>|<span data-ttu-id="98859-114">설명</span><span class="sxs-lookup"><span data-stu-id="98859-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98859-115">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="98859-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="98859-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="98859-116">Optional element.</span></span><br /><br /> <span data-ttu-id="98859-117">이 목록 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="98859-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="98859-118">ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="98859-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="98859-119">Optional element.</span></span><br /><br /> <span data-ttu-id="98859-120">이 목록 뷰 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98859-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="98859-121">ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="98859-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="98859-122">Optional element.</span></span><br /><br /> <span data-ttu-id="98859-123">이 목록 뷰 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="98859-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="98859-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="98859-124">Parent Elements</span></span>

|<span data-ttu-id="98859-125">요소</span><span class="sxs-lookup"><span data-stu-id="98859-125">Element</span></span>|<span data-ttu-id="98859-126">설명</span><span class="sxs-lookup"><span data-stu-id="98859-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98859-127">ListControl에 대한 ListEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="98859-128">목록의 행을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="98859-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98859-129">설명</span><span class="sxs-lookup"><span data-stu-id="98859-129">Remarks</span></span>

<span data-ttu-id="98859-130">목록 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98859-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="98859-131">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98859-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="98859-132">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="98859-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="98859-133">선택 조건에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98859-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="98859-134">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98859-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="98859-135">예제</span><span class="sxs-lookup"><span data-stu-id="98859-135">Example</span></span>

<span data-ttu-id="98859-136">다음 예제에서는 .NET 형식 이름을 사용 하 여 목록 뷰에 대 한 개체를 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98859-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="98859-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98859-137">See Also</span></span>

[<span data-ttu-id="98859-138">ListControl에 대한 ListEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="98859-139">ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="98859-140">ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="98859-141">ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="98859-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="98859-142">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="98859-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="98859-143">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="98859-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="98859-144">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="98859-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
