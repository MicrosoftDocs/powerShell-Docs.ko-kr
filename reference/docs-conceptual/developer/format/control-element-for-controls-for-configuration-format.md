---
title: 구성에 대 한 컨트롤 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9447efac84cff3cc33468aeebc97a8bdd6137518
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783826"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Configuration의 Controls에 대한 Control 요소(형식)

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.

구성 요소 (Format) 컨트롤의 구성 요소 컨트롤 요소 (형식)

## <a name="syntax"></a>구문

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소에 대 한 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Control` . 각 자식 요소 중 하나만 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|필수적 요소입니다.<br /><br /> 컨트롤을 정의 합니다.|
|[구성에 대 한 컨트롤의 Name 요소 (형식)](./name-element-for-control-for-controls-for-configuration-format.md)|필수적 요소입니다.<br /><br /> 컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성의 컨트롤 요소 (형식)](./controls-element-for-configuration-format.md)|서식 파일의 모든 보기 또는 다른 컨트롤에서 사용할 수 있는 공용 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

이 컨트롤에 지정 된 이름은 다음 요소에서 참조할 수 있습니다.

- [CustomItem에 대 한 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>참고 항목

[구성의 컨트롤 요소 (형식)](./controls-element-for-configuration-format.md)

[구성 (형식)의 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomItem에 대 한 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md)

[Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
