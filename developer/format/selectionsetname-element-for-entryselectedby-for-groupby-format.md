---
title: GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064070"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="dd2ec-102">GroupBy의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="dd2ec-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="dd2ec-103">목록 항목에 대 한.NET 개체 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="dd2ec-104">항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="dd2ec-105">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="dd2ec-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 GroupBy (형식)에 대 한 GroupBy (형식) EntrySelectedBy 요소에</span><span class="sxs-lookup"><span data-stu-id="dd2ec-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd2ec-107">구문</span><span class="sxs-lookup"><span data-stu-id="dd2ec-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd2ec-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="dd2ec-108">Attributes and Elements</span></span>

<span data-ttu-id="dd2ec-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd2ec-110">특성</span><span class="sxs-lookup"><span data-stu-id="dd2ec-110">Attributes</span></span>

<span data-ttu-id="dd2ec-111">없음</span><span class="sxs-lookup"><span data-stu-id="dd2ec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd2ec-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="dd2ec-112">Child Elements</span></span>

<span data-ttu-id="dd2ec-113">없음</span><span class="sxs-lookup"><span data-stu-id="dd2ec-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd2ec-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="dd2ec-114">Parent Elements</span></span>

|<span data-ttu-id="dd2ec-115">요소</span><span class="sxs-lookup"><span data-stu-id="dd2ec-115">Element</span></span>|<span data-ttu-id="dd2ec-116">설명</span><span class="sxs-lookup"><span data-stu-id="dd2ec-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd2ec-117">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="dd2ec-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="dd2ec-118">이 사용자 지정 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dd2ec-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="dd2ec-119">Text Value</span></span>

<span data-ttu-id="dd2ec-120">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd2ec-121">설명</span><span class="sxs-lookup"><span data-stu-id="dd2ec-121">Remarks</span></span>

<span data-ttu-id="dd2ec-122">각 사용자 지정 컨트롤 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="dd2ec-123">선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="dd2ec-124">예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="dd2ec-125">선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [선택 영역 설정 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="dd2ec-126">사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="dd2ec-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd2ec-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd2ec-127">See Also</span></span>

[<span data-ttu-id="dd2ec-128">GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="dd2ec-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="dd2ec-129">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="dd2ec-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="dd2ec-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="dd2ec-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
