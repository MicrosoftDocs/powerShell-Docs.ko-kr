---
title: TableColumnHeader 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858599"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader 요소(형식)

레이블, 열 너비와 테이블의 열 레이블 맞춤을 정의합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableHeaders 요소 TableControl (형식)에 대 한 TableHeaders TableColumnHeader 요소 TableControl (형식)에

## <a name="syntax"></a>구문

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableColumnHeader` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableColumnHeader 레이블 요소](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 열의 맨 위에 있는 표시 되는 레이블을 정의 합니다. 레이블이 없으면 지정 된 경우 값은 행에 표시 되는 속성의 이름을 사용 됩니다.|
|[TableControl (형식)에 대 한 TableColumnHeader 너비 요소](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|필수 요소입니다.<br /><br /> 너비 (문자 단위) 열을 지정합니다.|
|[TableControl (형식)에 대 한 TableColumbnHeader 요소 맞춤](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 열 레이블이 표시 되는 방식을 지정 합니다. 맞춤 없음이 지정 된 경우 레이블 왼쪽에 맞춰집니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableHeaders 요소 (형식)](./tableheaders-element-format.md)|테이블 보기의 열을 정의합니다.|

## <a name="remarks"></a>설명

테이블의 각 열에 대 한 헤더를 지정 합니다. 열이 나타나는 순서 대로 표시 됩니다는 `TableColumnHeader` 요소를 정의 합니다.

테이블에 동일한 수 있어야 합니다. `TableColumnHeader` 요소가 `TableRowEntry` 요소입니다. 열 머리글을 테이블의 맨 위에 있는 텍스트를 표시 되는 방식을 정의 합니다. 행 항목을 테이블의 행에 표시 되는 데이터를 정의 합니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 두 개의 `TableColumnHeader` 요소입니다. 첫 번째 요소 레이블을 "열 1", 16 자 너비 및 해당 레이블 왼쪽에 맞춰집니다 열을 정의 합니다. 두 번째 요소 레이블을 가운데 열에 있는 레이블 "열인지 2", 너비가 10 자 및 열을 정의 합니다.

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

[TableColumnHeader TableContrl (형식)에 대 한 맞춤 요소](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl (형식)에 대 한 TableColumnHeader 레이블 요소](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableControl (형식)에 대 한 TableHeaders 요소](./tableheaders-element-format.md)

[TableControl 요소 (형식)에 대 한 TableColumnHeader 너비](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
