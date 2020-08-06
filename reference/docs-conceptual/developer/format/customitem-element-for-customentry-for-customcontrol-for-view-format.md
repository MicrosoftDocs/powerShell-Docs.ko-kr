---
title: CustomControl (형식)에 대 한 Customitem 요소의 CustomItem 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 25101c9c156ef91657f51db7044bf9a6653142a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785832"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)

사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 customentries 요소

## <a name="syntax"></a>구문

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomItem` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에 표시 되는 데이터를 정의 합니다.|
|[View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.|
|[보기의 사용자 지정 컨트롤에 대 한 CustomItem의 줄 바꿈 요소 (형식)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의 표시에 빈 줄을 추가 합니다.|
|[CustomControl에 대 한 CustomItem의 Text 요소 (형식)](./text-element-for-customitem-for-customview-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에 표시 되는 데이터에 대 한 추가 텍스트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|사용자 지정 컨트롤 뷰의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[View에 대한 CustomControl의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[View에 대한 CustomControl의 CustomItem에 대한 NewLine 요소(형식)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomControl에 대 한 CustomItem의 Text 요소 (형식)](./text-element-for-customitem-for-customview-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
