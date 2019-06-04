---
title: TableControl (형식)에 대 한 TableColumnItem FormatString 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065635"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl의 TableColumnItem에 대한 FormatString 요소(형식)

테이블의 속성이 나 스크립트 값 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) TableColumnItems 요소 (형식) TableColumnItem 요소 (형식) FormatString 요소 TableColumnItem (형식)

## <a name="syntax"></a>구문

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `FormatString` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TableColumnItem 요소 (형식)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 형식을 지정 하는 데 사용 되는 패턴을 지정 합니다. 형식의 모든 속성의 값 형식을 지정 하려면이 패턴을 사용할 수 있습니다 예를 들어 [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {{0:mm}&fmt=csv}.

## <a name="remarks"></a>설명

테이블 뷰, 목록 뷰, 와이드 뷰 또는 사용자 지정 보기를 만들 때 형식 문자열을 사용할 수 있습니다. 보기에 표시 된 값 형식에 대 한 자세한 내용은 참조 하세요. [표시 된 데이터 서식 지정](./formatting-displayed-data.md)합니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[표시 되는 데이터 서식 지정](./formatting-displayed-data.md)

[TableColumnItem 요소 (형식)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
