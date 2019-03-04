---
title: 구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860909"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="63096-102">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="63096-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="63096-103">컨트롤의이 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63096-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="63096-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63096-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="63096-105">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry EntrySelectedBy 구성 (형식)에 대 한 컨트롤에 대 한 구성 (형식) SelectionSetName 요소에 대 한 컨트롤에 대 한 구성 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="63096-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63096-106">구문</span><span class="sxs-lookup"><span data-stu-id="63096-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="63096-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="63096-107">Attributes and Elements</span></span>

<span data-ttu-id="63096-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="63096-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63096-109">특성</span><span class="sxs-lookup"><span data-stu-id="63096-109">Attributes</span></span>

<span data-ttu-id="63096-110">없음</span><span class="sxs-lookup"><span data-stu-id="63096-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="63096-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="63096-111">Child Elements</span></span>

<span data-ttu-id="63096-112">없음</span><span class="sxs-lookup"><span data-stu-id="63096-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63096-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="63096-113">Parent Elements</span></span>

|<span data-ttu-id="63096-114">요소</span><span class="sxs-lookup"><span data-stu-id="63096-114">Element</span></span>|<span data-ttu-id="63096-115">설명</span><span class="sxs-lookup"><span data-stu-id="63096-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63096-116">구성 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="63096-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="63096-117">이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63096-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="63096-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="63096-118">Text Value</span></span>

<span data-ttu-id="63096-119">선택 항목 집합의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63096-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="63096-120">설명</span><span class="sxs-lookup"><span data-stu-id="63096-120">Remarks</span></span>

<span data-ttu-id="63096-121">각 컨트롤 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63096-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="63096-122">선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63096-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="63096-123">선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [선택 영역 설정 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="63096-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63096-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63096-124">See Also</span></span>

[<span data-ttu-id="63096-125">구성 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="63096-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="63096-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="63096-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
