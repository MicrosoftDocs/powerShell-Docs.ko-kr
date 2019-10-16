---
title: 이 listcontrol (형식)의 ListItem에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365192"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="012ee-102">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="012ee-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="012ee-103">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="012ee-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 ListEntries의이 listcontrol (Format) ListItems 요소 for이 listcontrol (format) ListItem 요소의 경우 ListItems에 대 한 ItemSelectionCondition 요소에 대 한이 listcontrol (형식)</span><span class="sxs-lookup"><span data-stu-id="012ee-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="012ee-105">구문</span><span class="sxs-lookup"><span data-stu-id="012ee-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="012ee-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="012ee-106">Attributes and Elements</span></span>

<span data-ttu-id="012ee-107">다음 섹션에서는 `ItemSelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="012ee-108">특성</span><span class="sxs-lookup"><span data-stu-id="012ee-108">Attributes</span></span>

<span data-ttu-id="012ee-109">없음</span><span class="sxs-lookup"><span data-stu-id="012ee-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="012ee-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="012ee-110">Child Elements</span></span>

|<span data-ttu-id="012ee-111">요소</span><span class="sxs-lookup"><span data-stu-id="012ee-111">Element</span></span>|<span data-ttu-id="012ee-112">설명</span><span class="sxs-lookup"><span data-stu-id="012ee-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="012ee-113">이 listcontrol (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="012ee-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="012ee-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-114">Optional element.</span></span><br /><br /> <span data-ttu-id="012ee-115">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="012ee-116">이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="012ee-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="012ee-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-117">Optional element.</span></span><br /><br /> <span data-ttu-id="012ee-118">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="012ee-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="012ee-119">Parent Elements</span></span>

|<span data-ttu-id="012ee-120">요소</span><span class="sxs-lookup"><span data-stu-id="012ee-120">Element</span></span>|<span data-ttu-id="012ee-121">설명</span><span class="sxs-lookup"><span data-stu-id="012ee-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="012ee-122">이 listcontrol에 대 한 ListItems의 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="012ee-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="012ee-123">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="012ee-124">설명</span><span class="sxs-lookup"><span data-stu-id="012ee-124">Remarks</span></span>

<span data-ttu-id="012ee-125">이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="012ee-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="012ee-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="012ee-126">See Also</span></span>

[<span data-ttu-id="012ee-127">이 listcontrol에 대 한 ListItems의 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="012ee-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="012ee-128">이 listcontrol (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="012ee-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="012ee-129">이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="012ee-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="012ee-130">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="012ee-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
