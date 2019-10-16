---
title: WideControl (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364782"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다. 넓은 항목 정의에 대해 지정할 수 있는 선택 조건 수에는 제한이 없습니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (Format) SelectionCondition 요소 WideEntry에 대 한 EntrySelectedBy (형식)

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

다음 섹션에서는 `SelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 단일 `PropertyName` 또는 `ScriptBlock` 요소를 지정 해야 합니다. @No__t-0 및 `TypeName` 요소는 선택 사항입니다. 두 요소 중 하나를 지정할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트 블록을 지정 합니다.|
|[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 형식 집합을 지정 합니다.|
|[WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 유형을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md)|이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.|

## <a name="remarks"></a>설명

각 넓은 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.

선택 조건을 정의 하는 경우 다음 요구 사항이 적용 됩니다.

- 선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- 선택 조건은 원하는 수의 .NET 형식 또는 선택 집합을 지정할 수 있지만 둘 다 지정할 수는 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[넓은 뷰 만들기](./creating-a-wide-view.md)

[데이터가 표시 되는 시점에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)

[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md)

[WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[WideEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition에 대 한 SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[WideEntry (형식)에 대해 EntrySelectedBy의 SelectionCondition에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
