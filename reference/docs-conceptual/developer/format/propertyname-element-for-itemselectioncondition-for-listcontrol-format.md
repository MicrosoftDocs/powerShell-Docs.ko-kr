---
title: 이 listcontrol (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362392"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)

조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 있거나 `true`된 것으로 평가 되 면 조건이 충족 되 고 뷰가 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol element (format) ListEntries element (format) ListEntry 요소 for이 listcontrol (format) ListItems Element for ListEntry (Format) ListItem ListItems에 대 한 요소 for이 listcontrol (Format) ItemSelectionCondition 요소 (ListControls의 경우 ListItem 요소)의 ItemSelectionCondition for이 listcontrol (Format)

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
|[이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>텍스트 값

값이 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[ListIControl (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
