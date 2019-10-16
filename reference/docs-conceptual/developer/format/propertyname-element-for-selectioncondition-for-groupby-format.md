---
title: GroupBy (형식)에 대 한 SelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364952"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="79fc2-102">GroupBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="79fc2-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="79fc2-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fc2-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="79fc2-104">이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fc2-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="79fc2-105">이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fc2-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="79fc2-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) EntrySelectedBy 요소에 대 한 CustomControl 요소에 대 한 CustomEntry for groupby (format) PropertyName 요소에 대 한 selectioncondition on groupby (format)의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="79fc2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79fc2-107">구문</span><span class="sxs-lookup"><span data-stu-id="79fc2-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79fc2-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="79fc2-108">Attributes and Elements</span></span>

<span data-ttu-id="79fc2-109">다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fc2-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79fc2-110">특성</span><span class="sxs-lookup"><span data-stu-id="79fc2-110">Attributes</span></span>

<span data-ttu-id="79fc2-111">없음</span><span class="sxs-lookup"><span data-stu-id="79fc2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79fc2-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="79fc2-112">Child Elements</span></span>

<span data-ttu-id="79fc2-113">없음</span><span class="sxs-lookup"><span data-stu-id="79fc2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="79fc2-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="79fc2-114">Parent Elements</span></span>

|<span data-ttu-id="79fc2-115">요소</span><span class="sxs-lookup"><span data-stu-id="79fc2-115">Element</span></span>|<span data-ttu-id="79fc2-116">설명</span><span class="sxs-lookup"><span data-stu-id="79fc2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79fc2-117">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="79fc2-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="79fc2-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fc2-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="79fc2-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="79fc2-119">Text Value</span></span>

<span data-ttu-id="79fc2-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fc2-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="79fc2-121">설명</span><span class="sxs-lookup"><span data-stu-id="79fc2-121">Remarks</span></span>

<span data-ttu-id="79fc2-122">선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79fc2-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="79fc2-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79fc2-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79fc2-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79fc2-124">See Also</span></span>

[<span data-ttu-id="79fc2-125">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="79fc2-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="79fc2-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="79fc2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
