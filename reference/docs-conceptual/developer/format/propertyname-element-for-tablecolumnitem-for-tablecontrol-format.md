---
title: TableControl (형식)의 TableColumnItem에 대 한 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bf267eeb83aef59abea2d945af12e849252309c8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772980"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)

행의 열에 값이 표시 되는 속성을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl element (format) TableRowEntries element (format) TableRowEntry element (format) TableColumnItems element (format) TableColumnItem element (format) PropertyName Element for TableColumnItem (Format)

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableColumnItem 요소 (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

값이 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 `TableColumnItem` `Status` [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 지정 하는 요소를 보여 줍니다.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[TableColumnItem 요소 (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
