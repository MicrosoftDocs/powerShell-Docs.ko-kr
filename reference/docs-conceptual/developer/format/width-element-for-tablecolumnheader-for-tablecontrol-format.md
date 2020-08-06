---
title: TableControl (형식)의 TableColumnHeader에 대 한 Width 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9540d3d351041ad7cb98a21bb360ebea7eca117
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779916"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl의 TableColumnHeader에 대한 Width 요소(형식)

열의 너비 (문자)를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) TableControl Element (format) TableColumnHeader Element의 TableHeaders 요소에 대 한 TableControl (형식) 요소 TableHeaders for TableColumnHeader for TableControl (형식)에 대 한의 Width 요소

## <a name="syntax"></a>구문

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `Width` 열 헤더를 정의할 때 사용 되는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

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

다음 예제에서는 `TableColumnHeader` 너비가 16 자인 요소를 보여 줍니다.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>참고 항목

[테이블 보기 만들기](./creating-a-table-view.md)

[TableControl의 TableHeader에 대 한 TableColumnHeader 요소 (형식)](./tablecolumnheader-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
