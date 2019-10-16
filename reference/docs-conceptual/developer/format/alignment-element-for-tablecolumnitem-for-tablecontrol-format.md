---
title: TableControl (형식)의 TableColumnItem에 대 한 Alignment 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369082"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl의 TableColumnItem에 대한 Alignment 요소(형식)

행의 열에 있는 데이터를 표시 하는 방법을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) TableColumnItems Element (format) TableColumnItem 요소 (format) TableColumnItem에 대 한 Alignment 요소 (Format)

## <a name="syntax"></a>구문

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `Alignment` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

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
