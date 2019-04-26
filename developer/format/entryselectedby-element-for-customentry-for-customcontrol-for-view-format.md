---
title: CustomControl 보려면 (형식)에 대 한 CustomEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066280"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="8ec1c-102">View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8ec1c-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="8ec1c-103">이 사용자 지정 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="8ec1c-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 뷰 (형식)에 대 한 CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ec1c-105">구문</span><span class="sxs-lookup"><span data-stu-id="8ec1c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ec1c-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-106">Attributes and Elements</span></span>

<span data-ttu-id="8ec1c-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ec1c-108">특성</span><span class="sxs-lookup"><span data-stu-id="8ec1c-108">Attributes</span></span>

<span data-ttu-id="8ec1c-109">없음</span><span class="sxs-lookup"><span data-stu-id="8ec1c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ec1c-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-110">Child Elements</span></span>

|<span data-ttu-id="8ec1c-111">요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-111">Element</span></span>|<span data-ttu-id="8ec1c-112">설명</span><span class="sxs-lookup"><span data-stu-id="8ec1c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ec1c-113">CustomEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="8ec1c-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8ec1c-115">이 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="8ec1c-116">CustomEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="8ec1c-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8ec1c-118">컨트롤 뷰이 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="8ec1c-119">EntrySelectedBy CustomEntry (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="8ec1c-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8ec1c-121">컨트롤 뷰이 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8ec1c-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-122">Parent Elements</span></span>

|<span data-ttu-id="8ec1c-123">요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-123">Element</span></span>|<span data-ttu-id="8ec1c-124">설명</span><span class="sxs-lookup"><span data-stu-id="8ec1c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ec1c-125">뷰 (형식)에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="8ec1c-126">특정.NET 개체에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ec1c-127">설명</span><span class="sxs-lookup"><span data-stu-id="8ec1c-127">Remarks</span></span>

<span data-ttu-id="8ec1c-128">하나 이상의 형식, 선택 영역 집합 또는 항목에 대 한 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="8ec1c-129">사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="8ec1c-130">선택 조건을 사용 하 여 사용할 조건을 정의한 다음 있어야 하는 데 사용할 항목에 대 한 개체의 특정 속성에 있을 때와 같은, 특정 속성 값 이거나 스크립트 계산 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="8ec1c-131">선택 조건에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8ec1c-132">사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 뷰](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ec1c-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec1c-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ec1c-133">See Also</span></span>

[<span data-ttu-id="8ec1c-134">CustomEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="8ec1c-135">CustomEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8ec1c-136">EntrySelectedBy CustomEntry (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8ec1c-137">뷰 (형식)에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="8ec1c-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8ec1c-138">사용자 지정 컨트롤 뷰</span><span class="sxs-lookup"><span data-stu-id="8ec1c-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8ec1c-139">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="8ec1c-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
