---
title: GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066229"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>GroupBy의 CustomEntry에 대한 EntrySelectedBy 요소(형식)

이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소 GroupBy (형식)에 대 한 CustomControl

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다. 하나 이상의 형식 또는 선택 집합 정의 대 한 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 이 정의 사용할 수 있어야 하는 조건을 정의 합니다.|
|[GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의이 정의 사용 하는.NET 형식의 집합을 지정 합니다.|
|[GroupBy (형식)에 대 한 EntrySelectedBy TypeName 요소](./typename-element-for-entryselectedby-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의이 정의 사용 하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-groupby-format.md)|컨트롤의 정의 제공합니다.|

## <a name="remarks"></a>설명

선택 조건을 사용 하 여 사용할 조건을 정의한 다음 있어야 하는 데 사용할 정의 대 한, 개체의 특정 속성에 있을 때와 같은 또는 특정 속성 값 이거나 스크립트 계산 `true`합니다. 선택 조건에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[GroupBy (형식)에 대 한 EntrySelectedBy TypeName 요소](./typename-element-for-entryselectedby-for-groupby-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-controls-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
