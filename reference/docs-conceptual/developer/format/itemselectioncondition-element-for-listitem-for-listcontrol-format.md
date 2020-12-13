---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)
description: ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667813"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="119eb-103">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="119eb-103">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="119eb-104">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="119eb-104">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="119eb-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한 ListEntries의 경우이 listcontrol에 대 한 ListItems (format) ListItem 요소의 ListEntry for이 listcontrol (format) ItemSelectionCondition 요소 (형식)의 ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="119eb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="119eb-106">구문</span><span class="sxs-lookup"><span data-stu-id="119eb-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="119eb-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="119eb-107">Attributes and Elements</span></span>

<span data-ttu-id="119eb-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="119eb-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="119eb-109">특성</span><span class="sxs-lookup"><span data-stu-id="119eb-109">Attributes</span></span>

<span data-ttu-id="119eb-110">없음</span><span class="sxs-lookup"><span data-stu-id="119eb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="119eb-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="119eb-111">Child Elements</span></span>

|<span data-ttu-id="119eb-112">요소</span><span class="sxs-lookup"><span data-stu-id="119eb-112">Element</span></span>|<span data-ttu-id="119eb-113">설명</span><span class="sxs-lookup"><span data-stu-id="119eb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="119eb-114">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="119eb-114">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="119eb-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="119eb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="119eb-116">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="119eb-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="119eb-117">ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="119eb-117">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="119eb-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="119eb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="119eb-119">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="119eb-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="119eb-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="119eb-120">Parent Elements</span></span>

|<span data-ttu-id="119eb-121">요소</span><span class="sxs-lookup"><span data-stu-id="119eb-121">Element</span></span>|<span data-ttu-id="119eb-122">설명</span><span class="sxs-lookup"><span data-stu-id="119eb-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="119eb-123">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="119eb-123">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="119eb-124">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="119eb-124">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="119eb-125">설명</span><span class="sxs-lookup"><span data-stu-id="119eb-125">Remarks</span></span>

<span data-ttu-id="119eb-126">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="119eb-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="119eb-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="119eb-127">See Also</span></span>

[<span data-ttu-id="119eb-128">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="119eb-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="119eb-129">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="119eb-129">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="119eb-130">ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="119eb-130">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="119eb-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="119eb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
