---
title: CustomControl 보려면 (형식)에 대 한 CustomEntry EntrySelectedBy 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859589"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)

이 사용자 지정 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 뷰 (형식)에 대 한 CustomEntry 요소

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
|[CustomEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 정의 사용할 수 있어야 하는 조건을 정의 합니다.|
|[CustomEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤 뷰이 정의 사용 하는.NET 형식의 집합을 지정 합니다.|
|[EntrySelectedBy CustomEntry (형식)에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤 뷰이 정의 사용 하는.NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|특정.NET 개체에서 사용 하는 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

하나 이상의 형식, 선택 영역 집합 또는 항목에 대 한 선택 조건을 지정 해야 합니다. 사용할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

선택 조건을 사용 하 여 사용할 조건을 정의한 다음 있어야 하는 데 사용할 항목에 대 한 개체의 특정 속성에 있을 때와 같은, 특정 속성 값 이거나 스크립트 계산 `true`합니다. 선택 조건에 대 한 자세한 내용은 참조 하세요. [경우 보기 항목에 대 한 조건은 정의 또는 항목이 사용 되 고](./defining-conditions-for-displaying-data.md)입니다.

사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 뷰](./creating-custom-controls.md)합니다.

## <a name="see-also"></a>참고 항목

[CustomEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[CustomEntry (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[EntrySelectedBy CustomEntry (형식)에 대 한 TypeName 요소](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[뷰 (형식)에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[사용자 지정 컨트롤 뷰](./creating-custom-controls.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
