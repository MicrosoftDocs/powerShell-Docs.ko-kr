---
title: 이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 29626b181f21d168e1ebf973e01afeb411d9ef54
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772776"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="25c5e-102">ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="25c5e-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="25c5e-103">목록 뷰의이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="25c5e-104">목록 정의에 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="25c5e-105">Configuration 요소 (Format) ViewDefinitions 요소 (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대해 ListEntry (format) SelectionCondition 요소에 대해 ListEntry (형식)에 대 한 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="25c5e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25c5e-106">구문</span><span class="sxs-lookup"><span data-stu-id="25c5e-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25c5e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-107">Attributes and Elements</span></span>

<span data-ttu-id="25c5e-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="25c5e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25c5e-109">특성</span><span class="sxs-lookup"><span data-stu-id="25c5e-109">Attributes</span></span>

<span data-ttu-id="25c5e-110">없음</span><span class="sxs-lookup"><span data-stu-id="25c5e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25c5e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-111">Child Elements</span></span>

|<span data-ttu-id="25c5e-112">요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-112">Element</span></span>|<span data-ttu-id="25c5e-113">설명</span><span class="sxs-lookup"><span data-stu-id="25c5e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25c5e-114">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="25c5e-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="25c5e-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="25c5e-117">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="25c5e-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="25c5e-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="25c5e-120">ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="25c5e-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="25c5e-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="25c5e-122">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="25c5e-123">ListEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="25c5e-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="25c5e-125">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="25c5e-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-126">Parent Elements</span></span>

|<span data-ttu-id="25c5e-127">요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-127">Element</span></span>|<span data-ttu-id="25c5e-128">설명</span><span class="sxs-lookup"><span data-stu-id="25c5e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25c5e-129">TableRowEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="25c5e-130">이 테이블 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="25c5e-131">설명</span><span class="sxs-lookup"><span data-stu-id="25c5e-131">Remarks</span></span>

<span data-ttu-id="25c5e-132">lWhen 선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="25c5e-133">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="25c5e-134">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25c5e-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="25c5e-135">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25c5e-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="25c5e-136">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25c5e-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="25c5e-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25c5e-137">See Also</span></span>

[<span data-ttu-id="25c5e-138">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="25c5e-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="25c5e-139">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="25c5e-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="25c5e-140">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="25c5e-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="25c5e-141">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="25c5e-142">ListEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="25c5e-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="25c5e-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="25c5e-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
