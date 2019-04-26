---
title: GroupBy (형식)에 대 한 SelectionCondition PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064818"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="33ce5-102">GroupBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="33ce5-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="33ce5-103">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="33ce5-104">이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="33ce5-105">이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="33ce5-106">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry EntrySelectedBy GroupBy (형식)에 대 한 SelectionCondition PropertyName 요소 GroupBy (형식)에 대 한 GroupBy (형식) SelectionCondition 요소에 대 한 GroupBy (형식) EntrySelectedBy 요소에</span><span class="sxs-lookup"><span data-stu-id="33ce5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33ce5-107">구문</span><span class="sxs-lookup"><span data-stu-id="33ce5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33ce5-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="33ce5-108">Attributes and Elements</span></span>

<span data-ttu-id="33ce5-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33ce5-110">특성</span><span class="sxs-lookup"><span data-stu-id="33ce5-110">Attributes</span></span>

<span data-ttu-id="33ce5-111">없음</span><span class="sxs-lookup"><span data-stu-id="33ce5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33ce5-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="33ce5-112">Child Elements</span></span>

<span data-ttu-id="33ce5-113">없음</span><span class="sxs-lookup"><span data-stu-id="33ce5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33ce5-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="33ce5-114">Parent Elements</span></span>

|<span data-ttu-id="33ce5-115">요소</span><span class="sxs-lookup"><span data-stu-id="33ce5-115">Element</span></span>|<span data-ttu-id="33ce5-116">설명</span><span class="sxs-lookup"><span data-stu-id="33ce5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33ce5-117">GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="33ce5-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="33ce5-118">사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="33ce5-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="33ce5-119">Text Value</span></span>

<span data-ttu-id="33ce5-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="33ce5-121">설명</span><span class="sxs-lookup"><span data-stu-id="33ce5-121">Remarks</span></span>

<span data-ttu-id="33ce5-122">선택 조건 최소 하나의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="33ce5-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="33ce5-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33ce5-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33ce5-124">See Also</span></span>

[<span data-ttu-id="33ce5-125">GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="33ce5-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="33ce5-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="33ce5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
