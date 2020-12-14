---
ms.date: 09/13/2016
ms.topic: reference
title: TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
description: TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: dcb59fc438ae217870566f09204fb16b8f031614
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665790"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="6f875-103">TableRowEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6f875-103">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="6f875-104">조건을 트리거하는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f875-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="6f875-105">이 속성이 존재 하거나로 평가 될 때 `true` 조건이 충족 되 고 테이블 항목이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f875-105">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="6f875-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy for TableRowEntry (format) PropertyName 요소에 대해 TableRowEntry (형식)에 대 한 SelectionCondition for (형식)에 대 한 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="6f875-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6f875-107">구문</span><span class="sxs-lookup"><span data-stu-id="6f875-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f875-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6f875-108">Attributes and Elements</span></span>

<span data-ttu-id="6f875-109">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="6f875-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f875-110">특성</span><span class="sxs-lookup"><span data-stu-id="6f875-110">Attributes</span></span>

<span data-ttu-id="6f875-111">없음</span><span class="sxs-lookup"><span data-stu-id="6f875-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f875-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6f875-112">Child Elements</span></span>

<span data-ttu-id="6f875-113">없음</span><span class="sxs-lookup"><span data-stu-id="6f875-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6f875-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6f875-114">Parent Elements</span></span>

|<span data-ttu-id="6f875-115">요소</span><span class="sxs-lookup"><span data-stu-id="6f875-115">Element</span></span>|<span data-ttu-id="6f875-116">설명</span><span class="sxs-lookup"><span data-stu-id="6f875-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f875-117">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="6f875-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="6f875-118">이 테이블 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f875-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6f875-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="6f875-119">Text Value</span></span>

<span data-ttu-id="6f875-120">.NET 속성 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f875-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f875-121">설명</span><span class="sxs-lookup"><span data-stu-id="6f875-121">Remarks</span></span>

<span data-ttu-id="6f875-122">선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f875-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="6f875-123">선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f875-123">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6f875-124">테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f875-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f875-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f875-125">See Also</span></span>

[<span data-ttu-id="6f875-126">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="6f875-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6f875-127">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="6f875-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6f875-128">TableRowEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="6f875-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6f875-129">TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="6f875-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6f875-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="6f875-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
