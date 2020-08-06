---
title: 구성 컨트롤의 컨트롤에 대 한 Name 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d45ba98b909ebee18e01d2b6985a48906ce39d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783537"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)

컨트롤의 이름을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤 요소 구성 (형식) 컨트롤의 요소 구성 (형식)에 대 한 컨트롤의 요소

## <a name="syntax"></a>구문

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Name` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration의 Controls에 대한 Control 요소(형식)](./control-element-for-controls-for-configuration-format.md)|서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

이 컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.

## <a name="remarks"></a>설명

여기에 지정 된 이름은 다음 요소에서이 컨트롤을 참조 하는 데 사용할 수 있습니다.

- 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 만들 때 컨트롤은 [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md) 와 같은 요소로 지정할 수 있습니다.

- 다른 공용 컨트롤을 만들 때이 컨트롤은 [구성 (형식)에 대 한 컨트롤의 CustomItem에 대 한 Expressionbinding 요소](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) 와 같은 요소로 지정할 수 있습니다.

- 뷰에서 사용할 수 있는 컨트롤을 만들 때이 컨트롤은 다음 요소를 사용 하 여 지정할 수 있습니다. [Expressionbinding 요소를 사용 하 여 뷰 컨트롤의 CustomItem에 대 한 요소입니다 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) .

## <a name="see-also"></a>참고 항목

[Configuration의 Controls에 대한 Control 요소(형식)](./control-element-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
