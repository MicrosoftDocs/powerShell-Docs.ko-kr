---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 GroupBy 요소(형식)
description: View에 대한 GroupBy 요소(형식)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652098"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="4a432-103">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-103">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="4a432-104">새 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-104">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="4a432-105">이 요소는 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-105">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="4a432-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a432-107">구문</span><span class="sxs-lookup"><span data-stu-id="4a432-107">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a432-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4a432-108">Attributes and Elements</span></span>

<span data-ttu-id="4a432-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a432-110">특성</span><span class="sxs-lookup"><span data-stu-id="4a432-110">Attributes</span></span>

<span data-ttu-id="4a432-111">없음</span><span class="sxs-lookup"><span data-stu-id="4a432-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a432-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4a432-112">Child Elements</span></span>

|<span data-ttu-id="4a432-113">요소</span><span class="sxs-lookup"><span data-stu-id="4a432-113">Element</span></span>|<span data-ttu-id="4a432-114">설명</span><span class="sxs-lookup"><span data-stu-id="4a432-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a432-115">GroupBy에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-115">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="4a432-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4a432-117">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-117">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="4a432-118">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-118">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="4a432-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4a432-120">새 그룹을 표시 하는 데 사용 되는 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-120">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="4a432-121">GroupBy에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-121">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="4a432-122">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-122">Optional element.</span></span><br /><br /> <span data-ttu-id="4a432-123">새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-123">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="4a432-124">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-124">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="4a432-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-125">Optional element.</span></span><br /><br /> <span data-ttu-id="4a432-126">에서 값이 변경 될 때마다 새 그룹을 시작 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-126">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="4a432-127">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="4a432-128">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-128">Optional element.</span></span><br /><br /> <span data-ttu-id="4a432-129">값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-129">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4a432-130">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4a432-130">Parent Elements</span></span>

|<span data-ttu-id="4a432-131">요소</span><span class="sxs-lookup"><span data-stu-id="4a432-131">Element</span></span>|<span data-ttu-id="4a432-132">설명</span><span class="sxs-lookup"><span data-stu-id="4a432-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a432-133">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-133">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4a432-134">하나 이상의 .NET 개체를 표시 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-134">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4a432-135">설명</span><span class="sxs-lookup"><span data-stu-id="4a432-135">Remarks</span></span>

<span data-ttu-id="4a432-136">새 개체 그룹을 표시 하는 방법을 정의할 때 새 그룹을 시작 하는 속성 또는 스크립트를 지정 해야 합니다. 그러나 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a432-136">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a432-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a432-137">See Also</span></span>

[<span data-ttu-id="4a432-138">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-138">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="4a432-139">GroupBy에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-139">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="4a432-140">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-140">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="4a432-141">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-141">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="4a432-142">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4a432-142">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="4a432-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4a432-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
