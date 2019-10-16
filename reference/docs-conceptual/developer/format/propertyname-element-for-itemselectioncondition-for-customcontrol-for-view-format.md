---
title: CustomControl (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362442"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="49feb-102">View에 대한 CustomControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="49feb-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="49feb-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49feb-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="49feb-104">이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49feb-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="49feb-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="49feb-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="49feb-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 보기 (형식)에 대 한 Customentry에 대 한 customentry의 CustomControl for view (Format) ItemSelectionCondition 요소에 대 한 CustomControl for View (format) PropertyName 요소에 대 한 ItemSelectionCondition 요소 보기에 대 한 CustomControl (형식</span><span class="sxs-lookup"><span data-stu-id="49feb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="49feb-107">구문</span><span class="sxs-lookup"><span data-stu-id="49feb-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49feb-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="49feb-108">Attributes and Elements</span></span>

<span data-ttu-id="49feb-109">다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="49feb-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49feb-110">특성</span><span class="sxs-lookup"><span data-stu-id="49feb-110">Attributes</span></span>

<span data-ttu-id="49feb-111">없음</span><span class="sxs-lookup"><span data-stu-id="49feb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49feb-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="49feb-112">Child Elements</span></span>

<span data-ttu-id="49feb-113">없음</span><span class="sxs-lookup"><span data-stu-id="49feb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49feb-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="49feb-114">Parent Elements</span></span>

|<span data-ttu-id="49feb-115">요소</span><span class="sxs-lookup"><span data-stu-id="49feb-115">Element</span></span>|<span data-ttu-id="49feb-116">설명</span><span class="sxs-lookup"><span data-stu-id="49feb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49feb-117">CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="49feb-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="49feb-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="49feb-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="49feb-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="49feb-119">Text Value</span></span>

<span data-ttu-id="49feb-120">조건을 트리거하는 .NET 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="49feb-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="49feb-121">설명</span><span class="sxs-lookup"><span data-stu-id="49feb-121">Remarks</span></span>

<span data-ttu-id="49feb-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="49feb-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="49feb-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49feb-123">See Also</span></span>

[<span data-ttu-id="49feb-124">CustomControl에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="49feb-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="49feb-125">CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="49feb-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="49feb-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="49feb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
