---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
description: CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)
ms.openlocfilehash: 38c88ad47e57cd20902c6b8aabdb0b8e8b682ba4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648047"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)

이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소 (형식) Customentries에 대 한 customentries 요소 View (format) CustomControl for view (format) ItemSelectionCondition 요소에 대 한 Customentries에 대 한 CustomControl for View (Format)

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
|[CustomControl에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[View에 대한 CustomControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)

[View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
