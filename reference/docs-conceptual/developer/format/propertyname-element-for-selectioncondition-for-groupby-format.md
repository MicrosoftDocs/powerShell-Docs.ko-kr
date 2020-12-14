---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 SelectionCondition에 대한 PropertyName 요소(형식)
description: GroupBy의 SelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: b89fead6185c88ca03956dc265135833696b91d7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665671"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="5dff8-103">GroupBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5dff8-103">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="5dff8-104">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5dff8-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5dff8-105">이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5dff8-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="5dff8-106">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5dff8-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5dff8-107">구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl groupby (형식)에 대 한 CustomControl의 경우에는 groupby (형식)에 대 한 SelectionCondition 요소에 대해에 대 한</span><span class="sxs-lookup"><span data-stu-id="5dff8-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5dff8-108">구문</span><span class="sxs-lookup"><span data-stu-id="5dff8-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5dff8-109">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5dff8-109">Attributes and Elements</span></span>

<span data-ttu-id="5dff8-110">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="5dff8-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5dff8-111">특성</span><span class="sxs-lookup"><span data-stu-id="5dff8-111">Attributes</span></span>

<span data-ttu-id="5dff8-112">없음</span><span class="sxs-lookup"><span data-stu-id="5dff8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5dff8-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5dff8-113">Child Elements</span></span>

<span data-ttu-id="5dff8-114">없음</span><span class="sxs-lookup"><span data-stu-id="5dff8-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5dff8-115">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5dff8-115">Parent Elements</span></span>

|<span data-ttu-id="5dff8-116">요소</span><span class="sxs-lookup"><span data-stu-id="5dff8-116">Element</span></span>|<span data-ttu-id="5dff8-117">설명</span><span class="sxs-lookup"><span data-stu-id="5dff8-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5dff8-118">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5dff8-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="5dff8-119">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5dff8-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5dff8-120">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="5dff8-120">Text Value</span></span>

<span data-ttu-id="5dff8-121">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5dff8-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5dff8-122">설명</span><span class="sxs-lookup"><span data-stu-id="5dff8-122">Remarks</span></span>

<span data-ttu-id="5dff8-123">선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5dff8-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="5dff8-124">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5dff8-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5dff8-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5dff8-125">See Also</span></span>

[<span data-ttu-id="5dff8-126">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5dff8-126">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="5dff8-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5dff8-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
