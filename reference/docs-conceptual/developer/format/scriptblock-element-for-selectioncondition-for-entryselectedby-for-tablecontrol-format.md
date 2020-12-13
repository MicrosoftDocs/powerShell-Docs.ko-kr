---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)
description: TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: a984bda6b8fba3a5cb9485576ffd847f0d366d3e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659897"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ace8b-103">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ace8b-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ace8b-104">조건을 트리거하는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ace8b-104">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="ace8b-105">이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 테이블 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ace8b-105">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="ace8b-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소에 대 한 TableRowEntry (format) SelectionCondition 요소에 대해 TableRowEntry (형식)에 대 한 SelectionCondition for TableRowEntry (형식)에 대 한 SelectionCondition의 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="ace8b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ace8b-107">구문</span><span class="sxs-lookup"><span data-stu-id="ace8b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ace8b-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ace8b-108">Attributes and Elements</span></span>

<span data-ttu-id="ace8b-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="ace8b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ace8b-110">특성</span><span class="sxs-lookup"><span data-stu-id="ace8b-110">Attributes</span></span>

<span data-ttu-id="ace8b-111">없음</span><span class="sxs-lookup"><span data-stu-id="ace8b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ace8b-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ace8b-112">Child Elements</span></span>

<span data-ttu-id="ace8b-113">없음</span><span class="sxs-lookup"><span data-stu-id="ace8b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ace8b-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ace8b-114">Parent Elements</span></span>

|<span data-ttu-id="ace8b-115">요소</span><span class="sxs-lookup"><span data-stu-id="ace8b-115">Element</span></span>|<span data-ttu-id="ace8b-116">설명</span><span class="sxs-lookup"><span data-stu-id="ace8b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ace8b-117">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ace8b-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="ace8b-118">이 테이블 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ace8b-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ace8b-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ace8b-119">Text Value</span></span>

<span data-ttu-id="ace8b-120">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ace8b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ace8b-121">설명</span><span class="sxs-lookup"><span data-stu-id="ace8b-121">Remarks</span></span>

<span data-ttu-id="ace8b-122">선택 조건은 하나 이상의 스크립트 블록이 나 속성 이름을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ace8b-122">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="ace8b-123">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ace8b-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ace8b-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ace8b-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ace8b-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ace8b-125">See Also</span></span>

[<span data-ttu-id="ace8b-126">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ace8b-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ace8b-127">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="ace8b-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ace8b-128">TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ace8b-128">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="ace8b-129">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="ace8b-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ace8b-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ace8b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
