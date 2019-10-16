---
title: 이 listcontrol (형식)의 ListItem에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365192"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)

이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 ListEntries의이 listcontrol (Format) ListItems 요소 for이 listcontrol (format) ListItem 요소의 경우 ListItems에 대 한 ItemSelectionCondition 요소에 대 한이 listcontrol (형식)

## <a name="syntax"></a>구문

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `ItemSelectionCondition` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[이 listcontrol (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 .NET 속성을 지정 합니다.|
|[이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건을 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[이 listcontrol에 대 한 ListItems의 ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="remarks"></a>설명

이 조건에 대해 하나의 속성 이름 또는 스크립트를 지정할 수 있지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[이 listcontrol에 대 한 ListItems의 ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[이 listcontrol (형식)에 대 한 ItemSelectionCondition의 PropertyName 요소](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[이 listcontrol (형식)에 대 한 ItemSelectionCondition의 ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
