---
title: WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 44c88ce75ae485e1c48ceb08bfd12f739a632996
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787447"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="f040b-102">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f040b-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="f040b-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f040b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="f040b-104">이 집합의 형식 중 하나라도 있으면 조건이 충족 되 고이 개체는 넓은 보기의이 정의를 사용 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f040b-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="f040b-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) SelectionCondition 요소에 대 한 요소 (형식)의 selectioncondition 요소에 대 한 SelectionCondition for WideEntry (형식)에 대 한 SelectionCondition의 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="f040b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f040b-106">구문</span><span class="sxs-lookup"><span data-stu-id="f040b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f040b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f040b-107">Attributes and Elements</span></span>

<span data-ttu-id="f040b-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="f040b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f040b-109">특성</span><span class="sxs-lookup"><span data-stu-id="f040b-109">Attributes</span></span>

<span data-ttu-id="f040b-110">없음</span><span class="sxs-lookup"><span data-stu-id="f040b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f040b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f040b-111">Child Elements</span></span>

<span data-ttu-id="f040b-112">없음</span><span class="sxs-lookup"><span data-stu-id="f040b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f040b-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f040b-113">Parent Elements</span></span>

|<span data-ttu-id="f040b-114">요소</span><span class="sxs-lookup"><span data-stu-id="f040b-114">Element</span></span>|<span data-ttu-id="f040b-115">설명</span><span class="sxs-lookup"><span data-stu-id="f040b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f040b-116">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="f040b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f040b-117">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f040b-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f040b-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="f040b-118">Text Value</span></span>

<span data-ttu-id="f040b-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f040b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f040b-120">설명</span><span class="sxs-lookup"><span data-stu-id="f040b-120">Remarks</span></span>

<span data-ttu-id="f040b-121">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f040b-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="f040b-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f040b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f040b-123">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="f040b-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="f040b-124">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f040b-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="f040b-125">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f040b-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f040b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f040b-126">See Also</span></span>

[<span data-ttu-id="f040b-127">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="f040b-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f040b-128">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="f040b-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f040b-129">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="f040b-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f040b-130">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="f040b-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f040b-131">WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="f040b-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f040b-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f040b-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
