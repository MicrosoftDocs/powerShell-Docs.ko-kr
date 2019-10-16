---
title: TableControl에 대 한 TableRowEntries 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368152"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableControl에 대한 TableRowEntries 요소(형식)

테이블의 행을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element for TableControl (Format)

## <a name="syntax"></a>구문

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `TableRowEntries` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl의 TableRowEntries 요소에 대 한 TableRowEntry 요소 (형식)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|필수 요소입니다.<br /><br /> 테이블의 행에 표시 되는 데이터를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl 요소 (Format)](./tablecontrol-element-format.md)|뷰의 테이블 형식을 정의 합니다.|

## <a name="remarks"></a>설명

테이블 뷰에 대해 하나 이상의 `TableRowEntry` 요소를 지정 해야 합니다. 추가할 수 있는 `TableRowEntry` 요소 수에는 제한이 없으며 순서는 중요 하지 않습니다.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 두 속성 값을 표시 하는 행을 정의 하는 `TableRowEntries` 요소를 보여 줍니다.

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl 요소 (Format)](./tablecontrol-element-format.md)

[TableRowEntry 요소 (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
