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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369012"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="aad67-102">Configuration의 Controls에 대한 Control 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="aad67-103">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="aad67-104">구성 요소 (Format) 컨트롤의 구성 요소 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aad67-105">구문</span><span class="sxs-lookup"><span data-stu-id="aad67-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aad67-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="aad67-106">Attributes and Elements</span></span>

<span data-ttu-id="aad67-107">다음 섹션에서는 `Control` 요소에 대 한 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="aad67-108">각 자식 요소 중 하나만 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aad67-109">특성</span><span class="sxs-lookup"><span data-stu-id="aad67-109">Attributes</span></span>

<span data-ttu-id="aad67-110">없음</span><span class="sxs-lookup"><span data-stu-id="aad67-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aad67-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="aad67-111">Child Elements</span></span>

|<span data-ttu-id="aad67-112">요소</span><span class="sxs-lookup"><span data-stu-id="aad67-112">Element</span></span>|<span data-ttu-id="aad67-113">설명</span><span class="sxs-lookup"><span data-stu-id="aad67-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aad67-114">구성에 대 한 컨트롤에 대 한 CustomControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="aad67-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-115">Required element.</span></span><br /><br /> <span data-ttu-id="aad67-116">컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-116">Defines the control.</span></span>|
|[<span data-ttu-id="aad67-117">구성에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="aad67-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-118">Required element.</span></span><br /><br /> <span data-ttu-id="aad67-119">컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aad67-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="aad67-120">Parent Elements</span></span>

|<span data-ttu-id="aad67-121">요소</span><span class="sxs-lookup"><span data-stu-id="aad67-121">Element</span></span>|<span data-ttu-id="aad67-122">설명</span><span class="sxs-lookup"><span data-stu-id="aad67-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aad67-123">구성의 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="aad67-124">서식 파일의 모든 보기 또는 다른 컨트롤에서 사용할 수 있는 공용 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aad67-125">설명</span><span class="sxs-lookup"><span data-stu-id="aad67-125">Remarks</span></span>

<span data-ttu-id="aad67-126">이 컨트롤에 지정 된 이름은 다음 요소에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad67-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="aad67-127">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="aad67-128">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="aad67-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aad67-129">See Also</span></span>

[<span data-ttu-id="aad67-130">구성의 컨트롤 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="aad67-131">구성 (형식)의 컨트롤에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="aad67-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="aad67-132">CustomItem에 대 한 ExpressionBinding 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="aad67-133">보기에 대 한 GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="aad67-134">구성 컨트롤에 대 한 컨트롤의 Name 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="aad67-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="aad67-135">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="aad67-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
