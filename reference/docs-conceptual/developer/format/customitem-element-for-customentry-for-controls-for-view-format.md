---
title: 뷰의 컨트롤에 대 한 CustomItem 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363942"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)

컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for View (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 (형식)에 대 한 CustomEntry 요소의 Customentry 요소

## <a name="syntax"></a>구문

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `CustomItem` 요소의 부모 요소에 대해 설명 합니다. 자세한 내용은 설명 부분을 참조 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에 표시 되는 데이터를 정의 합니다.|
|[View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.|
|[뷰 컨트롤의 CustomItem에 대 한 줄 바꿈 요소 (형식)](./newline-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의 표시에 빈 줄을 추가 합니다.|
|[뷰 컨트롤의 CustomItem에 대 한 텍스트 요소 (형식)](./text-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 괄호 또는 대괄호와 같은 텍스트를 컨트롤의 표시에 추가 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰의 컨트롤에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-controls-for-view-format.md)|컨트롤의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

`CustomItem` 요소의 자식 요소를 지정할 때는 다음 사항을 염두에 두어야 합니다.

- 자식 요소는 `ExpressionBinding`, `NewLine`, `Text`및 `Frame`순서로 추가 해야 합니다.

- 지정할 수 있는 시퀀스 수에 대 한 최대 제한은 없습니다.

- 각 시퀀스에서 사용할 수 있는 `ExpressionBinding` 요소 수에 대 한 최대 제한은 없습니다.

## <a name="see-also"></a>참고 항목

[뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-controls-for-view-format.md)

[뷰 컨트롤의 CustomItem에 대 한 줄 바꿈 요소 (형식)](./newline-element-for-customitem-for-controls-for-view-format.md)

[뷰 컨트롤의 CustomItem에 대 한 텍스트 요소 (형식)](./text-element-for-customitem-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
