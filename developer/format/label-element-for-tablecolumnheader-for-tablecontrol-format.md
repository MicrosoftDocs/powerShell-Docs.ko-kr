---
title: TableControl (형식)에 대 한 TableColumnHeader 요소 레이블에 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856089"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl의 TableColumnHeader에 대한 Label 요소(형식)

열의 맨 위에 있는 표시 되는 레이블을 정의 합니다. 이 요소는 테이블 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableHeaders 요소 TableHeaders TableControl (형식) 레이블 요소에 대 한 TableControl (형식) TableColumnHeader 요소에 TableColumnHeader TablControl (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Label` 요소입니다. 각 열에 대해 하나의 레이블만 허용 됩니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableHeaders TableColumnHeader 요소](./tablecolumnheader-element-format.md)|레이블, 너비 및 테이블의 열에 대 한 데이터의 맞춤을 정의합니다.|

## <a name="text-value"></a>텍스트 값

테이블의 열 위쪽에 표시 되는 텍스트를 지정 합니다. 열 레이블에 대 한 제한 없는 문자가 있습니다.

## <a name="remarks"></a>설명

레이블이 없으면 지정 된 경우 값은 행에 표시 되는 속성의 이름을 사용 됩니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

이 예제는 `TableColumnHeader` 요소 레이블을 열인지 "1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableColumnHeader 요소 (형식)](./tablecolumnheader-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
