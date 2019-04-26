---
title: 구성 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066824"
---
# <a name="configuration-element-format"></a><span data-ttu-id="39055-102">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="39055-102">Configuration Element (Format)</span></span>

<span data-ttu-id="39055-103">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="39055-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="39055-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="39055-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="39055-105">구문</span><span class="sxs-lookup"><span data-stu-id="39055-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="39055-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="39055-106">Attributes and Elements</span></span>

<span data-ttu-id="39055-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Configuration` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="39055-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="39055-108">이 요소에 각 서식 파일에 대 한 루트 요소가 있어야 합니다. 하 고이 요소는 자식 요소를 하나 이상 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39055-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="39055-109">특성</span><span class="sxs-lookup"><span data-stu-id="39055-109">Attributes</span></span>

<span data-ttu-id="39055-110">없음</span><span class="sxs-lookup"><span data-stu-id="39055-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="39055-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="39055-111">Child Elements</span></span>

|<span data-ttu-id="39055-112">요소</span><span class="sxs-lookup"><span data-stu-id="39055-112">Element</span></span>|<span data-ttu-id="39055-113">설명</span><span class="sxs-lookup"><span data-stu-id="39055-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="39055-114">구성 (형식)에 대 한 controls 요소</span><span class="sxs-lookup"><span data-stu-id="39055-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="39055-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="39055-115">Optional element.</span></span><br /><br /> <span data-ttu-id="39055-116">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39055-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="39055-117">DefaultSettings 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="39055-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="39055-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="39055-118">Optional element.</span></span><br /><br /> <span data-ttu-id="39055-119">서식 파일의 모든 뷰에 적용 되는 일반적인 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39055-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="39055-120">SelectionSets 요소 형식</span><span class="sxs-lookup"><span data-stu-id="39055-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="39055-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="39055-121">Optional element.</span></span><br /><br /> <span data-ttu-id="39055-122">서식 파일의 모든 보기에서 사용할 수 있는.NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39055-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="39055-123">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="39055-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="39055-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="39055-124">Optional element.</span></span><br /><br /> <span data-ttu-id="39055-125">개체를 표시 하는 데 사용 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39055-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="39055-126">부모 요소</span><span class="sxs-lookup"><span data-stu-id="39055-126">Parent Elements</span></span>

<span data-ttu-id="39055-127">없음</span><span class="sxs-lookup"><span data-stu-id="39055-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="39055-128">설명</span><span class="sxs-lookup"><span data-stu-id="39055-128">Remarks</span></span>

<span data-ttu-id="39055-129">서식 파일 개체 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="39055-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="39055-130">대부분의 경우가 루트 요소에 포함 된 [ViewDefinitions](./viewdefinitions-element-format.md) 테이블, 목록 및 서식 파일의 넓은 뷰를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="39055-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="39055-131">뷰 정의 하는 것 외에도 일반적인 선택 집합, 설정 및 이러한 뷰를 사용할 수 있는 컨트롤 서식 파일을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39055-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="39055-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39055-132">See Also</span></span>

[<span data-ttu-id="39055-133">구성 (형식)에 대 한 controls 요소</span><span class="sxs-lookup"><span data-stu-id="39055-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="39055-134">DefaultSettings 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="39055-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="39055-135">SelectionSets 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="39055-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="39055-136">ViewDefinitions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="39055-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="39055-137">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="39055-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
