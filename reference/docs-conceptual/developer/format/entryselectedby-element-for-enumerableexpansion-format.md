---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368802"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)

이 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.

Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions element (format) enumerableexpansions 요소 (format) EntrySelectedBy 요소 (형식)

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `EntrySelectedBy` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 컬렉션 개체를 확장 하는 방법에 대 한이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 TypeName 요소](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 컬렉션 개체를 확장 하는 방법에 대 한이 정의를 사용 하는 .NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion 요소 (형식)](./enumerableexpansion-element-format.md)|특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.|

## <a name="remarks"></a>설명

정의 항목에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가 `true`으로 평가 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다. 선택 조건에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 요소 (형식)](./enumerableexpansion-element-format.md)

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 TypeName 요소](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
