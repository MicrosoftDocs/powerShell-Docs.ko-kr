---
title: WideControl (Format)의 WideItem에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362032"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>WideControl의 WideItem에 대한 ScriptBlock 요소(형식)

넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries element (format) WideEntry Element (format) WideItem element (format) ScriptBlock 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `ScriptBlock` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideItem 요소 (Format)](./wideitem-element-for-widecontrol-format.md)|값이 넓은 뷰에 표시 되는 속성 또는 스크립트 블록을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

값이 표시 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 값이 뷰에 표시 되는 스크립트를 정의 하는 `WideItem` 요소를 보여 줍니다.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>참고 항목

[WideItem 요소 (Format)](./wideitem-element-for-widecontrol-format.md)

[넓은 뷰 만들기](./creating-a-wide-view.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
