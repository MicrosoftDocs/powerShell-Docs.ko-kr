---
title: GroupBy (형식)에 대 한 ItemSelectionCondition PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858269"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="cbafa-102">GroupBy의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cbafa-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="cbafa-103">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbafa-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="cbafa-104">이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 컨트롤이 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbafa-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="cbafa-105">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbafa-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="cbafa-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry CustomItem ExpressionBinding GroupBy (형식) PropertyName 요소에 대 한 GroupBy (형식) ItemSelectionCondition 요소에 대 한 GroupBy (형식) ExpressionBinding 요소에 대 한 GroupBy (형식) CustomItem 요소에 GroupBy (형식)에 대 한 ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="cbafa-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cbafa-107">구문</span><span class="sxs-lookup"><span data-stu-id="cbafa-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cbafa-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cbafa-108">Attributes and Elements</span></span>

<span data-ttu-id="cbafa-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cbafa-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cbafa-110">특성</span><span class="sxs-lookup"><span data-stu-id="cbafa-110">Attributes</span></span>

<span data-ttu-id="cbafa-111">없음</span><span class="sxs-lookup"><span data-stu-id="cbafa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cbafa-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cbafa-112">Child Elements</span></span>

<span data-ttu-id="cbafa-113">없음</span><span class="sxs-lookup"><span data-stu-id="cbafa-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cbafa-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cbafa-114">Parent Elements</span></span>

|<span data-ttu-id="cbafa-115">요소</span><span class="sxs-lookup"><span data-stu-id="cbafa-115">Element</span></span>|<span data-ttu-id="cbafa-116">설명</span><span class="sxs-lookup"><span data-stu-id="cbafa-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbafa-117">GroupBy (형식)에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="cbafa-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="cbafa-118">이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbafa-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cbafa-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="cbafa-119">Text Value</span></span>

<span data-ttu-id="cbafa-120">조건이 트리거하는.NET 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbafa-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="cbafa-121">설명</span><span class="sxs-lookup"><span data-stu-id="cbafa-121">Remarks</span></span>

<span data-ttu-id="cbafa-122">이 요소를 사용 하는 경우를 지정할 수 없습니다는 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) 요소 선택 조건을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbafa-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbafa-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbafa-123">See Also</span></span>

[<span data-ttu-id="cbafa-124">GroupBy (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="cbafa-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="cbafa-125">GroupBy (형식)에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="cbafa-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="cbafa-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="cbafa-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
