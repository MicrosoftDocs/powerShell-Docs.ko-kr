---
title: TableControl (형식)에 대 한 TableColumnHeader에 대 한 맞춤 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853759"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl의 TableColumnHeader에 대한 Alignment 요소(형식)

열 머리글의 데이터가 표시 되는 방식을 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableHeaders 요소 (형식) TableColumnHeader 요소 (형식) 맞춤 요소 TableColumnHeader (형식)에 대 한

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
|[TableColumnHeader 요소 (형식)](./tablecolumnheader-element-format.md)|레이블, 너비 및 테이블의 열에 대 한 데이터의 맞춤을 정의합니다.|

## <a name="text-value"></a>텍스트 값

다음 값 중 하나를 지정 합니다. 이러한 값은 대/소문자 구분 하지 않습니다.

왼쪽 맞춤 하는 왼쪽 열에 데이터 표시 이것이 기본값이이 요소가 지정 되지 않은 경우입니다.

오른쪽 열에 데이터 표시 오른쪽에 맞춥니다.

열에 표시 되는 데이터 센터를 center입니다.

## <a name="remarks"></a>설명

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

이 예제는 `TableColumnHeader` 요소 데이터 왼쪽에 맞춰집니다.

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
