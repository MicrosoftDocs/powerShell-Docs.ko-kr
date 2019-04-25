---
title: ColumnNumber 요소 WideControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066909"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>WideControl에 대한 ColumnNumber 요소(형식)

넓은 보기에 표시 된 열의 수를 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) ColumnNumber 요소 WideControl (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ColumnNumber` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideControl 요소 (형식)](./widecontrol-element-format.md)|와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다.|

## <a name="text-value"></a>텍스트 값

양의 정수 값을 지정 합니다.

## <a name="remarks"></a>설명

넓은 보기를 정의 하는 경우 추가할 수 있습니다 합니다 `AutoSize` 요소 또는 `ColumnNumber` 둘 다를 수 있지만 요소를 추가할 수 없습니다.

넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.

넓은 보기가의 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

## <a name="see-also"></a>참고 항목

[WideControl (형식)에 대 한 자동 크기 조정 요소](./autosize-element-for-widecontrol-format.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[넓은 보기 (Basic)](./wide-view-basic.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
