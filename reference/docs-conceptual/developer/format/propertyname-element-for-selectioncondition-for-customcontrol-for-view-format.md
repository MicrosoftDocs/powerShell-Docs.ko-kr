---
title: CustomControl에 대 한 SelectionCondition의 PropertyName 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362352"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="73760-102">View에 대한 CustomControl의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="73760-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="73760-103">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73760-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="73760-104">이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73760-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="73760-105">이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73760-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="73760-106">Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소에 대 한 CustomControl for view (format) EntrySelectedBy for view (format) SelectionCondition 요소에 대 한 CustomControl for CustomControl for View (Format) PropertyName CustomControl에 대 한 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="73760-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73760-107">구문</span><span class="sxs-lookup"><span data-stu-id="73760-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73760-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="73760-108">Attributes and Elements</span></span>

<span data-ttu-id="73760-109">다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="73760-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73760-110">특성</span><span class="sxs-lookup"><span data-stu-id="73760-110">Attributes</span></span>

<span data-ttu-id="73760-111">없음</span><span class="sxs-lookup"><span data-stu-id="73760-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73760-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="73760-112">Child Elements</span></span>

<span data-ttu-id="73760-113">없음</span><span class="sxs-lookup"><span data-stu-id="73760-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="73760-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="73760-114">Parent Elements</span></span>

|<span data-ttu-id="73760-115">요소</span><span class="sxs-lookup"><span data-stu-id="73760-115">Element</span></span>|<span data-ttu-id="73760-116">설명</span><span class="sxs-lookup"><span data-stu-id="73760-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73760-117">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="73760-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="73760-118">컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="73760-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="73760-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="73760-119">Text Value</span></span>

<span data-ttu-id="73760-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="73760-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="73760-121">설명</span><span class="sxs-lookup"><span data-stu-id="73760-121">Remarks</span></span>

<span data-ttu-id="73760-122">선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73760-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="73760-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="73760-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73760-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73760-124">See Also</span></span>

[<span data-ttu-id="73760-125">CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="73760-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="73760-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="73760-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
