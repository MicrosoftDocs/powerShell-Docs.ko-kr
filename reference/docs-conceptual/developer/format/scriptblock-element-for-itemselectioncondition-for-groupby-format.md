---
title: GroupBy (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7738b180f328c7360275058cdb9dea01df6ea285
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787651"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="2ee3b-102">GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2ee3b-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="2ee3b-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee3b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2ee3b-104">이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ee3b-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2ee3b-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ee3b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2ee3b-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소에 대 한 groupby 요소 (format) CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Format) GroupBy 항목에 대 한 Customentries 요소 groupby (format)에 대 한 Customentries에 대 한 요소에 대 한 요소에 대 한 요소에 대 한 요소에 대 한 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee3b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ee3b-107">구문</span><span class="sxs-lookup"><span data-stu-id="2ee3b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ee3b-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2ee3b-108">Attributes and Elements</span></span>

<span data-ttu-id="2ee3b-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="2ee3b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ee3b-110">특성</span><span class="sxs-lookup"><span data-stu-id="2ee3b-110">Attributes</span></span>

<span data-ttu-id="2ee3b-111">없음</span><span class="sxs-lookup"><span data-stu-id="2ee3b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ee3b-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2ee3b-112">Child Elements</span></span>

<span data-ttu-id="2ee3b-113">없음</span><span class="sxs-lookup"><span data-stu-id="2ee3b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2ee3b-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2ee3b-114">Parent Elements</span></span>

|<span data-ttu-id="2ee3b-115">요소</span><span class="sxs-lookup"><span data-stu-id="2ee3b-115">Element</span></span>|<span data-ttu-id="2ee3b-116">설명</span><span class="sxs-lookup"><span data-stu-id="2ee3b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ee3b-117">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2ee3b-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="2ee3b-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee3b-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2ee3b-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="2ee3b-119">Text Value</span></span>

<span data-ttu-id="2ee3b-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ee3b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ee3b-121">설명</span><span class="sxs-lookup"><span data-stu-id="2ee3b-121">Remarks</span></span>

<span data-ttu-id="2ee3b-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ee3b-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ee3b-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2ee3b-123">See Also</span></span>

[<span data-ttu-id="2ee3b-124">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2ee3b-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="2ee3b-125">GroupBy의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2ee3b-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="2ee3b-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2ee3b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
