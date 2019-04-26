---
title: GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066229"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="8985f-102">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8985f-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="8985f-103">이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="8985f-104">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8985f-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소 GroupBy (형식)에 대 한 CustomControl</span><span class="sxs-lookup"><span data-stu-id="8985f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8985f-106">구문</span><span class="sxs-lookup"><span data-stu-id="8985f-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8985f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-107">Attributes and Elements</span></span>

<span data-ttu-id="8985f-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="8985f-109">하나 이상의 형식 또는 선택 집합 정의 대 한 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="8985f-110">사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="8985f-111">특성</span><span class="sxs-lookup"><span data-stu-id="8985f-111">Attributes</span></span>

<span data-ttu-id="8985f-112">없음</span><span class="sxs-lookup"><span data-stu-id="8985f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8985f-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-113">Child Elements</span></span>

|<span data-ttu-id="8985f-114">요소</span><span class="sxs-lookup"><span data-stu-id="8985f-114">Element</span></span>|<span data-ttu-id="8985f-115">설명</span><span class="sxs-lookup"><span data-stu-id="8985f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8985f-116">GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="8985f-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8985f-118">이 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="8985f-119">GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="8985f-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8985f-121">컨트롤의이 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="8985f-122">GroupBy (형식)에 대 한 EntrySelectedBy TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="8985f-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-123">Optional element.</span></span><br /><br /> <span data-ttu-id="8985f-124">컨트롤의이 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8985f-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-125">Parent Elements</span></span>

|<span data-ttu-id="8985f-126">요소</span><span class="sxs-lookup"><span data-stu-id="8985f-126">Element</span></span>|<span data-ttu-id="8985f-127">설명</span><span class="sxs-lookup"><span data-stu-id="8985f-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8985f-128">GroupBy (형식)에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="8985f-129">컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8985f-130">설명</span><span class="sxs-lookup"><span data-stu-id="8985f-130">Remarks</span></span>

<span data-ttu-id="8985f-131">선택 조건을 사용 하 여 사용할 조건을 정의한 다음 있어야 하는 데 사용할 정의 대 한, 개체의 특정 속성에 있을 때와 같은 또는 특정 속성 값 이거나 스크립트 계산 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="8985f-132">선택 조건에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="8985f-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8985f-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8985f-133">See Also</span></span>

[<span data-ttu-id="8985f-134">GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="8985f-135">GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="8985f-136">GroupBy (형식)에 대 한 EntrySelectedBy TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="8985f-137">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="8985f-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="8985f-138">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="8985f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
