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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855649"
---
# <a name="defining-conditions-for-displaying-data"></a>데이터 표시 조건 정의

뷰 또는 컨트롤에서 표시 되는 데이터를 정의할 때는 데이터를 표시할 수 있어야 하는 조건을 지정할 수 있습니다. 특정 속성에 의해 또는 때 스크립트를 조건이 트리거할 수 있습니다 또는 평가 하는 속성 값 `true`합니다. 선택 조건 충족 되 면 뷰 또는 컨트롤의 정의 사용 됩니다.

## <a name="specifying-a-selection-condition-for-a-definition"></a>정의 선택 조건 지정

뷰 또는 컨트롤에 대 한 정의 만들 때의 `EntrySelectedBy` 요소 개체 정의 사용할지 또는 어떤 조건 정의 사용할 수 있어야를 지정 하는데 사용 됩니다. 조건으로 지정 된 `SelectionCondition` 요소입니다.

다음 예제에서는 테이블 뷰의 정의 대 한 선택 조건 지정 됩니다. 정의에 지정 된 스크립트를 계산 하는 경우에이 예에서 사용할 `true`합니다.

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

뷰 또는 컨트롤의 정의 대해 지정할 수 있는 선택 조건 수 제한은 없습니다. 유일한 요구 사항은 다음과 같습니다.

- 선택 조건 하나 속성 이름 또는 스크립트를 트리거할 조건을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.

## <a name="specifying-a-selection-condition-for-an-item"></a>항목 선택 조건 지정

목록 뷰 또는 컨트롤의 항목을 포함 하 여 사용 하는 경우를 지정할 수도 있습니다는 `ItemSelectionCondition` 항목 정의의 요소입니다. 다음 예제에서는 목록 뷰 항목 선택 조건을 지정 됩니다. 이 예제에서는 해당 항목이 사용 되는 스크립트를 계산 하는 경우에 `true`합니다.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

항목에 대 한 하나의 선택 조건을 지정할 수 있습니다. 및 조건이 하나의 속성 이름 또는 스크립트를 트리거할 조건을 지정 해야 하지만 둘 다 지정할 수 없습니다.

## <a name="xml-elements"></a>XML 요소

 선택 조건을 만들려면 다음 XML 요소가 사용 됩니다.

- 다음 요소를 뷰 정의 대 한 선택 조건을 지정합니다.

    - [TableControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [WideControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [CustomControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- 다음 요소 선택을 지정 일반적인 조건 및 보기 정의 제어 합니다.

    - [구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- 다음 요소에는 컬렉션 개체를 확장 하는 것에 대 한 선택 조건을 지정 합니다.

    - [EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 다음 요소에는 데이터의 새 그룹을 표시 하는 것에 대 한 선택 조건을 지정 합니다.

    - [GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- 다음 요소는 목록 보기에 대 한 항목 선택 조건을 지정합니다.

    - [ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- 다음 요소를 컨트롤에 대 한 항목 선택 조건을 지정합니다.

    - [구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [ExpressionBinding CustomControl (형식)에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
