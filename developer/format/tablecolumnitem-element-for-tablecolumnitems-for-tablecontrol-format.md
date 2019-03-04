---
title: TableControl (형식)에 대 한 TableColumnItems TableColumnItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862419"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableControl의 TableColumnItems에 대한 TableColumnItem 요소(형식)

속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 TableControl (형식)에 대 한 TableRowEntries TableRowEntry 요소 TableControl (형식)에 TableControl (형식)에 대 한 TableColumnItems TableColumnItem 요소 TableControl (형식)에 대 한 TableControlEntry TableColumnItems 요소

## <a name="syntax"></a>구문

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableColumnItem` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableColumnItem 요소 맞춤](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 데이터 행의 열에 표시 되는 방식을 정의 합니다.|
|[TableControl (형식)에 대 한 TableColumnItem FormatString 요소](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|행의 열에 데이터의 형식을 지정 하는 데 사용 되는 형식 패턴을 지정 합니다.|
|[TableControl (형식)에 대 한 TableColumnItem PropertyName 요소](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 값은 표시 되는 속성의 이름을 지정 합니다.|
|[TableControl (형식)에 대 한 TableColumnItem ScriptBlock 요소](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 값을 갖는 행의 열에 표시 됩니다 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableControlEntry TableColumnItems 요소](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|속성 또는 행의 값을 표시 하는 스크립트를 정의 합니다.|

## <a name="remarks"></a>설명

행의 각 열에는 개체 또는 스크립트의 속성을 지정할 수 있습니다. 지정 된 자식 요소가 없는 경우 항목 자리 표시자 이며 데이터가 표시 되지 않습니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

보여 주는이 예제는 `TableColumnItem` 값을 표시 하는 요소는 `Status` 의 속성을 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl (형식)에 대 한 TableColumnItem 요소 맞춤](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems 요소 (형식)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl (형식)에 대 한 TableColumnItem FormatString 요소](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl (형식)에 대 한 TableColumnItem PropertyName 요소](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl (형식)에 대 한 TableColumnItem ScriptBlock 요소](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
