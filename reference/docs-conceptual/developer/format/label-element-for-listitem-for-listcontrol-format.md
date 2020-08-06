---
title: 이 listcontrol (형식)의 ListItem에 대 한 Label 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783639"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 Label 요소(형식)

행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format)이 listcontrol의 경우 ListItems의 경우 ListEntry에 대 한이 listcontrol 요소 (format) ListItem 요소에 대 한 ListItems for이 listcontrol (형식)의 ListItem 요소에 대 한이 listcontrol (형식)

## <a name="syntax"></a>구문

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Label` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl의 ListItems에 대한 ListItem 요소(형식)](./listitem-element-for-listitems-for-listcontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

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

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
