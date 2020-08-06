---
title: 이 listcontrol (형식)의 ListEntry에 대 한 EntrySelectedBy 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774119"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>ListControl의 ListEntry에 대한 EntrySelectedBy 요소(형식)

이 목록 뷰 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다. 대부분의 경우 목록 뷰에 대 한 정의는 하나만 필요 합니다. 그러나 같은 목록 뷰를 사용 하 여 다른 개체에 대해 서로 다른 데이터를 표시 하려는 경우 목록 뷰에 대 한 여러 정의를 제공할 수 있습니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format)이 listcontrol Element (format) ListEntries Element for ListEntry (format) EntrySelectedBy 요소 for이 listcontrol (Format)

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[이 listcontrol (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 뷰 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 뷰 정의를 사용 하는 .NET 형식 집합을 지정 합니다.|
|[ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 뷰 정의를 사용 하는 .NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl에 대한 ListEntry 요소(형식)](./listentry-element-for-listcontrol-format.md)|목록의 행을 표시 하는 방법을 정의 합니다.|

## <a name="remarks"></a>설명

목록 뷰 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 정의를 사용 하기 위해 있어야 하는 조건을 정의 하는 데 사용 됩니다 `true` . 선택 조건에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 .NET 형식 이름을 사용 하 여 목록 뷰에 대 한 개체를 정의 하는 방법을 보여 줍니다.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>참고 항목

[ListControl에 대한 ListEntry 요소(형식)](./listentry-element-for-listcontrol-format.md)

[ListControl의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[목록 보기 만들기](./creating-a-list-view.md)

[데이터가 표시 되는 시점에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
