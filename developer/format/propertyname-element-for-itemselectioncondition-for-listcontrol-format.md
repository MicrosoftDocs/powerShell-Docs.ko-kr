---
title: PropertyName 요소 ListControl (형식)에 대 한 ItemSelectionCondition | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064750"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)

조건이 트리거하는.NET 속성을 지정 합니다. 이 속성이 있는 경우 또는로 평가 되 면 `true`, 조건이 충족 될 및 뷰가 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

ListItem ListControl (형식)에 대 한 ListEntry ListItems 요소 ListControl (형식)에 구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 요소 (형식) ListControl 요소 (형식) ListEntry 요소 ListEntries 요소 (형식) 요소 ListItems ListItem ListControl (형식)에 대 한 ItemSelectionCondition ListControls PropertyName 요소에 대 한 ListControl (형식) ItemSelectionCondition 요소에 대 한

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `PropertyName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>텍스트 값

값은 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우를 지정할 수 없습니다는 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) 요소 선택 조건을 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[ListIControl (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
