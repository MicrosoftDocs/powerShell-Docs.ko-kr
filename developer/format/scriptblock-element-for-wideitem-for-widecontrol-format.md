---
title: ScriptBlock 요소 WideControl (형식)에 대 한 WideItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064206"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>WideControl의 WideItem에 대한 ScriptBlock 요소(형식)

값을 갖는 넓은 보기에 표시 됩니다 스크립트를 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) WideItem 요소 (형식) ScriptBlock 요소 WideItem (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideItem 요소 (형식)](./wideitem-element-for-widecontrol-format.md)|값을 갖는 넓은 보기에 표시 됩니다 속성 또는 스크립트 블록을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

해당 값이 표시 하는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.

## <a name="example"></a>예제

이 예제는 `WideItem` 값인 보기에 표시 되는 스크립트를 정의 하는 요소입니다.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>참고 항목

[WideItem 요소 (형식)](./wideitem-element-for-widecontrol-format.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
