---
title: WideControl (형식)에 대 한 ColumnNumber 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5f151bb0e629efcebe6295cdcae6cebcbbb1b39b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783860"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>WideControl에 대한 ColumnNumber 요소(형식)

넓은 보기에 표시 되는 열 수를 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) ColumnNumber Element for WideControl (format)

## <a name="syntax"></a>구문

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ColumnNumber` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideControl 요소(형식)](./widecontrol-element-format.md)|뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

양의 정수 값을 지정 하십시오.

## <a name="remarks"></a>설명

넓은 뷰를 정의할 때는 `AutoSize` 요소 또는 요소를 추가할 수 `ColumnNumber` 있지만 둘 다를 추가할 수는 없습니다.

넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

넓은 보기의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[WideControl에 대 한 Autosize 요소 (형식)](./autosize-element-for-widecontrol-format.md)

[넓게 보기 만들기](./creating-a-wide-view.md)

[넓게 보기(기본)](./wide-view-basic.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
