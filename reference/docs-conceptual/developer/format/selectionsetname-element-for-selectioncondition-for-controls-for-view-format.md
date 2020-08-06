---
title: View 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787532"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="b8bd7-102">View에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8bd7-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="b8bd7-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b8bd7-104">이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="b8bd7-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b8bd7-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소입니다. view (format) EntrySelectedBy의 컨트롤에 대 한 CustomEntries 요소의 항목 요소에 대 한 참조 요소 뷰 (format) SelectionSetName 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 컨트롤의 SelectionCondition 요소입니다 (형식).</span><span class="sxs-lookup"><span data-stu-id="b8bd7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8bd7-107">구문</span><span class="sxs-lookup"><span data-stu-id="b8bd7-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8bd7-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b8bd7-108">Attributes and Elements</span></span>

<span data-ttu-id="b8bd7-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="b8bd7-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8bd7-110">특성</span><span class="sxs-lookup"><span data-stu-id="b8bd7-110">Attributes</span></span>

<span data-ttu-id="b8bd7-111">없음</span><span class="sxs-lookup"><span data-stu-id="b8bd7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8bd7-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b8bd7-112">Child Elements</span></span>

<span data-ttu-id="b8bd7-113">없음</span><span class="sxs-lookup"><span data-stu-id="b8bd7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b8bd7-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b8bd7-114">Parent Elements</span></span>

|<span data-ttu-id="b8bd7-115">요소</span><span class="sxs-lookup"><span data-stu-id="b8bd7-115">Element</span></span>|<span data-ttu-id="b8bd7-116">설명</span><span class="sxs-lookup"><span data-stu-id="b8bd7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8bd7-117">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8bd7-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b8bd7-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b8bd7-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b8bd7-119">Text Value</span></span>

<span data-ttu-id="b8bd7-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8bd7-121">설명</span><span class="sxs-lookup"><span data-stu-id="b8bd7-121">Remarks</span></span>

<span data-ttu-id="b8bd7-122">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b8bd7-123">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b8bd7-124">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b8bd7-125">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8bd7-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8bd7-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8bd7-126">See Also</span></span>

[<span data-ttu-id="b8bd7-127">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8bd7-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="b8bd7-128">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="b8bd7-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b8bd7-129">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="b8bd7-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b8bd7-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b8bd7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
