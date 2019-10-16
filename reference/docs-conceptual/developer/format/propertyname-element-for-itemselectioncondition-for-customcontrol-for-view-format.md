---
title: CustomControl (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362442"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)

조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 있거나 `true`으로 평가 되 면 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 보기 (형식)에 대 한 Customentry에 대 한 customentry의 CustomControl for view (Format) ItemSelectionCondition 요소에 대 한 CustomControl for View (format) PropertyName 요소에 대 한 ItemSelectionCondition 요소 보기에 대 한 CustomControl (형식

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `PropertyName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

조건을 트리거하는 .NET 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[CustomControl에 대 한 ItemSelectionCondition의 ScriptBlock 요소 (형식)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
