---
title: GroupBy (형식)에 대 한 SelectionCondition SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856759"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>GroupBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)

트리거 조건이 있는.NET 형식의 집합을 지정 합니다. 이 형식의 값이 있는 경우 조건이 충족 될 하 고 개체는이 컨트롤을 사용 하 여 표시 됩니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry EntrySelectedBy GroupBy (형식)에 대 한 SelectionCondition SelectionSetName 요소 GroupBy (형식)에 대 한 GroupBy (형식) SelectionCondition 요소에 대 한 GroupBy (형식) EntrySelectedBy 요소에

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 항목 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 영역 집합은 일반적인 그룹 형식 지정 파일을 정의 하는 모든 보기에서 사용할 수 있는.NET 개체입니다. 만들기 및 선택 집합을 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [선택 영역 설정 정의](./defining-selection-sets.md)합니다.

이 요소를 지정 하는 경우 지정할 수 없습니다는 [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) 요소입니다. 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 SelectionCondition TypeName 요소](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[선택 영역 집합을 정의](./defining-selection-sets.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
