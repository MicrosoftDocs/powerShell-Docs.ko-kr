---
title: GroupBy (형식)에 대 한 CustomEntry CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856929"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)

사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomItem 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 GroupBy (형식)에 대 한 CustomEntry

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomItem` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에 표시 되는 데이터를 정의 합니다.|
|[GroupBy (형식)에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.|
|[GroupBy (형식)에 대 한 CustomItem 줄 바꿈 요소](./newline-element-for-customitem-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의 표시에 빈 줄을 추가합니다.|
|[GroupBy (형식)에 대 한 CustomItem에 대 한 텍스트 요소](./text-element-for-customitem-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 추가 텍스트 컨트롤에 의해 표시 되는 데이터를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-groupby-format.md)|사용자 지정 컨트롤 뷰의 정의 제공합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 CustomControl CustomEntry 요소](./customentry-element-for-customcontrol-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomItem 프레임 요소](./frame-element-for-customitem-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomItem 줄 바꿈 요소](./newline-element-for-customitem-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomItem에 대 한 텍스트 요소](./text-element-for-customitem-for-groupby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
