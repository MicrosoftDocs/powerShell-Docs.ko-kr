---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: GroupBy의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: 7ebe5d884061243c8b4af196788187d84c15a92e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651852"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="43e19-103">GroupBy의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="43e19-103">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="43e19-104">목록 항목에 대 한 .NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="43e19-105">항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="43e19-106">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="43e19-107">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소 (format) CustomControl 요소에 대 한 CustomControl의 경우 CustomControl에 대 한 groupby (형식)의 customentries 요소에 대 한 요소에 대 한 Customentries 요소에 대 한 참조</span><span class="sxs-lookup"><span data-stu-id="43e19-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43e19-108">구문</span><span class="sxs-lookup"><span data-stu-id="43e19-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43e19-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="43e19-109">Attributes and Elements</span></span>

<span data-ttu-id="43e19-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="43e19-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43e19-111">특성</span><span class="sxs-lookup"><span data-stu-id="43e19-111">Attributes</span></span>

<span data-ttu-id="43e19-112">없음</span><span class="sxs-lookup"><span data-stu-id="43e19-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43e19-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="43e19-113">Child Elements</span></span>

<span data-ttu-id="43e19-114">없음</span><span class="sxs-lookup"><span data-stu-id="43e19-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43e19-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="43e19-115">Parent Elements</span></span>

|<span data-ttu-id="43e19-116">요소</span><span class="sxs-lookup"><span data-stu-id="43e19-116">Element</span></span>|<span data-ttu-id="43e19-117">설명</span><span class="sxs-lookup"><span data-stu-id="43e19-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43e19-118">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="43e19-118">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="43e19-119">이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-119">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="43e19-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="43e19-120">Text Value</span></span>

<span data-ttu-id="43e19-121">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="43e19-122">설명</span><span class="sxs-lookup"><span data-stu-id="43e19-122">Remarks</span></span>

<span data-ttu-id="43e19-123">각 사용자 지정 컨트롤 정의에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-123">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="43e19-124">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-124">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="43e19-125">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43e19-125">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="43e19-126">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43e19-126">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="43e19-127">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43e19-127">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43e19-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="43e19-128">See Also</span></span>

[<span data-ttu-id="43e19-129">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="43e19-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="43e19-130">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="43e19-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="43e19-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="43e19-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
