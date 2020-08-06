---
title: 이 listcontrol (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780868"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="6b278-102">ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6b278-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="6b278-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b278-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="6b278-104">이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 뷰가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b278-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="6b278-105">이 요소는 목록 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b278-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="6b278-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol element (format) ListEntries element (format) ListItems 요소의 ListEntry에 대 한이 listcontrol (format) ListItem 요소의 ListItems에 대 한이 listcontrol 요소의 ItemSelectionCondition 요소에 대 한 ItemSelectionCondition의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="6b278-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b278-107">구문</span><span class="sxs-lookup"><span data-stu-id="6b278-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b278-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6b278-108">Attributes and Elements</span></span>

<span data-ttu-id="6b278-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="6b278-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b278-110">특성</span><span class="sxs-lookup"><span data-stu-id="6b278-110">Attributes</span></span>

<span data-ttu-id="6b278-111">없음</span><span class="sxs-lookup"><span data-stu-id="6b278-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b278-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6b278-112">Child Elements</span></span>

<span data-ttu-id="6b278-113">없음</span><span class="sxs-lookup"><span data-stu-id="6b278-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6b278-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6b278-114">Parent Elements</span></span>

|<span data-ttu-id="6b278-115">요소</span><span class="sxs-lookup"><span data-stu-id="6b278-115">Element</span></span>|<span data-ttu-id="6b278-116">설명</span><span class="sxs-lookup"><span data-stu-id="6b278-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b278-117">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6b278-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="6b278-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="6b278-118">Text Value</span></span>

<span data-ttu-id="6b278-119">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b278-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b278-120">설명</span><span class="sxs-lookup"><span data-stu-id="6b278-120">Remarks</span></span>

<span data-ttu-id="6b278-121">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6b278-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b278-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b278-122">See Also</span></span>

[<span data-ttu-id="6b278-123">ListIControl (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="6b278-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="6b278-124">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6b278-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="6b278-125">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6b278-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
