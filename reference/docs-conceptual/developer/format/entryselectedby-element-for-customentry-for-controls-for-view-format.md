---
title: 뷰 (형식)의 컨트롤에 대 한 CustomEntry의 EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363892"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="ab3b8-102">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ab3b8-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="ab3b8-103">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ab3b8-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ab3b8-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. 보기 (형식)의 컨트롤에 대 한 CustomControl 컨트롤의 CustomEntry 요소에 대 한 컨트롤의 customentry 요소 (형식)에 대 한 CustomEntry의 Customentry 요소</span><span class="sxs-lookup"><span data-stu-id="ab3b8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab3b8-106">구문</span><span class="sxs-lookup"><span data-stu-id="ab3b8-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab3b8-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ab3b8-107">Attributes and Elements</span></span>

<span data-ttu-id="ab3b8-108">다음 섹션에서는 `EntrySelectedBy` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="ab3b8-109">정의의 유형, 선택 집합 또는 선택 조건을 하나 이상 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="ab3b8-110">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab3b8-111">특성</span><span class="sxs-lookup"><span data-stu-id="ab3b8-111">Attributes</span></span>

<span data-ttu-id="ab3b8-112">없음</span><span class="sxs-lookup"><span data-stu-id="ab3b8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab3b8-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ab3b8-113">Child Elements</span></span>

|<span data-ttu-id="ab3b8-114">요소</span><span class="sxs-lookup"><span data-stu-id="ab3b8-114">Element</span></span>|<span data-ttu-id="ab3b8-115">설명</span><span class="sxs-lookup"><span data-stu-id="ab3b8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab3b8-116">보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ab3b8-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ab3b8-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ab3b8-118">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ab3b8-119">View의 컨트롤에 대 한 EntrySelectedBy의 SelectionSetName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ab3b8-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ab3b8-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ab3b8-121">컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="ab3b8-122">View 컨트롤에 대 한 EntrySelectedBy (형식)의 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="ab3b8-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="ab3b8-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-123">Optional element.</span></span><br /><br /> <span data-ttu-id="ab3b8-124">컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab3b8-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ab3b8-125">Parent Elements</span></span>

|<span data-ttu-id="ab3b8-126">요소</span><span class="sxs-lookup"><span data-stu-id="ab3b8-126">Element</span></span>|<span data-ttu-id="ab3b8-127">설명</span><span class="sxs-lookup"><span data-stu-id="ab3b8-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab3b8-128">뷰의 컨트롤에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ab3b8-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="ab3b8-129">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab3b8-130">설명</span><span class="sxs-lookup"><span data-stu-id="ab3b8-130">Remarks</span></span>

<span data-ttu-id="ab3b8-131">선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가 `true`으로 평가 되는 경우와 같이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="ab3b8-132">선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab3b8-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab3b8-133">See Also</span></span>

[<span data-ttu-id="ab3b8-134">뷰의 컨트롤에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ab3b8-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="ab3b8-135">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ab3b8-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
