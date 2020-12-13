---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)
description: Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 5e4368a9546307c5ff223ae42ecaa1d2872bc587
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665960"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="92799-103">Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="92799-103">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="92799-104">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92799-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="92799-105">이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92799-105">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="92799-106">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="92799-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="92799-107">Configuration 요소 (format) 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한의 Customentries 요소 구성 (형식) EntrySelectedBy 요소 구성 (형식)에 대 한 컨트롤에 대 한 customentries의 구성 (형식) PropertyName 요소에 대해 ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="92799-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92799-108">구문</span><span class="sxs-lookup"><span data-stu-id="92799-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92799-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="92799-109">Attributes and Elements</span></span>

<span data-ttu-id="92799-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="92799-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92799-111">특성</span><span class="sxs-lookup"><span data-stu-id="92799-111">Attributes</span></span>

<span data-ttu-id="92799-112">없음</span><span class="sxs-lookup"><span data-stu-id="92799-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92799-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="92799-113">Child Elements</span></span>

<span data-ttu-id="92799-114">없음</span><span class="sxs-lookup"><span data-stu-id="92799-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92799-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="92799-115">Parent Elements</span></span>

|<span data-ttu-id="92799-116">요소</span><span class="sxs-lookup"><span data-stu-id="92799-116">Element</span></span>|<span data-ttu-id="92799-117">설명</span><span class="sxs-lookup"><span data-stu-id="92799-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92799-118">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="92799-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="92799-119">공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="92799-119">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92799-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="92799-120">Text Value</span></span>

<span data-ttu-id="92799-121">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="92799-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="92799-122">설명</span><span class="sxs-lookup"><span data-stu-id="92799-122">Remarks</span></span>

<span data-ttu-id="92799-123">선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92799-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="92799-124">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="92799-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92799-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92799-125">See Also</span></span>

[<span data-ttu-id="92799-126">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="92799-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="92799-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="92799-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
