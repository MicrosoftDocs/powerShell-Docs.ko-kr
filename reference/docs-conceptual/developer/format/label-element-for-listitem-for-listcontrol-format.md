---
title: 이 listcontrol (형식)의 ListItem에 대 한 Label 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362892"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 Label 요소(형식)

행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View element (format)이 listcontrol Element (format) ListEntries Element for이 listcontrol (format) ListItems for ListEntry for이 listcontrol 요소 ( Format) ListItems의 ListItem 요소에 대해이 listcontrol (형식)의 ListItem 요소에 대 한 요소를 지정 합니다 (형식).

## <a name="syntax"></a>구문

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `Label` 요소의 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[이 listcontrol에 대 한 ListItems의 ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

속성이 나 스크립트 값의 왼쪽에 표시할 레이블을 지정 합니다.

## <a name="remarks"></a>설명

레이블을 지정 하지 않으면 속성이 나 스크립트의 이름이 표시 됩니다. 목록 뷰에서 레이블을 사용 하는 방법에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 행에 레이블을 추가 하는 방법을 보여 줍니다.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>참고 항목

[목록 보기 만들기](./creating-a-list-view.md)

[ListItem 요소 (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
