---
title: ExpressionBinding CustomControl 보려면 (형식)에 대 한 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860439"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)

공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 CustomControl CustomEntries CustomItem 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 보기 (형식) CustomEntries 요소에 CustomEntry CustomItem (형식)에 대 한 식 바인딩의 CustomItem (형식) CustomControlName 요소에 대 한 보기 (형식) ExpressionBinding 요소에 대 한 요소

## <a name="syntax"></a>구문

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControlName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ExpressionBinding 요소 CustomItem (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

형식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있습니다 하 고 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 이러한 컨트롤의 이름은 다음 요소에 의해 지정 됩니다.

- [구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-configuration-format.md)

- [뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-configuration-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding 요소 CustomItem (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
