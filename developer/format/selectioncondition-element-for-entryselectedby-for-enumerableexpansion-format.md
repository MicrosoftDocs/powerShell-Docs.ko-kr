---
title: EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858289"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

이 정의의 컬렉션 개체를 확장 하려면 있어야 하는 조건을 정의 합니다.

구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) EntrySelectedBy 요소에 대 한 EntrySelectedBy SelectionCondition 요소 EnumerableExpansion (형식)에 EnumerableExpansion (형식)

## <a name="syntax"></a>구문

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다. 단일 지정 해야 합니다 `PropertyName` 또는 `ScriptBlock` 요소입니다. 합니다 `SelectionSetName` 고 `TypeName` 요소는 선택 사항입니다. 두 요소 중 하나를 지정할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 속성을 지정 합니다.|
|[EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는 스크립트를 지정 합니다.|
|[EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식의 집합을 지정 합니다.|
|[SelectionCondition EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-enumerableexpansion-format.md)|이 정의 의해 확장 되는.NET 컬렉션 개체를 정의 합니다.|

## <a name="remarks"></a>설명

각 정의 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.

- 선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [Diplaying 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [와이드 보기인 경우](./creating-a-wide-view.md)합니다.

## <a name="see-also"></a>참고 항목

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
