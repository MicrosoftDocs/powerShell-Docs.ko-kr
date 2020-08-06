---
title: CustomControl for View (Format)의 경우 EntrySelectedBy에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3728a1886d5406b8fa4888125d1c031d0f9b1b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785305"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="edb21-102">View에 대한 CustomControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="edb21-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="edb21-103">목록 항목에 대 한 .NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="edb21-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="edb21-104">항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="edb21-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="edb21-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) customentries for view (format) customentries 요소에 대 한 CustomEntries 요소에 대 한 customentries 요소에 대 한 customentries 요소 (형식)의 경우 EntrySelectedBy View (format) SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="edb21-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="edb21-106">구문</span><span class="sxs-lookup"><span data-stu-id="edb21-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="edb21-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="edb21-107">Attributes and Elements</span></span>

<span data-ttu-id="edb21-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="edb21-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="edb21-109">특성</span><span class="sxs-lookup"><span data-stu-id="edb21-109">Attributes</span></span>

<span data-ttu-id="edb21-110">없음</span><span class="sxs-lookup"><span data-stu-id="edb21-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="edb21-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="edb21-111">Child Elements</span></span>

<span data-ttu-id="edb21-112">없음</span><span class="sxs-lookup"><span data-stu-id="edb21-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="edb21-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="edb21-113">Parent Elements</span></span>

|<span data-ttu-id="edb21-114">요소</span><span class="sxs-lookup"><span data-stu-id="edb21-114">Element</span></span>|<span data-ttu-id="edb21-115">설명</span><span class="sxs-lookup"><span data-stu-id="edb21-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edb21-116">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="edb21-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="edb21-117">이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="edb21-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="edb21-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="edb21-118">Text Value</span></span>

<span data-ttu-id="edb21-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="edb21-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="edb21-120">설명</span><span class="sxs-lookup"><span data-stu-id="edb21-120">Remarks</span></span>

<span data-ttu-id="edb21-121">각 사용자 지정 컨트롤 항목에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="edb21-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="edb21-122">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edb21-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="edb21-123">예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edb21-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="edb21-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="edb21-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="edb21-125">사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="edb21-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="edb21-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="edb21-126">See Also</span></span>

[<span data-ttu-id="edb21-127">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="edb21-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="edb21-128">사용자 지정 컨트롤 뷰</span><span class="sxs-lookup"><span data-stu-id="edb21-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="edb21-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="edb21-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
