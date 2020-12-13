---
ms.date: 09/13/2016
ms.topic: reference
title: View의 Controls에 대한 Control 요소(형식)
description: View의 Controls에 대한 Control 요소(형식)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668085"
---
# <a name="control-element-for-controls-for-view--format"></a>View의 Controls에 대한 Control 요소(형식)

뷰에서 사용할 수 있는 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소에 대 한 컨트롤 요소 (형식)

## <a name="syntax"></a>구문

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Control` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[View 컨트롤의 Name 요소 (Format)](./name-element-for-control-for-controls-for-view-format.md)|필수적 요소입니다.<br /><br /> 컨트롤의 이름을 지정 합니다.|
|[View에 대한 Controls의 Control에 대한 CustomControl 요소(형식)](./customcontrol-element-for-control-for-controls-for-view-format.md)|필수적 요소입니다.<br /><br /> 이 뷰에서 사용 하는 컨트롤을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Controls 요소 (Format)](./controls-element-for-view-format.md)|특정 뷰에서 사용할 수 있는 뷰 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

이 컨트롤은 다음 요소로 지정할 수 있습니다.

- [View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [GroupBy에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>참고 항목

[View에 대한 Controls의 Control에 대한 CustomControl 요소(형식)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls 요소 (Format)](./controls-element-for-view-format.md)

[View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
