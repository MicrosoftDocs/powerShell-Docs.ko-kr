---
title: 구성 (형식)에 대 한 컨트롤에 대 한 요소 CustomItem에 대 한 프레임 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065566"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)

왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

CustomControl Configuration (구성 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소 CustomEntry CustomItem 구성 (형식)에 대 한 컨트롤에 대 한 구성 프레임 요소에 대 한 컨트롤에 대 한 구성 (형식) CustomItem 요소에 대 한 컨트롤에 대 한 CustomControl CustomEntry 요소 형식)

## <a name="syntax"></a>구문

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Frame` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`CustomItem Element`|필수 요소|
|[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다.|
|[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineIndent 요소](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다.|
|[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 LeftIndent 요소](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다.|
|[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 RightIndent 요소](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.|

## <a name="remarks"></a>설명

지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 하며 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 동일한 요소 `Frame` 요소입니다.

## <a name="see-also"></a>참고 항목

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 FirstLineIndent 요소](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 LeftIndent 요소](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[구성 (형식)에 대 한 컨트롤에 대 한 프레임에 대 한 RightIndent 요소](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[구성에 대 한 컨트롤에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
