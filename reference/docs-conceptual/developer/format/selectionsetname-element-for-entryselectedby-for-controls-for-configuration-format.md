---
title: 구성 (형식)의 컨트롤에 대 한 EntrySelectedBy의 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364792"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="f77ec-102">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f77ec-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f77ec-103">컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="f77ec-104">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f77ec-105">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) CustomControl의 컨트롤에 대 한 CustomEntry 요소 구성 (형식)의 컨트롤에 대 한 customentry 요소 구성 (형식)에 대 한 컨트롤의 경우 EntrySelectedBy 요소에 대 한 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f77ec-106">구문</span><span class="sxs-lookup"><span data-stu-id="f77ec-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f77ec-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f77ec-107">Attributes and Elements</span></span>

<span data-ttu-id="f77ec-108">다음 섹션에서는 `SelectionSetName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f77ec-109">특성</span><span class="sxs-lookup"><span data-stu-id="f77ec-109">Attributes</span></span>

<span data-ttu-id="f77ec-110">없음</span><span class="sxs-lookup"><span data-stu-id="f77ec-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f77ec-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f77ec-111">Child Elements</span></span>

<span data-ttu-id="f77ec-112">없음</span><span class="sxs-lookup"><span data-stu-id="f77ec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f77ec-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f77ec-113">Parent Elements</span></span>

|<span data-ttu-id="f77ec-114">요소</span><span class="sxs-lookup"><span data-stu-id="f77ec-114">Element</span></span>|<span data-ttu-id="f77ec-115">설명</span><span class="sxs-lookup"><span data-stu-id="f77ec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f77ec-116">구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f77ec-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f77ec-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f77ec-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="f77ec-118">Text Value</span></span>

<span data-ttu-id="f77ec-119">선택 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f77ec-120">설명</span><span class="sxs-lookup"><span data-stu-id="f77ec-120">Remarks</span></span>

<span data-ttu-id="f77ec-121">각 컨트롤 정의에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f77ec-122">선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f77ec-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="f77ec-123">선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f77ec-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f77ec-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f77ec-124">See Also</span></span>

[<span data-ttu-id="f77ec-125">구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f77ec-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f77ec-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f77ec-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
