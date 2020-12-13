---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl의 TableColumnItem에 대한 Alignment 요소(형식)
description: TableControl의 TableColumnItem에 대한 Alignment 요소(형식)
ms.openlocfilehash: d2bb81ff894cad44e16212891faffd22ee627383
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646115"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl의 TableColumnItem에 대한 Alignment 요소(형식)

행의 열에 있는 데이터를 표시 하는 방법을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl element (format) TableRowEntries element (format) TableRowEntry Element (format) TableColumnItems Element (format) TableColumnItem 요소 (format) Alignment 요소 (format)

## <a name="syntax"></a>구문

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Alignment` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableColumnItem 요소 (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

다음 값 중 하나를 지정 합니다. 이러한 값은 대/소문자를 구분 하지 않습니다.

왼쪽에 열에 표시 된 데이터를 왼쪽으로 이동 합니다. 이 요소를 지정 하지 않은 경우에는 기본값입니다.

열에 표시 되는 데이터를 오른쪽으로 이동 합니다.

가운데 열에 표시 되는 데이터를 가운데에 맞춥니다.

## <a name="remarks"></a>설명

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[테이블 보기](./creating-a-table-view.md)

[TableColumnItem 요소 (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
