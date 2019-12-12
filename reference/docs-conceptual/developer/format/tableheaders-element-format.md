---
title: TableHeaders 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361822"
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

다음 섹션에서는 `TableHeaders` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 표시 될 개체의 각 속성에 대 한 자식 요소가 있어야 합니다. 열 머리글 정보는 자식 요소가 지정 된 순서 대로 표시 됩니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableColumnHeader 요소 (Format)](./tablecolumnheader-element-format.md)|선택적 요소입니다.<br /><br /> 테이블 뷰의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl 요소 (Format)](./tablecontrol-element-format.md)|뷰의 테이블 형식을 정의 합니다.|

## <a name="remarks"></a>설명

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 두 개의 열 머리글을 정의 하는 `TableHeaders` 요소를 보여 줍니다.

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

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableColumnHeader 요소 (Format)](./tablecolumnheader-element-format.md)

[TableControl 요소 (Format)](./tablecontrol-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
