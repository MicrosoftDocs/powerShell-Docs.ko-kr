---
title: TableControl (형식)에 대 한 EntrySelectedBy의 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368322"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)

테이블 뷰의이 항목을 사용 하는 .NET 형식 집합을 지정 합니다. 항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) TableControl Element (format) TableRowEntries Element (format) TableRowEntry Element (format) EntrySelectedBy 요소 (format) SelectionSetName 요소 TableRowEntry에 대 한 EntrySelectedBy (형식)

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|이 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다. 예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다. 선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

항목에 대 한 선택 집합을 지정 하는 경우 형식 이름을 지정할 수 없습니다. .NET 형식을 지정 하는 방법에 대 한 자세한 내용은 [TableRowEntry (형식)에 대 한 EntrySelectedBy에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-tablecontrol-format.md)를 참조 하세요.

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[보기에 대 한 개체 집합 정의](./defining-selection-sets.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
