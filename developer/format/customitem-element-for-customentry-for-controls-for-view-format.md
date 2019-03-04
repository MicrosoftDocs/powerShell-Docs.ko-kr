---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855609"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)

컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry 보기 (형식)에 대 한 컨트롤에 대 한 보기 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomItem` 요소입니다. 자세한 내용은 설명 부분을 참조 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에 표시 되는 데이터를 정의 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다.|
|[줄 바꿈 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem 요소](./newline-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의 표시에 빈 줄을 추가합니다.|
|[텍스트 보기 (형식)에 대 한 컨트롤에 대 한 CustomItem 요소](./text-element-for-customitem-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의 표시에 대괄호 또는 괄호와 같은 텍스트를 추가합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-controls-for-view-format.md)|컨트롤의 정의 제공합니다.|

## <a name="remarks"></a>설명

자식 요소를 지정 하는 경우는 `CustomItem` 요소를 다음 염두 합니다.

- 다음 순서 대로 자식 요소를 추가 해야 합니다. `ExpressionBinding`, `NewLine`를 `Text`, 및 `Frame`합니다.

- 지정할 수 있는 시퀀스의 수는 최대 제한은 없습니다.

- 각 시퀀스에는 수의 최대 제한이 `ExpressionBinding` 사용할 수 있는 요소입니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-controls-for-view-format.md)

[줄 바꿈 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem 요소](./newline-element-for-customitem-for-controls-for-view-format.md)

[텍스트 보기 (형식)에 대 한 컨트롤에 대 한 CustomItem 요소](./text-element-for-customitem-for-controls-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
