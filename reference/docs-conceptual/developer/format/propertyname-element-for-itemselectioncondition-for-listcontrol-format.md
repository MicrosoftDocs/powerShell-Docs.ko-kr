---
title: 이 listcontrol (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362392"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="c3b6e-102">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="c3b6e-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="c3b6e-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3b6e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c3b6e-104">이 속성이 있거나 `true`된 것으로 평가 되 면 조건이 충족 되 고 뷰가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3b6e-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="c3b6e-105">이 요소는 목록 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3b6e-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="c3b6e-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol element (format) ListEntries element (format) ListEntry 요소 for이 listcontrol (format) ListItems Element for ListEntry (Format) ListItem ListItems에 대 한 요소 for이 listcontrol (Format) ItemSelectionCondition 요소 (ListControls의 경우 ListItem 요소)의 ItemSelectionCondition for이 listcontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="c3b6e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3b6e-107">구문</span><span class="sxs-lookup"><span data-stu-id="c3b6e-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3b6e-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="c3b6e-108">Attributes and Elements</span></span>

<span data-ttu-id="c3b6e-109">다음 섹션에서는 특성, 자식 요소 및 `PropertyName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3b6e-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3b6e-110">특성</span><span class="sxs-lookup"><span data-stu-id="c3b6e-110">Attributes</span></span>

<span data-ttu-id="c3b6e-111">없음</span><span class="sxs-lookup"><span data-stu-id="c3b6e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3b6e-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="c3b6e-112">Child Elements</span></span>

<span data-ttu-id="c3b6e-113">없음</span><span class="sxs-lookup"><span data-stu-id="c3b6e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3b6e-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="c3b6e-114">Parent Elements</span></span>

|<span data-ttu-id="c3b6e-115">요소</span><span class="sxs-lookup"><span data-stu-id="c3b6e-115">Element</span></span>|<span data-ttu-id="c3b6e-116">설명</span><span class="sxs-lookup"><span data-stu-id="c3b6e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3b6e-117">이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c3b6e-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="c3b6e-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="c3b6e-118">Text Value</span></span>

<span data-ttu-id="c3b6e-119">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3b6e-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3b6e-120">설명</span><span class="sxs-lookup"><span data-stu-id="c3b6e-120">Remarks</span></span>

<span data-ttu-id="c3b6e-121">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3b6e-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3b6e-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3b6e-122">See Also</span></span>

[<span data-ttu-id="c3b6e-123">ListIControl (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="c3b6e-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="c3b6e-124">이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="c3b6e-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c3b6e-125">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="c3b6e-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
