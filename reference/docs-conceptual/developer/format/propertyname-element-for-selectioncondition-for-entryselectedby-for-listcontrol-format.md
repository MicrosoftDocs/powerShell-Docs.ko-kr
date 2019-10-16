---
title: 이 listcontrol (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362292"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 PropertyName 요소(형식)

조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 목록 항목이 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (Format) SelectionCondition 요소 ListEntry (형식)에 대 한 EntrySelectedBy의 ListEntry (Format) PropertyName 요소에 대 한 EntrySelectedBy

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 속성 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 조건은 하나 이상의 속성 이름 또는 스크립트 블록을 지정 해야 하지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

목록 뷰의 다른 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[목록 보기 만들기](./creating-a-list-view.md)

[데이터가 표시 되는 시점에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)

[ListEntry 요소 (Format)](./listentry-element-for-listcontrol-format.md)

[ListEntry (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
