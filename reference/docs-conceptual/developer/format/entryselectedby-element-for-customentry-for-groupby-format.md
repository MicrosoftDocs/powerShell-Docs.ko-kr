---
title: GroupBy (형식)에 대 한 CustomEntry의 EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363862"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="42702-102">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42702-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="42702-103">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42702-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="42702-104">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42702-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="42702-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl GroupBy (형식)에 대 한 CustomEntry에 대해 GroupBy (Format) EntrySelectedBy 요소에 대 한 CustomControl</span><span class="sxs-lookup"><span data-stu-id="42702-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42702-106">구문</span><span class="sxs-lookup"><span data-stu-id="42702-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42702-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="42702-107">Attributes and Elements</span></span>

<span data-ttu-id="42702-108">다음 섹션에서는 특성, 자식 요소 및 `EntrySelectedBy` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="42702-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="42702-109">정의의 유형, 선택 집합 또는 선택 조건을 하나 이상 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42702-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="42702-110">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42702-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="42702-111">특성</span><span class="sxs-lookup"><span data-stu-id="42702-111">Attributes</span></span>

<span data-ttu-id="42702-112">없음</span><span class="sxs-lookup"><span data-stu-id="42702-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42702-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="42702-113">Child Elements</span></span>

|<span data-ttu-id="42702-114">요소</span><span class="sxs-lookup"><span data-stu-id="42702-114">Element</span></span>|<span data-ttu-id="42702-115">설명</span><span class="sxs-lookup"><span data-stu-id="42702-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42702-116">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="42702-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="42702-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="42702-117">Optional element.</span></span><br /><br /> <span data-ttu-id="42702-118">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42702-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="42702-119">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="42702-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="42702-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="42702-120">Optional element.</span></span><br /><br /> <span data-ttu-id="42702-121">컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42702-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="42702-122">GroupBy (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="42702-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="42702-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="42702-123">Optional element.</span></span><br /><br /> <span data-ttu-id="42702-124">컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42702-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="42702-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="42702-125">Parent Elements</span></span>

|<span data-ttu-id="42702-126">요소</span><span class="sxs-lookup"><span data-stu-id="42702-126">Element</span></span>|<span data-ttu-id="42702-127">설명</span><span class="sxs-lookup"><span data-stu-id="42702-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42702-128">GroupBy (형식)에 대 한 CustomControl의 CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="42702-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="42702-129">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="42702-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="42702-130">설명</span><span class="sxs-lookup"><span data-stu-id="42702-130">Remarks</span></span>

<span data-ttu-id="42702-131">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가 `true`로 평가 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42702-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="42702-132">선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42702-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42702-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42702-133">See Also</span></span>

[<span data-ttu-id="42702-134">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="42702-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="42702-135">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="42702-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="42702-136">GroupBy (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="42702-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="42702-137">뷰의 컨트롤에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="42702-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="42702-138">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="42702-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
