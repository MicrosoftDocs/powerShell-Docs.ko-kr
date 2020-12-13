---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
description: GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665094"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="f53df-103">GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f53df-103">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="f53df-104">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53df-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f53df-105">이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53df-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="f53df-106">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53df-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f53df-107">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소에 대 한 groupby 요소 (format) CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Format) GroupBy 항목에 대 한 Customentries 요소 groupby (format)에 대 한 Customentries에 대 한 요소에 대 한 요소에 대 한 요소에 대 한 요소에 대 한 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53df-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f53df-108">구문</span><span class="sxs-lookup"><span data-stu-id="f53df-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f53df-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f53df-109">Attributes and Elements</span></span>

<span data-ttu-id="f53df-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="f53df-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f53df-111">특성</span><span class="sxs-lookup"><span data-stu-id="f53df-111">Attributes</span></span>

<span data-ttu-id="f53df-112">없음</span><span class="sxs-lookup"><span data-stu-id="f53df-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f53df-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f53df-113">Child Elements</span></span>

<span data-ttu-id="f53df-114">없음</span><span class="sxs-lookup"><span data-stu-id="f53df-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f53df-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f53df-115">Parent Elements</span></span>

|<span data-ttu-id="f53df-116">요소</span><span class="sxs-lookup"><span data-stu-id="f53df-116">Element</span></span>|<span data-ttu-id="f53df-117">설명</span><span class="sxs-lookup"><span data-stu-id="f53df-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f53df-118">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f53df-118">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="f53df-119">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53df-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f53df-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="f53df-120">Text Value</span></span>

<span data-ttu-id="f53df-121">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53df-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f53df-122">설명</span><span class="sxs-lookup"><span data-stu-id="f53df-122">Remarks</span></span>

<span data-ttu-id="f53df-123">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53df-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="f53df-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f53df-124">See Also</span></span>

[<span data-ttu-id="f53df-125">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f53df-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f53df-126">GroupBy의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f53df-126">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="f53df-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f53df-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
