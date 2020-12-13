---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls 요소(형식)
description: Configuration에 대한 Controls 요소(형식)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668102"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="2cc0c-103">Configuration에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cc0c-103">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="2cc0c-104">서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cc0c-104">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="2cc0c-105">구성 요소 (형식) 컨트롤 구성 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="2cc0c-105">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2cc0c-106">구문</span><span class="sxs-lookup"><span data-stu-id="2cc0c-106">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2cc0c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2cc0c-107">Attributes and Elements</span></span>

<span data-ttu-id="2cc0c-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Controls` .</span><span class="sxs-lookup"><span data-stu-id="2cc0c-108">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2cc0c-109">특성</span><span class="sxs-lookup"><span data-stu-id="2cc0c-109">Attributes</span></span>

<span data-ttu-id="2cc0c-110">없음</span><span class="sxs-lookup"><span data-stu-id="2cc0c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2cc0c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2cc0c-111">Child Elements</span></span>

|<span data-ttu-id="2cc0c-112">요소</span><span class="sxs-lookup"><span data-stu-id="2cc0c-112">Element</span></span>|<span data-ttu-id="2cc0c-113">설명</span><span class="sxs-lookup"><span data-stu-id="2cc0c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2cc0c-114">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cc0c-114">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="2cc0c-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="2cc0c-115">Required element.</span></span><br /><br /> <span data-ttu-id="2cc0c-116">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cc0c-116">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2cc0c-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2cc0c-117">Parent Elements</span></span>

|<span data-ttu-id="2cc0c-118">요소</span><span class="sxs-lookup"><span data-stu-id="2cc0c-118">Element</span></span>|<span data-ttu-id="2cc0c-119">설명</span><span class="sxs-lookup"><span data-stu-id="2cc0c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2cc0c-120">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cc0c-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="2cc0c-121">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2cc0c-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2cc0c-122">설명</span><span class="sxs-lookup"><span data-stu-id="2cc0c-122">Remarks</span></span>

<span data-ttu-id="2cc0c-123">원하는 수의 공용 컨트롤을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cc0c-123">You can create any number of common controls.</span></span> <span data-ttu-id="2cc0c-124">각 컨트롤에 대해 컨트롤을 참조 하는 데 사용 되는 이름과 컨트롤의 구성 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cc0c-124">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cc0c-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2cc0c-125">See Also</span></span>

[<span data-ttu-id="2cc0c-126">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cc0c-126">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="2cc0c-127">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cc0c-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="2cc0c-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2cc0c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
