---
title: 보기 (형식)의 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362482"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="28441-102">View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="28441-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="28441-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28441-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="28441-104">이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28441-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="28441-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28441-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="28441-106">Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for view (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry의 요소에 대 한 형식입니다. 뷰 (형식) 컨트롤에 대 한 ItemSelectionCondition의 View (Format) PropertyName 요소에 대 한 ExpressionBinding의 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="28441-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="28441-107">구문</span><span class="sxs-lookup"><span data-stu-id="28441-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="28441-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="28441-108">Attributes and Elements</span></span>

<span data-ttu-id="28441-109">다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="28441-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="28441-110">특성</span><span class="sxs-lookup"><span data-stu-id="28441-110">Attributes</span></span>

<span data-ttu-id="28441-111">없음</span><span class="sxs-lookup"><span data-stu-id="28441-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="28441-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="28441-112">Child Elements</span></span>

<span data-ttu-id="28441-113">없음</span><span class="sxs-lookup"><span data-stu-id="28441-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="28441-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="28441-114">Parent Elements</span></span>

|<span data-ttu-id="28441-115">요소</span><span class="sxs-lookup"><span data-stu-id="28441-115">Element</span></span>|<span data-ttu-id="28441-116">설명</span><span class="sxs-lookup"><span data-stu-id="28441-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28441-117">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="28441-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="28441-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="28441-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="28441-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="28441-119">Text Value</span></span>

<span data-ttu-id="28441-120">조건을 트리거하는 .NET 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28441-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="28441-121">설명</span><span class="sxs-lookup"><span data-stu-id="28441-121">Remarks</span></span>

<span data-ttu-id="28441-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28441-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="28441-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28441-123">See Also</span></span>

[<span data-ttu-id="28441-124">View 컨트롤에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="28441-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="28441-125">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="28441-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="28441-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="28441-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
