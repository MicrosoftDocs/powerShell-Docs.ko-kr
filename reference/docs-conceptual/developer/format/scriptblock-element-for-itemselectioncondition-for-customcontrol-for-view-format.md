---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
description: View에 대한 CustomControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: d762f400f5bb52af314093079fe94223c56d3f31
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665127"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="faeeb-103">View에 대한 CustomControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="faeeb-103">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="faeeb-104">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="faeeb-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="faeeb-105">이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="faeeb-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="faeeb-106">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="faeeb-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="faeeb-107">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 CustomEntries 요소에 대 한 customentries 요소 (형식) Customentries 요소 view (format) 요소에 대 한 항목 CustomControl for view (format) ItemSelectionCondition 요소에 대 한 CustomControl for view (format) ScriptBlock 요소의 ItemSelectionCondition for view (Format)</span><span class="sxs-lookup"><span data-stu-id="faeeb-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="faeeb-108">구문</span><span class="sxs-lookup"><span data-stu-id="faeeb-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="faeeb-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="faeeb-109">Attributes and Elements</span></span>

<span data-ttu-id="faeeb-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="faeeb-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="faeeb-111">특성</span><span class="sxs-lookup"><span data-stu-id="faeeb-111">Attributes</span></span>

<span data-ttu-id="faeeb-112">없음</span><span class="sxs-lookup"><span data-stu-id="faeeb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="faeeb-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="faeeb-113">Child Elements</span></span>

<span data-ttu-id="faeeb-114">없음</span><span class="sxs-lookup"><span data-stu-id="faeeb-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="faeeb-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="faeeb-115">Parent Elements</span></span>

|<span data-ttu-id="faeeb-116">요소</span><span class="sxs-lookup"><span data-stu-id="faeeb-116">Element</span></span>|<span data-ttu-id="faeeb-117">설명</span><span class="sxs-lookup"><span data-stu-id="faeeb-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="faeeb-118">CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="faeeb-118">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="faeeb-119">이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="faeeb-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="faeeb-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="faeeb-120">Text Value</span></span>

<span data-ttu-id="faeeb-121">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="faeeb-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="faeeb-122">설명</span><span class="sxs-lookup"><span data-stu-id="faeeb-122">Remarks</span></span>

<span data-ttu-id="faeeb-123">이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="faeeb-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="faeeb-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="faeeb-124">See Also</span></span>

[<span data-ttu-id="faeeb-125">View에 대한 CustomControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="faeeb-125">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="faeeb-126">CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="faeeb-126">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="faeeb-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="faeeb-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
