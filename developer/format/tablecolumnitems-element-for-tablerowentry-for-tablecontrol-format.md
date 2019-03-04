---
title: TableControl (형식)에 대 한 TableRowEntry TableColumnItems 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859449"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableControl의 TableRowEntry에 대한 TableColumnItems 요소(형식)

속성 또는 행의 값을 표시 하는 스크립트를 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소 TableControl (형식)에 TableControl (형식)에 대 한 TableControlEntry TableColumnItems 요소

## <a name="syntax"></a>구문

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableColumnItems` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableColumnItems TableColumnItem 요소](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|필수 요소입니다.<br /><br /> 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|테이블의 행에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

`TableColumnItem` 요소는 행의 각 열에 대 한 필요 합니다. 첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `TableColumnItems` 의 세 가지 속성을 정의 하는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.

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

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableColumnItem 요소 (형식)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry 요소 (형식)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
