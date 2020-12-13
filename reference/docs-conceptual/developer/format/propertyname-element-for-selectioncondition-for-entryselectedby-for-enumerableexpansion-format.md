---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
description: EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 8e28118894661b50e90a5ccc86a36fbbe77e4b03
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665841"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="08a96-103">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08a96-103">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="08a96-104">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08a96-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="08a96-105">이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08a96-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="08a96-106">Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)-enumerableexpansions (format)에 대 한 entryselectedby에 대 한 요소 (형식)에 대 한 요소에 대 한 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="08a96-106">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08a96-107">구문</span><span class="sxs-lookup"><span data-stu-id="08a96-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08a96-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="08a96-108">Attributes and Elements</span></span>

<span data-ttu-id="08a96-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="08a96-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08a96-110">특성</span><span class="sxs-lookup"><span data-stu-id="08a96-110">Attributes</span></span>

<span data-ttu-id="08a96-111">없음</span><span class="sxs-lookup"><span data-stu-id="08a96-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08a96-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="08a96-112">Child Elements</span></span>

<span data-ttu-id="08a96-113">없음</span><span class="sxs-lookup"><span data-stu-id="08a96-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08a96-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="08a96-114">Parent Elements</span></span>

|<span data-ttu-id="08a96-115">요소</span><span class="sxs-lookup"><span data-stu-id="08a96-115">Element</span></span>|<span data-ttu-id="08a96-116">설명</span><span class="sxs-lookup"><span data-stu-id="08a96-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08a96-117">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08a96-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="08a96-118">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="08a96-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08a96-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="08a96-119">Text Value</span></span>

<span data-ttu-id="08a96-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08a96-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="08a96-121">설명</span><span class="sxs-lookup"><span data-stu-id="08a96-121">Remarks</span></span>

<span data-ttu-id="08a96-122">선택 조건은 평가할 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08a96-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="08a96-123">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08a96-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08a96-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08a96-124">See Also</span></span>

[<span data-ttu-id="08a96-125">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="08a96-125">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="08a96-126">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08a96-126">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="08a96-127">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="08a96-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="08a96-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="08a96-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
