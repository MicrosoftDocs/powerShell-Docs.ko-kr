---
title: View (Format)의 컨트롤에 대 한 EntrySelectedBy의 SelectionSetName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c762a626fff746266919d1f7fcb991a8cdbcdf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787549"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>View에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)

컨트롤의이 정의를 사용 하는 .NET 형식 집합을 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) controls 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤에 대 한 뷰 (format) CustomEntries 요소에 대 한 컨트롤 요소 view (format) Entry 항목에 대 한 컨트롤의 Customentries 요소에 대 한 컨트롤 뷰 (format) SelectionSetName 요소에 대 한 컨트롤의 Customentries 요소 (형식)에 대 한 컨트롤의 경우 EntrySelectedBy

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `SelectionSetName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

각 컨트롤 정의에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.

선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다. 선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
