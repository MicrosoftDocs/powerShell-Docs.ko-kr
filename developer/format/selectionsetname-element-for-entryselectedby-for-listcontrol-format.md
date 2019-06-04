---
title: ListControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075565"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)

목록 항목에 대 한.NET 개체 집합을 지정합니다. 항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) EntrySelectedBy 요소에 대 한 ListEntry (형식) SelectionSetName 요소에 대 한 EntrySelectedBy ListEntry (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSetName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|이 목록 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 항목 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

각 목록 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다. 예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다. 선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [보기에 대 한 개체 집합을 정의](./defining-selection-sets.md)합니다.

목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 선택 목록 뷰 항목에 대 한 세트를 지정 하는 방법을 보여 줍니다.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[ListEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
