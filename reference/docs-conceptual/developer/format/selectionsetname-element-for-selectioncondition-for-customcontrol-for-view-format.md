---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 SelectionCondition에 대한 SelectionSetName 요소(형식)
description: View에 대한 CustomControl의 SelectionCondition에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651608"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="d722e-103">View에 대한 CustomControl의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d722e-103">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="d722e-104">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d722e-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="d722e-105">이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d722e-105">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="d722e-106">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d722e-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d722e-107">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) customentries 요소에 대 한 customentries 요소에 대 한 CustomEntries 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="d722e-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d722e-108">구문</span><span class="sxs-lookup"><span data-stu-id="d722e-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d722e-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d722e-109">Attributes and Elements</span></span>

<span data-ttu-id="d722e-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="d722e-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d722e-111">특성</span><span class="sxs-lookup"><span data-stu-id="d722e-111">Attributes</span></span>

<span data-ttu-id="d722e-112">없음</span><span class="sxs-lookup"><span data-stu-id="d722e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d722e-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d722e-113">Child Elements</span></span>

<span data-ttu-id="d722e-114">없음</span><span class="sxs-lookup"><span data-stu-id="d722e-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d722e-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d722e-115">Parent Elements</span></span>

|<span data-ttu-id="d722e-116">요소</span><span class="sxs-lookup"><span data-stu-id="d722e-116">Element</span></span>|<span data-ttu-id="d722e-117">설명</span><span class="sxs-lookup"><span data-stu-id="d722e-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d722e-118">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d722e-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="d722e-119">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d722e-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d722e-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d722e-120">Text Value</span></span>

<span data-ttu-id="d722e-121">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d722e-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d722e-122">설명</span><span class="sxs-lookup"><span data-stu-id="d722e-122">Remarks</span></span>

<span data-ttu-id="d722e-123">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="d722e-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="d722e-124">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d722e-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d722e-125">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d722e-125">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="d722e-126">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d722e-126">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d722e-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d722e-127">See Also</span></span>

[<span data-ttu-id="d722e-128">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="d722e-128">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="d722e-129">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="d722e-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d722e-130">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="d722e-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d722e-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d722e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
