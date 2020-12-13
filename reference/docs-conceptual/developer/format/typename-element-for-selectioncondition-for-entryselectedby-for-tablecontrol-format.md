---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)
description: TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)
ms.openlocfilehash: 66e90ab33775cf35d5e98e45266996d2d1a622d7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659638"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)

조건을 트리거하는 .NET 유형을 지정 합니다. 이 형식이 있으면 조건이 충족 되 고 테이블 행이 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소에 대 한 TableRowEntry (format) SelectionCondition 요소에 대해 TableRowEntry (형식)에 대 한 selectioncondition 요소

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|이 테이블 행을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .

## <a name="remarks"></a>설명

선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[데이터가 표시 되는 시점에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)

[TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
