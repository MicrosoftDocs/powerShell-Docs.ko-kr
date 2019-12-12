---
title: WideControl (형식)의 경우 EntrySelectedBy의 SelectionCondition에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368562"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="31e4a-102">WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31e4a-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="31e4a-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31e4a-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="31e4a-104">이 스크립트가 `true`평가 되 면 조건이 충족 되 고 넓은 항목 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31e4a-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="31e4a-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (Format) SelectionCondition 요소 WideEntry (형식)에 대 한 EntrySelectedBy에 대 한 WideEntry (Format) ScriptBlock 요소의 EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="31e4a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31e4a-106">구문</span><span class="sxs-lookup"><span data-stu-id="31e4a-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31e4a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="31e4a-107">Attributes and Elements</span></span>

<span data-ttu-id="31e4a-108">다음 섹션에서는 특성, 자식 요소 및 `ScriptBlock` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="31e4a-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31e4a-109">특성</span><span class="sxs-lookup"><span data-stu-id="31e4a-109">Attributes</span></span>

<span data-ttu-id="31e4a-110">없음</span><span class="sxs-lookup"><span data-stu-id="31e4a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31e4a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="31e4a-111">Child Elements</span></span>

<span data-ttu-id="31e4a-112">없음</span><span class="sxs-lookup"><span data-stu-id="31e4a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31e4a-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="31e4a-113">Parent Elements</span></span>

|<span data-ttu-id="31e4a-114">요소</span><span class="sxs-lookup"><span data-stu-id="31e4a-114">Element</span></span>|<span data-ttu-id="31e4a-115">설명</span><span class="sxs-lookup"><span data-stu-id="31e4a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31e4a-116">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="31e4a-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="31e4a-117">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31e4a-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31e4a-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="31e4a-118">Text Value</span></span>

<span data-ttu-id="31e4a-119">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31e4a-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="31e4a-120">설명</span><span class="sxs-lookup"><span data-stu-id="31e4a-120">Remarks</span></span>

<span data-ttu-id="31e4a-121">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31e4a-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="31e4a-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31e4a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="31e4a-123">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="31e4a-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31e4a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31e4a-124">See Also</span></span>

[<span data-ttu-id="31e4a-125">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="31e4a-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="31e4a-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="31e4a-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="31e4a-127">WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="31e4a-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="31e4a-128">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="31e4a-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="31e4a-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="31e4a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
