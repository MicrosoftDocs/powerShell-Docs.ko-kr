---
title: PropertyName 요소 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064954"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="7567a-102">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7567a-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7567a-103">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7567a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7567a-104">이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7567a-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="7567a-105">구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소에 대 한 EntrySelectedBy SelectionCondition 요소 EnumerableExpansion (형식)에 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소 EnumerableExpansion (형식)</span><span class="sxs-lookup"><span data-stu-id="7567a-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7567a-106">구문</span><span class="sxs-lookup"><span data-stu-id="7567a-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7567a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7567a-107">Attributes and Elements</span></span>

<span data-ttu-id="7567a-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7567a-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7567a-109">특성</span><span class="sxs-lookup"><span data-stu-id="7567a-109">Attributes</span></span>

<span data-ttu-id="7567a-110">없음</span><span class="sxs-lookup"><span data-stu-id="7567a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7567a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7567a-111">Child Elements</span></span>

<span data-ttu-id="7567a-112">없음</span><span class="sxs-lookup"><span data-stu-id="7567a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7567a-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7567a-113">Parent Elements</span></span>

|<span data-ttu-id="7567a-114">요소</span><span class="sxs-lookup"><span data-stu-id="7567a-114">Element</span></span>|<span data-ttu-id="7567a-115">설명</span><span class="sxs-lookup"><span data-stu-id="7567a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7567a-116">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="7567a-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7567a-117">이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7567a-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7567a-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="7567a-118">Text Value</span></span>

<span data-ttu-id="7567a-119">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7567a-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7567a-120">설명</span><span class="sxs-lookup"><span data-stu-id="7567a-120">Remarks</span></span>

<span data-ttu-id="7567a-121">선택 조건 하나 이상의 속성 이름 또는 평가 수행 하려면 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7567a-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7567a-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7567a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7567a-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7567a-123">See Also</span></span>

[<span data-ttu-id="7567a-124">표시 되는 경우 데이터에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="7567a-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7567a-125">EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="7567a-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7567a-126">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="7567a-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7567a-127">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="7567a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
