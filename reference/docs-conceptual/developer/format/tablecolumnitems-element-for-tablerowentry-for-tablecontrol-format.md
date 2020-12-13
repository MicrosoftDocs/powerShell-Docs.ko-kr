---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)
description: TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667762"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)

값이 행에 표시 되는 속성 또는 스크립트를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format) TableControl Element (format) TableRowEntries Element for TableRowEntries for TableControl (format) TableColumnItems 요소의 TableControlEntry for TableControl (Format)

## <a name="syntax"></a>구문

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableColumnItems` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|필수적 요소입니다.<br /><br /> 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|테이블의 행에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

`TableColumnItem`행의 각 열에 요소가 필요 합니다. 첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `TableColumnItems` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 세 가지 속성을 정의 하는 요소를 보여 줍니다.

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[TableColumnItem 요소 (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry 요소 (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
