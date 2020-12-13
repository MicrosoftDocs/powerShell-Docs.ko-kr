---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)
description: ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: ec7691358d0ff3758411317a349221e1704a1895
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659900"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="9f4f3-103">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9f4f3-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="9f4f3-104">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f4f3-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9f4f3-105">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f4f3-105">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="9f4f3-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (format) SelectionCondition 요소에 대해 ListEntry (형식)에 대 한 SelectionCondition for ListEntry (형식)에 대 한 SelectionCondition의 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f4f3-107">구문</span><span class="sxs-lookup"><span data-stu-id="9f4f3-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f4f3-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-108">Attributes and Elements</span></span>

<span data-ttu-id="9f4f3-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="9f4f3-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f4f3-110">특성</span><span class="sxs-lookup"><span data-stu-id="9f4f3-110">Attributes</span></span>

<span data-ttu-id="9f4f3-111">없음</span><span class="sxs-lookup"><span data-stu-id="9f4f3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f4f3-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-112">Child Elements</span></span>

<span data-ttu-id="9f4f3-113">없음</span><span class="sxs-lookup"><span data-stu-id="9f4f3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f4f3-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-114">Parent Elements</span></span>

|<span data-ttu-id="9f4f3-115">요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-115">Element</span></span>|<span data-ttu-id="9f4f3-116">설명</span><span class="sxs-lookup"><span data-stu-id="9f4f3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f4f3-117">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="9f4f3-118">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f4f3-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9f4f3-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="9f4f3-119">Text Value</span></span>

<span data-ttu-id="9f4f3-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f4f3-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f4f3-121">설명</span><span class="sxs-lookup"><span data-stu-id="9f4f3-121">Remarks</span></span>

<span data-ttu-id="9f4f3-122">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f4f3-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="9f4f3-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9f4f3-123">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="9f4f3-124">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9f4f3-124">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f4f3-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f4f3-125">See Also</span></span>

[<span data-ttu-id="9f4f3-126">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="9f4f3-126">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="9f4f3-127">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-127">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9f4f3-128">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="9f4f3-128">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9f4f3-129">목록 보기</span><span class="sxs-lookup"><span data-stu-id="9f4f3-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9f4f3-130">뷰 항목이 나 항목을 사용 하는 경우 조건 정의</span><span class="sxs-lookup"><span data-stu-id="9f4f3-130">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9f4f3-131">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9f4f3-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
