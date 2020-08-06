---
title: TableControl (형식)의 TableColumnHeader에 대 한 Label 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b7b1d6825d3bca0e36b230415d19c2ac48377a46
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785747"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl의 TableColumnHeader에 대한 Label 요소(형식)

열 맨 위에 표시 되는 레이블을 정의 합니다. 이 요소는 테이블 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableControl (format)의 tableheaders 요소에 대 한 TableColumnHeader 요소에 대 한 TableControl (format) Label 요소 for TableColumnHeader (Format)

## <a name="syntax"></a>구문

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Label` . 각 열에는 하나의 레이블만 사용할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소](./tablecolumnheader-element-format.md)|테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

테이블의 열 맨 위에 표시 되는 텍스트를 지정 합니다. 열 레이블에 대해 제한 된 문자가 없습니다.

## <a name="remarks"></a>설명

레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예에서는 `TableColumnHeader` 레이블이 "열 1" 인 요소를 보여 줍니다.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[TableColumnHeader 요소(형식)](./tablecolumnheader-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
