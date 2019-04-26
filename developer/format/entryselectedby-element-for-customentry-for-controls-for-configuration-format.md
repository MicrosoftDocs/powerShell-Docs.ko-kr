---
title: 구성 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066297"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="52c7e-102">Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="52c7e-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="52c7e-103">공용 컨트롤 또는이 컨트롤을 사용할 수 있어야 하는 조건을 정의 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="52c7e-104">이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="52c7e-105">CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry 구성 (형식)에 대 한 컨트롤에 대 한 구성 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식)</span><span class="sxs-lookup"><span data-stu-id="52c7e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52c7e-106">구문</span><span class="sxs-lookup"><span data-stu-id="52c7e-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52c7e-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-107">Attributes and Elements</span></span>

<span data-ttu-id="52c7e-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52c7e-109">특성</span><span class="sxs-lookup"><span data-stu-id="52c7e-109">Attributes</span></span>

<span data-ttu-id="52c7e-110">없음</span><span class="sxs-lookup"><span data-stu-id="52c7e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52c7e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-111">Child Elements</span></span>

|<span data-ttu-id="52c7e-112">요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-112">Element</span></span>|<span data-ttu-id="52c7e-113">설명</span><span class="sxs-lookup"><span data-stu-id="52c7e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52c7e-114">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="52c7e-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="52c7e-116">공용 컨트롤 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="52c7e-117">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="52c7e-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="52c7e-119">공용 컨트롤의이 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="52c7e-120">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="52c7e-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="52c7e-122">공용 컨트롤의이 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52c7e-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-123">Parent Elements</span></span>

|<span data-ttu-id="52c7e-124">요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-124">Element</span></span>|<span data-ttu-id="52c7e-125">설명</span><span class="sxs-lookup"><span data-stu-id="52c7e-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52c7e-126">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="52c7e-127">공용 컨트롤의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52c7e-128">설명</span><span class="sxs-lookup"><span data-stu-id="52c7e-128">Remarks</span></span>

<span data-ttu-id="52c7e-129">최소한 각 정의 하나 이상의.NET 유형, 선택 항목 집합 또는 지정 된 선택 조건이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="52c7e-130">형식, 선택 항목 집합 또는 지정할 수 있는 선택 조건 수가 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52c7e-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="52c7e-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52c7e-131">See Also</span></span>

[<span data-ttu-id="52c7e-132">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="52c7e-133">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="52c7e-134">구성 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="52c7e-135">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="52c7e-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="52c7e-136">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="52c7e-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
