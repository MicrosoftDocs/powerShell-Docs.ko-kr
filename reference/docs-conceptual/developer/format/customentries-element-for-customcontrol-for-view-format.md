---
ms.date: 09/13/2016
ms.topic: reference
title: View의 CustomControl에 대한 CustomEntries 요소(형식)
description: View의 CustomControl에 대한 CustomEntries 요소(형식)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649973"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="c7cb0-103">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c7cb0-103">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="c7cb0-104">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-104">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="c7cb0-105">사용자 지정 컨트롤 뷰에서 하나 이상의 정의를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-105">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="c7cb0-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="c7cb0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7cb0-107">구문</span><span class="sxs-lookup"><span data-stu-id="c7cb0-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7cb0-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c7cb0-108">Attributes and Elements</span></span>

<span data-ttu-id="c7cb0-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlEntries` .</span><span class="sxs-lookup"><span data-stu-id="c7cb0-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="c7cb0-110">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7cb0-111">특성</span><span class="sxs-lookup"><span data-stu-id="c7cb0-111">Attributes</span></span>

<span data-ttu-id="c7cb0-112">없음</span><span class="sxs-lookup"><span data-stu-id="c7cb0-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7cb0-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c7cb0-113">Child Elements</span></span>

|<span data-ttu-id="c7cb0-114">요소</span><span class="sxs-lookup"><span data-stu-id="c7cb0-114">Element</span></span>|<span data-ttu-id="c7cb0-115">설명</span><span class="sxs-lookup"><span data-stu-id="c7cb0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7cb0-116">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c7cb0-116">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="c7cb0-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-117">Required element.</span></span><br /><br /> <span data-ttu-id="c7cb0-118">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-118">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c7cb0-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c7cb0-119">Parent Elements</span></span>

|<span data-ttu-id="c7cb0-120">요소</span><span class="sxs-lookup"><span data-stu-id="c7cb0-120">Element</span></span>|<span data-ttu-id="c7cb0-121">설명</span><span class="sxs-lookup"><span data-stu-id="c7cb0-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7cb0-122">View에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c7cb0-122">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="c7cb0-123">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-123">Required element.</span></span><br /><br /> <span data-ttu-id="c7cb0-124">뷰의 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-124">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c7cb0-125">설명</span><span class="sxs-lookup"><span data-stu-id="c7cb0-125">Remarks</span></span>

<span data-ttu-id="c7cb0-126">대부분의 경우 컨트롤에는 단일 요소에 정의 된 정의가 하나만 있습니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="c7cb0-126">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="c7cb0-127">그러나 같은 컨트롤을 사용 하 여 서로 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-127">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c7cb0-128">이러한 경우 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7cb0-128">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7cb0-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7cb0-129">See Also</span></span>

[<span data-ttu-id="c7cb0-130">View에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c7cb0-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="c7cb0-131">뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c7cb0-131">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c7cb0-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c7cb0-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
