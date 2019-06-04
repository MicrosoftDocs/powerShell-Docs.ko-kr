---
title: TableControl (형식)에 대 한 TableColumnItem에 대 한 맞춤 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066943"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl의 TableColumnItem에 대한 Alignment 요소(형식)

데이터 행의 열에 표시 되는 방식을 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) TableColumnItems 요소 (형식) TableColumnItem 요소 (형식) TableColumnItem (형식)에 대 한 맞춤 요소

## <a name="syntax"></a>구문

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Alignment` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableColumnItem 요소 (형식)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|레이블, 너비 및 테이블의 열에 대 한 데이터의 맞춤을 정의합니다.|

## <a name="text-value"></a>텍스트 값

다음 값 중 하나를 지정 합니다. (이 값은 대/소문자 구분 합니다.)

왼쪽된 시프트 왼쪽 열에 표시 되는 데이터입니다. (이 경우 기본이이 요소가 지정 되지 않은 경우)

오른쪽 시프트 오른쪽 열에 표시 되는 데이터입니다.

열에 표시 되는 데이터 센터를 center입니다.

## <a name="remarks"></a>설명

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰](./creating-a-table-view.md)합니다.

## <a name="see-also"></a>참고 항목

[테이블 뷰](./creating-a-table-view.md)

[TableColumnItem 요소 (형식)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
