---
title: ExpressionBinding CustomControl (형식)에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858189"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>CustomControl의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)

이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다. 컨트롤 항목에 지정 될 수 있는 선택 조건 수 제한은 없습니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry CustomItem CustomControl CustomControl에 대 한 보기 (형식)에 대 한 식 바인딩 ItemSelectionCondition 요소 (형식) 보기에 대 한에 대 한 보기 (형식) ExpressionBinding 요소에 대 한

## <a name="syntax"></a>구문

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ItemSelectionCondition` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[PropertyName ItemSelectionCondition CustomControl 보려면 (형식에 대 한 요소](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 속성을 지정 합니다.|
|[CustomControl 보려면 (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

하면 하나의 속성 이름 또는이 조건에 대 한 스크립트를 지정할 수 있지만 둘 다 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)

[ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
