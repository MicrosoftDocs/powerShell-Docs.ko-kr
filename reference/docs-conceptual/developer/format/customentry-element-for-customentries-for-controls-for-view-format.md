---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)
description: View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)
ms.openlocfilehash: a525b198c8f595e04dc0804d36b5533b94f43c6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646083"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="b5861-103">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5861-103">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="b5861-104">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5861-104">Provides a definition of the control.</span></span> <span data-ttu-id="b5861-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5861-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b5861-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 컨트롤에 대 한 컨트롤의 요소 (format) Customentries 요소에 대 한 컨트롤의 컨트롤에 대 한 CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="b5861-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5861-107">구문</span><span class="sxs-lookup"><span data-stu-id="b5861-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5861-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b5861-108">Attributes and Elements</span></span>

<span data-ttu-id="b5861-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="b5861-109">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5861-110">특성</span><span class="sxs-lookup"><span data-stu-id="b5861-110">Attributes</span></span>

<span data-ttu-id="b5861-111">없음</span><span class="sxs-lookup"><span data-stu-id="b5861-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5861-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b5861-112">Child Elements</span></span>

|<span data-ttu-id="b5861-113">요소</span><span class="sxs-lookup"><span data-stu-id="b5861-113">Element</span></span>|<span data-ttu-id="b5861-114">설명</span><span class="sxs-lookup"><span data-stu-id="b5861-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5861-115">View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5861-115">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="b5861-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b5861-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b5861-117">이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5861-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="b5861-118">View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5861-118">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="b5861-119">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b5861-119">Required element.</span></span><br /><br /> <span data-ttu-id="b5861-120">컨트롤에서 데이터를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5861-120">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5861-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b5861-121">Parent Elements</span></span>

|<span data-ttu-id="b5861-122">요소</span><span class="sxs-lookup"><span data-stu-id="b5861-122">Element</span></span>|<span data-ttu-id="b5861-123">설명</span><span class="sxs-lookup"><span data-stu-id="b5861-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5861-124">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5861-124">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="b5861-125">컨트롤에 대 한 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5861-125">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5861-126">설명</span><span class="sxs-lookup"><span data-stu-id="b5861-126">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b5861-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5861-127">See Also</span></span>

[<span data-ttu-id="b5861-128">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b5861-128">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b5861-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b5861-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
