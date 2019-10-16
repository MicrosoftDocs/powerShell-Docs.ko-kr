---
title: 구성 (형식)의 ItemSeclectionCondition에 대 한 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362532"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="7913f-102">Configuration에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="7913f-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7913f-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7913f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7913f-104">이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7913f-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="7913f-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7913f-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7913f-106">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) 구성에 대 한 컨트롤의 CustomControl에 대 한 CustomEntry 요소 구성 (형식)에 대 한 컨트롤의 Customentry 요소 구성 요소에 대 한 Customentry에 대 한 컨트롤의 customentry 구성 (형식)에 대 한 컨트롤의 ItemSeclectionCondition에 대 한 구성 (형식) PropertyName 요소의 ExpressionBinding에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="7913f-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7913f-107">구문</span><span class="sxs-lookup"><span data-stu-id="7913f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7913f-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="7913f-108">Attributes and Elements</span></span>

<span data-ttu-id="7913f-109">다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7913f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7913f-110">특성</span><span class="sxs-lookup"><span data-stu-id="7913f-110">Attributes</span></span>

<span data-ttu-id="7913f-111">없음</span><span class="sxs-lookup"><span data-stu-id="7913f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7913f-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="7913f-112">Child Elements</span></span>

<span data-ttu-id="7913f-113">없음</span><span class="sxs-lookup"><span data-stu-id="7913f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7913f-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="7913f-114">Parent Elements</span></span>

|<span data-ttu-id="7913f-115">요소</span><span class="sxs-lookup"><span data-stu-id="7913f-115">Element</span></span>|<span data-ttu-id="7913f-116">설명</span><span class="sxs-lookup"><span data-stu-id="7913f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7913f-117">구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7913f-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="7913f-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7913f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7913f-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="7913f-119">Text Value</span></span>

<span data-ttu-id="7913f-120">조건을 트리거하는 .NET 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7913f-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="7913f-121">설명</span><span class="sxs-lookup"><span data-stu-id="7913f-121">Remarks</span></span>

<span data-ttu-id="7913f-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7913f-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="7913f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7913f-123">See Also</span></span>

[<span data-ttu-id="7913f-124">구성에 대 한 컨트롤의 ItemSeclectionCondition에 대 한 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7913f-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7913f-125">구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="7913f-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="7913f-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="7913f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
