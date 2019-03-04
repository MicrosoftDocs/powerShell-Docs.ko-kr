---
title: WideControl 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859829"
---
# <a name="widecontrol-element-format"></a>WideControl 요소(형식)

와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다. 이 보기에는 단일 속성 값 또는 각 개체에 대 한 스크립트 값을 표시합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식)

## <a name="syntax"></a>구문

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideControl` 요소입니다. 지정할 수 없습니다는 `AutoSize` 및 `ColumnNumber` 동시 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideControl (형식)에 대 한 자동 크기 조정 요소](./autosize-element-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 조정 여부를 열 크기 및 열 개수는 데이터의 크기를 기준으로 지정 합니다.|
|[ColumnNumber 요소 WideControl (형식)](./columnnumber-element-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 넓은 보기에 표시 된 열의 수를 지정 합니다.|
|[WideEntries 요소 (형식)](./wideentries-element-for-widecontrol-format.md)|필수 요소입니다.<br /><br /> 넓은 보기의 정의 제공합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 요소 (형식)](./view-element-format.md)|하나 이상의.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

넓은 보기를 정의 하는 경우 추가할 수 있습니다 합니다 `AutoSize` 요소 또는 `ColumnNumber` 있지만 둘 다를 추가할 수 없습니다.

대부분의 경우에서 하나만 정의 각 넓은 보기가에 대 한 필수 이지만 다른.NET 개체를 표시 하려면 같은 뷰를 사용 하려는 경우 정의가 여러 개 있을 수 있습니다. 이러한 경우 각 개체 또는 개체 집합에 대 한 별도 정의 제공할 수 있습니다.

넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [뷰 구성 요소를 와이드](./creating-a-wide-view.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `WideControl` 의 속성을 표시 하는 데 사용 되는 요소는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

## <a name="see-also"></a>참고 항목

[WideControl (형식)에 대 한 자동 크기 조정 요소](./autosize-element-for-widecontrol-format.md)

[ColumnNumber 요소 WideControl (형식)](./columnnumber-element-for-widecontrol-format.md)

[뷰 요소 (형식)](./view-element-format.md)

[WideEntries 요소 (형식)](./wideentries-element-for-widecontrol-format.md)

[넓은 보기 (Basic)](./wide-view-basic.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
