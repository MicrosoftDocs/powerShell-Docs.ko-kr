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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362392"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="852b0-102">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="852b0-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="852b0-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="852b0-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="852b0-104">이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 뷰가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="852b0-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="852b0-105">이 요소는 목록 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="852b0-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="852b0-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol element (format) ListEntries element (format) ListEntry 요소 for이 listcontrol (format) ListItems Element for ListEntry (Format) ListItem ListItems에 대 한 요소 for이 listcontrol (Format) ItemSelectionCondition 요소 (ListControls의 경우 ListItem 요소)의 ItemSelectionCondition for이 listcontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="852b0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="852b0-107">구문</span><span class="sxs-lookup"><span data-stu-id="852b0-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="852b0-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="852b0-108">Attributes and Elements</span></span>

<span data-ttu-id="852b0-109">다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="852b0-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="852b0-110">특성</span><span class="sxs-lookup"><span data-stu-id="852b0-110">Attributes</span></span>

<span data-ttu-id="852b0-111">없음</span><span class="sxs-lookup"><span data-stu-id="852b0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="852b0-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="852b0-112">Child Elements</span></span>

<span data-ttu-id="852b0-113">없음</span><span class="sxs-lookup"><span data-stu-id="852b0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="852b0-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="852b0-114">Parent Elements</span></span>

|<span data-ttu-id="852b0-115">요소</span><span class="sxs-lookup"><span data-stu-id="852b0-115">Element</span></span>|<span data-ttu-id="852b0-116">설명</span><span class="sxs-lookup"><span data-stu-id="852b0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="852b0-117">이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="852b0-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="852b0-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="852b0-118">Text Value</span></span>

<span data-ttu-id="852b0-119">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="852b0-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="852b0-120">설명</span><span class="sxs-lookup"><span data-stu-id="852b0-120">Remarks</span></span>

<span data-ttu-id="852b0-121">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="852b0-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="852b0-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="852b0-122">See Also</span></span>

[<span data-ttu-id="852b0-123">ListIControl (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="852b0-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="852b0-124">이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="852b0-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="852b0-125">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="852b0-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
