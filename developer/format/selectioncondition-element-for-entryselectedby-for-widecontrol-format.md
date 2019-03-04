---
title: WideControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854119"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>WideControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)

이 정의 사용할 수 있어야 하는 조건을 정의 합니다. 수가 와이드 항목 정의 대해 지정할 수 있는 선택 조건 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소에 대 한 WideEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy WideEntry (형식)에 대 한

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
|[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 속성을 지정 합니다.|
|[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는 스크립트 블록을 지정 합니다.|
|[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식의 집합을 지정 합니다.|
|[SelectionCondition EntrySelectedBy WideEntry (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md)|이 와이드 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="remarks"></a>설명

각 와이드 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

선택 조건을 정의 하는 경우 다음 요구 사항을 적용 합니다.

- 선택 조건 최소 하나의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다.

선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.

넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.

## <a name="see-also"></a>참고 항목

[넓은 보기 만들기](./creating-a-wide-view.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md)

[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[SelectionCondition EntrySelectedBy WideEntry (형식)에 대 한에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
