---
title: TableControl (형식)의 TableColumnItem에 대 한 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362252"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl의 TableColumnItem에 대한 PropertyName 요소(형식)

행의 열에 값이 표시 되는 속성을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) TableColumnItems Element (format) TableColumnItem 요소 (format) TableColumnItem에 대 한 PropertyName 요소 (형식)

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

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

이 예제에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 `Status` 속성을 지정 하는 `TableColumnItem` 요소를 보여 줍니다.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[TableColumnItem 요소 (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
