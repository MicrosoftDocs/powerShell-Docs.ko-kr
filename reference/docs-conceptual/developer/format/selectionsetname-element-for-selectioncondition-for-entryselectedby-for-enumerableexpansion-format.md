---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)
description: EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: 0c9372113a79f75cfbda67acf869164fde894ee3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651591"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)

조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 됩니다.

구성 요소 DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)에 대 한 Entryselectedby 요소에 대 한 By enumerableexpansions (형식)의 selectioncondition 요소에 대 한 by

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 조건에서 선택 집합 또는 .NET 형식을 지정할 수 있지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다. 선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[선택 영역 집합 정의](./defining-selection-sets.md)

[EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
