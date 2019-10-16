---
title: WideControl (Format)의 AutoSize 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369052"
---
# <a name="autosize-element-for-widecontrol-format"></a>WideControl에 대한 AutoSize 요소(형식)

데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View Element (format) WideControl Element (format) Autosize Element for WideControl (Format)

## <a name="syntax"></a>구문

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `AutoSize` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideControl 요소 (Format)](./widecontrol-element-format.md)|뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.|

## <a name="remarks"></a>설명

넓은 뷰를 정의할 때 `AutoSize` 요소 또는 [Columnnumber](./columnnumber-element-for-widecontrol-format.md) 요소를 추가할 수 있지만 둘 다를 추가할 수는 없습니다.

넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

넓은 보기의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[WideControl에 대 한 ColumnNumber 요소 (형식)](./columnnumber-element-for-widecontrol-format.md)

[넓은 뷰 만들기](./creating-a-wide-view.md)

[WideControl 요소 (Format)](./widecontrol-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
