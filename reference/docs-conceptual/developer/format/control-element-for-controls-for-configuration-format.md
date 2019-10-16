---
title: 구성에 대 한 컨트롤 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369012"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="40b92-102">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="40b92-103">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="40b92-104">구성 요소 (Format) 컨트롤의 구성 요소 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="40b92-105">구문</span><span class="sxs-lookup"><span data-stu-id="40b92-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40b92-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="40b92-106">Attributes and Elements</span></span>

<span data-ttu-id="40b92-107">다음 섹션에서는 `Control` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="40b92-108">각 자식 요소 중 하나만 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="40b92-109">특성</span><span class="sxs-lookup"><span data-stu-id="40b92-109">Attributes</span></span>

<span data-ttu-id="40b92-110">없음</span><span class="sxs-lookup"><span data-stu-id="40b92-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="40b92-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="40b92-111">Child Elements</span></span>

|<span data-ttu-id="40b92-112">요소</span><span class="sxs-lookup"><span data-stu-id="40b92-112">Element</span></span>|<span data-ttu-id="40b92-113">설명</span><span class="sxs-lookup"><span data-stu-id="40b92-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40b92-114">구성에 대 한 컨트롤에 대 한 CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="40b92-115">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-115">Required element.</span></span><br /><br /> <span data-ttu-id="40b92-116">컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-116">Defines the control.</span></span>|
|[<span data-ttu-id="40b92-117">구성에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="40b92-118">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-118">Required element.</span></span><br /><br /> <span data-ttu-id="40b92-119">컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="40b92-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="40b92-120">Parent Elements</span></span>

|<span data-ttu-id="40b92-121">요소</span><span class="sxs-lookup"><span data-stu-id="40b92-121">Element</span></span>|<span data-ttu-id="40b92-122">설명</span><span class="sxs-lookup"><span data-stu-id="40b92-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40b92-123">구성의 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="40b92-124">서식 파일의 모든 보기 또는 다른 컨트롤에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="40b92-125">설명</span><span class="sxs-lookup"><span data-stu-id="40b92-125">Remarks</span></span>

<span data-ttu-id="40b92-126">이 컨트롤에 지정 된 이름은 다음 요소에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40b92-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="40b92-127">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="40b92-128">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="40b92-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40b92-129">See Also</span></span>

[<span data-ttu-id="40b92-130">구성의 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="40b92-131">구성 (형식)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="40b92-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="40b92-132">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="40b92-133">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="40b92-134">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="40b92-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="40b92-135">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="40b92-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
