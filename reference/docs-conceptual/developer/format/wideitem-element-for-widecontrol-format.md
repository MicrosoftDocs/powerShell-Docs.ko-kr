---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl에 대한 WideItem 요소(형식)
description: WideControl에 대한 WideItem 요소(형식)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647810"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideControl에 대한 WideItem 요소(형식)

값이 표시 되는 속성 또는 스크립트를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries element (format) WideEntry Element (format) WideItem Element (format)

## <a name="syntax"></a>구문

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `WideItem` . `FormatString` 요소는 선택적입니다. 그러나 또는 요소를 지정 해야 `PropertyName` `ScriptBlock` 하지만 둘 다 지정할 수는 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideControl의 WideItem에 대한 FormatString 요소(형식)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.|
|[WideItem에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|넓은 보기에 값이 표시 되는 개체의 속성을 지정 합니다.|
|[WideItem에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|넓은 보기에 값이 표시 되는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry 요소 (Format)](./wideentry-element-for-widecontrol-format.md)|넓은 뷰의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide view](./creating-a-wide-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `WideEntry` 단일 요소를 정의 하는 요소를 보여 줍니다 `WideItem` . `WideItem`요소는 값이 뷰에 표시 되는 속성이 나 스크립트를 정의 합니다.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[WideControl의 WideItem에 대한 FormatString 요소(형식)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[WideItem에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[WideItem에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry 요소 (Format)](./wideentry-element-for-widecontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
