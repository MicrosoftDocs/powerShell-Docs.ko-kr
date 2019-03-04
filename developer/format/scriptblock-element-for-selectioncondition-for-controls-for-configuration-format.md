---
title: 구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853219"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 SelectionCondition에 대한 ScriptBlock 요소(형식)

조건이 트리거하는 스크립트를 지정 합니다. 이 스크립트를 계산할 때 `true`조건이 충족 되 고 정의가 사용 됩니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry EntrySelectedBy 구성 (형식)에 대 한 컨트롤에 대 한 구성 (형식) SelectionCondition 요소에 대 한 컨트롤에 대 한 구성 (형식) EntrySelectedBy 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식) 구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition ScriptBlock 요소

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|공용 컨트롤 정의 사용할 수 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

계산 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

선택 조건 최소 하나의 스크립트 또는 속성 이름을 평가 수행 하려면을 지정 해야 하지만 둘 다 지정할 수 없습니다. 선택 조건을 사용할 수 있는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="see-also"></a>참고 항목

[구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
