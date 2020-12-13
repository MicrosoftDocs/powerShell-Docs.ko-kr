---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
description: Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)
ms.openlocfilehash: ce00cdf868a3075875043aeb59f2cb8a17d049a9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645778"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 구성 요소에 대 한 컨트롤의 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 CustomEntries 요소 구성 (형식)의 컨트롤에 대 한 CustomControl의 Customentries 요소 구성에 대 한 컨트롤의 Customentries 요소 (형식)에 대 한 customentries 요소에 대 한 컨트롤의 SelectionCondition 요소

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

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionCondition` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|
|[Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 형식 집합을 지정 합니다.|
|[Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 유형을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|공용 컨트롤 정의의이 항목을 사용 하는 .NET 형식을 정의 합니다.|

## <a name="remarks"></a>설명

선택 조건을 정의할 때는 다음 지침을 따라야 합니다.

- 선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- 선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.

선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Windows PowerShell 서식 지정 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
