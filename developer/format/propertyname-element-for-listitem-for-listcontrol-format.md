---
title: PropertyName ListControl (형식)에 대 한 ListItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064920"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 PropertyName 요소(형식)

값 목록에 표시 되는.NET 속성을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) ListItems 요소 (형식) ListItem 요소 (형식) PropertyName 요소에 대 한 ListItem (형식)

## <a name="syntax"></a>구문

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|속성 또는 목록 뷰의 행에 해당 값이 표시 되는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

값은 표시 되는 속성의 이름을 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 지정할 수 없습니다는 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소입니다.

속성 값을 표시 하는 것 외에도 값 또는 값의 표시를 변경 하는 형식 문자열에 대 한 레이블을 지정할 수도 있습니다. 목록 뷰에서 데이터를 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

다음 예에서는 레이블 및 해당 값이 표시 하는 속성을 지정 하는 방법을 보여 줍니다.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>참고 항목

[ScriptBlock ListControl (형식)에 대 한 ListItem 요소](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[목록 뷰 만들기](./creating-a-list-view.md)

[ListControl(Format) ListItem 요소](./listitem-element-for-listitems-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
