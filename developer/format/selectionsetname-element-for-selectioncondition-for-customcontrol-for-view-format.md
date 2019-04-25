---
title: CustomControl 보려면 (형식)에 대 한 SelectionCondition SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075582"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="1d7dd-102">View에 대한 CustomControl의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1d7dd-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="1d7dd-103">트리거 조건이 있는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1d7dd-104">있는 경우이 집합의 형식 중 하나는 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="1d7dd-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1d7dd-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 뷰 (형식)에 대 한 CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="1d7dd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d7dd-107">구문</span><span class="sxs-lookup"><span data-stu-id="1d7dd-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d7dd-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1d7dd-108">Attributes and Elements</span></span>

<span data-ttu-id="1d7dd-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d7dd-110">특성</span><span class="sxs-lookup"><span data-stu-id="1d7dd-110">Attributes</span></span>

<span data-ttu-id="1d7dd-111">없음</span><span class="sxs-lookup"><span data-stu-id="1d7dd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d7dd-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1d7dd-112">Child Elements</span></span>

<span data-ttu-id="1d7dd-113">없음</span><span class="sxs-lookup"><span data-stu-id="1d7dd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1d7dd-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1d7dd-114">Parent Elements</span></span>

|<span data-ttu-id="1d7dd-115">요소</span><span class="sxs-lookup"><span data-stu-id="1d7dd-115">Element</span></span>|<span data-ttu-id="1d7dd-116">설명</span><span class="sxs-lookup"><span data-stu-id="1d7dd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d7dd-117">CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1d7dd-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="1d7dd-118">사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1d7dd-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1d7dd-119">Text Value</span></span>

<span data-ttu-id="1d7dd-120">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d7dd-121">설명</span><span class="sxs-lookup"><span data-stu-id="1d7dd-121">Remarks</span></span>

<span data-ttu-id="1d7dd-122">선택 영역 집합은 일반적인 그룹 형식 지정 파일을 정의 하는 모든 보기에서 사용할 수 있는.NET 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1d7dd-123">만들기 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1d7dd-124">선택 조건 선택 집합 또는.NET 형식을 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="1d7dd-125">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d7dd-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d7dd-126">See Also</span></span>

[<span data-ttu-id="1d7dd-127">CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1d7dd-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="1d7dd-128">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7dd-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1d7dd-129">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="1d7dd-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1d7dd-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1d7dd-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
