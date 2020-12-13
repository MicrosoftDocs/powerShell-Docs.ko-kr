---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)
description: Configuration에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 860683eb54b2a3579767640c1d3f0937897b8f8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655122"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)

조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) Customentries 요소에 대 한 CustomControl 요소에 대 한 구성 (형식)) Customentries 요소 구성 요소에 대 한 컨트롤의 Customentries에 대 한 컨트롤의 요소에 대 한 컨트롤의 요소에 대 한 요소에 대 한 컨트롤의 요소에 대 한 요소에 대 한 요소를 구성 하는 ItemSeclectionCondition 요소에 대 한 컨트롤의 요소입니다.

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

조건을 트리거하는 .NET 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
