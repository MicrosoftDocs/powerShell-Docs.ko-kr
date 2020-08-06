---
title: Configuration 요소 (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 90be02f8e27c0bd391e01da1a08ecd8eeb29b84c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783843"
---
# <a name="configuration-element-format"></a><span data-ttu-id="f9a30-102">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-102">Configuration Element (Format)</span></span>

<span data-ttu-id="f9a30-103">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="f9a30-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f9a30-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="f9a30-105">구문</span><span class="sxs-lookup"><span data-stu-id="f9a30-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9a30-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f9a30-106">Attributes and Elements</span></span>

<span data-ttu-id="f9a30-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="f9a30-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="f9a30-108">이 요소는 각 서식 파일에 대 한 루트 요소 여야 하 고이 요소에는 자식 요소가 하나 이상 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9a30-109">특성</span><span class="sxs-lookup"><span data-stu-id="f9a30-109">Attributes</span></span>

<span data-ttu-id="f9a30-110">없음</span><span class="sxs-lookup"><span data-stu-id="f9a30-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9a30-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f9a30-111">Child Elements</span></span>

|<span data-ttu-id="f9a30-112">요소</span><span class="sxs-lookup"><span data-stu-id="f9a30-112">Element</span></span>|<span data-ttu-id="f9a30-113">설명</span><span class="sxs-lookup"><span data-stu-id="f9a30-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9a30-114">Configuration에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="f9a30-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a30-116">서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="f9a30-117">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="f9a30-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a30-119">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="f9a30-120">SelectionSets 형식 설정</span><span class="sxs-lookup"><span data-stu-id="f9a30-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="f9a30-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a30-122">서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="f9a30-123">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="f9a30-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f9a30-125">개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f9a30-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f9a30-126">Parent Elements</span></span>

<span data-ttu-id="f9a30-127">없음</span><span class="sxs-lookup"><span data-stu-id="f9a30-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9a30-128">설명</span><span class="sxs-lookup"><span data-stu-id="f9a30-128">Remarks</span></span>

<span data-ttu-id="f9a30-129">서식 파일은 개체가 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="f9a30-130">대부분의 경우이 루트 요소는 서식 파일의 테이블, 목록 및 넓은 뷰를 정의 하는 [Viewdefinitions](./viewdefinitions-element-format.md) 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="f9a30-131">뷰 정의 외에도 서식 파일은 해당 뷰에서 사용할 수 있는 일반 선택 집합, 설정 및 컨트롤을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9a30-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9a30-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9a30-132">See Also</span></span>

[<span data-ttu-id="f9a30-133">Configuration에 대한 Controls 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="f9a30-134">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="f9a30-135">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="f9a30-136">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f9a30-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="f9a30-137">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f9a30-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
