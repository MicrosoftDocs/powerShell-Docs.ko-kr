---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
description: ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 1e318e3a29f07b157b9ae7343ba08759db8efbb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665824"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="b13a6-103">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b13a6-103">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="b13a6-104">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b13a6-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b13a6-105">이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b13a6-105">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="b13a6-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy for ListEntry (format) PropertyName 요소에 대해 ListEntry (형식)에 대 한 SelectionCondition for (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b13a6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b13a6-107">구문</span><span class="sxs-lookup"><span data-stu-id="b13a6-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b13a6-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b13a6-108">Attributes and Elements</span></span>

<span data-ttu-id="b13a6-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="b13a6-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b13a6-110">특성</span><span class="sxs-lookup"><span data-stu-id="b13a6-110">Attributes</span></span>

<span data-ttu-id="b13a6-111">없음</span><span class="sxs-lookup"><span data-stu-id="b13a6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b13a6-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b13a6-112">Child Elements</span></span>

<span data-ttu-id="b13a6-113">없음</span><span class="sxs-lookup"><span data-stu-id="b13a6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b13a6-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b13a6-114">Parent Elements</span></span>

|<span data-ttu-id="b13a6-115">요소</span><span class="sxs-lookup"><span data-stu-id="b13a6-115">Element</span></span>|<span data-ttu-id="b13a6-116">설명</span><span class="sxs-lookup"><span data-stu-id="b13a6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b13a6-117">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="b13a6-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b13a6-118">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b13a6-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b13a6-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b13a6-119">Text Value</span></span>

<span data-ttu-id="b13a6-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b13a6-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b13a6-121">설명</span><span class="sxs-lookup"><span data-stu-id="b13a6-121">Remarks</span></span>

<span data-ttu-id="b13a6-122">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b13a6-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="b13a6-123">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b13a6-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b13a6-124">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b13a6-124">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b13a6-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b13a6-125">See Also</span></span>

[<span data-ttu-id="b13a6-126">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="b13a6-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b13a6-127">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="b13a6-127">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b13a6-128">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b13a6-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="b13a6-129">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="b13a6-129">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b13a6-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b13a6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
