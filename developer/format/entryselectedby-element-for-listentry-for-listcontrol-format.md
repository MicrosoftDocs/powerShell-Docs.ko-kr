---
title: ListControl (형식)에 대 한 ListEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 723619e67612b859d0acbab37eecd82141adf923
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854949"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>ListControl의 ListEntry에 대한 EntrySelectedBy 요소(형식)

이 목록 뷰 정의 사용 하는.NET 형식 또는이 정의를 사용할 수 있어야 하는 조건을 정의 합니다. 대부분의 경우 목록 보기에 대 한 정의 하나만 필요 합니다. 그러나 동일한 목록 뷰를 사용 하 여 다른 개체에 대 한 다양 한 데이터를 표시 하려면 목록 보기에 대 한 여러 정의 제공할 수 있습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntry ListControl (형식) EntrySelectedBy 요소에 대 한 (형식) ListControl ListEntry 요소에 ListEntry ListControl (형식)에 대 한

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
|[ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 뷰 정의 사용할 수 있어야 하는 조건을 정의 합니다.|
|[ListControl (형식)에 대 한 EnrtySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 뷰 정의 사용 하는.NET 형식의 집합을 지정 합니다.|
|[EntrySelectedBy ListControl (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 뷰 정의 사용 하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl (형식)에 대 한 ListEntry 요소](./listentry-element-for-listcontrol-format.md)|목록의 행 표시 되는 방식을 정의 합니다.|

## <a name="remarks"></a>설명

하나 이상의 형식, 선택 항목 집합 또는 목록 뷰 정의 대 한 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

선택 조건을 사용 하 여 정의 개체의 특정 속성에 때와 같이 사용할 수 있어야 하는 조건을 정의 또는 스크립트나 특정 속성 값으로 계산 되는 `true`합니다. 선택 조건에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 해당.NET 형식 이름을 사용 하는 목록 보기에 대 한 개체를 정의 하는 방법을 보여 줍니다.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>참고 항목

[ListControl (형식)에 대 한 ListEntry 요소](./listentry-element-for-listcontrol-format.md)

[ListControl (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl (형식)에 대 한 EnrtySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[EntrySelectedBy ListControl (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[목록 뷰 만들기](./creating-a-list-view.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
