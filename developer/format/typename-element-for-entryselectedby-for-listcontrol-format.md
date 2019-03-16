---
title: EntrySelectedBy ListControl (형식)에 대 한 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059697"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>ListControl의 EntrySelectedBy에 대한 TypeName 요소(형식)

이 항목의 목록 보기를 사용 하는.NET 형식을 지정 합니다. 목록 항목에 대해 지정할 수 있는 형식의 수 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 TypeName 요소 ListEntry (형식)에 대 한 EntrySelectedBy ListControl (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|이 목록 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.

## <a name="remarks"></a>설명

각 목록 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

목록 보기에이 요소를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 선택 목록 뷰 항목에 대 한 세트를 지정 하는 방법을 보여 줍니다.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
