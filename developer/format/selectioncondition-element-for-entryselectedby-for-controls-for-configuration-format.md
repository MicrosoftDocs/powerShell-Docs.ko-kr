---
title: 구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854149"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="4a04a-102">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a04a-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4a04a-103">사용할 일반적인 컨트롤 정의에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="4a04a-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4a04a-105">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomControl CustomEntry 구성 (형식)에 대 한 CustomEntry에 대 한 EntrySelectedBy SelectionCondition 요소에 대 한 컨트롤에 대 한 구성 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomEntry 요소 구성 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a04a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a04a-106">구문</span><span class="sxs-lookup"><span data-stu-id="4a04a-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a04a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-107">Attributes and Elements</span></span>

<span data-ttu-id="4a04a-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a04a-109">특성</span><span class="sxs-lookup"><span data-stu-id="4a04a-109">Attributes</span></span>

<span data-ttu-id="4a04a-110">없음</span><span class="sxs-lookup"><span data-stu-id="4a04a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a04a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-111">Child Elements</span></span>

|<span data-ttu-id="4a04a-112">요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-112">Element</span></span>|<span data-ttu-id="4a04a-113">설명</span><span class="sxs-lookup"><span data-stu-id="4a04a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a04a-114">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4a04a-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="4a04a-116">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4a04a-117">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4a04a-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="4a04a-119">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="4a04a-120">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4a04a-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="4a04a-122">조건이 트리거하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="4a04a-123">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="4a04a-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="4a04a-125">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4a04a-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-126">Parent Elements</span></span>

|<span data-ttu-id="4a04a-127">요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-127">Element</span></span>|<span data-ttu-id="4a04a-128">설명</span><span class="sxs-lookup"><span data-stu-id="4a04a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a04a-129">구성 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="4a04a-130">이 항목의 공용 컨트롤 정의 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4a04a-131">설명</span><span class="sxs-lookup"><span data-stu-id="4a04a-131">Remarks</span></span>

<span data-ttu-id="4a04a-132">선택 조건을 정의 하는 경우 다음 지침을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="4a04a-133">선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="4a04a-134">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="4a04a-135">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4a04a-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4a04a-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a04a-136">See Also</span></span>

[<span data-ttu-id="4a04a-137">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a04a-138">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a04a-139">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a04a-140">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a04a-141">구성 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="4a04a-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a04a-142">Windows PowerShell 형식 지정을 작성 하 고 파일 형식</span><span class="sxs-lookup"><span data-stu-id="4a04a-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
