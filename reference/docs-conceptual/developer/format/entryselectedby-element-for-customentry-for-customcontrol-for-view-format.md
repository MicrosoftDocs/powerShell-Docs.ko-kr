---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
description: View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655355"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="517e0-103">View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="517e0-103">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="517e0-104">이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-104">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="517e0-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) customentries 요소에 대 한 customentries 요소에 대 한 CustomEntries 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="517e0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="517e0-106">구문</span><span class="sxs-lookup"><span data-stu-id="517e0-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="517e0-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-107">Attributes and Elements</span></span>

<span data-ttu-id="517e0-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="517e0-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="517e0-109">특성</span><span class="sxs-lookup"><span data-stu-id="517e0-109">Attributes</span></span>

<span data-ttu-id="517e0-110">없음</span><span class="sxs-lookup"><span data-stu-id="517e0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="517e0-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-111">Child Elements</span></span>

|<span data-ttu-id="517e0-112">요소</span><span class="sxs-lookup"><span data-stu-id="517e0-112">Element</span></span>|<span data-ttu-id="517e0-113">설명</span><span class="sxs-lookup"><span data-stu-id="517e0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="517e0-114">CustomEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-114">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="517e0-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="517e0-116">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-116">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="517e0-117">CustomEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-117">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="517e0-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="517e0-119">컨트롤 뷰의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-119">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="517e0-120">CustomEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-120">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="517e0-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="517e0-122">컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-122">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="517e0-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-123">Parent Elements</span></span>

|<span data-ttu-id="517e0-124">요소</span><span class="sxs-lookup"><span data-stu-id="517e0-124">Element</span></span>|<span data-ttu-id="517e0-125">설명</span><span class="sxs-lookup"><span data-stu-id="517e0-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="517e0-126">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="517e0-126">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="517e0-127">특정 .NET 개체에서 사용 하는 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-127">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="517e0-128">설명</span><span class="sxs-lookup"><span data-stu-id="517e0-128">Remarks</span></span>

<span data-ttu-id="517e0-129">항목에 대 한 형식, 선택 집합 또는 선택 조건을 하나 이상 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-129">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="517e0-130">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="517e0-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="517e0-131">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 사용 될 항목에 대해 존재 해야 하는 조건을 정의 하는 데 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="517e0-131">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="517e0-132">선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="517e0-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="517e0-133">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 뷰](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="517e0-133">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="517e0-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="517e0-134">See Also</span></span>

[<span data-ttu-id="517e0-135">CustomEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-135">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="517e0-136">CustomEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-136">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="517e0-137">CustomEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="517e0-137">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="517e0-138">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="517e0-138">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="517e0-139">사용자 지정 컨트롤 뷰</span><span class="sxs-lookup"><span data-stu-id="517e0-139">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="517e0-140">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="517e0-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
