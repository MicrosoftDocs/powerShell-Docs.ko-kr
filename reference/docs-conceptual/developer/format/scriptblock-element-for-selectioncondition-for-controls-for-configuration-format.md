---
title: 구성 (형식)의 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368622"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 `true`으로 평가 하면 조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) CustomControl에 대 한 컨트롤의 CustomEntry 요소 구성 (형식)의 컨트롤에 대 한 CustomEntry 요소 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 SelectionCondition 요소 구성 (형식)에 대 한 컨트롤입니다. 구성 컨트롤에 대 한 SelectionCondition의 ScriptBlock 요소 (형식)

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
|[구성에 대 한 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|공용 컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

선택 조건은 평가할 스크립트나 속성 이름을 하나 이상 지정 해야 하지만 둘 다 지정할 수는 없습니다. 선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[구성에 대 한 컨트롤에 대해 EntrySelectedBy의 SelectionCondition 요소 (형식)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
