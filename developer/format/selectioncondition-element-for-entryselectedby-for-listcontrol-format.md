---
title: ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: ec75945c5517c02fa001f0a38573c045ffcdbfd3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857489"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d4fb0-102">ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d4fb0-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d4fb0-103">이 목록 뷰의이 정의 사용 하도록 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="d4fb0-104">목록 정의 대해 지정할 수 있는 선택 조건 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="d4fb0-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 ListEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy ListEntry (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="d4fb0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4fb0-106">구문</span><span class="sxs-lookup"><span data-stu-id="d4fb0-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4fb0-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-107">Attributes and Elements</span></span>

<span data-ttu-id="d4fb0-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4fb0-109">특성</span><span class="sxs-lookup"><span data-stu-id="d4fb0-109">Attributes</span></span>

<span data-ttu-id="d4fb0-110">없음</span><span class="sxs-lookup"><span data-stu-id="d4fb0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4fb0-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-111">Child Elements</span></span>

|<span data-ttu-id="d4fb0-112">요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-112">Element</span></span>|<span data-ttu-id="d4fb0-113">설명</span><span class="sxs-lookup"><span data-stu-id="d4fb0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4fb0-114">PropertyName SelectionCondition EmtrySelectedBy ListEntry (형식)에 대 한에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-114">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d4fb0-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d4fb0-116">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d4fb0-117">EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d4fb0-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d4fb0-119">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="d4fb0-120">EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="d4fb0-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d4fb0-122">트리거 조건이 있는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="d4fb0-123">SelectionCondition EntrySelectedBy ListEntry (형식)에 대 한에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d4fb0-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d4fb0-125">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d4fb0-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-126">Parent Elements</span></span>

|<span data-ttu-id="d4fb0-127">요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-127">Element</span></span>|<span data-ttu-id="d4fb0-128">설명</span><span class="sxs-lookup"><span data-stu-id="d4fb0-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4fb0-129">TableRowEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d4fb0-130">이 테이블 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d4fb0-131">설명</span><span class="sxs-lookup"><span data-stu-id="d4fb0-131">Remarks</span></span>

<span data-ttu-id="d4fb0-132">lWhen 선택 조건을 정의 하는, 다음 요구 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="d4fb0-133">선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="d4fb0-134">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="d4fb0-135">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d4fb0-136">목록 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4fb0-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4fb0-137">See Also</span></span>

[<span data-ttu-id="d4fb0-138">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="d4fb0-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d4fb0-139">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d4fb0-140">ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d4fb0-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="d4fb0-141">ListEntry (형식)에 대 한 EnrtySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-141">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d4fb0-142">EntrySelectedBy ListEntry (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="d4fb0-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[<span data-ttu-id="d4fb0-143">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="d4fb0-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
