---
title: ScriptBlock 요소 CustomControl 보려면 (형식)에 대 한 ItemSelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064478"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)

조건이 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 컨트롤이 사용 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry CustomItem CustomControl CustomControl에 대 한 보기 (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소에 대 한 식 바인딩 ItemSelectionCondition 요소 (형식) 보기에 대 한에 대 한 보기 (형식) ExpressionBinding 요소에 대 한 CustomControl 보려면 (형식)

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 CustomControl에 대 한 식 바인딩 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|이 컨트롤을 사용할 수 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

계산 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우를 지정할 수 없습니다는 [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 요소 선택 조건을 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[PropertyName ItemSelectionCondition CustomControl 보려면 (형식)에 대 한 요소](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[뷰 (형식)에 대 한 CustomControl에 대 한 식 바인딩 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
