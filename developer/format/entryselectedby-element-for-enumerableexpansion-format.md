---
title: EntrySelectedBy 요소 EnumerableExpansion (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855589"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)

이 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.

구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소 EnumerableExpansion (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 이 정의의 컬렉션 개체를 확장 하는 방법을 사용 하는.NET 형식의 집합을 지정 합니다.|
|[EntrySelectedBy EnumerableExpansion (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 컬렉션 개체를 확장 하는 방법을이 정의 하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion 요소 (형식)](./enumerableexpansion-element-format.md)|개체는 뷰에서 표시 되는 확장은 어떻게 특정.NET 컬렉션을 정의 합니다.|

## <a name="remarks"></a>설명

하나 이상의 형식, 선택 영역 집합 또는 정의 항목에 대 한 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

선택 조건을 사용 하 여 정의 개체의 특정 속성에 때와 같이 사용할 수 있어야 하는 조건을 정의 또는 스크립트나 특정 속성 값으로 계산 되는 `true`합니다. 선택 조건에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="see-also"></a>참고 항목

[데이터를 표시 하기 위한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 요소 (형식)](./enumerableexpansion-element-format.md)

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EntrySelectedBy EnumerableExpansion (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
