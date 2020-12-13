---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration 요소(형식)
description: Configuration 요소(형식)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655683"
---
# <a name="configuration-element-format"></a><span data-ttu-id="d815a-103">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-103">Configuration Element (Format)</span></span>

<span data-ttu-id="d815a-104">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-104">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="d815a-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d815a-105">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="d815a-106">구문</span><span class="sxs-lookup"><span data-stu-id="d815a-106">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d815a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d815a-107">Attributes and Elements</span></span>

<span data-ttu-id="d815a-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="d815a-108">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="d815a-109">이 요소는 각 서식 파일에 대 한 루트 요소 여야 하 고이 요소에는 자식 요소가 하나 이상 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-109">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d815a-110">특성</span><span class="sxs-lookup"><span data-stu-id="d815a-110">Attributes</span></span>

<span data-ttu-id="d815a-111">없음</span><span class="sxs-lookup"><span data-stu-id="d815a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d815a-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d815a-112">Child Elements</span></span>

|<span data-ttu-id="d815a-113">요소</span><span class="sxs-lookup"><span data-stu-id="d815a-113">Element</span></span>|<span data-ttu-id="d815a-114">설명</span><span class="sxs-lookup"><span data-stu-id="d815a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d815a-115">Configuration에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-115">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="d815a-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d815a-117">서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-117">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="d815a-118">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-118">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="d815a-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d815a-120">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-120">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="d815a-121">SelectionSets 형식 설정</span><span class="sxs-lookup"><span data-stu-id="d815a-121">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="d815a-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d815a-123">서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-123">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="d815a-124">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-124">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="d815a-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="d815a-126">개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-126">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d815a-127">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d815a-127">Parent Elements</span></span>

<span data-ttu-id="d815a-128">없음</span><span class="sxs-lookup"><span data-stu-id="d815a-128">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="d815a-129">설명</span><span class="sxs-lookup"><span data-stu-id="d815a-129">Remarks</span></span>

<span data-ttu-id="d815a-130">서식 파일은 개체가 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-130">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="d815a-131">대부분의 경우이 루트 요소는 서식 파일의 테이블, 목록 및 넓은 뷰를 정의 하는 [Viewdefinitions](./viewdefinitions-element-format.md) 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-131">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="d815a-132">뷰 정의 외에도 서식 파일은 해당 뷰에서 사용할 수 있는 일반 선택 집합, 설정 및 컨트롤을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d815a-132">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="d815a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d815a-133">See Also</span></span>

[<span data-ttu-id="d815a-134">Configuration에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-134">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="d815a-135">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-135">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="d815a-136">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="d815a-137">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d815a-137">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="d815a-138">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d815a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
