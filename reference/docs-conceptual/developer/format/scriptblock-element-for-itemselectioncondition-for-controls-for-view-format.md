---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
description: View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: c005215f7b7984541806d2f5de47372d536787ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665197"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="cccd6-103">View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cccd6-103">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="cccd6-104">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cccd6-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="cccd6-105">이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cccd6-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="cccd6-106">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cccd6-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="cccd6-107">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 컨트롤에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소 (format) Customentries 요소 CustomControl view (format) Customentries 요소 for View (format)의 컨트롤에 대 한 customentries 요소 뷰 (format)의 컨트롤에 대 한 ExpressionBinding 요소에 대 한 컨트롤의 요소에 대 한 요소에 대 한 요소를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cccd6-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cccd6-108">구문</span><span class="sxs-lookup"><span data-stu-id="cccd6-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cccd6-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cccd6-109">Attributes and Elements</span></span>

<span data-ttu-id="cccd6-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="cccd6-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cccd6-111">특성</span><span class="sxs-lookup"><span data-stu-id="cccd6-111">Attributes</span></span>

<span data-ttu-id="cccd6-112">없음</span><span class="sxs-lookup"><span data-stu-id="cccd6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cccd6-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cccd6-113">Child Elements</span></span>

<span data-ttu-id="cccd6-114">없음</span><span class="sxs-lookup"><span data-stu-id="cccd6-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cccd6-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cccd6-115">Parent Elements</span></span>

|<span data-ttu-id="cccd6-116">요소</span><span class="sxs-lookup"><span data-stu-id="cccd6-116">Element</span></span>|<span data-ttu-id="cccd6-117">설명</span><span class="sxs-lookup"><span data-stu-id="cccd6-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cccd6-118">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cccd6-118">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="cccd6-119">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cccd6-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cccd6-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="cccd6-120">Text Value</span></span>

<span data-ttu-id="cccd6-121">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cccd6-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="cccd6-122">설명</span><span class="sxs-lookup"><span data-stu-id="cccd6-122">Remarks</span></span>

<span data-ttu-id="cccd6-123">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cccd6-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="cccd6-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cccd6-124">See Also</span></span>

[<span data-ttu-id="cccd6-125">View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cccd6-125">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="cccd6-126">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cccd6-126">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cccd6-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="cccd6-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
