---
title: 이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787634"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)

조건을 트리거하는 스크립트를 지정 합니다. 이 스크립트를로 평가 하면 `true` 조건이 충족 되 고 목록 항목이 사용 됩니다. 이 요소는 목록 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format)이 listcontrol Element (format) ListEntries Element for ListEntries (format) ListEntry element for이 listcontrol (format) element for ListItems (format) element for ListEntry (format)의 ListItem 요소에 대 한이 listcontrol (형식)에 대 한 ItemSelectionCondition 요소에 대 한 ListItems (형식)

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

평가 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하는 경우 `PropertyName` 선택 조건을 정의할 때 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
