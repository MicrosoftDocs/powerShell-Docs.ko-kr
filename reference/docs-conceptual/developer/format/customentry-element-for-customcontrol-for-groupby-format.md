---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)
description: GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)
ms.openlocfilehash: 0df2ff9c15308939e6d2552f51e2961bdabc59fb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646062"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="14853-103">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="14853-103">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="14853-104">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="14853-104">Provides a definition of the control.</span></span> <span data-ttu-id="14853-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14853-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="14853-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomControl 요소에 대 한 CustomControl의 경우 groupby (format) Customentries 요소에 대해 groupby (형식)의 경우 CustomControl에 대 한 Customentries 요소</span><span class="sxs-lookup"><span data-stu-id="14853-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="14853-107">구문</span><span class="sxs-lookup"><span data-stu-id="14853-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="14853-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="14853-108">Attributes and Elements</span></span>

<span data-ttu-id="14853-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="14853-109">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="14853-110">특성</span><span class="sxs-lookup"><span data-stu-id="14853-110">Attributes</span></span>

<span data-ttu-id="14853-111">없음</span><span class="sxs-lookup"><span data-stu-id="14853-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="14853-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="14853-112">Child Elements</span></span>

|<span data-ttu-id="14853-113">요소</span><span class="sxs-lookup"><span data-stu-id="14853-113">Element</span></span>|<span data-ttu-id="14853-114">설명</span><span class="sxs-lookup"><span data-stu-id="14853-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="14853-115">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="14853-115">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="14853-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="14853-116">Optional element.</span></span><br /><br /> <span data-ttu-id="14853-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="14853-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="14853-118">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="14853-118">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="14853-119">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="14853-119">Required element.</span></span><br /><br /> <span data-ttu-id="14853-120">컨트롤에서 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="14853-120">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="14853-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="14853-121">Parent Elements</span></span>

|<span data-ttu-id="14853-122">요소</span><span class="sxs-lookup"><span data-stu-id="14853-122">Element</span></span>|<span data-ttu-id="14853-123">설명</span><span class="sxs-lookup"><span data-stu-id="14853-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="14853-124">GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="14853-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="14853-125">컨트롤에 대 한 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="14853-125">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="14853-126">설명</span><span class="sxs-lookup"><span data-stu-id="14853-126">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="14853-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14853-127">See Also</span></span>

[<span data-ttu-id="14853-128">GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="14853-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="14853-129">GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="14853-129">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="14853-130">GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="14853-130">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="14853-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="14853-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
