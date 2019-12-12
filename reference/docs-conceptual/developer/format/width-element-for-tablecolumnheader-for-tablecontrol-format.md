---
title: TableControl (형식)의 TableColumnHeader에 대 한 Width 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367872"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl의 TableColumnHeader에 대한 Width 요소(형식)

열의 너비 (문자)를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableColumnHeader Element의 TableHeaders 요소에 대 한 TableControl (Format) Width 요소의 TableHeaders TableControl에 대 한 TableColumnHeader (형식)

## <a name="syntax"></a>구문

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 열 머리글을 정의할 때 사용 되는 `Width` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (Format)의 TableHeaders에 대 한 TableColumnHeader 요소](./tablecolumnheader-element-format.md)|테이블의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

가능 하면 표시 된 속성 값의 길이 보다 큰 너비 (문자)를 지정 합니다.

## <a name="remarks"></a>설명

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 너비가 16 자인 `TableColumnHeader` 요소를 보여 줍니다.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl의 TableHeader에 대 한 TableColumnHeader 요소 (형식)](./tablecolumnheader-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
