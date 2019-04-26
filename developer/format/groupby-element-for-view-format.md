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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065546"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="8cb5b-102">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="8cb5b-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="8cb5b-103">새 개체 그룹에 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="8cb5b-104">이 요소는 테이블, 목록, 넓게 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="8cb5b-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 보려면 (형식)</span><span class="sxs-lookup"><span data-stu-id="8cb5b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8cb5b-106">구문</span><span class="sxs-lookup"><span data-stu-id="8cb5b-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8cb5b-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-107">Attributes and Elements</span></span>

<span data-ttu-id="8cb5b-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8cb5b-109">특성</span><span class="sxs-lookup"><span data-stu-id="8cb5b-109">Attributes</span></span>

<span data-ttu-id="8cb5b-110">없음</span><span class="sxs-lookup"><span data-stu-id="8cb5b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8cb5b-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-111">Child Elements</span></span>

|<span data-ttu-id="8cb5b-112">요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-112">Element</span></span>|<span data-ttu-id="8cb5b-113">설명</span><span class="sxs-lookup"><span data-stu-id="8cb5b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8cb5b-114">GroupBy (형식)에 대 한 CustomControl 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="8cb5b-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb5b-116">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="8cb5b-117">GroupBy (형식)에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="8cb5b-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb5b-119">새 그룹을 표시 하는 데 사용 되는 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="8cb5b-120">GroupBy (형식)에 대 한 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="8cb5b-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb5b-122">새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="8cb5b-123">GroupBy (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="8cb5b-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb5b-125">시작 하 여.NET 속성을 지정 합니다. 해당 값이 변경 될 때마다 새 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="8cb5b-126">GroupBy (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="8cb5b-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8cb5b-128">해당 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8cb5b-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-129">Parent Elements</span></span>

|<span data-ttu-id="8cb5b-130">요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-130">Element</span></span>|<span data-ttu-id="8cb5b-131">설명</span><span class="sxs-lookup"><span data-stu-id="8cb5b-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8cb5b-132">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8cb5b-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="8cb5b-133">하나 이상의.NET 개체를 표시 하는 보기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8cb5b-134">설명</span><span class="sxs-lookup"><span data-stu-id="8cb5b-134">Remarks</span></span>

<span data-ttu-id="8cb5b-135">새 개체 그룹에 표시 되는 방식을 정의할 때 속성 또는 새 그룹을 시작 하는 스크립트를 지정 해야 합니다. 그러나 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8cb5b-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cb5b-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8cb5b-136">See Also</span></span>

[<span data-ttu-id="8cb5b-137">GroupBy (형식)에 대 한 CustomControlName 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="8cb5b-138">GroupBy (형식)에 대 한 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="8cb5b-139">GroupBy (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="8cb5b-140">GroupBy (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="8cb5b-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="8cb5b-141">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="8cb5b-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="8cb5b-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="8cb5b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
