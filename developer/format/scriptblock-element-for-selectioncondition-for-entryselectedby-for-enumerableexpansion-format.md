---
title: ScriptBlock 요소 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854799"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="6d247-102">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6d247-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="6d247-103">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d247-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="6d247-104">구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소에 대 한 EntrySelectedBy SelectionCondition 요소 EnumerableExpansion (형식)에 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소 EnumerableExpansion (형식)</span><span class="sxs-lookup"><span data-stu-id="6d247-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d247-105">구문</span><span class="sxs-lookup"><span data-stu-id="6d247-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d247-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6d247-106">Attributes and Elements</span></span>

<span data-ttu-id="6d247-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6d247-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d247-108">특성</span><span class="sxs-lookup"><span data-stu-id="6d247-108">Attributes</span></span>

<span data-ttu-id="6d247-109">없음</span><span class="sxs-lookup"><span data-stu-id="6d247-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d247-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6d247-110">Child Elements</span></span>

<span data-ttu-id="6d247-111">없음</span><span class="sxs-lookup"><span data-stu-id="6d247-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6d247-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6d247-112">Parent Elements</span></span>

|<span data-ttu-id="6d247-113">요소</span><span class="sxs-lookup"><span data-stu-id="6d247-113">Element</span></span>|<span data-ttu-id="6d247-114">설명</span><span class="sxs-lookup"><span data-stu-id="6d247-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d247-115">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="6d247-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="6d247-116">이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d247-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6d247-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="6d247-117">Text Value</span></span>

<span data-ttu-id="6d247-118">계산 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d247-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d247-119">설명</span><span class="sxs-lookup"><span data-stu-id="6d247-119">Remarks</span></span>

<span data-ttu-id="6d247-120">선택 조건 평가 수행 하려면 하나 이상의 스크립트 또는 속성 이름을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d247-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6d247-121">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6d247-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d247-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d247-122">See Also</span></span>

[<span data-ttu-id="6d247-123">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d247-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6d247-124">EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="6d247-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6d247-125">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="6d247-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="6d247-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="6d247-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
