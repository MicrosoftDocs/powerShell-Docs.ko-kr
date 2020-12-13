---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)
description: ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667813"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)

이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한 ListEntries의 경우이 listcontrol에 대 한 ListItems (format) ListItem 요소의 ListEntry for이 listcontrol (format) ItemSelectionCondition 요소 (형식)의 ListItem 요소

## <a name="syntax"></a>구문

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `ItemSelectionCondition` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl의 ListItems에 대한 ListItem 요소(형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="remarks"></a>설명

이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[ListControl의 ListItems에 대한 ListItem 요소(형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[ListControl의 ItemSelectionCondition에 대한 PropertyName 요소(형식)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl의 ItemSelectionCondition에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
