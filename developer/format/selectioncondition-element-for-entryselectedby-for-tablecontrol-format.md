---
title: TableControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075667"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="b497e-102">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b497e-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="b497e-103">테이블 보기의이 정의에 사용할 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="b497e-104">테이블 정의에 지정 될 수 있는 선택 조건 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="b497e-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 TableRowEntry (형식)에 대 한 TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b497e-106">구문</span><span class="sxs-lookup"><span data-stu-id="b497e-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b497e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-107">Attributes and Elements</span></span>

<span data-ttu-id="b497e-108">다음 섹션에서는 특성, 자식 요소 및 SelectionCondition 요소의 부모 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b497e-109">특성</span><span class="sxs-lookup"><span data-stu-id="b497e-109">Attributes</span></span>

<span data-ttu-id="b497e-110">없음</span><span class="sxs-lookup"><span data-stu-id="b497e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b497e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-111">Child Elements</span></span>

|<span data-ttu-id="b497e-112">요소</span><span class="sxs-lookup"><span data-stu-id="b497e-112">Element</span></span>|<span data-ttu-id="b497e-113">설명</span><span class="sxs-lookup"><span data-stu-id="b497e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b497e-114">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="b497e-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b497e-116">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b497e-117">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b497e-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b497e-119">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="b497e-120">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b497e-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b497e-122">트리거 조건이 있는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="b497e-123">SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="b497e-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b497e-125">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b497e-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-126">Parent Elements</span></span>

|<span data-ttu-id="b497e-127">요소</span><span class="sxs-lookup"><span data-stu-id="b497e-127">Element</span></span>|<span data-ttu-id="b497e-128">설명</span><span class="sxs-lookup"><span data-stu-id="b497e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b497e-129">TableRowEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="b497e-130">이 테이블 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b497e-131">설명</span><span class="sxs-lookup"><span data-stu-id="b497e-131">Remarks</span></span>

<span data-ttu-id="b497e-132">각 목록 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b497e-133">선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="b497e-134">선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="b497e-135">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="b497e-136">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b497e-137">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b497e-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b497e-138">See Also</span></span>

[<span data-ttu-id="b497e-139">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="b497e-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b497e-140">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b497e-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b497e-141">EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b497e-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="b497e-142">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="b497e-143">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b497e-144">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b497e-145">SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="b497e-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="b497e-146">Windows PowerShell 형식 지정을 작성 하 고 파일 형식</span><span class="sxs-lookup"><span data-stu-id="b497e-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
