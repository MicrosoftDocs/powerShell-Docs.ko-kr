---
title: GroupBy (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368432"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) EntrySelectedBy 요소에 대 한 CustomControl 요소에 대 한 CustomEntry for groupby (format)의 경우 EntrySelectedBy에 대 한 요소입니다.

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

다음 섹션에서는 `SelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[GroupBy (형식)에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|
|[GroupBy (Format)의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 형식 집합을 지정 합니다.|
|[GroupBy (형식)에 대 한 SelectionCondition의 TypeName 요소](./typename-element-for-selectioncondition-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 유형을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomEntry의 EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)|이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|

## <a name="remarks"></a>설명

선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.

- 선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- 선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CustomControl에 대 한 SelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomControl에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[보기에 대 한 사용자 지정 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[GroupBy (형식)에 대 한 SelectionCondition의 TypeName 요소](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomEntry의 EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
