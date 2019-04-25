---
title: ListItem 요소 ListItems ListControl (형식)에 대 한 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065770"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListControl의 ListItems에 대한 ListItem 요소(형식)

속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListControl (형식)에 대 한 ListControl (형식) ListItems 요소에 대 한 ListEntry 요소의 ListControl (형식) ListItem ListControl 요소 (형식)

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListItem` 요소입니다. 속성 또는 스크립트를 하나만 지정할 수 있습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ListItem ListControl (형식)에 대 한 FormatString 요소](./formatstring-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 문자열을 지정 합니다.|
|[ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 이 목록 항목을 사용할 수 있어야 하는 조건을 정의 합니다.|
|[ListItem ListControl (형식)에 대 한 레이블 요소](./label-element-for-listitem-for-listcontrol-format.md)|선택적 요소<br /><br /> 행의 속성이 나 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.|
|[PropertyName ListControl (형식)에 대 한 ListItem 요소](./propertyname-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> .NET 속성 값을 갖는 행에 표시 됩니다 지정 합니다.|
|[ScriptBlock ListControl (형식)에 대 한 ListItem 요소](./scriptblock-element-for-listitem-for-listcontrol-format.md)|선택적 요소입니다.<br /><br /> 행에 해당 값이 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[목록 컨트롤 (형식)에 대 한 ListItems 요소](./listitems-element-for-listentry-for-listcontrol-format.md)|속성 및 값을 목록 보기에 표시 되는 스크립트를 정의 합니다.|

## <a name="remarks"></a>설명

목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

이 예제에서는 목록 보기의 3 개의 행을 정의 하는 XML 요소를 보여 줍니다. .NET 속성의 값을 표시 하는 처음 두 행 및 마지막 행을 스크립트에 의해 생성 된 값을 표시 합니다.

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

[ListItems 요소 (형식)](./listitems-element-for-listentry-for-listcontrol-format.md)

[ListItem (형식)에 대 한 FormatString 요소](./formatstring-element-for-listitem-for-listcontrol-format.md)

[ListItem (형식)에 대 한 레이블 요소](./label-element-for-listitem-for-listcontrol-format.md)

[ListItem (형식)에 대 한 PropertyName 요소](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ListItem (형식)에 대 한 ScriptBlock 요소](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[목록 뷰 만들기](./creating-a-list-view.md)

[Windows PowerShell 형식 지정을 작성 하 고 파일 형식](./writing-a-powershell-formatting-file.md)
