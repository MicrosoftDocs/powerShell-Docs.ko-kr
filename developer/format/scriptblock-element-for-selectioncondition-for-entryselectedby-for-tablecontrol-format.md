---
title: TableControl (형식)에 대 한 EntrySelectedBy에 대 한 SelectionCondition ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076347"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="1ab29-102">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1ab29-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="1ab29-103">조건이 트리거하는 스크립트 블록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="1ab29-104">이 스크립트를 계산할 때 `true`조건이 충족 되 고 테이블 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="1ab29-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 TableRowEntry (형식)에 대 한 EntrySelectedBy EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소 TableRowEntry (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ab29-106">구문</span><span class="sxs-lookup"><span data-stu-id="1ab29-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ab29-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-107">Attributes and Elements</span></span>

<span data-ttu-id="1ab29-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ab29-109">특성</span><span class="sxs-lookup"><span data-stu-id="1ab29-109">Attributes</span></span>

<span data-ttu-id="1ab29-110">없음</span><span class="sxs-lookup"><span data-stu-id="1ab29-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ab29-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-111">Child Elements</span></span>

<span data-ttu-id="1ab29-112">없음</span><span class="sxs-lookup"><span data-stu-id="1ab29-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ab29-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-113">Parent Elements</span></span>

|<span data-ttu-id="1ab29-114">요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-114">Element</span></span>|<span data-ttu-id="1ab29-115">설명</span><span class="sxs-lookup"><span data-stu-id="1ab29-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ab29-116">TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1ab29-117">사용할이 테이블 엔트리에 대해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ab29-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1ab29-118">Text Value</span></span>

<span data-ttu-id="1ab29-119">계산 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ab29-120">설명</span><span class="sxs-lookup"><span data-stu-id="1ab29-120">Remarks</span></span>

<span data-ttu-id="1ab29-121">선택 조건 하나 이상의 스크립트 블록 또는 속성 이름을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="1ab29-122">선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1ab29-123">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ab29-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ab29-124">See Also</span></span>

[<span data-ttu-id="1ab29-125">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="1ab29-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1ab29-126">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ab29-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1ab29-127">EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="1ab29-128">TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="1ab29-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1ab29-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1ab29-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
