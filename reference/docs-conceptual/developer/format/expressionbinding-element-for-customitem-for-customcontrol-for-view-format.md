---
title: CustomControl 용 CustomItem에 대 한 ExpressionBinding 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363152"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)

컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소 CustomControl for View (Format) ExpressionBinding 요소의 CustomItem에 대 한 CustomControl for View (Format)

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

다음 섹션에서는 특성, 자식 요소 및 `ExpressionBinding` 요소의 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`CustomControl Element`|선택적 요소입니다.<br /><br /> 이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.|
|[CustomControl에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.|
|[CustomControl에 대 한 ExpressionBinding의 EnumerateCollection 요소 (형식)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컬렉션의 요소가 표시 되도록 지정 합니다.|
|[CustomControl에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[CustomControl에 대 한 ExpressionBinding의 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.|
|[CustomCustomControl에 대 한 ExpressionBinding의 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomControl에 대 한 Customitem 요소의 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[CustomControl에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl에 대 한 ExpressionBinding의 EnumerateCollection 요소 (형식)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[CustomControl에 대 한 ExpressionBinding의 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl에 대 한 ExpressionBinding의 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl에 대 한 Customitem 요소의 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
