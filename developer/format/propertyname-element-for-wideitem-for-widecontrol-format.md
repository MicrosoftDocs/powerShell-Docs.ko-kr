---
title: PropertyName 요소 WideControl (형식)에 대 한 WideItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860959"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>WideControl의 WideItem에 대한 PropertyName 요소(형식)

값은 넓은 보기에서 표시 된 개체의 속성을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) WideItem 요소 (형식) PropertyName 요소 WideItem (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideItem 요소 (형식)](./wideitem-element-for-widecontrol-format.md)|속성 또는 값은 넓은 보기에 표시 된 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

값은 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.

## <a name="example"></a>예제

ProcessName 속성 값을 표시 하는 넓은 보기를 보여 주는이 예제는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.

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

[WideItem 요소 (형식)](./wideitem-element-for-widecontrol-format.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
