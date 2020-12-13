---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)
description: ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645660"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)

목록 뷰의이 항목을 사용 하는 .NET 형식을 지정 합니다. 목록 항목에 대해 지정할 수 있는 형식 수에는 제한이 없습니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry Element (format) EntrySelectedBy 요소에 대 한 ListEntry (형식) TypeName 요소에 대해이 listcontrol (형식)에 대해 EntrySelectedBy

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|이 목록 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

같은 .NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo` 합니다.

## <a name="remarks"></a>설명

각 목록 항목에는 하나 이상의 유형 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.

이 요소를 목록 뷰에서 사용 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 목록 뷰의 항목에 대해 선택 집합을 지정 하는 방법을 보여 줍니다.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>참고 항목

[목록 보기 만들기](./creating-a-list-view.md)

[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntry (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
