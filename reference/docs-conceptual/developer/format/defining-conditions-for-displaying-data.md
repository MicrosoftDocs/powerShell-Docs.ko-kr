---
ms.date: 09/13/2016
ms.topic: reference
title: 데이터 표시 조건 정의
description: 데이터 표시 조건 정의
ms.openlocfilehash: 9a8b7a618da8c64de978c13b527435a2d7793677
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660312"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="cecd6-103">데이터 표시 조건 정의</span><span class="sxs-lookup"><span data-stu-id="cecd6-103">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="cecd6-104">보기 또는 컨트롤에 의해 표시 되는 데이터를 정의 하는 경우 데이터를 표시 하기 위해 존재 해야 하는 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-104">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="cecd6-105">조건은 특정 속성에 의해 트리거하거나 스크립트나 속성 값이로 평가 될 때 트리거될 수 있습니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="cecd6-105">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="cecd6-106">선택 조건이 충족 되 면 뷰나 컨트롤의 정의가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-106">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="cecd6-107">정의에 대 한 선택 조건 지정</span><span class="sxs-lookup"><span data-stu-id="cecd6-107">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="cecd6-108">뷰 또는 컨트롤에 대 한 정의를 만들 때 `EntrySelectedBy` 요소는 정의를 사용할 개체를 지정 하는 데 사용 되거나 정의를 사용할 조건을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-108">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="cecd6-109">조건은 요소에 의해 지정 됩니다 `SelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="cecd6-109">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="cecd6-110">다음 예에서는 테이블 뷰 정의에 대 한 선택 조건이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-110">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="cecd6-111">이 예에서는 지정 된 스크립트가로 평가 되는 경우에만 정의가 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="cecd6-111">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="cecd6-112">뷰나 컨트롤의 정의에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-112">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="cecd6-113">유일한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-113">The only requirements are the following:</span></span>

- <span data-ttu-id="cecd6-114">선택 조건은 조건을 트리거할 속성 이름 또는 스크립트를 하나 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-114">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="cecd6-115">선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-115">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="cecd6-116">항목에 대 한 선택 조건 지정</span><span class="sxs-lookup"><span data-stu-id="cecd6-116">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="cecd6-117">항목 정의에 요소를 포함 하 여 목록 뷰 또는 컨트롤의 항목을 사용 하는 경우를 지정할 수도 있습니다 `ItemSelectionCondition` .</span><span class="sxs-lookup"><span data-stu-id="cecd6-117">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="cecd6-118">다음 예에서는 목록 뷰의 항목에 대해 선택 조건이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-118">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="cecd6-119">이 예제에서 항목은 스크립트가로 평가 되는 경우에만 사용 됩니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="cecd6-119">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="cecd6-120">항목에 대해 선택 조건을 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-120">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="cecd6-121">조건에서 조건을 트리거하기 위한 속성 이름 또는 스크립트를 하나 지정 해야 하지만 둘 다 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-121">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="cecd6-122">XML 요소</span><span class="sxs-lookup"><span data-stu-id="cecd6-122">XML Elements</span></span>

 <span data-ttu-id="cecd6-123">다음 XML 요소는 선택 조건을 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-123">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="cecd6-124">다음 요소는 뷰 정의에 대 한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-124">The following elements specify selection conditions for view definitions:</span></span>

  - [<span data-ttu-id="cecd6-125">TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-125">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="cecd6-126">ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-126">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="cecd6-127">WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-127">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="cecd6-128">CustomControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-128">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="cecd6-129">다음 요소는 공용 및 뷰 컨트롤 정의의 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-129">The following elements specify selection conditions for common and view control definitions:</span></span>

  - [<span data-ttu-id="cecd6-130">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-130">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="cecd6-131">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-131">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="cecd6-132">다음 요소는 컬렉션 개체를 확장 하기 위한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-132">The following element specifies the selection condition for expanding collection objects:</span></span>

  - [<span data-ttu-id="cecd6-133">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-133">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="cecd6-134">다음 요소는 새 데이터 그룹을 표시 하기 위한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-134">The following element specifies the selection condition for displaying a new group of data:</span></span>

  - [<span data-ttu-id="cecd6-135">GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-135">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="cecd6-136">다음 요소는 목록 뷰에 대 한 항목 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-136">The following element specifies an item selection condition for a list view:</span></span>

  - [<span data-ttu-id="cecd6-137">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-137">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="cecd6-138">다음 요소는 컨트롤에 대 한 항목 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cecd6-138">The following elements specify an item selection condition for controls:</span></span>

  - [<span data-ttu-id="cecd6-139">Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-139">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="cecd6-140">View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-140">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [<span data-ttu-id="cecd6-141">CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cecd6-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="cecd6-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cecd6-142">See Also</span></span>

[<span data-ttu-id="cecd6-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="cecd6-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
