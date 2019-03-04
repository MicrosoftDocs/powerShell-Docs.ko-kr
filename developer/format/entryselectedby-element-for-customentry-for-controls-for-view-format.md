---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859539"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="b1d83-102">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b1d83-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="b1d83-103">이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="b1d83-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b1d83-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry 보기 (형식)에 대 한 컨트롤에 대 한 보기 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한 컨트롤에 대 한</span><span class="sxs-lookup"><span data-stu-id="b1d83-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1d83-106">구문</span><span class="sxs-lookup"><span data-stu-id="b1d83-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1d83-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-107">Attributes and Elements</span></span>

<span data-ttu-id="b1d83-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="b1d83-109">하나 이상의 형식 또는 선택 집합 정의 대 한 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="b1d83-110">사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1d83-111">특성</span><span class="sxs-lookup"><span data-stu-id="b1d83-111">Attributes</span></span>

<span data-ttu-id="b1d83-112">없음</span><span class="sxs-lookup"><span data-stu-id="b1d83-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1d83-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-113">Child Elements</span></span>

|<span data-ttu-id="b1d83-114">요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-114">Element</span></span>|<span data-ttu-id="b1d83-115">설명</span><span class="sxs-lookup"><span data-stu-id="b1d83-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1d83-116">뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b1d83-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b1d83-118">이 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="b1d83-119">뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b1d83-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b1d83-121">컨트롤의이 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="b1d83-122">뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b1d83-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b1d83-124">컨트롤의이 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b1d83-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-125">Parent Elements</span></span>

|<span data-ttu-id="b1d83-126">요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-126">Element</span></span>|<span data-ttu-id="b1d83-127">설명</span><span class="sxs-lookup"><span data-stu-id="b1d83-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1d83-128">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b1d83-129">컨트롤의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1d83-130">설명</span><span class="sxs-lookup"><span data-stu-id="b1d83-130">Remarks</span></span>

<span data-ttu-id="b1d83-131">선택 조건을 사용 하 여 사용할 조건을 정의한 다음 있어야 하는 데 사용할 정의 대 한, 개체의 특정 속성에 있을 때와 같은 또는 특정 속성 값 이거나 스크립트 계산 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="b1d83-132">선택 조건에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="b1d83-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1d83-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1d83-133">See Also</span></span>

[<span data-ttu-id="b1d83-134">뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="b1d83-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="b1d83-135">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="b1d83-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
