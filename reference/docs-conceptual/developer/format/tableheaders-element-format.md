---
ms.date: 09/13/2016
ms.topic: reference
title: TableHeaders 요소(형식)
description: TableHeaders 요소(형식)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659822"
---
# <a name="tableheaders-element-format"></a>TableHeaders 요소(형식)

테이블의 열에 대 한 헤더를 정의 합니다.

ViewDefinitions 요소 (Format) View 요소 (format) TableControl Element (format) TableHeaders 요소 TableControl (format)

## <a name="syntax"></a>구문

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TableHeaders` . 표시 될 개체의 각 속성에 대 한 자식 요소가 있어야 합니다. 열 머리글 정보는 자식 요소가 지정 된 순서 대로 표시 됩니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableColumnHeader 요소(형식)](./tablecolumnheader-element-format.md)|선택적 요소입니다.<br /><br /> 테이블 뷰의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl 요소(형식)](./tablecontrol-element-format.md)|뷰의 테이블 형식을 정의 합니다.|

## <a name="remarks"></a>설명

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 `TableHeaders` 두 개의 열 머리글을 정의 하는 요소를 보여 줍니다.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[TableColumnHeader 요소(형식)](./tablecolumnheader-element-format.md)

[TableControl 요소(형식)](./tablecontrol-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
