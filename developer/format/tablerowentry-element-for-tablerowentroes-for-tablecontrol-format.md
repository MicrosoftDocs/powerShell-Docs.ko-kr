---
title: TableControl (형식)에 대 한 TableRowEntroes TableRowEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853589"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a>TableControl의 TableRowEntries에 대한 TableRowEntry 요소(형식)

테이블의 행에 표시 되는 데이터를 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소 TableControl (형식)에

## <a name="syntax"></a>구문

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableRowEntry` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableRowEntry EntrySelectedBy 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|필수 요소입니다.<br /><br /> 속성 값은 행에 표시 되는 개체를 정의 합니다.|
|[TableControl (형식)에 대 한 TableRowEntry TableColumnItems 요소](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|필수 요소입니다.<br /><br /> 속성 또는 값을 표시 하는 스크립트를 정의 합니다.|
|[TableCntrol (형식)에 대 한 TableRowEntry 하기 위해 요소를 래핑](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|선택적 요소입니다.<br /><br /> 지정 된 열 너비를 초과 하는 텍스트가 다음 줄에 표시 됩니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableRowEntries 요소](./tablerowentries-element-for-tablecontrol-format.md)|테이블의 행을 정의합니다.|

## <a name="remarks"></a>설명

하나의 `TableColumnItems` 요소와 `EntrySelectedBy` 요소를 지정 해야 합니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `TableRowEntry` 의 두 속성의 값을 표시 하는 행을 정의 하는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.

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

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl (형식)에 대 한 TableRowEntry EntrySelectedBy 요소](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl (형식)에 대 한 TableRowEntry TableColumnItems 요소](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl (형식)에 대 한 TableRowEntries 요소](./tablerowentries-element-for-tablecontrol-format.md)

[TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[TableCntrol (형식)에 대 한 TableRowEntry 하기 위해 요소를 래핑](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
