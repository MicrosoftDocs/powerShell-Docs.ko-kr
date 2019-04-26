---
title: 요소 (형식) 보기에 대 한 CustomControl에 대 한 CustomItem에 대 한 프레임 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065583"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)

왼쪽 또는 오른쪽에 데이터를 이동 하는 등 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) CustomControl 요소 (형식) CustomEntries 요소 CustomControl CustomEntries CustomItem 요소 (형식) 보기에 대 한 보기 (형식) CustomEntry 요소에 대 한 CustomControlView (형식) 프레임에 대 한 요소의 CustomControl 보려면 (형식)에 대 한 CustomItem CustomEntry

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
|[FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 데이터의 첫 번째 줄은 왼쪽으로 이동 하는 문자 수를 지정 합니다.|
|[FirstLineIndent 요소](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 데이터의 첫 번째 줄은 오른쪽으로 옮겨집니다 문자 수를 지정 합니다.|
|[LeftIndent 요소](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 왼쪽된 여백에서 데이터 이동은 문자 수를 지정 합니다.|
|[RightIndent 요소](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 오른쪽 여백에서 데이터 이동은 문자 수를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|컨트롤에서 표시 되는 데이터 및 표시 되는 방식을 정의 합니다.|

## <a name="remarks"></a>설명

지정할 수 없습니다는 [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 하며 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 동일한 요소 `Frame` 요소입니다.

## <a name="see-also"></a>참고 항목

[FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent 요소](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent 요소](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent 요소](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[뷰 (형식)에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
