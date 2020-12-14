---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
description: WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: bda34b0c1e97fb85536132bedcec3986072801b7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665705"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="42614-103">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="42614-103">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="42614-104">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42614-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="42614-105">이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42614-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="42614-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy for WideEntry (format) PropertyName 요소에 대해 WideEntry (형식)에 대 한 SelectionCondition for (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="42614-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42614-107">구문</span><span class="sxs-lookup"><span data-stu-id="42614-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="42614-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="42614-108">Attributes and Elements</span></span>

<span data-ttu-id="42614-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="42614-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42614-110">특성</span><span class="sxs-lookup"><span data-stu-id="42614-110">Attributes</span></span>

<span data-ttu-id="42614-111">없음</span><span class="sxs-lookup"><span data-stu-id="42614-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42614-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="42614-112">Child Elements</span></span>

<span data-ttu-id="42614-113">없음</span><span class="sxs-lookup"><span data-stu-id="42614-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42614-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="42614-114">Parent Elements</span></span>

|<span data-ttu-id="42614-115">요소</span><span class="sxs-lookup"><span data-stu-id="42614-115">Element</span></span>|<span data-ttu-id="42614-116">설명</span><span class="sxs-lookup"><span data-stu-id="42614-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42614-117">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="42614-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="42614-118">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="42614-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42614-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="42614-119">Text Value</span></span>

<span data-ttu-id="42614-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="42614-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="42614-121">설명</span><span class="sxs-lookup"><span data-stu-id="42614-121">Remarks</span></span>

<span data-ttu-id="42614-122">선택 조건은 평가할 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42614-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="42614-123">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42614-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="42614-124">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42614-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42614-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42614-125">See Also</span></span>

[<span data-ttu-id="42614-126">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="42614-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="42614-127">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="42614-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="42614-128">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="42614-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="42614-129">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="42614-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="42614-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="42614-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
