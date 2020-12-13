---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ListItem에 대한 PropertyName 요소(형식)
description: ListControl의 ListItem에 대한 PropertyName 요소(형식)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665977"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 PropertyName 요소(형식)

값이 목록에 표시 되는 .NET 속성을 지정 합니다.

구성 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry element (format) ListItems Element (format) ListItem 요소 (format) PropertyName 요소 (format)

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
|[ListItem 요소 (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

값이 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하면 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소를 지정할 수 없습니다.

속성 값을 표시 하는 것 외에도 값의 표시를 변경 하는 데 사용할 수 있는 서식 문자열 또는 값에 대 한 레이블을 지정할 수 있습니다. 목록 뷰에서 데이터를 지정 하는 방법에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 값이 표시 되는 레이블 및 속성을 지정 하는 방법을 보여 줍니다.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>참고 항목

[ListControl의 ListItem에 대한 ScriptBlock 요소(형식)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[목록 보기 만들기](./creating-a-list-view.md)

[이 listcontrol에 대 한 ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
