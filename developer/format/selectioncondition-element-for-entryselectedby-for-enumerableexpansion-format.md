---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064138"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="a53a7-102">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a53a7-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="a53a7-103">이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="a53a7-104">구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소에 대 한 EntrySelectedBy SelectionCondition 요소 EnumerableExpansion (형식)에 EnumerableExpansion (형식)</span><span class="sxs-lookup"><span data-stu-id="a53a7-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a53a7-105">구문</span><span class="sxs-lookup"><span data-stu-id="a53a7-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a53a7-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-106">Attributes and Elements</span></span>

<span data-ttu-id="a53a7-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="a53a7-108">단일 지정 해야 합니다 `PropertyName` 또는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="a53a7-109">합니다 `SelectionSetName` 고 `TypeName` 요소는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="a53a7-110">두 요소 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a53a7-111">특성</span><span class="sxs-lookup"><span data-stu-id="a53a7-111">Attributes</span></span>

<span data-ttu-id="a53a7-112">없음</span><span class="sxs-lookup"><span data-stu-id="a53a7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a53a7-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-113">Child Elements</span></span>

|<span data-ttu-id="a53a7-114">요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-114">Element</span></span>|<span data-ttu-id="a53a7-115">설명</span><span class="sxs-lookup"><span data-stu-id="a53a7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a53a7-116">EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a53a7-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a53a7-118">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a53a7-119">EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a53a7-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a53a7-121">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a53a7-122">EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a53a7-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a53a7-124">조건이 트리거하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a53a7-125">SelectionCondition EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="a53a7-126">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a53a7-127">조건이 트리거하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a53a7-128">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-128">Parent Elements</span></span>

|<span data-ttu-id="a53a7-129">요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-129">Element</span></span>|<span data-ttu-id="a53a7-130">설명</span><span class="sxs-lookup"><span data-stu-id="a53a7-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a53a7-131">EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="a53a7-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="a53a7-132">이 정의 의해 확장 되는.NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a53a7-133">설명</span><span class="sxs-lookup"><span data-stu-id="a53a7-133">Remarks</span></span>

<span data-ttu-id="a53a7-134">각 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a53a7-135">선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a53a7-136">선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a53a7-137">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a53a7-138">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [Diplaying 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a53a7-139">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [와이드 보기인 경우](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a53a7-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a53a7-140">See Also</span></span>

[<span data-ttu-id="a53a7-141">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a53a7-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a53a7-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="a53a7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
