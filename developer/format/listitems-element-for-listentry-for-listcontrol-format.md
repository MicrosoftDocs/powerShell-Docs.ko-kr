---
title: ListEntry ListControl (형식)에 대 한 요소 ListItems | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858589"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl의 ListEntry에 대한 ListItems 요소(형식)

속성 및 값을 목록 뷰의 행에 표시 되는 스크립트를 정의 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListControl (형식)에 대 한 ListControl (형식) ListItems 요소에 대 한 목록 컨트롤 (형식) ListEntry 요소에 대 한

## <a name="syntax"></a>구문

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListItems` 요소입니다. 지정할 수 있는 자식 요소의 수에 제한은 없습니다. 자식 요소의 순서는 값 목록 보기에 표시 되는 순서를 정의 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ListControl (형식)에 대 한 ListItem 요소](./listitem-element-for-listitems-for-listcontrol-format.md)|필수 요소입니다.<br /><br /> 속성 또는 목록 보기에서 해당 값이 표시 되는 스크립트를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl (형식)에 대 한 ListEntry 요소](./listentry-element-for-listcontrol-format.md)|목록 보기의 정의 제공 합니다.|

## <a name="remarks"></a>설명

뷰의이 유형에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

이 예제에서는 목록 보기의 3 개의 행을 정의 하는 XML 요소를 보여 줍니다.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>참고 항목

[ListControl (형식)에 대 한 ListEntry 요소](./listentry-element-for-listcontrol-format.md)

[ListControl (형식)에 대 한 ListItem 요소](./listitem-element-for-listitems-for-listcontrol-format.md)

[목록 뷰 만들기](./creating-a-list-view.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
