---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: View에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: 3211b7cacd7e57770b48b03f4aade33da506f180
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664735"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="4eb9c-103">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4eb9c-103">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="4eb9c-104">컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb9c-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="4eb9c-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb9c-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4eb9c-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) controls 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤에 대 한 뷰 (format) CustomEntries 요소에 대 한 컨트롤 요소 view (format) Entry 항목에 대 한 컨트롤의 Customentries 요소에 대 한 컨트롤 뷰 (format) SelectionSetName 요소에 대 한 컨트롤의 Customentries 요소 (형식)에 대 한 컨트롤의 경우 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="4eb9c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4eb9c-107">구문</span><span class="sxs-lookup"><span data-stu-id="4eb9c-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4eb9c-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4eb9c-108">Attributes and Elements</span></span>

<span data-ttu-id="4eb9c-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="4eb9c-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4eb9c-110">특성</span><span class="sxs-lookup"><span data-stu-id="4eb9c-110">Attributes</span></span>

<span data-ttu-id="4eb9c-111">None</span><span class="sxs-lookup"><span data-stu-id="4eb9c-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="4eb9c-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4eb9c-112">Child Elements</span></span>

<span data-ttu-id="4eb9c-113">없음</span><span class="sxs-lookup"><span data-stu-id="4eb9c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4eb9c-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4eb9c-114">Parent Elements</span></span>

|<span data-ttu-id="4eb9c-115">요소</span><span class="sxs-lookup"><span data-stu-id="4eb9c-115">Element</span></span>|<span data-ttu-id="4eb9c-116">설명</span><span class="sxs-lookup"><span data-stu-id="4eb9c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4eb9c-117">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4eb9c-117">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="4eb9c-118">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb9c-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4eb9c-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4eb9c-119">Text Value</span></span>

<span data-ttu-id="4eb9c-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb9c-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4eb9c-121">설명</span><span class="sxs-lookup"><span data-stu-id="4eb9c-121">Remarks</span></span>

<span data-ttu-id="4eb9c-122">각 컨트롤 정의에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb9c-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4eb9c-123">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb9c-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4eb9c-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4eb9c-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4eb9c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4eb9c-125">See Also</span></span>

[<span data-ttu-id="4eb9c-126">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4eb9c-126">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="4eb9c-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4eb9c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
