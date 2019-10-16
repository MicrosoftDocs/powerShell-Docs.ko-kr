---
title: 보기 (형식)의 컨트롤에 대 한 ItemSelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364922"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>View에 대한 Controls의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를 사용 하 여 `true`으로 평가 되 면 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for view (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry의 요소에 대 한 형식입니다. 뷰 (형식) 컨트롤에 대 한 ItemSelectionCondition의 뷰 (Format) ScriptBlock 요소에 대 한 ExpressionBinding의 ItemSelectionCondition 요소

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
|[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[View 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 (형식)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
