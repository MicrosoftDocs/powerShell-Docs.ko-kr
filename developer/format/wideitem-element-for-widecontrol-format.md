---
title: WideItem 요소 WideControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083640"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideControl에 대한 WideItem 요소(형식)

속성 또는 해당 값이 표시 되는 스크립트를 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) WideItem 요소 (형식)

## <a name="syntax"></a>구문

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideItem` 요소입니다. `FormatString` 요소는 선택 사항입니다. 그러나 지정 해야 합니다는 `PropertyName` 또는 `ScriptBlock` 있지만 요소를 모두 지정할 수 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideControl (형식)에 대 한 WideItem FormatString 요소](./formatstring-element-for-wideitem-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 속성 또는 스크립트 값 보기에 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.|
|[WideItem (형식)에 대 한 PropertyName 요소](./propertyname-element-for-wideitem-for-widecontrol-format.md)|값은 넓은 보기에서 표시 된 개체의 속성을 지정 합니다.|
|[WideItem (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|값을 갖는 넓은 보기에 표시 됩니다 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry 요소 (형식)](./wideentry-element-for-widecontrol-format.md)|넓은 보기의 정의 제공 합니다.|

## <a name="remarks"></a>설명

넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [와이드 보기인 경우](./creating-a-wide-view.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `WideEntry` 단일 정의 하는 요소 `WideItem` 요소입니다. `WideItem` 속성 또는 값 보기에 표시 되는 스크립트 요소를 정의 합니다.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

## <a name="see-also"></a>참고 항목

[WideControl (형식)에 대 한 WideItem FormatString 요소](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[WideItem (형식)에 대 한 PropertyName 요소](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[WideItem (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry 요소 (형식)](./wideentry-element-for-widecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
