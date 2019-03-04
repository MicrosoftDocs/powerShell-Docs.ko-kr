---
title: ScriptBlock ListControl (형식)에 대 한 ListItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855559"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 ScriptBlock 요소(형식)

행에 해당 값이 표시 하는 스크립트를 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntries ListEntry ListItems 요소 ListControl (형식)에 대 한 (형식) ListControl ListEntry 요소에 ListItems ListControl (형식)에 대 한 ListItem ScriptBlock 요소 ListControl (형식)에 대 한 (형식) ListControl ListItem 요소에

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
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
|[ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

행에 해당 값이 표시 하는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 지정할 수 없습니다는 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소입니다.

목록 보기에서 스크립트를 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 값이 표시 되는 속성을 지정 하는 방법을 보여 줍니다.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>참고 항목

[PropertyName ListControl (형식)에 대 한 ListItem 요소](./propertyname-element-for-listitem-for-listcontrol-format.md)

[목록 뷰 만들기](./creating-a-list-view.md)

[ListItem 요소 ListItems ListControl (형식)에 대 한](./listitem-element-for-listitems-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
