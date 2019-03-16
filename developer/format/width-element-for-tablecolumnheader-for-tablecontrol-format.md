---
title: TableControl (형식)에 대 한 TableColumnHeader 너비 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055192"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl의 TableColumnHeader에 대한 Width 요소(형식)

너비 (문자 단위) 열을 정의합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableHeaders 요소에 대 한 너비 요소 TableControl (형식)에 대 한 TableColumnHeader 요소 TableHeaders TableControl (형식)에 대 한 TableControl (형식)에 대 한 TableColumnHeader

## <a name="syntax"></a>구문

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Width` 열 헤더를 정의할 때 사용 되는 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 TableHeaders TableColumnHeader 요소](./tablecolumnheader-element-format.md)|레이블, 너비 및 맞춤의 데이터 테이블의 열을 정의합니다.|

## <a name="text-value"></a>텍스트 값

모든 가능한에 때 표시 된 속성 값의 길이 보다 큰 문자에서 너비를 지정 합니다.

## <a name="remarks"></a>설명

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

다음 예제와 `TableColumnHeader` 너비가 16 자 하는 요소입니다.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableControl (형식)에 대 한 TableHeader TableColumnHeader 요소](./tablecolumnheader-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
