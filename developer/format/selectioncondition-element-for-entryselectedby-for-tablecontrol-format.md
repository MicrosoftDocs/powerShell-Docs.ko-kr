---
title: TableControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075667"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

테이블 보기의이 정의에 사용할 있어야 하는 조건을 정의 합니다. 테이블 정의에 지정 될 수 있는 선택 조건 수 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 TableRowEntry (형식)에 대 한 TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소

## <a name="syntax"></a>구문

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 SelectionCondition 요소의 부모 요소를 설명합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 속성을 지정 합니다.|
|[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는 스크립트를 지정 합니다.|
|[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 트리거 조건이 있는.NET 형식의 집합을 지정 합니다.|
|[SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableRowEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|이 테이블 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="remarks"></a>설명

각 목록 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.

- 선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Windows PowerShell 형식 지정을 작성 하 고 파일 형식](./writing-a-powershell-formatting-file.md)
