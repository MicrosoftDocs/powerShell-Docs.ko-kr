---
title: 데이터 표시 조건 정의 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363902"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="95b2c-102">데이터 표시 조건 정의</span><span class="sxs-lookup"><span data-stu-id="95b2c-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="95b2c-103">보기 또는 컨트롤에 의해 표시 되는 데이터를 정의 하는 경우 데이터를 표시 하기 위해 존재 해야 하는 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="95b2c-104">조건은 특정 속성에 의해 트리거하거나 스크립트나 속성 값이 `true`로 평가 될 때 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="95b2c-105">선택 조건이 충족 되 면 뷰나 컨트롤의 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="95b2c-106">정의에 대 한 선택 조건 지정</span><span class="sxs-lookup"><span data-stu-id="95b2c-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="95b2c-107">뷰 또는 컨트롤에 대 한 정의를 만들 때 `EntrySelectedBy` 요소를 사용 하 여 정의를 사용할 개체 또는 정의를 사용할 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="95b2c-108">조건은 `SelectionCondition` 요소에 의해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="95b2c-109">다음 예에서는 테이블 뷰 정의에 대 한 선택 조건이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="95b2c-110">이 예에서는 지정 된 스크립트가 `true`로 평가 되는 경우에만 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="95b2c-111">뷰나 컨트롤의 정의에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="95b2c-112">유일한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-112">The only requirements are the following:</span></span>

- <span data-ttu-id="95b2c-113">선택 조건은 조건을 트리거할 속성 이름 또는 스크립트를 하나 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="95b2c-114">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="95b2c-115">항목에 대 한 선택 조건 지정</span><span class="sxs-lookup"><span data-stu-id="95b2c-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="95b2c-116">항목 정의에서 `ItemSelectionCondition` 요소를 포함 하 여 목록 뷰 또는 컨트롤의 항목을 사용 하는 경우를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="95b2c-117">다음 예에서는 목록 뷰의 항목에 대해 선택 조건이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="95b2c-118">이 예제에서 항목은 스크립트를 `true`으로 평가 하는 경우에만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="95b2c-119">항목에 대해 선택 조건을 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="95b2c-120">조건에서 조건을 트리거하기 위한 속성 이름 또는 스크립트를 하나 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="95b2c-121">XML 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-121">XML Elements</span></span>

 <span data-ttu-id="95b2c-122">다음 XML 요소는 선택 조건을 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="95b2c-123">다음 요소는 뷰 정의에 대 한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="95b2c-124">TableControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="95b2c-125">이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="95b2c-126">WideControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="95b2c-127">CustomControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="95b2c-128">다음 요소는 공용 및 뷰 컨트롤 정의의 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="95b2c-129">구성에 대 한 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95b2c-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="95b2c-130">보기의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95b2c-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="95b2c-131">다음 요소는 컬렉션 개체를 확장 하기 위한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="95b2c-132">EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="95b2c-133">다음 요소는 새 데이터 그룹을 표시 하기 위한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="95b2c-134">GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="95b2c-135">다음 요소는 목록 뷰에 대 한 항목 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="95b2c-136">이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95b2c-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="95b2c-137">다음 요소는 컨트롤에 대 한 항목 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b2c-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="95b2c-138">구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95b2c-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="95b2c-139">View 컨트롤의 ExpressionBinding에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="95b2c-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="95b2c-140">CustomControl (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="95b2c-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="95b2c-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95b2c-141">See Also</span></span>

[<span data-ttu-id="95b2c-142">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="95b2c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
