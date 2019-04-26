---
title: 구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064730"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="11bc2-102">Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="11bc2-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="11bc2-103">조건이 트리거하는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="11bc2-104">이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="11bc2-105">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="11bc2-106">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry EntrySelectedBy CustomEntry 구성 (에 대 한 구성 (형식) SelectionCondition 요소에 대 한 컨트롤에 대 한 구성 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식) EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="11bc2-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11bc2-107">구문</span><span class="sxs-lookup"><span data-stu-id="11bc2-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11bc2-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="11bc2-108">Attributes and Elements</span></span>

<span data-ttu-id="11bc2-109">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11bc2-110">특성</span><span class="sxs-lookup"><span data-stu-id="11bc2-110">Attributes</span></span>

<span data-ttu-id="11bc2-111">없음</span><span class="sxs-lookup"><span data-stu-id="11bc2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11bc2-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="11bc2-112">Child Elements</span></span>

<span data-ttu-id="11bc2-113">없음</span><span class="sxs-lookup"><span data-stu-id="11bc2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11bc2-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="11bc2-114">Parent Elements</span></span>

|<span data-ttu-id="11bc2-115">요소</span><span class="sxs-lookup"><span data-stu-id="11bc2-115">Element</span></span>|<span data-ttu-id="11bc2-116">설명</span><span class="sxs-lookup"><span data-stu-id="11bc2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11bc2-117">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="11bc2-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="11bc2-118">사용할 일반적인 컨트롤 정의에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11bc2-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="11bc2-119">Text Value</span></span>

<span data-ttu-id="11bc2-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="11bc2-121">설명</span><span class="sxs-lookup"><span data-stu-id="11bc2-121">Remarks</span></span>

<span data-ttu-id="11bc2-122">선택 조건 최소 하나의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="11bc2-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="11bc2-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11bc2-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11bc2-124">See Also</span></span>

[<span data-ttu-id="11bc2-125">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="11bc2-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="11bc2-126">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="11bc2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
