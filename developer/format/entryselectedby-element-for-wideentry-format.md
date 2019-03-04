---
title: EntrySelectedBy 요소 WideEntry (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854979"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>WideEntry에 대한 EntrySelectedBy 요소(형식)

이 정의 된 와이드 보기인 경우 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식) EntrySelectedBy 요소 WideEntry (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EntrySelectedBy` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 사용할이 넓은 보기 정의가 있어야 하는 조건을 정의 합니다.|
|[WideEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|선택적 요소입니다.<br /><br /> 이 넓은 보기 정의 사용 하는.NET 형식의 집합을 지정 합니다.|
|[EntrySelectedBy WideEntry (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-wideentry-format.md)|선택적 요소입니다.<br /><br /> 이 넓은 보기 정의 사용 하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry 요소 (형식)](./wideentry-element-for-widecontrol-format.md)|넓은 보기의 정의 제공 합니다.|

## <a name="remarks"></a>설명

하나 이상의 형식, 선택 영역 집합 또는 와이드 뷰 정의 대 한 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

선택 조건을 사용 하 여 정의 개체의 특정 속성에 때와 같이 사용할 수 있어야 하는 조건을 정의 또는 스크립트 또는 특정 속성 값으로 계산 되는 `true`합니다. 선택 조건에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.

## <a name="see-also"></a>참고 항목

[WideEntry 요소 (형식)](./wideentry-element-for-widecontrol-format.md)

[WideEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[EntrySelectedBy WideEntry (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-wideentry-format.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[데이터를 표시 하기 위한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
