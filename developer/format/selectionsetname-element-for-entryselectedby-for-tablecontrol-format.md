---
title: TableControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063924"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)

.NET의 집합 형식을 사용 하 여 테이블 보기의이 항목을 지정 합니다. 항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식) TableRowEntries 요소 (형식) TableRowEntry 요소 (형식) EntrySelectedBy 요소 (형식) SelectionSetName 요소에 대 한 EntrySelectedBy TableRowEntry (형식)에 대 한

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소를 설명합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|이 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 항목 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다. 예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다. 선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [보기에 대 한 개체 집합을 정의](./defining-selection-sets.md)합니다.

선택 항목에 대 한 세트를 지정 하는 경우 형식 이름을 지정할 수 없습니다. .NET 형식을 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [EntrySelectedBy TableRowEntry (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-tablecontrol-format.md)합니다.

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="see-also"></a>참고 항목

[EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[보기에 대 한 개체의 집합을 정의합니다.](./defining-selection-sets.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
