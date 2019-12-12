---
title: WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368412"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="81f44-102">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="81f44-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="81f44-103">조건을 트리거하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f44-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="81f44-104">이 집합의 형식 중 하나라도 있으면 조건이 충족 되 고이 개체는 넓은 보기의이 정의를 사용 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81f44-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="81f44-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (Format) SelectionCondition 요소 WideEntry (형식)에 대 한 EntrySelectedBy WideEntry (Format) SelectionSetName 요소에 대 한 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="81f44-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81f44-106">구문</span><span class="sxs-lookup"><span data-stu-id="81f44-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81f44-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="81f44-107">Attributes and Elements</span></span>

<span data-ttu-id="81f44-108">다음 섹션에서는 특성, 자식 요소 및 `SelectionSetName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f44-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81f44-109">특성</span><span class="sxs-lookup"><span data-stu-id="81f44-109">Attributes</span></span>

<span data-ttu-id="81f44-110">없음</span><span class="sxs-lookup"><span data-stu-id="81f44-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81f44-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="81f44-111">Child Elements</span></span>

<span data-ttu-id="81f44-112">없음</span><span class="sxs-lookup"><span data-stu-id="81f44-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="81f44-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="81f44-113">Parent Elements</span></span>

|<span data-ttu-id="81f44-114">요소</span><span class="sxs-lookup"><span data-stu-id="81f44-114">Element</span></span>|<span data-ttu-id="81f44-115">설명</span><span class="sxs-lookup"><span data-stu-id="81f44-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81f44-116">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="81f44-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="81f44-117">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f44-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="81f44-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="81f44-118">Text Value</span></span>

<span data-ttu-id="81f44-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f44-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="81f44-120">설명</span><span class="sxs-lookup"><span data-stu-id="81f44-120">Remarks</span></span>

<span data-ttu-id="81f44-121">선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81f44-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="81f44-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="81f44-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="81f44-123">선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="81f44-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="81f44-124">선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="81f44-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="81f44-125">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="81f44-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81f44-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81f44-126">See Also</span></span>

[<span data-ttu-id="81f44-127">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="81f44-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="81f44-128">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="81f44-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="81f44-129">선택 집합 정의</span><span class="sxs-lookup"><span data-stu-id="81f44-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="81f44-130">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="81f44-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="81f44-131">WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="81f44-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="81f44-132">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="81f44-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
