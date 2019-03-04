---
title: TableControl (형식)에 대 한 EntrySelectedBy에 대 한 SelectionCondition TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856499"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)

조건이 트리거하는.NET 형식을 지정 합니다. 이 형식은 존재 하는 경우 조건이 충족 되 고 테이블 행 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 TypeName 요소 TableRowEntry (형식)에 대 한 SelectionCondition 요소

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
|[TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|사용할 테이블 행이 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

와 같이.NET 형식의 정규화 된 이름을 지정 `System.IO.DirectoryInfo`합니다.

## <a name="remarks"></a>설명

선택 조건.NET 형식의 숫자를 지정할 수 또는 선택 영역 집합을 모두 지정할 수 없습니다. 선택 조건을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[TableRowEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[EntrySelectedBy TableRowEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
