---
title: TableColumnHeader 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361852"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader 요소(형식)

테이블의 열에 대 한 레이블, 열의 너비 및 레이블의 맞춤을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableHeaders 요소에 대 한 TableControl (format) TableColumnHeader 요소 (형식)의 tableheaders 요소

## <a name="syntax"></a>구문

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `TableColumnHeader` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)의 TableColumnHeader에 대 한 Label 요소](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 열 맨 위에 표시 되는 레이블을 정의 합니다. 레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.|
|[TableControl의 TableColumnHeader에 대 한 Width 요소 (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|필수 요소입니다.<br /><br /> 열의 너비 (문자)를 지정 합니다.|
|[TableControl에 대 한 TableColumnHeader의 Alignment 요소 (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 열의 레이블을 표시 하는 방법을 지정 합니다. 맞춤을 지정 하지 않으면 레이블은 왼쪽에 정렬 됩니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableHeaders 요소 (Format)](./tableheaders-element-format.md)|테이블 뷰의 열을 정의 합니다.|

## <a name="remarks"></a>설명

테이블의 각 열에 대 한 헤더를 지정 합니다. 열은 `TableColumnHeader` 요소가 정의 된 순서 대로 표시 됩니다.

테이블의 @no__t 요소 수는 `TableRowEntry` 개 요소와 동일 해야 합니다. 열 머리글은 테이블의 위쪽에 있는 텍스트가 표시 되는 방법을 정의 합니다. 행 항목은 테이블의 행에 표시 되는 데이터를 정의 합니다.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 두 개의 `TableColumnHeader` 요소를 보여 줍니다. 첫 번째 요소는 레이블이 "열 1"이 고 너비가 16 자인 열을 정의 하며 레이블은 왼쪽에 정렬 됩니다. 두 번째 요소는 레이블이 "열 2"이 고 너비는 10 자인 열을 정의 합니다.

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

[TableControl에 대 한 TableColumnHeader의 Alignment 요소 (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl (형식)의 TableColumnHeader에 대 한 Label 요소](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableControl (형식)의 TableHeaders 요소](./tableheaders-element-format.md)

[TableControl 요소에 대 한 TableColumnHeader의 너비 (형식)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
