---
title: 구성 (형식)의 ItemSeclectionCondition에 대 한 ScriptBlock 요소 Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f44b1a7f059fa5f41c19eed93762b61eda5110e8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772895"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="e2153-102">Configuration에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2153-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e2153-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2153-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e2153-104">이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2153-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e2153-105">이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2153-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e2153-106">Configuration 요소 (format) 컨트롤 구성 요소에 대 한 Control 요소의 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) Customentries 요소에 대 한 CustomControl 요소에 대 한 구성 (형식) 구성 요소에 대 한 컨트롤의 customentries 요소 구성 요소에 대 한 컨트롤의 Customentries에 대 한 컨트롤의 요소에 대 한 컨트롤의 요소에 대 한 요소에 대 한 요소에 대 한 요소 구성 (형식)에 대 한 컨트롤에 대 한 요소를 구성 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e2153-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2153-107">구문</span><span class="sxs-lookup"><span data-stu-id="e2153-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2153-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e2153-108">Attributes and Elements</span></span>

<span data-ttu-id="e2153-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="e2153-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2153-110">특성</span><span class="sxs-lookup"><span data-stu-id="e2153-110">Attributes</span></span>

<span data-ttu-id="e2153-111">없음</span><span class="sxs-lookup"><span data-stu-id="e2153-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2153-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e2153-112">Child Elements</span></span>

<span data-ttu-id="e2153-113">없음</span><span class="sxs-lookup"><span data-stu-id="e2153-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2153-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e2153-114">Parent Elements</span></span>

|<span data-ttu-id="e2153-115">요소</span><span class="sxs-lookup"><span data-stu-id="e2153-115">Element</span></span>|<span data-ttu-id="e2153-116">설명</span><span class="sxs-lookup"><span data-stu-id="e2153-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2153-117">Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2153-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e2153-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2153-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2153-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e2153-119">Text Value</span></span>

<span data-ttu-id="e2153-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2153-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2153-121">설명</span><span class="sxs-lookup"><span data-stu-id="e2153-121">Remarks</span></span>

<span data-ttu-id="e2153-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2153-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2153-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2153-123">See Also</span></span>

[<span data-ttu-id="e2153-124">Configuration에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2153-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e2153-125">Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2153-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="e2153-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="e2153-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
