---
title: 뷰 (형식)에 대 한 GroupBy 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2f9071a3ebbc7cc2ccb7721dd518e82723e9cc4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781429"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="db6f0-102">View에 대한 GroupBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="db6f0-103">새 개체 그룹을 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="db6f0-104">이 요소는 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="db6f0-105">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) GroupBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db6f0-106">구문</span><span class="sxs-lookup"><span data-stu-id="db6f0-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db6f0-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="db6f0-107">Attributes and Elements</span></span>

<span data-ttu-id="db6f0-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="db6f0-109">특성</span><span class="sxs-lookup"><span data-stu-id="db6f0-109">Attributes</span></span>

<span data-ttu-id="db6f0-110">없음</span><span class="sxs-lookup"><span data-stu-id="db6f0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db6f0-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="db6f0-111">Child Elements</span></span>

|<span data-ttu-id="db6f0-112">요소</span><span class="sxs-lookup"><span data-stu-id="db6f0-112">Element</span></span>|<span data-ttu-id="db6f0-113">설명</span><span class="sxs-lookup"><span data-stu-id="db6f0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db6f0-114">GroupBy에 대한 CustomControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="db6f0-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="db6f0-116">새 그룹을 표시 하는 사용자 지정 컨트롤을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="db6f0-117">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="db6f0-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="db6f0-119">새 그룹을 표시 하는 데 사용 되는 컨트롤의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="db6f0-120">GroupBy에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="db6f0-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="db6f0-122">새 그룹이 발견 될 때 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="db6f0-123">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="db6f0-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-124">Optional element.</span></span><br /><br /> <span data-ttu-id="db6f0-125">에서 값이 변경 될 때마다 새 그룹을 시작 하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="db6f0-126">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="db6f0-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-127">Optional element.</span></span><br /><br /> <span data-ttu-id="db6f0-128">값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db6f0-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="db6f0-129">Parent Elements</span></span>

|<span data-ttu-id="db6f0-130">요소</span><span class="sxs-lookup"><span data-stu-id="db6f0-130">Element</span></span>|<span data-ttu-id="db6f0-131">설명</span><span class="sxs-lookup"><span data-stu-id="db6f0-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db6f0-132">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="db6f0-133">하나 이상의 .NET 개체를 표시 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db6f0-134">설명</span><span class="sxs-lookup"><span data-stu-id="db6f0-134">Remarks</span></span>

<span data-ttu-id="db6f0-135">새 개체 그룹을 표시 하는 방법을 정의할 때 새 그룹을 시작 하는 속성 또는 스크립트를 지정 해야 합니다. 그러나 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db6f0-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="db6f0-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db6f0-136">See Also</span></span>

[<span data-ttu-id="db6f0-137">GroupBy에 대한 CustomControlName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="db6f0-138">GroupBy에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="db6f0-139">GroupBy에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="db6f0-140">GroupBy에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="db6f0-141">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="db6f0-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="db6f0-142">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="db6f0-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
