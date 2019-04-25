---
title: ExpressionBinding 요소 구성 (형식)에 대 한 컨트롤에 대 한 CustomItem | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065948"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)

컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry CustomItem 구성 (형식)에 대 한 컨트롤에 대 한 구성 ExpressionBinding 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식)

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
|[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 CustomControlName 요소](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다.|
|[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 컬렉션의 요소는 컨트롤에서 표시 되도록 지정 합니다.|
|[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 이 공용 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.|
|[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 PropertyName 요소](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤에서 해당 값이 표시.NET 속성을 지정 합니다.|
|[구성 (형식)에 대 한 컨트롤에 대 한 ExpressionBinding에 대 한 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤에서 해당 값이 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
