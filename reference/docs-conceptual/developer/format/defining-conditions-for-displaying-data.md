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
ms.openlocfilehash: 6036f30816e253b3f0c40c6b916279d0643acdb8
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692494"
---
# <a name="defining-conditions-for-displaying-data"></a>데이터 표시 조건 정의

보기 또는 컨트롤에 의해 표시 되는 데이터를 정의 하는 경우 데이터를 표시 하기 위해 존재 해야 하는 조건을 지정할 수 있습니다. 조건은 특정 속성에 의해 트리거하거나 스크립트나 속성 값이로 평가 될 때 트리거될 수 있습니다 `true` . 선택 조건이 충족 되 면 뷰나 컨트롤의 정의가 사용 됩니다.

## <a name="specifying-a-selection-condition-for-a-definition"></a>정의에 대 한 선택 조건 지정

뷰 또는 컨트롤에 대 한 정의를 만들 때 `EntrySelectedBy` 요소는 정의를 사용할 개체를 지정 하는 데 사용 되거나 정의를 사용할 조건을 지정 하는 데 사용 됩니다. 조건은 요소에 의해 지정 됩니다 `SelectionCondition` .

다음 예에서는 테이블 뷰 정의에 대 한 선택 조건이 지정 됩니다. 이 예에서는 지정 된 스크립트가로 평가 되는 경우에만 정의가 사용 됩니다 `true` .

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

뷰나 컨트롤의 정의에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다. 유일한 요구 사항은 다음과 같습니다.

- 선택 조건은 조건을 트리거할 속성 이름 또는 스크립트를 하나 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- 선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.

## <a name="specifying-a-selection-condition-for-an-item"></a>항목에 대 한 선택 조건 지정

항목 정의에 요소를 포함 하 여 목록 뷰 또는 컨트롤의 항목을 사용 하는 경우를 지정할 수도 있습니다 `ItemSelectionCondition` . 다음 예에서는 목록 뷰의 항목에 대해 선택 조건이 지정 됩니다. 이 예제에서 항목은 스크립트가로 평가 되는 경우에만 사용 됩니다 `true` .

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

항목에 대해 선택 조건을 하나만 지정할 수 있습니다. 조건에서 조건을 트리거하기 위한 속성 이름 또는 스크립트를 하나 지정 해야 하지만 둘 다 지정할 수는 없습니다.

## <a name="xml-elements"></a>XML 요소

 다음 XML 요소는 선택 조건을 만드는 데 사용 됩니다.

- 다음 요소는 뷰 정의에 대 한 선택 조건을 지정 합니다.

  - [TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [CustomControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- 다음 요소는 공용 및 뷰 컨트롤 정의의 선택 조건을 지정 합니다.

  - [Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- 다음 요소는 컬렉션 개체를 확장 하기 위한 선택 조건을 지정 합니다.

  - [EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 다음 요소는 새 데이터 그룹을 표시 하기 위한 선택 조건을 지정 합니다.

  - [GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- 다음 요소는 목록 뷰에 대 한 항목 선택 조건을 지정 합니다.

  - [ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- 다음 요소는 컨트롤에 대 한 항목 선택 조건을 지정 합니다.

  - [Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>참고 항목

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
