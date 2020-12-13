---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)
description: View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)
ms.openlocfilehash: ff481f13e6f16267bdda4c3053faebc96d9a6d3a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646052"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="f4baf-103">View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-103">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="f4baf-104">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-104">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="f4baf-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 customentries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4baf-106">구문</span><span class="sxs-lookup"><span data-stu-id="f4baf-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4baf-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f4baf-107">Attributes and Elements</span></span>

<span data-ttu-id="f4baf-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="f4baf-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="f4baf-109">정의에 표시 되는 항목을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4baf-110">특성</span><span class="sxs-lookup"><span data-stu-id="f4baf-110">Attributes</span></span>

<span data-ttu-id="f4baf-111">없음</span><span class="sxs-lookup"><span data-stu-id="f4baf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4baf-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f4baf-112">Child Elements</span></span>

|<span data-ttu-id="f4baf-113">요소</span><span class="sxs-lookup"><span data-stu-id="f4baf-113">Element</span></span>|<span data-ttu-id="f4baf-114">설명</span><span class="sxs-lookup"><span data-stu-id="f4baf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4baf-115">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-115">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="f4baf-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f4baf-117">사용자 지정 컨트롤 뷰의 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-117">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f4baf-118">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-118">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="f4baf-119">사용자 지정 컨트롤 정의에 대 한 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-119">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f4baf-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f4baf-120">Parent Elements</span></span>

|<span data-ttu-id="f4baf-121">요소</span><span class="sxs-lookup"><span data-stu-id="f4baf-121">Element</span></span>|<span data-ttu-id="f4baf-122">설명</span><span class="sxs-lookup"><span data-stu-id="f4baf-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4baf-123">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="f4baf-124">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-124">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="f4baf-125">사용자 지정 컨트롤 뷰에서 하나 이상의 정의를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-125">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f4baf-126">설명</span><span class="sxs-lookup"><span data-stu-id="f4baf-126">Remarks</span></span>

<span data-ttu-id="f4baf-127">대부분의 경우 각 사용자 지정 컨트롤 뷰에 대해 정의가 하나만 필요 하지만 동일한 뷰를 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 정의가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-127">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="f4baf-128">이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4baf-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4baf-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4baf-129">See Also</span></span>

[<span data-ttu-id="f4baf-130">View에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="f4baf-131">View 항목에 대 한 CustomItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f4baf-132">View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f4baf-132">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f4baf-133">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f4baf-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
