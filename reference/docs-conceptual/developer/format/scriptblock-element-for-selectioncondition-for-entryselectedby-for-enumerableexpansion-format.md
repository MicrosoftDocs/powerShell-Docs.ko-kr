---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 71fd969fd3e5c0a4e39762c9a026982a8ca2a9d1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785373"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="95871-102">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="95871-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="95871-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95871-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="95871-104">Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)-enumerableexpansions (format)에 대 한 entryselectedby에 대 한 요소 (형식)-enumerableexpansions (형식)에 대 한 SelectionCondition의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95871-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95871-105">구문</span><span class="sxs-lookup"><span data-stu-id="95871-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95871-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="95871-106">Attributes and Elements</span></span>

<span data-ttu-id="95871-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="95871-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95871-108">특성</span><span class="sxs-lookup"><span data-stu-id="95871-108">Attributes</span></span>

<span data-ttu-id="95871-109">없음</span><span class="sxs-lookup"><span data-stu-id="95871-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95871-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="95871-110">Child Elements</span></span>

<span data-ttu-id="95871-111">없음</span><span class="sxs-lookup"><span data-stu-id="95871-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="95871-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="95871-112">Parent Elements</span></span>

|<span data-ttu-id="95871-113">요소</span><span class="sxs-lookup"><span data-stu-id="95871-113">Element</span></span>|<span data-ttu-id="95871-114">설명</span><span class="sxs-lookup"><span data-stu-id="95871-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95871-115">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="95871-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="95871-116">이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="95871-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="95871-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="95871-117">Text Value</span></span>

<span data-ttu-id="95871-118">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95871-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="95871-119">설명</span><span class="sxs-lookup"><span data-stu-id="95871-119">Remarks</span></span>

<span data-ttu-id="95871-120">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95871-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="95871-121">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95871-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95871-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95871-122">See Also</span></span>

[<span data-ttu-id="95871-123">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="95871-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="95871-124">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="95871-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="95871-125">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="95871-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="95871-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="95871-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
