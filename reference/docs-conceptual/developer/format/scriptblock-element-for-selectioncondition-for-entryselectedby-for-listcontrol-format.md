---
title: 이 listcontrol (형식)의 경우 EntrySelectedBy의 SelectionCondition에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 56bd04c9af74bdaa7a186a208fc15a67cb08b004
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772861"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="6391f-102">ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6391f-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="6391f-103">조건을 트리거하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6391f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6391f-104">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6391f-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="6391f-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (format) SelectionCondition 요소에 대해 ListEntry (형식)에 대 한 SelectionCondition for ListEntry (형식)에 대 한 SelectionCondition의 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="6391f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6391f-106">구문</span><span class="sxs-lookup"><span data-stu-id="6391f-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6391f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6391f-107">Attributes and Elements</span></span>

<span data-ttu-id="6391f-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="6391f-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6391f-109">특성</span><span class="sxs-lookup"><span data-stu-id="6391f-109">Attributes</span></span>

<span data-ttu-id="6391f-110">없음</span><span class="sxs-lookup"><span data-stu-id="6391f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6391f-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6391f-111">Child Elements</span></span>

<span data-ttu-id="6391f-112">없음</span><span class="sxs-lookup"><span data-stu-id="6391f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6391f-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6391f-113">Parent Elements</span></span>

|<span data-ttu-id="6391f-114">요소</span><span class="sxs-lookup"><span data-stu-id="6391f-114">Element</span></span>|<span data-ttu-id="6391f-115">설명</span><span class="sxs-lookup"><span data-stu-id="6391f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6391f-116">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="6391f-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="6391f-117">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6391f-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6391f-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="6391f-118">Text Value</span></span>

<span data-ttu-id="6391f-119">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6391f-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6391f-120">설명</span><span class="sxs-lookup"><span data-stu-id="6391f-120">Remarks</span></span>

<span data-ttu-id="6391f-121">선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6391f-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6391f-122">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6391f-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="6391f-123">목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6391f-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6391f-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6391f-124">See Also</span></span>

[<span data-ttu-id="6391f-125">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="6391f-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="6391f-126">ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="6391f-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6391f-127">ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="6391f-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6391f-128">목록 보기</span><span class="sxs-lookup"><span data-stu-id="6391f-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6391f-129">뷰 항목이 나 항목을 사용 하는 경우 조건 정의</span><span class="sxs-lookup"><span data-stu-id="6391f-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6391f-130">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6391f-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
