---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
description: View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655355"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomEntry에 대한 EntrySelectedBy 요소(형식)

이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) customentries 요소에 대 한 customentries 요소에 대 한 CustomEntries 요소 (format)

## <a name="syntax"></a>구문

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EntrySelectedBy` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[CustomEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[CustomEntry (형식)에 대 한 EntrySelectedBy 요소](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤 뷰의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다.|
|[CustomEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤 뷰의이 정의를 사용 하는 .NET 형식을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|특정 .NET 개체에서 사용 하는 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

항목에 대 한 형식, 선택 집합 또는 선택 조건을 하나 이상 지정 해야 합니다. 사용할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

선택 조건은 개체가 특정 속성을가지고 있거나 특정 속성 값 또는 스크립트가로 계산 되는 경우와 같이 사용 될 항목에 대해 존재 해야 하는 조건을 정의 하는 데 사용 됩니다 `true` . 선택 조건에 대 한 자세한 내용은 [뷰 항목이 나 항목을 사용 하는 경우에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 뷰](./creating-custom-controls.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CustomEntry (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[CustomEntry (형식)에 대 한 EntrySelectedBy 요소](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[CustomEntry (형식)에 대 한 EntrySelectedBy의 TypeName 요소](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[사용자 지정 컨트롤 뷰](./creating-custom-controls.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
