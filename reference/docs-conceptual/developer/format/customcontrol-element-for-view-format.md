---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl 요소(형식)
description: View에 대한 CustomControl 요소(형식)
ms.openlocfilehash: 41352be55f0c03b2eaca0dbe2d7345e7cf804a7c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655473"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="d0cb9-103">View에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d0cb9-103">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="d0cb9-104">뷰의 사용자 지정 컨트롤 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0cb9-104">Defines a custom control format for the view.</span></span>

<span data-ttu-id="d0cb9-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="d0cb9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0cb9-106">구문</span><span class="sxs-lookup"><span data-stu-id="d0cb9-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0cb9-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d0cb9-107">Attributes and Elements</span></span>

<span data-ttu-id="d0cb9-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControl` .</span><span class="sxs-lookup"><span data-stu-id="d0cb9-108">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="d0cb9-109">하나의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0cb9-109">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0cb9-110">특성</span><span class="sxs-lookup"><span data-stu-id="d0cb9-110">Attributes</span></span>

<span data-ttu-id="d0cb9-111">없음</span><span class="sxs-lookup"><span data-stu-id="d0cb9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0cb9-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d0cb9-112">Child Elements</span></span>

|<span data-ttu-id="d0cb9-113">요소</span><span class="sxs-lookup"><span data-stu-id="d0cb9-113">Element</span></span>|<span data-ttu-id="d0cb9-114">설명</span><span class="sxs-lookup"><span data-stu-id="d0cb9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0cb9-115">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d0cb9-115">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="d0cb9-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d0cb9-116">Required element.</span></span><br /><br /> <span data-ttu-id="d0cb9-117">사용자 지정 컨트롤 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0cb9-117">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0cb9-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d0cb9-118">Parent Elements</span></span>

|<span data-ttu-id="d0cb9-119">요소</span><span class="sxs-lookup"><span data-stu-id="d0cb9-119">Element</span></span>|<span data-ttu-id="d0cb9-120">설명</span><span class="sxs-lookup"><span data-stu-id="d0cb9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0cb9-121">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d0cb9-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d0cb9-122">하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0cb9-122">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0cb9-123">설명</span><span class="sxs-lookup"><span data-stu-id="d0cb9-123">Remarks</span></span>

<span data-ttu-id="d0cb9-124">대부분의 경우 각 컨트롤 뷰에 대해 정의가 하나만 필요 하지만 동일한 뷰를 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0cb9-124">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="d0cb9-125">이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0cb9-125">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0cb9-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0cb9-126">See Also</span></span>

[<span data-ttu-id="d0cb9-127">View의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d0cb9-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d0cb9-128">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d0cb9-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d0cb9-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d0cb9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
