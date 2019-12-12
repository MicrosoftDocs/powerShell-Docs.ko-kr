---
title: TableControl (형식)의 TableColumnHeader에 대 한 Label 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365172"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl의 TableColumnHeader에 대한 Label 요소(형식)

열 맨 위에 표시 되는 레이블을 정의 합니다. 이 요소는 테이블 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableColumnHeader 요소에 대 한 TableControl의 tableheaders 요소 TableControl에 대 한 TableColumnHeader (형식)

## <a name="syntax"></a>구문

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `Label` 요소의 부모 요소에 대해 설명 합니다. 각 열에는 하나의 레이블만 사용할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소](./tablecolumnheader-element-format.md)|테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

테이블의 열 맨 위에 표시 되는 텍스트를 지정 합니다. 열 레이블에 대해 제한 된 문자가 없습니다.

## <a name="remarks"></a>설명

레이블이 지정 되지 않은 경우 행에 값이 표시 되는 속성의 이름이 사용 됩니다.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예에서는 레이블이 "열 1" 인 `TableColumnHeader` 요소를 보여 줍니다.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableColumnHeader 요소 (Format)](./tablecolumnheader-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
