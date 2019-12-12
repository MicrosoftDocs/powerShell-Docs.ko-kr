---
title: CustomControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368442"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="3db8d-102">CustomControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="3db8d-103">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="3db8d-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3db8d-105">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소 CustomControl for view (format) EntrySelectedBy for view (format) CustomControl for view (format) SelectionCondition Element for CustomControl for view (Format)</span><span class="sxs-lookup"><span data-stu-id="3db8d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3db8d-106">구문</span><span class="sxs-lookup"><span data-stu-id="3db8d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3db8d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3db8d-107">Attributes and Elements</span></span>

<span data-ttu-id="3db8d-108">다음 섹션에서는 특성, 자식 요소 및 `SelectionCondition` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3db8d-109">특성</span><span class="sxs-lookup"><span data-stu-id="3db8d-109">Attributes</span></span>

<span data-ttu-id="3db8d-110">없음</span><span class="sxs-lookup"><span data-stu-id="3db8d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3db8d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3db8d-111">Child Elements</span></span>

|<span data-ttu-id="3db8d-112">요소</span><span class="sxs-lookup"><span data-stu-id="3db8d-112">Element</span></span>|<span data-ttu-id="3db8d-113">설명</span><span class="sxs-lookup"><span data-stu-id="3db8d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3db8d-114">CustomControl에 대 한 SelectionCondition의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3db8d-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3db8d-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3db8d-117">CustomControl에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3db8d-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3db8d-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3db8d-120">보기에 대 한 사용자 지정 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3db8d-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3db8d-122">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="3db8d-123">CustomControl에 대 한 SelectionCondition의 TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3db8d-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3db8d-125">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3db8d-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3db8d-126">Parent Elements</span></span>

|<span data-ttu-id="3db8d-127">요소</span><span class="sxs-lookup"><span data-stu-id="3db8d-127">Element</span></span>|<span data-ttu-id="3db8d-128">설명</span><span class="sxs-lookup"><span data-stu-id="3db8d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3db8d-129">CustomControl에 대 한 CustomEntry의 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3db8d-130">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3db8d-131">설명</span><span class="sxs-lookup"><span data-stu-id="3db8d-131">Remarks</span></span>

<span data-ttu-id="3db8d-132">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="3db8d-133">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3db8d-134">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3db8d-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3db8d-135">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3db8d-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3db8d-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3db8d-136">See Also</span></span>

[<span data-ttu-id="3db8d-137">CustomControl에 대 한 SelectionCondition의 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3db8d-138">CustomControl에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3db8d-139">보기에 대 한 사용자 지정 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3db8d-140">CustomControl에 대 한 SelectionCondition의 TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3db8d-141">CustomControl에 대 한 CustomEntry의 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3db8d-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3db8d-142">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3db8d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
