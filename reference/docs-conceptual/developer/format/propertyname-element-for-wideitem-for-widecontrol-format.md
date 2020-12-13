---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 WideItem에 대한 PropertyName 요소(형식)
description: WideControl의 WideItem에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665620"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>WideControl의 WideItem에 대한 PropertyName 요소(형식)

넓은 보기에 값이 표시 되는 개체의 속성을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl element (format) WideEntries element (format) WideEntry element (format) WideItem Element (format) PropertyName Element for WideItem (Format)

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideItem 요소 (Format)](./wideitem-element-for-widecontrol-format.md)|값이 넓은 뷰에 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

값이 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 ProcessName 개체의 속성 값을 표시 하는 넓은 보기를 보여 [줍니다.](/dotnet/api/System.Diagnostics.Process)

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>참고 항목

[WideItem 요소 (Format)](./wideitem-element-for-widecontrol-format.md)

[넓게 보기 만들기](./creating-a-wide-view.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
