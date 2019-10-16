---
title: 구성에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363192"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 CustomItem에 대한 ExpressionBinding 요소(형식)

컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) 구성에 대 한 컨트롤의 CustomControl에 대 한 CustomEntry 요소 구성 (형식)에 대 한 컨트롤의 Customentry 요소 구성 요소에 대 한 Customentry에 대 한 컨트롤의 customentry

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

다음 섹션에서는 `ExpressionBinding` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`CustomControl Element`|선택적 요소입니다.<br /><br /> 이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.|
|[구성에 대 한 컨트롤에 대 한 ExpressionBinding의 CustomControlName 요소 (형식)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.|
|[구성에 대 한 컨트롤의 ExpressionBinding에 대 한 EnumerateCollection 요소 (형식)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 컬렉션의 요소를 표시 하도록 지정 합니다.|
|[구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 이 공용 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[구성에 대 한 컨트롤의 ExpressionBinding에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.|
|[구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ScriptBlock 요소 (형식)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 컨트롤 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[구성에 대 한 컨트롤 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
