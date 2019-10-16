---
title: GroupBy (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365292"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)

이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다. 컨트롤 항목에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 CustomControl에 대 한 customitem 요소에 대 한 customitem에 대 한 customitem에 대 한 CustomItem에 대 한 CustomItem의 경우 groupby (형식)에 대 한 ExpressionBinding에 대 한 요소

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
|[GroupBy (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[GroupBy (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomItem의 ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="remarks"></a>설명

이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)

[GroupBy (형식)에 대 한 CustomItem의 ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md)
