---
title: 구성 (형식)의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 690b6ae01b8116b72fbd00aef574feda1fd737b0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786036"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 ExpressionBinding에 대한 CustomControlName 요소(형식)

공용 컨트롤의 이름을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl for Configuration (Format) Customentries 요소 CustomControl 구성에 대 한 컨트롤의 경우 (Format) Customentries 요소 구성의 컨트롤에 대 한 customentries의 컨트롤에 대 한 customentries 요소 구성 (형식)에 대 한 컨트롤의 요소에 대 한 CustomControlName 요소 구성 (형식)

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
|[Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 다음 요소는 이러한 컨트롤의 이름을 지정 합니다.

- [Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

- [View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

[View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

[Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
