---
title: CustomControl (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 31873e886af04f8eedaf859af1d6bc1d5bcfdbf7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772878"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 계산 하면 `true` 조건이 충족 되 고 컨트롤이 사용 됩니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 CustomEntries 요소에 대 한 customentries 요소 (형식) Customentries 요소 view (format) 요소에 대 한 항목 CustomControl for view (format) ItemSelectionCondition 요소에 대 한 CustomControl for view (format) ScriptBlock 요소의 ItemSelectionCondition for view (Format)

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
|[CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[View에 대한 CustomControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[CustomControl for View (Format)의 식 바인딩에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
