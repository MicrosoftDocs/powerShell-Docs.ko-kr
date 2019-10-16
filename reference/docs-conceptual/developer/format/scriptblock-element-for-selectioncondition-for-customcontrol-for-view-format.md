---
title: CustomControl에 대 한 SelectionCondition의 ScriptBlock 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368642"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 SelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 `true`으로 평가 하면 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions element (Format) View 요소 (format) CustomControl 요소에 대 한 view (format) CustomEntries 요소에 대 한 CustomControl Format) CustomItem 요소에 대 한 CustomControl for view (format) SelectionCondition 요소에 대 한 CustomControl for view (format) ScriptBlock 요소에 대해 SelectionCondition for CustomControl for view (Format)

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `ScriptBlock` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CustomControl for View (Format)에 대해 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
