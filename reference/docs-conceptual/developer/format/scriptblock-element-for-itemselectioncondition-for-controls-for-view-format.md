---
title: 보기 (형식)의 컨트롤에 대 한 ItemSelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74b3e23005f595c4c550320849cac5b196e9d479
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787668"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="9c21a-102">View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c21a-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="9c21a-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c21a-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9c21a-104">이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c21a-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="9c21a-105">이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c21a-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="9c21a-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 컨트롤에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소 (format) Customentries 요소 CustomControl view (format) Customentries 요소 for View (format)의 컨트롤에 대 한 customentries 요소 뷰 (format)의 컨트롤에 대 한 ExpressionBinding 요소에 대 한 컨트롤의 요소에 대 한 요소에 대 한 요소를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9c21a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c21a-107">구문</span><span class="sxs-lookup"><span data-stu-id="9c21a-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c21a-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9c21a-108">Attributes and Elements</span></span>

<span data-ttu-id="9c21a-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="9c21a-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c21a-110">특성</span><span class="sxs-lookup"><span data-stu-id="9c21a-110">Attributes</span></span>

<span data-ttu-id="9c21a-111">없음</span><span class="sxs-lookup"><span data-stu-id="9c21a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c21a-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9c21a-112">Child Elements</span></span>

<span data-ttu-id="9c21a-113">없음</span><span class="sxs-lookup"><span data-stu-id="9c21a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c21a-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9c21a-114">Parent Elements</span></span>

|<span data-ttu-id="9c21a-115">요소</span><span class="sxs-lookup"><span data-stu-id="9c21a-115">Element</span></span>|<span data-ttu-id="9c21a-116">설명</span><span class="sxs-lookup"><span data-stu-id="9c21a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c21a-117">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9c21a-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="9c21a-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c21a-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9c21a-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9c21a-119">Text Value</span></span>

<span data-ttu-id="9c21a-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c21a-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c21a-121">설명</span><span class="sxs-lookup"><span data-stu-id="9c21a-121">Remarks</span></span>

<span data-ttu-id="9c21a-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c21a-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c21a-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c21a-123">See Also</span></span>

[<span data-ttu-id="9c21a-124">View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9c21a-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9c21a-125">View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="9c21a-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="9c21a-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9c21a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
