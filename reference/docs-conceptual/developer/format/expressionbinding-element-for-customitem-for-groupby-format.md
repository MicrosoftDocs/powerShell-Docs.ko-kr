---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)
description: GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655300"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)

컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소에 대 한 CustomControl 요소의 groupby (format) customentries 요소에 대 한 CustomControl의 경우 CustomControl에 대 한 customentries 요소에 대 한 Customentries 요소에 대 한 Customentries 요소

## <a name="syntax"></a>구문

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ExpressionBinding` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`CustomControl Element`|선택적 요소입니다.<br /><br /> 이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.|
|[GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.|
|[GroupBy (형식)에 대 한 ExpressionBinding의 Enumeratecollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) GroupBy (형식)에 대 한 ExpressionBinding의 EnumerateCollection 요소|선택적 요소입니다.<br /><br /> 컬렉션의 요소가 표시 되도록 지정 합니다.|
|[GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[GroupBy의 ExpressionBinding에 대한 PropertyName 요소(형식)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.|
|[GroupBy의 ExpressionBinding에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)](./customitem-element-for-customentry-for-groupby-format.md)|사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="see-also"></a>참고 항목

[GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy의 ExpressionBinding에 대한 EnumerateCollection 요소(형식)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy의 ExpressionBinding에 대한 PropertyName 요소(형식)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy의 ExpressionBinding에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)](./customitem-element-for-customentry-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
