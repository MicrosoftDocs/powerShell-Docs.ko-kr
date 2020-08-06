---
title: GroupBy (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6d671035bfd2ef6323b638fdd951bb020bd6548
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780885"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="5a9ce-102">GroupBy의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5a9ce-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="5a9ce-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a9ce-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5a9ce-104">이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a9ce-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="5a9ce-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a9ce-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5a9ce-106">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소에 대 한 groupby 요소 (format) CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Format) GroupBy 항목에 대 한 Customentries 요소 groupby (format)의 Customentries에 대 한 요소에 대 한 요소에 대 한 요소에 대 한 요소를</span><span class="sxs-lookup"><span data-stu-id="5a9ce-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a9ce-107">구문</span><span class="sxs-lookup"><span data-stu-id="5a9ce-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a9ce-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5a9ce-108">Attributes and Elements</span></span>

<span data-ttu-id="5a9ce-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="5a9ce-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a9ce-110">특성</span><span class="sxs-lookup"><span data-stu-id="5a9ce-110">Attributes</span></span>

<span data-ttu-id="5a9ce-111">없음</span><span class="sxs-lookup"><span data-stu-id="5a9ce-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a9ce-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5a9ce-112">Child Elements</span></span>

<span data-ttu-id="5a9ce-113">없음</span><span class="sxs-lookup"><span data-stu-id="5a9ce-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5a9ce-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5a9ce-114">Parent Elements</span></span>

|<span data-ttu-id="5a9ce-115">요소</span><span class="sxs-lookup"><span data-stu-id="5a9ce-115">Element</span></span>|<span data-ttu-id="5a9ce-116">설명</span><span class="sxs-lookup"><span data-stu-id="5a9ce-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a9ce-117">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5a9ce-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="5a9ce-118">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a9ce-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5a9ce-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="5a9ce-119">Text Value</span></span>

<span data-ttu-id="5a9ce-120">조건을 트리거하는 .NET 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a9ce-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a9ce-121">설명</span><span class="sxs-lookup"><span data-stu-id="5a9ce-121">Remarks</span></span>

<span data-ttu-id="5a9ce-122">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a9ce-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a9ce-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a9ce-123">See Also</span></span>

[<span data-ttu-id="5a9ce-124">GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5a9ce-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="5a9ce-125">GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5a9ce-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="5a9ce-126">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5a9ce-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
