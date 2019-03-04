---
title: ExpressionBinding 요소 (형식) 보기에 대 한 컨트롤에 대 한 CustomItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858299"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>View에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)

컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry CustomItem 보기 (형식)에 대 한 컨트롤에 대 한 보기 (형식) ExpressionBinding 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ExpressionBinding` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`CustomControl Element`|선택적 요소입니다.<br /><br /> 이 컨트롤에서 사용 되는 컨트롤을 정의 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 CustomControlName 요소](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컬렉션의 요소 표시 되도록 지정 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 해당 값이 표시.NET 속성을 지정 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-view-format.md)|컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 CustomControlName 요소](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
