---
title: TableControl (형식)의 경우 EntrySelectedBy의 SelectionCondition에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368582"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="17a77-102">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="17a77-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="17a77-103">조건을 트리거하는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17a77-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="17a77-104">이 스크립트가 `true`평가 되 면 조건이 충족 되 고 테이블 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17a77-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="17a77-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (형식) TableRowEntry (형식)에 대 한 EntrySelectedBy TableRowEntry (Format) ScriptBlock 요소의 selectioncondition 요소에 대 한 selectioncondition 요소</span><span class="sxs-lookup"><span data-stu-id="17a77-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17a77-106">구문</span><span class="sxs-lookup"><span data-stu-id="17a77-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17a77-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="17a77-107">Attributes and Elements</span></span>

<span data-ttu-id="17a77-108">다음 섹션에서는 특성, 자식 요소 및 `ScriptBlock` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="17a77-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="17a77-109">특성</span><span class="sxs-lookup"><span data-stu-id="17a77-109">Attributes</span></span>

<span data-ttu-id="17a77-110">없음</span><span class="sxs-lookup"><span data-stu-id="17a77-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17a77-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="17a77-111">Child Elements</span></span>

<span data-ttu-id="17a77-112">없음</span><span class="sxs-lookup"><span data-stu-id="17a77-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="17a77-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="17a77-113">Parent Elements</span></span>

|<span data-ttu-id="17a77-114">요소</span><span class="sxs-lookup"><span data-stu-id="17a77-114">Element</span></span>|<span data-ttu-id="17a77-115">설명</span><span class="sxs-lookup"><span data-stu-id="17a77-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17a77-116">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="17a77-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="17a77-117">이 테이블 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="17a77-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="17a77-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="17a77-118">Text Value</span></span>

<span data-ttu-id="17a77-119">평가 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17a77-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="17a77-120">설명</span><span class="sxs-lookup"><span data-stu-id="17a77-120">Remarks</span></span>

<span data-ttu-id="17a77-121">선택 조건은 하나 이상의 스크립트 블록이 나 속성 이름을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17a77-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="17a77-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17a77-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="17a77-123">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17a77-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17a77-124">관련 항목</span><span class="sxs-lookup"><span data-stu-id="17a77-124">See Also</span></span>

[<span data-ttu-id="17a77-125">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="17a77-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="17a77-126">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="17a77-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="17a77-127">TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="17a77-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="17a77-128">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="17a77-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="17a77-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="17a77-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
