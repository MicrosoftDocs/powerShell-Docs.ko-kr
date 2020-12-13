---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)
description: GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)
ms.openlocfilehash: cde59d38b83930cb64a3a0040891783e4ab96723
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666793"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="ccca6-103">GroupBy의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ccca6-103">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="ccca6-104">컨트롤에 대 한 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccca6-104">Provides the definitions for the control.</span></span> <span data-ttu-id="ccca6-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccca6-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ccca6-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소에 대 한 groupby 요소 (format) CustomControl 요소에 대 한 groupby 요소 (형식)의 경우 CustomControl에 대 한 CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="ccca6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccca6-107">구문</span><span class="sxs-lookup"><span data-stu-id="ccca6-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccca6-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ccca6-108">Attributes and Elements</span></span>

<span data-ttu-id="ccca6-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntries` .</span><span class="sxs-lookup"><span data-stu-id="ccca6-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="ccca6-110">지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccca6-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccca6-111">특성</span><span class="sxs-lookup"><span data-stu-id="ccca6-111">Attributes</span></span>

<span data-ttu-id="ccca6-112">없음</span><span class="sxs-lookup"><span data-stu-id="ccca6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccca6-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ccca6-113">Child Elements</span></span>

|<span data-ttu-id="ccca6-114">요소</span><span class="sxs-lookup"><span data-stu-id="ccca6-114">Element</span></span>|<span data-ttu-id="ccca6-115">설명</span><span class="sxs-lookup"><span data-stu-id="ccca6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccca6-116">GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ccca6-116">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="ccca6-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ccca6-117">Required element.</span></span><br /><br /> <span data-ttu-id="ccca6-118">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccca6-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ccca6-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ccca6-119">Parent Elements</span></span>

|<span data-ttu-id="ccca6-120">요소</span><span class="sxs-lookup"><span data-stu-id="ccca6-120">Element</span></span>|<span data-ttu-id="ccca6-121">설명</span><span class="sxs-lookup"><span data-stu-id="ccca6-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccca6-122">GroupBy에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ccca6-122">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="ccca6-123">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccca6-123">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ccca6-124">설명</span><span class="sxs-lookup"><span data-stu-id="ccca6-124">Remarks</span></span>

<span data-ttu-id="ccca6-125">대부분의 경우 컨트롤에는 단일 요소에 지정 된 정의가 하나만 있습니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="ccca6-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="ccca6-126">그러나 같은 컨트롤을 사용 하 여 다른 그룹을 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccca6-126">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="ccca6-127">이러한 경우 그룹의 요소를 정의할 수 있습니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="ccca6-127">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccca6-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ccca6-128">See Also</span></span>

[<span data-ttu-id="ccca6-129">View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ccca6-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="ccca6-130">GroupBy에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ccca6-130">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="ccca6-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ccca6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
