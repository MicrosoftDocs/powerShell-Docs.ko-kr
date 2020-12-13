---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)
description: EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: bd72a9bc914ea6543d8dab768b5e20e9a580ada7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664910"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다.

Configuration 요소 (Format) DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)-enumerableexpansions (format)에 대 한 entryselectedby에 대 한 요소 (형식)-enumerableexpansions (형식)에 대 한 SelectionCondition의 SelectionCondition 요소

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
|[EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[데이터가 표시 되는 시점에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
