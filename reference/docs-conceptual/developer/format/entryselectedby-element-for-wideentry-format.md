---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry에 대한 EntrySelectedBy 요소(형식)
description: WideEntry에 대한 EntrySelectedBy 요소(형식)
ms.openlocfilehash: 246a1967300ab0551f376c4799deac275068308c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660250"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="0d169-103">WideEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0d169-103">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="0d169-104">이 정의를 사용 하기 위해 존재 해야 하는 조건 또는 넓은 뷰의이 정의를 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-104">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="0d169-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0d169-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d169-106">구문</span><span class="sxs-lookup"><span data-stu-id="0d169-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d169-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0d169-107">Attributes and Elements</span></span>

<span data-ttu-id="0d169-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="0d169-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d169-109">특성</span><span class="sxs-lookup"><span data-stu-id="0d169-109">Attributes</span></span>

<span data-ttu-id="0d169-110">없음</span><span class="sxs-lookup"><span data-stu-id="0d169-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d169-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0d169-111">Child Elements</span></span>

|<span data-ttu-id="0d169-112">요소</span><span class="sxs-lookup"><span data-stu-id="0d169-112">Element</span></span>|<span data-ttu-id="0d169-113">설명</span><span class="sxs-lookup"><span data-stu-id="0d169-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d169-114">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="0d169-114">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0d169-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0d169-116">이 광범위 한 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-116">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="0d169-117">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="0d169-117">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0d169-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0d169-119">이 넓은 뷰 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-119">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="0d169-120">WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0d169-120">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="0d169-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0d169-122">이 광범위 한 뷰 정의를 사용 하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-122">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d169-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0d169-123">Parent Elements</span></span>

|<span data-ttu-id="0d169-124">요소</span><span class="sxs-lookup"><span data-stu-id="0d169-124">Element</span></span>|<span data-ttu-id="0d169-125">설명</span><span class="sxs-lookup"><span data-stu-id="0d169-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d169-126">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0d169-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="0d169-127">넓은 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d169-128">설명</span><span class="sxs-lookup"><span data-stu-id="0d169-128">Remarks</span></span>

<span data-ttu-id="0d169-129">넓은 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-129">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="0d169-130">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d169-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="0d169-131">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트 값이로 평가 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="0d169-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="0d169-132">선택 조건에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d169-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0d169-133">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d169-133">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d169-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d169-134">See Also</span></span>

[<span data-ttu-id="0d169-135">WideEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0d169-135">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="0d169-136">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="0d169-136">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0d169-137">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="0d169-137">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0d169-138">WideEntry의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0d169-138">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0d169-139">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="0d169-139">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0d169-140">데이터 표시 조건 정의</span><span class="sxs-lookup"><span data-stu-id="0d169-140">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0d169-141">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="0d169-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
