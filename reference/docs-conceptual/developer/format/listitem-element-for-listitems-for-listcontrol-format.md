---
title: 이 listcontrol (형식)에 대 한 ListItems의 ListItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365132"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListControl의 ListItems에 대한 ListItem 요소(형식)

목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소의이 listcontrol (format) ListItems 요소 (형식) 이 listcontrol 요소에 대 한 ListItem (형식)

## <a name="syntax"></a>구문

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `ListItem` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 하나의 속성 또는 스크립트만 지정할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[이 listcontrol의 ListItem 요소에 대 한 FormatString 요소 (형식)](./formatstring-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 서식 문자열을 지정 합니다.|
|[이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[이 listcontrol (형식)의 ListItem에 대 한 Label 요소](./label-element-for-listitem-for-listcontrol-format.md)|선택적 요소<br /><br /> 행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.|
|[이 listcontrol의 ListItem 요소에 대 한 PropertyName 요소 (형식)](./propertyname-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 해당 값이 행에 표시 되는 .NET 속성을 지정 합니다.|
|[이 listcontrol (형식)의 ListItem 요소에 대 한 ScriptBlock 요소](./scriptblock-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 행에 값이 표시 되는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[List 컨트롤 (Format)의 ListItems 요소](./listitems-element-for-listentry-for-listcontrol-format.md)|값이 목록 뷰에 표시 되는 속성 및 스크립트를 정의 합니다.|

## <a name="remarks"></a>설명

목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예에서는 목록 뷰의 세 행을 정의 하는 XML 요소를 보여 줍니다. 처음 두 행에는 .NET 속성의 값이 표시 되 고 마지막 행에는 스크립트에 의해 생성 된 값이 표시 됩니다.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>참고 항목

[ListItems 요소 (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[ListItem의 FormatString 요소 (형식)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[ListItem의 Label 요소 (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[ListItem의 PropertyName 요소 (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ListItem의 ScriptBlock 요소 (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[목록 보기 만들기](./creating-a-list-view.md)

[Windows PowerShell 서식 지정 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
