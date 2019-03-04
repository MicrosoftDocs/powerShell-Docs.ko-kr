---
title: PropertyName 요소 EntrySelectedBy ListControl (형식)에 대 한에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: f857f5944b9e971215a06d6f5c39f7c22c6cf99f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853299"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)

조건이 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 목록 항목이 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 ListEntry (형식) SelectionCondition 요소에 대 한 EntrySelectedBy EmtrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition PropertyName 요소 ListEntry (형식)에

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|사용할이 목록 항목에 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 속성 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 조건 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.

목록 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [목록 보기 만들기](./creating-a-list-view.md)합니다.

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[표시 되는 경우 데이터에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)

[ListEntry 요소 (형식)](./listentry-element-for-listcontrol-format.md)

[EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
