---
title: CustomControl for View (Format)의 경우 EntrySelectedBy에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364752"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="36d9c-102">View에 대한 CustomControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="36d9c-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="36d9c-103">목록 항목에 대 한 .NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="36d9c-104">항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="36d9c-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) Customentries 요소에 대 한 CustomControl의 customentries 요소 view (형식) EntrySelectedBy CustomEntry (형식)에 대해 EntrySelectedBy View (Format) SelectionSetName 요소의 CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="36d9c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36d9c-106">구문</span><span class="sxs-lookup"><span data-stu-id="36d9c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36d9c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="36d9c-107">Attributes and Elements</span></span>

<span data-ttu-id="36d9c-108">다음 섹션에서는 `SelectionSetName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36d9c-109">특성</span><span class="sxs-lookup"><span data-stu-id="36d9c-109">Attributes</span></span>

<span data-ttu-id="36d9c-110">없음</span><span class="sxs-lookup"><span data-stu-id="36d9c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36d9c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="36d9c-111">Child Elements</span></span>

<span data-ttu-id="36d9c-112">없음</span><span class="sxs-lookup"><span data-stu-id="36d9c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="36d9c-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="36d9c-113">Parent Elements</span></span>

|<span data-ttu-id="36d9c-114">요소</span><span class="sxs-lookup"><span data-stu-id="36d9c-114">Element</span></span>|<span data-ttu-id="36d9c-115">설명</span><span class="sxs-lookup"><span data-stu-id="36d9c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36d9c-116">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="36d9c-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="36d9c-117">이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="36d9c-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="36d9c-118">Text Value</span></span>

<span data-ttu-id="36d9c-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="36d9c-120">설명</span><span class="sxs-lookup"><span data-stu-id="36d9c-120">Remarks</span></span>

<span data-ttu-id="36d9c-121">각 사용자 지정 컨트롤 항목에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="36d9c-122">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="36d9c-123">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36d9c-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="36d9c-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36d9c-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="36d9c-125">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36d9c-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36d9c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36d9c-126">See Also</span></span>

[<span data-ttu-id="36d9c-127">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="36d9c-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="36d9c-128">사용자 지정 컨트롤 뷰</span><span class="sxs-lookup"><span data-stu-id="36d9c-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="36d9c-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="36d9c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
