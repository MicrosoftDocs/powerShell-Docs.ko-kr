---
title: CustomControl for View (Format)의 경우 EntrySelectedBy에 대 한 SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364752"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)

목록 항목에 대 한 .NET 개체 집합을 지정 합니다. 항목에 지정할 수 있는 선택 집합 수에는 제한이 없습니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) Customentries 요소에 대 한 CustomControl의 customentries 요소 view (형식) EntrySelectedBy CustomEntry (형식)에 대해 EntrySelectedBy View (Format) SelectionSetName 요소의 CustomEntry 요소

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `SelectionSetName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|이 사용자 지정 항목을 사용 하는 .NET 형식 또는이 항목을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

각 사용자 지정 컨트롤 항목에는 하나 이상의 형식 이름, 선택 집합 또는 선택 조건이 정의 되어 있어야 합니다.

선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다. 예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다. 선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.

사용자 지정 컨트롤 뷰의 구성 요소에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[사용자 지정 컨트롤 뷰](./creating-custom-controls.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
