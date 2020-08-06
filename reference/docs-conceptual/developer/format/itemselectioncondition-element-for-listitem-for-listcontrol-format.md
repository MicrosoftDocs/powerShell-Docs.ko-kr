---
title: 이 listcontrol (형식)의 ListItem에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f5c388928668e03b96923130fb5849f637548f12
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783622"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="d9c6d-102">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9c6d-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="d9c6d-103">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c6d-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="d9c6d-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한 ListEntries의 경우이 listcontrol에 대 한 ListItems (format) ListItem 요소의 ListEntry for이 listcontrol (format) ItemSelectionCondition 요소 (형식)의 ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="d9c6d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9c6d-105">구문</span><span class="sxs-lookup"><span data-stu-id="d9c6d-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9c6d-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d9c6d-106">Attributes and Elements</span></span>

<span data-ttu-id="d9c6d-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="d9c6d-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9c6d-108">특성</span><span class="sxs-lookup"><span data-stu-id="d9c6d-108">Attributes</span></span>

<span data-ttu-id="d9c6d-109">없음</span><span class="sxs-lookup"><span data-stu-id="d9c6d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9c6d-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d9c6d-110">Child Elements</span></span>

|<span data-ttu-id="d9c6d-111">요소</span><span class="sxs-lookup"><span data-stu-id="d9c6d-111">Element</span></span>|<span data-ttu-id="d9c6d-112">설명</span><span class="sxs-lookup"><span data-stu-id="d9c6d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9c6d-113">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9c6d-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="d9c6d-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d9c6d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d9c6d-115">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c6d-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d9c6d-116">ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9c6d-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="d9c6d-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d9c6d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d9c6d-118">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c6d-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d9c6d-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d9c6d-119">Parent Elements</span></span>

|<span data-ttu-id="d9c6d-120">요소</span><span class="sxs-lookup"><span data-stu-id="d9c6d-120">Element</span></span>|<span data-ttu-id="d9c6d-121">설명</span><span class="sxs-lookup"><span data-stu-id="d9c6d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9c6d-122">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9c6d-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="d9c6d-123">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9c6d-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9c6d-124">설명</span><span class="sxs-lookup"><span data-stu-id="d9c6d-124">Remarks</span></span>

<span data-ttu-id="d9c6d-125">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9c6d-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9c6d-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9c6d-126">See Also</span></span>

[<span data-ttu-id="d9c6d-127">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9c6d-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="d9c6d-128">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9c6d-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="d9c6d-129">ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d9c6d-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="d9c6d-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d9c6d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
