---
title: 구성 (형식)의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783418"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="f5609-102">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f5609-103">공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="f5609-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f5609-105">구성 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 구성 요소에 대 한 컨트롤의 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 CustomEntries 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 Customentries 요소 구성에 대 한 컨트롤의 Customentries 요소 (형식)에 대 한 customentries 요소에 대 한 컨트롤의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="f5609-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5609-106">구문</span><span class="sxs-lookup"><span data-stu-id="f5609-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5609-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f5609-107">Attributes and Elements</span></span>

<span data-ttu-id="f5609-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="f5609-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5609-109">특성</span><span class="sxs-lookup"><span data-stu-id="f5609-109">Attributes</span></span>

<span data-ttu-id="f5609-110">없음</span><span class="sxs-lookup"><span data-stu-id="f5609-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5609-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f5609-111">Child Elements</span></span>

|<span data-ttu-id="f5609-112">요소</span><span class="sxs-lookup"><span data-stu-id="f5609-112">Element</span></span>|<span data-ttu-id="f5609-113">설명</span><span class="sxs-lookup"><span data-stu-id="f5609-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5609-114">Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f5609-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f5609-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f5609-117">Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f5609-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f5609-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f5609-120">Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f5609-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f5609-122">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f5609-123">Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="f5609-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f5609-125">조건을 트리거하는 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f5609-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f5609-126">Parent Elements</span></span>

|<span data-ttu-id="f5609-127">요소</span><span class="sxs-lookup"><span data-stu-id="f5609-127">Element</span></span>|<span data-ttu-id="f5609-128">설명</span><span class="sxs-lookup"><span data-stu-id="f5609-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5609-129">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f5609-130">공용 컨트롤 정의의이 항목을 사용 하는 .NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5609-131">설명</span><span class="sxs-lookup"><span data-stu-id="f5609-131">Remarks</span></span>

<span data-ttu-id="f5609-132">선택 조건을 정의할 때는 다음 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="f5609-133">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f5609-134">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f5609-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f5609-135">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5609-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5609-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5609-136">See Also</span></span>

[<span data-ttu-id="f5609-137">Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f5609-138">Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f5609-139">Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f5609-140">Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="f5609-141">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f5609-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f5609-142">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f5609-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
