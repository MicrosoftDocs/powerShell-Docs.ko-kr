---
title: 뷰 (형식)의 컨트롤에 대 한 CustomEntry의 EntrySelectedBy 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c82e02d23b1694d05f7a32578ccc5d33686f13f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774255"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="e5bbc-102">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e5bbc-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="e5bbc-103">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="e5bbc-104">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e5bbc-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤 요소 (형식)의 컨트롤에 대 한 컨트롤 요소 (format) CustomControl 요소 뷰 (format)의 컨트롤에 대 한 CustomControl에 대 한 CustomEntries 요소 뷰 (format) EntrySelectedBy 요소에 대 한 컨트롤의 Customentries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e5bbc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5bbc-106">구문</span><span class="sxs-lookup"><span data-stu-id="e5bbc-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5bbc-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e5bbc-107">Attributes and Elements</span></span>

<span data-ttu-id="e5bbc-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="e5bbc-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="e5bbc-109">정의의 유형, 선택 집합 또는 선택 조건을 하나 이상 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="e5bbc-110">사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5bbc-111">특성</span><span class="sxs-lookup"><span data-stu-id="e5bbc-111">Attributes</span></span>

<span data-ttu-id="e5bbc-112">없음</span><span class="sxs-lookup"><span data-stu-id="e5bbc-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5bbc-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e5bbc-113">Child Elements</span></span>

|<span data-ttu-id="e5bbc-114">요소</span><span class="sxs-lookup"><span data-stu-id="e5bbc-114">Element</span></span>|<span data-ttu-id="e5bbc-115">설명</span><span class="sxs-lookup"><span data-stu-id="e5bbc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5bbc-116">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e5bbc-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e5bbc-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e5bbc-118">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e5bbc-119">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e5bbc-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e5bbc-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e5bbc-121">컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="e5bbc-122">View에 대한 Controls의 EntrySelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e5bbc-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="e5bbc-123">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e5bbc-124">컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5bbc-125">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e5bbc-125">Parent Elements</span></span>

|<span data-ttu-id="e5bbc-126">요소</span><span class="sxs-lookup"><span data-stu-id="e5bbc-126">Element</span></span>|<span data-ttu-id="e5bbc-127">설명</span><span class="sxs-lookup"><span data-stu-id="e5bbc-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5bbc-128">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e5bbc-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="e5bbc-129">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5bbc-130">설명</span><span class="sxs-lookup"><span data-stu-id="e5bbc-130">Remarks</span></span>

<span data-ttu-id="e5bbc-131">선택 조건은 개체가 특정 속성을 가지는 경우 나 특정 속성 값 또는 스크립트가로 평가 되는 경우와 같이 사용 될 정의에 대해 존재 해야 하는 조건을 정의 하는 데 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="e5bbc-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e5bbc-132">선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e5bbc-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5bbc-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5bbc-133">See Also</span></span>

[<span data-ttu-id="e5bbc-134">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e5bbc-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="e5bbc-135">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e5bbc-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
