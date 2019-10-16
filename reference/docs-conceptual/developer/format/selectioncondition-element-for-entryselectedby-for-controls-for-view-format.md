---
title: 보기 (형식)의 컨트롤에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362052"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. View (format) CustomControl 컨트롤에 대 한 컨트롤의 CustomEntry 요소에 대 한 컨트롤에 대 한 Customentry 요소에 대 한 컨트롤의 CustomEntry 요소 형식과

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
|[View 컨트롤의 SelectionCondition에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[View 컨트롤의 SelectionCondition에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|
|[View 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 형식 집합을 지정 합니다.|
|[View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 유형을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|

## <a name="remarks"></a>설명

선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.

- 선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- 선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[View 컨트롤의 SelectionCondition에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[View 컨트롤의 SelectionCondition에 대 한 ScriptBlock 요소 (형식)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[View 컨트롤의 SelectionCondition에 대 한 SelectionSetName 요소 (형식)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[View 컨트롤의 SelectionCondition에 대 한 TypeName 요소 (형식)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[View 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
