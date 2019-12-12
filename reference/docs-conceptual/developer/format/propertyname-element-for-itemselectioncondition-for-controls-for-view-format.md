---
title: 보기 (형식)의 컨트롤에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362482"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>View에 대한 Controls의 ItemSelectionCondition에 대한 PropertyName 요소(형식)

조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 있거나 `true`된 것으로 평가 되 면 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for view (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry의 요소에 대 한 형식입니다. 뷰 (형식) 컨트롤에 대 한 ItemSelectionCondition의 View (Format) PropertyName 요소에 대 한 ExpressionBinding의 ItemSelectionCondition 요소

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `PropertyName` 요소의 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

조건을 트리거하는 .NET 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[View 컨트롤에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[View 컨트롤에 대 한 ExpressionBinding의 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
