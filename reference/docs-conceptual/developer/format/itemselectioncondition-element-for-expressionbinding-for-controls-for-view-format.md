---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
description: View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648058"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>View에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)

이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 view (format) CustomEntries 요소에 대 한 컨트롤 요소 (형식) Customentries 뷰 (형식)의 컨트롤에 대 한 Customentries 요소의 Customentries 요소 뷰 (format)의 컨트롤에 대 한 customentries 요소에 대 한 컨트롤의 customentries 요소에 대 한 컨트롤의 Customentries 요소에 대 한 컨트롤의 요소입니다.

## <a name="syntax"></a>구문

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
