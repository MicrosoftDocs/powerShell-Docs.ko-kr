---
title: PropertyName 요소 CustomControl 보려면 (형식)에 대 한 SelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860969"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 SelectionCondition에 대한 PropertyName 요소(형식)

조건이 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 CustomControl CustomEntries CustomControl 보기 (에 대 한 보기 (형식) CustomEntry 요소에 대 한 보기 (형식) CustomEntries 요소에 CustomControl CustomEntry CustomControl EntrySelectedBy CustomControl PropertyName 보기 (형식)에 대 한에 대 한 보기 (형식) SelectionCondition 요소에 대 한 보기 (형식) EntrySelectedBy 요소에 대 한 CustomEntry CustomItem 요소 형식) SelectionCondition CustomControl 보려면 (형식)에 대 한 요소

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|사용할 컨트롤 정의에 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 속성 이름을 지정 합니다.

## <a name="remarks"></a>설명

선택 조건 최소 하나의 속성 이름 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다. 선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="see-also"></a>참고 항목

[CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
