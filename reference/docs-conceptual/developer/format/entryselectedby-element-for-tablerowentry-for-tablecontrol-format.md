---
title: TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 047a10fb6b38dfa8f78a7741fd50b781d4a14b6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787702"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>TableControl의 TableRowEntry에 대한 EntrySelectedBy 요소(형식)

이 정의를 사용 하기 위해 존재 해야 하는 조건 또는이 테이블 뷰의 정의를 사용 하는 .NET 형식을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (format)

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 이 테이블 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 이 테이블 뷰 정의를 사용 하는 .NET 유형 집합을 지정 합니다.|
|[TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 이 테이블 뷰 정의를 사용 하는 .NET 유형을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl에 대 한 TableRowEntry 요소 (형식)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|테이블의 행에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

테이블 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다 `true` . 선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `TableRowEntry` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 표시 하는 데 사용 되는 요소를 보여 줍니다.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[TableControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableControl에 대 한 TableRowEntry 요소 (형식)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TableControl의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
