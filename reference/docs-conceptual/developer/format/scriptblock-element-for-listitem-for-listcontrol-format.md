---
title: 이 listcontrol (형식)의 ListItem 요소에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785458"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ListControl의 ListItem에 대한 ScriptBlock 요소(형식)

행에 값이 표시 되는 스크립트를 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한 ListEntries의 경우이 listcontrol에 대 한 ListItems (format) ListItem 요소의 ListEntry for이 listcontrol (format) 요소

## <a name="syntax"></a>구문

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListItem 요소 (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

해당 값이 행에 표시 되는 스크립트를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하면 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소를 지정할 수 없습니다.

목록 뷰에서 스크립트를 지정 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 값이 표시 되는 속성을 지정 하는 방법을 보여 줍니다.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>참고 항목

[ListControl의 ListItem에 대한 PropertyName 요소(형식)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[목록 보기 만들기](./creating-a-list-view.md)

[ListControl의 ListItems에 대한 ListItem 요소(형식)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
