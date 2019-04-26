---
title: PropertyName 요소 ListControl (형식)에 대 한 ItemSelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064750"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="ef029-102">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ef029-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="ef029-103">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef029-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ef029-104">이 속성이 있는 경우 또는로 평가 되 면 `true`, 조건이 충족 될 및 뷰가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef029-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="ef029-105">이 요소는 목록 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef029-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="ef029-106">ListItem ListControl (형식)에 대 한 ListEntry ListItems 요소 ListControl (형식)에 구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 요소 (형식) ListControl 요소 (형식) ListEntry 요소 ListEntries 요소 (형식) 요소 ListItems ListItem ListControl (형식)에 대 한 ItemSelectionCondition ListControls PropertyName 요소에 대 한 ListControl (형식) ItemSelectionCondition 요소에 대 한</span><span class="sxs-lookup"><span data-stu-id="ef029-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef029-107">구문</span><span class="sxs-lookup"><span data-stu-id="ef029-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef029-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ef029-108">Attributes and Elements</span></span>

<span data-ttu-id="ef029-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef029-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef029-110">특성</span><span class="sxs-lookup"><span data-stu-id="ef029-110">Attributes</span></span>

<span data-ttu-id="ef029-111">없음</span><span class="sxs-lookup"><span data-stu-id="ef029-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef029-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ef029-112">Child Elements</span></span>

<span data-ttu-id="ef029-113">없음</span><span class="sxs-lookup"><span data-stu-id="ef029-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef029-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ef029-114">Parent Elements</span></span>

|<span data-ttu-id="ef029-115">요소</span><span class="sxs-lookup"><span data-stu-id="ef029-115">Element</span></span>|<span data-ttu-id="ef029-116">설명</span><span class="sxs-lookup"><span data-stu-id="ef029-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef029-117">ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ef029-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="ef029-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ef029-118">Text Value</span></span>

<span data-ttu-id="ef029-119">값은 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef029-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef029-120">설명</span><span class="sxs-lookup"><span data-stu-id="ef029-120">Remarks</span></span>

<span data-ttu-id="ef029-121">이 요소를 사용 하는 경우를 지정할 수 없습니다는 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 요소 선택 조건을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef029-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef029-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef029-122">See Also</span></span>

[<span data-ttu-id="ef029-123">ListIControl (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="ef029-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="ef029-124">ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ef029-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="ef029-125">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="ef029-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
