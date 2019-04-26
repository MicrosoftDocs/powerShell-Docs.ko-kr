---
title: 데이터를 표시 하기 위한 조건을 정의 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066331"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="e026d-102">데이터 표시 조건 정의</span><span class="sxs-lookup"><span data-stu-id="e026d-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="e026d-103">뷰 또는 컨트롤에서 표시 되는 데이터를 정의할 때는 데이터를 표시할 수 있어야 하는 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="e026d-104">특정 속성에 의해 또는 때 스크립트를 조건이 트리거할 수 있습니다 또는 평가 하는 속성 값 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="e026d-105">선택 조건 충족 되 면 뷰 또는 컨트롤의 정의 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="e026d-106">정의 선택 조건 지정</span><span class="sxs-lookup"><span data-stu-id="e026d-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="e026d-107">뷰 또는 컨트롤에 대 한 정의 만들 때의 `EntrySelectedBy` 요소 개체 정의 사용할지 또는 어떤 조건 정의 사용할 수 있어야를 지정 하는데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="e026d-108">조건으로 지정 된 `SelectionCondition` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="e026d-109">다음 예제에서는 테이블 뷰의 정의 대 한 선택 조건 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="e026d-110">정의에 지정 된 스크립트를 계산 하는 경우에이 예에서 사용할 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="e026d-111">뷰 또는 컨트롤의 정의 대해 지정할 수 있는 선택 조건 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="e026d-112">유일한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-112">The only requirements are the following:</span></span>

- <span data-ttu-id="e026d-113">선택 조건 하나 속성 이름 또는 스크립트를 트리거할 조건을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="e026d-114">선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="e026d-115">항목 선택 조건 지정</span><span class="sxs-lookup"><span data-stu-id="e026d-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="e026d-116">목록 뷰 또는 컨트롤의 항목을 포함 하 여 사용 하는 경우를 지정할 수도 있습니다는 `ItemSelectionCondition` 항목 정의의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="e026d-117">다음 예제에서는 목록 뷰 항목 선택 조건을 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="e026d-118">이 예제에서는 해당 항목이 사용 되는 스크립트를 계산 하는 경우에 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="e026d-119">항목에 대 한 하나의 선택 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="e026d-120">및 조건이 하나의 속성 이름 또는 스크립트를 트리거할 조건을 지정 해야 하지만 둘 다 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="e026d-121">XML 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-121">XML Elements</span></span>

 <span data-ttu-id="e026d-122">선택 조건을 만들려면 다음 XML 요소가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="e026d-123">다음 요소를 뷰 정의 대 한 선택 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="e026d-124">TableControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="e026d-125">ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="e026d-126">WideControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="e026d-127">CustomControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="e026d-128">다음 요소 선택을 지정 일반적인 조건 및 보기 정의 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="e026d-129">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="e026d-130">뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="e026d-131">다음 요소에는 컬렉션 개체를 확장 하는 것에 대 한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="e026d-132">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="e026d-133">다음 요소에는 데이터의 새 그룹을 표시 하는 것에 대 한 선택 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="e026d-134">GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="e026d-135">다음 요소는 목록 보기에 대 한 항목 선택 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="e026d-136">ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="e026d-137">다음 요소를 컨트롤에 대 한 항목 선택 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e026d-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="e026d-138">구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="e026d-139">뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="e026d-140">ExpressionBinding CustomControl (형식)에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="e026d-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="e026d-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e026d-141">See Also</span></span>

[<span data-ttu-id="e026d-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="e026d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
