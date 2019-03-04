---
title: WideControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854119"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="893e4-102">WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="893e4-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="893e4-103">이 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="893e4-104">수가 와이드 항목 정의 대해 지정할 수 있는 선택 조건 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="893e4-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소에 대 한 WideEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy WideEntry (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="893e4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="893e4-106">구문</span><span class="sxs-lookup"><span data-stu-id="893e4-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="893e4-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-107">Attributes and Elements</span></span>

<span data-ttu-id="893e4-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="893e4-109">단일 지정 해야 합니다 `PropertyName` 또는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="893e4-110">합니다 `SelectionSetName` 고 `TypeName` 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="893e4-111">두 요소 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="893e4-112">특성</span><span class="sxs-lookup"><span data-stu-id="893e4-112">Attributes</span></span>

<span data-ttu-id="893e4-113">없음</span><span class="sxs-lookup"><span data-stu-id="893e4-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="893e4-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-114">Child Elements</span></span>

|<span data-ttu-id="893e4-115">요소</span><span class="sxs-lookup"><span data-stu-id="893e4-115">Element</span></span>|<span data-ttu-id="893e4-116">설명</span><span class="sxs-lookup"><span data-stu-id="893e4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="893e4-117">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="893e4-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="893e4-119">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="893e4-120">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="893e4-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="893e4-122">조건이 트리거하는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="893e4-123">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="893e4-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="893e4-125">조건이 트리거하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="893e4-126">SelectionCondition EntrySelectedBy WideEntry (형식)에 대 한에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="893e4-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-127">Optional element.</span></span><br /><br /> <span data-ttu-id="893e4-128">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="893e4-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-129">Parent Elements</span></span>

|<span data-ttu-id="893e4-130">요소</span><span class="sxs-lookup"><span data-stu-id="893e4-130">Element</span></span>|<span data-ttu-id="893e4-131">설명</span><span class="sxs-lookup"><span data-stu-id="893e4-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="893e4-132">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="893e4-133">이 와이드 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="893e4-134">설명</span><span class="sxs-lookup"><span data-stu-id="893e4-134">Remarks</span></span>

<span data-ttu-id="893e4-135">각 와이드 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="893e4-136">선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="893e4-137">선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="893e4-138">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="893e4-139">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="893e4-140">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="893e4-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893e4-141">See Also</span></span>

[<span data-ttu-id="893e4-142">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="893e4-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="893e4-143">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="893e4-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="893e4-144">WideEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="893e4-145">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="893e4-146">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="893e4-147">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="893e4-148">SelectionCondition EntrySelectedBy WideEntry (형식)에 대 한에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="893e4-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="893e4-149">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="893e4-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
