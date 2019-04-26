---
title: CustomControl 보려면 (형식)에 대 한 CustomEntry CustomItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066416"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomEntry에 대한 CustomItem 요소(형식)

사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomEntry 보려면 (형식)

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
|[ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에 표시 되는 데이터를 정의 합니다.|
|[CustomItem CustomControl 보려면 (형식)에 대 한 프레임 요소](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 사용자 지정 컨트롤 보기에 의해 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.|
|[줄 바꿈 (형식) 보기에 대 한 사용자 지정 컨트롤에 대 한 CustomItem 요소](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 컨트롤의 표시에 빈 줄을 추가합니다.|
|[CustomItem CustomControl 보려면 (형식)에 대 한 텍스트 요소](./text-element-for-customitem-for-customview-for-view-format.md)|선택적 요소입니다.<br /><br /> 추가 텍스트 컨트롤에 의해 표시 되는 데이터를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CustomControl 보려면 (형식)에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|사용자 지정 컨트롤 뷰의 정의 제공합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding CustomItem CustomControl 보려면 (형식)에 대 한 요소](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomItem CustomControl 보려면 (형식)에 대 한 프레임 요소](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[줄 바꿈 CustomItem CustomControl 보려면 (형식)에 대 한 요소](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomItem CustomControl 보려면 (형식)에 대 한 텍스트 요소](./text-element-for-customitem-for-customview-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
