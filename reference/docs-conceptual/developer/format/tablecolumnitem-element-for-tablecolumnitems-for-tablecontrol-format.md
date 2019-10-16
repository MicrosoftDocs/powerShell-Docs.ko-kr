---
title: TableColumnItems의 TableControl 요소에 대 한 TableColumnItem 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368232"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)

행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries 요소에 대 한 TableControl (format) TableRowEntry Element for TableRowEntries (Format) TableColumnItems에 대 한 TableControlEntry for TableControl (Format) TableColumnItem 요소에 대 한 TableColumnItems 요소 (형식)

## <a name="syntax"></a>구문

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `TableColumnItem` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl에 대 한 TableColumnItem의 Alignment 요소 (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 행의 열에 있는 데이터를 표시 하는 방법을 정의 합니다.|
|[TableControl의 TableColumnItem에 대 한 FormatString 요소 (형식)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|행의 열에 있는 데이터의 서식을 지정 하는 데 사용 되는 형식 패턴을 지정 합니다.|
|[TableControl의 TableColumnItem에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 값이 표시 되는 속성의 이름을 지정 합니다.|
|[TableControl의 TableColumnItem에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 행의 열에 값이 표시 되는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl의 TableControlEntry 요소에 대 한 TableColumnItems 요소 (형식)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="remarks"></a>설명

행의 각 열에 개체 또는 스크립트의 속성을 지정할 수 있습니다. 자식 요소가 지정 되지 않은 경우 해당 항목은 자리 표시자 이며 데이터는 표시 되지 않습니다.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 `Status` 속성 값을 표시 하는 `TableColumnItem` 요소를 보여 줍니다.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl에 대 한 TableColumnItem의 Alignment 요소 (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems 요소 (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl의 TableColumnItem에 대 한 FormatString 요소 (형식)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl의 TableColumnItem에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl의 TableColumnItem에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
