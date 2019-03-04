---
title: ScriptBlock 요소 EntrySelectedBy ListControl (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858659"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="e2fe0-102">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e2fe0-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="e2fe0-103">조건이 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fe0-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e2fe0-104">이 스크립트를 계산할 때 `true`조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fe0-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="e2fe0-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 ListEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소 ListEntry (형식)에</span><span class="sxs-lookup"><span data-stu-id="e2fe0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2fe0-106">구문</span><span class="sxs-lookup"><span data-stu-id="e2fe0-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2fe0-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e2fe0-107">Attributes and Elements</span></span>

<span data-ttu-id="e2fe0-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e2fe0-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2fe0-109">특성</span><span class="sxs-lookup"><span data-stu-id="e2fe0-109">Attributes</span></span>

<span data-ttu-id="e2fe0-110">없음</span><span class="sxs-lookup"><span data-stu-id="e2fe0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2fe0-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e2fe0-111">Child Elements</span></span>

<span data-ttu-id="e2fe0-112">없음</span><span class="sxs-lookup"><span data-stu-id="e2fe0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2fe0-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e2fe0-113">Parent Elements</span></span>

|<span data-ttu-id="e2fe0-114">요소</span><span class="sxs-lookup"><span data-stu-id="e2fe0-114">Element</span></span>|<span data-ttu-id="e2fe0-115">설명</span><span class="sxs-lookup"><span data-stu-id="e2fe0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2fe0-116">ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e2fe0-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e2fe0-117">사용할이 목록 항목에 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fe0-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2fe0-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e2fe0-118">Text Value</span></span>

<span data-ttu-id="e2fe0-119">계산 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fe0-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2fe0-120">설명</span><span class="sxs-lookup"><span data-stu-id="e2fe0-120">Remarks</span></span>

<span data-ttu-id="e2fe0-121">선택 조건 최소 하나의 스크립트 또는 속성 이름을 평가 수행 하려면을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2fe0-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e2fe0-122">(선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="e2fe0-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="e2fe0-123">목록 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰에](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fe0-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2fe0-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2fe0-124">See Also</span></span>

[<span data-ttu-id="e2fe0-125">ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e2fe0-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="e2fe0-126">PropertyName SelectionCondition EmtrySelectedBy ListEntry (형식)에 대 한에 대 한 요소</span><span class="sxs-lookup"><span data-stu-id="e2fe0-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e2fe0-127">ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e2fe0-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e2fe0-128">목록 보기</span><span class="sxs-lookup"><span data-stu-id="e2fe0-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e2fe0-129">보기 항목 또는 항목에 사용 되는 경우에 대 한 조건을 정의</span><span class="sxs-lookup"><span data-stu-id="e2fe0-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e2fe0-130">Windows PowerShell 형식 지정을 작성 하 고 파일 형식</span><span class="sxs-lookup"><span data-stu-id="e2fe0-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
