---
title: ScriptBlock 요소 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064376"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 ScriptBlock 요소(형식)

조건이 트리거하는 스크립트를 지정 합니다.

구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소에 대 한 EntrySelectedBy SelectionCondition 요소 EnumerableExpansion (형식)에 EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소 EnumerableExpansion (형식)

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
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

계산 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

선택 조건 평가 수행 하려면 하나 이상의 스크립트 또는 속성 이름을 지정 해야 하지만 둘 다 지정할 수 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="see-also"></a>참고 항목

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
