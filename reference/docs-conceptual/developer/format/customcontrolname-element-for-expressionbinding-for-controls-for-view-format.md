---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)
description: View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)
ms.openlocfilehash: 35e1554a9eed491f37499a7455e9c5cae3cd9e1e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655456"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>View에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)

공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 view (format) CustomEntries 요소에 대 한 컨트롤 요소 (형식) Customentries view (format)의 컨트롤에 대 한 Customentries 요소의 Customentries 요소 뷰 (Format)의 컨트롤에 대 한 customentries 요소에 대 한 컨트롤의 customentries 요소에 대 한 컨트롤의 Customentries 요소

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
|[View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 다음 요소는 이러한 컨트롤의 이름을 지정 합니다.

- [Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

- [View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

[View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

[View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
