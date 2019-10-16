---
title: CustomControl에 대 한 CustomEntry의 EntrySelectedBy 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368782"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="8883d-102">View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8883d-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="8883d-103">이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="8883d-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) Customentries 요소에 대 한 CustomControl의 customentries 요소 view (형식) EntrySelectedBy View의 CustomEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="8883d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8883d-105">구문</span><span class="sxs-lookup"><span data-stu-id="8883d-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8883d-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-106">Attributes and Elements</span></span>

<span data-ttu-id="8883d-107">다음 섹션에서는 `EntrySelectedBy` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8883d-108">특성</span><span class="sxs-lookup"><span data-stu-id="8883d-108">Attributes</span></span>

<span data-ttu-id="8883d-109">없음</span><span class="sxs-lookup"><span data-stu-id="8883d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8883d-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-110">Child Elements</span></span>

|<span data-ttu-id="8883d-111">요소</span><span class="sxs-lookup"><span data-stu-id="8883d-111">Element</span></span>|<span data-ttu-id="8883d-112">설명</span><span class="sxs-lookup"><span data-stu-id="8883d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8883d-113">CustomEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="8883d-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="8883d-115">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="8883d-116">CustomEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="8883d-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8883d-118">컨트롤 뷰의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="8883d-119">CustomEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="8883d-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8883d-121">컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8883d-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-122">Parent Elements</span></span>

|<span data-ttu-id="8883d-123">요소</span><span class="sxs-lookup"><span data-stu-id="8883d-123">Element</span></span>|<span data-ttu-id="8883d-124">설명</span><span class="sxs-lookup"><span data-stu-id="8883d-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8883d-125">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8883d-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="8883d-126">특정 .NET 개체에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8883d-127">설명</span><span class="sxs-lookup"><span data-stu-id="8883d-127">Remarks</span></span>

<span data-ttu-id="8883d-128">항목에 대 한 형식, 선택 집합 또는 선택 조건을 하나 이상 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="8883d-129">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="8883d-130">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가 `true`으로 평가 되는 경우와 같이 사용할 항목에 대해 존재 해야 하는 조건을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8883d-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="8883d-131">선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8883d-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8883d-132">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 뷰](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8883d-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8883d-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8883d-133">See Also</span></span>

[<span data-ttu-id="8883d-134">CustomEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="8883d-135">CustomEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8883d-136">CustomEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="8883d-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8883d-137">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8883d-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8883d-138">사용자 지정 컨트롤 뷰</span><span class="sxs-lookup"><span data-stu-id="8883d-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8883d-139">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="8883d-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
