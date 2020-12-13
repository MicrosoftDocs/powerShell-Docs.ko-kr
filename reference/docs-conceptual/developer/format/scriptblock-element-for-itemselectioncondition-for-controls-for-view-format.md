---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
description: View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: c005215f7b7984541806d2f5de47372d536787ff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665197"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 컨트롤에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소 (format) Customentries 요소 CustomControl view (format) Customentries 요소 for View (format)의 컨트롤에 대 한 customentries 요소 뷰 (format)의 컨트롤에 대 한 ExpressionBinding 요소에 대 한 컨트롤의 요소에 대 한 요소에 대 한 요소를 참조 하십시오.

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
