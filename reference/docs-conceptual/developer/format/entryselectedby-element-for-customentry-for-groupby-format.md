---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
description: GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
ms.openlocfilehash: 5af4abe081ca268699d281a1b586a584107b9a83
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652354"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)

이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (format) CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl의 경우 CustomControl에 대 한 groupby (형식) Entry Selectedby 요소에 대해 groupby (형식)

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `EntrySelectedBy` . 정의의 유형, 선택 집합 또는 선택 조건을 하나 이상 지정 해야 합니다. 사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[GroupBy의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.|
|[GroupBy의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-entryselectedby-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)](./customentry-element-for-customcontrol-for-groupby-format.md)|컨트롤의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

선택 조건은 개체가 특정 속성을 가지는 경우 나 특정 속성 값 또는 스크립트가로 평가 되는 경우와 같이 사용 될 정의에 대해 존재 해야 하는 조건을 정의 하는 데 사용 됩니다 `true` . 선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[GroupBy의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[GroupBy의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-entryselectedby-for-groupby-format.md)

[View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
