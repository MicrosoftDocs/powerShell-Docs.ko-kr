---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
description: GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665094"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>GroupBy의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소에 대 한 groupby 요소 (format) CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Format) GroupBy 항목에 대 한 Customentries 요소 groupby (format)에 대 한 Customentries에 대 한 요소에 대 한 요소에 대 한 요소에 대 한 요소에 대 한 요소를 지정 합니다.

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[GroupBy의 ExpressionBinding에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy의 ItemSelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
