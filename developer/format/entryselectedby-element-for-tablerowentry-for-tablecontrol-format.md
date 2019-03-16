---
title: TableControl (형식)에 대 한 TableRowEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058762"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="69755-102">TableControl의 TableRowEntry에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="69755-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="69755-103">테이블 뷰 또는이 정의를 사용할 수 있어야 하는 조건을이 정의 사용 하는.NET 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="69755-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="69755-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="69755-105">구문</span><span class="sxs-lookup"><span data-stu-id="69755-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="69755-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="69755-106">Attributes and Elements</span></span>

<span data-ttu-id="69755-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="69755-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="69755-108">특성</span><span class="sxs-lookup"><span data-stu-id="69755-108">Attributes</span></span>

<span data-ttu-id="69755-109">없음</span><span class="sxs-lookup"><span data-stu-id="69755-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69755-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="69755-110">Child Elements</span></span>

|<span data-ttu-id="69755-111">요소</span><span class="sxs-lookup"><span data-stu-id="69755-111">Element</span></span>|<span data-ttu-id="69755-112">설명</span><span class="sxs-lookup"><span data-stu-id="69755-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69755-113">TableControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="69755-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="69755-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="69755-114">Optional element.</span></span><br /><br /> <span data-ttu-id="69755-115">이 테이블 뷰 정의 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="69755-116">TableControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="69755-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="69755-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="69755-117">Optional element.</span></span><br /><br /> <span data-ttu-id="69755-118">이 테이블 뷰 정의 사용 하는.NET 형식의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="69755-119">TableControl (형식)에 대 한 EntrySelectedBy TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="69755-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="69755-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="69755-120">Optional element.</span></span><br /><br /> <span data-ttu-id="69755-121">이 테이블 뷰 정의 사용 하는.NET 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="69755-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="69755-122">Parent Elements</span></span>

|<span data-ttu-id="69755-123">요소</span><span class="sxs-lookup"><span data-stu-id="69755-123">Element</span></span>|<span data-ttu-id="69755-124">설명</span><span class="sxs-lookup"><span data-stu-id="69755-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69755-125">TableControl (형식)에 대 한 TableRowEntry 요소</span><span class="sxs-lookup"><span data-stu-id="69755-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="69755-126">테이블의 행에 표시 되는 데이터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="69755-127">설명</span><span class="sxs-lookup"><span data-stu-id="69755-127">Remarks</span></span>

<span data-ttu-id="69755-128">하나 이상의 형식, 선택 항목 집합 또는 테이블 뷰 정의 대 한 선택 조건을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="69755-129">사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69755-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="69755-130">선택 조건을 사용 하 여 정의 개체의 특정 속성에 때와 같이 사용할 수 있어야 하는 조건을 정의 또는 스크립트나 특정 속성 값으로 계산 되는 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="69755-131">선택 조건에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="69755-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="69755-132">테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="69755-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="69755-133">예제</span><span class="sxs-lookup"><span data-stu-id="69755-133">Example</span></span>

<span data-ttu-id="69755-134">에서는 다음 예제는 `TableRowEntry` 의 속성을 표시 하는 데 사용 되는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="69755-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="69755-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69755-135">See Also</span></span>

[<span data-ttu-id="69755-136">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="69755-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="69755-137">TableControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="69755-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="69755-138">TableControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="69755-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="69755-139">TableControl (형식)에 대 한 TableRowEntry 요소</span><span class="sxs-lookup"><span data-stu-id="69755-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="69755-140">TableControl (형식)에 대 한 EntrySelectedBy TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="69755-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="69755-141">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="69755-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
