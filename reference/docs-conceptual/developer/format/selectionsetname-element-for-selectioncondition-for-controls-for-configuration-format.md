---
title: 구성 (형식)에 대 한 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 62f186be9e4b1dd5a297add0ce82011bc1ccdcd1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785237"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="87aca-102">Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="87aca-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="87aca-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="87aca-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="87aca-104">이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87aca-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="87aca-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87aca-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="87aca-106">Configuration 요소 (format) 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 구성 (형식) Customentries 요소 구성에 대 한 컨트롤 (format) EntrySelectedBy 요소 구성 (format)의 컨트롤에 대 한 컨트롤에 대 한 항목의 SelectionCondition 요소 구성 (형식)에 대 한 컨트롤의 SelectionCondition 요소 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="87aca-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87aca-107">구문</span><span class="sxs-lookup"><span data-stu-id="87aca-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87aca-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="87aca-108">Attributes and Elements</span></span>

<span data-ttu-id="87aca-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="87aca-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87aca-110">특성</span><span class="sxs-lookup"><span data-stu-id="87aca-110">Attributes</span></span>

<span data-ttu-id="87aca-111">없음</span><span class="sxs-lookup"><span data-stu-id="87aca-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87aca-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="87aca-112">Child Elements</span></span>

<span data-ttu-id="87aca-113">없음</span><span class="sxs-lookup"><span data-stu-id="87aca-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="87aca-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="87aca-114">Parent Elements</span></span>

|<span data-ttu-id="87aca-115">요소</span><span class="sxs-lookup"><span data-stu-id="87aca-115">Element</span></span>|<span data-ttu-id="87aca-116">설명</span><span class="sxs-lookup"><span data-stu-id="87aca-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87aca-117">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="87aca-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="87aca-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="87aca-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="87aca-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="87aca-119">Text Value</span></span>

<span data-ttu-id="87aca-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="87aca-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="87aca-121">설명</span><span class="sxs-lookup"><span data-stu-id="87aca-121">Remarks</span></span>

<span data-ttu-id="87aca-122">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="87aca-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="87aca-123">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87aca-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="87aca-124">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87aca-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="87aca-125">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="87aca-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87aca-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87aca-126">See Also</span></span>

[<span data-ttu-id="87aca-127">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="87aca-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="87aca-128">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="87aca-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="87aca-129">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="87aca-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="87aca-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="87aca-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
