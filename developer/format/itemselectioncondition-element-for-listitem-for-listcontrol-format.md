---
title: ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861869"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="4dacc-102">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4dacc-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="4dacc-103">이 목록 항목을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="4dacc-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntries ListEntry ListItems 요소 ListControl (형식)에 대 한 (형식) ListControl ListEntry 요소에 ListItems ListControl (형식)에 대 한 ListItem ItemSelectionCondition 요소 ListControl (형식)에 대 한 (형식) ListControl ListItem 요소에</span><span class="sxs-lookup"><span data-stu-id="4dacc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4dacc-105">구문</span><span class="sxs-lookup"><span data-stu-id="4dacc-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4dacc-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-106">Attributes and Elements</span></span>

<span data-ttu-id="4dacc-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ItemSelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4dacc-108">특성</span><span class="sxs-lookup"><span data-stu-id="4dacc-108">Attributes</span></span>

<span data-ttu-id="4dacc-109">없음</span><span class="sxs-lookup"><span data-stu-id="4dacc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4dacc-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-110">Child Elements</span></span>

|<span data-ttu-id="4dacc-111">요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-111">Element</span></span>|<span data-ttu-id="4dacc-112">설명</span><span class="sxs-lookup"><span data-stu-id="4dacc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4dacc-113">PropertyName ItemSelectionCondition ListControl (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="4dacc-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="4dacc-115">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4dacc-116">ListControl (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="4dacc-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4dacc-118">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4dacc-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-119">Parent Elements</span></span>

|<span data-ttu-id="4dacc-120">요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-120">Element</span></span>|<span data-ttu-id="4dacc-121">설명</span><span class="sxs-lookup"><span data-stu-id="4dacc-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4dacc-122">ListItem 요소 ListItems ListControl (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="4dacc-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="4dacc-123">속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4dacc-124">설명</span><span class="sxs-lookup"><span data-stu-id="4dacc-124">Remarks</span></span>

<span data-ttu-id="4dacc-125">하면 하나의 속성 이름 또는이 조건에 대 한 스크립트를 지정할 수 있지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4dacc-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dacc-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4dacc-126">See Also</span></span>

[<span data-ttu-id="4dacc-127">ListItem 요소 ListItems ListControl (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="4dacc-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="4dacc-128">PropertyName ItemSelectionCondition ListControl (형식)에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="4dacc-129">ListControl (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="4dacc-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="4dacc-130">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="4dacc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
