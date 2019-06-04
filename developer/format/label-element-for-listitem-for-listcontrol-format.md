---
title: ListItem 요소 ListControl (형식)에 대 한 레이블에 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065430"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 Label 요소(형식)

행의 속성이 나 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntry ListControl 요소 (에 대 한 ListItems ListControl (형식)에 대 한 ListEntry 요소의 ListControl (형식) ListItem 요소 ListItems ListItem ListControl (형식)에 대 한 레이블 요소 ListControl (형식)에 대 한 형식)

## <a name="syntax"></a>구문

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Label` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListItem 요소 ListItems ListControl (형식)에 대 한](./listitem-element-for-listitems-for-listcontrol-format.md)|속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

속성 또는 스크립트 값의 왼쪽에 표시 되도록 레이블을 지정 합니다.

## <a name="remarks"></a>설명

레이블을 지정 하지 않으면 속성 또는 스크립트의 이름을 표시 됩니다. 레이블을 사용 하 여 목록 보기에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.

## <a name="example"></a>예제

다음 예에서는 행에 레이블을 추가 하는 방법을 보여 줍니다.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[ListItem 요소 (형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
