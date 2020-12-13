---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
description: ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: 1e518f898e0e1e62ca64f9897b1323cc6dd89ae9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665065"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="fb002-103">ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fb002-103">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="fb002-104">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb002-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fb002-105">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb002-105">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="fb002-106">이 요소는 목록 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb002-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="fb002-107">Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format)이 listcontrol Element (format) ListEntries Element for ListEntries (format) ListEntry element for이 listcontrol (format) element for ListItems (format) element for ListEntry (format)의 ListItem 요소에 대 한이 listcontrol (형식)에 대 한 ItemSelectionCondition 요소에 대 한 ListItems (형식)</span><span class="sxs-lookup"><span data-stu-id="fb002-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb002-108">구문</span><span class="sxs-lookup"><span data-stu-id="fb002-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb002-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="fb002-109">Attributes and Elements</span></span>

<span data-ttu-id="fb002-110">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="fb002-110">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb002-111">특성</span><span class="sxs-lookup"><span data-stu-id="fb002-111">Attributes</span></span>

<span data-ttu-id="fb002-112">없음</span><span class="sxs-lookup"><span data-stu-id="fb002-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb002-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="fb002-113">Child Elements</span></span>

<span data-ttu-id="fb002-114">없음</span><span class="sxs-lookup"><span data-stu-id="fb002-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb002-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="fb002-115">Parent Elements</span></span>

|<span data-ttu-id="fb002-116">요소</span><span class="sxs-lookup"><span data-stu-id="fb002-116">Element</span></span>|<span data-ttu-id="fb002-117">설명</span><span class="sxs-lookup"><span data-stu-id="fb002-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb002-118">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="fb002-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="fb002-119">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb002-119">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fb002-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="fb002-120">Text Value</span></span>

<span data-ttu-id="fb002-121">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb002-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb002-122">설명</span><span class="sxs-lookup"><span data-stu-id="fb002-122">Remarks</span></span>

<span data-ttu-id="fb002-123">이 요소를 사용 하는 경우 `PropertyName` 선택 조건을 정의할 때 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb002-123">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb002-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb002-124">See Also</span></span>

[<span data-ttu-id="fb002-125">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="fb002-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
