---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: ce00cdf868a3075875043aeb59f2cb8a17d049a9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645778"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="f11e3-103">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-103">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f11e3-104">공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-104">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="f11e3-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f11e3-106">구성 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 구성 요소에 대 한 컨트롤의 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 CustomEntries 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 Customentries 요소 구성에 대 한 컨트롤의 Customentries 요소 (형식)에 대 한 customentries 요소에 대 한 컨트롤의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="f11e3-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f11e3-107">구문</span><span class="sxs-lookup"><span data-stu-id="f11e3-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f11e3-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f11e3-108">Attributes and Elements</span></span>

<span data-ttu-id="f11e3-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="f11e3-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f11e3-110">특성</span><span class="sxs-lookup"><span data-stu-id="f11e3-110">Attributes</span></span>

<span data-ttu-id="f11e3-111">없음</span><span class="sxs-lookup"><span data-stu-id="f11e3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f11e3-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f11e3-112">Child Elements</span></span>

|<span data-ttu-id="f11e3-113">요소</span><span class="sxs-lookup"><span data-stu-id="f11e3-113">Element</span></span>|<span data-ttu-id="f11e3-114">설명</span><span class="sxs-lookup"><span data-stu-id="f11e3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f11e3-115">Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-115">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f11e3-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f11e3-117">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f11e3-118">Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-118">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f11e3-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f11e3-120">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f11e3-121">Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-121">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f11e3-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f11e3-123">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f11e3-124">Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-124">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f11e3-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f11e3-126">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f11e3-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f11e3-127">Parent Elements</span></span>

|<span data-ttu-id="f11e3-128">요소</span><span class="sxs-lookup"><span data-stu-id="f11e3-128">Element</span></span>|<span data-ttu-id="f11e3-129">설명</span><span class="sxs-lookup"><span data-stu-id="f11e3-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f11e3-130">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-130">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f11e3-131">공용 컨트롤 정의의이 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-131">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f11e3-132">설명</span><span class="sxs-lookup"><span data-stu-id="f11e3-132">Remarks</span></span>

<span data-ttu-id="f11e3-133">선택 조건을 정의할 때는 다음 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-133">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="f11e3-134">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f11e3-135">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f11e3-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f11e3-136">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f11e3-136">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f11e3-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f11e3-137">See Also</span></span>

[<span data-ttu-id="f11e3-138">Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-138">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f11e3-139">Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-139">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f11e3-140">Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-140">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f11e3-141">Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-141">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f11e3-142">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f11e3-142">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f11e3-143">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f11e3-143">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
