---
title: ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 633204f3b181316761746ea2679910216fb74657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064104"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

이 목록 뷰의이 정의 사용 하도록 있어야 하는 조건을 정의 합니다. 목록 정의 대해 지정할 수 있는 선택 조건 수 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 ListEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy ListEntry (형식)에 대 한

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[PropertyName SelectionCondition EntrySelectedBy ListEntry (형식)에 대 한에 대 한 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 속성을 지정 합니다.|
|[EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는 스크립트를 지정 합니다.|
|[EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|선택적 요소입니다.<br /><br /> 트리거 조건이 있는.NET 형식의 집합을 지정 합니다.|
|[SelectionCondition EntrySelectedBy ListEntry (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableRowEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|이 테이블 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="remarks"></a>설명

lWhen 선택 조건을 정의 하는, 다음 요구 사항을 적용 합니다.

- 선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

목록 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[ListEntry 요소 (형식)](./listentry-element-for-listcontrol-format.md)

[ListEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[EntrySelectedBy ListEntry (형식)에 대 한 TypeName 요소](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
