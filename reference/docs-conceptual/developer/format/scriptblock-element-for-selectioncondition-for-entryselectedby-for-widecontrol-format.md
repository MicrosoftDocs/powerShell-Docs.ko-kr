---
title: WideControl (형식)의 경우 EntrySelectedBy의 SelectionCondition에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8f2223d4a1217786a930eb82390c24b81d2f72e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787617"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="4d974-102">WideControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4d974-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="4d974-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d974-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="4d974-104">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 넓은 항목 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d974-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="4d974-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) SelectionCondition 요소에 대해 WideEntry (형식)에 대 한 SelectionCondition for WideEntry (형식)에 대 한 SelectionCondition의 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="4d974-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d974-106">구문</span><span class="sxs-lookup"><span data-stu-id="4d974-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d974-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4d974-107">Attributes and Elements</span></span>

<span data-ttu-id="4d974-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="4d974-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d974-109">특성</span><span class="sxs-lookup"><span data-stu-id="4d974-109">Attributes</span></span>

<span data-ttu-id="4d974-110">없음</span><span class="sxs-lookup"><span data-stu-id="4d974-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d974-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4d974-111">Child Elements</span></span>

<span data-ttu-id="4d974-112">없음</span><span class="sxs-lookup"><span data-stu-id="4d974-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4d974-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4d974-113">Parent Elements</span></span>

|<span data-ttu-id="4d974-114">요소</span><span class="sxs-lookup"><span data-stu-id="4d974-114">Element</span></span>|<span data-ttu-id="4d974-115">설명</span><span class="sxs-lookup"><span data-stu-id="4d974-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d974-116">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="4d974-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="4d974-117">이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d974-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4d974-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4d974-118">Text Value</span></span>

<span data-ttu-id="4d974-119">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d974-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d974-120">설명</span><span class="sxs-lookup"><span data-stu-id="4d974-120">Remarks</span></span>

<span data-ttu-id="4d974-121">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d974-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="4d974-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d974-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4d974-123">넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d974-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d974-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d974-124">See Also</span></span>

[<span data-ttu-id="4d974-125">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="4d974-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4d974-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="4d974-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4d974-127">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4d974-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="4d974-128">WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="4d974-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4d974-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4d974-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
