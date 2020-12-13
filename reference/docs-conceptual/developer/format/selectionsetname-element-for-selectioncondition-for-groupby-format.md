---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)
description: GroupBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654986"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>GroupBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)

조건을 트리거하는 .NET 형식 집합을 지정 합니다. 이 집합에 있는 형식이 있으면 조건이 충족 되 고이 컨트롤을 사용 하 여 개체가 표시 됩니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl CustomControl for GroupBy (format) EntrySelectedBy 요소에 대 한 Customentries for groupby (format) SelectionSetName 요소에 대 한 selectioncondition 요소에 대해 groupby (형식)의 SelectionCondition 요소

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 집합은 형식 지정 파일에서 정의 하는 모든 뷰에서 사용할 수 있는 .NET 개체의 공통 그룹입니다. 선택 집합을 만들고 참조 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.

이 요소를 지정 하면 [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) 요소를 지정할 수 없습니다. 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[GroupBy의 SelectionCondition에 대한 TypeName 요소(형식)](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[데이터가 표시 되는 시점에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)

[선택 영역 집합 정의](./defining-selection-sets.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
