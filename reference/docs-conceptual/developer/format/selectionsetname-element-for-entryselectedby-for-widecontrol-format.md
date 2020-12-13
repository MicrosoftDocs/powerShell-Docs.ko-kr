---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
description: WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651688"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)

정의에 대 한 .NET 개체 집합을 지정 합니다. 정의는 이러한 개체 중 하나가 표시 될 때마다 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format) WideControl Element (format) WideEntries Element (format) WideEntry Element (format) EntrySelectedBy 요소에 대 한 WideEntry (format) SelectionSetName 요소에 대해 WideEntry (형식)

## <a name="syntax"></a>구문

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSetName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry에 대한 EntrySelectedBy 요소(형식)](./entryselectedby-element-for-wideentry-format.md)|이 항목을 사용 하기 위해 존재 해야 하는 조건 또는이 광범위 한 항목을 사용 하는 .NET 형식을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합의 이름을 지정 합니다.

## <a name="remarks"></a>설명

각 정의는 하나의 유형 이름, 선택 집합 또는 선택 조건을 지정 해야 합니다.

선택 집합은 일반적으로 여러 뷰에서 사용 되는 개체 그룹을 정의 하려는 경우에 사용 됩니다. 예를 들어 동일한 개체 집합에 대 한 테이블 뷰와 목록 뷰를 만들 수 있습니다. 선택 집합을 정의 하는 방법에 대 한 자세한 내용은 [보기에 대 한 개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[넓게 보기 만들기](./creating-a-wide-view.md)

[선택 영역 집합 정의](./defining-selection-sets.md)

[WideEntry에 대한 EntrySelectedBy 요소(형식)](./entryselectedby-element-for-wideentry-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
