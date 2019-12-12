---
title: WideEntry (형식)에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363332"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>WideEntry에 대한 EntrySelectedBy 요소(형식)

이 정의를 사용 하기 위해 존재 해야 하는 조건 또는 넓은 뷰의이 정의를 사용 하는 .NET 형식을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소 (형식)

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `EntrySelectedBy` 요소의 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 이 광범위 한 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 이 넓은 뷰 정의를 사용 하는 .NET 형식 집합을 지정 합니다.|
|[WideEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소](./typename-element-for-entryselectedby-for-wideentry-format.md)|선택적 요소입니다.<br /><br /> 이 광범위 한 뷰 정의를 사용 하는 .NET 유형을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry 요소 (Format)](./wideentry-element-for-widecontrol-format.md)|넓은 뷰의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

넓은 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트 값이 `true`로 평가 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다. 선택 조건에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[WideEntry 요소 (Format)](./wideentry-element-for-widecontrol-format.md)

[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry에 대 한 EntrySelectedBy (형식)의 TypeName 요소](./typename-element-for-entryselectedby-for-wideentry-format.md)

[넓은 뷰 만들기](./creating-a-wide-view.md)

[데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
