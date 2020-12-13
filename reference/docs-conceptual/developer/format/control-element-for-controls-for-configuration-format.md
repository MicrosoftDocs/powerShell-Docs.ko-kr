---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration의 Controls에 대한 Control 요소(형식)
description: Configuration의 Controls에 대한 Control 요소(형식)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655657"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="9731b-103">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-103">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9731b-104">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-104">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="9731b-105">구성 요소 (Format) 컨트롤의 구성 요소 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9731b-106">구문</span><span class="sxs-lookup"><span data-stu-id="9731b-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9731b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9731b-107">Attributes and Elements</span></span>

<span data-ttu-id="9731b-108">다음 섹션에서는 요소에 대 한 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Control` .</span><span class="sxs-lookup"><span data-stu-id="9731b-108">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="9731b-109">각 자식 요소 중 하나만 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-109">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9731b-110">특성</span><span class="sxs-lookup"><span data-stu-id="9731b-110">Attributes</span></span>

<span data-ttu-id="9731b-111">없음</span><span class="sxs-lookup"><span data-stu-id="9731b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9731b-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9731b-112">Child Elements</span></span>

|<span data-ttu-id="9731b-113">요소</span><span class="sxs-lookup"><span data-stu-id="9731b-113">Element</span></span>|<span data-ttu-id="9731b-114">설명</span><span class="sxs-lookup"><span data-stu-id="9731b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9731b-115">Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-115">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="9731b-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-116">Required element.</span></span><br /><br /> <span data-ttu-id="9731b-117">컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-117">Defines the control.</span></span>|
|[<span data-ttu-id="9731b-118">구성에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-118">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="9731b-119">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-119">Required element.</span></span><br /><br /> <span data-ttu-id="9731b-120">컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-120">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9731b-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9731b-121">Parent Elements</span></span>

|<span data-ttu-id="9731b-122">요소</span><span class="sxs-lookup"><span data-stu-id="9731b-122">Element</span></span>|<span data-ttu-id="9731b-123">설명</span><span class="sxs-lookup"><span data-stu-id="9731b-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9731b-124">구성의 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-124">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="9731b-125">서식 파일의 모든 보기 또는 다른 컨트롤에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-125">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9731b-126">설명</span><span class="sxs-lookup"><span data-stu-id="9731b-126">Remarks</span></span>

<span data-ttu-id="9731b-127">이 컨트롤에 지정 된 이름은 다음 요소에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9731b-127">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="9731b-128">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="9731b-129">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-129">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="9731b-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9731b-130">See Also</span></span>

[<span data-ttu-id="9731b-131">구성의 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-131">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="9731b-132">구성 (형식)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="9731b-132">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="9731b-133">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-133">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="9731b-134">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-134">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9731b-135">Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9731b-135">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="9731b-136">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9731b-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
