---
title: WideControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364782"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="08010-102">WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08010-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="08010-103">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="08010-104">넓은 항목 정의에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08010-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="08010-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (Format) SelectionCondition 요소 WideEntry에 대 한 EntrySelectedBy (형식)</span><span class="sxs-lookup"><span data-stu-id="08010-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08010-106">구문</span><span class="sxs-lookup"><span data-stu-id="08010-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08010-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="08010-107">Attributes and Elements</span></span>

<span data-ttu-id="08010-108">다음 섹션에서는 `SelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="08010-109">단일 `PropertyName` 또는 `ScriptBlock` 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="08010-110">@No__t-0 및 `TypeName` 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="08010-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="08010-111">두 요소 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08010-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08010-112">특성</span><span class="sxs-lookup"><span data-stu-id="08010-112">Attributes</span></span>

<span data-ttu-id="08010-113">없음</span><span class="sxs-lookup"><span data-stu-id="08010-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08010-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="08010-114">Child Elements</span></span>

|<span data-ttu-id="08010-115">요소</span><span class="sxs-lookup"><span data-stu-id="08010-115">Element</span></span>|<span data-ttu-id="08010-116">설명</span><span class="sxs-lookup"><span data-stu-id="08010-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08010-117">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="08010-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="08010-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08010-118">Optional element.</span></span><br /><br /> <span data-ttu-id="08010-119">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="08010-120">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="08010-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="08010-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08010-121">Optional element.</span></span><br /><br /> <span data-ttu-id="08010-122">조건을 트리거하는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="08010-123">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="08010-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="08010-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08010-124">Optional element.</span></span><br /><br /> <span data-ttu-id="08010-125">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="08010-126">WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="08010-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="08010-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="08010-127">Optional element.</span></span><br /><br /> <span data-ttu-id="08010-128">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="08010-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="08010-129">Parent Elements</span></span>

|<span data-ttu-id="08010-130">요소</span><span class="sxs-lookup"><span data-stu-id="08010-130">Element</span></span>|<span data-ttu-id="08010-131">설명</span><span class="sxs-lookup"><span data-stu-id="08010-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08010-132">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="08010-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="08010-133">이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="08010-134">설명</span><span class="sxs-lookup"><span data-stu-id="08010-134">Remarks</span></span>

<span data-ttu-id="08010-135">각 넓은 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08010-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="08010-136">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08010-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="08010-137">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08010-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="08010-138">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08010-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="08010-139">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08010-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="08010-140">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08010-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08010-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08010-141">See Also</span></span>

[<span data-ttu-id="08010-142">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="08010-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="08010-143">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="08010-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="08010-144">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="08010-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="08010-145">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="08010-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="08010-146">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="08010-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="08010-147">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="08010-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="08010-148">WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="08010-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="08010-149">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="08010-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
