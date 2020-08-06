---
title: CustomControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 52858dba5c7a5222b5410835f3374546ce8b88a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785356"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="86b99-102">CustomControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="86b99-103">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="86b99-104">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="86b99-105">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) Customentries 요소 CustomControl for view (format) EntrySelectedBy for view (format) CustomControl for view (format) SelectionCondition Element for CustomControl for view (Format)</span><span class="sxs-lookup"><span data-stu-id="86b99-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86b99-106">구문</span><span class="sxs-lookup"><span data-stu-id="86b99-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86b99-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="86b99-107">Attributes and Elements</span></span>

<span data-ttu-id="86b99-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="86b99-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86b99-109">특성</span><span class="sxs-lookup"><span data-stu-id="86b99-109">Attributes</span></span>

<span data-ttu-id="86b99-110">없음</span><span class="sxs-lookup"><span data-stu-id="86b99-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86b99-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="86b99-111">Child Elements</span></span>

|<span data-ttu-id="86b99-112">요소</span><span class="sxs-lookup"><span data-stu-id="86b99-112">Element</span></span>|<span data-ttu-id="86b99-113">설명</span><span class="sxs-lookup"><span data-stu-id="86b99-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86b99-114">View에 대한 CustomControl의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="86b99-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-115">Optional element.</span></span><br /><br /> <span data-ttu-id="86b99-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="86b99-117">View에 대한 CustomControl의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="86b99-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-118">Optional element.</span></span><br /><br /> <span data-ttu-id="86b99-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="86b99-120">보기에 대 한 사용자 지정 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="86b99-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-121">Optional element.</span></span><br /><br /> <span data-ttu-id="86b99-122">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="86b99-123">View에 대한 CustomControl의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="86b99-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-124">Optional element.</span></span><br /><br /> <span data-ttu-id="86b99-125">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86b99-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="86b99-126">Parent Elements</span></span>

|<span data-ttu-id="86b99-127">요소</span><span class="sxs-lookup"><span data-stu-id="86b99-127">Element</span></span>|<span data-ttu-id="86b99-128">설명</span><span class="sxs-lookup"><span data-stu-id="86b99-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86b99-129">View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="86b99-130">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86b99-131">설명</span><span class="sxs-lookup"><span data-stu-id="86b99-131">Remarks</span></span>

<span data-ttu-id="86b99-132">선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="86b99-133">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="86b99-134">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="86b99-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="86b99-135">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86b99-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86b99-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86b99-136">See Also</span></span>

[<span data-ttu-id="86b99-137">View에 대한 CustomControl의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86b99-138">View에 대한 CustomControl의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86b99-139">보기에 대 한 사용자 지정 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86b99-140">View에 대한 CustomControl의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86b99-141">View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="86b99-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="86b99-142">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="86b99-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
