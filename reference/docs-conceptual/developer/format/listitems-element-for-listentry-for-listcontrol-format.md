---
title: ListEntry의이 listcontrol 요소에 대 한 ListItems 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362742"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListControl의 ListEntry에 대한 ListItems 요소(형식)

목록 뷰의 행에 값이 표시 되는 속성 및 스크립트를 정의 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol element (format) ListEntries Element for이 listcontrol (format) ListItems Element for이 listcontrol (Format)

## <a name="syntax"></a>구문

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `ListItems` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 지정할 수 있는 자식 요소 수에는 제한이 없습니다. 자식 요소의 순서는 목록 보기에 값이 표시 되는 순서를 정의 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[이 listcontrol에 대 한 ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|필수 요소입니다.<br /><br /> 목록 뷰에서 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[이 listcontrol에 대 한 ListEntry 요소 (형식)](./listentry-element-for-listcontrol-format.md)|목록 뷰의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

이 유형의 보기에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예에서는 목록 뷰의 세 행을 정의 하는 XML 요소를 보여 줍니다.

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

[이 listcontrol에 대 한 ListEntry 요소 (형식)](./listentry-element-for-listcontrol-format.md)

[이 listcontrol에 대 한 ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[목록 보기 만들기](./creating-a-list-view.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
