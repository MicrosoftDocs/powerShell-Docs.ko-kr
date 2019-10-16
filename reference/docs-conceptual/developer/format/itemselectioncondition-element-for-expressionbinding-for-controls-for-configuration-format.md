---
title: 구성 (형식)의 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362922"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)

이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) 구성에 대 한 컨트롤의 CustomControl에 대 한 CustomEntry 요소 구성 (형식)에 대 한 컨트롤의 Customentry 요소 구성 요소에 대 한 Customentry에 대 한 컨트롤의 customentry 구성에 대 한 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `ItemSelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[구성 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[구성에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[구성 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[구성에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[구성에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
