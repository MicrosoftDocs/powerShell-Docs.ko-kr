---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)
description: ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)
ms.openlocfilehash: c515efe70afdb1c1186c0a07fe1f52dc49ad57b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665994"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)

조건을 트리거하는 .NET 속성을 지정 합니다. 이 속성이 존재 하거나로 확인 되 면 `true` 조건이 충족 되 고 뷰가 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol element (format) ListEntries element (format) ListItems 요소의 ListEntry에 대 한이 listcontrol (format) ListItem 요소의 ListItems에 대 한이 listcontrol 요소의 ItemSelectionCondition 요소에 대 한 ItemSelectionCondition의 ItemSelectionCondition 요소 (형식)

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `PropertyName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>텍스트 값

값이 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 선택 조건을 정의할 때 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[ListIControl (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
