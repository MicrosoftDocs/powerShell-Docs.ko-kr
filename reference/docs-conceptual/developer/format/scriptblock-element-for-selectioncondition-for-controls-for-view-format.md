---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)
description: View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: 7eed3b8a06bc45396026b8e2a7454447b3090d74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664937"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a>View에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) CustomControl 요소에 대 한 컨트롤의 컨트롤에 대 한 컨트롤의 요소입니다. view (format) EntrySelectedBy의 컨트롤에 대 한 CustomEntries 요소의 항목 요소에 대 한 참조 요소 뷰 (format)의 컨트롤에 대 한 컨트롤의 SelectionCondition 요소에 대 한 컨트롤에 대 한 SelectionCondition 요소에 대 한 컨트롤의 SelectionCondition 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ScriptBlock` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[View에 대한 Controls의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
