---
title: 구성 (형식)의 컨트롤에 대 한 SelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7730951a840fcfcd8bf819fff5182049bd6b6c23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773133"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 SelectionCondition에 대한 PropertyName 요소(형식)

조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 항목이 사용 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (format) 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한의 Customentries 요소 구성 (형식) EntrySelectedBy 요소 구성 (형식)에 대 한 컨트롤에 대 한 customentries의 구성 (형식) PropertyName 요소에 대해 ListEntry (형식)에 대 한 EntrySelectedBy SelectionCondition 요소

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `PropertyName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 속성 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 조건은 하나 이상의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
