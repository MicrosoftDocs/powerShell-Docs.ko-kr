---
title: CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionSetName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855029"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)

목록 항목에 대 한.NET 개체 집합을 지정합니다. 항목에 대해 지정할 수 있는 선택 항목 집합 수에 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries EntrySelectedBy 보기 (형식)에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry EntrySelectedBy CustomEntry (형식)에 대 한 보기 (형식) SelectionSetName 요소에 대 한 요소

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
|[뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|이 사용자 지정 항목 또는 사용할이 항목에 대 한 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 항목 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

각 사용자 지정 컨트롤 항목 형식 이름, 선택 집합 또는 정의 된 선택 조건을 하나 이상 있어야 합니다.

선택 영역 집합은 여러 뷰에서 사용 되는 개체의 그룹을 정의 하려는 경우에 일반적으로 사용 됩니다. 예를 들어 다음 테이블 뷰를 만들고 동일한 개체 집합에 대 한 목록 뷰는 것이 좋습니다. 선택 영역 집합을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [선택 영역 설정 정의](./defining-selection-sets.md)합니다.

사용자 지정 컨트롤 보기의 구성 요소에 대 한 자세한 내용은 참조 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[사용자 지정 컨트롤 뷰](./creating-custom-controls.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
