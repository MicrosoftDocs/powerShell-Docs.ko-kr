---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl에 대한 AutoSize 요소(형식)
description: WideControl에 대한 AutoSize 요소(형식)
ms.openlocfilehash: 42dfae337ba8805e1ddcff4269401afdb3e281f6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650011"
---
# <a name="autosize-element-for-widecontrol-format"></a>WideControl에 대한 AutoSize 요소(형식)

데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View Element (format) WideControl Element (format) Autosize Element for WideControl (Format)

## <a name="syntax"></a>구문

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `AutoSize` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideControl 요소(형식)](./widecontrol-element-format.md)|뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.|

## <a name="remarks"></a>설명

넓은 뷰를 정의할 때는 `AutoSize` 요소나 [columnnumber](./columnnumber-element-for-widecontrol-format.md) 요소를 추가할 수 있지만 둘 다를 추가할 수는 없습니다.

넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

넓은 보기의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[WideControl에 대한 ColumnNumber 요소(형식)](./columnnumber-element-for-widecontrol-format.md)

[넓게 보기 만들기](./creating-a-wide-view.md)

[WideControl 요소(형식)](./widecontrol-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
