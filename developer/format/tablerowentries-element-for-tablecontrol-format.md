---
title: TableControl (형식)에 대 한 TableRowEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055736"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableControl에 대한 TableRowEntries 요소(형식)

테이블의 행을 정의합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableRowEntries` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|필수 요소입니다.<br /><br /> 테이블의 행에 표시 되는 데이터를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl 요소 (형식)](./tablecontrol-element-format.md)|보기에 대 한 테이블 형식으로 정의합니다.|

## <a name="remarks"></a>설명

하나 이상 지정 해야 `TableRowEntry` 테이블 보기에 대 한 요소입니다. 수의 최대 제한은 없습니다 `TableRowEntry` 추가할 수 있는 요소와 순서는 중요 합니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `TableRowEntries` 의 두 속성의 값을 표시 하는 행을 정의 하는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.

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

[TableControl 요소 (형식)](./tablecontrol-element-format.md)

[TableRowEntry 요소 (형식)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
