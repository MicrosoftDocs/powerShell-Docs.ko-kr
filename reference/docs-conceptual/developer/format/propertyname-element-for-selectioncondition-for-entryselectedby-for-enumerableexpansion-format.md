---
title: EnumerableExpansion (형식)의 경우 EntrySelectedBy의 SelectionCondition에 대 한 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c0081cb724ccaf1c04241aafa177880d7c0e5dbe
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783469"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="63a04-102">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="63a04-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="63a04-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63a04-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="63a04-104">이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63a04-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="63a04-105">Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)-enumerableexpansions (format)에 대 한 entryselectedby에 대 한 요소 (형식)에 대 한 요소에 대 한 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="63a04-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63a04-106">구문</span><span class="sxs-lookup"><span data-stu-id="63a04-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63a04-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="63a04-107">Attributes and Elements</span></span>

<span data-ttu-id="63a04-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="63a04-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63a04-109">특성</span><span class="sxs-lookup"><span data-stu-id="63a04-109">Attributes</span></span>

<span data-ttu-id="63a04-110">없음</span><span class="sxs-lookup"><span data-stu-id="63a04-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63a04-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="63a04-111">Child Elements</span></span>

<span data-ttu-id="63a04-112">없음</span><span class="sxs-lookup"><span data-stu-id="63a04-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63a04-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="63a04-113">Parent Elements</span></span>

|<span data-ttu-id="63a04-114">요소</span><span class="sxs-lookup"><span data-stu-id="63a04-114">Element</span></span>|<span data-ttu-id="63a04-115">설명</span><span class="sxs-lookup"><span data-stu-id="63a04-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63a04-116">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="63a04-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="63a04-117">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63a04-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="63a04-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="63a04-118">Text Value</span></span>

<span data-ttu-id="63a04-119">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63a04-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="63a04-120">설명</span><span class="sxs-lookup"><span data-stu-id="63a04-120">Remarks</span></span>

<span data-ttu-id="63a04-121">선택 조건은 평가할 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63a04-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="63a04-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63a04-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63a04-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63a04-123">See Also</span></span>

[<span data-ttu-id="63a04-124">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="63a04-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="63a04-125">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="63a04-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="63a04-126">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="63a04-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="63a04-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="63a04-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
