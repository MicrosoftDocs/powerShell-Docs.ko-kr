---
title: TableControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: db751c40b22db52985bc7cd9f8f4296a64a523f0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787464"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="1299e-102">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1299e-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="1299e-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1299e-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1299e-104">이 집합의 형식 중 하나라도 있으면 조건이 충족 되 고 테이블 뷰의이 정의를 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1299e-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="1299e-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소에 대 한 TableRowEntry (format) SelectionCondition 요소에 대 한 요소 (형식)의 selectioncondition 요소에 대 한 SelectionCondition for TableRowEntry (형식)에 대 한 SelectionCondition의 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="1299e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1299e-106">구문</span><span class="sxs-lookup"><span data-stu-id="1299e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1299e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1299e-107">Attributes and Elements</span></span>

<span data-ttu-id="1299e-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="1299e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1299e-109">특성</span><span class="sxs-lookup"><span data-stu-id="1299e-109">Attributes</span></span>

<span data-ttu-id="1299e-110">없음</span><span class="sxs-lookup"><span data-stu-id="1299e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1299e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1299e-111">Child Elements</span></span>

<span data-ttu-id="1299e-112">없음</span><span class="sxs-lookup"><span data-stu-id="1299e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1299e-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1299e-113">Parent Elements</span></span>

|<span data-ttu-id="1299e-114">요소</span><span class="sxs-lookup"><span data-stu-id="1299e-114">Element</span></span>|<span data-ttu-id="1299e-115">설명</span><span class="sxs-lookup"><span data-stu-id="1299e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1299e-116">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1299e-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1299e-117">테이블 뷰의이 정의에 사용할 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1299e-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1299e-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1299e-118">Text Value</span></span>

<span data-ttu-id="1299e-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1299e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1299e-120">설명</span><span class="sxs-lookup"><span data-stu-id="1299e-120">Remarks</span></span>

<span data-ttu-id="1299e-121">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1299e-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="1299e-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1299e-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1299e-123">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="1299e-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1299e-124">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1299e-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1299e-125">넓은 뷰의 다른 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1299e-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1299e-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1299e-126">See Also</span></span>

[<span data-ttu-id="1299e-127">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="1299e-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1299e-128">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="1299e-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1299e-129">TableRowEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="1299e-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1299e-130">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1299e-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1299e-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1299e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
