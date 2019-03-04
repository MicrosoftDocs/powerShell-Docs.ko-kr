---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858019"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntries CustomEntry EntrySelectedBy 보기 (컨트롤에 대 한 보기 (형식) SelectionCondition 요소에 대 한 컨트롤에 대 한 보기 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 보기 (형식) CustomEntry 요소에 대 한 컨트롤에 대 한 형식)

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionCondition` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 속성을 지정 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는 스크립트를 지정 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식의 집합을 지정 합니다.|
|[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition TypeName 요소](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="remarks"></a>설명

선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.

- 선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition TypeName 요소](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
