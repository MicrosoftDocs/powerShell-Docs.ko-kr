---
title: WideControl 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367992"
---
# <a name="widecontrol-element-format"></a>WideControl 요소(형식)

뷰의 넓은 (단일 값) 목록 형식을 정의 합니다. 이 보기에는 각 개체에 대 한 단일 속성 값 또는 스크립트 값이 표시 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl 요소 (Format)

## <a name="syntax"></a>구문

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `WideControl` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. `AutoSize` 및 `ColumnNumber` 요소를 동시에 지정할 수 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideControl에 대 한 AutoSize 요소 (형식)](./autosize-element-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.|
|[WideControl에 대 한 ColumnNumber 요소 (형식)](./columnnumber-element-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 넓은 보기에 표시 되는 열 수를 지정 합니다.|
|[WideEntries 요소 (Format)](./wideentries-element-for-widecontrol-format.md)|필수적 요소입니다.<br /><br /> 넓은 뷰의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 요소 (Format)](./view-element-format.md)|하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

넓은 뷰를 정의할 때 `AutoSize` 요소나 `ColumnNumber`를 추가할 수 있지만 둘 다를 추가할 수는 없습니다.

대부분의 경우 각 넓은 뷰에 대해 정의가 하나만 필요 하지만 동일한 뷰를 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 사용할 수 있습니다. 이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.

넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide View 구성 요소](./creating-a-wide-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체의 속성을 표시 하는 데 사용 되는 `WideControl` 요소를 보여 줍니다.

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

넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[WideControl에 대 한 Autosize 요소 (형식)](./autosize-element-for-widecontrol-format.md)

[WideControl에 대 한 ColumnNumber 요소 (형식)](./columnnumber-element-for-widecontrol-format.md)

[View 요소 (Format)](./view-element-format.md)

[WideEntries 요소 (Format)](./wideentries-element-for-widecontrol-format.md)

[넓은 보기 (기본)](./wide-view-basic.md)

[넓은 뷰 만들기](./creating-a-wide-view.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
