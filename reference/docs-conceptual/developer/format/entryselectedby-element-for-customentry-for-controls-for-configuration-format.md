---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
description: Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666674"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)

공용 컨트롤의 정의를 사용 하는 .NET 형식 또는이 컨트롤을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (format) 컨트롤 구성 요소에 대 한 컨트롤의 요소 구성 (format) CustomControl 요소 구성 (형식)에 대 한 컨트롤의 Customentries 요소 구성 (형식)에 대 한 컨트롤의 customentries 요소 구성 (형식)에 대 한 컨트롤에 대 한 CustomEntries 요소 구성 (형식)

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.|
|[Configuration에 대한 Controls의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤의이 정의를 사용 하는 .NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|공용 컨트롤의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

최소한 각 정의에는 하나 이상의 .NET 유형, 선택 집합 또는 선택 조건이 지정 되어 있어야 합니다. 지정할 수 있는 형식, 선택 집합 또는 선택 조건의 수에는 제한이 없습니다.

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
