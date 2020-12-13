---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: b775aa8a3184aa3ebcbda17a8e3191c69d67a700
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645723"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="e2276-103">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2276-103">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e2276-104">컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2276-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="e2276-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2276-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e2276-106">구성 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤 요소 구성 (형식)의 CustomControl에 대 한 CustomEntries 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 Customentries 요소 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 Customentries 요소 구성 (형식)에 대 한 컨트롤의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e2276-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2276-107">구문</span><span class="sxs-lookup"><span data-stu-id="e2276-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2276-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e2276-108">Attributes and Elements</span></span>

<span data-ttu-id="e2276-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="e2276-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2276-110">특성</span><span class="sxs-lookup"><span data-stu-id="e2276-110">Attributes</span></span>

<span data-ttu-id="e2276-111">None</span><span class="sxs-lookup"><span data-stu-id="e2276-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2276-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e2276-112">Child Elements</span></span>

<span data-ttu-id="e2276-113">없음</span><span class="sxs-lookup"><span data-stu-id="e2276-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2276-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e2276-114">Parent Elements</span></span>

|<span data-ttu-id="e2276-115">요소</span><span class="sxs-lookup"><span data-stu-id="e2276-115">Element</span></span>|<span data-ttu-id="e2276-116">설명</span><span class="sxs-lookup"><span data-stu-id="e2276-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2276-117">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2276-117">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e2276-118">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2276-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2276-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e2276-119">Text Value</span></span>

<span data-ttu-id="e2276-120">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2276-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2276-121">설명</span><span class="sxs-lookup"><span data-stu-id="e2276-121">Remarks</span></span>

<span data-ttu-id="e2276-122">각 컨트롤 정의에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2276-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e2276-123">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2276-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e2276-124">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2276-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2276-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2276-125">See Also</span></span>

[<span data-ttu-id="e2276-126">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2276-126">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e2276-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e2276-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
