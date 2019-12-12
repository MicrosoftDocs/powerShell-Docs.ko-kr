---
title: 구성 (형식)의 ItemSeclectionCondition에 대 한 ScriptBlock 요소 Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362122"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="005ba-102">Configuration에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="005ba-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="005ba-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="005ba-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="005ba-104">이 스크립트가 `true`평가 되 면 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="005ba-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="005ba-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="005ba-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="005ba-106">구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) 구성에 대 한 컨트롤의 CustomControl에 대 한 CustomEntry 요소 구성 (형식)에 대 한 컨트롤의 Customentry 요소 구성 요소에 대 한 Customentry에 대 한 컨트롤의 customentry 구성 (형식)의 컨트롤에 대 한 ItemSelectionCondition의 구성 (Format) ScriptBlock 요소에 대 한 ExpressionBinding의 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="005ba-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="005ba-107">구문</span><span class="sxs-lookup"><span data-stu-id="005ba-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="005ba-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="005ba-108">Attributes and Elements</span></span>

<span data-ttu-id="005ba-109">다음 섹션에서는 특성, 자식 요소 및 `ScriptBlock` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="005ba-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="005ba-110">특성</span><span class="sxs-lookup"><span data-stu-id="005ba-110">Attributes</span></span>

<span data-ttu-id="005ba-111">없음</span><span class="sxs-lookup"><span data-stu-id="005ba-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="005ba-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="005ba-112">Child Elements</span></span>

<span data-ttu-id="005ba-113">없음</span><span class="sxs-lookup"><span data-stu-id="005ba-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="005ba-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="005ba-114">Parent Elements</span></span>

|<span data-ttu-id="005ba-115">요소</span><span class="sxs-lookup"><span data-stu-id="005ba-115">Element</span></span>|<span data-ttu-id="005ba-116">설명</span><span class="sxs-lookup"><span data-stu-id="005ba-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="005ba-117">구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="005ba-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="005ba-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="005ba-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="005ba-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="005ba-119">Text Value</span></span>

<span data-ttu-id="005ba-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="005ba-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="005ba-121">설명</span><span class="sxs-lookup"><span data-stu-id="005ba-121">Remarks</span></span>

<span data-ttu-id="005ba-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="005ba-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="005ba-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="005ba-123">See Also</span></span>

[<span data-ttu-id="005ba-124">구성에 대 한 ItemSeclectionCondition에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="005ba-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="005ba-125">구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="005ba-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="005ba-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="005ba-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
