---
title: ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065447"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)

이 목록 항목을 사용할 수 있어야 하는 조건을 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntries ListEntry ListItems 요소 ListControl (형식)에 대 한 (형식) ListControl ListEntry 요소에 ListItems ListControl (형식)에 대 한 ListItem ItemSelectionCondition 요소 ListControl (형식)에 대 한 (형식) ListControl ListItem 요소에

## <a name="syntax"></a>구문

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ItemSelectionCondition` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[PropertyName ItemSelectionCondition ListControl (형식)에 대 한 요소](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는.NET 속성을 지정 합니다.|
|[ListControl (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 조건이 트리거하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListItem 요소 ListItems ListControl (형식)에 대 한](./listitem-element-for-listitems-for-listcontrol-format.md)|속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.|

## <a name="remarks"></a>설명

하면 하나의 속성 이름 또는이 조건에 대 한 스크립트를 지정할 수 있지만 둘 다 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[ListItem 요소 ListItems ListControl (형식)에 대 한](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName ItemSelectionCondition ListControl (형식)에 대 한 요소](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ListControl (형식)에 대 한 ItemSelectionCondition ScriptBlock 요소](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
