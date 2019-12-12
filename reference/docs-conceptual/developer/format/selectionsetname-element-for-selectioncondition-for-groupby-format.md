---
title: GroupBy (형식)의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361862"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="25d20-102">GroupBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="25d20-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="25d20-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="25d20-104">이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="25d20-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="25d20-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) EntrySelectedBy 요소에 대 한 CustomControl 요소에 대 한 CustomEntry for groupby (format) SelectionSetName 요소에 대 한 SelectionCondition 요소의 groupby (형식)</span><span class="sxs-lookup"><span data-stu-id="25d20-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25d20-107">구문</span><span class="sxs-lookup"><span data-stu-id="25d20-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25d20-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="25d20-108">Attributes and Elements</span></span>

<span data-ttu-id="25d20-109">다음 섹션에서는 특성, 자식 요소 및 `SelectionSetName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25d20-110">특성</span><span class="sxs-lookup"><span data-stu-id="25d20-110">Attributes</span></span>

<span data-ttu-id="25d20-111">없음</span><span class="sxs-lookup"><span data-stu-id="25d20-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25d20-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="25d20-112">Child Elements</span></span>

<span data-ttu-id="25d20-113">없음</span><span class="sxs-lookup"><span data-stu-id="25d20-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25d20-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="25d20-114">Parent Elements</span></span>

|<span data-ttu-id="25d20-115">요소</span><span class="sxs-lookup"><span data-stu-id="25d20-115">Element</span></span>|<span data-ttu-id="25d20-116">설명</span><span class="sxs-lookup"><span data-stu-id="25d20-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25d20-117">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="25d20-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="25d20-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="25d20-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="25d20-119">Text Value</span></span>

<span data-ttu-id="25d20-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="25d20-121">설명</span><span class="sxs-lookup"><span data-stu-id="25d20-121">Remarks</span></span>

<span data-ttu-id="25d20-122">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="25d20-123">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25d20-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="25d20-124">이 요소를 지정 하면 [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25d20-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="25d20-125">선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25d20-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="25d20-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25d20-126">See Also</span></span>

[<span data-ttu-id="25d20-127">GroupBy (형식)에 대 한 SelectionCondition의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="25d20-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="25d20-128">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="25d20-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="25d20-129">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="25d20-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="25d20-130">선택 집합 정의</span><span class="sxs-lookup"><span data-stu-id="25d20-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="25d20-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="25d20-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
