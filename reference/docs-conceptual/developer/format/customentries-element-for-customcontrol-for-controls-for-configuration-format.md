---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)
description: Configuration에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655391"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="a5912-103">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a5912-103">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a5912-104">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5912-104">Provides the definitions of a common control.</span></span> <span data-ttu-id="a5912-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5912-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a5912-106">구성 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤 요소 구성 (형식)의 CustomControl에 대 한 CustomEntries 요소</span><span class="sxs-lookup"><span data-stu-id="a5912-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5912-107">구문</span><span class="sxs-lookup"><span data-stu-id="a5912-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5912-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a5912-108">Attributes and Elements</span></span>

<span data-ttu-id="a5912-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomEntries` .</span><span class="sxs-lookup"><span data-stu-id="a5912-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="a5912-110">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5912-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5912-111">특성</span><span class="sxs-lookup"><span data-stu-id="a5912-111">Attributes</span></span>

<span data-ttu-id="a5912-112">없음</span><span class="sxs-lookup"><span data-stu-id="a5912-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5912-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a5912-113">Child Elements</span></span>

|<span data-ttu-id="a5912-114">요소</span><span class="sxs-lookup"><span data-stu-id="a5912-114">Element</span></span>|<span data-ttu-id="a5912-115">설명</span><span class="sxs-lookup"><span data-stu-id="a5912-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5912-116">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a5912-116">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="a5912-117">공용 컨트롤의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5912-117">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a5912-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a5912-118">Parent Elements</span></span>

|<span data-ttu-id="a5912-119">요소</span><span class="sxs-lookup"><span data-stu-id="a5912-119">Element</span></span>|<span data-ttu-id="a5912-120">설명</span><span class="sxs-lookup"><span data-stu-id="a5912-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5912-121">구성 (형식)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="a5912-121">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="a5912-122">공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5912-122">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5912-123">설명</span><span class="sxs-lookup"><span data-stu-id="a5912-123">Remarks</span></span>

<span data-ttu-id="a5912-124">대부분의 경우 컨트롤에는 단일 요소에 정의 된 정의가 하나만 있습니다 `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="a5912-124">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="a5912-125">그러나 같은 컨트롤을 사용 하 여 서로 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5912-125">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="a5912-126">이러한 경우 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5912-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5912-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5912-127">See Also</span></span>

[<span data-ttu-id="a5912-128">구성 (형식)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="a5912-128">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a5912-129">Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a5912-129">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="a5912-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a5912-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
