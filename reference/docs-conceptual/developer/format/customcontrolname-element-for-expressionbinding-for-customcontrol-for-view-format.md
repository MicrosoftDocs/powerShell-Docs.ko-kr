---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)
description: View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)
ms.openlocfilehash: 24b27428c07d7178f0069f6d0e5b7ffc555efe34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666810"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 ExpressionBinding에 대한 CustomControlName 요소(형식)

공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) Viewcontrolelement (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) Customentries 요소의 view (format) customentries 요소에 대 한 customentries 요소 (view)의 customentries 요소 (형식)의 customentries 요소에 대 한 customentries 요소 (customentries의 경우)

## <a name="syntax"></a>구문

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomItem에 대 한 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 이러한 컨트롤의 이름은 다음 요소로 지정 됩니다.

- [Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

- [View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

[View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

[CustomItem에 대 한 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
