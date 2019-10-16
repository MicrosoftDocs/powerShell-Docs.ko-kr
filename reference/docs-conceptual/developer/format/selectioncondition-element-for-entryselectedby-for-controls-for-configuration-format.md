---
title: 구성 (형식)의 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368452"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 요소에 대 한 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤 요소에 대 한 CustomControl의 CustomEntries 요소에 대 한 컨트롤의 요소 구성 (형식)에 대 한 CustomControl 구성 요소에 대 한 구성 (형식) EntrySelectedBy의 컨트롤에 대 한 customentry의 구성 (형식)

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

다음 섹션에서는 `SelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[구성 컨트롤에 대 한 SelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[구성 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|
|[구성에 대 한 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 형식 집합을 지정 합니다.|
|[구성 컨트롤에 대 한 SelectionCondition의 TypeName 요소 (형식)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 유형을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|공용 컨트롤 정의의이 항목을 사용 하는 .NET 형식을 정의 합니다.|

## <a name="remarks"></a>설명

선택 조건을 정의할 때는 다음 지침을 따라야 합니다.

- 선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- 선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.

선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[구성 컨트롤에 대 한 SelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[구성 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[구성에 대 한 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[구성 컨트롤에 대 한 SelectionCondition의 TypeName 요소 (형식)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Windows PowerShell 서식 지정 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
