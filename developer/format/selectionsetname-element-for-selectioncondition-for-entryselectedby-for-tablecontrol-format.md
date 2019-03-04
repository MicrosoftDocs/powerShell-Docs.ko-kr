---
title: TableControl (형식)에 대 한 EntrySelectedBy에 대 한 SelectionCondition SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863279"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="bed6f-102">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="bed6f-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="bed6f-103">트리거 조건이 있는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="bed6f-104">있는 경우이 집합의 형식 중 하나는 조건이 충족 하 고 개체 테이블 보기의이 정의 사용 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="bed6f-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 TableRowEntry (형식)에 대 한 EntrySelectedBy EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소 TableRowEntry (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bed6f-106">구문</span><span class="sxs-lookup"><span data-stu-id="bed6f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bed6f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-107">Attributes and Elements</span></span>

<span data-ttu-id="bed6f-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bed6f-109">특성</span><span class="sxs-lookup"><span data-stu-id="bed6f-109">Attributes</span></span>

<span data-ttu-id="bed6f-110">없음</span><span class="sxs-lookup"><span data-stu-id="bed6f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bed6f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-111">Child Elements</span></span>

<span data-ttu-id="bed6f-112">없음</span><span class="sxs-lookup"><span data-stu-id="bed6f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bed6f-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-113">Parent Elements</span></span>

|<span data-ttu-id="bed6f-114">요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-114">Element</span></span>|<span data-ttu-id="bed6f-115">설명</span><span class="sxs-lookup"><span data-stu-id="bed6f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bed6f-116">TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="bed6f-117">테이블 보기의이 정의에 사용할 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bed6f-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="bed6f-118">Text Value</span></span>

<span data-ttu-id="bed6f-119">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="bed6f-120">설명</span><span class="sxs-lookup"><span data-stu-id="bed6f-120">Remarks</span></span>

<span data-ttu-id="bed6f-121">선택 조건 선택 집합 또는.NET 형식을 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="bed6f-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="bed6f-123">선택 영역 집합은 일반적인 그룹 형식 지정 파일을 정의 하는 모든 보기에서 사용할 수 있는.NET 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="bed6f-124">만들기 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="bed6f-125">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bed6f-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bed6f-126">See Also</span></span>

[<span data-ttu-id="bed6f-127">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="bed6f-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bed6f-128">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bed6f-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bed6f-129">SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="bed6f-130">TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="bed6f-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="bed6f-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="bed6f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
