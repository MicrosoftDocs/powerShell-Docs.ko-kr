---
title: 이 listcontrol (형식)의 ListItem 요소에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364812"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 ScriptBlock 요소(형식)

행에 값이 표시 되는 스크립트를 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 ListEntries의이 listcontrol (Format) ListItems 요소 이 listcontrol (Format)의 ListItem 요소에 대 한 ListItems for이 listcontrol (format)이 listcontrol 요소에 대 한 for (format) ListItem 요소

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `ScriptBlock` 요소의 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListItem 요소 (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

해당 값이 행에 표시 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하면 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소를 지정할 수 없습니다.

목록 뷰에서 스크립트를 지정 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 값이 표시 되는 속성을 지정 하는 방법을 보여 줍니다.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>참고 항목

[이 listcontrol의 ListItem 요소에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[목록 보기 만들기](./creating-a-list-view.md)

[이 listcontrol에 대 한 ListItems의 ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
