---
title: TableHeaders 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075412"
---
# <a name="tableheaders-element-format"></a>TableHeaders 요소(형식)

테이블의 열에 대 한 헤더를 정의합니다.

TableControl (형식)에 대 한 ViewDefinitions 요소 (형식) 보기 요소 (형식) TableControl 요소 (형식) TableHeaders 요소

## <a name="syntax"></a>구문

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `TableHeaders` 요소입니다. 표시 되는 개체의 각 속성에 대 한 자식 요소 여야 합니다. 열 헤더 정보를 자식 요소에 지정 된 순서로 표시 됩니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableColumnHeader 요소 (형식)](./tablecolumnheader-element-format.md)|선택적 요소입니다.<br /><br /> 레이블, 너비 및 테이블 뷰의 열에 대 한 데이터의 맞춤을 정의합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl 요소 (형식)](./tablecontrol-element-format.md)|보기에 대 한 테이블 형식으로 정의합니다.|

## <a name="remarks"></a>설명

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

이 예제는 `TableHeaders` 두 열 헤더를 정의 하는 요소입니다.

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

[TableColumnHeader 요소 (형식)](./tablecolumnheader-element-format.md)

[TableControl 요소 (형식)](./tablecontrol-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
