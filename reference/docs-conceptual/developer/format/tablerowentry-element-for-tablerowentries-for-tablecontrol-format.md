---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)
description: TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)
ms.openlocfilehash: 60d64b7c14b40e87825ada36e19f52a66fe8b6cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659766"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)

테이블의 행에 표시 되는 데이터를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소에 대 한 TableControl (format) TableRowEntry Element for TableRowEntries (Format)

## <a name="syntax"></a>구문

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableRowEntry` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|필수적 요소입니다.<br /><br /> 해당 속성 값이 행에 표시 되는 개체를 정의 합니다.|
|[TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|필수적 요소입니다.<br /><br /> 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|
|[TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 열 너비를 초과 하는 텍스트를 다음 줄에 표시 하도록 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl에 대한 TableRowEntries 요소(형식)](./tablerowentries-element-for-tablecontrol-format.md)|테이블의 행을 정의 합니다.|

## <a name="remarks"></a>설명

`TableColumnItems`요소 하 나와 요소 하나를 `EntrySelectedBy` 지정 해야 합니다.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `TableRowEntry` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 요소를 보여 줍니다.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[TableControl (형식)의 TableRowEntry에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl에 대한 TableRowEntries 요소(형식)](./tablerowentries-element-for-tablecontrol-format.md)

[TableControl의 TableRowEntry 요소에 대 한 Wrap 요소 (형식)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
