---
title: 뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363782"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)

컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for view (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry의 요소에 대 한 형식입니다.

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
|[뷰의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.|
|[View 컨트롤의 ExpressionBinding에 대 한 EnumerateCollection 요소 (형식)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컬렉션의 요소를 표시 하도록 지정 합니다.|
|[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[View 컨트롤의 ExpressionBinding에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.|
|[View 컨트롤의 ExpressionBinding에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰의 컨트롤에 대 한 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-controls-for-view-format.md)|컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[뷰의 컨트롤에 대 한 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[뷰의 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[View 컨트롤의 ExpressionBinding에 대 한 EnumerateCollection 요소 (형식)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[View 컨트롤의 ExpressionBinding에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[View 컨트롤의 ExpressionBinding에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
