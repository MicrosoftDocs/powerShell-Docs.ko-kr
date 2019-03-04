---
title: GroupBy 요소 보려면 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859529"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="9f06d-102">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9f06d-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="9f06d-103">새 개체 그룹에 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="9f06d-104">이 요소는 테이블, 목록, 넓게 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="9f06d-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 보려면 (형식)</span><span class="sxs-lookup"><span data-stu-id="9f06d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f06d-106">구문</span><span class="sxs-lookup"><span data-stu-id="9f06d-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f06d-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-107">Attributes and Elements</span></span>

<span data-ttu-id="9f06d-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f06d-109">특성</span><span class="sxs-lookup"><span data-stu-id="9f06d-109">Attributes</span></span>

<span data-ttu-id="9f06d-110">없음</span><span class="sxs-lookup"><span data-stu-id="9f06d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f06d-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-111">Child Elements</span></span>

|<span data-ttu-id="9f06d-112">요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-112">Element</span></span>|<span data-ttu-id="9f06d-113">설명</span><span class="sxs-lookup"><span data-stu-id="9f06d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f06d-114">GroupBy (형식)에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="9f06d-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9f06d-116">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="9f06d-117">GroupBy (형식)에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="9f06d-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9f06d-119">새 그룹을 표시 하는 데 사용 되는 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="9f06d-120">GroupBy (형식)에 대 한 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="9f06d-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9f06d-122">새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="9f06d-123">GroupBy (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="9f06d-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9f06d-125">시작 하 여.NET 속성을 지정 합니다. 해당 값이 변경 될 때마다 새 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="9f06d-126">GroupBy (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="9f06d-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-127">Optional element.</span></span><br /><br /> <span data-ttu-id="9f06d-128">해당 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9f06d-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-129">Parent Elements</span></span>

|<span data-ttu-id="9f06d-130">요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-130">Element</span></span>|<span data-ttu-id="9f06d-131">설명</span><span class="sxs-lookup"><span data-stu-id="9f06d-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f06d-132">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9f06d-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="9f06d-133">하나 이상의.NET 개체를 표시 하는 보기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f06d-134">설명</span><span class="sxs-lookup"><span data-stu-id="9f06d-134">Remarks</span></span>

<span data-ttu-id="9f06d-135">새 개체 그룹에 표시 되는 방식을 정의할 때 속성 또는 새 그룹을 시작 하는 스크립트를 지정 해야 합니다. 그러나 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f06d-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f06d-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f06d-136">See Also</span></span>

[<span data-ttu-id="9f06d-137">GroupBy (형식)에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="9f06d-138">GroupBy (형식)에 대 한 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="9f06d-139">GroupBy (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="9f06d-140">GroupBy (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="9f06d-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="9f06d-141">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9f06d-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="9f06d-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="9f06d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
