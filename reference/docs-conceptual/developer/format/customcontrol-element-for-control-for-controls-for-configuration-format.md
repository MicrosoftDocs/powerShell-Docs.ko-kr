---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)
description: Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)
ms.openlocfilehash: 631995c6a50c0f020cb2e991cfbf58a09a75cc72
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649995"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="4a1e8-103">Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a1e8-103">CustomControl Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4a1e8-104">컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1e8-104">Defines a control.</span></span> <span data-ttu-id="4a1e8-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a1e8-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4a1e8-106">구성 요소 (format) 컨트롤 요소 구성 (format)의 컨트롤 요소 구성 (format)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="4a1e8-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a1e8-107">구문</span><span class="sxs-lookup"><span data-stu-id="4a1e8-107">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a1e8-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4a1e8-108">Attributes and Elements</span></span>

<span data-ttu-id="4a1e8-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomControl` .</span><span class="sxs-lookup"><span data-stu-id="4a1e8-109">The following sections describe the attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="4a1e8-110">이 요소에는 자식 요소가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1e8-110">This element must have at least one child element.</span></span> <span data-ttu-id="4a1e8-111">지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a1e8-111">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a1e8-112">특성</span><span class="sxs-lookup"><span data-stu-id="4a1e8-112">Attributes</span></span>

<span data-ttu-id="4a1e8-113">없음</span><span class="sxs-lookup"><span data-stu-id="4a1e8-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a1e8-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4a1e8-114">Child Elements</span></span>

|<span data-ttu-id="4a1e8-115">요소</span><span class="sxs-lookup"><span data-stu-id="4a1e8-115">Element</span></span>|<span data-ttu-id="4a1e8-116">설명</span><span class="sxs-lookup"><span data-stu-id="4a1e8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a1e8-117">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a1e8-117">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="4a1e8-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a1e8-118">Required element.</span></span><br /><br /> <span data-ttu-id="4a1e8-119">컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1e8-119">Provides the definitions of a control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4a1e8-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4a1e8-120">Parent Elements</span></span>

|<span data-ttu-id="4a1e8-121">요소</span><span class="sxs-lookup"><span data-stu-id="4a1e8-121">Element</span></span>|<span data-ttu-id="4a1e8-122">설명</span><span class="sxs-lookup"><span data-stu-id="4a1e8-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a1e8-123">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a1e8-123">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="4a1e8-124">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a1e8-124">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4a1e8-125">설명</span><span class="sxs-lookup"><span data-stu-id="4a1e8-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="4a1e8-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a1e8-126">See Also</span></span>

[<span data-ttu-id="4a1e8-127">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a1e8-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a1e8-128">구성에 대 한 CustomControl의 CustomEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a1e8-128">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a1e8-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4a1e8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
