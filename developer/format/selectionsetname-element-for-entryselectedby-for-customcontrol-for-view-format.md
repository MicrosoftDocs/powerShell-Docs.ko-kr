---
title: CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063979"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="9fcb1-102">View에 대한 CustomControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9fcb1-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="9fcb1-103">목록 항목에 대 한.NET 개체 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="9fcb1-104">항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="9fcb1-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry EntrySelectedBy CustomEntry (형식)에 대 한 보기 (형식) SelectionSetName 요소에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="9fcb1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9fcb1-106">구문</span><span class="sxs-lookup"><span data-stu-id="9fcb1-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9fcb1-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9fcb1-107">Attributes and Elements</span></span>

<span data-ttu-id="9fcb1-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9fcb1-109">특성</span><span class="sxs-lookup"><span data-stu-id="9fcb1-109">Attributes</span></span>

<span data-ttu-id="9fcb1-110">없음</span><span class="sxs-lookup"><span data-stu-id="9fcb1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9fcb1-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9fcb1-111">Child Elements</span></span>

<span data-ttu-id="9fcb1-112">없음</span><span class="sxs-lookup"><span data-stu-id="9fcb1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9fcb1-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9fcb1-113">Parent Elements</span></span>

|<span data-ttu-id="9fcb1-114">요소</span><span class="sxs-lookup"><span data-stu-id="9fcb1-114">Element</span></span>|<span data-ttu-id="9fcb1-115">설명</span><span class="sxs-lookup"><span data-stu-id="9fcb1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fcb1-116">뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="9fcb1-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="9fcb1-117">이 사용자 지정 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9fcb1-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9fcb1-118">Text Value</span></span>

<span data-ttu-id="9fcb1-119">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9fcb1-120">설명</span><span class="sxs-lookup"><span data-stu-id="9fcb1-120">Remarks</span></span>

<span data-ttu-id="9fcb1-121">각 사용자 지정 컨트롤 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9fcb1-122">선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9fcb1-123">예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="9fcb1-124">선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [선택 영역 설정 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9fcb1-125">사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="9fcb1-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fcb1-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fcb1-126">See Also</span></span>

[<span data-ttu-id="9fcb1-127">뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="9fcb1-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9fcb1-128">사용자 지정 컨트롤 뷰</span><span class="sxs-lookup"><span data-stu-id="9fcb1-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="9fcb1-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="9fcb1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
